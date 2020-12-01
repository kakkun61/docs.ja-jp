---
title: キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長
ms.date: 03/30/2017
helpviewer_keywords:
- maximum staleness
- freshness of cached resources
- time, cached resources
- maximum age policy
- staleness of cached resources
- age of cached resources
ms.assetid: 7f775925-89a1-4956-ba90-c869c1749a94
ms.openlocfilehash: bdfa608b5169755b2b4daaaa26e562308ae2be01
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250607"
---
# <a name="cache-policy-interactionmaximum-age-and-maximum-staleness"></a><span data-ttu-id="13c81-102">キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長</span><span class="sxs-lookup"><span data-stu-id="13c81-102">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>

<span data-ttu-id="13c81-103">最新のコンテンツをクライアント アプリケーションに確実に返すために、クライアントのキャッシュ ポリシーとサーバーの再検証要件の相互作用によって、常に最も保守的なキャッシュ ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="13c81-104">このトピックの例はいずれも、1 月 1 日にキャッシュされ、1 月 4 日に期限切れになるリソースのキャッシュ ポリシーを示しています。</span><span class="sxs-lookup"><span data-stu-id="13c81-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="13c81-105">以下の例では、最大期限延長値 (`maxStale`) と最大有効期間 (`maxAge`) を組み合わせて使用しています。</span><span class="sxs-lookup"><span data-stu-id="13c81-105">In the following examples, the maximum staleness value (`maxStale`) is used in conjunction with a maximum age (`maxAge`):</span></span>  
  
- <span data-ttu-id="13c81-106">キャッシュ ポリシーで `maxAge` = 5 日間が設定され、`maxStale` 値が指定されていない場合は、`maxAge` 値に従い、コンテンツは 1 月 6 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="13c81-106">If the cache policy sets `maxAge` = 5 days and does not specify a `maxStale` value, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="13c81-107">ただし、サーバーの再検証要件に従い、コンテンツは 1 月 4 日に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="13c81-107">However, according to the server's revalidation requirements, the content expires on January 4.</span></span> <span data-ttu-id="13c81-108">コンテンツの有効期限の方が保守的 (早い) ので、`maxAge` ポリシーよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-108">Because the content expiration date is more conservative (sooner), it takes precedence over the `maxAge` policy.</span></span> <span data-ttu-id="13c81-109">そのため、コンテンツは 1 月 4 日に期限切れになり、最大有効期間に達していないとしても、必ず再検証されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-109">Therefore, the content expires on January 4 and must be revalidated even though its maximum age has not been reached.</span></span>  
  
- <span data-ttu-id="13c81-110">キャッシュ ポリシーで `maxAge` = 5 日間と `maxStale` = 3 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 6 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="13c81-110">If the cache policy sets `maxAge` = 5 days and `maxStale` = 3 days, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="13c81-111">`maxStale` 値に従い、コンテンツは 1 月 7 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="13c81-111">According to the `maxStale` value, the content is usable until January 7.</span></span> <span data-ttu-id="13c81-112">そのため、コンテンツは 1 月 6 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-112">Therefore, the content gets revalidated on January 6.</span></span>  
  
- <span data-ttu-id="13c81-113">キャッシュ ポリシーで `maxAge` = 5 日間と `maxStale` = 1 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 6 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="13c81-113">If the cache policy sets `maxAge` = 5 days and `maxStale` = 1 day, according to the `maxAge` value, the content is usable until January 6.</span></span> <span data-ttu-id="13c81-114">`maxStale` 値に従い、コンテンツは 1 月 5 日まで使用できます。</span><span class="sxs-lookup"><span data-stu-id="13c81-114">According to the `maxStale` value, the content is usable until January 5.</span></span> <span data-ttu-id="13c81-115">そのため、コンテンツは 1 月 5 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-115">Therefore, the content gets revalidated on January 5.</span></span>  
  
 <span data-ttu-id="13c81-116">最大有効期間がコンテンツの有効期限よりも短い場合、より保守的なキャッシュ動作が常に優先され、最大期限延長値の影響はありません。</span><span class="sxs-lookup"><span data-stu-id="13c81-116">When the maximum age is less than the content expiration date, the more conservative caching behavior always prevails and the maximum staleness value has no effect.</span></span> <span data-ttu-id="13c81-117">以下の例は、コンテンツの期限切れ前に最大有効期間 (`maxAge`) に達したときの最大期限延長 (`maxStale`) 値の影響を示しています。</span><span class="sxs-lookup"><span data-stu-id="13c81-117">The following examples illustrate the effect of setting a maximum staleness (`maxStale`) value when the maximum age (`maxAge`) is reached before the content expires:</span></span>  
  
- <span data-ttu-id="13c81-118">キャッシュ ポリシーで `maxAge` = 1 日間に設定され、`maxStale` 値が指定されていない場合、期限切れ前でも、コンテンツは 1 月 2 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-118">If the cache policy sets `maxAge` = 1 day and does not specify a value for `maxStale` value, the content is revalidated on January 2 even though it has not expired.</span></span>  
  
- <span data-ttu-id="13c81-119">キャッシュ ポリシーで `maxAge` = 1 日、`maxStale` = 3 日間が設定されている場合、より保守的なポリシー設定を適用するために、コンテンツは 1 月 2 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-119">If the cache policy sets `maxAge` = 1 day and `maxStale` = 3 days, the content is revalidated on January 2 to enforce the more conservative policy setting.</span></span>  
  
- <span data-ttu-id="13c81-120">キャッシュ ポリシーで `maxAge` = 1 日、`maxStale` = 1 日が設定されている場合、コンテンツは 1 月 2 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="13c81-120">If the cache policy sets `maxAge` = 1 day and `maxStale` = 1 day, the content is revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c81-121">参照</span><span class="sxs-lookup"><span data-stu-id="13c81-121">See also</span></span>

- [<span data-ttu-id="13c81-122">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="13c81-122">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="13c81-123">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="13c81-123">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="13c81-124">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="13c81-124">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="13c81-125">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="13c81-125">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="13c81-126">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="13c81-126">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="13c81-127">キャッシュ ポリシーの相互作用 - 最大有効期間と最小鮮度</span><span class="sxs-lookup"><span data-stu-id="13c81-127">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>](cache-policy-interaction-maximum-age-and-minimum-freshness.md)
