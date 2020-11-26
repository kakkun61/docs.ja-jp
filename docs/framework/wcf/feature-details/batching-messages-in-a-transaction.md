---
title: トランザクションに含まれるメッセージのバッチ処理
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: c18d5a36f4263a93589b75129517d66df80ce463
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247461"
---
# <a name="batching-messages-in-a-transaction"></a><span data-ttu-id="9cc4c-102">トランザクションに含まれるメッセージのバッチ処理</span><span class="sxs-lookup"><span data-stu-id="9cc4c-102">Batching Messages in a Transaction</span></span>

<span data-ttu-id="9cc4c-103">キューに置かれたアプリケーションは、トランザクションを使用してメッセージの正確性および信頼性のある配信を確保します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-103">Queued applications use transactions to ensure correctness and reliable delivery of messages.</span></span> <span data-ttu-id="9cc4c-104">ただし、トランザクション操作には負荷がかかるため、メッセージのスループットが大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-104">Transactions, however, are expensive operations and can dramatically reduce message throughput.</span></span> <span data-ttu-id="9cc4c-105">メッセージ スループットを向上する方法の 1 つは、アプリケーションにより、単一のトランザクション内で複数のメッセージを読み取って処理することです。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-105">One way to improve message throughput is to have an application read and process multiple messages within a single transaction.</span></span> <span data-ttu-id="9cc4c-106">ただし、その場合、バッチ内のメッセージ数が増えるにつれて、トランザクションをロールバックしたときに必要な回復の作業量も増えるため、パフォーマンスと回復の間のトレードオフを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-106">The trade-off is between performance and recovery: as the number of messages in a batch increases, so does the amount of recovery work that required if transactions are rolled back.</span></span> <span data-ttu-id="9cc4c-107">したがって、トランザクションでのメッセージのバッチ処理とセッションの違いに注目することが重要です。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-107">It is important to note the difference between batching messages in a transaction and sessions.</span></span> <span data-ttu-id="9cc4c-108">*セッション* とは、1つのアプリケーションによって処理され、1つの単位としてコミットされる、関連するメッセージのグループです。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-108">A *session* is a grouping of related messages that are processed by a single application and committed as a single unit.</span></span> <span data-ttu-id="9cc4c-109">セッションは、一般に、関連メッセージのグループをまとめて処理する必要がある場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-109">Sessions are generally used when a group of related messages must be processed together.</span></span> <span data-ttu-id="9cc4c-110">この例として、オンライン ショッピング Web サイトがあります。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-110">An example of this is an online shopping Web site.</span></span> <span data-ttu-id="9cc4c-111">*バッチ* は、メッセージのスループットを向上させる方法で、関連のない複数のメッセージを処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-111">*Batches* are used to process multiple, unrelated messages in a way that increases message throughput.</span></span> <span data-ttu-id="9cc4c-112">セッションの詳細については、「 [セッションでキューに置かれたメッセージをグループ化する](grouping-queued-messages-in-a-session.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-112">For more information about sessions, see [Grouping Queued Messages in a Session](grouping-queued-messages-in-a-session.md).</span></span> <span data-ttu-id="9cc4c-113">バッチ内のメッセージもまた、単一のアプリケーションによって処理され、1 つの単位としてコミットされますが、バッチ内のメッセージが関連している必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-113">Messages in a batch are also processed by a single application and committed as a single unit, but there may be no relationship between the messages in the batch.</span></span> <span data-ttu-id="9cc4c-114">トランザクションでのメッセージのバッチ処理は、アプリケーションの実行方法を変更しない最適化です。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-114">Batching messages in a transaction is an optimization that does not change how the application runs.</span></span>  
  
