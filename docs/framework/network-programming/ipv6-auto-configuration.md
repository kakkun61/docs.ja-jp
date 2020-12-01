---
title: IPv6 の自動構成
description: ノードが IPv6 ネットワークに参加し、人間の介入なしで設定されるノード Plug and Play が IPv6 でサポートされるしくみについて説明します。
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: db6156433e21411ff1e88634a359bbde7528fd91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258375"
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="ac556-103">IPv6 の自動構成</span><span class="sxs-lookup"><span data-stu-id="ac556-103">IPv6 Auto-Configuration</span></span>

<span data-ttu-id="ac556-104">IPv6 用の 1 つの重要な目標は、ノードのプラグ アンド プレイをサポートすることです。</span><span class="sxs-lookup"><span data-stu-id="ac556-104">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="ac556-105">つまり、IPv6 ネットワークにノードを接続して、それを人間の操作なしに自動的に構成できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac556-105">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="ac556-106">自動構成の種類</span><span class="sxs-lookup"><span data-stu-id="ac556-106">Type of Auto-Configuration</span></span>  

 <span data-ttu-id="ac556-107">IPv6 は、次の種類の自動構成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ac556-107">IPv6 supports the following types of auto-configuration:</span></span>  
  
- <span data-ttu-id="ac556-108">**ステートフルな自動構成**</span><span class="sxs-lookup"><span data-stu-id="ac556-108">**Stateful auto-configuration**.</span></span> <span data-ttu-id="ac556-109">この種類の構成では、ノードのインストールと管理のために IPv6 用動的ホスト構成プロトコル (DHCPv6) サーバーが必要なので、特定のレベルの人間の操作が必要です。</span><span class="sxs-lookup"><span data-stu-id="ac556-109">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="ac556-110">DHCPv6 サーバーは、構成情報を提供するノードのリストを保持します。</span><span class="sxs-lookup"><span data-stu-id="ac556-110">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="ac556-111">また、状態情報も保持するのでサーバーは、各アドレスがどのくらいの時間使用されているか、および再割り当てできるようになるタイミングを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="ac556-111">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
- <span data-ttu-id="ac556-112">**ステートレスな自動構成**</span><span class="sxs-lookup"><span data-stu-id="ac556-112">**Stateless auto-configuration**.</span></span> <span data-ttu-id="ac556-113">この種類の構成は、小規模な組織や個人に適しています。</span><span class="sxs-lookup"><span data-stu-id="ac556-113">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="ac556-114">この場合、各ホストは、受信したルーター アドバタイズの内容からそのアドレスを決定します。</span><span class="sxs-lookup"><span data-stu-id="ac556-114">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="ac556-115">IEEE EUI-64 標準を使用して、アドレスのネットワーク ID 部分を定義しますが、リンク上のホストアドレスの一意性を前提とすることは合理的です。</span><span class="sxs-lookup"><span data-stu-id="ac556-115">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="ac556-116">アドレスの決定方法に関係なく、ノードは、潜在的なアドレスがローカル リンクに対して一意であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac556-116">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="ac556-117">これは、潜在的なアドレスに近隣要請を送信することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="ac556-117">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="ac556-118">ノードが応答を受信する場合は、アドレスが既に使用されていて別のアドレスを決定する必要があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ac556-118">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="ac556-119">IPv6 モビリティ</span><span class="sxs-lookup"><span data-stu-id="ac556-119">IPv6 Mobility</span></span>  

 <span data-ttu-id="ac556-120">モバイル デバイスの普及により、新しい要件が導入されています。デバイスが IPv6 インターネット上の場所を任意に変更しても既存の接続を維持できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac556-120">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="ac556-121">この機能を提供するために、モバイル ノードに常に到達できるホーム アドレスが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="ac556-121">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="ac556-122">モバイル ノードが自宅にあるときは、ホーム リンクに接続し、ホーム アドレスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac556-122">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="ac556-123">モバイル ノードが自宅から離れた場所にあるときは、ホーム エージェント (通常はルーター) が、モバイル ノードと通信相手のノードの間でメッセージを中継します。</span><span class="sxs-lookup"><span data-stu-id="ac556-123">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac556-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac556-124">See also</span></span>

- [<span data-ttu-id="ac556-125">インターネット プロトコル バージョン 6</span><span class="sxs-lookup"><span data-stu-id="ac556-125">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)
- [<span data-ttu-id="ac556-126">ソケット</span><span class="sxs-lookup"><span data-stu-id="ac556-126">Sockets</span></span>](sockets.md)
