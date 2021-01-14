---
title: '方法: アクティビティを作成する'
description: この記事では、Workflow Foundation で2つのアクティビティを作成する方法を示します。1つはコードを使用してロジックを実装し、もう1つは他のアクティビティを使用して定義します。
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: c7610d8612eb944afa9c23e1bf2abceeb3a6d38b
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190768"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="400bb-103">方法: アクティビティを作成する</span><span class="sxs-lookup"><span data-stu-id="400bb-103">How to: Create an Activity</span></span>

<span data-ttu-id="400bb-104">アクティビティは [!INCLUDE[wf1](../../../includes/wf1-md.md)] の動作の中心的な単位です。</span><span class="sxs-lookup"><span data-stu-id="400bb-104">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="400bb-105">アクティビティの実行ロジックはマネージド コードで実装できます。または他のアクティビティを使用して実装できます。</span><span class="sxs-lookup"><span data-stu-id="400bb-105">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="400bb-106">このトピックでは、2 つのアクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="400bb-106">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="400bb-107">最初のアクティビティは、コードを使用してその実行ロジックを実装する単純なアクティビティです。</span><span class="sxs-lookup"><span data-stu-id="400bb-107">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="400bb-108">2 番目のアクティビティの実装は他のアクティビティを使用して定義されています。</span><span class="sxs-lookup"><span data-stu-id="400bb-108">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="400bb-109">これらのアクティビティは、チュートリアルの次の手順で使用します。</span><span class="sxs-lookup"><span data-stu-id="400bb-109">These activities are used in following steps in the tutorial.</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="400bb-110">アクティビティライブラリプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="400bb-110">Create the activity library project</span></span>