## <a name="entering-batching-mode"></a><span data-ttu-id="9cc4c-115">バッチ処理モードの開始</span><span class="sxs-lookup"><span data-stu-id="9cc4c-115">Entering Batching Mode</span></span>  

 <span data-ttu-id="9cc4c-116">バッチ処理は、<xref:System.ServiceModel.Description.TransactedBatchingBehavior> エンドポイント動作によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-116">The <xref:System.ServiceModel.Description.TransactedBatchingBehavior> endpoint behavior controls batching.</span></span> <span data-ttu-id="9cc4c-117">このエンドポイント動作をサービスエンドポイントに追加すると、トランザクション内のメッセージをバッチ処理するように Windows Communication Foundation (WCF) に指示されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-117">Adding this endpoint behavior to a service endpoint tells Windows Communication Foundation (WCF) to batch messages in a transaction.</span></span> <span data-ttu-id="9cc4c-118">すべてのメッセージでトランザクションが要求されるわけではないので、トランザクションを必要とするメッセージのみがバッチに格納され、とでマークされた操作から送信されたメッセージのみがバッチで考慮され `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` ます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-118">Not all messages require a transaction, so only messages that require a transaction are placed in a batch, and only messages sent from operations marked with `TransactionScopeRequired` = `true` and `TransactionAutoComplete` = `true` are considered for a batch.</span></span> <span data-ttu-id="9cc4c-119">サービスコントラクトに対するすべての操作がとでマークされている場合 `TransactionScopeRequired`  =  `false` `TransactionAutoComplete`  =  `false` 、バッチモードは入力されません。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-119">If all operations on the service contract are marked with `TransactionScopeRequired` = `false` and `TransactionAutoComplete` = `false`, then batching mode is never entered.</span></span>  
  
## <a name="committing-a-transaction"></a><span data-ttu-id="9cc4c-120">トランザクションのコミット</span><span class="sxs-lookup"><span data-stu-id="9cc4c-120">Committing a Transaction</span></span>  

 <span data-ttu-id="9cc4c-121">バッチ トランザクションは、次の基準に基づいてコミットされます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-121">A batched transaction is committed based on the following:</span></span>  
  
- <span data-ttu-id="9cc4c-122">`MaxBatchSize`.</span><span class="sxs-lookup"><span data-stu-id="9cc4c-122">`MaxBatchSize`.</span></span> <span data-ttu-id="9cc4c-123"><xref:System.ServiceModel.Description.TransactedBatchingBehavior> 動作のプロパティ。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-123">A property of the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> behavior.</span></span> <span data-ttu-id="9cc4c-124">このプロパティは、バッチに含められるメッセージの最大数を決定します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-124">This property determines the maximum number of messages that are placed into a batch.</span></span> <span data-ttu-id="9cc4c-125">この数に達すると、バッチがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-125">When this number is reached, the batch is committed.</span></span> <span data-ttu-id="9cc4c-126">この値は厳密に定められたものではないため、この数のメッセージを受信する前にバッチをコミットすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-126">This is value is not a strict limit, it is possible to commit a batch before receiving this number of messages.</span></span>  
  
- <span data-ttu-id="9cc4c-127">`Transaction Timeout`.</span><span class="sxs-lookup"><span data-stu-id="9cc4c-127">`Transaction Timeout`.</span></span> <span data-ttu-id="9cc4c-128">トランザクションのタイムアウトの 80% が経過すると、バッチがコミットされ、新しいバッチが作成されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-128">After 80 percent of the transaction's time-out has elapsed, the batch is committed and a new batch is created.</span></span> <span data-ttu-id="9cc4c-129">つまり、トランザクションが完了するために指定された時間の残りが 20% 以下になると、バッチがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-129">This means that if 20 percent or less of the time given for a transaction to complete remains, the batch is committed.</span></span>  
  
- <span data-ttu-id="9cc4c-130">`TransactionScopeRequired`.</span><span class="sxs-lookup"><span data-stu-id="9cc4c-130">`TransactionScopeRequired`.</span></span> <span data-ttu-id="9cc4c-131">メッセージのバッチを処理するときに、があるバッチを検出すると、そのバッチが `TransactionScopeRequired`  =  `false` コミットされ、との最初のメッセージの受信時に新しいバッチが再度開かれ `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` ます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-131">When processing a batch of messages, if WCF finds one that has `TransactionScopeRequired` = `false`, it commits the batch and reopens a new batch on receipt of the first message with `TransactionScopeRequired` = `true` and `TransactionAutoComplete` = `true`.</span></span>  
  
