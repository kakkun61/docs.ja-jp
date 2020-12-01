---
ms.openlocfilehash: ae5a5fbf97ed4a03de7d35b9d5d5ca8de3aebc39
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032461"
---
### <a name="caching-responsecaching-pubternal-types-changed-to-internal"></a><span data-ttu-id="8216f-101">キャッシュ:ResponseCaching の "pubternal" 型を internal に変更</span><span class="sxs-lookup"><span data-stu-id="8216f-101">Caching: ResponseCaching "pubternal" types changed to internal</span></span>

<span data-ttu-id="8216f-102">ASP.NET Core 3.0 では、`ResponseCaching` の "pubternal" 型が `internal` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="8216f-102">In ASP.NET Core 3.0, "pubternal" types in `ResponseCaching` have been changed to `internal`.</span></span>

<span data-ttu-id="8216f-103">また、`IResponseCachingPolicyProvider` と `IResponseCachingKeyProvider` の既定の実装は、`AddResponseCaching` メソッドの一部としてサービスに追加されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8216f-103">In addition, default implementations of `IResponseCachingPolicyProvider` and `IResponseCachingKeyProvider` are no longer added to services as part of the `AddResponseCaching` method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8216f-104">変更の説明</span><span class="sxs-lookup"><span data-stu-id="8216f-104">Change description</span></span>

<span data-ttu-id="8216f-105">ASP.NET Core では、"pubternal" 型は `public` として宣言されますが、`.Internal` サフィックスが付加された名前空間に存在します。</span><span class="sxs-lookup"><span data-stu-id="8216f-105">In ASP.NET Core, "pubternal" types are declared as `public` but reside in a namespace suffixed with `.Internal`.</span></span> <span data-ttu-id="8216f-106">これらの型は public ですが、サポート ポリシーがなく、破壊的変更の対象となります。</span><span class="sxs-lookup"><span data-stu-id="8216f-106">While these types are public, they have no support policy and are subject to breaking changes.</span></span> <span data-ttu-id="8216f-107">残念ながら、これらの型が誤って使用されることが多かったため、これらのプロジェクトに破壊的変更が加えられ、フレームワークを維持する機能が制限されることになりました。</span><span class="sxs-lookup"><span data-stu-id="8216f-107">Unfortunately, accidental use of these types has been common, resulting in breaking changes to these projects and limiting the ability to maintain the framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8216f-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8216f-108">Version introduced</span></span>

<span data-ttu-id="8216f-109">3.0</span><span class="sxs-lookup"><span data-stu-id="8216f-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8216f-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="8216f-110">Old behavior</span></span>

<span data-ttu-id="8216f-111">これらの型は公開されていましたが、サポートされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="8216f-111">These types were publicly visible, but unsupported.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8216f-112">新しい動作</span><span class="sxs-lookup"><span data-stu-id="8216f-112">New behavior</span></span>

<span data-ttu-id="8216f-113">これらの型は `internal` になりました。</span><span class="sxs-lookup"><span data-stu-id="8216f-113">These types are now `internal`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8216f-114">変更理由</span><span class="sxs-lookup"><span data-stu-id="8216f-114">Reason for change</span></span>

<span data-ttu-id="8216f-115">`internal` スコープでは、サポートされていないポリシーが適切に反映されます。</span><span class="sxs-lookup"><span data-stu-id="8216f-115">The `internal` scope better reflects the unsupported policy.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8216f-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="8216f-116">Recommended action</span></span>

<span data-ttu-id="8216f-117">アプリまたはライブラリで使用される型をコピーします。</span><span class="sxs-lookup"><span data-stu-id="8216f-117">Copy types that are used by your app or library.</span></span>

#### <a name="category"></a><span data-ttu-id="8216f-118">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="8216f-118">Category</span></span>

<span data-ttu-id="8216f-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8216f-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8216f-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8216f-120">Affected APIs</span></span>

- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- <xref:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.%23ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedResponse`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.CachedVaryByRules`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCacheEntry`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.MemoryResponseCache`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingContext`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingKeyProvider`
- `T:Microsoft.AspNetCore.ResponseCaching.Internal.ResponseCachingPolicyProvider`
- `M:Microsoft.AspNetCore.ResponseCaching.ResponseCachingMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.ResponseCaching.ResponseCachingOptions},Microsoft.Extensions.Logging.ILoggerFactory,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingPolicyProvider,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCache,Microsoft.AspNetCore.ResponseCaching.Internal.IResponseCachingKeyProvider)",
"nameWithType": "ResponseCachingMiddleware.ResponseCachingMiddleware(RequestDelegate, IOptions<ResponseCachingOptions>, ILoggerFactory, IResponseCachingPolicyProvider, IResponseCache, IResponseCachingKeyProvider)`

-->
