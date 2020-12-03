---
title: '破壊的変更: 承認:エンドポイント ルーティングのリソースは HttpContext'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: 承認: エンドポイント ルーティングのリソースは HttpContext'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7c5a77cb8999c60a7780b9b4f7ad2a1c79fd8310
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760010"
---
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="b25e7-103">承認:エンドポイント ルーティングのリソースは HttpContext</span><span class="sxs-lookup"><span data-stu-id="b25e7-103">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="b25e7-104">ASP.NET Core 3.1 でエンドポイント ルーティングを使用する場合、承認に使用されるリソースはエンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="b25e7-104">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="b25e7-105">この方法は、ルート データ (<xref:Microsoft.AspNetCore.Routing.RouteData>) へのアクセスを付与するためには不十分でした。</span><span class="sxs-lookup"><span data-stu-id="b25e7-105">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="b25e7-106">MVC では以前、エンドポイント (<xref:Microsoft.AspNetCore.Http.Endpoint>) とルート データの両方にアクセスできるようにするため、<xref:Microsoft.AspNetCore.Http.HttpContext> リソースが渡されました。</span><span class="sxs-lookup"><span data-stu-id="b25e7-106">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="b25e7-107">この変更により、承認に渡されるリソースは常に `HttpContext` になります。</span><span class="sxs-lookup"><span data-stu-id="b25e7-107">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b25e7-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b25e7-108">Version introduced</span></span>

<span data-ttu-id="b25e7-109">5.0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="b25e7-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="b25e7-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="b25e7-110">Old behavior</span></span>

<span data-ttu-id="b25e7-111">エンドポイント ルーティングと承認ミドルウェア (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) または [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) 属性を使用する場合、承認に渡されるリソースは一致するエンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="b25e7-111">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="b25e7-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="b25e7-112">New behavior</span></span>

<span data-ttu-id="b25e7-113">`HttpContext` がエンドポイント ルーティングから承認に渡されます。</span><span class="sxs-lookup"><span data-stu-id="b25e7-113">Endpoint routing passes the `HttpContext` to authorization.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b25e7-114">変更理由</span><span class="sxs-lookup"><span data-stu-id="b25e7-114">Reason for change</span></span>

<span data-ttu-id="b25e7-115">`HttpContext` からエンドポイントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b25e7-115">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="b25e7-116">一方で、エンドポイントからルート データなどにアクセスする方法はありませんでした。</span><span class="sxs-lookup"><span data-stu-id="b25e7-116">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="b25e7-117">エンドポイント以外のルーティングからの機能に不足がありました。</span><span class="sxs-lookup"><span data-stu-id="b25e7-117">There was a loss in functionality from non-endpoint routing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b25e7-118">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="b25e7-118">Recommended action</span></span>

<span data-ttu-id="b25e7-119">アプリでエンドポイント リソースが使用される場合は、`HttpContext` で <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> を呼び出して、エンドポイントへのアクセスを継続します。</span><span class="sxs-lookup"><span data-stu-id="b25e7-119">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="b25e7-120">ASP.NET Core 5.0 Preview 8 以降では、<xref:System.AppContext.SetSwitch%2A> を使用して以前の動作に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="b25e7-120">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="b25e7-121">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b25e7-121">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a><span data-ttu-id="b25e7-122">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b25e7-122">Affected APIs</span></span>

<span data-ttu-id="b25e7-123">None</span><span class="sxs-lookup"><span data-stu-id="b25e7-123">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
