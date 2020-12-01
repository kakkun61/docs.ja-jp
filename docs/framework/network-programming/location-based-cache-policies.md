---
title: 場所ベースのキャッシュ ポリシー
ms.date: 03/30/2017
helpviewer_keywords:
- Cache If Available policy
- reload policy
- location-based cache policies
- Cache Only policy
- local cache
- intermediate cache
- No Cache No Store policy
- cache [.NET Framework], location-based policies
- Revalidate policy
- freshness of cached resources
- Cache Or Next Cache Only policy
- Refresh policy
ms.assetid: e41d7f1a-0a6a-4dee-97d1-c6a8b6a07fc2
ms.openlocfilehash: 22d99111cd22ef24603f3cdd213c9c9afac5a974
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242202"
---
# <a name="location-based-cache-policies"></a><span data-ttu-id="afc56-102">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-102">Location-Based Cache Policies</span></span>

<span data-ttu-id="afc56-103">場所ベースのキャッシュ ポリシーでは、要求されたリソースを取得できる場所に基づいて、有効なキャッシュされたエントリの鮮度を定義します。</span><span class="sxs-lookup"><span data-stu-id="afc56-103">A location-based cache policy defines the freshness of valid cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="afc56-104">キャッシュされたリソースを使用しても、サーバーに指定されている再検証要件に違反しない場合、キャッシュされたリソースは有効です。</span><span class="sxs-lookup"><span data-stu-id="afc56-104">A cached resource is valid if using it does not does not violate server-specified revalidation requirements.</span></span> <span data-ttu-id="afc56-105">場所ベースのキャッシュ ポリシーをプログラムで作成するには、<xref:System.Net.Cache.RequestCachePolicy> または <xref:System.Net.Cache.HttpRequestCachePolicy> クラス コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="afc56-105">A location-based cache policy is created programmatically by using a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class constructor.</span></span> <span data-ttu-id="afc56-106">場所ベースのポリシーの種類は、<xref:System.Net.Cache.RequestCacheLevel> または <xref:System.Net.Cache.HttpRequestCacheLevel> 列挙値を使用してコンストラクターに渡されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-106">The type of location-based policy is passed to the constructor using a <xref:System.Net.Cache.RequestCacheLevel> or <xref:System.Net.Cache.HttpRequestCacheLevel> enumeration value.</span></span> <span data-ttu-id="afc56-107">場所ベースのキャッシュ ポリシーを作成するコード例については、「[How to: Set a Location-Based Cache Policy for an Application](how-to-set-a-location-based-cache-policy-for-an-application.md)」(方法: アプリケーションの場所ベースのキャッシュ ポリシーを設定する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afc56-107">For code examples that create location-based cache policies, see [How to: Set a Location-Based Cache Policy for an Application](how-to-set-a-location-based-cache-policy-for-an-application.md).</span></span> <span data-ttu-id="afc56-108">以下のセクションでは、ハイパーテキスト転送プロトコル (http と https) リソースに使用できる各種の場所ベースのキャッシュ ポリシーを定義します。</span><span class="sxs-lookup"><span data-stu-id="afc56-108">The following sections explain each type of location-based cache policy for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
## <a name="cache-if-available-policy"></a><span data-ttu-id="afc56-109">"利用可能ならキャッシュを使用" ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-109">Cache If Available Policy</span></span>  

 <span data-ttu-id="afc56-110">有効な要求されたリソースがローカル キャッシュ内にある場合、キャッシュされたリソースが使用されます。それ以外の場合、そのリソースの要求はサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-110">If a valid requested resource is in the local cache, the cached resource is used; otherwise, the request for the resource is sent to the server.</span></span> <span data-ttu-id="afc56-111">要求されたリソースがクライアントとサーバーの間の何らかのキャッシュ内にある場合、中間のキャッシュが要求を満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="afc56-111">If the requested resource is available in any cache between the client and the server, the request can be satisfied by an intermediate cache.</span></span>  
  
## <a name="cache-only-policy"></a><span data-ttu-id="afc56-112">"キャッシュのみを使用" ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-112">Cache Only Policy</span></span>  

 <span data-ttu-id="afc56-113">有効な要求されたリソースがローカル キャッシュ内にある場合、キャッシュされたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-113">If a valid requested resource is in the local cache, the cached resource is used.</span></span> <span data-ttu-id="afc56-114">このキャッシュ ポリシー レベルが指定された場合、項目がローカル キャッシュ内にない場合は <xref:System.Net.WebException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="afc56-114">When this cache policy level is specified, a <xref:System.Net.WebException> exception is thrown if the item is not in the local cache.</span></span>  
  
