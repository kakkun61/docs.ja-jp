---
title: 破壊的変更:ミドルウェア:非推奨とマークされたデータベース エラー ページ
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: ミドルウェア:非推奨とマークされたデータベース エラー ページ'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f828b5e20c2a9a709d675e435caa99727aebd5b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759897"
---
# <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="85c51-103">ミドルウェア:非推奨とマークされたデータベース エラー ページ</span><span class="sxs-lookup"><span data-stu-id="85c51-103">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="85c51-104">[DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) とそれに関連付けられている拡張メソッドは ASP.NET Core 5.0 で非推奨としてマークされました。</span><span class="sxs-lookup"><span data-stu-id="85c51-104">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="85c51-105">このミドルウェアと拡張メソッドは ASP.NET Core 6.0 で削除されます。</span><span class="sxs-lookup"><span data-stu-id="85c51-105">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="85c51-106">この機能は代わりに `DatabaseDeveloperPageExceptionFilter` とその拡張メソッドによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="85c51-106">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="85c51-107">ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85c51-107">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="85c51-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="85c51-108">Version introduced</span></span>

<span data-ttu-id="85c51-109">5.0 RC 1</span><span class="sxs-lookup"><span data-stu-id="85c51-109">5.0 RC 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="85c51-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="85c51-110">Old behavior</span></span>

<span data-ttu-id="85c51-111">`DatabaseErrorPageMiddleware` とそれに関連付けられている拡張メソッドは非推奨ではありませんでした。</span><span class="sxs-lookup"><span data-stu-id="85c51-111">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="85c51-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="85c51-112">New behavior</span></span>

<span data-ttu-id="85c51-113">`DatabaseErrorPageMiddleware` とそれに関連付けられている拡張メソッドは非推奨です。</span><span class="sxs-lookup"><span data-stu-id="85c51-113">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="85c51-114">変更理由</span><span class="sxs-lookup"><span data-stu-id="85c51-114">Reason for change</span></span>

<span data-ttu-id="85c51-115">`DatabaseErrorPageMiddleware` は、[開発者例外ページ](/aspnet/core/fundamentals/error-handling#developer-exception-page)の拡張可能 API に移行されました。</span><span class="sxs-lookup"><span data-stu-id="85c51-115">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="85c51-116">拡張可能 API の詳細については、GitHub イシュー [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="85c51-116">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="85c51-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="85c51-117">Recommended action</span></span>

<span data-ttu-id="85c51-118">次の手順のようにします。</span><span class="sxs-lookup"><span data-stu-id="85c51-118">Complete the following steps:</span></span>

1. <span data-ttu-id="85c51-119">プロジェクトでの `DatabaseErrorPageMiddleware` の使用を停止してください。</span><span class="sxs-lookup"><span data-stu-id="85c51-119">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="85c51-120">たとえば、`Startup.Configure` から `UseDatabaseErrorPage` メソッド呼び出しを削除します。</span><span class="sxs-lookup"><span data-stu-id="85c51-120">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="85c51-121">開発者例外ページをプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="85c51-121">Add the developer exception page to your project.</span></span> <span data-ttu-id="85c51-122">たとえば、`Startup.Configure` で <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="85c51-122">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="85c51-123">プロジェクト ファイルに [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="85c51-123">Add the [Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore](https://www.nuget.org/packages/Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore) NuGet package to the project file.</span></span>

1. <span data-ttu-id="85c51-124">データベース開発者ページ例外フィルターをサービス コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="85c51-124">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="85c51-125">たとえば、`Startup.ConfigureServices` で `AddDatabaseDeveloperPageExceptionFilter` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="85c51-125">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

## <a name="affected-apis"></a><span data-ttu-id="85c51-126">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="85c51-126">Affected APIs</span></span>

- [<span data-ttu-id="85c51-127">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="85c51-127">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="85c51-128">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span><span class="sxs-lookup"><span data-stu-id="85c51-128">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
