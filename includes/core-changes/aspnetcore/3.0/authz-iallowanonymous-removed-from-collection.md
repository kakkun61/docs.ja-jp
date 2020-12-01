---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032468"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="98f68-101">承認:IAllowAnonymous が AuthorizationFilterContext.Filters から削除されました</span><span class="sxs-lookup"><span data-stu-id="98f68-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="98f68-102">ASP.NET Core 3.0 時点で、MVC は、コントローラーとアクション メソッドで検出された [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) 属性に対して [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) を追加しません。</span><span class="sxs-lookup"><span data-stu-id="98f68-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="98f68-103">この変更は、<xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute> の派生物についてはローカルに対処されますが、<xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> と <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> の実装では破壊的変更です。</span><span class="sxs-lookup"><span data-stu-id="98f68-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="98f68-104">[[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) 属性でラップするこのような実装は、構成と依存関係の挿入の両方が必要な場合に、厳密に型指定された属性ベースの承認を実現するための[一般的](https://stackoverflow.com/a/41348219/608220)でサポートされる方法です。</span><span class="sxs-lookup"><span data-stu-id="98f68-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="98f68-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="98f68-105">Version introduced</span></span>

<span data-ttu-id="98f68-106">3.0</span><span class="sxs-lookup"><span data-stu-id="98f68-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="98f68-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="98f68-107">Old behavior</span></span>

<span data-ttu-id="98f68-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> が [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) コレクションに表示されました。</span><span class="sxs-lookup"><span data-stu-id="98f68-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="98f68-109">このインターフェイスの存在をテストすることは、個々のコントローラー メソッドでフィルターをオーバーライドまたは無効にするための有効なアプローチでした。</span><span class="sxs-lookup"><span data-stu-id="98f68-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="98f68-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="98f68-110">New behavior</span></span>

<span data-ttu-id="98f68-111">`IAllowAnonymous` は `AuthorizationFilterContext.Filters` コレクションに表示されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="98f68-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="98f68-112">以前の動作に依存する `IAsyncAuthorizationFilter` の実装では、通常、HTTP 401 権限なしまたは HTTP 403 禁止応答が断続的に発生します。</span><span class="sxs-lookup"><span data-stu-id="98f68-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="98f68-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="98f68-113">Reason for change</span></span>

<span data-ttu-id="98f68-114">新しいエンドポイント ルーティング戦略が ASP.NET Core 3.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="98f68-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="98f68-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="98f68-115">Recommended action</span></span>

<span data-ttu-id="98f68-116">エンドポイント メタデータで `IAllowAnonymous`を検索します。</span><span class="sxs-lookup"><span data-stu-id="98f68-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="98f68-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="98f68-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="98f68-118">この手法の例については、[こちらの HasAllowAnonymous メソッド](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98f68-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="98f68-119">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="98f68-119">Category</span></span>

<span data-ttu-id="98f68-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="98f68-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="98f68-121">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="98f68-121">Affected APIs</span></span>

<span data-ttu-id="98f68-122">None</span><span class="sxs-lookup"><span data-stu-id="98f68-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
