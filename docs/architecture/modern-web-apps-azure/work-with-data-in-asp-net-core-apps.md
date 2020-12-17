---
title: ASP.NET Core アプリでのデータの操作
description: ASP.NET Core および Azure での最新の Web アプリケーションの設計 | ASP.NET Core アプリでのデータの操作
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
no-loc:
- Blazor
- WebAssembly
ms.openlocfilehash: 9d85d700ecb8d6cbe7afd8d3c724f499ee5fed71
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851257"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="ee815-103">ASP.NET Core アプリでのデータの操作</span><span class="sxs-lookup"><span data-stu-id="ee815-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="ee815-104">"データは貴重なものであり、システム自体よりも長く存在します。"</span><span class="sxs-lookup"><span data-stu-id="ee815-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="ee815-105">Tim Berners-lee</span><span class="sxs-lookup"><span data-stu-id="ee815-105">Tim Berners-Lee</span></span>

<span data-ttu-id="ee815-106">データ アクセスは、ほぼすべてのソフトウェア アプリケーションの重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="ee815-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="ee815-107">ASP.NET Core は、Entity Framework Core (および Entity Framework 6 も) を含む、さまざまなデータ アクセス オプションをサポートし、どの .NET データ アクセス フレームワークでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="ee815-108">使用するデータ アクセス フレームワークの選択は、アプリケーションのニーズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ee815-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="ee815-109">ApplicationCore および UI プロジェクトからのこれらの選択を抽象化し、インフラストラクチャに実装の詳細をカプセル化することは、疎結合のテスト可能なソフトウェアの生成に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ee815-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="ee815-110">Entity Framework Core (リレーショナル データベース用)</span><span class="sxs-lookup"><span data-stu-id="ee815-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="ee815-111">リレーショナル データを操作する必要がある新しい ASP.NET Core アプリケーションを作成する場合、Entity Framework Core (EF Core) を使用して、アプリケーションからそのデータにアクセスすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ee815-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="ee815-112">EF Core はオブジェクト リレーショナル マッパー (O/RM) であり、.NET 開発者がデータ ソースのオブジェクトを保持できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ee815-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="ee815-113">これにより、通常は開発者が記述する必要があるほとんどのデータ アクセス コードが不要になります。</span><span class="sxs-lookup"><span data-stu-id="ee815-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="ee815-114">ASP.NET Core と同様、EF Core は、モジュラー型クロスプラットフォーム アプリケーションをサポートするために、完全に書き換えられました。</span><span class="sxs-lookup"><span data-stu-id="ee815-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="ee815-115">NuGet パッケージとしてご利用のアプリケーションに追加し、Startup で構成し、必要に応じて依存関係の挿入を介して要求します。</span><span class="sxs-lookup"><span data-stu-id="ee815-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="ee815-116">SQL Server データベースで EE Core を使用するには、次の dotnet CLI コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ee815-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="ee815-117">テストのために、InMemory データ ソースのサポートを追加するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee815-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="ee815-118">DbContext</span><span class="sxs-lookup"><span data-stu-id="ee815-118">The DbContext</span></span>

<span data-ttu-id="ee815-119">EF Core を操作するには、<xref:Microsoft.EntityFrameworkCore.DbContext> のサブクラスが必要です。</span><span class="sxs-lookup"><span data-stu-id="ee815-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="ee815-120">このクラスでは、ご利用のアプリケーションで操作するエンティティのコレクションを表すプロパティを保持します。</span><span class="sxs-lookup"><span data-stu-id="ee815-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="ee815-121">eShopOnWeb サンプルには、アイテム、ブランド、型のコレクションと共に CatalogContext が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee815-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="ee815-122">DbContext には、DbContextOptions を受け入れるコンストラクターが必要です。また、この引数を基本の DbContext コンストラクターに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="ee815-123">アプリケーションに DbContext を 1 つだけ含める場合は、DbContextOptions のインスタンスを渡すことができますが、複数含める場合は、汎用の DbContextOptions\<T> 型を使用し、汎用パラメーターとして DbContext 型を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="ee815-124">EF Core の構成</span><span class="sxs-lookup"><span data-stu-id="ee815-124">Configuring EF Core</span></span>

<span data-ttu-id="ee815-125">ASP.NET Core アプリケーションでは、通常、ConfigureServices メソッドで EF コアを構成します。</span><span class="sxs-lookup"><span data-stu-id="ee815-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="ee815-126">EF Core では、構成を効率化するいくつかの便利な拡張メソッドをサポートする、DbContextOptionsBuilder を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee815-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="ee815-127">Configuration で定義されている接続文字列で SQL Server データベースを使用するように CatalogContext を構成するには、次のコードを ConfigureServices に追加します。</span><span class="sxs-lookup"><span data-stu-id="ee815-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="ee815-128">メモリ内データベースを使用するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="ee815-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="ee815-129">EF Core をインストールして、DbContext の子の型を作成し、それを ConfigureServices で構成したら、EE Core を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="ee815-130">DbContext 型のインスタンスを必要とする任意のサービスで要求し、単にコレクション内にある場合と同じように、LINQ を使用して永続化されたエンティティの操作を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="ee815-131">EF Core では、ご利用のデータを格納して取得するために、LINQ 式を SQL クエリに変換する作業を行います。</span><span class="sxs-lookup"><span data-stu-id="ee815-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="ee815-132">図 8-1 に示すように、ロガーを構成し、そのレベルが少なくとも Information に設定されていることを確認することで、EF Core で実行されるクエリを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![コンソールへの EF Core クエリのログ記録](./media/image8-1.png)

<span data-ttu-id="ee815-134">**図 8-1**。</span><span class="sxs-lookup"><span data-stu-id="ee815-134">**Figure 8-1**.</span></span> <span data-ttu-id="ee815-135">コンソールへの EF Core クエリのログ記録</span><span class="sxs-lookup"><span data-stu-id="ee815-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="ee815-136">データのフェッチと格納</span><span class="sxs-lookup"><span data-stu-id="ee815-136">Fetching and storing Data</span></span>

