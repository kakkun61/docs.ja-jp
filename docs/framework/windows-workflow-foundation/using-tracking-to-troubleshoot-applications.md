---
title: 追跡を使用したアプリケーションのトラブルシューティング
ms.date: 03/30/2017
ms.assetid: 8851adde-c3c2-4391-9523-d8eb831490af
ms.openlocfilehash: 62f2240831dd33bdaf78655199aad75b7e29c59c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293573"
---
# <a name="using-tracking-to-troubleshoot-applications"></a><span data-ttu-id="1dbc2-102">追跡を使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1dbc2-102">Using Tracking to Troubleshoot Applications</span></span>

<span data-ttu-id="1dbc2-103">Windows Workflow Foundation (WF) を使用すると、ワークフロー関連の情報を追跡して、Windows Workflow Foundation アプリケーションまたはサービスの実行に詳細を提供できます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-103">Windows Workflow Foundation (WF) enables you to track workflow-related information to give details into the execution of a Windows Workflow Foundation application or service.</span></span> <span data-ttu-id="1dbc2-104">Windows Workflow Foundation ホストは、ワークフローインスタンスの実行中にワークフローイベントをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-104">Windows Workflow Foundation hosts are able to capture workflow events during the execution of a workflow instance.</span></span> <span data-ttu-id="1dbc2-105">ワークフローによってエラーまたは例外が生成された場合は、Windows Workflow Foundation 追跡の詳細を使用して、処理のトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-105">If your workflow generates faults or exceptions, you can use the Windows Workflow Foundation tracking details to troubleshooting its processing.</span></span>  
  
## <a name="troubleshooting-a-wf-using-wf-tracking"></a><span data-ttu-id="1dbc2-106">WF の追跡を使用した WF のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="1dbc2-106">Troubleshooting a WF using WF Tracking</span></span>  

 <span data-ttu-id="1dbc2-107">Windows Workflow Foundation アクティビティの処理中に発生したエラーを検出するには、状態が Faulted であるを照会する追跡プロファイルを使用して追跡を有効にすることができ <xref:System.Activities.Tracking.ActivityStateRecord> ます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-107">To detect faults within the processing of a Windows Workflow Foundation activity, you can enable tracking with a tracking profile that queries for an <xref:System.Activities.Tracking.ActivityStateRecord> with the state of Faulted.</span></span> <span data-ttu-id="1dbc2-108">対応するクエリは、次のコードで指定されています。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-108">The corresponding query is specified in the following code.</span></span>  
  
```xml  
<activityStateQueries>  
              <activityStateQuery activityName="*">  
                <states>  
                  <state name="Faulted" />  
                </states>  
              </activityStateQuery>  
 </activityStateQueries>  
```  
  
 <span data-ttu-id="1dbc2-109">エラーがエラー ハンドラー (<xref:System.Activities.Statements.TryCatch> アクティビティなど) 内で反映および処理される場合、<xref:System.Activities.Tracking.FaultPropagationRecord> を使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-109">If a fault is propagated and handled within a fault handler (such as a <xref:System.Activities.Statements.TryCatch> activity) this can be detected using a <xref:System.Activities.Tracking.FaultPropagationRecord>.</span></span> <span data-ttu-id="1dbc2-110"><xref:System.Activities.Tracking.FaultPropagationRecord> は、エラーのソース アクティビティとエラー ハンドラーの名前を示します。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-110">The <xref:System.Activities.Tracking.FaultPropagationRecord> indicates the source activity of the fault and the name of the fault handler.</span></span> <span data-ttu-id="1dbc2-111">には、エラー <xref:System.Activities.Tracking.FaultPropagationRecord> の例外スタックの形式でエラーの詳細が含まれています。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-111">The <xref:System.Activities.Tracking.FaultPropagationRecord> contains fault details in form of the exception stack for the fault.</span></span> <span data-ttu-id="1dbc2-112">をサブスクライブするためのクエリを <xref:System.Activities.Tracking.FaultPropagationRecord> 次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-112">The query to subscribe for a <xref:System.Activities.Tracking.FaultPropagationRecord> is shown in the following example.</span></span>  
  
