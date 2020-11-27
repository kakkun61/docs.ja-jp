---
title: 補正
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 60e2789c4bbd29185af50eaf6555307b894d3902
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289192"
---
# <a name="compensation"></a><span data-ttu-id="0cb51-102">補正</span><span class="sxs-lookup"><span data-stu-id="0cb51-102">Compensation</span></span>

<span data-ttu-id="0cb51-103">Windows Workflow Foundation (WF) での補正は、それ以降の障害が発生したときに、以前に完了した作業を元に戻したり補正したりするためのメカニズムです (アプリケーションで定義されているロジックに従ってください)。</span><span class="sxs-lookup"><span data-stu-id="0cb51-103">Compensation in Windows Workflow Foundation (WF) is the mechanism by which previously completed work can be undone or compensated (following the logic defined by the application) when a subsequent failure occurs.</span></span> <span data-ttu-id="0cb51-104">ここでは、ワークフローで補正を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-104">This section describes how to use compensation in workflows.</span></span>  
  
## <a name="compensation-vs-transactions"></a><span data-ttu-id="0cb51-105">補正とトランザクション</span><span class="sxs-lookup"><span data-stu-id="0cb51-105">Compensation vs. Transactions</span></span>  

 <span data-ttu-id="0cb51-106">トランザクションを使用することで、複数の操作を 1 つの作業単位にまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-106">A transaction allows you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="0cb51-107">アプリケーションでトランザクションを使用すると、トランザクションのプロセスでエラーが発生した場合、トランザクション内で実行されたすべての変更を中止 (ロールバック) できます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-107">Using a transaction gives your application the ability to abort (roll back) all changes executed from within the transaction if any errors occur during any part of the transaction process.</span></span> <span data-ttu-id="0cb51-108">ただし、作業が長時間実行されている場合は、トランザクションの使用が適切でないことがあります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-108">However, using transactions may not be appropriate if the work is long running.</span></span> <span data-ttu-id="0cb51-109">たとえば、旅行計画用アプリケーションはワークフローとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-109">For example, a travel planning application is implemented as a workflow.</span></span> <span data-ttu-id="0cb51-110">このワークフローの手順は、フライトの予約、マネージャーによる承認の待機、およびチケットの支払いで構成されていることがあります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-110">The steps of the workflow may consist of booking a flight, waiting for manager approval, and then paying for the flight.</span></span> <span data-ttu-id="0cb51-111">このプロセスには数日かかる場合があり、フライトの予約と支払いの手順を同じトランザクションに参加させるのは実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="0cb51-111">This process could take many days and it is not practical for the steps of booking and paying for the flight to participate in the same transaction.</span></span> <span data-ttu-id="0cb51-112">このようなシナリオでは、処理の後半でエラーが発生した場合、補正を使用してワークフローの予約の手順を取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-112">In a scenario such as this, compensation could be used to undo the booking step of the workflow if there is a failure later in the processing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cb51-113">このトピックでは、ワーク フローの補正について説明します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-113">This topic covers compensation in workflows.</span></span> <span data-ttu-id="0cb51-114">ワークフローのトランザクションの詳細については、「 [トランザクション](workflow-transactions.md) 」と「」を参照してください <xref:System.Activities.Statements.TransactionScope> 。</span><span class="sxs-lookup"><span data-stu-id="0cb51-114">For more information about transactions in workflows, see [Transactions](workflow-transactions.md) and <xref:System.Activities.Statements.TransactionScope>.</span></span> <span data-ttu-id="0cb51-115">トランザクションの詳細については、「」および「」を参照してください <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.Transaction?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="0cb51-115">For more information about transactions, see <xref:System.Transactions?displayProperty=nameWithType> and <xref:System.Transactions.Transaction?displayProperty=nameWithType>.</span></span>  
  
