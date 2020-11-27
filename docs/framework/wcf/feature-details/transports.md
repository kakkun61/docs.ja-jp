---
title: Windows Communication Foundation のトランスポート
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 8623b788b848867f25836a657b07349dd50c2780
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251686"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="7a616-102">Windows Communication Foundation のトランスポート</span><span class="sxs-lookup"><span data-stu-id="7a616-102">Transports in Windows Communication Foundation</span></span>

<span data-ttu-id="7a616-103">トランスポート層は、チャネル スタックの最も低いレベルにあります。</span><span class="sxs-lookup"><span data-stu-id="7a616-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="7a616-104">Windows Communication Foundation (WCF) で使用される主なトランスポートは、HTTP、HTTPS、TCP、および名前付きパイプです。</span><span class="sxs-lookup"><span data-stu-id="7a616-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="7a616-105">このセクションのトピックでは、このようなトランスポートの選択、トランスポートの構成、およびチューニング プロパティの設定について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="7a616-106">WCF には、追加のトランスポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7a616-106">WCF includes additional transports.</span></span> <span data-ttu-id="7a616-107">メッセージキュー (MSMQ) トランスポートの詳細については、「 [キューと信頼できるセッション](queues-and-reliable-sessions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a616-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="7a616-108">ピアツーピアトランスポートの詳細については、「 [ピアツーピアネットワーク](peer-to-peer-networking.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a616-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a616-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7a616-109">In This Section</span></span>  

 [<span data-ttu-id="7a616-110">トランスポートの選択</span><span class="sxs-lookup"><span data-stu-id="7a616-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="7a616-111">3 つの主なトランスポートについて説明し、そのうちの 1 つを選択する際の考慮事項を示します。</span><span class="sxs-lookup"><span data-stu-id="7a616-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="7a616-112">メッセージ エンコーダーを選択する</span><span class="sxs-lookup"><span data-stu-id="7a616-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="7a616-113">メッセージ エンコーディングのバインド要素を選択する際に考慮する必要のある要因について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="7a616-114">メッセージ転送ストリーミング</span><span class="sxs-lookup"><span data-stu-id="7a616-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="7a616-115">ストリーミングが行われるようにトランスポート層を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="7a616-116">HTTP および HTTPS の構成</span><span class="sxs-lookup"><span data-stu-id="7a616-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="7a616-117">HTTP および HTTPS トランスポート バインディング要素の構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="7a616-118">方法: WCF URL 予約を制限付きの予約に置き換える</span><span class="sxs-lookup"><span data-stu-id="7a616-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="7a616-119">WCFURL 制限付き予約の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="7a616-120">トランスポート クォータ</span><span class="sxs-lookup"><span data-stu-id="7a616-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="7a616-121">トランスポート層で使用できるクォータを設定する際の考慮事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="7a616-122">NAT とファイアウォールの使用</span><span class="sxs-lookup"><span data-stu-id="7a616-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="7a616-123">ファイアウォールを介してメッセージを送受信する場合や、ネットワーク アドレス交換 (NAT) が存在する場合にトランスポート層を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="7a616-124">Net.TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="7a616-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="7a616-125">WCF の Net.tcp ポート共有コンポーネントの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a616-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7a616-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a616-126">Reference</span></span>  

 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="7a616-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7a616-127">Related Sections</span></span>  

 [<span data-ttu-id="7a616-128">バインド</span><span class="sxs-lookup"><span data-stu-id="7a616-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="7a616-129">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="7a616-129">Extending Bindings</span></span>](../extending/extending-bindings.md)
