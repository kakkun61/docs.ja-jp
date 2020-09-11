---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811273"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="06a20-101">ミドルウェア:非推奨とマークされたデータベース エラー ページ</span><span class="sxs-lookup"><span data-stu-id="06a20-101">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="06a20-102">[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) とそれに関連付けられている拡張メソッドは ASP.NET Core 5.0 で非推奨としてマークされました。</span><span class="sxs-lookup"><span data-stu-id="06a20-102">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="06a20-103">このミドルウェアと拡張メソッドは ASP.NET Core 6.0 で削除されます。</span><span class="sxs-lookup"><span data-stu-id="06a20-103">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="06a20-104">この機能は代わりに `DatabaseDeveloperPageExceptionFilter` とその拡張メソッドによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="06a20-104">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="06a20-105">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06a20-105">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="06a20-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="06a20-106">Version introduced</span></span>

<span data-ttu-id="06a20-107">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="06a20-107">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="06a20-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="06a20-108">Old behavior</span></span>

<span data-ttu-id="06a20-109">`DatabaseErrorPageMiddleware` とそれに関連付けられている拡張メソッドは非推奨ではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="06a20-109">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="06a20-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="06a20-110">New behavior</span></span>

<span data-ttu-id="06a20-111">`DatabaseErrorPageMiddleware` とそれに関連付けられている拡張メソッドは非推奨です。</span><span class="sxs-lookup"><span data-stu-id="06a20-111">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="06a20-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="06a20-112">Reason for change</span></span>

<span data-ttu-id="06a20-113">`DatabaseErrorPageMiddleware` は、[開発者例外ページ](/aspnet/core/fundamentals/error-handling#developer-exception-page)の拡張可能 API に移行されました。</span><span class="sxs-lookup"><span data-stu-id="06a20-113">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="06a20-114">拡張可能 API の詳細については、GitHub イシュー [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06a20-114">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="06a20-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="06a20-115">Recommended action</span></span>

<span data-ttu-id="06a20-116">次の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="06a20-116">Complete the following steps:</span></span>

1. <span data-ttu-id="06a20-117">プロジェクトでの `DatabaseErrorPageMiddleware` の使用を停止してください。</span><span class="sxs-lookup"><span data-stu-id="06a20-117">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="06a20-118">たとえば、`Startup.Configure` から `UseDatabaseErrorPage` メソッド呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="06a20-118">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="06a20-119">開発者例外ページをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="06a20-119">Add the developer exception page to your project.</span></span> <span data-ttu-id="06a20-120">たとえば、`Startup.Configure` で <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="06a20-120">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="06a20-121">データベース開発者ページ例外フィルターをサービス コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="06a20-121">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="06a20-122">たとえば、`Startup.ConfigureServices` で `AddDatabaseDeveloperPageExceptionFilter` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="06a20-122">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a><span data-ttu-id="06a20-123">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="06a20-123">Category</span></span>

<span data-ttu-id="06a20-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="06a20-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06a20-125">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="06a20-125">Affected APIs</span></span>

- [<span data-ttu-id="06a20-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="06a20-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="06a20-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="06a20-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->