## <a name="using-compensableactivity"></a><span data-ttu-id="0cb51-116">CompensableActivity の使用</span><span class="sxs-lookup"><span data-stu-id="0cb51-116">Using CompensableActivity</span></span>  

 <span data-ttu-id="0cb51-117"><xref:System.Activities.Statements.CompensableActivity> は、[!INCLUDE[wf1](../../../includes/wf1-md.md)] の中心的な補正アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-117"><xref:System.Activities.Statements.CompensableActivity> is the core compensation activity in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="0cb51-118">補正が必要な可能性がある作業を実行するアクティビティは、すべて <xref:System.Activities.Statements.CompensableActivity.Body%2A> の <xref:System.Activities.Statements.CompensableActivity> に配置されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-118">Any activities that perform work that may need to be compensated are placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="0cb51-119">この例では、航空券を購入する予約手順を <xref:System.Activities.Statements.CompensableActivity.Body%2A> の <xref:System.Activities.Statements.CompensableActivity> に配置し、予約の取り消しを <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> に配置します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-119">In this example, the reservation step of purchasing a flight is placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> and the cancellation of the reservation is placed into the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>.</span></span> <span data-ttu-id="0cb51-120">ワークフロー内の <xref:System.Activities.Statements.CompensableActivity> の直後には、マネージャーの承認を待ち、航空券の購入手順を完了するという 2 つのアクティビティがあります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-120">Immediately following the <xref:System.Activities.Statements.CompensableActivity> in the workflow are two activities that wait for manager approval and then complete the purchasing step of the flight.</span></span> <span data-ttu-id="0cb51-121"><xref:System.Activities.Statements.CompensableActivity> が正常に完了した後に、エラー条件によってワークフローが取り消された場合、<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> ハンドラー内のアクティビティがスケジュールされ、航空券は取り消されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-121">If an error condition causes the workflow to be canceled after the <xref:System.Activities.Statements.CompensableActivity> has successfully completed, then the activities in the <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> handler are scheduled and the flight is canceled.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 <span data-ttu-id="0cb51-122">次の例は XAML のワークフローです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-122">The following example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="0cb51-123">このワークフローが呼び出されると、次の出力がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-123">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="0cb51-124">**ReserveFlight: チケットは予約されています。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-124">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="0cb51-125">**Managerapproval: マネージャーの承認を受け取りました。** 
**PurchaseFlight: チケットが購入されます。** 
**ワークフローは正常に完了しました。状態: Closed。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-125">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**Workflow completed successfully with status: Closed.**</span></span>
> [!NOTE]
> <span data-ttu-id="0cb51-126">`ReserveFlight` などのこのトピックのサンプル アクティビティでは、コンソールにアクティビティの名前や目的が表示されるため、補正が行われるときのアクティビティの順序がわかりやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="0cb51-126">The sample activities in this topic such as `ReserveFlight` display their name and purpose to the console to help illustrate the order in which the activities are executed when compensation occurs.</span></span>  
  
### <a name="default-workflow-compensation"></a><span data-ttu-id="0cb51-127">既定のワークフローの補正</span><span class="sxs-lookup"><span data-stu-id="0cb51-127">Default Workflow Compensation</span></span>  

 <span data-ttu-id="0cb51-128">既定では、ワークフローを取り消すと、正常に完了済みであるがまだ確認または補正されていない補正可能なアクティビティに対して、補正ロジックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-128">By default, if the workflow is canceled, the compensation logic is run for any compensable activity that has successfully completely and has not already been confirmed or compensated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cb51-129"><xref:System.Activities.Statements.CompensableActivity>が *確認* されると、アクティビティの補正を呼び出すことができなくなります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-129">When a <xref:System.Activities.Statements.CompensableActivity> is *confirmed*, compensation for the activity can no longer be invoked.</span></span> <span data-ttu-id="0cb51-130">確認プロセスについては、このセクションの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-130">The confirmation process is described later in this section.</span></span>  
  
 <span data-ttu-id="0cb51-131">この例では、航空券の予約後かつマネージャーの承認手順前に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-131">In this example, an exception is thrown after the flight is reserved but before the manager approval step.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 <span data-ttu-id="0cb51-132">この例は XAML のワークフローです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-132">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 <span data-ttu-id="0cb51-133">ワークフローが呼び出されると、シミュレートされたエラー状態の例外が <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> のホスト アプリケーションで処理されて、ワークフローが取り消され、補正ロジックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-133">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the compensation logic is invoked.</span></span>  
  
 <span data-ttu-id="0cb51-134">**ReserveFlight: チケットは予約されています。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-134">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="0cb51-135">**SimulatedErrorCondition: ApplicationException をスローしています。** 
**ワークフローのハンドルされない例外:** 
**ApplicationException: ワークフロー** 
 でのシミュレートされたエラー状態。**Cancelflight: チケットは取り消されました。** 
