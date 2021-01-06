---
title: 回復力の高い Entity Framework Core SQL 接続を実装する
description: 回復力の高い Entity Framework Core SQL 接続を実装する方法について説明します。 この手法は、クラウドで Azure SQL Database を使用する場合に特に重要です。
ms.date: 10/16/2018
ms.openlocfilehash: cae3550ce301750949b042957d5d10f0167e614c
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899562"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="3abf7-104">回復力の高い Entity Framework Core SQL 接続を実装する</span><span class="sxs-lookup"><span data-stu-id="3abf7-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="3abf7-105">Azure SQL DB の場合、Entity Framework (EF) Core に内部データベース接続の復元機能と再試行ロジックが既に用意されています。</span><span class="sxs-lookup"><span data-stu-id="3abf7-105">For Azure SQL DB, Entity Framework (EF) Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="3abf7-106">ただし、[回復力のある EF Core 接続](/ef/core/miscellaneous/connection-resiliency)を使用する場合は、各 <xref:Microsoft.EntityFrameworkCore.DbContext> 接続に対して Entity Framework 実行戦略を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3abf7-106">But you need to enable the Entity Framework execution strategy for each <xref:Microsoft.EntityFrameworkCore.DbContext> connection if you want to have [resilient EF Core connections](/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="3abf7-107">たとえば、EF Core 接続レベルで次のコードを実行すると、接続が失敗した場合に再試行される回復力のある SQL 接続が有効になります。</span><span class="sxs-lookup"><span data-stu-id="3abf7-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="3abf7-108">BeginTransaction と複数の DbContext を使用した実行戦略と明示的なトランザクション</span><span class="sxs-lookup"><span data-stu-id="3abf7-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="3abf7-109">EF Core 接続で再試行を有効にすると、EF Core を使用して実行する各操作は、独自の再試行可能な操作になります。</span><span class="sxs-lookup"><span data-stu-id="3abf7-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="3abf7-110">一時的なエラーが発生した場合、`SaveChanges` への各クエリと各呼び出しは 1 つのユニットとして再試行されます。</span><span class="sxs-lookup"><span data-stu-id="3abf7-110">Each query and each call to `SaveChanges` will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="3abf7-111">一方、`BeginTransaction` を使用してトランザクションを開始するコードの場合、1 ユニットとして扱う必要のある独自の操作グループを定義しています。</span><span class="sxs-lookup"><span data-stu-id="3abf7-111">However, if your code initiates a transaction using `BeginTransaction`, you're defining your own group of operations that need to be treated as a unit.</span></span> <span data-ttu-id="3abf7-112">エラーが発生した場合は、トランザクション内のすべてをロールバックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3abf7-112">Everything inside the transaction has to be rolled back if a failure occurs.</span></span>

<span data-ttu-id="3abf7-113">EF 実行戦略 (再試行ポリシー) を使用しているときにそのトランザクションを実行しようとして、複数の DbContext から `SaveChanges` を呼び出すと、次のような例外を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3abf7-113">If you try to execute that transaction when using an EF execution strategy (retry policy) and you call `SaveChanges` from multiple DbContexts, you'll get an exception like this one:</span></span>

> <span data-ttu-id="3abf7-114">System.InvalidOperationException:構成された実行戦略 'SqlServerRetryingExecutionStrategy' は、ユーザーが開始したトランザクションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="3abf7-114">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="3abf7-115">'DbContext.Database.CreateExecutionStrategy()' から返された実行戦略を使用して、再試行可能なユニットとしてトランザクション内のすべての操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="3abf7-115">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="3abf7-116">この解決策では、実行する必要があるすべてを表すデリゲートを使用して EF 実行戦略を手動で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3abf7-116">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="3abf7-117">一時的なエラーが発生した場合、実行戦略によってデリゲートが再び呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3abf7-117">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="3abf7-118">たとえば、次のコードは、製品を更新し、別の DbContext を使用する必要がある ProductPriceChangedIntegrationEvent オブジェクトを保存するときに、2 つの DbContext (\_catalogContext と IntegrationEventLogContext) を使用して eShopOnContainers で実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3abf7-118">For example, the following code show how it's implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

```csharp
public async Task<IActionResult> UpdateProduct(
    [FromBody]CatalogItem productToUpdate)
{
    // Other code ...

    var oldPrice = catalogItem.Price;
    var raiseProductPriceChangedEvent = oldPrice != productToUpdate.Price;

    // Update current product
    catalogItem = productToUpdate;

    // Save product's data and publish integration event through the Event Bus
    // if price has changed
    if (raiseProductPriceChangedEvent)
    {
        //Create Integration Event to be published through the Event Bus
        var priceChangedEvent = new ProductPriceChangedIntegrationEvent(
          catalogItem.Id, productToUpdate.Price, oldPrice);

       // Achieving atomicity between original Catalog database operation and the
       // IntegrationEventLog thanks to a local transaction
       await _catalogIntegrationEventService.SaveEventAndCatalogContextChangesAsync(
           priceChangedEvent);

       // Publish through the Event Bus and mark the saved event as published
       await _catalogIntegrationEventService.PublishThroughEventBusAsync(
           priceChangedEvent);
    }
    // Just save the updated product because the Product's Price hasn't changed.
    else
    {
        await _catalogContext.SaveChangesAsync();
    }
}
```

