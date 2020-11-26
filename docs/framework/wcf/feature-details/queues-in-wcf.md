---
title: Windows Communication Foundation のキュー
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: d63b03e519484ad6ec90b4267a49b77738593e45
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244653"
---
# <a name="queues-in-windows-communication-foundation"></a><span data-ttu-id="d7c71-102">Windows Communication Foundation のキュー</span><span class="sxs-lookup"><span data-stu-id="d7c71-102">Queues in Windows Communication Foundation</span></span>

<span data-ttu-id="d7c71-103">このセクションのトピックでは、キューの Windows Communication Foundation (WCF) のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-103">The topics in this section discuss Windows Communication Foundation (WCF) support for queues.</span></span> <span data-ttu-id="d7c71-104">WCF では、Microsoft Message Queuing (旧称 MSMQ) をトランスポートとして利用してキューをサポートし、次のシナリオを実現します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-104">WCF provides support for queuing by leveraging Microsoft Message Queuing (previously known as MSMQ) as a transport and enables the following scenarios:</span></span>  
  
- <span data-ttu-id="d7c71-105">疎結合アプリケーション。</span><span class="sxs-lookup"><span data-stu-id="d7c71-105">Loosely coupled applications.</span></span> <span data-ttu-id="d7c71-106">送信元アプリケーションは、受信側アプリケーションでメッセージ処理の用意ができているかどうかを確認せずにキューにメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-106">Sending applications can send messages to queues without needing to know whether the receiving application is available to process the message.</span></span> <span data-ttu-id="d7c71-107">キューにより処理の独立性が提供されるため、送信元アプリケーションは、受信側アプリケーションのメッセージ処理速度とは関係なく、キューにメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-107">The queue provides processing independence that allows a sending application to send messages to the queue at a rate that does not depend on how fast the receiving applications can process the messages.</span></span> <span data-ttu-id="d7c71-108">キューに対するメッセージの送信がメッセージ処理と密接に結び付けられていない場合は、システムの全体的な可用性が向上します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-108">Overall system availability increases when sending messages to a queue is not tightly coupled to message processing.</span></span>  
  
- <span data-ttu-id="d7c71-109">エラーの分離。</span><span class="sxs-lookup"><span data-stu-id="d7c71-109">Failure isolation.</span></span> <span data-ttu-id="d7c71-110">キューにメッセージを送受信するアプリケーションは、互いに影響を与えずにエラーを発生させることができます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-110">Applications sending or receiving messages to a queue can fail without affecting each other.</span></span> <span data-ttu-id="d7c71-111">たとえば、受信側のアプリケーションでエラーが発生しても、送信側のアプリケーションではメッセージをキューに送信し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-111">If, for example, the receiving application fails, the sending application can continue to send messages to the queue.</span></span> <span data-ttu-id="d7c71-112">受信側は、エラーからの復帰後、キューにあるメッセージを処理できます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-112">When the receiver is up again, it can process the messages from the queue.</span></span> <span data-ttu-id="d7c71-113">エラーの分離により、システムの全体的な信頼性と可用性が向上します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-113">Failure isolation increases the overall system reliability and availability.</span></span>  
  
- <span data-ttu-id="d7c71-114">負荷の平準化。</span><span class="sxs-lookup"><span data-stu-id="d7c71-114">Load leveling.</span></span> <span data-ttu-id="d7c71-115">送信元アプリケーションから送信するメッセージが多すぎるために、受信側アプリケーションの処理が間に合わなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="d7c71-115">Sending applications can overwhelm receiving applications with messages.</span></span> <span data-ttu-id="d7c71-116">キューによってこの送信側と受信側のメッセージの不均衡が調整されるため、受信側の処理が間に合わなくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="d7c71-116">Queues can manage mismatched message production and consumption rates so that a receiver is not overwhelmed.</span></span>  
  