**ワークフローは正常に完了しました。状態: キャンセル。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-135">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Canceled.**</span></span>

### <a name="cancellation-and-compensableactivity"></a><span data-ttu-id="0cb51-136">取り消しと CompensableActivity</span><span class="sxs-lookup"><span data-stu-id="0cb51-136">Cancellation and CompensableActivity</span></span>  

 <span data-ttu-id="0cb51-137"><xref:System.Activities.Statements.CompensableActivity.Body%2A> の <xref:System.Activities.Statements.CompensableActivity> 内のアクティビティが完了せず、アクティビティが取り消されると、<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> が実行されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-137">If the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of a <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled, the activities in the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> are executed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cb51-138"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> が呼び出されるのは、<xref:System.Activities.Statements.CompensableActivity.Body%2A> の <xref:System.Activities.Statements.CompensableActivity> 内のアクティビティが完了せず、アクティビティが取り消された場合だけです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-138">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is only invoked if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have not completed and the activity is canceled.</span></span> <span data-ttu-id="0cb51-139"><xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> は、<xref:System.Activities.Statements.CompensableActivity.Body%2A> の <xref:System.Activities.Statements.CompensableActivity> 内のアクティビティが正常に完了し、その後にアクティビティで補正が呼び出された場合にのみ実行されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-139">The <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> is only executed if the activities in the <xref:System.Activities.Statements.CompensableActivity.Body%2A> of the <xref:System.Activities.Statements.CompensableActivity> have successfully completed and compensation is subsequently invoked on the activity.</span></span>  
  
 <span data-ttu-id="0cb51-140"><xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> を使用すると、ワークフローの作成者は、適切な取り消しロジックを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-140">The <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> gives workflow authors the opportunity to provide any appropriate cancellation logic.</span></span> <span data-ttu-id="0cb51-141">次の例では、<xref:System.Activities.Statements.CompensableActivity.Body%2A> の実行中に例外がスローされてから、<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-141">In the following example, an exception is thrown during the execution of the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, and then the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> is invoked.</span></span>  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 <span data-ttu-id="0cb51-142">この例は XAML のワークフローです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-142">This example is the workflow in XAML</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 <span data-ttu-id="0cb51-143">ワークフローが呼び出されると、シミュレートされたエラー状態の例外が、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> のホスト アプリケーションで処理されて、ワークフローが取り消され、<xref:System.Activities.Statements.CompensableActivity> の取り消しロジックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-143">When the workflow is invoked, the simulated error condition exception is handled by the host application in <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, the workflow is canceled, and the cancellation logic of the <xref:System.Activities.Statements.CompensableActivity> is invoked.</span></span> <span data-ttu-id="0cb51-144">この例では、補正ロジックと取り消しロジックの目的は異なります</span><span class="sxs-lookup"><span data-stu-id="0cb51-144">In this example, the compensation logic and the cancellation logic have different goals.</span></span> <span data-ttu-id="0cb51-145"><xref:System.Activities.Statements.CompensableActivity.Body%2A> が正常に完了した場合、これはクレジット カードに課金されてフライトが予約されたことを意味するので、補正で両方の手順を取り消す必要があります</span><span class="sxs-lookup"><span data-stu-id="0cb51-145">If the <xref:System.Activities.Statements.CompensableActivity.Body%2A> completed successfully, then this means the credit card was charged and the flight booked, so the compensation should undo both steps.</span></span> <span data-ttu-id="0cb51-146">(この例では、フライトをキャンセルすると、クレジットカードの料金が自動的にキャンセルされます)。ただし、が取り消された場合は、が <xref:System.Activities.Statements.CompensableActivity> 完了していないことを意味し <xref:System.Activities.Statements.CompensableActivity.Body%2A> ます。そのため、のロジックは、 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> キャンセルを適切に処理する方法を決定できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-146">(In this example, canceling the flight automatically cancels the credit card charges.) However, if the <xref:System.Activities.Statements.CompensableActivity> is canceled, this means the <xref:System.Activities.Statements.CompensableActivity.Body%2A> did not complete and so the logic of the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> needs to be able to determine how to best handle the cancellation.</span></span> <span data-ttu-id="0cb51-147">この例では、<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> はクレジット カードへの課金を取り消しますが、`ReserveFlight` は <xref:System.Activities.Statements.CompensableActivity.Body%2A> の最後のアクティビティであるので、航空券の取り消しを試みません。</span><span class="sxs-lookup"><span data-stu-id="0cb51-147">In this example, the <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> cancels the credit card charge, but since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, it does not attempt to cancel the flight.</span></span> <span data-ttu-id="0cb51-148">`ReserveFlight` は <xref:System.Activities.Statements.CompensableActivity.Body%2A> の最後のアクティビティであるので、そのアクティビティが正常に完了して <xref:System.Activities.Statements.CompensableActivity.Body%2A> が完了すると、取り消しは不可能となります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-148">Since `ReserveFlight` was the last activity in the <xref:System.Activities.Statements.CompensableActivity.Body%2A>, if it had successfully completed then the <xref:System.Activities.Statements.CompensableActivity.Body%2A> would have completed and no cancellation would be possible.</span></span>  
  
 <span data-ttu-id="0cb51-149">**ChargeCreditCard: 航空券の料金をクレジット カードに請求します。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-149">**ChargeCreditCard: Charge credit card for flight.**</span></span>  
