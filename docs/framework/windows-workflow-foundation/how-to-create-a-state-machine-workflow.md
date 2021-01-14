---
title: '方法: ステート マシン ワークフローを作成する'
description: この記事では、StateMachine アクティビティなどの組み込みアクティビティとカスタムアクティビティの両方を使用するワークフローを作成します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3ec60e8f-fad4-493e-a426-e7962d7aee8c
ms.openlocfilehash: 8e977a182d55143f8d877d61a0f0345bbe6bded4
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190469"
---
# <a name="how-to-create-a-state-machine-workflow"></a><span data-ttu-id="4b681-103">方法: ステート マシン ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="4b681-103">How to: Create a State Machine Workflow</span></span>

<span data-ttu-id="4b681-104">ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。</span><span class="sxs-lookup"><span data-stu-id="4b681-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="4b681-105">このトピックでは、アクティビティなどの組み込みのアクティビティ <xref:System.Activities.Statements.StateMachine> と、前の「 [How To: Create a activity](how-to-create-an-activity.md) 」のカスタムアクティビティの両方を使用するワークフローを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b681-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.StateMachine> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="4b681-106">このワークフローは、数値推測ゲームをモデル化しています。</span><span class="sxs-lookup"><span data-stu-id="4b681-106">The workflow models a number guessing game.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b681-107">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="4b681-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="4b681-108">このトピックを完了するには、まず「 [方法: アクティビティを作成](how-to-create-an-activity.md)する」を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b681-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
### <a name="to-create-the-workflow"></a><span data-ttu-id="4b681-109">ワークフローを作成するには</span><span class="sxs-lookup"><span data-stu-id="4b681-109">To create the workflow</span></span>  
  
