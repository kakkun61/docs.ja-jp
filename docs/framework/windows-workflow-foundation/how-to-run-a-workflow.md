---
title: '方法: ワークフローを実行する'
description: この記事では、ワークフローホストを作成し、この Windows Workflow Foundation チュートリアルシリーズの前の記事で定義したワークフローを実行する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
ms.openlocfilehash: b92385fa169e03254abdf940f2964c1966cbc2ce
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190092"
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="7a091-103">方法: ワークフローを実行する</span><span class="sxs-lookup"><span data-stu-id="7a091-103">How to: Run a Workflow</span></span>

<span data-ttu-id="7a091-104">このトピックでは、Windows Workflow Foundation チュートリアル入門の続きと、ワークフロー ホストを作成して、前の「 [How to: Create a Workflow](how-to-create-a-workflow.md) 」で定義したワークフローを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a091-104">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="7a091-105">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="7a091-105">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="7a091-106">このトピックを完了する前に、「 [How to: Create an Activity](how-to-create-an-activity.md) 」および「 [How to: Create a Workflow](how-to-create-a-workflow.md)」を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a091-106">To complete this topic you must first complete [How to: Create an Activity](how-to-create-an-activity.md) and [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="7a091-107">ワークフロー ホスト プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="7a091-107">To create the workflow host project</span></span>  
  
1. <span data-ttu-id="7a091-108">Visual Studio 2012 を使用して、前の「 [方法: アクティビティの作成](how-to-create-an-activity.md) 」トピックからソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="7a091-108">Open the solution from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic by using Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="7a091-109">**ソリューション エクスプローラー** で **WF45GettingStartedTutorial** ソリューションを右クリックし、 **[追加]** をポイントして、 **[新しいプロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a091-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="7a091-110">[**ソリューション エクスプローラー**] ウィンドウが表示されていない場合は、[**表示**] メニューから [**ソリューション エクスプローラー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a091-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

3. <span data-ttu-id="7a091-111">**[インストール済み]** ノードで、 **[Visual C#]**、 **[ワークフロー]** (または **[Visual Basic]**、 **[ワークフロー]**) の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="7a091-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7a091-112">Visual Studio でのプライマリ言語の構成によっては、[**Visual C#**] または [**Visual Basic**] ノードが [**インストール**] ノードの [**他の言語**] ノードの下になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a091-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="7a091-113">[.NET Framework バージョン] ドロップダウン リストで [**.NET Framework 4.5**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7a091-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="7a091-114">**[ワークフロー]** の一覧から **[ワークフロー コンソール アプリケーション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a091-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="7a091-115">`NumberGuessWorkflowHost` [名前] **ボックスに「** 」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a091-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="7a091-116">これで、基本的なワークフロー ホスティングをサポートする、基本ワークフロー アプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7a091-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="7a091-117">この基本的なホスティング コードを変更し、ワークフロー アプリケーションの実行に使用します。</span><span class="sxs-lookup"><span data-stu-id="7a091-117">This basic hosting code is modified and used to run the workflow application.</span></span>

4. <span data-ttu-id="7a091-118">**ソリューション エクスプローラー** で新しく追加した **NumberGuessWorkflowHost** プロジェクトを右クリックし、 **[参照の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a091-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="7a091-119">**[参照の追加]** の一覧から **[ソリューション]** を選択し、 **NumberGuessWorkflowActivities** の横にあるチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a091-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>

5. <span data-ttu-id="7a091-120">**ソリューション エクスプローラー** で **Workflow1.xaml** を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7a091-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="7a091-121">**[OK]** をクリックして確定します。</span><span class="sxs-lookup"><span data-stu-id="7a091-121">Click **OK** to confirm.</span></span>

### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="7a091-122">ワークフロー ホスティング コードを変更するには</span><span class="sxs-lookup"><span data-stu-id="7a091-122">To modify the workflow hosting code</span></span>

1. <span data-ttu-id="7a091-123">**ソリューション エクスプローラー** で、 **Program.cs** または **Module1.vb** をダブルクリックしてコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7a091-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>

    > [!TIP]
    > <span data-ttu-id="7a091-124">[**ソリューション エクスプローラー**] ウィンドウが表示されていない場合は、[**表示**] メニューから [**ソリューション エクスプローラー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a091-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>

     <span data-ttu-id="7a091-125">このプロジェクトは **ワークフロー コンソール アプリケーション** テンプレートを使用して作成されたため、 **Program.cs** または **Module1.vb** には、次のようなワークフローの基本的なホスティング コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a091-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>

    ```vb
    ' Create and cache the workflow definition.
    Dim workflow1 As Activity = New Workflow1()
    WorkflowInvoker.Invoke(workflow1)
    ```

    ```csharp
    // Create and cache the workflow definition.
    Activity workflow1 = new Workflow1();
    WorkflowInvoker.Invoke(workflow1);
    ```

     <span data-ttu-id="7a091-126">この生成されたホスト コードでは <xref:System.Activities.WorkflowInvoker>を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a091-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="7a091-127"><xref:System.Activities.WorkflowInvoker> は、メソッド呼び出しのようにワークフローを呼び出す簡単な方法を提供し、永続化を使用しないワークフローのみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="7a091-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="7a091-128"><xref:System.Activities.WorkflowApplication> は、ライフ サイクル イベントの通知、実行制御、ブックマークの再開、および永続化を含むワークフローを実行するための豊富なモデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="7a091-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="7a091-129">次の例ではブックマークを使用し、ワークフローのホスティングには <xref:System.Activities.WorkflowApplication> を使用します。</span><span class="sxs-lookup"><span data-stu-id="7a091-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="7a091-130">`using` Program.cs **または** Module1.vb **の先頭にある既存の** using **ステートメントまたは** Imports **ステートメントの下に、次の** ステートメントまたは **Imports** ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7a091-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowActivities
    Imports System.Threading
    ```

    ```csharp
    using NumberGuessWorkflowActivities;
    using System.Threading;
    ```

     <span data-ttu-id="7a091-131"><xref:System.Activities.WorkflowInvoker> を使用するコード行を次の <xref:System.Activities.WorkflowApplication> の基本的なホスティング コードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="7a091-132">このサンプル ホスティング コードでは、ワークフローをホストして呼び出すための基本的な手順を示します。ただし、このトピックのワークフローを正しく実行するための機能はまだありません。</span><span class="sxs-lookup"><span data-stu-id="7a091-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="7a091-133">次の手順では、アプリケーションが完了するまでにこの基本的なコードを変更して機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="7a091-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7a091-134">前の「 `Workflow1` 」の手順で完了したワークフローに応じて、これらの例の `FlowchartNumberGuessWorkflow`をポイントして、 `SequentialNumberGuessWorkflow`、 `StateMachineNumberGuessWorkflow`、または [How to: Create a Workflow](how-to-create-a-workflow.md) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="7a091-135">`Workflow1` を置き換えないと、ワークフローをビルドまたは実行しようとするときにビルド エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7a091-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#4](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]

     <span data-ttu-id="7a091-136">このコードでは <xref:System.Activities.WorkflowApplication>を作成し、3 つのワークフローのライフサイクル イベントに定期受信し、 <xref:System.Activities.WorkflowApplication.Run%2A>を呼び出してワークフローを開始し、そのワークフローが完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="7a091-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="7a091-137">ワークフローが完了すると <xref:System.Threading.AutoResetEvent> が設定され、ホスト アプリケーションが完了します。</span><span class="sxs-lookup"><span data-stu-id="7a091-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>

### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="7a091-138">ワークフローの入力引数を設定するには</span><span class="sxs-lookup"><span data-stu-id="7a091-138">To set input arguments of a workflow</span></span>

1. <span data-ttu-id="7a091-139">**Program.cs** または **Module1.vb** の先頭にある既存の `using` ステートメントまたは `Imports` ステートメントの下に、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7a091-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#5](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]

2. <span data-ttu-id="7a091-140">新しい <xref:System.Activities.WorkflowApplication> を作成するコード行を、作成時にワークフローにパラメーターの辞書を作成して渡す次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7a091-141">前の「 `Workflow1` 」の手順で完了したワークフローに応じて、これらの例の `FlowchartNumberGuessWorkflow`をポイントして、 `SequentialNumberGuessWorkflow`、 `StateMachineNumberGuessWorkflow`、または [How to: Create a Workflow](how-to-create-a-workflow.md) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="7a091-142">`Workflow1` を置き換えないと、ワークフローをビルドまたは実行しようとするときにビルド エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7a091-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="7a091-143">この辞書には、 `MaxNumber`というキーを持つ 1 つの要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a091-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="7a091-144">入力辞書のキーは、ワークフローのルート アクティビティの入力引数に対応します。</span><span class="sxs-lookup"><span data-stu-id="7a091-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="7a091-145">`MaxNumber` は、ランダムに生成される数値の上限を決定するためにワークフローによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a091-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>

### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="7a091-146">ワークフローの出力引数を取得するには</span><span class="sxs-lookup"><span data-stu-id="7a091-146">To retrieve output arguments of a workflow</span></span>

1. <span data-ttu-id="7a091-147"><xref:System.Activities.WorkflowApplication.Completed%2A> ハンドラーを変更して、ワークフローが使用する順番の数を取得して表示します。</span><span class="sxs-lookup"><span data-stu-id="7a091-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#7](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]

### <a name="to-resume-a-bookmark"></a><span data-ttu-id="7a091-148">ブックマークを再開するには</span><span class="sxs-lookup"><span data-stu-id="7a091-148">To resume a bookmark</span></span>

1. <span data-ttu-id="7a091-149">`Main` メソッドの上部にある既存の <xref:System.Threading.AutoResetEvent> 宣言の直後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7a091-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#8](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]

2. <span data-ttu-id="7a091-150"><xref:System.Activities.WorkflowApplication.Idle%2A> にある既存の 3 つのワークフロー ライフサイクル ハンドラーの直後に、次の `Main`ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="7a091-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#9](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]

     <span data-ttu-id="7a091-151">ワークフローが次の推定値を待機してアイドル状態になるたびに、このハンドラーが呼び出され、 `idleAction` <xref:System.Threading.AutoResetEvent> が設定されます。</span><span class="sxs-lookup"><span data-stu-id="7a091-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="7a091-152">次の手順のコードでは、 `idleEvent` と `syncEvent` を使用して、ワークフローが次の推定値を待機しているのか、完了しているのかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7a091-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7a091-153">この例では、ホスト アプリケーションは <xref:System.Activities.WorkflowApplication.Completed%2A> および <xref:System.Activities.WorkflowApplication.Idle%2A> ハンドラーの自動リセット イベントを使用して、ホスト アプリケーションとワークフローの進行状況を同期させます。</span><span class="sxs-lookup"><span data-stu-id="7a091-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="7a091-154">ブックマークを再開する前にワークフローがアイドル状態になるのをブロックして待機する必要はありませんが、この例では同期イベントが必要であるため、ホストはワークフローが完了しているのか、さらにユーザーの入力を待っているのかを <xref:System.Activities.Bookmark>を使用して把握します。</span><span class="sxs-lookup"><span data-stu-id="7a091-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> <span data-ttu-id="7a091-155">詳細については、「 [ブックマーク](bookmarks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a091-155">For more information, see [Bookmarks](bookmarks.md).</span></span>

3. <span data-ttu-id="7a091-156">`WaitOne`への呼び出しを削除して、ユーザーからの入力を収集して <xref:System.Activities.Bookmark>を再開するためのコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>

     <span data-ttu-id="7a091-157">次のコード行を削除します。</span><span class="sxs-lookup"><span data-stu-id="7a091-157">Remove the following line of code.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#10](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]

     <span data-ttu-id="7a091-158">これを次の例に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-158">Replace it with the following example.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#11](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]

## <a name="to-build-and-run-the-application"></a><a name="BKMK_ToRunTheApplication"></a> <span data-ttu-id="7a091-159">アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="7a091-159">To build and run the application</span></span>

1. <span data-ttu-id="7a091-160">**ソリューション エクスプローラー** で **NumberGuessWorkflowHost** を右クリックして **[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a091-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="7a091-161">Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="7a091-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="7a091-162">できるだけ早い順番の数を推測します。</span><span class="sxs-lookup"><span data-stu-id="7a091-162">Try to guess the number in as few turns as possible.</span></span>

     <span data-ttu-id="7a091-163">他のスタイルのワークフローのいずれかでアプリケーションを試すには、目的のワークフローのスタイルに応じて、 `Workflow1` を作成するコード内の <xref:System.Activities.WorkflowApplication> を、 `FlowchartNumberGuessWorkflow`、 `SequentialNumberGuessWorkflow`、または `StateMachineNumberGuessWorkflow`に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#6](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]

     <span data-ttu-id="7a091-164">ワークフロー アプリケーションに永続化を追加する方法については、次のトピック「 [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a091-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md).</span></span>

## <a name="example"></a><span data-ttu-id="7a091-165">例</span><span class="sxs-lookup"><span data-stu-id="7a091-165">Example</span></span>

 <span data-ttu-id="7a091-166">次の例では、 `Main` メソッドの完全なコードの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7a091-166">The following example is the complete code listing for the `Main` method.</span></span>

> [!NOTE]
> <span data-ttu-id="7a091-167">前の「 `Workflow1` 」の手順で完了したワークフローに応じて、これらの例の `FlowchartNumberGuessWorkflow`をポイントして、 `SequentialNumberGuessWorkflow`、 `StateMachineNumberGuessWorkflow`、または [How to: Create a Workflow](how-to-create-a-workflow.md) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7a091-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="7a091-168">`Workflow1` を置き換えないと、ワークフローをビルドまたは実行しようとするときにビルド エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7a091-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>

 [!code-csharp[CFX_WF_GettingStarted#12](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]

## <a name="see-also"></a><span data-ttu-id="7a091-169">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="7a091-169">See also</span></span>

- <xref:System.Activities.WorkflowApplication>
- <xref:System.Activities.Bookmark>
- [<span data-ttu-id="7a091-170">Windows Workflow Foundation プログラミングの新機能</span><span class="sxs-lookup"><span data-stu-id="7a091-170">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="7a091-171">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="7a091-171">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="7a091-172">方法: ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="7a091-172">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="7a091-173">方法: 長時間にわたって実行されるワークフローを作成して実行する</span><span class="sxs-lookup"><span data-stu-id="7a091-173">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)
- [<span data-ttu-id="7a091-174">ワークフロー内での入力の待機</span><span class="sxs-lookup"><span data-stu-id="7a091-174">Waiting for Input in a Workflow</span></span>](waiting-for-input-in-a-workflow.md)
- [<span data-ttu-id="7a091-175">ワークフローのホスティング</span><span class="sxs-lookup"><span data-stu-id="7a091-175">Hosting Workflows</span></span>](hosting-workflows.md)
