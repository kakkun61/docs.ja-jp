---
title: キャッシュ ポリシー
description: 要求されたリソースのキャッシュ コピーを使用して要求を満たすことができるかどうかを決定するルールである、キャッシュ ポリシーについて学習します。
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- location-based cache policies
- cache [.NET Framework], policies
- request cache policies
- freshness of cached resources
- content cache policies
- expired content
ms.assetid: 1a7e04ec-7872-41c2-96c6-52566dcb412b
ms.openlocfilehash: 5492fd9f7b27f7546b951710e4b3e099a1d6664d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250594"
---
# <a name="cache-policy"></a><span data-ttu-id="b6358-103">キャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="b6358-103">Cache Policy</span></span>

<span data-ttu-id="b6358-104">キャッシュ ポリシーには、要求されたリソースのキャッシュ コピーを使用して要求を満たすことができるかどうかを決定するルールを定義します。</span><span class="sxs-lookup"><span data-stu-id="b6358-104">A cache policy defines rules that are used to determine whether a request can be satisfied using a cached copy of the requested resource.</span></span> <span data-ttu-id="b6358-105">アプリケーションは、更新のクライアント キャッシュ要件を指定しますが、実質的なキャッシュ ポリシーは、クライアントのキャッシュ要件、サーバーのコンテンツ有効期限要件、およびサーバーの再検証要件によって決まります。</span><span class="sxs-lookup"><span data-stu-id="b6358-105">Applications specify client cache requirements for freshness, but the effective cache policy is determined by the client cache requirements, the server's content expiration requirements, and the server's revalidation requirements.</span></span> <span data-ttu-id="b6358-106">最新のコンテンツをクライアント アプリケーションに確実に返すために、クライアントのキャッシュ ポリシーとサーバーの要件の相互作用によって、常に最も保守的なキャッシュ ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="b6358-106">The interaction of client cache policy and server requirements always results in the most conservative cache policy, to help ensure that the freshest content is returned to the client application.</span></span>  
  
 <span data-ttu-id="b6358-107">キャッシュ ポリシーは、場所ベースまたは時間ベースです。</span><span class="sxs-lookup"><span data-stu-id="b6358-107">Cache policies are either location-based or time-based.</span></span> <span data-ttu-id="b6358-108">場所ベースのキャッシュ ポリシーでは、要求されたリソースを取得できる場所に基づいて、キャッシュされたエントリの鮮度を定義します。</span><span class="sxs-lookup"><span data-stu-id="b6358-108">A location-based cache policy defines the freshness of cached entries based on where the requested resource can be taken from.</span></span> <span data-ttu-id="b6358-109">時間ベースのキャッシュ ポリシーは、リソースの取得時間、リソースと共に返されたヘッダー、現在時刻を利用し、キャッシュされているエントリの更新の確認間隔を定義します。</span><span class="sxs-lookup"><span data-stu-id="b6358-109">A time-based cache policy defines the freshness of cached entries using the time the resource was retrieved, headers returned with the resource, and the current time.</span></span> <span data-ttu-id="b6358-110">ほとんどのアプリケーションでは、既定の時間ベースのキャッシュ ポリシーを使用できます。時間ベースのキャッシュ ポリシーは、RFC 2616 ([インターネット技術標準化委員会 (IETF)](https://www.ietf.org/) Web サイトで入手可能) に規定されているキャッシュ ポリシーを実装しています。</span><span class="sxs-lookup"><span data-stu-id="b6358-110">Most applications can use the default time-based cache policy, which implements the caching policy specified in RFC 2616, available at [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website.</span></span>  
  
 <span data-ttu-id="b6358-111">次の表で説明されているクラスを使用して、キャッシュ ポリシーを指定します。</span><span class="sxs-lookup"><span data-stu-id="b6358-111">The classes described in the following table are used to specify cache policies.</span></span>  
  
|<span data-ttu-id="b6358-112">クラス名</span><span class="sxs-lookup"><span data-stu-id="b6358-112">Class name</span></span>|<span data-ttu-id="b6358-113">説明</span><span class="sxs-lookup"><span data-stu-id="b6358-113">Description</span></span>|  
|----------------|-----------------|  
|<xref:System.Net.Cache.HttpRequestCachePolicy>|<span data-ttu-id="b6358-114"><xref:System.Net.HttpWebRequest> オブジェクトを使用して要求されたリソースの場所ベースと時間ベースのキャッシュ ポリシーを表します。</span><span class="sxs-lookup"><span data-stu-id="b6358-114">Represents location-based and time-based cache policies for resources requested using <xref:System.Net.HttpWebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCachePolicy>|<span data-ttu-id="b6358-115"><xref:System.Net.WebRequest> オブジェクトを使用して要求されたリソースの場所ベースのキャッシュ ポリシーまたは <xref:System.Net.Cache.RequestCacheLevel.Default> 時間ベースのキャッシュ ポリシーを表します。</span><span class="sxs-lookup"><span data-stu-id="b6358-115">Represents location-based cache policies or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based cache policy for resources requested using <xref:System.Net.WebRequest> objects.</span></span>|  
|<xref:System.Net.Cache.HttpCacheAgeControl>|<span data-ttu-id="b6358-116">時間ベースの <xref:System.Net.Cache.HttpRequestCachePolicy> オブジェクトの作成に使用される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6358-116">Specifies values used to create time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.HttpRequestCacheLevel>|<span data-ttu-id="b6358-117">場所ベースと時間ベースの <xref:System.Net.Cache.HttpRequestCachePolicy> オブジェクトの作成に使用される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6358-117">Specifies values used to create location-based and time-based <xref:System.Net.Cache.HttpRequestCachePolicy> objects.</span></span>|  
|<xref:System.Net.Cache.RequestCacheLevel>|<span data-ttu-id="b6358-118">場所ベースまたは <xref:System.Net.Cache.RequestCacheLevel.Default> 時間ベースの <xref:System.Net.Cache.RequestCachePolicy> オブジェクトの作成に使用される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6358-118">Specifies values used to create location-based or the <xref:System.Net.Cache.RequestCacheLevel.Default> time-based <xref:System.Net.Cache.RequestCachePolicy> objects.</span></span>|  
  
 <span data-ttu-id="b6358-119">アプリケーションから発行されるすべての要求、または個々の要求に対してキャッシュ ポリシーを定義できます。</span><span class="sxs-lookup"><span data-stu-id="b6358-119">You can define a cache policy for all requests made by your application or for individual requests.</span></span> <span data-ttu-id="b6358-120">アプリケーションレベルのキャッシュ ポリシーと要求レベルのキャッシュ ポリシーの両方を指定すると、要求レベルのポリシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b6358-120">When you specify both an application-level cache policy and a request-level cache policy, the request-level policy is used.</span></span> <span data-ttu-id="b6358-121">アプリケーションレベルのキャッシュ ポリシーを指定するには、プログラム、またはアプリケーションやコンピューターの構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6358-121">You can specify an application-level cache policy programmatically or by using the application or machine configuration files.</span></span> <span data-ttu-id="b6358-122">詳細については、「[\<requestCaching> 要素 (ネットワーク設定)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6358-122">For more information, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
 <span data-ttu-id="b6358-123">キャッシュ ポリシーを作成するには、<xref:System.Net.Cache.RequestCachePolicy> クラスまたは <xref:System.Net.Cache.HttpRequestCachePolicy> クラスのインスタンスを作成して、ポリシー オブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6358-123">To create a cache policy, you must create a policy object by creating an instance of the <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> class.</span></span> <span data-ttu-id="b6358-124">要求でポリシーを指定するには、要求の <xref:System.Net.WebRequest.CachePolicy%2A> プロパティをポリシー オブジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="b6358-124">To specify the policy on a request, set the request's <xref:System.Net.WebRequest.CachePolicy%2A> property to the policy object.</span></span> <span data-ttu-id="b6358-125">アプリケーションレベルのポリシーをプログラムで設定する場合は、<xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> プロパティをポリシー オブジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="b6358-125">When setting an application-level policy programmatically, set the <xref:System.Net.HttpWebRequest.DefaultCachePolicy%2A> property to the policy object.</span></span>  
  
 <span data-ttu-id="b6358-126">キャッシュ ポリシーを作成し、利用する方法を示すコード例については、「[ネットワーク アプリケーションでのキャッシュの構成](configuring-caching-in-network-applications.md)」(ネットワーク アプリケーションでのキャッシュの構成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6358-126">For code examples that demonstrate creating and using cache policies, see [Configuring Caching in Network Applications](configuring-caching-in-network-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6358-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6358-127">See also</span></span>

- [<span data-ttu-id="b6358-128">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="b6358-128">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="b6358-129">場所ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="b6358-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="b6358-130">時間ベースのキャッシュ ポリシー</span><span class="sxs-lookup"><span data-stu-id="b6358-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="b6358-131">ネットワーク アプリケーションでのキャッシュの構成</span><span class="sxs-lookup"><span data-stu-id="b6358-131">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
