---
title: データアクセスと管理
description: ASP.NET Web フォームおよびでデータにアクセスして処理する方法について説明し Blazor ます。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 11/20/2020
ms.openlocfilehash: 66e6001cbcac612cb556e90fb86fd694ca7d1459
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509755"
---
# <a name="work-with-data"></a><span data-ttu-id="ad59c-103">データの処理</span><span class="sxs-lookup"><span data-stu-id="ad59c-103">Work with data</span></span>

<span data-ttu-id="ad59c-104">データアクセスは、ASP.NET Web フォームアプリのバックボーンです。</span><span class="sxs-lookup"><span data-stu-id="ad59c-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="ad59c-105">Web 用のフォームを構築している場合、そのデータはどうなりますか。</span><span class="sxs-lookup"><span data-stu-id="ad59c-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="ad59c-106">Web フォームでは、データベースの操作に使用できるデータアクセス手法が複数ありました。</span><span class="sxs-lookup"><span data-stu-id="ad59c-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="ad59c-107">ソリューション エクスプローラー</span><span class="sxs-lookup"><span data-stu-id="ad59c-107">Data Sources</span></span>
- <span data-ttu-id="ad59c-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ad59c-108">ADO.NET</span></span>
- <span data-ttu-id="ad59c-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ad59c-109">Entity Framework</span></span>

<span data-ttu-id="ad59c-110">データソースは、Web フォームページ上に配置し、他のコントロールと同様に構成できるコントロールでした。</span><span class="sxs-lookup"><span data-stu-id="ad59c-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="ad59c-111">Visual Studio には、コントロールを構成して Web フォームページにバインドするための一連のダイアログボックスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ad59c-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="ad59c-112">"低コード" または "コードなし" のアプローチを利用している開発者は、Web フォームが最初にリリースされたときにこの手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ad59c-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![ソリューション エクスプローラー](media/data/datasources.png)

<span data-ttu-id="ad59c-114">ADO.NET は、データベースと対話するための低レベルのアプローチです。</span><span class="sxs-lookup"><span data-stu-id="ad59c-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="ad59c-115">アプリでは、操作のためのコマンド、レコードセット、およびデータセットを使用してデータベースへの接続を作成できます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="ad59c-116">結果は、コードを記述せずに画面上のフィールドにバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="ad59c-117">この方法の欠点は、ADO.NET オブジェクト (、、および) の各セットが、 `Connection` `Command` `Recordset` データベースベンダーによって提供されるライブラリにバインドされていることでした。</span><span class="sxs-lookup"><span data-stu-id="ad59c-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="ad59c-118">これらのコンポーネントを使用すると、コードが固定され、別のデータベースへの移行が困難になります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="ad59c-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ad59c-119">Entity Framework</span></span>

<span data-ttu-id="ad59c-120">Entity Framework (EF) は、.NET Foundation によって管理されるオープンソースのオブジェクトリレーショナルマッピングフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="ad59c-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="ad59c-121">.NET Framework と共に最初にリリースされた EF では、データベース接続、ストレージスキーマ、および相互作用のコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="ad59c-122">この抽象化により、アプリのビジネスルールに集中し、信頼されたデータベース管理者がデータベースを管理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="ad59c-123">.NET では、EF Core と呼ばれる更新バージョンの EF を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-123">In .NET, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="ad59c-124">EF Core は、コマンドラインツールを使用して使用できる一連のコマンドを使用して、コードとデータベースの間の対話を生成し、維持するのに役立ち `dotnet ef` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="ad59c-125">データベースを操作するためのいくつかのサンプルを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="ad59c-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="ad59c-126">EF Code First</span><span class="sxs-lookup"><span data-stu-id="ad59c-126">EF Code First</span></span>