- <span data-ttu-id="d7c71-117">操作の切断。</span><span class="sxs-lookup"><span data-stu-id="d7c71-117">Disconnected operations.</span></span> <span data-ttu-id="d7c71-118">モバイル デバイスのように遅延の大きなネットワーク、または可用性に制限のあるネットワークを介して通信を行う場合に、送信、受信、および処理の各操作を切断できます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-118">Sending, receiving, and processing operations can become disconnected when communicating over high-latency networks or limited-availability networks, such as in the case of mobile devices.</span></span> <span data-ttu-id="d7c71-119">エンドポイントが切断された場合も、キューによってこれらの操作を続行できます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-119">Queues allow these operations to continue, even when the endpoints are disconnected.</span></span> <span data-ttu-id="d7c71-120">接続が再度確立されると、メッセージはキューから受信側アプリケーションに転送されます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-120">When the connection is reestablished, the queue forwards messages to the receiving application.</span></span>  
  
 <span data-ttu-id="d7c71-121">WCF アプリケーションでキュー機能を使用するには、標準バインディングのいずれかを使用するか、標準バインディングのいずれかが要件を満たさない場合はカスタムバインディングを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d7c71-121">To use the queues feature in a WCF application, you can use one of the standard bindings, or you can create a custom binding if one of the standard bindings does not satisfy your requirements.</span></span> <span data-ttu-id="d7c71-122">関連する標準バインディングとその選択方法の詳細については、「 [方法: WCF エンドポイントとメッセージキューアプリケーションを使用](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)してメッセージを交換する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7c71-122">For more information about relevant standard bindings and how to choose one, see [How to: Exchange Messages with WCF Endpoints and Message Queuing Applications](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).</span></span> <span data-ttu-id="d7c71-123">カスタム バインドを作成する方法の詳細については、「[カスタム バインディング](../extending/custom-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7c71-123">For more information about creating custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7c71-124">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d7c71-124">In This Section</span></span>  

 [<span data-ttu-id="d7c71-125">キューの概要</span><span class="sxs-lookup"><span data-stu-id="d7c71-125">Queues Overview</span></span>](queues-overview.md)  
 <span data-ttu-id="d7c71-126">メッセージ キュー概念について概要を示します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-126">An overview of message queuing concepts.</span></span>  
  
 [<span data-ttu-id="d7c71-127">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="d7c71-127">Queuing in WCF</span></span>](queuing-in-wcf.md)  
 <span data-ttu-id="d7c71-128">WCF キューのサポートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-128">An overview of WCF queue support.</span></span>  
  
 [<span data-ttu-id="d7c71-129">方法: WCF エンドポイントを使用してキューに置かれたメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="d7c71-129">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 <span data-ttu-id="d7c71-130">クラスを使用して、 <xref:System.ServiceModel.NetMsmqBinding> wcf クライアントと wcf サービスの間の通信を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-130">Explains how to use the <xref:System.ServiceModel.NetMsmqBinding> class to communicate between a WCF client and WCF service.</span></span>  
  
 [<span data-ttu-id="d7c71-131">方法: WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="d7c71-131">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 <span data-ttu-id="d7c71-132">を使用して、 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> WCF アプリケーションとメッセージキューアプリケーション間の通信を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-132">Explains how to use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> to communicate between WCF and Message Queuing applications.</span></span>  
  
 [<span data-ttu-id="d7c71-133">セッションでキューに置かれたメッセージのグループ化</span><span class="sxs-lookup"><span data-stu-id="d7c71-133">Grouping Queued Messages in a Session</span></span>](grouping-queued-messages-in-a-session.md)  
 <span data-ttu-id="d7c71-134">単一の受信側アプリケーションが関連メッセージを迅速に処理できるように、キューでメッセージをグループ化する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-134">Explains how to group messages in a queue to facilitate correlated message processing by a single receiving application.</span></span>  
  
 [<span data-ttu-id="d7c71-135">トランザクションに含まれるメッセージのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="d7c71-135">Batching Messages in a Transaction</span></span>](batching-messages-in-a-transaction.md)  
 <span data-ttu-id="d7c71-136">トランザクションでメッセージをバッチ処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-136">Explains how to batch messages in a transaction.</span></span>  
  
 [<span data-ttu-id="d7c71-137">配信不能キューを使用したメッセージ転送エラー処理</span><span class="sxs-lookup"><span data-stu-id="d7c71-137">Using Dead-Letter Queues to Handle Message Transfer Failures</span></span>](using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 <span data-ttu-id="d7c71-138">配信不能キューを使用してメッセージの転送エラーと配信エラーを処理する方法、および配信不能キューのメッセージを処理する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-138">Explains how to handle message transfer and delivery failures using dead letter queues and how to process messages from the dead letter queue.</span></span>  
  
 [<span data-ttu-id="d7c71-139">有害メッセージ処理</span><span class="sxs-lookup"><span data-stu-id="d7c71-139">Poison Message Handling</span></span>](poison-message-handling.md)  
 <span data-ttu-id="d7c71-140">有害メッセージ (受信側アプリケーションへの配信試行の回数が最大値を超えたメッセージ) の処理方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-140">Explains how to handle poison messages (messages that have exceeded the maximum number of delivery attempts to the receiving application).</span></span>  
  
 [<span data-ttu-id="d7c71-141">Windows Vista、Windows Server 2003、および Windows XP におけるキュー機能の相違点</span><span class="sxs-lookup"><span data-stu-id="d7c71-141">Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP</span></span>](diff-in-queue-in-vista-server-2003-windows-xp.md)  
 <span data-ttu-id="d7c71-142">Windows Vista、Windows Server 2003、および Windows XP の WCF キュー機能の違いについて概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-142">Summarizes the differences in the WCF queues feature between Windows Vista, Windows Server 2003, and Windows XP.</span></span>  
  
 [<span data-ttu-id="d7c71-143">トランスポート セキュリティを使用したメッセージのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d7c71-143">Securing Messages Using Transport Security</span></span>](securing-messages-using-transport-security.md)  
 <span data-ttu-id="d7c71-144">トランスポート セキュリティを使用して、キューに置かれたメッセージを保護する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-144">Describes how to use transport security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="d7c71-145">メッセージ セキュリティを使用したメッセージのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d7c71-145">Securing Messages Using Message Security</span></span>](securing-messages-using-message-security.md)  
 <span data-ttu-id="d7c71-146">メッセージ セキュリティを使用して、キューに置かれたメッセージを保護する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-146">Describes how to use message security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="d7c71-147">キューに置かれたメッセージングのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d7c71-147">Troubleshooting Queued Messaging</span></span>](troubleshooting-queued-messaging.md)  
 <span data-ttu-id="d7c71-148">一般的なキューの問題をトラブルシューティングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-148">Explains how to troubleshoot common queuing problems.</span></span>  
  
 [<span data-ttu-id="d7c71-149">キューに置かれた通信のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="d7c71-149">Best Practices for Queued Communication</span></span>](best-practices-for-queued-communication.md)  
 <span data-ttu-id="d7c71-150">WCF キュー通信を使用するためのベストプラクティスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d7c71-150">Explains best practices for using WCF queued communication.</span></span>  