```xml  
<faultPropagationQueries>  
              <faultPropagationQuery faultSourceActivityName ="*" faultHandlerActivityName="*"/>  
 </faultPropagationQueries>  
```  
  
 <span data-ttu-id="1dbc2-113">エラーがワークフロー内で処理されない場合は、ワークフロー インスタンスでハンドルされない例外になり、ワークフロー インスタンスは中止されます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-113">If a fault is not handled within the workflow it results in an unhandled exception at the workflow instance and the workflow instance is aborted.</span></span> <span data-ttu-id="1dbc2-114">ハンドルされない例外の詳細を把握するために、追跡プロファイルでは、次のように `state name="UnhandledException"` を持つワークフロー インスタンス レコードを照会する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-114">To understand the details of the unhandled exception, the tracking profile must query the workflow instance record with `state name="UnhandledException"` as specified in the following example.</span></span>  
  
```xml  
<workflowInstanceQueries>  
              <workflowInstanceQuery>  
                <states>  
                  <state name="UnhandledException" />  
                </states>  
              </workflowInstanceQuery>  
</workflowInstanceQueries>  
```  
  
 <span data-ttu-id="1dbc2-115">ワークフローインスタンスでハンドルされない例外が発生した場合、 <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> Windows Workflow Foundation の追跡が有効になっていると、オブジェクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-115">When a workflow instance encounters an unhandled exception, a <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord> object is emitted if Windows Workflow Foundation tracking has been enabled.</span></span>  
  
 <span data-ttu-id="1dbc2-116">この追跡レコードには、例外スタックの形式でエラーの詳細が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-116">This tracking record contains the fault details in the form of the exception stack.</span></span> <span data-ttu-id="1dbc2-117">これには、エラーの原因となったエラー (アクティビティなど) の詳細が含まれており、未処理の例外が発生しています。Windows Workflow Foundation からのエラーイベントをサブスクライブするには、追跡参加要素を追加して追跡を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-117">It has details of the source of the fault (for example, the activity) that faulted and resulted in the unhandled exception.To subscribe to fault events from a Windows Workflow Foundation, enable tracking by adding a tracking participant.</span></span> <span data-ttu-id="1dbc2-118">この参加要素は、`ActivityStateQuery (state="Faulted")`、<xref:System.Activities.Tracking.FaultPropagationRecord>、および `WorkflowInstanceQuery (state="UnhandledException")` を照会する追跡プロファイルで構成します。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-118">Configure this participant with a tracking profile that queries for `ActivityStateQuery (state="Faulted")`, <xref:System.Activities.Tracking.FaultPropagationRecord>, and `WorkflowInstanceQuery (state="UnhandledException")`.</span></span>  
  
 <span data-ttu-id="1dbc2-119">ETW 追跡参加要素を使用して追跡を有効にした場合、エラー イベントは ETW セッションに書き出されます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-119">If tracking is enabled using the ETW tracking participant, the fault events are emitted to an ETW session.</span></span> <span data-ttu-id="1dbc2-120">イベントはイベント ビューアーを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-120">The events can be viewed using the Event Viewer event viewer.</span></span> <span data-ttu-id="1dbc2-121">これは、分析チャネルの [ **イベントビューアー] >[アプリケーションとサービスログ]->[Microsoft >Windows->アプリケーションサーバー-アプリケーション** ] の下にあります。</span><span class="sxs-lookup"><span data-stu-id="1dbc2-121">This can be found under the node **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications** in the analytic channel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dbc2-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dbc2-122">See also</span></span>

- <span data-ttu-id="1dbc2-123">[Windows Server App Fabric の監視](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1dbc2-123">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="1dbc2-124">[App Fabric を使用したアプリケーションの監視](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1dbc2-124">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