1. <span data-ttu-id="4b681-110">**ソリューションエクスプローラー** で [ **NumberGuessWorkflowActivities** ] を右クリックし、[**追加**]、[**新しい項目**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="4b681-110">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>  
  
2. <span data-ttu-id="4b681-111">[ **インストール済み**] の [ **共通項目** ] ノードで、[ **ワークフロー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b681-111">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="4b681-112">[**ワークフロー**] 一覧から [**アクティビティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b681-112">Select **Activity** from the **Workflow** list.</span></span>  
  
3. <span data-ttu-id="4b681-113">`StateMachineNumberGuessWorkflow`[**名前**] ボックスに「」と入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b681-113">Type `StateMachineNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>  
  
4. <span data-ttu-id="4b681-114">**ツールボックス** の [**ステートマシン**] セクションから **StateMachine** アクティビティをドラッグし、ワークフローデザインサーフェイスの [**ここにアクティビティをドロップ**] ラベルにドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-114">Drag a **StateMachine** activity from the **State Machine** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>  
  
### <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="4b681-115">ワークフロー変数および引数を作成するには</span><span class="sxs-lookup"><span data-stu-id="4b681-115">To create the workflow variables and arguments</span></span>  
  
1. <span data-ttu-id="4b681-116">**ソリューションエクスプローラー** で **statemachinenumberguessworkflow.xaml** をダブルクリックして、ワークフローをデザイナーに表示します (まだ表示されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="4b681-116">Double-click **StateMachineNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>  
  
2. <span data-ttu-id="4b681-117">ワークフローデザイナーの左下にある [ **引数** ] をクリックして、[ **引数** ] ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="4b681-117">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>  
  
3. <span data-ttu-id="4b681-118">[**Create Argument**] (引数の作成) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b681-118">Click **Create Argument**.</span></span>  
  
4. <span data-ttu-id="4b681-119">[名前] ボックスに「」と入力し、[ `MaxNumber` **方向**] ドロップダウンリストから [ **In** ] を選択します。次に、[**引数の型**] ドロップダウンリストから [ **Int32** ] を選択し、enter キーを押して引数を保存します。 </span><span class="sxs-lookup"><span data-stu-id="4b681-119">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>  
  
5. <span data-ttu-id="4b681-120">[**Create Argument**] (引数の作成) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b681-120">Click **Create Argument**.</span></span>  
  
6. <span data-ttu-id="4b681-121">`Turns`新しく追加された引数の下にある [**名前**] ボックスに「」と入力し、 `MaxNumber` [**方向**] ドロップダウンリストから [ **Out** ] を選択します。次に、[**引数の型**] ドロップダウンリストから [ **Int32** ] を選択し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4b681-121">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>  
  
7. <span data-ttu-id="4b681-122">アクティビティ デザイナーの左下にある [**引数**] をクリックして、[**引数**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4b681-122">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>  
  
8. <span data-ttu-id="4b681-123">ワークフローデザイナーの左下にある [ **変数** ] をクリックして、[ **変数** ] ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="4b681-123">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>  
  
9. <span data-ttu-id="4b681-124">[**変数の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b681-124">Click **Create Variable**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="4b681-125">[ **変数の作成** ] ボックスが表示されない場合は、 <xref:System.Activities.Statements.StateMachine> ワークフローデザイナー画面でアクティビティをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="4b681-125">If no **Create Variable** box is displayed, click the <xref:System.Activities.Statements.StateMachine> activity on the workflow designer surface to select it.</span></span>  
  
10. <span data-ttu-id="4b681-126">[ `Guess` **名前**] ボックスに「」と入力し、[**変数の型**] ドロップダウンリストから [ **Int32** ] を選択します。次に、enter キーを押して変数を保存します。</span><span class="sxs-lookup"><span data-stu-id="4b681-126">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
11. <span data-ttu-id="4b681-127">[**変数の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b681-127">Click **Create Variable**.</span></span>  
  
12. <span data-ttu-id="4b681-128">[ `Target` **名前**] ボックスに「」と入力し、[**変数の型**] ドロップダウンリストから [ **Int32** ] を選択します。次に、enter キーを押して変数を保存します。</span><span class="sxs-lookup"><span data-stu-id="4b681-128">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>  
  
13. <span data-ttu-id="4b681-129">アクティビティ デザイナーの左下にある [**変数**] をクリックして、[**変数**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4b681-129">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>  
  
### <a name="to-add-the-workflow-activities"></a><span data-ttu-id="4b681-130">ワークフロー アクティビティを追加するには</span><span class="sxs-lookup"><span data-stu-id="4b681-130">To add the workflow activities</span></span>  
  
1. <span data-ttu-id="4b681-131">[ **State1** ] をクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="4b681-131">Click **State1** to select it.</span></span> <span data-ttu-id="4b681-132">[ **プロパティ] ウィンドウ** で、 **DisplayName** をに変更し `Initialize Target` ます。</span><span class="sxs-lookup"><span data-stu-id="4b681-132">In the **Properties Window**, change the **DisplayName** to `Initialize Target`.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="4b681-133">[**プロパティ] ウィンドウ** が表示されていない場合は、[**表示**] メニューの [**プロパティウィンドウ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b681-133">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>  
  
2. <span data-ttu-id="4b681-134">ワークフローデザイナーで、新しく名前を変更した [ **初期化のターゲット** ] 状態をダブルクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4b681-134">Double-click the newly renamed **Initialize Target** state in the workflow designer to expand it.</span></span>  
  
3. <span data-ttu-id="4b681-135">**ツールボックス** の [**プリミティブ**] セクションから **Assign** アクティビティをドラッグし、状態の **Entry** セクションにドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-135">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span> <span data-ttu-id="4b681-136">[ `Target` **To** ] ボックスに「」と入力し、[ **C# の式を入力** するか、VB の式を **入力** してください] ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-136">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
    ```vb  
    New System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    ```csharp  
    new System.Random().Next(1, MaxNumber + 1)  
    ```  
  
    > [!TIP]
    > <span data-ttu-id="4b681-137">[**ツールパレット**] ウィンドウが表示されていない場合は、[**表示**] メニューから [**ツールパレット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b681-137">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>  
  
4. <span data-ttu-id="4b681-138">ワークフローデザイナーの上部にある階層リンク表示で [ **StateMachine** ] をクリックして、ワークフローデザイナーの全体的なステートマシンビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4b681-138">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
5. <span data-ttu-id="4b681-139">**ツールボックス** の [**ステートマシン**] セクションから **state** アクティビティをワークフローデザイナーにドラッグし、[ **Initialize Target** ] 状態の上に置きます。</span><span class="sxs-lookup"><span data-stu-id="4b681-139">Drag a **State** activity from the **State Machine** section of the **Toolbox** onto the workflow designer and hover it over the **Initialize Target** state.</span></span> <span data-ttu-id="4b681-140">新しい状態がその上にあると、4つの三角形が **Initialize ターゲット** 状態の周囲に表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b681-140">Note that four triangles will appear around the **Initialize Target** state when the new state is over it.</span></span> <span data-ttu-id="4b681-141">**Initialize ターゲット** 状態のすぐ下にある三角形に新しい状態をドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-141">Drop the new state on the triangle that is immediately below the **Initialize Target** state.</span></span> <span data-ttu-id="4b681-142">これにより、新しい状態がワークフローに配置され、 **Initialize ターゲット** 状態から新しい状態への遷移が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b681-142">This places the new state onto the workflow and creates a transition from the **Initialize Target** state to the new state.</span></span>  
  
6. <span data-ttu-id="4b681-143">[ **State1** ] をクリックして選択し、 **DisplayName** をに変更し `Enter Guess` ます。次に、ワークフローデザイナーで状態をダブルクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4b681-143">Click **State1** to select it, change the **DisplayName** to `Enter Guess`, and then double-click the state in the workflow designer to expand it.</span></span>  
  
7. <span data-ttu-id="4b681-144">**ツールボックス** の [**プリミティブ**] セクションから **WriteLine** アクティビティをドラッグし、状態の **Entry** セクションにドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-144">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Entry** section of the state.</span></span>  
  
8. <span data-ttu-id="4b681-145">**WriteLine** の [ **Text** ] プロパティボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-145">Type the following expression into the **Text** property box of the **WriteLine**.</span></span>  
  
    ```vb  
    "Please enter a number between 1 and " & MaxNumber  
    ```  
  
    ```csharp  
    "Please enter a number between 1 and " + MaxNumber  
    ```  
  
9. <span data-ttu-id="4b681-146">[**ツールボックス**] の [**プリミティブ**] セクションから **Assign** アクティビティをドラッグし、状態の [**終了**] セクションにドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-146">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop onto the **Exit** section of the state.</span></span>  
  
10. <span data-ttu-id="4b681-147">[ `Turns` **To** ] ボックスに「」と入力し、[C# の式を入力するか、VB の式を入力してください `Turns + 1` ] ボックスに入力します 。 </span><span class="sxs-lookup"><span data-stu-id="4b681-147">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>  
  
11. <span data-ttu-id="4b681-148">ワークフローデザイナーの上部にある階層リンク表示で [ **StateMachine** ] をクリックして、ワークフローデザイナーの全体的なステートマシンビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4b681-148">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
12. <span data-ttu-id="4b681-149">**ツールボックス** の [**ステートマシン**] セクションから **finalstate** アクティビティをドラッグし、 **enter guess** 状態の上にマウスポインターを移動して **、enter guess 状態の** 右側に表示される三角形にドロップします。これにより、 **enter guess** と **finalstate** の間に遷移が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4b681-149">Drag a **FinalState** activity from the **State Machine** section of the **Toolbox**, hover it over the **Enter Guess** state, and drop it onto the triangle that appears to the right of the **Enter Guess** state so that a transition is created between **Enter Guess** and **FinalState**.</span></span>  
  
13. <span data-ttu-id="4b681-150">遷移の既定の名前は **T2** です。</span><span class="sxs-lookup"><span data-stu-id="4b681-150">The default name of the transition is **T2**.</span></span> <span data-ttu-id="4b681-151">ワークフローデザイナーで遷移をクリックして選択し、その **DisplayName** を [ **正しい推測**] に設定します。</span><span class="sxs-lookup"><span data-stu-id="4b681-151">Click the transition in the workflow designer to select it, and set its **DisplayName** to **Guess Correct**.</span></span> <span data-ttu-id="4b681-152">次に、[ **Finalstate**] をクリックして選択し、右側にドラッグして、2つの状態のいずれかをオーバーレイせずに完全な遷移名を表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4b681-152">Then click and select the **FinalState**, and drag it to the right so that there is room for the full transition name to be displayed without overlaying either of the two states.</span></span> <span data-ttu-id="4b681-153">これにより、チュートリアルの残りの手順をより簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="4b681-153">This will make it easier to complete the remaining steps in the tutorial.</span></span>  
  
14. <span data-ttu-id="4b681-154">ワークフローデザイナーで、新しく名前を変更した [ **推測** ] をダブルクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4b681-154">Double-click the newly renamed **Guess Correct** transition in the workflow designer to expand it.</span></span>  
  
15. <span data-ttu-id="4b681-155">[**ツールボックス**] の [ **NumberGuessWorkflowActivities** ] セクションから **readint** アクティビティをドラッグし、遷移の [**トリガー** ] セクションにドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-155">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Trigger** section of the transition.</span></span>  
  
16. <span data-ttu-id="4b681-156">**Readint** アクティビティの [**プロパティ] ウィンドウ** で、[ `"EnterGuess"` **BookmarkName** ] プロパティ値ボックスに引用符を含めて「」と入力し、 `Guess` **結果** のプロパティ値ボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-156">In the **Properties Window** for the **ReadInt** activity, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box, and type `Guess` into the **Result** property value box</span></span>  
  
17. <span data-ttu-id="4b681-157">[ **正しい** 移行の **条件** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-157">Type the following expression into the **Guess Correct** transition’s **Condition** property value box.</span></span>  
  
    ```vb  
    Guess = Target  
    ```  
  
    ```csharp  
    Guess == Target  
    ```  
  
18. <span data-ttu-id="4b681-158">ワークフローデザイナーの上部にある階層リンク表示で [ **StateMachine** ] をクリックして、ワークフローデザイナーの全体的なステートマシンビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4b681-158">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4b681-159">トリガー イベントが受け取られ、<xref:System.Activities.Statements.Transition.Condition%2A> (存在する場合) が `True` と評価される場合に遷移が発生します。</span><span class="sxs-lookup"><span data-stu-id="4b681-159">A transition occurs when the trigger event is received and the <xref:System.Activities.Statements.Transition.Condition%2A>, if present, evaluates to `True`.</span></span> <span data-ttu-id="4b681-160">この遷移では、ユーザーのが `Guess` ランダムに生成されたと一致 `Target` すると、制御が **finalstate** に渡され、ワークフローが完了します。</span><span class="sxs-lookup"><span data-stu-id="4b681-160">For this transition, if the user’s `Guess` matches the randomly generated `Target`, then control passes to the **FinalState** and the workflow completes.</span></span>  
  
19. <span data-ttu-id="4b681-161">推定値が正しいかどうかに応じて、ワークフローは、 **Finalstate** に遷移するか、別の try に対し **て Enter guess** 状態に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b681-161">Depending on whether the guess is correct, the workflow should transition either to the **FinalState** or back to the **Enter Guess** state for another try.</span></span> <span data-ttu-id="4b681-162">両方の遷移は、 **Readint** アクティビティを使用してユーザーの推定値を受け取ることを待機しているのと同じトリガーを共有します。</span><span class="sxs-lookup"><span data-stu-id="4b681-162">Both transitions share the same trigger of waiting for the user’s guess to be received via the **ReadInt** activity.</span></span> <span data-ttu-id="4b681-163">これは、共有遷移と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4b681-163">This is called a shared transition.</span></span> <span data-ttu-id="4b681-164">共有遷移を作成するには、 **推測の正しい** 切り替え効果の開始を示す円をクリックし、目的の状態にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4b681-164">To create a shared transition, click the circle that indicates the start of the **Guess Correct** transition and drag it to the desired state.</span></span> <span data-ttu-id="4b681-165">この場合、切り替え効果は自己遷移型であるため、 **推測** の開始点をドラッグして、 **Enter Guess** 状態の下にドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-165">In this case the transition is a self-transition, so drag the start point of the **Guess Correct** transition and drop it back onto the bottom of the **Enter Guess** state.</span></span> <span data-ttu-id="4b681-166">遷移を作成した後、ワークフローデザイナーでそれを選択し、その **DisplayName** プロパティを「 **正しくない推測**」に設定します。</span><span class="sxs-lookup"><span data-stu-id="4b681-166">After creating the transition, select it in the workflow designer and set its **DisplayName** property to **Guess Incorrect**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4b681-167">切り替え効果は、切り替え効果デザイナーの下部にある [ **共有トリガー遷移の追加** ] をクリックして、[ **接続可能な状態** ] ボックスから目的のターゲット状態を選択することによっても作成できます。</span><span class="sxs-lookup"><span data-stu-id="4b681-167">Shared transitions can also be created from within the transition designer by clicking **Add shared trigger transition** at the bottom of the transition designer, and then selecting the desired target state from the **Available states to connect** drop-down.</span></span>  
    > [!NOTE]
    > <span data-ttu-id="4b681-168">遷移の <xref:System.Activities.Statements.Transition.Condition%2A> が `false` と評価された場合 (またはトリガーを共有する遷移すべての状態が `false` と評価された場合)、遷移は行われず、その状態からのすべての遷移のすべてのトリガーが再スケジュールされます。</span><span class="sxs-lookup"><span data-stu-id="4b681-168">Note that if the <xref:System.Activities.Statements.Transition.Condition%2A> of a transition evaluates to `false` (or all of the conditions of a shared trigger transition evaluate to `false`), the transition will not occur and all triggers for all the transitions from the state will be rescheduled.</span></span> <span data-ttu-id="4b681-169">このチュートリアルでは、条件の構成方法 (推定値が正しいか間違っているかを判断する特定のアクションが用意されています) により、この状況は発生しません。</span><span class="sxs-lookup"><span data-stu-id="4b681-169">In this tutorial, this situation cannot happen because of the way the conditions are configured (we have specific actions for whether the guess is correct or incorrect).</span></span>  
  
20. <span data-ttu-id="4b681-170">ワークフローデザイナーで [ **推測** されない] をダブルクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="4b681-170">Double-click the **Guess Incorrect** transition in the workflow designer to expand it.</span></span> <span data-ttu-id="4b681-171">**トリガー** は、**推定の正しい** 切り替えによって使用されたのと同じ **readint** アクティビティに既に設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4b681-171">Note that the **Trigger** is already set to the same **ReadInt** activity that was used by the **Guess Correct** transition.</span></span>  
  
21. <span data-ttu-id="4b681-172">[ **条件** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-172">Type the following expression into the **Condition** property value box.</span></span>  
  
    ```vb  
    Guess <> Target  
    ```  
  
    ```csharp  
    Guess != Target  
    ```  
  
22. <span data-ttu-id="4b681-173">[**ツールボックス**] の [**制御フロー** ] セクションから **If** アクティビティをドラッグし、遷移の [**アクション**] セクションにドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-173">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Action** section of the transition.</span></span>  
  
23. <span data-ttu-id="4b681-174">**If** アクティビティの [ **Condition** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-174">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>  
  
    ```text
    Guess < Target
    ```  
  
24. <span data-ttu-id="4b681-175">**ツールボックス** の [**プリミティブ**] セクションから2つの **WriteLine** アクティビティをドラッグし、 **if** アクティビティの **Then** セクション、1が **Else** セクションにあるようにドロップします。</span><span class="sxs-lookup"><span data-stu-id="4b681-175">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the **If** activity, and one is in the **Else** section.</span></span>  
  
25. <span data-ttu-id="4b681-176">**[Then** ] セクションで [ **WriteLine** ] アクティビティをクリックして選択し、[ **Text** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-176">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too low."  
    ```  
  
26. <span data-ttu-id="4b681-177">[ **Else** ] セクションの **WriteLine** アクティビティをクリックして選択し、[ **Text** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="4b681-177">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>  
  
    ```text
    "Your guess is too high."  
    ```  
  
27. <span data-ttu-id="4b681-178">ワークフローデザイナーの上部にある階層リンク表示で [ **StateMachine** ] をクリックして、ワークフローデザイナーの全体的なステートマシンビューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4b681-178">Return to the overall state machine view in the workflow designer by clicking **StateMachine** in the breadcrumb display at the top of the workflow designer.</span></span>  
  
     <span data-ttu-id="4b681-179">次の例は完成したワークフローを示しています。</span><span class="sxs-lookup"><span data-stu-id="4b681-179">The following example illustrates the completed workflow.</span></span>  
  
     ![完成したステートマシンのワークフローを示す図。](./media/how-to-create-a-state-machine-workflow/complete-state-machine-workflow.jpg)  
  
### <a name="to-build-the-workflow"></a><span data-ttu-id="4b681-181">ワークフローをビルドするには</span><span class="sxs-lookup"><span data-stu-id="4b681-181">To build the workflow</span></span>  
  
1. <span data-ttu-id="4b681-182">Ctrl + Shift + B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="4b681-182">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
     <span data-ttu-id="4b681-183">ワークフローを実行する方法については、次のトピック「 [方法: ワークフローを実行](how-to-run-a-workflow.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b681-183">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="4b681-184">[「方法:](how-to-run-a-workflow.md)ワークフローステップを別のスタイルのワークフローで実行し、この手順のステートマシンワークフローを使用して実行する場合は、「 [How to: run a workflow](how-to-run-a-workflow.md)」の「[アプリケーションをビルドして実行するに](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)は」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="4b681-184">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the state machine workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b681-185">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="4b681-185">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="4b681-186">Windows Workflow Foundation プログラミングの新機能</span><span class="sxs-lookup"><span data-stu-id="4b681-186">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="4b681-187">ワークフローの設計</span><span class="sxs-lookup"><span data-stu-id="4b681-187">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="4b681-188">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="4b681-188">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="4b681-189">方法: アクティビティを作成する</span><span class="sxs-lookup"><span data-stu-id="4b681-189">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="4b681-190">方法: ワークフローを実行する</span><span class="sxs-lookup"><span data-stu-id="4b681-190">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