<span data-ttu-id="ee815-137">EF Core からデータを取得するには、適切なプロパティにアクセスし、LINQ を使用して結果をフィルター処理します。</span><span class="sxs-lookup"><span data-stu-id="ee815-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="ee815-138">また、LINQ を使用して射影を実行し、1 つの型から別の型に結果を変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="ee815-139">次の例では、CatalogBrands を取得します。ここでは、名前で並べ替え、Enabled プロパティでフィルター処理し、SelectListItem 型に射影します。</span><span class="sxs-lookup"><span data-stu-id="ee815-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="ee815-140">上記の例では、クエリをすぐに実行するために、ToListAsync への呼び出しを追加することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ee815-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="ee815-141">それ以外の場合、ステートメントは IQueryable\<SelectListItem> を brandItems に割り当て、列挙されるまで実行されません。</span><span class="sxs-lookup"><span data-stu-id="ee815-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="ee815-142">メソッドから IQueryable 結果を返すことには長所と短所があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="ee815-143">EF Core で構築されるクエリをさらに変更できますが、EF Core で変換できないクエリに操作が追加された場合、実行時にのみ発生するエラーが発生する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="ee815-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="ee815-144">データ アクセスを実行するメソッドにすべてのフィルターを渡して、結果としてメモリ内コレクション (List\<T> など) を戻す方が一般的には安全です。</span><span class="sxs-lookup"><span data-stu-id="ee815-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="ee815-145">EF Core は、永続化からフェッチするエンティティの変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="ee815-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="ee815-146">追跡対象エンティティの変更を保存するには、DbContext で SaveChanges メソッドを呼び出すだけです。これで、エンティティのフェッチに使用されたものと同じ DbContext インスタンスであることが確認されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="ee815-147">エンティティの追加と削除は適切な DbSet プロパティで直接行います。この場合も、データベース コマンドを実行するために SaveChanges を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ee815-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="ee815-148">次の例では、永続化のエンティティの追加、更新、および削除を示します。</span><span class="sxs-lookup"><span data-stu-id="ee815-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="ee815-149">EF Core では、フェッチおよび保存のための同期と非同期の両方のメソッドがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ee815-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="ee815-150">Web アプリケーションでは、非同期メソッドで async/await パターンを使用することをお勧めします。これにより、データ アクセス操作が完了するのを待機している間に、Web サーバーのスレッドがブロックされなくなります。</span><span class="sxs-lookup"><span data-stu-id="ee815-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="ee815-151">関連データのフェッチ</span><span class="sxs-lookup"><span data-stu-id="ee815-151">Fetching related data</span></span>

<span data-ttu-id="ee815-152">EF Core は、エンティティの取得時に、データベースのそのエンティティを直接格納されているすべてのプロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="ee815-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="ee815-153">関連エンティティのリストなどの、ナビゲーション プロパティは設定されず、その値が null に設定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="ee815-154">このプロセスにより、EF Core は必要以上のデータをフェッチしなくなります。これは、効率的にすばやく要求を処理し、応答を返す必要がある Web アプリケーションで特に重要です。</span><span class="sxs-lookup"><span data-stu-id="ee815-154">This process ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="ee815-155">_一括読み込み_ を使用して、エンティティとのリレーションシップを含めるには、次のように、クエリで Include 拡張メソッドを使用してプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee815-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="ee815-156">複数のリレーションシップを含めることができます。また、ThenInclude を使用して、サブリレーションシップを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="ee815-157">EF Core は単一のクエリを実行して、エンティティの結果セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="ee815-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="ee815-158">あるいは、次のように '.' で区切った文字列を `.Include()` 拡張メソッドに渡すことで、ナビゲーション プロパティを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="ee815-159">この仕様はフィルタリング ロジックをカプセル化するだけでなく、データを入力するプロパティなど、返すデータのシェイプも指定できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="ee815-160">eShopOnWeb サンプルには、仕様内で一括読み込み情報のカプセル化を実演するいくつかの仕様が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee815-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="ee815-161">クエリの一部として仕様がどのように使用されるのかここで確認できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="ee815-162">関連データを読み込むために、_明示的読み込み_ を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="ee815-163">明示的読み込みを使用すれば、既に取得されているエンティティに追加データを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="ee815-164">この方法では、データベースに別の要求を行う必要があるため、要求ごとに行うデータベース ラウンドトリップの数を最小限に抑える必要がある Web アプリケーションにはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="ee815-164">Since this approach involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="ee815-165">_遅延読み込み_ は、アプリケーションでの参照時に関連データを自動的に読み込む機能です。</span><span class="sxs-lookup"><span data-stu-id="ee815-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="ee815-166">EF Core では、バージョン 2.1 で遅延読み込みのサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="ee815-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="ee815-167">遅延読み込みは既定では有効になりません。`Microsoft.EntityFrameworkCore.Proxies` をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="ee815-168">明示的読み込みと同様、遅延読み込みは通常、Web アプリケーションでは無効にする必要があります。遅延読み込みを使用すると、各 Web 要求内で追加のデータベース クエリが行われるためです。</span><span class="sxs-lookup"><span data-stu-id="ee815-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="ee815-169">待機時間が短く、テストに使用されるデータ セットが少量である場合、遅延読み込みによって発生するオーバーヘッドは、残念ながら開発時にはあまり気付かれません。</span><span class="sxs-lookup"><span data-stu-id="ee815-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when the latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="ee815-170">しかし、ユーザーやデータがより多く、待機時間がより長い運用環境では、追加のデータベース要求により、遅延読み込みを多用する Web アプリケーションのパフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="ee815-171">Web アプリケーションでのエンティティの遅延読み込みを回避する</span><span class="sxs-lookup"><span data-stu-id="ee815-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="ee815-172">データをカプセル化する</span><span class="sxs-lookup"><span data-stu-id="ee815-172">Encapsulating data</span></span>