<span data-ttu-id="0cb51-150">**SimulatedErrorCondition: ApplicationException をスローしています。** 
**ワークフローのハンドルされない例外:** 
**ApplicationException: ワークフロー** 
 でのシミュレートされたエラー状態。**CancelCreditCard: クレジットカードの請求をキャンセルします。** 
**ワークフローは正常に完了しました。状態: キャンセル。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-150">**SimulatedErrorCondition: Throwing an ApplicationException.**
**Workflow Unhandled Exception:**
**System.ApplicationException: Simulated error condition in the workflow.**
**CancelCreditCard: Cancel credit card charges.**
**Workflow completed successfully with status: Canceled.**</span></span>  <span data-ttu-id="0cb51-151">取り消しの詳細については、「 [キャンセル](modeling-cancellation-behavior-in-workflows.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cb51-151">For more information about cancellation, see [Cancellation](modeling-cancellation-behavior-in-workflows.md).</span></span>  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a><span data-ttu-id="0cb51-152">Compensate アクティビティを使用する明示的な補正</span><span class="sxs-lookup"><span data-stu-id="0cb51-152">Explicit Compensation Using the Compensate Activity</span></span>  

 <span data-ttu-id="0cb51-153">前のセクションでは、暗黙的な補正について説明しました。</span><span class="sxs-lookup"><span data-stu-id="0cb51-153">In the previous section, implicit compensation was covered.</span></span> <span data-ttu-id="0cb51-154">暗黙的な補正は単純なシナリオには適していますが、補正処理のスケジュールに関して、より明示的な制御が必要な場合は、<xref:System.Activities.Statements.Compensate> アクティビティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-154">Implicit compensation can be appropriate for simple scenarios, but if more explicit control is required over the scheduling of compensation handling then the <xref:System.Activities.Statements.Compensate> activity can be used.</span></span> <span data-ttu-id="0cb51-155"><xref:System.Activities.Statements.Compensate> アクティビティを使用して補正プロセスを開始するには、補正が望ましい <xref:System.Activities.Statements.CompensationToken> の <xref:System.Activities.Statements.CompensableActivity> を使用します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-155">To initiate the compensation process with the <xref:System.Activities.Statements.Compensate> activity, the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> for which compensation is desired is used.</span></span> <span data-ttu-id="0cb51-156"><xref:System.Activities.Statements.Compensate> アクティビティは、完了した <xref:System.Activities.Statements.CompensableActivity> で、まだ確認または補正されていない場合に補正を開始するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-156">The <xref:System.Activities.Statements.Compensate> activity can be used to initiate compensation on any completed <xref:System.Activities.Statements.CompensableActivity> that has not been confirmed or compensated.</span></span> <span data-ttu-id="0cb51-157">たとえば、<xref:System.Activities.Statements.Compensate> アクティビティは <xref:System.Activities.Statements.TryCatch.Catches%2A> アクティビティの <xref:System.Activities.Statements.TryCatch> セクションで使用できます。また、<xref:System.Activities.Statements.CompensableActivity> が完了した後の任意のタイミングで使用できます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-157">For example, a <xref:System.Activities.Statements.Compensate> activity could be used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity, or any time after the <xref:System.Activities.Statements.CompensableActivity> has completed.</span></span> <span data-ttu-id="0cb51-158">この例では、<xref:System.Activities.Statements.Compensate> アクティビティを <xref:System.Activities.Statements.TryCatch.Catches%2A> アクティビティの <xref:System.Activities.Statements.TryCatch> プロパティに使用し、<xref:System.Activities.Statements.CompensableActivity> のアクションを反転します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-158">In this example, the <xref:System.Activities.Statements.Compensate> activity is used in the <xref:System.Activities.Statements.TryCatch.Catches%2A> section of a <xref:System.Activities.Statements.TryCatch> activity to reverse the action of the <xref:System.Activities.Statements.CompensableActivity>.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 <span data-ttu-id="0cb51-159">この例は XAML のワークフローです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-159">This example is the workflow in XAML.</span></span>  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 <span data-ttu-id="0cb51-160">このワークフローが呼び出されると、次の出力がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-160">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
 <span data-ttu-id="0cb51-161">**ReserveFlight: チケットは予約されています。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-161">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="0cb51-162">**SimulatedErrorCondition: ApplicationException をスローしています。** 
**Cancelflight: チケットは取り消されました。** 
**ワークフローは正常に完了しました。状態: Closed。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-162">**SimulatedErrorCondition: Throwing an ApplicationException.**
**CancelFlight: Ticket is canceled.**
**Workflow completed successfully with status: Closed.**</span></span>

### <a name="confirming-compensation"></a><span data-ttu-id="0cb51-163">補正の確認</span><span class="sxs-lookup"><span data-stu-id="0cb51-163">Confirming Compensation</span></span>  

 <span data-ttu-id="0cb51-164">既定で、補正可能なアクティビティは、完了後の任意のタイミングで補正できます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-164">By default, compensable activities can be compensated any time after they have completed.</span></span> <span data-ttu-id="0cb51-165">ただし、シナリオによっては適切でない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-165">In some scenarios this may not be appropriate.</span></span> <span data-ttu-id="0cb51-166">前の例では、航空券予約の補正は、予約の取り消しでした。</span><span class="sxs-lookup"><span data-stu-id="0cb51-166">In the previous example the compensation to reserving the ticket was to cancel the reservation.</span></span> <span data-ttu-id="0cb51-167">ただし、この航空券に関する処理が完了すると、この補正手順は有効ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-167">However, after the flight has been completed this compensation step is no longer valid.</span></span> <span data-ttu-id="0cb51-168">補正可能なアクティビティを確認すると、<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> で指定したアクティビティが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-168">Confirming the compensable activity invokes the activity specified by the <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>.</span></span> <span data-ttu-id="0cb51-169">この使用例としては、補正を実行する必要があるリソースを解放できるようになることが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-169">One possible use for this is to allow any resources that are necessary to perform the compensation to be released.</span></span> <span data-ttu-id="0cb51-170">補正可能なアクティビティは、確認されると補正できなくなります。また、この処理が試行されると、<xref:System.InvalidOperationException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-170">After a compensable activity is confirmed it is not possible for it to be compensated, and if this is attempted an <xref:System.InvalidOperationException> exception is thrown.</span></span> <span data-ttu-id="0cb51-171">ワークフローが正常に完了すると、正常に完了したがまだ確認も補正も実行されていない補正可能なすべてのアクティビティは、補正とは逆の順序で確認されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-171">When a workflow completes successfully, all non-confirmed and non-compensated compensable activities that completed successfully are confirmed in reverse order of completion.</span></span> <span data-ttu-id="0cb51-172">この例では、航空券の予約、購入、および完了後に、補正可能なアクティビティが確認されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-172">In this example the flight is reserved, purchased, and completed, and then the compensable activity is confirmed.</span></span> <span data-ttu-id="0cb51-173"><xref:System.Activities.Statements.CompensableActivity> を確認するには、<xref:System.Activities.Statements.Confirm> アクティビティを使用し、<xref:System.Activities.Statements.CompensationToken> の <xref:System.Activities.Statements.CompensableActivity> を指定します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-173">To confirm a <xref:System.Activities.Statements.CompensableActivity>, use the <xref:System.Activities.Statements.Confirm> activity and specify the <xref:System.Activities.Statements.CompensationToken> of the <xref:System.Activities.Statements.CompensableActivity> to confirm.</span></span>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 <span data-ttu-id="0cb51-174">この例は XAML のワークフローです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-174">This example is the workflow in XAML.</span></span>  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
<span data-ttu-id="0cb51-175">このワークフローが呼び出されると、次の出力がコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-175">When the workflow is invoked, the following output is displayed to the console.</span></span>  
  
<span data-ttu-id="0cb51-176">**ReserveFlight: チケットは予約されています。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-176">**ReserveFlight: Ticket is reserved.**</span></span>  
<span data-ttu-id="0cb51-177">**Managerapproval: マネージャーの承認を受け取りました。** 
**PurchaseFlight: チケットが購入されます。** 
**動力飛行: フライトが完了しました。** 
**Confirmflight: フライトが実行されました。補正することはできません。** 
**ワークフローは正常に完了しました。状態: Closed。**</span><span class="sxs-lookup"><span data-stu-id="0cb51-177">**ManagerApproval: Manager approval received.**
**PurchaseFlight: Ticket is purchased.**
**TakeFlight: Flight is completed.**
**ConfirmFlight: Flight has been taken, no compensation possible.**
**Workflow completed successfully with status: Closed.**</span></span>

## <a name="nesting-compensation-activities"></a><span data-ttu-id="0cb51-178">補正アクティビティの入れ子化</span><span class="sxs-lookup"><span data-stu-id="0cb51-178">Nesting Compensation Activities</span></span>  

<span data-ttu-id="0cb51-179"><xref:System.Activities.Statements.CompensableActivity> は、別の <xref:System.Activities.Statements.CompensableActivity.Body%2A> の <xref:System.Activities.Statements.CompensableActivity> セクションに配置できます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-179">A <xref:System.Activities.Statements.CompensableActivity> can be placed into the <xref:System.Activities.Statements.CompensableActivity.Body%2A> section of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="0cb51-180"><xref:System.Activities.Statements.CompensableActivity> は、別の <xref:System.Activities.Statements.CompensableActivity> のハンドラーで処理されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="0cb51-180">A <xref:System.Activities.Statements.CompensableActivity> may not be placed into a handler of another <xref:System.Activities.Statements.CompensableActivity>.</span></span> <span data-ttu-id="0cb51-181">親の <xref:System.Activities.Statements.CompensableActivity> が取り消されたとき、確認されたとき、または補正されたとき、正常に完了していてまだ確認または補正されていないすべての子の補正可能なアクティビティを、親が取り消し、確認、または補正を完了する前に、確認または補正されるようにするのが親のそのアクティビティの役割ですです。</span><span class="sxs-lookup"><span data-stu-id="0cb51-181">It is the responsibility of a parent <xref:System.Activities.Statements.CompensableActivity> to ensure that when it is canceled, confirmed, or compensated, all child compensable activities that have completed successfully and have not already been confirmed or compensated must be confirmed or compensated before the parent completes cancellation, confirmation, or compensation.</span></span> <span data-ttu-id="0cb51-182">補正が明示的にモデル化されていない場合、親の <xref:System.Activities.Statements.CompensableActivity> は、親が取り消しまたは補正のシグナルを受け取ったとき、子の補正可能なアクティビティを暗黙的に補正します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-182">If this is not modeled explicitly the parent <xref:System.Activities.Statements.CompensableActivity> will implicitly compensate child compensable activities if the parent received the cancel or compensate signal.</span></span> <span data-ttu-id="0cb51-183">親は、確認通知を受け取ると、暗黙的に子の補正可能なアクティビティを確認します。</span><span class="sxs-lookup"><span data-stu-id="0cb51-183">If the parent received the confirm signal the parent will implicitly confirm child compensable activities.</span></span> <span data-ttu-id="0cb51-184">取り消し、確認、または補正を処理するロジックが親の <xref:System.Activities.Statements.CompensableActivity> のハンドラーで明示的にモデル化されている場合、明示的に処理されなかった子は暗黙的に確認されます。</span><span class="sxs-lookup"><span data-stu-id="0cb51-184">If the logic to handle cancellation, confirmation, or compensation is explicitly modeled in the handler of the parent <xref:System.Activities.Statements.CompensableActivity>, any child not explicitly handled will be implicitly confirmed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb51-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cb51-185">See also</span></span>

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>