<span data-ttu-id="ad59c-127">データベースとの対話の構築を簡単に開始するには、操作するクラスオブジェクトから開始する方法があります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="ad59c-128">EF には、クラスに適したデータベースコードを生成するためのツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ad59c-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="ad59c-129">このアプローチは、"Code First" の開発と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="ad59c-130">`Product`Microsoft SQL Server のようなリレーショナルデータベースに格納するサンプルストアアプリの場合は、次のクラスを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="ad59c-131">製品には主キーと、データベースに作成される3つの追加フィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="ad59c-132">EF では、 `Id` 規則によってプロパティが主キーとして識別されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="ad59c-133">`Name` は、テキストストレージ用に構成された列に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="ad59c-134">`[Required]`このプロパティを装飾する属性は、 `not null` プロパティのこの宣言された動作を強制するための制約を追加します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="ad59c-135">`Description` は、テキストストレージ用に構成された列に格納され、最大長は属性で指定された4000文字に設定され `[MaxLength]` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="ad59c-136">データベーススキーマは、 `MaxLength` データ型を使用してという名前の列で構成され `varchar(4000)` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="ad59c-137">`Price`プロパティは通貨として格納されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="ad59c-138">属性は、 `[Range]` 宣言された最小値と最大値の範囲外のデータストレージを防ぐために、適切な制約を生成します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="ad59c-139">この `Product` クラスは、データベースでの接続操作と変換操作を定義するデータベースコンテキストクラスに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="ad59c-140">クラスには、 `MyDbContext` クラスのアクセスと変換を定義する1つのプロパティが用意されて `Product` います。</span><span class="sxs-lookup"><span data-stu-id="ad59c-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="ad59c-141">アプリケーションでは、クラスのメソッドの次のエントリを使用して、データベースとの対話のためにこのクラスを構成し `Startup` `ConfigureServices` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="ad59c-142">上記のコードは、指定された接続文字列を使用して SQL Server データベースに接続します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="ad59c-143">appsettings.jsの接続文字列を、ファイル、環境変数、またはその他の構成ストレージの場所に配置し、この埋め込み文字列を適切 *に* 置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="ad59c-144">その後、次のコマンドを使用して、このクラスに適したデータベーステーブルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="ad59c-145">最初のコマンドは、という新しい EF 移行として、データベーススキーマに対して行っている変更を定義し `Create Product table` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="ad59c-146">移行では、新しいデータベースの変更を適用および削除する方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="ad59c-147">適用すると、データベースの単純な `Product` テーブルと、データベーススキーマの管理に役立つ新しいクラスがプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="ad59c-148">これらの生成されたクラスは、既定では、 *移行* という名前の新しいフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="ad59c-149">クラスに変更を加え `Product` たり、データベースと対話する関連クラスを追加したりする場合は、移行の新しい名前を指定してコマンドラインコマンドを再度実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="ad59c-150">このコマンドでは、データベーススキーマを更新するために別の一連の移行クラスが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="ad59c-151">EF Database First</span><span class="sxs-lookup"><span data-stu-id="ad59c-151">EF Database First</span></span>

<span data-ttu-id="ad59c-152">既存のデータベースの場合は、.NET コマンドラインツールを使用して EF Core のクラスを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="ad59c-153">クラスをスキャフォールディングするには、次のコマンドのバリエーションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="ad59c-154">上記のコマンドは、指定された接続文字列とプロバイダーを使用してデータベースに接続し `Microsoft.EntityFrameworkCore.SqlServer` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="ad59c-155">接続されると、という名前のデータベースコンテキストクラス `MyDbContext` が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="ad59c-156">また、 `Product` オプションで指定されたテーブルおよびテーブルに対してサポートクラスが作成され `Customer` `-t` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="ad59c-157">このコマンドには、データベースに適したクラス階層を生成するための多くの構成オプションがあります。</span><span class="sxs-lookup"><span data-stu-id="ad59c-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="ad59c-158">完全なリファレンスについては、 [コマンドのドキュメント](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad59c-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="ad59c-159">[EF Core](/ef/core/)の詳細については、Microsoft Docs サイトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad59c-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="ad59c-160">Web サービスとの対話</span><span class="sxs-lookup"><span data-stu-id="ad59c-160">Interact with web services</span></span>

<span data-ttu-id="ad59c-161">ASP.NET が最初にリリースされたときに、web サーバーとクライアントがデータを交換するために、SOAP サービスが推奨されていました。</span><span class="sxs-lookup"><span data-stu-id="ad59c-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="ad59c-162">その後、多くの変更が行われ、HTTP クライアントとの対話を直接行うためにサービスとの優先的なやり取りが行われています。</span><span class="sxs-lookup"><span data-stu-id="ad59c-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="ad59c-163">と ASP.NET Core を使用 Blazor すると、 `HttpClient` クラスのメソッドにの構成を登録でき `Startup` `ConfigureServices` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="ad59c-164">HTTP エンドポイントと対話する必要がある場合は、その構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="ad59c-165">次の構成コードを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="ad59c-166">GitHub からデータにアクセスする必要がある場合は常に、という名前のクライアントを作成 `github` します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="ad59c-167">クライアントはベースアドレスを使用して構成され、要求ヘッダーが適切に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="ad59c-168">`IHttpClientFactory` Blazor ディレクティブまたはプロパティの属性を使用して、をコンポーネントに挿入し `@inject` `[Inject]` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="ad59c-169">次の構文を使用して、名前付きクライアントを作成し、サービスと対話します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = await response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="ad59c-170">このメソッドは、 *dotnet/docs* GitHub リポジトリ内の問題のコレクションを記述する文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="ad59c-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="ad59c-171">JSON 形式でコンテンツを返し、適切な GitHub issue オブジェクトに逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="ad59c-172">事前に構成されたオブジェクトを配信するようにを構成するには、さまざまな方法があり `HttpClientFactory` `HttpClient` ます。</span><span class="sxs-lookup"><span data-stu-id="ad59c-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="ad59c-173">使用 `HttpClient` するさまざまな web サービスに対して、異なる名前とエンドポイントで複数のインスタンスを構成してみてください。</span><span class="sxs-lookup"><span data-stu-id="ad59c-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="ad59c-174">この方法では、これらのサービスとのやり取りを、各ページで簡単に操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ad59c-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="ad59c-175">詳細については、 [IHttpClientFactory のドキュメント](/aspnet/core/fundamentals/http-requests)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad59c-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ad59c-176">[前へ](forms-validation.md)
>[次へ](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="ad59c-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
