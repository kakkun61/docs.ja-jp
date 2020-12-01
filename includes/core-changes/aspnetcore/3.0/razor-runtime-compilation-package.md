---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032640"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="afcd6-101">Razor: 実行時コンパイルをパッケージに移動</span><span class="sxs-lookup"><span data-stu-id="afcd6-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="afcd6-102">Razor ビューおよび Razor Pages の実行時コンパイルのサポートが個別のパッケージに移動されました。</span><span class="sxs-lookup"><span data-stu-id="afcd6-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="afcd6-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="afcd6-103">Version introduced</span></span>

<span data-ttu-id="afcd6-104">3.0</span><span class="sxs-lookup"><span data-stu-id="afcd6-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="afcd6-105">以前の動作</span><span class="sxs-lookup"><span data-stu-id="afcd6-105">Old behavior</span></span>

<span data-ttu-id="afcd6-106">追加のパッケージを必要とせずに、実行時コンパイルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="afcd6-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="afcd6-107">新しい動作</span><span class="sxs-lookup"><span data-stu-id="afcd6-107">New behavior</span></span>

<span data-ttu-id="afcd6-108">この機能は [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) パッケージに移動されました。</span><span class="sxs-lookup"><span data-stu-id="afcd6-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="afcd6-109">次の API は、実行時コンパイルをサポートするために、以前は `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` で使用できました。</span><span class="sxs-lookup"><span data-stu-id="afcd6-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="afcd6-110">これらの API は、`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` を介して使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="afcd6-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="afcd6-111">`RazorViewEngineOptions.FileProviders` は、現在 `MvcRazorRuntimeCompilationOptions.FileProviders` です</span><span class="sxs-lookup"><span data-stu-id="afcd6-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="afcd6-112">`RazorViewEngineOptions.AdditionalCompilationReferences` は、現在 `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths` です</span><span class="sxs-lookup"><span data-stu-id="afcd6-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="afcd6-113">また、`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` が削除されました。</span><span class="sxs-lookup"><span data-stu-id="afcd6-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="afcd6-114">ファイルの変更時の再コンパイルは、`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` パッケージを参照することによって既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="afcd6-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="afcd6-115">変更理由</span><span class="sxs-lookup"><span data-stu-id="afcd6-115">Reason for change</span></span>

<span data-ttu-id="afcd6-116">この変更は、ASP.NET Core 共有フレームワークの Roslyn への依存関係を削除するために必要でした。</span><span class="sxs-lookup"><span data-stu-id="afcd6-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="afcd6-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="afcd6-117">Recommended action</span></span>

<span data-ttu-id="afcd6-118">Razor ファイルの実行時コンパイルまたは再コンパイルを必要とするアプリでは、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afcd6-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="afcd6-119">`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` パッケージへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="afcd6-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="afcd6-120">プロジェクトの `Startup.ConfigureServices` メソッドを更新して、`AddRazorRuntimeCompilation` の呼び出しを含めます。</span><span class="sxs-lookup"><span data-stu-id="afcd6-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="afcd6-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="afcd6-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="afcd6-122">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="afcd6-122">Category</span></span>

<span data-ttu-id="afcd6-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="afcd6-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="afcd6-124">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="afcd6-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