<span data-ttu-id="ee815-173">EF Core は、モデルでその状態を正しくカプセル化するための機能をいくつか備えています。</span><span class="sxs-lookup"><span data-stu-id="ee815-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="ee815-174">ドメイン モデルでよくある問題として、コレクションのナビゲーション プロパティが一般にアクセス可能なリスト型として公開されることがあります。</span><span class="sxs-lookup"><span data-stu-id="ee815-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="ee815-175">この問題により、すべてのコラボレーターがこれらのコレクション型のコンテンツを操作できるようになり、結果として、コレクションに関係する重要なビジネス ルールが無視され、オブジェクトが無効な状態のままになるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="ee815-175">This problem allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="ee815-176">この問題の解決策は、関連するコレクションへの読み取り専用アクセスを公開することと、クライアントがこれらのコレクションを操作する方法を定義したメソッドを明示的に提供することです。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee815-176">The solution to this problem is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="ee815-177">このエンティティ型ではパブリックの `List` または `ICollection` プロパティが公開されず、代わりに、基になるリスト型をラップする `IReadOnlyCollection` 型が公開されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="ee815-178">このパターンを使用するとき、次のように、バッキング フィールドを使用するように Entity Framework Core に指示できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="ee815-179">ドメイン モデルを改善する別の方法としては、ID がなく、そのプロパティだけで区別される型に値オブジェクトを使用するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="ee815-180">エンティティのプロパティとしてこのような型を使用すると、ロジックはそれが属する値オブジェクトに固有となり、同じ概念を使用する複数のエンティティ間でロジックが重複することがありません。</span><span class="sxs-lookup"><span data-stu-id="ee815-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="ee815-181">Entity Framework Core では、次のように、所有されるエンティティとして型を構成することで、所有するエンティティと同じテーブルに値オブジェクトを保持できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="ee815-182">この例では、`ShipToAddress` プロパティの型は `Address` です。</span><span class="sxs-lookup"><span data-stu-id="ee815-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="ee815-183">`Address` は、`Street` や `City` など、いくつかのプロパティを持つ値オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="ee815-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="ee815-184">EF Core では、`Address` プロパティごとに 1 列の配分で `Order` オブジェクトがそのテーブルにマッピングされます。各列の名前の先頭にプロパティの名前が接頭辞として付きます。</span><span class="sxs-lookup"><span data-stu-id="ee815-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="ee815-185">この例で、`Order` テーブルに `ShipToAddress_Street` や `ShipToAddress_City` などの列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee815-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="ee815-186">必要に応じて、所有型を別のテーブルに格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="ee815-187">詳細については、[EF Core の所有エンティティのサポート](/ef/core/modeling/owned-entities)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee815-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="ee815-188">回復力のある接続</span><span class="sxs-lookup"><span data-stu-id="ee815-188">Resilient connections</span></span>

<span data-ttu-id="ee815-189">SQL データベースなどの外部リソースが使用できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="ee815-190">一時的に使用できなくなった場合、アプリケーションは再試行ロジックを使用して、例外の発生を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="ee815-191">この手法は一般的に _接続の復元性_ と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ee815-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="ee815-192">[指数バックオフを含む独自の再試行](/azure/architecture/patterns/retry)手法は、最大再試行回数に達するまで、指数関数的に増加する待機時間で再試行することで実装できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-192">You can implement your [own retry with exponential backoff](/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="ee815-193">この手法を使用すると、クラウドのリソースが短時間、断続的に使用できなくなるおそれがあり、その結果、一部の要求が失敗してしまいます。</span><span class="sxs-lookup"><span data-stu-id="ee815-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in the failure of some requests.</span></span>