<span data-ttu-id="3abf7-119">最初の <xref:Microsoft.EntityFrameworkCore.DbContext> は `_catalogContext` であり、2 つ目の `DbContext` は `_catalogIntegrationEventService` オブジェクト内にあります。</span><span class="sxs-lookup"><span data-stu-id="3abf7-119">The first <xref:Microsoft.EntityFrameworkCore.DbContext> is `_catalogContext` and the second `DbContext` is within the `_catalogIntegrationEventService` object.</span></span> <span data-ttu-id="3abf7-120">Commit アクションは、EF 実行戦略を使用してすべての `DbContext` オブジェクト全体で実行されます。</span><span class="sxs-lookup"><span data-stu-id="3abf7-120">The Commit action is performed across all `DbContext` objects using an EF execution strategy.</span></span>

<span data-ttu-id="3abf7-121">この複数の `DbContext` コミットを達成するために、次のコード例に示すように、`SaveEventAndCatalogContextChangesAsync` には `ResilientTransaction` クラスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3abf7-121">To achieve this multiple `DbContext` commit, the `SaveEventAndCatalogContextChangesAsync` uses a `ResilientTransaction` class, as shown in the following code:</span></span>

```csharp
public class CatalogIntegrationEventService : ICatalogIntegrationEventService
{
    //…
    public async Task SaveEventAndCatalogContextChangesAsync(
        IntegrationEvent evt)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        await ResilientTransaction.New(_catalogContext).ExecuteAsync(async () =>
        {
            // Achieving atomicity between original catalog database
            // operation and the IntegrationEventLog thanks to a local transaction
            await _catalogContext.SaveChangesAsync();
            await _eventLogService.SaveEventAsync(evt,
                _catalogContext.Database.CurrentTransaction.GetDbTransaction());
        });
    }
}
```

<span data-ttu-id="3abf7-122">基本的に、`ResilientTransaction.ExecuteAsync` メソッドでは、渡された `DbContext` (`_catalogContext`) からのトランザクションを開始し、次に `EventLogService` にそのトランザクションを使用して `IntegrationEventLogContext` からの変更を保存してから、トランザクション全体をコミットします。</span><span class="sxs-lookup"><span data-stu-id="3abf7-122">The `ResilientTransaction.ExecuteAsync` method basically begins a transaction from the passed `DbContext` (`_catalogContext`) and then makes the `EventLogService` use that transaction to save changes from the `IntegrationEventLogContext` and then commits the whole transaction.</span></span>

```csharp
public class ResilientTransaction
{
    private DbContext _context;
    private ResilientTransaction(DbContext context) =>
        _context = context ?? throw new ArgumentNullException(nameof(context));

    public static ResilientTransaction New (DbContext context) =>
        new ResilientTransaction(context);

    public async Task ExecuteAsync(Func<Task> action)
    {
        // Use of an EF Core resiliency strategy when using multiple DbContexts
        // within an explicit BeginTransaction():
        // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
        var strategy = _context.Database.CreateExecutionStrategy();
        await strategy.ExecuteAsync(async () =>
        {
            await using var transaction = await _context.Database.BeginTransactionAsync();
            await action();
            await transaction.CommitAsync();
        });
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="3abf7-123">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="3abf7-123">Additional resources</span></span>

- <span data-ttu-id="3abf7-124">**ASP.NET MVC アプリケーションの EF での接続回復性とコマンド傍受** </span><span class="sxs-lookup"><span data-stu-id="3abf7-124">**Connection Resiliency and Command Interception with EF in an ASP.NET MVC Application** </span></span>\
  [https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/connection-resiliency-and-command-interception-with-the-entity-framework-in-an-asp-net-mvc-application)

- <span data-ttu-id="3abf7-125">**Cesar de la Torre。回復力の高い Entity Framework Core SQL 接続とトランザクションの使用** </span><span class="sxs-lookup"><span data-stu-id="3abf7-125">**Cesar de la Torre. Using Resilient Entity Framework Core SQL Connections and Transactions** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/>

>[!div class="step-by-step"]
><span data-ttu-id="3abf7-126">[前へ](implement-retries-exponential-backoff.md)
>[次へ](use-httpclientfactory-to-implement-resilient-http-requests.md)</span><span class="sxs-lookup"><span data-stu-id="3abf7-126">[Previous](implement-retries-exponential-backoff.md)
[Next](use-httpclientfactory-to-implement-resilient-http-requests.md)</span></span>