- <span data-ttu-id="9cc4c-132">キューのメッセージがなくなると、`MaxBatchSize` に達していない場合やトランザクションのタイムアウトの 80% が経過していない場合でも、現在のバッチがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-132">If no more messages exist in the queue, then the current batch is committed, even if the `MaxBatchSize` has not been reached or 80 percent of the transaction's time-out has not elapsed.</span></span>  
  
## <a name="leaving-batching-mode"></a><span data-ttu-id="9cc4c-133">バッチ処理モードの終了</span><span class="sxs-lookup"><span data-stu-id="9cc4c-133">Leaving Batching Mode</span></span>  

 <span data-ttu-id="9cc4c-134">バッチ内のメッセージによってトランザクションが中止されたときの動作は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-134">If a message in a batch causes the transaction to abort, the following steps occur:</span></span>  
  
1. <span data-ttu-id="9cc4c-135">メッセージのバッチ全体がロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-135">The entire batch of messages is rolled back.</span></span>  
  
2. <span data-ttu-id="9cc4c-136">読み取られたメッセージの数がバッチの最大サイズの 2 倍を超えるまで、一度に 1 つのメッセージが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-136">Messages are read one at a time until the number of messages read exceeds twice the maximum batch size.</span></span>  
  
3. <span data-ttu-id="9cc4c-137">再度、バッチ モードに入ります。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-137">Batch mode is re-entered.</span></span>  
  
## <a name="choosing-the-batch-size"></a><span data-ttu-id="9cc4c-138">バッチ サイズの選択</span><span class="sxs-lookup"><span data-stu-id="9cc4c-138">Choosing the Batch Size</span></span>  

 <span data-ttu-id="9cc4c-139">バッチのサイズは、アプリケーションに依存します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-139">The size of a batch is application-dependent.</span></span> <span data-ttu-id="9cc4c-140">アプリケーションに最適なバッチ サイズは、経験に基づいて決定するのが最良の方法です。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-140">The empirical method is the best way to arrive at an optimal batch size for the application.</span></span> <span data-ttu-id="9cc4c-141">バッチ サイズを選択する際には、アプリケーションの実際の展開モデルに応じたサイズを選択することが重要です。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-141">It is important to remember when choosing a batch size to choose the size according to your application's actual deployment model.</span></span> <span data-ttu-id="9cc4c-142">たとえば、アプリケーションの展開で、リモート コンピューターに SQL サーバーを配置し、キューとその SQL サーバーにまたがるトランザクションを実行する必要がある場合は、そのとおりの構成を実行してバッチ サイズを決定するのが最良の方法です。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-142">For example, when deploying the application, if you need an SQL server on a remote machine and a transaction that spans the queue and the SQL server, then the batch size is best determined by running this exact configuration.</span></span>  
  