<span data-ttu-id="ee815-194">Azure SQL DB の場合、Entity Framework Core に内部データベース接続の復元機能と再試行ロジックが既に用意されています。</span><span class="sxs-lookup"><span data-stu-id="ee815-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="ee815-195">ただし、回復力のある EF Core 接続を使用する場合は、各 DbContext 接続に対して Entity Framework 実行戦略を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="ee815-196">たとえば、EF Core 接続レベルで次のコードを実行すると、接続が失敗した場合に再試行される回復力のある SQL 接続が有効になります。</span><span class="sxs-lookup"><span data-stu-id="ee815-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30),
            errorNumbersToAdd: null);
        });
    });
}
//...
```

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="ee815-197">BeginTransaction と複数の DbContext を使用した実行戦略と明示的なトランザクション</span><span class="sxs-lookup"><span data-stu-id="ee815-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="ee815-198">EF Core 接続で再試行を有効にすると、EF Core を使用して実行する各操作は、独自の再試行可能な操作になります。</span><span class="sxs-lookup"><span data-stu-id="ee815-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="ee815-199">一時的なエラーが発生した場合、SaveChanges への各クエリと各呼び出しは 1 つのユニットとして再試行されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="ee815-200">一方、BeginTransaction を使用してトランザクションを開始するコードの場合、1 ユニットとして扱う必要のある独自の操作グループを定義しています。エラーが発生した場合、トランザクション内のすべてがロールバックされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="ee815-201">EF 実行戦略 (再試行ポリシー) を使用し、複数の DbContext からの SaveChanges をいくつかトランザクションに含める場合、そのトランザクションを実行しようとすると、次のような例外が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="ee815-202">System.InvalidOperationException:構成された実行戦略 'SqlServerRetryingExecutionStrategy' は、ユーザーが開始したトランザクションをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ee815-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="ee815-203">'DbContext.Database.CreateExecutionStrategy()' から返された実行戦略を使用して、再試行可能なユニットとしてトランザクション内のすべての操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ee815-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="ee815-204">この解決策では、実行する必要があるすべてを表すデリゲートを使用して EF 実行戦略を手動で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ee815-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="ee815-205">一時的なエラーが発生した場合、実行戦略によってデリゲートが再び呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="ee815-206">次のコードは、この方法を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ee815-206">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy();
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="ee815-207">最初の DbContext は \_catalogContext で、2 つ目の DbContext は \_integrationEventLogService オブジェクト内にあります。</span><span class="sxs-lookup"><span data-stu-id="ee815-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="ee815-208">最後に、Commit アクションが、複数の DbContext で EF 実行戦略を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="ee815-209">参照 – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="ee815-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="ee815-210">**EF Core ドキュメント**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="ee815-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="ee815-211">**EF Core: 関連データ**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="ee815-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="ee815-212">**ASPNET アプリケーションでのエンティティの遅延読み込みを回避する**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="ee815-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="ee815-213">EF Core または micro-ORM の選択</span><span class="sxs-lookup"><span data-stu-id="ee815-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="ee815-214">EF Core は、永続化を管理するための優れた選択肢であり、ほとんどの場合でアプリケーション開発者からデータベースの詳細をカプセル化することができますが、これが唯一の選択肢というわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ee815-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="ee815-215">もう 1 つの一般的なオープンソースの代替手段として、[Dapper](https://github.com/StackExchange/Dapper) (いわゆる micro-ORM) もあります。</span><span class="sxs-lookup"><span data-stu-id="ee815-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="ee815-216">micro-ORM はデータ構造にオブジェクトをマップするための軽量なツールであり、すべての機能が備わっているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="ee815-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="ee815-217">Dapper の場合、その設計目標は、データの取得と更新に使用される基になるクエリの完全なカプセル化ではなく、パフォーマンスに重点を置くことです。</span><span class="sxs-lookup"><span data-stu-id="ee815-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="ee815-218">開発者からの SQL が抽象化されないため、Dapper は "機械により近い" ものであり、開発者は特定のデータ アクセス操作で使用する正確なクエリを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="ee815-219">EF Core では 2 つの重要な機能が提供されます。これらは Dapper とは異なり、パフォーマンスのオーバーヘッドも増えます。</span><span class="sxs-lookup"><span data-stu-id="ee815-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="ee815-220">1 つ目は、LINQ 式から SQL への変換です。</span><span class="sxs-lookup"><span data-stu-id="ee815-220">The first is the translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="ee815-221">これらの変換はキャッシュされますが、それでも最初の実行時にオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="ee815-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="ee815-222">2 つ目は、エンティティの変更追跡です (効率的な更新ステートメントを生成できます)。</span><span class="sxs-lookup"><span data-stu-id="ee815-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="ee815-223">この動作は、<xref:System.Data.Entity.DbExtensions.AsNoTracking%2A> 拡張機能を使用することで、特定のクエリに対してオフにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-223">This behavior can be turned off for specific queries by using the <xref:System.Data.Entity.DbExtensions.AsNoTracking%2A> extension.</span></span> <span data-ttu-id="ee815-224">また、EF Core は、通常は非常に効率的で、パフォーマンスの観点から完全に受け入れ可能である場合に SQL クエリを生成します。ただし、実行する正確なクエリを微調整する必要がある場合は、EF Core を使用して、カスタム SQL を渡す (またはストアド プロシージャを実行する) こともできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="ee815-225">この場合も、Dapper はほんのわずかですが EE Core より優れています。</span><span class="sxs-lookup"><span data-stu-id="ee815-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="ee815-226">Julie Lerman は、2016 年 5 月の MSDN 記事「[Dapper、Entity Framework、およびハイブリッド アプリ](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps)」で一部のパフォーマンス データを提供しています。</span><span class="sxs-lookup"><span data-stu-id="ee815-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="ee815-227">さまざまなデータ アクセス方法の追加のパフォーマンス ベンチマーク データについては、[Dapper サイト](https://github.com/StackExchange/Dapper)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee815-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="ee815-228">EF Core と Dapper との構文の違いを確認するために、アイテム リストを取得する同じ方法の次の 2 つのバージョンについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ee815-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="ee815-229">Dapper でより複雑なオブジェクト グラフを作成する必要がある場合は、(EF Core の場合と同じように Include を追加するのではなく) 関連付けられているクエリを自分で記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="ee815-230">この機能は、複数のマップされたオブジェクトに個々の行をマップできる、マルチ マッピングという機能などのさまざまな構文で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-230">This functionality is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="ee815-231">たとえば、User という種類の Owner プロパティを指定した Post クラスの場合、次の SQL では必要なデータがすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="ee815-232">返された各行には、User と Post の両方のデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee815-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="ee815-233">User データを Owner プロパティを使用して Post データにアタッチする必要があるため、次の関数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="ee815-234">関連付けられているユーザー データが設定された Owner プロパティを使用してポストのコレクションを返すための完全なコード リストは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ee815-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="ee815-235">あまり優れたカプセル化は提供されないため、Dapper では、開発者がデータの格納方法と、データを効率的にクエリし、さらにコードを記述してフェッチする方法の詳細を把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="ee815-236">モデルが変更された場合、単に新しい移行を作成したり (EE Core の別の機能)、DbContext の 1 つの場所でマッピング情報を更新するのではなく、影響を受けるすべてのクエリを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="ee815-237">これらのクエリではコンパイル時間が保証されないため、モデルやデータベースの変更に応じて実行時に中断し、エラーの迅速な検出がより困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="ee815-238">これらのトレードオフと引き換えに、Dapper では非常に高速なパフォーマンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="ee815-239">ほとんどのアプリケーション、およびほぼすべてのアプリケーションのほとんどの部分に対して、EE Core は許容可能なパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee815-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="ee815-240">したがって、その開発者の生産性の利点が、そのパフォーマンスのオーバーヘッドを上回る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="ee815-241">キャッシュから利点を得られるクエリの場合、実際のクエリはごくわずかな時間にのみ実行され、比較的小さなクエリ パフォーマンスの違いが問題になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="ee815-242">SQL または NoSQL</span><span class="sxs-lookup"><span data-stu-id="ee815-242">SQL or NoSQL</span></span>

<span data-ttu-id="ee815-243">従来、SQL Server などのリレーショナル データベースが永続的なデータ記憶域のマーケットプレースの多くを占めますが、使用可能な唯一のソリューションではありません。</span><span class="sxs-lookup"><span data-stu-id="ee815-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="ee815-244">[MongoDB](https://www.mongodb.com/what-is-mongodb) などの NoSQL データベースでは、オブジェクトを格納するさまざまな方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="ee815-245">オブジェクトをテーブルと行にマップするのではなく、オブジェクト グラフ全体をシリアル化して、結果を格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="ee815-246">この方法の利点は、少なくとも最初は単純さとパフォーマンスとなります。</span><span class="sxs-lookup"><span data-stu-id="ee815-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="ee815-247">オブジェクトを、そのオブジェクトがデータベースから最後に取得されてから変更された可能性のある、リレーションシップ、更新、および行を持つ多くのテーブルに分解するよりも、キーを持つ単一のシリアル化されたオブジェクトを格納する方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="ee815-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="ee815-248">同様に、キーベースのストアから単一のオブジェクトをフェッチして逆シリアル化することは、リレーショナル データベースから同じオブジェクトを完全に構成するために必要な複雑な結合や複数のデータベース クエリよりも通常ははるかに速くて簡単です。</span><span class="sxs-lookup"><span data-stu-id="ee815-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="ee815-249">また、ロックやトランザクションあるいは固定スキーマがないため、NoSQL データベースは多くのコンピューターにわたるスケーリングに適しており、非常に大規模なデータセットをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="ee815-250">その一方で、NoSQL データベース (通常は呼び出し時に) には欠点があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="ee815-251">リレーショナル データベースでは、正規化を使用して整合性を適用し、データの重複を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="ee815-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="ee815-252">この方法により、データベースの合計サイズが小さくなり、共有データの更新がデータベース全体ですぐに使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ee815-252">This approach reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="ee815-253">リレーショナル データベースでは、Address テーブルによって、ID を使用して Country テーブルが参照される場合があります。国/地域の名前が変更された場合、アドレス レコードは更新プログラムの利点が得られ、それ自体の更新は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="ee815-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="ee815-254">ただし、NoSQL データベースでは、Address とそれに関連付けられている Country が、格納されている多くのオブジェクトの一部としてシリアル化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-254">However, in a NoSQL database, Address, and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="ee815-255">国/地域の名前を更新するには、単一行ではなく、すべてのオブジェクトを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="ee815-256">リレーショナル データベースでは、外部キーのようなルールを適用することで、リレーショナルの整合性を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="ee815-257">通常、NoSQL データベースでは、そのデータに対するこのような制約は提供されません。</span><span class="sxs-lookup"><span data-stu-id="ee815-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="ee815-258">NoSQL データベースで対処する必要があるもう 1 つの複雑なものとして、バージョン管理があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="ee815-259">オブジェクトのプロパティが変更された場合、格納された過去のバージョンから逆シリアル化できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="ee815-260">したがって、シリアル化された (以前の) バージョンのオブジェクトを持つ既存のすべてのオブジェクトを更新して、新しいスキーマに準拠する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="ee815-261">この方法は、スキーマの変更に更新スクリプトとマッピング更新が必要な場合がある、リレーショナル データベースとは概念的に異なります。</span><span class="sxs-lookup"><span data-stu-id="ee815-261">This approach is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="ee815-262">ただし、NoSQL の方法では多くの場合、変更する必要があるエントリの数がはるかに増えます。これは、データの重複が増えるためです。</span><span class="sxs-lookup"><span data-stu-id="ee815-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="ee815-263">NoSQL データベースには、リレーショナル データベースでは通常サポートされない固定スキーマなど、複数のバージョンのオブジェクトを格納できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="ee815-264">ただし、その場合、自分のアプリケーション コードに以前のバージョンのオブジェクトが存在することを考慮する必要があり、複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="ee815-264">However, in this case, your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="ee815-265">通常、NoSQL データベースでは [ACID](https://en.wikipedia.org/wiki/ACID) が適用されません。つまり、リレーショナル データベースよりもパフォーマンスとスケーラビリティの両方が優れています。</span><span class="sxs-lookup"><span data-stu-id="ee815-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="ee815-266">これは、正規化されたテーブル構造のストレージには適さない非常に大規模なデータセットとオブジェクトに最適です。</span><span class="sxs-lookup"><span data-stu-id="ee815-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="ee815-267">単一のアプリケーションでリレーショナル データベースと NoSQL データベースの両方 (それぞれ適宜使用) を利用できない理由はありません。</span><span class="sxs-lookup"><span data-stu-id="ee815-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="ee815-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="ee815-268">Azure Cosmos DB</span></span>

<span data-ttu-id="ee815-269">Azure Cosmos DB はフル マネージドの NoSQL データベース サービスであり、クラウドベースのスキーマレスなデータ ストレージを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee815-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="ee815-270">Azure Cosmos DB は、高速で予測可能なパフォーマンス、高可用性、エラスティック スケーリング、およびグローバル配布用に作成されています。</span><span class="sxs-lookup"><span data-stu-id="ee815-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="ee815-271">NoSQL データベースであるにもかかわらず、開発者は JSON データで豊富で使い慣れた SQL クエリ機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="ee815-272">Azure Cosmos DB のすべてのリソースは、JSON ドキュメントとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="ee815-273">リソースは、_アイテム_ (メタデータを含むドキュメント) および _フィード_ (アイテムのコレクション) として管理されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="ee815-274">図 8-2 は、さまざまな Azure Cosmos DB リソース間の関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="ee815-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![Azure Cosmos DB (NoSQL JSON データベース) のリソース間の階層関係](./media/image8-2.png)

<span data-ttu-id="ee815-276">**図 8-2**</span><span class="sxs-lookup"><span data-stu-id="ee815-276">**Figure 8-2.**</span></span> <span data-ttu-id="ee815-277">Azure Cosmos DB リソースの編成。</span><span class="sxs-lookup"><span data-stu-id="ee815-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="ee815-278">Azure Cosmos DB のクエリ言語は、JSON ドキュメントを照会するためのシンプルで強力なインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="ee815-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="ee815-279">言語では ANSI SQL 文法のサブセットがサポートされ、JavaScript のオブジェクト、配列、オブジェクトの構築、関数呼び出しと緊密に統合できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="ee815-280">**参照 – Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="ee815-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="ee815-281">Azure Cosmos DB の概要 <https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="ee815-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="ee815-282">その他の永続性オプション</span><span class="sxs-lookup"><span data-stu-id="ee815-282">Other persistence options</span></span>

<span data-ttu-id="ee815-283">リレーショナルおよび NoSQL ストレージ オプションに加え、ASP.NET Core アプリケーションでは Azure Storage を使用して、クラウドベースのスケーラブルな方法でさまざまなデータ形式とファイルを格納できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="ee815-284">Azure Storage は非常にスケーラブルであるため、最初に少量のデータを格納し、アプリケーションで必要になった場合に数百または数テラバイトのデータを格納するようにスケール アップできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="ee815-285">Azure Storage では次の 4 つの種類のデータがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ee815-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="ee815-286">非構造化テキストまたはバイナリ ストレージ用の Blob Storage。これは、オブジェクト ストレージとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ee815-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="ee815-287">行キーを使用してアクセス可能な、構造化データセット用の Table Storage。</span><span class="sxs-lookup"><span data-stu-id="ee815-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="ee815-288">信頼性の高いキューベースのメッセージング用の Queue Storage。</span><span class="sxs-lookup"><span data-stu-id="ee815-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="ee815-289">Azure 仮想マシンとオンプレミス アプリケーション間での共有ファイル アクセス用の File Storage。</span><span class="sxs-lookup"><span data-stu-id="ee815-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="ee815-290">**参照 – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="ee815-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="ee815-291">Azure Storage の概要 <https://docs.microsoft.com/azure/storage/common/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="ee815-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/common/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="ee815-292">キャッシュ</span><span class="sxs-lookup"><span data-stu-id="ee815-292">Caching</span></span>

<span data-ttu-id="ee815-293">Web アプリケーションでは、各 Web 要求をできるだけ短時間に完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="ee815-294">この機能を実現する 1 つの方法は、サーバーが要求を完了するために行う必要がある、外部呼出しの数を制限することです。</span><span class="sxs-lookup"><span data-stu-id="ee815-294">One way to achieve this functionality is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="ee815-295">キャッシュでは、サーバー (または、データ ソースよりクエリが簡単な別のデータ ストア) にデータのコピーを格納します。</span><span class="sxs-lookup"><span data-stu-id="ee815-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="ee815-296">Web アプリケーション、および特に非 SPA の従来の Web アプリケーションでは、要求ごとにユーザー インターフェイス全体を構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="ee815-297">この方法では、ユーザー要求のたびに同じ多数のデータベース クエリが何度も繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-297">This approach frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="ee815-298">ほとんどの場合、このデータはめったに変更されないため、データベースから常に要求する理由はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="ee815-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="ee815-299">ASP.NET Core では (ページ全体をキャッシュする) 応答キャッシュおよび (より詳細なキャッシュ動作をサポートする) データ キャッシュがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ee815-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="ee815-300">キャッシュを実装する場合、関心の分離に注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ee815-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="ee815-301">データ アクセス ロジック、またはユーザー インターフェイスでのキャッシュ ロジックの実装は避けてください。</span><span class="sxs-lookup"><span data-stu-id="ee815-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="ee815-302">代わりに、独自のクラスにキャッシュをカプセル化し、その動作を管理する構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="ee815-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="ee815-303">この方法は、開放/閉鎖および単一責任の原則に従っており、成長に伴う自分のアプリケーションのキャッシュの使用方法を管理しやすくします。</span><span class="sxs-lookup"><span data-stu-id="ee815-303">This approach follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="ee815-304">ASP.NET Core の応答キャッシュ</span><span class="sxs-lookup"><span data-stu-id="ee815-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="ee815-305">ASP.NET Core では、2 つのレベルの応答キャッシュがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ee815-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="ee815-306">最初のレベルではサーバーには何もキャッシュしませんが、応答をキャッシュするようにクライアントおよびプロキシ サーバーに指示する HTTP ヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="ee815-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="ee815-307">この機能は、個々のコントローラーまたはアクションに ResponseCache 属性を追加すると実装されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-307">This functionality is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="ee815-308">前の例では、応答に次のヘッダーが追加され、最大で 60 秒間、結果をキャッシュするようクライアントに指示します。</span><span class="sxs-lookup"><span data-stu-id="ee815-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="ee815-309">Cache-Control: public,max-age=60</span><span class="sxs-lookup"><span data-stu-id="ee815-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="ee815-310">サーバー側のメモリ内キャッシュをアプリケーションに追加するには、Microsoft.AspNetCore.ResponseCaching NuGet パッケージを参照し、応答キャッシュ ミドルウェアを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="ee815-311">このミドルウェは、Startup の ConfigureServices と Configure の両方で構成されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="ee815-312">応答キャッシュ ミドルウェアは、カスタマイズ可能な一連の条件に基づいて、自動的に応答をキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="ee815-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="ee815-313">既定では、GET または HEAD メソッドを使用して要求された 200 (OK) の応答のみがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="ee815-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="ee815-314">さらに、要求には、Cache-Control: public ヘッダーを含む応答が必要であり、Authorization や Set-Cookie のヘッダーを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="ee815-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="ee815-315">[応答キャッシュ ミドルウェアで使用されるキャッシュ条件の完全なリスト](/aspnet/core/performance/caching/middleware#conditions-for-caching)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee815-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="ee815-316">データ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="ee815-316">Data caching</span></span>

<span data-ttu-id="ee815-317">完全な Web 応答のキャッシュではなく (または、このようなキャッシュに加えて)、個々のデータ クエリの結果をキャッシュすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="ee815-318">この機能には、Web サーバーでメモリ内キャッシュを使用するか、[分散キャッシュ](/aspnet/core/performance/caching/distributed)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-318">For this functionality, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="ee815-319">このセクションでは、メモリ内キャッシュの実装方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ee815-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="ee815-320">次のように、ConfigureServices でメモリ (または分散) キャッシュのサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="ee815-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="ee815-321">必ず、Microsoft.Extensions.Caching.Memory NuGet パッケージも追加してください。</span><span class="sxs-lookup"><span data-stu-id="ee815-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="ee815-322">サービスを追加したら、キャッシュにアクセスする必要がある場合は常に、依存関係の挿入を使用して IMemoryCache を要求します。</span><span class="sxs-lookup"><span data-stu-id="ee815-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="ee815-323">この例では、CachedCatalogService で、基になる CatalogService 実装へのアクセスを制御する (または動作を追加する) ICatalogService の代替実装を提供して、プロキシ (またはデコレーター) 設計パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee815-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }

    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }

    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }

    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="ee815-324">キャッシュされたバージョンのサービスを使用するが、そのコンストラクターで必要になる CatalogService のインスタンスをサービスが引き続き取得できるようにアプリケーションを構成するには、ConfigureServices に以下の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="ee815-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following lines in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="ee815-325">このコードがあることで、カタログ データをフェッチするデータセット呼び出しは、要求ごとではなく、1 分に 1 回だけ行われるようになります。</span><span class="sxs-lookup"><span data-stu-id="ee815-325">With this code in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="ee815-326">サイトへのトラフィックによっては、データベースに対して行われるクエリの数と、このサービスによって公開されている 3 つのクエリすべてに現在依存しているホーム ページの平均ページ読み込み時間に、これが大きな影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="ee815-327">キャッシュの実装時に発生する問題は、"_古いデータ_" です。つまり、ソースで変更されても、その古いバージョンがキャッシュ内に残っているデータです。</span><span class="sxs-lookup"><span data-stu-id="ee815-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="ee815-328">この問題を軽減する簡単な方法は、キャッシュ期間を短くすることです。これは、ビジーなアプリケーションで、データのキャッシュ期間を長くすることで得られる利益が限定的であるためです。</span><span class="sxs-lookup"><span data-stu-id="ee815-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is a limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="ee815-329">たとえば、単一のデータベース クエリを実行し、1 秒ごとに 10 回要求されるページがあるとします。</span><span class="sxs-lookup"><span data-stu-id="ee815-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="ee815-330">このページが 1 分間キャッシュされると、1 分ごとに実行されるデータベース クエリの数は 600 から 1 に減り、99.8% の減少率となります。</span><span class="sxs-lookup"><span data-stu-id="ee815-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="ee815-331">代わりにキャッシュ期間を 1 時間にした場合、全体的な減少率は 99.997% となりますが、古いデータの確率的および潜在的な経過期間はどちらも大幅に増えます。</span><span class="sxs-lookup"><span data-stu-id="ee815-331">If instead the cache duration was made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="ee815-332">含まれているデータを更新する場合、事前にキャッシュ エントリを削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="ee815-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="ee815-333">キーがわかっている場合は、個々のエントリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="ee815-334">アプリケーションでキャッシュされているエントリを更新する機能が公開されている場合は、更新を実行するコードの対応するキャッシュ エントリを削除することができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="ee815-335">特定のデータ セットに依存する多くの異なるエントリが存在する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ee815-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="ee815-336">その場合は、CancellationChangeToken を使用して、キャッシュ エントリ間の依存関係を作成すると便利です。</span><span class="sxs-lookup"><span data-stu-id="ee815-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="ee815-337">CancellationChangeToken を使用すれば、トークンをキャンセルすることで一度に複数のキャッシュ エントリを期限切れにすることができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

<span data-ttu-id="ee815-338">キャッシュでは、データベースから同じ値を繰り返し要求する Web ページのパフォーマンスを大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="ee815-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="ee815-339">キャッシュを適用する前に、必ずデータ アクセスとページのパフォーマンスを測定し、改善の必要性があると判断した場合にのみ、キャッシュを適用するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ee815-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="ee815-340">キャッシュでは Web サーバーのメモリ リソースが消費され、アプリケーションの複雑さも増すため、この手法を使用して不完全な最適化を行わないことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ee815-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

## <a name="getting-data-to-no-locblazor-no-locwebassembly-apps"></a><span data-ttu-id="ee815-341">Blazor WebAssembly アプリにデータを取得する</span><span class="sxs-lookup"><span data-stu-id="ee815-341">Getting data to Blazor WebAssembly apps</span></span>

<span data-ttu-id="ee815-342">Blazor Server を使用するアプリを構築している場合は、この章でここまで説明してきたように、Entity Framework やその他の直接データ アクセス テクノロジを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-342">If you're building apps that use Blazor Server, you can use Entity Framework and other direct data access technologies as they've been discussed thus far in this chapter.</span></span> <span data-ttu-id="ee815-343">ところが、他の SPA フレームワークのように、Blazor WebAssembly アプリを構築する場合は、データ アクセスのための別の方法が必要になります。</span><span class="sxs-lookup"><span data-stu-id="ee815-343">However, when building Blazor WebAssembly apps, like other SPA frameworks, you will need a different strategy for data access.</span></span> <span data-ttu-id="ee815-344">通常、これらのアプリケーションによって、データ アクセスと Web API エンドポイントを介したサーバーとのやりとりが行われます。</span><span class="sxs-lookup"><span data-stu-id="ee815-344">Typically, these applications access data and interact with the server through web API endpoints.</span></span>

<span data-ttu-id="ee815-345">実行されるデータまたは操作の機密性が高い場合は、[前の章](develop-asp-net-core-mvc-apps.md)のセキュリティに関するセクションを確認し、承認されていないアクセスから API を保護してください。</span><span class="sxs-lookup"><span data-stu-id="ee815-345">If the data or operations being performed are sensitive, be sure to review the section on security in the [previous chapter](develop-asp-net-core-mvc-apps.md) and protect your APIs against unauthorized access.</span></span>

<span data-ttu-id="ee815-346">Blazor WebAssembly アプリの例は、BlazorAdmin プロジェクトの [eShopOnWeb 参照アプリケーション](https://github.com/dotnet-architecture/eShopOnWeb)内にあります。</span><span class="sxs-lookup"><span data-stu-id="ee815-346">You'll find an example of a Blazor WebAssembly app in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb), in the BlazorAdmin project.</span></span> <span data-ttu-id="ee815-347">このプロジェクトは eShopOnWeb Web プロジェクト内でホストされ、管理者グループのユーザーがストア内の項目を管理できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-347">This project is hosted within the eShopOnWeb Web project, and allows users in the Administrators group to manage the items in the store.</span></span> <span data-ttu-id="ee815-348">図 8-3 は、アプリケーションのスクリーンショットです。</span><span class="sxs-lookup"><span data-stu-id="ee815-348">You can see a screenshot of the application in Figure 8-3.</span></span>

![eShopOnWeb Catalog Admin スクリーンショット](./media/image8-3.jpg)

<span data-ttu-id="ee815-350">**図 8-3**</span><span class="sxs-lookup"><span data-stu-id="ee815-350">**Figure 8-3.**</span></span> <span data-ttu-id="ee815-351">eShopOnWeb Catalog Admin スクリーンショット。</span><span class="sxs-lookup"><span data-stu-id="ee815-351">eShopOnWeb Catalog Admin Screenshot.</span></span>

<span data-ttu-id="ee815-352">Blazor WebAssembly アプリ内の Web API からデータをフェッチする場合は、.NET アプリケーションの場合と同様に `HttpClient` のインスタンスを使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="ee815-352">When fetching data from web APIs within a Blazor WebAssembly app, you just use an instance of `HttpClient` as you would in any .NET application.</span></span> <span data-ttu-id="ee815-353">基本的な手順としては、送信する要求 (必要に応じて、通常は POST または PUT 要求用) を作成し、要求自体を待機して、ステータス コードを確認し、応答を逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="ee815-353">The basic steps involved are to create the request to send (if necessary, usually for POST or PUT requests), await the request itself, verify the status code, and deserialize the response.</span></span> <span data-ttu-id="ee815-354">API の特定のセットに対して行う要求の数が多い場合は、API をカプセル化し、`HttpClient` ベース アドレスを一元的に構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ee815-354">If you're going to make many requests to a given set of APIs, it's a good idea to encapsulate your APIs and configure the `HttpClient` base address centrally.</span></span> <span data-ttu-id="ee815-355">このようにすると、環境間でこれらの設定を調整する必要がある場合に 1 か所で変更するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="ee815-355">This way, if you need to adjust any of these settings between environments, you can make the changes in just one place.</span></span> <span data-ttu-id="ee815-356">このサービスのサポートを `Program.Main` に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-356">You should add support for this service in your `Program.Main`:</span></span>

```csharp
builder.Services.AddScoped(sp =>
    new HttpClient
    {
        BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)
    });
