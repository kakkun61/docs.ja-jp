---
title: IPv6 のルーティング
ms.date: 03/30/2017
ms.assetid: c98731b4-b542-46a2-9947-1cea63c186b2
ms.openlocfilehash: 646eef4ec178472a99f60de4785fd53381296c3a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258336"
---
# <a name="ipv6-routing"></a><span data-ttu-id="89a54-102">IPv6 のルーティング</span><span class="sxs-lookup"><span data-stu-id="89a54-102">IPv6 Routing</span></span>

<span data-ttu-id="89a54-103">柔軟なルーティング メカニズムは、IPv6 の利点です。</span><span class="sxs-lookup"><span data-stu-id="89a54-103">A flexible routing mechanism is a benefit of IPv6.</span></span> <span data-ttu-id="89a54-104">IPv4 ネットワーク ID が割り当てられた方法のために、インターネット バックボーン上にあるルーターは大規模なルーティング テーブルを保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89a54-104">Due to the way in which IPv4 network IDs were and are allocated, large routing tables need to be maintained by the routers that are on the Internet backbones.</span></span> <span data-ttu-id="89a54-105">これらのルーターは、インターネット上の任意のノードに送られる可能性のあるパケットを転送するために、すべてのルートを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="89a54-105">These routers must know all the routes in order to forward packets that are potentially directed to any node on the Internet.</span></span> <span data-ttu-id="89a54-106">アドレスを集計する機能により、IPv6 では、柔軟なアドレス指定が可能であり、ルーティング テーブルのサイズを大幅に縮小することができます。</span><span class="sxs-lookup"><span data-stu-id="89a54-106">With its ability to aggregate addresses, IPv6 allows flexible addressing and drastically reduces the size of routing tables.</span></span> <span data-ttu-id="89a54-107">この新しいアドレス指定アーキテクチャでは、中間のルーターは、ネットワークのローカル部分だけを追跡すれば、メッセージを適切に転送できます。</span><span class="sxs-lookup"><span data-stu-id="89a54-107">In this new addressing architecture, intermediate routers must keep track only of the local portion of their network in order to forward the messages appropriately.</span></span>  
  
## <a name="neighbor-discovery"></a><span data-ttu-id="89a54-108">近隣探索</span><span class="sxs-lookup"><span data-stu-id="89a54-108">Neighbor Discovery</span></span>  

 <span data-ttu-id="89a54-109">近隣探索によって次の機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="89a54-109">Some of the features provided by Neighbor Discovery are:</span></span>  
  
- <span data-ttu-id="89a54-110">ルーター探索。</span><span class="sxs-lookup"><span data-stu-id="89a54-110">Router discovery.</span></span> <span data-ttu-id="89a54-111">これにより、ホストがローカル ルーターを識別できます。</span><span class="sxs-lookup"><span data-stu-id="89a54-111">This allows hosts to identify local routers.</span></span>  
  
- <span data-ttu-id="89a54-112">アドレス解決。</span><span class="sxs-lookup"><span data-stu-id="89a54-112">Address resolution.</span></span> <span data-ttu-id="89a54-113">これにより、ノードが対応する次ホップ アドレスのリンク層アドレス (アドレス解決プロトコル (ARP) の代替) を解決することができます。</span><span class="sxs-lookup"><span data-stu-id="89a54-113">This allows nodes to resolve a link-layer address for a corresponding next-hop address (a replacement for Address Resolution Protocol [ARP]).</span></span>  
  
- <span data-ttu-id="89a54-114">アドレスの自動構成。</span><span class="sxs-lookup"><span data-stu-id="89a54-114">Address auto-configuration.</span></span> <span data-ttu-id="89a54-115">これにより、ホストが、サイト ローカル アドレスおよびグローバル アドレスを自動的に構成することができます。</span><span class="sxs-lookup"><span data-stu-id="89a54-115">This allows hosts to automatically configure site-local and global addresses.</span></span>  
  
 <span data-ttu-id="89a54-116">近隣探索では、次のものを含む IPv6 のインターネット制御メッセージ プロトコル (ICMPv6) メッセージを使用します。</span><span class="sxs-lookup"><span data-stu-id="89a54-116">Neighbor Discovery uses Internet Control Message Protocol for IPv6 (ICMPv6) messages that include:</span></span>  
  
- <span data-ttu-id="89a54-117">ルーター アドバタイズ。</span><span class="sxs-lookup"><span data-stu-id="89a54-117">Router advertisement.</span></span> <span data-ttu-id="89a54-118">擬似定期的にまたはルーター要請に応じてルーターによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="89a54-118">Sent by a router on a pseudo-periodic basis or in response to a router solicitation.</span></span> <span data-ttu-id="89a54-119">IPv6 ルーターは、ルーター アドバタイズを使用して、その可用性、アドレス プレフィックス、およびその他のパラメーターをアドバタイズします。</span><span class="sxs-lookup"><span data-stu-id="89a54-119">IPv6 routers use router advertisements to advertise their availability, address prefixes, and other parameters.</span></span>  
  
- <span data-ttu-id="89a54-120">ルーター要請。</span><span class="sxs-lookup"><span data-stu-id="89a54-120">Router solicitation.</span></span> <span data-ttu-id="89a54-121">ホストによって送信され、リンク上のルーターがルーター アドバタイズをすぐに送信することを要求します。</span><span class="sxs-lookup"><span data-stu-id="89a54-121">Sent by a host to request that routers on the link send a router advertisement immediately.</span></span>  
  
- <span data-ttu-id="89a54-122">近隣要請。</span><span class="sxs-lookup"><span data-stu-id="89a54-122">Neighbor solicitation.</span></span> <span data-ttu-id="89a54-123">アドレス解決、重複アドレスの検出、または近隣ノードが到達可能であることを確認するためにノードによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="89a54-123">Sent by nodes for address resolution, duplicate address detection, or to verify that a neighbor is still reachable.</span></span>  
  
- <span data-ttu-id="89a54-124">近隣アドバタイズ。</span><span class="sxs-lookup"><span data-stu-id="89a54-124">Neighbor advertisement.</span></span> <span data-ttu-id="89a54-125">近隣要請に応答するかまたはリンク層アドレスの変更を近隣ノードに通知するために、ノードによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="89a54-125">Sent by nodes to respond to a neighbor solicitation or to notify neighbors of a change in link-layer address.</span></span>  
  
- <span data-ttu-id="89a54-126">リダイレクト。</span><span class="sxs-lookup"><span data-stu-id="89a54-126">Redirect.</span></span> <span data-ttu-id="89a54-127">送信元ノード向けに特定の宛先へのより良い次ホップ アドレスを示すために、ルーターによって送信されます。</span><span class="sxs-lookup"><span data-stu-id="89a54-127">Sent by routers to indicate a better next-hop address to a particular destination for a sending node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a54-128">参照</span><span class="sxs-lookup"><span data-stu-id="89a54-128">See also</span></span>

- [<span data-ttu-id="89a54-129">インターネット プロトコル バージョン 6</span><span class="sxs-lookup"><span data-stu-id="89a54-129">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="89a54-130">ソケット</span><span class="sxs-lookup"><span data-stu-id="89a54-130">Sockets</span></span>](sockets.md)