## <a name="concurrency-and-batching"></a><span data-ttu-id="9cc4c-143">コンカレンシーとバッチ処理</span><span class="sxs-lookup"><span data-stu-id="9cc4c-143">Concurrency and Batching</span></span>  

 <span data-ttu-id="9cc4c-144">スループットを向上させるために、多数のバッチを同時に実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-144">To increase throughput, you can also have many batches run concurrently.</span></span> <span data-ttu-id="9cc4c-145">同時バッチ処理を有効にするには、`ConcurrencyMode.Multiple` の `ServiceBehaviorAttribute` を設定します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-145">By setting `ConcurrencyMode.Multiple` in `ServiceBehaviorAttribute`, you enable concurrent batching.</span></span>  
  
 <span data-ttu-id="9cc4c-146">サービスの *調整* とは、サービスに対して同時に実行できる最大呼び出し数を示すために使用されるサービスの動作です。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-146">*Service throttling* is a service behavior that is used to indicate how many maximum concurrent calls can be made on the service.</span></span> <span data-ttu-id="9cc4c-147">この動作をバッチ処理で使用すると、実行できる同時バッチの数と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-147">When used with batching, this is interpreted as how many concurrent batches can be run.</span></span> <span data-ttu-id="9cc4c-148">サービス調整が設定されていない場合、WCF では、同時呼び出しの最大数が既定で16に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-148">If the service throttling is not set, WCF defaults the maximum concurrent calls to 16.</span></span> <span data-ttu-id="9cc4c-149">したがって、バッチ動作が既定で追加されると、最大で 16 個のバッチが同時にアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-149">Thus, if batching behavior were added by default, a maximum of 16 batches can be active at the same time.</span></span> <span data-ttu-id="9cc4c-150">容量に基づいてサービス調整とバッチ処理を調整することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-150">It is best to tune the service throttling and batching based on your capacity.</span></span> <span data-ttu-id="9cc4c-151">たとえば、キューに 100 個のメッセージがあり、20 個のメッセージを含むバッチを実行する必要がある場合、同時呼び出しの最大数を 16 に設定しても実用的ではありません。それは、スループットによっては、バッチ処理をオンにしていない場合と同様に、16 個のトランザクションがアクティブになる可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-151">For example, if the queue has 100 messages and a batch of 20 is desired, having the maximum concurrent calls set to 16 is not useful because, depending on throughput, 16 transactions could be active, similar to not having batching turned on.</span></span> <span data-ttu-id="9cc4c-152">したがって、パフォーマンスを微調整するためには、同時バッチ処理を設定しないか、正しいサービス調整のサイズで同時バッチ処理を設定します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-152">Therefore, when fine-tuning for performance, either do not have concurrent batching or have concurrent batching with the correct service throttle size.</span></span>  
  
## <a name="batching-and-multiple-endpoints"></a><span data-ttu-id="9cc4c-153">バッチ処理と複数のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="9cc4c-153">Batching and Multiple Endpoints</span></span>  

 <span data-ttu-id="9cc4c-154">エンドポイントは、アドレスとコントラクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-154">An endpoint is composed of an address and a contract.</span></span> <span data-ttu-id="9cc4c-155">同じバインディングを共有するエンドポイントが複数ある場合があります。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-155">There may be multiple endpoints that share the same binding.</span></span> <span data-ttu-id="9cc4c-156">2 つのエンドポイントが同じバインディングと、リッスン URI (Uniform Resource Identifier) つまりキュー アドレスを共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-156">It is possible for two endpoints to share the same binding and listen Uniform Resource Identifier (URI), or queue address.</span></span> <span data-ttu-id="9cc4c-157">2 つのエンドポイントが同じキューから読み取りを行っている場合、トランザクション バッチ動作を両方のエンドポイントに追加すると、指定したバッチ サイズ間で競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-157">If two endpoints are reading from the same queue, and transacted batching behavior is added to both endpoints, a conflict in the batch sizes specified could arise.</span></span> <span data-ttu-id="9cc4c-158">この問題を解決するには、2 つのトランザクション バッチ動作の間に指定される最小バッチ サイズを使用してバッチを実装します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-158">This is resolved by implementing batching using the minimal batch size specified between the two transacted batching behaviors.</span></span> <span data-ttu-id="9cc4c-159">このシナリオでは、どちらかのエンドポイントがトランザクション バッチを指定していない場合、両方のエンドポイントがバッチ処理を使用しません。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-159">In this scenario, if one of the endpoints does not specify transacted batching, then both endpoints would not use batching.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cc4c-160">例</span><span class="sxs-lookup"><span data-stu-id="9cc4c-160">Example</span></span>  

 <span data-ttu-id="9cc4c-161">構成ファイルで `TransactedBatchingBehavior` を指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-161">The following example shows how to specify the `TransactedBatchingBehavior` in a configuration file.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 <span data-ttu-id="9cc4c-162">コードで <xref:System.ServiceModel.Description.TransactedBatchingBehavior> を指定する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9cc4c-162">The following example shows how to specify the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> in code.</span></span>  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));

     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cc4c-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="9cc4c-163">See also</span></span>

- [<span data-ttu-id="9cc4c-164">キューの概要</span><span class="sxs-lookup"><span data-stu-id="9cc4c-164">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="9cc4c-165">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="9cc4c-165">Queuing in WCF</span></span>](queuing-in-wcf.md)