```

<span data-ttu-id="ee815-357">サービスに安全にアクセスする必要がある場合は、セキュリティで保護されたトークンにアクセスし、すべての要求でこのトークンを認証ヘッダーとして渡すように `HttpClient` を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee815-357">If you need to access services securely, you should access a secure token and configure the `HttpClient` to pass this token as an Authentication header with every request:</span></span>

```csharp
_httpClient.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", token);
```

<span data-ttu-id="ee815-358">この操作は、`Transient` の有効期間で `HttpClient` がアプリケーションのサービスに追加されていない場合に、`HttpClient` が挿入されているすべてのコンポーネントから実行できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-358">This activity can be done from any component that has the `HttpClient` injected into it, provided that `HttpClient` wasn't added to the application's services with a `Transient` lifetime.</span></span> <span data-ttu-id="ee815-359">アプリケーション内の `HttpClient` へのすべての参照が同じインスタンスを参照するため、1 つのコンポーネント内でそれを変更すると、アプリケーション全体にフローされます。</span><span class="sxs-lookup"><span data-stu-id="ee815-359">Every reference to `HttpClient` in the application references the same instance, so changes to it in one component flow through the entire application.</span></span> <span data-ttu-id="ee815-360">この認証チェックを実行する (続けてトークンを指定する) のに適した場所は、サイトのメイン ナビゲーションのような共有コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="ee815-360">A good place to perform this authentication check (followed by specifying the token) is in a shared component like the main navigation for the site.</span></span> <span data-ttu-id="ee815-361">このアプローチの詳細については、[eShopOnWeb 参照アプリケーション](https://github.com/dotnet-architecture/eShopOnWeb)の `BlazorAdmin` プロジェクトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee815-361">Learn more about this approach in the `BlazorAdmin` project in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

<span data-ttu-id="ee815-362">従来の JavaScript SPA に対するBlazor WebAssembly の利点の 1 つが、データ転送オブジェクト (DTO) のコピーを同期させておく必要がないことです。</span><span class="sxs-lookup"><span data-stu-id="ee815-362">One benefit of Blazor WebAssembly over traditional JavaScript SPAs is that you don't need to keep to copies of your data transfer objects(DTOs) synchronized.</span></span> <span data-ttu-id="ee815-363">Blazor WebAssembly プロジェクトと Web API プロジェクトはどちらも、共通の共有プロジェクトで同じ DTO を共有できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-363">Your Blazor WebAssembly project and your web API project can both share the same DTOs in a common shared project.</span></span> <span data-ttu-id="ee815-364">この方法により、SPA の開発に伴う摩擦の一部が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="ee815-364">This approach eliminates some of the friction involved in developing SPAs.</span></span>

<span data-ttu-id="ee815-365">API エンドポイントからデータを迅速に取得するには、組み込みのヘルパー メソッド `GetFromJsonAsync` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ee815-365">To quickly get data from an API endpoint, you can use the built-in helper method, `GetFromJsonAsync`.</span></span> <span data-ttu-id="ee815-366">同様のメソッドは、POST、PUT などにもあります。以下は、Blazor WebAssembly アプリで構成済みの `HttpClient` を使用して、API エンドポイントから CatalogItem を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ee815-366">There are similar methods for POST, PUT, etc. The following shows how to get a CatalogItem from an API endpoint using a configured `HttpClient` in a Blazor WebAssembly app:</span></span>

```csharp
var item = await _httpClient.GetFromJsonAsync<CatalogItem>($"catalog-items/{id}");
```

<span data-ttu-id="ee815-367">必要なデータが得られたら、通常はローカルで変更を追跡します。</span><span class="sxs-lookup"><span data-stu-id="ee815-367">Once you have the data you need, you'll typically track changes locally.</span></span> <span data-ttu-id="ee815-368">バックエンド データ ストアを更新する場合は、この目的のために追加の Web API を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ee815-368">When you want to make updates to the backend data store, you'll call additional web APIs for this purpose.</span></span>

<span data-ttu-id="ee815-369">**参照 – Blazor データ**</span><span class="sxs-lookup"><span data-stu-id="ee815-369">**References – Blazor Data**</span></span>

- <span data-ttu-id="ee815-370">ASP.NET Core Blazor から Web API を呼び出す</span><span class="sxs-lookup"><span data-stu-id="ee815-370">Call a web API from ASP.NET Core Blazor</span></span>
  <https://docs.microsoft.com/aspnet/core/blazor/call-web-api>

>[!div class="step-by-step"]
><span data-ttu-id="ee815-371">[前へ](develop-asp-net-core-mvc-apps.md)
>[次へ](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="ee815-371">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
