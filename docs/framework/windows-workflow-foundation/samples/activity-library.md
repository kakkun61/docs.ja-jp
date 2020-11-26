---
title: アクティビティ ライブラリ
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 1a0c289315d7181645573098916788f18493abb8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245704"
---
# <a name="activity-library"></a><span data-ttu-id="b05b6-102">アクティビティ ライブラリ</span><span class="sxs-lookup"><span data-stu-id="b05b6-102">Activity Library</span></span>

<span data-ttu-id="b05b6-103">このセクションには、Windows Workflow Foundation (WF) の高度なカスタムアクティビティを示すサンプルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b05b6-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b05b6-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b05b6-104">In This Section</span></span>

 [<span data-ttu-id="b05b6-105">SendMail カスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="b05b6-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="b05b6-106"><xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b05b6-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="b05b6-107">制限された並列 ForEach</span><span class="sxs-lookup"><span data-stu-id="b05b6-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="b05b6-108">ph x="1" /&gt; アクティビティは、実行するコンカレンシー分岐の数を制限するためのコンカレンシー要因を設定できるという 1 つの例外を除き、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティと似ていることについて示します。</span><span class="sxs-lookup"><span data-stu-id="b05b6-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="b05b6-109">データベース アクセス アクティビティ</span><span class="sxs-lookup"><span data-stu-id="b05b6-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="b05b6-110">データベースにアクセスして情報を取得または変更し、 [ADO.NET](../../data/adonet/index.md) を使用してデータベースにアクセスできるようにするアクティビティを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b05b6-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="b05b6-111">.NET Framework 4.5 の外部化されたポリシー アクティビティ</span><span class="sxs-lookup"><span data-stu-id="b05b6-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="b05b6-112">ExternalizedPolicy4 アクティビティを使用して、 <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] wf 3.5 に付属するルールエンジンを使用して、(wf 4.5) の Windows Workflow Foundation の .NET Framework 3.5 (wf 3.5) オブジェクトの既存の Windows Workflow Foundation を直接実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b05b6-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="b05b6-113">非ジェネリックの ForEach</span><span class="sxs-lookup"><span data-stu-id="b05b6-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="b05b6-114"><xref:System.Activities.Statements.ForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b05b6-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="b05b6-115">非ジェネリックの ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="b05b6-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="b05b6-116"><xref:System.Activities.Statements.ParallelForEach%601> アクティビティの非ジェネリック バージョンを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b05b6-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="b05b6-117">WorkflowInstanceId の取得</span><span class="sxs-lookup"><span data-stu-id="b05b6-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="b05b6-118">カスタム アクティビティ `GetWorkflowInstanceId` を使用して、ワークフロー インスタンス ID を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b05b6-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
