---
title: キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: d4182268341f4a4334a627fc8c9e24fa235f003f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287554"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="ff5a6-102">キャッシュ ポリシーの相互作用 — 最大有効期間と最小鮮度</span><span class="sxs-lookup"><span data-stu-id="ff5a6-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>

<span data-ttu-id="ff5a6-103">最新のコンテンツをクライアント アプリケーションに確実に返すために、クライアントのキャッシュ ポリシーとサーバーの再検証要件の相互作用によって、常に最も保守的なキャッシュ ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="ff5a6-104">このトピックの例はいずれも、1 月 1 日にキャッシュされ、1 月 4 日に期限切れになるリソースのキャッシュ ポリシーを示しています。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="ff5a6-105">以下の例は、最大有効期間 (`maxAge`) と最小鮮度 (`minFresh`) 値の相互作用の結果となるキャッシュ ポリシーを示しています。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="ff5a6-106">キャッシュ ポリシーで `maxAge` = 2 日間と設定され、`minFresh` が指定されていない場合、コンテンツは 1 月 3 日に再検証されます。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="ff5a6-107">キャッシュ ポリシーで `maxAge` = 2 日間と `minFresh` = 1 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 3 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="ff5a6-108">`minFresh` 値に従い、コンテンツは 1 月 3 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="ff5a6-109">そのため、コンテンツは 1 月 3 日に再検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="ff5a6-110">キャッシュ ポリシーで `maxAge` = 2 日間と `minFresh` = 2 日間が設定されている場合、`maxAge` 値に従い、コンテンツは 1 月 3 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="ff5a6-111">`minFresh` 値に従い、コンテンツは 1 月 2 日まで最新です。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="ff5a6-112">そのため、コンテンツは 1 月 2 日に再検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ff5a6-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5a6-113">参照</span><span class="sxs-lookup"><span data-stu-id="ff5a6-113">See also</span></span>

- [<span data-ttu-id="ff5a6-114">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="ff5a6-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="ff5a6-115">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="ff5a6-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="ff5a6-116">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="ff5a6-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="ff5a6-117">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="ff5a6-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="ff5a6-118">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="ff5a6-118">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="ff5a6-119">キャッシュ ポリシーの相互作用 — 最大有効期間と最大期限延長</span><span class="sxs-lookup"><span data-stu-id="ff5a6-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
