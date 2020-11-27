---
title: 転送
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: da31dcb24234e750c88383b9f1bea4f088f4ee3d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293404"
---
# <a name="transfer"></a><span data-ttu-id="ee204-102">転送</span><span class="sxs-lookup"><span data-stu-id="ee204-102">Transfer</span></span>

<span data-ttu-id="ee204-103">このトピックでは、Windows Communication Foundation (WCF) アクティビティトレースモデルでの転送について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee204-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="ee204-104">転送の定義</span><span class="sxs-lookup"><span data-stu-id="ee204-104">Transfer Definition</span></span>  

 <span data-ttu-id="ee204-105">アクティビティ間の転送は、エンドポイント内の関連アクティビティで発生したイベント間の因果関係を表します。</span><span class="sxs-lookup"><span data-stu-id="ee204-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="ee204-106">制御が 2 つのアクティビティ間を流れる場合 (アクティビティの境界を越えたメソッド呼び出しなど)、転送によってこれらのアクティビティが関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="ee204-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="ee204-107">WCF では、サービスでバイトが受信されると、メッセージオブジェクトが作成されたときに、受信側の受信アクティビティが Bytes Receive アクティビティに転送されます。</span><span class="sxs-lookup"><span data-stu-id="ee204-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="ee204-108">エンドツーエンドのトレースシナリオの一覧と、それぞれのアクティビティとトレースの設計については、「 [エンドツーエンドのトレースのシナリオ](end-to-end-tracing-scenarios.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee204-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="ee204-109">転送トレースを出力するには、次の構成コードのように、トレース ソースに `ActivityTracing` を設定します。</span><span class="sxs-lookup"><span data-stu-id="ee204-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="ee204-110">転送を使用したエンドポイント内でのアクティビティの関連付け</span><span class="sxs-lookup"><span data-stu-id="ee204-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  

 <span data-ttu-id="ee204-111">アクティビティと転送により、ユーザーはエラーの根本原因をほぼ突き止めることができます。</span><span class="sxs-lookup"><span data-stu-id="ee204-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="ee204-112">たとえば、コンポーネント M と N のアクティビティ M と N の間で、M から N および N から M への転送を行い、M への転送の直後に N でクラッシュが発生した場合、N から M にデータを返したことが原因でクラッシュが発生した可能性があるという結論を下すことができます。</span><span class="sxs-lookup"><span data-stu-id="ee204-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="ee204-113">アクティビティ M とアクティビティ N の間に制御のフローが存在する場合、転送トレースは M から N に出力されます。たとえば、メソッド呼び出しがアクティビティの境界を越えるため、N が M に代わって何らかの処理を実行するとします。</span><span class="sxs-lookup"><span data-stu-id="ee204-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="ee204-114">N は既に存在する場合もあれば、作成されている場合もあります。</span><span class="sxs-lookup"><span data-stu-id="ee204-114">N may already exist or has been created.</span></span> <span data-ttu-id="ee204-115">N が、M に代わって何らかの処理を実行する新しいアクティビティである場合、N は M によって発生します。</span><span class="sxs-lookup"><span data-stu-id="ee204-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="ee204-116">M から N への転送の後に、N から M に転送することはできません。これは、M は N で処理を発生させることはできますが、N がその処理をいつ完了するかまでは追跡しないからです。</span><span class="sxs-lookup"><span data-stu-id="ee204-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="ee204-117">実際、N がタスクを完了する前に M が終了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="ee204-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="ee204-118">これは、リスナーアクティビティ (N) を生成して終了する "Open ServiceHost" アクティビティ (M) で発生します。</span><span class="sxs-lookup"><span data-stu-id="ee204-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="ee204-119">N から M への転送は、N が M に関連する処理を完了したことを意味します。</span><span class="sxs-lookup"><span data-stu-id="ee204-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="ee204-120">N は、M に関連しない他の処理を引き続き実行できます。たとえば、既存の認証システム アクティビティ (N) は、さまざまなログイン アクティビティからのログイン要求 (M) を受信し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="ee204-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="ee204-121">アクティビティ M と N の間に、入れ子のリレーションシップが必ずしも存在するわけではありません。入れ子のリレーションシップが存在しない状況が発生する原因として、2 つのケースが考えられます。</span><span class="sxs-lookup"><span data-stu-id="ee204-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="ee204-122">1 つは、アクティビティ M が アクティビティ N を開始したが、N で実行される実際の処理を M が監視しない場合です。もう 1 つは、N が既に存在する場合です。</span><span class="sxs-lookup"><span data-stu-id="ee204-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="ee204-123">転送の例</span><span class="sxs-lookup"><span data-stu-id="ee204-123">Example of Transfers</span></span>  

 <span data-ttu-id="ee204-124">転送の 2 つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ee204-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="ee204-125">サービス ホストの作成時に、コンストラクターは呼び出し元のコードから制御を取得します。つまり、呼び出し元のコードがコンストラクターに転送されます。</span><span class="sxs-lookup"><span data-stu-id="ee204-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="ee204-126">コンストラクターは、必要な処理を終えると、呼び出し元に制御を返します。つまり、コンストラクターから呼び出し元への逆転送が起こります。</span><span class="sxs-lookup"><span data-stu-id="ee204-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="ee204-127">これは、入れ子になったリレーションシップの例です。</span><span class="sxs-lookup"><span data-stu-id="ee204-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="ee204-128">リスナーはトランスポート データの処理を開始するときに、新しいスレッドを作成し、"バイトを受信" アクティビティに、処理の適切なコンテキストとして制御とデータを渡します。</span><span class="sxs-lookup"><span data-stu-id="ee204-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="ee204-129">このスレッドが要求の処理を完了しても、"バイトを受信" アクティビティからリスナーには何も渡されません。</span><span class="sxs-lookup"><span data-stu-id="ee204-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="ee204-130">この場合、新しいスレッドのアクティビティへの転送はありますが、このアクティビティからの転送はありません。</span><span class="sxs-lookup"><span data-stu-id="ee204-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="ee204-131">2 つのアクティビティは関連していますが、入れ子にはなっていません。</span><span class="sxs-lookup"><span data-stu-id="ee204-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="ee204-132">アクティビティ転送シーケンス</span><span class="sxs-lookup"><span data-stu-id="ee204-132">Activity Transfer Sequence</span></span>  

 <span data-ttu-id="ee204-133">適切なアクティビティ転送シーケンスには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ee204-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="ee204-134">新しい gAId を選択して、新しいアクティビティを開始します。</span><span class="sxs-lookup"><span data-stu-id="ee204-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="ee204-135">現在のアクティビティ ID から新しい gAId への転送トレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="ee204-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="ee204-136">TLS に新しい ID を設定します。</span><span class="sxs-lookup"><span data-stu-id="ee204-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="ee204-137">Start トレースを出力して、新しいアクティビティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="ee204-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="ee204-138">次の手順を実行して、元のアクティビティに戻ります。</span><span class="sxs-lookup"><span data-stu-id="ee204-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="ee204-139">元の gAId への転送トレースを出力します。</span><span class="sxs-lookup"><span data-stu-id="ee204-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="ee204-140">Stop トレースを出力して、新しいアクティビティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="ee204-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="ee204-141">TLS を以前の gAId に設定します。</span><span class="sxs-lookup"><span data-stu-id="ee204-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="ee204-142">これを実行する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="ee204-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="ee204-143">この例は、新しいアクティビティへの転送時にブロック呼び出しが行われることを想定しており、Suspend トレースと Resume トレースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee204-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="ee204-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee204-144">See also</span></span>

- [<span data-ttu-id="ee204-145">トレースの構成</span><span class="sxs-lookup"><span data-stu-id="ee204-145">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="ee204-146">サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ee204-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="ee204-147">エンドツーエンドのトレースのシナリオ</span><span class="sxs-lookup"><span data-stu-id="ee204-147">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="ee204-148">サービス トレース ビューアー ツール (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="ee204-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
