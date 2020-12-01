---
ms.openlocfilehash: 5741e8cdd51e00d5459c4c1032a56682429aab17
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032618"
---
### <a name="mvc-pubternal-types-changed-to-internal"></a><span data-ttu-id="3fae8-101">MVC:"pubternal" 型を internal に変更</span><span class="sxs-lookup"><span data-stu-id="3fae8-101">MVC: "Pubternal" types changed to internal</span></span>

<span data-ttu-id="3fae8-102">ASP.NET Core 3.0 では、MVC のすべての "pubternal" 型が、サポートされている名前空間で `public` になるか、必要に応じて `internal` になるように更新されました。</span><span class="sxs-lookup"><span data-stu-id="3fae8-102">In ASP.NET Core 3.0, all "pubternal" types in MVC were updated to either be `public` in a supported namespace or `internal` as appropriate.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3fae8-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="3fae8-103">Change description</span></span>

<span data-ttu-id="3fae8-104">ASP.NET Core では、"pubternal" 型は `public` として宣言されますが、`.Internal` サフィックスが付加された名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="3fae8-104">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a `.Internal`-suffixed namespace.</span></span> <span data-ttu-id="3fae8-105">これらの型は `public` ですが、サポート ポリシーがなく、破壊的変更の対象となります。</span><span class="sxs-lookup"><span data-stu-id="3fae8-105">While these types are `public`, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="3fae8-106">残念ながら、これらの型が誤って使用されることが多かったため、これらのプロジェクトに破壊的変更が加えられ、フレームワークを維持する機能が制限されることになりました。</span><span class="sxs-lookup"><span data-stu-id="3fae8-106">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3fae8-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="3fae8-107">Version introduced</span></span>

<span data-ttu-id="3fae8-108">3.0</span><span class="sxs-lookup"><span data-stu-id="3fae8-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3fae8-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="3fae8-109">Old behavior</span></span>

<span data-ttu-id="3fae8-110">MVC の一部の型は `public` でしたが、`.Internal` 名前空間に存在していました。</span><span class="sxs-lookup"><span data-stu-id="3fae8-110">Some types in MVC were `public` but in a `.Internal` namespace.</span></span> <span data-ttu-id="3fae8-111">これらの型にはサポート ポリシーがなく、破壊的変更の対象となりました。</span><span class="sxs-lookup"><span data-stu-id="3fae8-111">These types had no support policy and were subject to breaking changes.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3fae8-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="3fae8-112">New behavior</span></span>

<span data-ttu-id="3fae8-113">このような型はすべて、サポートされている名前空間で `public` になるか、`internal` としてマークされるように更新されます。</span><span class="sxs-lookup"><span data-stu-id="3fae8-113">All such types are updated either to be `public` in a supported namespace or marked as `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3fae8-114">変更理由</span><span class="sxs-lookup"><span data-stu-id="3fae8-114">Reason for change</span></span>

<span data-ttu-id="3fae8-115">"pubternal" 型が誤って使用されることが多かったため、これらのプロジェクトに破壊的変更が加えられ、フレームワークを維持する機能が制限されることになりました。</span><span class="sxs-lookup"><span data-stu-id="3fae8-115">Accidental use of the "pubternal" types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3fae8-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="3fae8-116">Recommended action</span></span>

<span data-ttu-id="3fae8-117">真に `public` になり、サポートされている新しい名前空間に移動された型を使用する場合は、新しい名前空間に一致するように参照を更新してください。</span><span class="sxs-lookup"><span data-stu-id="3fae8-117">If you're using types that have become truly `public` and have been moved into a new, supported namespace, update your references to match the new namespaces.</span></span>

<span data-ttu-id="3fae8-118">`internal` としてマークされるようになった型を使用する場合は、代替を見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="3fae8-118">If you're using types that have become marked as `internal`, you'll need to find an alternative.</span></span> <span data-ttu-id="3fae8-119">以前の "pubternal" 型は、一般的な使用ではサポートされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="3fae8-119">The previously "pubternal" types were never supported for public use.</span></span> <span data-ttu-id="3fae8-120">これらの名前空間に、アプリにとって重要な特定の型が存在する場合は、[dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) で問題を報告してください。</span><span class="sxs-lookup"><span data-stu-id="3fae8-120">If there are specific types in these namespaces that are critical to your apps, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span> <span data-ttu-id="3fae8-121">要求された型を `public` にするために検討される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3fae8-121">Considerations may be made for making the requested types `public`.</span></span>

#### <a name="category"></a><span data-ttu-id="3fae8-122">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="3fae8-122">Category</span></span>

<span data-ttu-id="3fae8-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3fae8-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3fae8-124">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="3fae8-124">Affected APIs</span></span>

<span data-ttu-id="3fae8-125">この変更には、次の名前空間の型が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3fae8-125">This change includes types in the following namespaces:</span></span>

- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`

-->