1. <span data-ttu-id="400bb-111">Visual Studio を開き  >  、[**ファイル**] メニューの [新しい **プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="400bb-112">[**新しいプロジェクト**] ダイアログの [**インストール済み**] カテゴリで、[ **Visual C#**  >  **ワークフロー** ] (または **Visual Basic**  >  **ワークフロー**) を選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="400bb-113">[ **ワークフロー** テンプレート] カテゴリが表示されない場合は、Visual Studio の **Windows Workflow Foundation** コンポーネントのインストールが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="400bb-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="400bb-114">[**新しいプロジェクト**] ダイアログの左側にある [ **Visual Studio インストーラーを開く**] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="400bb-115">Visual Studio インストーラーで、[ **個々のコンポーネント** ] タブを選択します。次に、[ **開発アクティビティ** ] カテゴリで、[ **Windows Workflow Foundation** ] コンポーネントを選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="400bb-116">[ **変更** ] を選択してコンポーネントをインストールします。</span><span class="sxs-lookup"><span data-stu-id="400bb-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="400bb-117">[ **アクティビティライブラリ** ] プロジェクトテンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="400bb-118">[**名前**] ボックスに「`NumberGuessWorkflowActivities`」と入力して、[**OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="400bb-119">**ソリューション エクスプローラー** で、[**Activity1.xaml**] を右クリックし、[**削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="400bb-120">**[OK]** をクリックして確定します。</span><span class="sxs-lookup"><span data-stu-id="400bb-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="400bb-121">ReadInt アクティビティを作成する</span><span class="sxs-lookup"><span data-stu-id="400bb-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="400bb-122">[**プロジェクト**] メニューの [**新しい項目の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="400bb-123">[**インストールされている**  >  **共通項目**] ノードで、[**ワークフロー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="400bb-124">[**ワークフロー** ] の一覧から [**コードアクティビティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="400bb-125">[**名前**] ボックスに「`ReadInt`」と入力して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="400bb-126">既存の `ReadInt` 定義を次の定義に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="400bb-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="400bb-127">`ReadInt` アクティビティは、コード アクティビティ テンプレートの既定値である <xref:System.Activities.NativeActivity%601> ではなく <xref:System.Activities.CodeActivity> から派生します。</span><span class="sxs-lookup"><span data-stu-id="400bb-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="400bb-128"><xref:System.Activities.CodeActivity%601> は、<xref:System.Activities.Activity%601.Result%2A> 引数を介して公開される 1 つの結果がアクティビティによって提供される場合に使用できますが、<xref:System.Activities.CodeActivity%601> ではブックマークの使用がサポートされていないため、<xref:System.Activities.NativeActivity%601> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="400bb-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="400bb-129">Prompt アクティビティを作成する</span><span class="sxs-lookup"><span data-stu-id="400bb-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="400bb-130">**Ctrl** + **Shift** + **B** キーを押して、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="400bb-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="400bb-131">プロジェクトをビルドすると、このプロジェクトの `ReadInt` アクティビティを使用して、この手順からカスタム アクティビティをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="400bb-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="400bb-132">[**プロジェクト**] メニューの [**新しい項目の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="400bb-133">[**インストールされている**  >  **共通項目**] ノードで、[**ワークフロー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="400bb-134">[**ワークフロー**] 一覧から [**アクティビティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="400bb-135">[**名前**] ボックスに「`Prompt`」と入力して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="400bb-136">**ソリューションエクスプローラー** で [ **Prompt .xaml** ] をダブルクリックしてデザイナーに表示します (まだ表示されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="400bb-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="400bb-137">アクティビティ デザイナーの左下にある [**引数**] をクリックして、[**引数**] ウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="400bb-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="400bb-138">[**Create Argument**] (引数の作成) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="400bb-139">[名前] ボックスに「」と入力し、[ `BookmarkName` **方向**] ドロップダウンリストから [ **In** ] を選択します。次に、[**引数の型**] ドロップダウンリストから [**文字列**] を選択し **、enter** キーを押して引数を保存します。 </span><span class="sxs-lookup"><span data-stu-id="400bb-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="400bb-140">[**Create Argument**] (引数の作成) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="400bb-141">`Result`新しく追加された引数の下にある [**名前**] ボックスに「」と入力し、 `BookmarkName` [**方向**] ドロップダウンリストから [ **Out** ] を選択します。次に、[**引数の型**] ドロップダウンリストから [ **Int32** ] を選択し **、enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="400bb-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="400bb-142">[**Create Argument**] (引数の作成) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="400bb-143">[名前] ボックスに「」と入力し、[ `Text` **方向**] ドロップダウンリストから [ **In** ] を選択します。次に、[**引数の型**] ドロップダウンリストから [**文字列**] を選択し **、enter** キーを押して引数を保存します。 </span><span class="sxs-lookup"><span data-stu-id="400bb-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="400bb-144">これら 3 つの引数は、次の手順で、<xref:System.Activities.Statements.WriteLine> アクティビティに追加される `ReadInt` アクティビティと `Prompt` アクティビティの対応する引数にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="400bb-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="400bb-145">アクティビティ デザイナーの左下にある [**引数**] をクリックして、[**引数**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="400bb-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="400bb-146">[**ツールボックス**] の [**制御フロー** ] セクションから **Sequence** アクティビティをドラッグし、 **Prompt** アクティビティデザイナーの [**ここにアクティビティをドロップ**] ラベルの上にドロップします。</span><span class="sxs-lookup"><span data-stu-id="400bb-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="400bb-147">[**ツールパレット**] ウィンドウが表示されていない場合は、[**表示**] メニューから [**ツールパレット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="400bb-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="400bb-148">**ツールボックス** の [**プリミティブ**] セクションから **WriteLine** アクティビティをドラッグし、 **Sequence** アクティビティの [ここに **アクティビティをドロップ**] ラベルにドロップします。</span><span class="sxs-lookup"><span data-stu-id="400bb-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="400bb-149">[プロパティ] ウィンドウの [  C# の式を入力するか、VB の式を入力してください] ボックスに「」と入力し、WriteLine アクティビティの **Text** 引数を **Prompt** アクティビティの **text** 引数にバインド `Text` します。次に、 **tab** キーを2回押します。   </span><span class="sxs-lookup"><span data-stu-id="400bb-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="400bb-150">これで、IntelliSense リスト メンバー ウィンドウを閉じ、プロパティから選択を外してプロパティ値を保存します。</span><span class="sxs-lookup"><span data-stu-id="400bb-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="400bb-151">このプロパティは `Text` 、アクティビティ自体の [C# の **式を入力** するか、 **VB の式を入力** してください] ボックスに「」と入力して設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="400bb-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="400bb-152">[**プロパティ] ウィンドウ** が表示されていない場合は、[**表示**] メニューの [**プロパティウィンドウ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="400bb-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="400bb-153">**ツールボックス** の [ **NumberGuessWorkflowActivities** ] セクションから **readint** アクティビティをドラッグし、 **WriteLine** アクティビティに従うように **Sequence** アクティビティにドロップします。</span><span class="sxs-lookup"><span data-stu-id="400bb-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="400bb-154">[   プロパティ] ウィンドウで BookmarkName 引数の右にある [VB の式を入力してください] ボックスに「」と入力し、tab キーを2回押して、IntelliSense の一覧のメンバーウィンドウを閉じ、プロパティを保存して、 **Readint** アクティビティの BookmarkName 引数を Prompt アクティビティの BookmarkName 引数にバインド `BookmarkName` します。    </span><span class="sxs-lookup"><span data-stu-id="400bb-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="400bb-155">[  プロパティ ] ウィンドウで result 引数の右側にある [VB の式を入力してください] ボックスに「」と入力して、 **Readint** アクティビティの result 引数を Prompt アクティビティの result 引数にバインドし、 `Result` **tab** キーを2回押します。   </span><span class="sxs-lookup"><span data-stu-id="400bb-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="400bb-156">**Ctrl** + **Shift** + **B** キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="400bb-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="400bb-157">次の手順</span><span class="sxs-lookup"><span data-stu-id="400bb-157">Next steps</span></span>

<span data-ttu-id="400bb-158">これらのアクティビティを使用してワークフローを作成する方法については、チュートリアルの次の手順「 [方法: ワークフローを作成](how-to-create-a-workflow.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="400bb-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="400bb-159">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="400bb-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="400bb-160">カスタム アクティビティの設計と実装</span><span class="sxs-lookup"><span data-stu-id="400bb-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="400bb-161">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="400bb-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="400bb-162">方法: ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="400bb-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="400bb-163">カスタム アクティビティ デザイナーでの ExpressionTextBox の使用</span><span class="sxs-lookup"><span data-stu-id="400bb-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