## <a name="cache-or-next-cache-only-policy"></a><span data-ttu-id="afc56-115">"キャッシュまたは次のキャッシュのみを使用" ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-115">Cache Or Next Cache Only Policy</span></span>  

 <span data-ttu-id="afc56-116">有効な要求されたリソースがローカル キャッシュ内にあるか、ローカル エリア ネットワーク上の中間キャッシュ内にある場合、キャッシュされたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-116">If a valid requested resource is in the local cache or an intermediate cache on the local area network, the cached resource is used.</span></span> <span data-ttu-id="afc56-117">このような操作を行わない場合、<xref:System.Net.WebException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="afc56-117">Otherwise, a <xref:System.Net.WebException> exception is thrown.</span></span> <span data-ttu-id="afc56-118">HTTP キャッシュ プロトコルの場合、only-if-cached キャッシュ コントロール ディレクティブを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-118">In the HTTP caching protocol, this is achieved using the only-if-cached cache control directive.</span></span>  
  
## <a name="no-cache-no-store-policy"></a><span data-ttu-id="afc56-119">"キャッシュを使用せず格納しない" ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-119">No Cache No Store Policy</span></span>  

 <span data-ttu-id="afc56-120">要求されたリソースはキャッシュ内からは使用されず、キャッシュには格納されません。</span><span class="sxs-lookup"><span data-stu-id="afc56-120">A requested resource is never used from any cache and is never placed in any cache.</span></span> <span data-ttu-id="afc56-121">要求されたリソースがローカル キャッシュ内にある場合は削除されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-121">If a requested resource is present in the local cache, it is removed.</span></span> <span data-ttu-id="afc56-122">このポリシー レベルは、リソースの削除も必要な中間キャッシュに指定します。</span><span class="sxs-lookup"><span data-stu-id="afc56-122">This policy level indicates to intermediate caches that they should also remove the resource.</span></span> <span data-ttu-id="afc56-123">HTTP キャッシュ プロトコルの場合、no-store キャッシュ コントロール ディレクティブを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-123">In the HTTP caching protocol, this is achieved using the no-store cache control directive.</span></span>  
  
## <a name="refresh-policy"></a><span data-ttu-id="afc56-124">更新ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-124">Refresh Policy</span></span>  

 <span data-ttu-id="afc56-125">要求されたリソースがサーバーから取得された場合、またはローカル キャッシュ以外のキャッシュで見つかった場合、その要求されたリソースを使用できます。</span><span class="sxs-lookup"><span data-stu-id="afc56-125">A requested resource can be used if it is obtained from the server or found in a cache other than the local cache.</span></span> <span data-ttu-id="afc56-126">中間キャッシュが要求を満たす前に、そのキャッシュは、サーバーに対してキャッシュされたエントリの再検証を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="afc56-126">Before the request can be satisfied by an intermediate cache, that cache must revalidate its cached entry with the server.</span></span> <span data-ttu-id="afc56-127">HTTP キャッシュ プロトコルの場合、max-age = 0 キャッシュ コントロール ディレクティブと、no-cache Pragma ヘッダーを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-127">In the HTTP caching protocol, this is achieved using the max-age = 0 cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="reload-policy"></a><span data-ttu-id="afc56-128">ポリシーの再読み込み</span><span class="sxs-lookup"><span data-stu-id="afc56-128">Reload Policy</span></span>  

 <span data-ttu-id="afc56-129">要求されたリソースは、サーバーから取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afc56-129">Requested resources must be obtained from the server.</span></span> <span data-ttu-id="afc56-130">リソースがローカル キャッシュに保存されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="afc56-130">The response might be saved in the local cache.</span></span> <span data-ttu-id="afc56-131">HTTP キャッシュ プロトコルの場合、no-cache キャッシュ コントロール ディレクティブと、no-cache Pragma ヘッダーを使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-131">In the HTTP caching protocol, this is achieved using the no-cache cache control directive and the no-cache Pragma header.</span></span>  
  
## <a name="revalidate-policy"></a><span data-ttu-id="afc56-132">再検証ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-132">Revalidate Policy</span></span>  

 <span data-ttu-id="afc56-133">キャッシュ内のリソースのコピーとサーバー上のコピーを比較します。</span><span class="sxs-lookup"><span data-stu-id="afc56-133">Compares the copy of the resource in the cache with the copy on the server.</span></span> <span data-ttu-id="afc56-134">サーバー上のコピーが新しい場合は、要求を満たすために使用され、キャッシュ内のコピーは置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="afc56-134">If the copy on the server is newer, it is used to satisfy the request and replaces the copy in the cache.</span></span> <span data-ttu-id="afc56-135">キャッシュ内のコピーがサーバー上のコピーと同じ場合、キャッシュされたコピーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-135">If the copy in the cache is the same as the server copy, the cached copy is used.</span></span> <span data-ttu-id="afc56-136">HTTP キャッシュ プロトコルの場合、条件付き要求を使用してこの処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="afc56-136">In the HTTP caching protocol, this is achieved using a conditional request.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc56-137">参照</span><span class="sxs-lookup"><span data-stu-id="afc56-137">See also</span></span>

- [<span data-ttu-id="afc56-138">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="afc56-138">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="afc56-139">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-139">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="afc56-140">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="afc56-140">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="afc56-141">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="afc56-141">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="afc56-142">\<requestCaching> 要素 (ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="afc56-142">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)
