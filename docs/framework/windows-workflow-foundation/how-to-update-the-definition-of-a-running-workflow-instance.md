---
title: '方法: 実行中のワークフロー インスタンスの定義を更新する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: b94c7564b1ce87695f82f28eb6daf7686203b41f
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190430"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="33ae0-102">方法: 実行中のワークフロー インスタンスの定義を更新する</span><span class="sxs-lookup"><span data-stu-id="33ae0-102">How to: Update the Definition of a Running Workflow Instance</span></span>

<span data-ttu-id="33ae0-103">動的更新は、ワークフロー アプリケーションの開発者が永続化されたワークフロー インスタンスのワークフロー定義を更新するためのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="33ae0-104">必要な変更には、バグ修正の実装、新しい要件の実装、または予期しない変更への対応があります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="33ae0-105">このチュートリアルのこの手順では、動的更新を使用して、数値推測ワークフローの永続化されたインスタンスを変更し、 `v1` [「方法: ワークフローの複数のバージョンを Side-by-side でホストする](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)」で導入された新しい機能に対応する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="33ae0-106">このトピックの内容</span><span class="sxs-lookup"><span data-stu-id="33ae0-106">In this topic</span></span>

- [<span data-ttu-id="33ae0-107">CreateUpdateMaps プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-107">To create the CreateUpdateMaps project</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [<span data-ttu-id="33ae0-108">StateMachineNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-108">To update StateMachineNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [<span data-ttu-id="33ae0-109">FlowchartNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-109">To update FlowchartNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [<span data-ttu-id="33ae0-110">SequentialNumberGuessWorkflow を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-110">To update SequentialNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [<span data-ttu-id="33ae0-111">CreateUpdateMaps アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-111">To build and run the CreateUpdateMaps application</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [<span data-ttu-id="33ae0-112">更新されたワークフロー アセンブリをビルドするには</span><span class="sxs-lookup"><span data-stu-id="33ae0-112">To build the updated workflow assembly</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [<span data-ttu-id="33ae0-113">新しいバージョンで WorkflowVersionMap を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-113">To update WorkflowVersionMap with the new versions</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="33ae0-114">動的更新を適用するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-114">To apply the dynamic updates</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [<span data-ttu-id="33ae0-115">更新されたワークフローを含むアプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-115">To run the application with the updated workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [<span data-ttu-id="33ae0-116">ワークフローの以前のバージョンを開始できるようにするには</span><span class="sxs-lookup"><span data-stu-id="33ae0-116">To enable starting previous versions of the workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="to-create-the-createupdatemaps-project"></a><a name="BKMK_CreateProject"></a> <span data-ttu-id="33ae0-117">CreateUpdateMaps プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-117">To create the CreateUpdateMaps project</span></span>

1. <span data-ttu-id="33ae0-118">**ソリューションエクスプローラー** で [ **WF45GettingStartedTutorial** ] を右クリックし、[**追加**]、[**新しいプロジェクト**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-118">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="33ae0-119">[ **インストール済み** ] ノードで、[ **Visual C#**]、[ **windows** ] (または [ **Visual Basic**]、[ **windows**]) のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-119">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="33ae0-120">Visual Studio でのプライマリ言語の構成によっては、[**Visual C#**] または [**Visual Basic**] ノードが [**インストール**] ノードの [**他の言語**] ノードの下になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-120">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="33ae0-121">[.NET Framework バージョン] ドロップダウン リストで [**.NET Framework 4.5**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-121">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="33ae0-122">**Windows** の一覧から [**コンソールアプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-122">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="33ae0-123">[**名前**] ボックスに「 **Createupdatemaps** 」と入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-123">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="33ae0-124">**ソリューションエクスプローラー** で **Createupdatemaps** を右クリックし、[**参照の追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-124">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="33ae0-125">[**参照の追加**] ボックスの [**アセンブリ**] ノードで [**フレームワーク**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-125">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="33ae0-126">[**アセンブリの検索**] ボックスに「system.string」と入力して、アセンブリをフィルター処理し、目的の参照を選択しやすくし **ます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-126">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>

5. <span data-ttu-id="33ae0-127">[**検索結果**] の一覧で [**システム**] の横のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-127">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

6. <span data-ttu-id="33ae0-128">[**アセンブリの検索**] ボックスに「**シリアル化**」と入力し、[**検索結果**] の一覧で [system.string]**の横に** あるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-128">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

7. <span data-ttu-id="33ae0-129">[**アセンブリの検索**] ボックスに「system.string」と入力し、[**検索結果**] の一覧で [ **app.xaml** ] の横にあるチェックボックスを **オンにし** ます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-129">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>

8. <span data-ttu-id="33ae0-130">[ **OK** ] をクリックして **参照マネージャー** を閉じ、参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-130">Click **OK** to close **Reference Manager** and add the references.</span></span>

9. <span data-ttu-id="33ae0-131">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-131">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.Statements
    Imports System.Xaml
    Imports System.Reflection
    Imports System.IO
    Imports System.Activities.XamlIntegration
    Imports System.Activities.DynamicUpdate
    Imports System.Runtime.Serialization
    Imports Microsoft.VisualBasic.Activities
    ```

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    using System.IO;
    using System.Xaml;
    using System.Reflection;
    using System.Activities.XamlIntegration;
    using System.Activities.DynamicUpdate;
    using System.Runtime.Serialization;
    using Microsoft.CSharp.Activities;
    ```

10. <span data-ttu-id="33ae0-132">`Program` クラス (または `Module1`) に次の 2 つの文字列メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-132">Add the following two string members to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. <span data-ttu-id="33ae0-133">`StartUpdate` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-133">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-134">このメソッドにより、指定した xaml ワークフロー定義が `ActivityBuilder` に読み込まれた後、`DynamicUpdate.PrepareForUpdate` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-134">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="33ae0-135">`PrepareForUpdate` は `ActivityBuilder` 内にワークフロー定義のコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-135">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="33ae0-136">ワークフロー定義が変更されると、更新マップを作成するように変更されたワークフロー定義と共に、このコピーは使用されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-136">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace refers to artifacts that come from
        'the same project as the XAML. When loading XAML if the currently executing
        'assembly is not the same assembly that was referred to as "local" in the XAML
        'LocalAssembly must be set to the assembly containing the artifacts.
        'Assembly.LoadFile requires an absolute path so convert this relative path
        'to an absolute path.
        readerSettings.LocalAssembly = Assembly.LoadFile(
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))

        Dim fullPath As String = Path.Combine(definitionPath, name)
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)

        'Load the workflow definition into an ActivityBuilder.
        Dim wf As ActivityBuilder = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))

        'PrepareForUpdate makes a copy of the workflow definition in the
        'ActivityBuilder that is used for comparison when the update
        'map is created.
        DynamicUpdateServices.PrepareForUpdate(wf)

        Return wf
    End Function
    ```

    ```csharp
    private static ActivityBuilder StartUpdate(string name)
    {
        // Create the XamlXmlReaderSettings.
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
        {
            // In the XAML the "local" namespace refers to artifacts that come from
            // the same project as the XAML. When loading XAML if the currently executing
            // assembly is not the same assembly that was referred to as "local" in the XAML
            // LocalAssembly must be set to the assembly containing the artifacts.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            LocalAssembly = Assembly.LoadFile(
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))
        };

        string path = Path.Combine(definitionPath, name);
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);

        // Load the workflow definition into an ActivityBuilder.
        ActivityBuilder wf = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))
            as ActivityBuilder;

        // PrepareForUpdate makes a copy of the workflow definition in the
        // ActivityBuilder that is used for comparison when the update
        // map is created.
        DynamicUpdateServices.PrepareForUpdate(wf);

        return wf;
    }
    ```

12. <span data-ttu-id="33ae0-137">次に、`CreateUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-137">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-138">これにより、DynamicUpdateServices.CreateUpdateMap が呼び出されて動的更新マップが作成され、指定した名前を使用してその更新マップが保存されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-138">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="33ae0-139">この更新マップには、`ActivityBuilder` に格納されている元のワークフロー定義を使用して開始された、永続化されたワークフロー インスタンスが、更新されたワークフロー定義を使用して完了するよう更新するために、ワークフロー ランタイムで必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="33ae0-139">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)
        'Create the UpdateMap.
        Dim map As DynamicUpdateMap =
            DynamicUpdateServices.CreateUpdateMap(wf)

        'Serialize it to a file.
        Dim mapFullPath As String = Path.Combine(mapPath, name)
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)
            sz.WriteObject(fs, map)
        End Using
    End Sub
    ```

    ```csharp
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)
    {
        // Create the UpdateMap.
        DynamicUpdateMap map =
            DynamicUpdateServices.CreateUpdateMap(wf);

        // Serialize it to a file.
        string path = Path.Combine(mapPath, name);
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))
        {
            sz.WriteObject(fs, map);
        }
    }
    ```

13. <span data-ttu-id="33ae0-140">`SaveUpdatedDefinition` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-140">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-141">このメソッドは、更新マップが作成されると、更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-141">This method saves the updated workflow definition once the update map is created.</span></span>

    ```vb
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)
        Dim xamlPath As String = Path.Combine(definitionPath, name)
        Dim sw As StreamWriter = File.CreateText(xamlPath)
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(
            New XamlXmlWriter(sw, New XamlSchemaContext()))
        XamlServices.Save(xw, wf)
        sw.Close()
    End Sub
    ```

    ```csharp
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)
    {
        string xamlPath = Path.Combine(definitionPath, name);
        StreamWriter sw = File.CreateText(xamlPath);
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(
            new XamlXmlWriter(sw, new XamlSchemaContext()));
        XamlServices.Save(xw, wf);
        sw.Close();
    }
    ```

### <a name="to-update-statemachinenumberguessworkflow"></a><a name="BKMK_StateMachine"></a> <span data-ttu-id="33ae0-142">Statemachinenumberguessworkflow.xaml を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-142">To update StateMachineNumberGuessWorkflow</span></span>

1. <span data-ttu-id="33ae0-143">`CreateStateMachineUpdateMap` クラス (または `Program`) に `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-143">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. <span data-ttu-id="33ae0-144">`StartUpdate` を呼び出し、ワークフローのルート `StateMachine` アクティビティへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-144">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>

    ```vb
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

    'Get a reference to the root StateMachine activity.
    Dim sm As StateMachine = wf.Implementation
    ```

    ```csharp
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

    // Get a reference to the root StateMachine activity.
    StateMachine sm = wf.Implementation as StateMachine;
    ```

3. <span data-ttu-id="33ae0-145">次に、 `WriteLine` ユーザーの推定値が大きすぎるか低すぎるかを示す2つのアクティビティの式を更新して、 [「方法: 複数のバージョンのワークフローを並列にホストする](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)」に記載されている更新と一致するようにします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-145">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    ```vb
    'Update the Text of the two WriteLine activities that write the
    'results of the user's guess. They are contained in the workflow as the
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

    'Update the "too low" message.
    Dim tooLow As WriteLine = guessLow.Then
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

    'Update the "too high" message.
    Dim tooHigh As WriteLine = guessLow.Else
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")
    ```

    ```csharp
    // Update the Text of the two WriteLine activities that write the
    // results of the user's guess. They are contained in the workflow as the
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    If guessLow = sm.States[1].Transitions[1].Action as If;

    // Update the "too low" message.
    WriteLine tooLow = guessLow.Then as WriteLine;
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

    // Update the "too high" message.
    WriteLine tooHigh = guessLow.Else as WriteLine;
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");
    ```

4. <span data-ttu-id="33ae0-146">終了メッセージを表示する新しい `WriteLine` アクティビティを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-146">Next, add the new `WriteLine` activity that displays the closing message.</span></span>

    ```vb
    'Create the new WriteLine that displays the closing message.
    Dim wl As New WriteLine() With
    {
        .Text = New VisualBasicValue(Of String) _
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
    }

    'Add it as the Action for the Guess Correct transition. The Guess Correct
    'transition is the first transition of States[1]. The transitions are listed
    'at the bottom of the State activity designer.
    sm.States(1).Transitions(0).Action = wl
    ```

    ```csharp
    // Create the new WriteLine that displays the closing message.
    WriteLine wl = new WriteLine
    {
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
    };

    // Add it as the Action for the Guess Correct transition. The Guess Correct
    // transition is the first transition of States[1]. The transitions are listed
    // at the bottom of the State activity designer.
    sm.States[1].Transitions[0].Action = wl;
    ```

5. <span data-ttu-id="33ae0-147">ワークフローを更新したら、`CreateUpdateMaps` と `SaveUpdatedDefinition` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-147">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="33ae0-148">`CreateUpdateMaps` は `DynamicUpdateMap` を作成して保存し、`SaveUpdatedDefinition` は更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-148">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>

    ```vb
    'Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

    'Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    ```

    ```csharp
    // Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

    // Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    ```

    <span data-ttu-id="33ae0-149">完成した `CreateStateMachineUpdateMap` メソッドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-149">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

        'Get a reference to the root StateMachine activity.
        Dim sm As StateMachine = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

        'Update the "too low" message.
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Add it as the Action for the Guess Correct transition. The Guess Correct
        'transition is the first transition of States[1]. The transitions are listed
        'at the bottom of the State activity designer.
        sm.States(1).Transitions(0).Action = wl

        'Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

        // Get a reference to the root StateMachine activity.
        StateMachine sm = wf.Implementation as StateMachine;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        If guessLow = sm.States[1].Transitions[1].Action as If;

        // Update the "too low" message.
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Create the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Add it as the Action for the Guess Correct transition. The Guess Correct
        // transition is the first transition of States[1]. The transitions are listed
        // at the bottom of the State activity designer.
        sm.States[1].Transitions[0].Action = wl;

        // Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-flowchartnumberguessworkflow"></a><a name="BKMK_Flowchart"></a> <span data-ttu-id="33ae0-150">Flowchartnumberguessworkflow.xaml を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-150">To update FlowchartNumberGuessWorkflow</span></span>

1. <span data-ttu-id="33ae0-151">`CreateFlowchartUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-151">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-152">このメソッドは `CreateStateMachineUpdateMap` に似ています。</span><span class="sxs-lookup"><span data-stu-id="33ae0-152">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="33ae0-153">最初に `StartUpdate` を呼び出し、フローチャート ワークフロー定義を更新して、最後に更新マップおよび更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-153">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateFlowchartUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")

        'Get a reference to the root Flowchart activity.
        Dim fc As Flowchart = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'True and False action of the "Guess < Target" FlowDecision, which is
        'Nodes[4].
        Dim guessLow As FlowDecision = fc.Nodes(4)

        'Update the "too low" message.
        Dim trueStep As FlowStep = guessLow.True
        Dim tooLow As WriteLine = trueStep.Action
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim falseStep As FlowStep = guessLow.False
        Dim tooHigh As WriteLine = falseStep.Action
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Create a FlowStep to hold the WriteLine.
        Dim closingStep As New FlowStep() With
        {
            .Action = wl
        }

        'Add this new FlowStep to the True action of the
        '"Guess = Guess" FlowDecision
        Dim guessCorrect As FlowDecision = fc.Nodes(3)
        guessCorrect.True = closingStep

        'Add the new FlowStep to the Nodes collection.
        'If closingStep was replacing an existing node then
        'we would need to remove that Step from the collection.
        'In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep)

        'Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateFlowchartUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");

        // Get a reference to the root Flowchart activity.
        Flowchart fc = wf.Implementation as Flowchart;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // True and False action of the "Guess < Target" FlowDecision, which is
        // Nodes[4].
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;

        // Update the "too low" message.
        FlowStep trueStep = guessLow.True as FlowStep;
        WriteLine tooLow = trueStep.Action as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        FlowStep falseStep = guessLow.False as FlowStep;
        WriteLine tooHigh = falseStep.Action as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Create a FlowStep to hold the WriteLine.
        FlowStep closingStep = new FlowStep
        {
            Action = wl
        };

        // Add this new FlowStep to the True action of the
        // "Guess == Guess" FlowDecision
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;
        guessCorrect.True = closingStep;

        // Add the new FlowStep to the Nodes collection.
        // If closingStep was replacing an existing node then
        // we would need to remove that Step from the collection.
        // In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep);

        // Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");

        //  Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-sequentialnumberguessworkflow"></a><a name="BKMK_Sequential"></a> <span data-ttu-id="33ae0-154">Sequentialnumberguessworkflow.xaml を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-154">To update SequentialNumberGuessWorkflow</span></span>

1. <span data-ttu-id="33ae0-155">`CreateSequentialUpdateMethod` クラス (または `Program`) に次の `Module1` を追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-155">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-156">このメソッドは、他の 2 つのメソッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="33ae0-156">This method is similar to the other two methods.</span></span> <span data-ttu-id="33ae0-157">最初に `StartUpdate` を呼び出し、シーケンシャル ワークフロー定義を更新して、最後に更新マップおよび更新されたワークフロー定義を保存します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-157">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateSequentialUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")

        'Get a reference to the root activity in the workflow.
        Dim rootSequence As Sequence = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the "Guess < Target" If activity.
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)
        Dim gameBody As Sequence = gameLoop.Body
        Dim guessCorrect As Statements.If = gameBody.Activities(2)
        Dim guessLow As Statements.If = guessCorrect.Then
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl)

        'Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateSequentialUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");

        // Get a reference to the root activity in the workflow.
        Sequence rootSequence = wf.Implementation as Sequence;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the "Guess < Target" If activity.
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;
        Sequence gameBody = gameLoop.Body as Sequence;
        If guessCorrect = gameBody.Activities[2] as If;
        If guessLow = guessCorrect.Then as If;
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl);

        // Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-build-and-run-the-createupdatemaps-application"></a><a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="33ae0-158">CreateUpdateMaps アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-158">To build and run the CreateUpdateMaps application</span></span>

1. <span data-ttu-id="33ae0-159">`Main` メソッドを更新し、次の 3 つのメソッド呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-159">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="33ae0-160">これらのメソッドは次のセクションで追加されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-160">These methods are added in the following sections.</span></span> <span data-ttu-id="33ae0-161">各メソッドは、対応する数値推測ワークフローを更新し、更新内容を示す `DynamicUpdateMap` を作成します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-161">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>

    ```vb
    Sub Main()
        'Create the update maps for the changes needed to the v1 activities
        'so they match the v2 activities.
        CreateSequentialUpdateMap()
        CreateFlowchartUpdateMap()
        CreateStateMachineUpdateMap()
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        // Create the update maps for the changes needed to the v1 activities
        // so they match the v2 activities.
        CreateSequentialUpdateMap();
        CreateFlowchartUpdateMap();
        CreateStateMachineUpdateMap();
    }
    ```

2. <span data-ttu-id="33ae0-162">**ソリューションエクスプローラー** で **Createupdatemaps** を右クリックし、[**スタートアッププロジェクトに設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-162">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

3. <span data-ttu-id="33ae0-163">Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押して `CreateUpdateMaps` アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-163">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="33ae0-164">アプリケーションでは `CreateUpdateMaps` 、実行中に状態情報は表示されませんが、 **NumberGuessWorkflowActivities_du** フォルダーと **以前のバージョン** のフォルダーを確認すると、更新されたワークフロー定義ファイルと更新マップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-164">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>

    <span data-ttu-id="33ae0-165">更新マップが作成され、ワークフロー定義が更新されたら、次に、更新された定義を含む更新されたワークフロー アセンブリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-165">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>

### <a name="to-build-the-updated-workflow-assembly"></a><a name="BKMK_BuildAssembly"></a> <span data-ttu-id="33ae0-166">更新されたワークフローアセンブリをビルドするには</span><span class="sxs-lookup"><span data-stu-id="33ae0-166">To build the updated workflow assembly</span></span>

1. <span data-ttu-id="33ae0-167">Visual Studio 2012 の2番目のインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-167">Open a second instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="33ae0-168">[**ファイル**] メニューの [**開く**]、[**プロジェクト/ソリューション**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-168">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>

3. <span data-ttu-id="33ae0-169">「[方法: 複数のバージョンのワークフローをサイドバイサイドでホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)する」で作成した **NumberGuessWorkflowActivities_du** フォルダーに移動し、 **NumberGuessWorkflowActivities** (または **.Vbproj**) を選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-169">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>

4. <span data-ttu-id="33ae0-170">**ソリューションエクスプローラー** で、 **sequentialnumberguessworkflow.xaml** を右クリックし、[**プロジェクトから除外**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-170">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="33ae0-171">**Flowchartnumberguessworkflow.xaml** と **statemachinenumberguessworkflow.xaml** でも同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="33ae0-171">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="33ae0-172">この手順により、以前のバージョンのワークフロー定義がプロジェクトから削除されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-172">This step removes the previous versions of the workflow definitions from the project.</span></span>

5. <span data-ttu-id="33ae0-173">[**プロジェクト**] メニューの [**既存項目の追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-173">Choose **Add Existing Item** from the **Project** menu.</span></span>

6. <span data-ttu-id="33ae0-174">[「方法: 複数のバージョンのワークフローをサイドバイサイドでホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)する」で作成した **NumberGuessWorkflowActivities_du** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-174">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

7. <span data-ttu-id="33ae0-175">**Xaml ファイル ( \* .xaml; を選択 \* します。**[**ファイルの種類**] ボックスの一覧から [xoml]) を削除します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-175">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>

8. <span data-ttu-id="33ae0-176">**SequentialNumberGuessWorkflow_du .xaml**、 **FlowchartNumberGuessWorkflow_du .xaml**、および **StateMachineNumberGuessWorkflow_du** を選択し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-176">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="33ae0-177">複数の項目を同時に選択するには、Ctrl を押しながら各項目をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-177">CTRL+Click to select multiple items at a time.</span></span>

    <span data-ttu-id="33ae0-178">この手順により、更新されたワークフロー定義がプロジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-178">This step adds the updated versions of the workflow definitions to the project.</span></span>

9. <span data-ttu-id="33ae0-179">Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-179">Press CTRL+SHIFT+B to build the project.</span></span>

10. <span data-ttu-id="33ae0-180">[**ファイル**] メニューの [**ソリューションを閉じる**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-180">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="33ae0-181">プロジェクトのソリューションファイルは必要ありません。そのため、[ **いいえ** ] をクリックして、ソリューションファイルを保存せずに Visual Studio を閉じます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-181">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="33ae0-182">[**ファイル**] メニューの [**終了**] をクリックして、Visual Studio を閉じます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-182">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>

11. <span data-ttu-id="33ae0-183">エクスプローラーを開き、 **NumberGuessWorkflowActivities_du \bin\debug** フォルダー (またはプロジェクトの設定によっては **bin\Release** ) に移動します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>

12. <span data-ttu-id="33ae0-184">**NumberGuessWorkflowActivities.dll** の名前を **NumberGuessWorkflowActivities_v15.dll** に変更し、「[方法: ワークフローの複数のバージョンを side-by-side にホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)する」で作成した以前の **バージョン** のフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-184">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

### <a name="to-update-workflowversionmap-with-the-new-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="33ae0-185">新しいバージョンで WorkflowVersionMap を更新するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-185">To update WorkflowVersionMap with the new versions</span></span>

1. <span data-ttu-id="33ae0-186">Visual Studio 2012 の初期インスタンスに戻ります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-186">Switch back to the initial instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="33ae0-187">**NumberGuessWorkflowHost** プロジェクトの下にある **WorkflowVersionMap.cs** (または **workflowversionmap .vb**) をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-187">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

3. <span data-ttu-id="33ae0-188">既存の 6 つのワークフロー ID 宣言の直後に、新しいワークフロー ID を 3 つ追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-188">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="33ae0-189">このチュートリアルでは、`1.5.0.0` は動的更新 ID の `WorkflowIdentity.Version` として使用されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-189">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="33ae0-190">これらの新しい `v15` ワークフロー ID は、動的に更新される永続化されたワークフロー インスタンスに適切なワークフロー定義を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-190">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamic Update) identities.
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

    // v1.5 (Dynamic Update) identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;
    ```

4. <span data-ttu-id="33ae0-191">コンストラクターの末尾に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-191">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="33ae0-192">このコードでは、動的更新ワークフロー ID を初期化し、対応するワークフロー定義を読み込み、これらをワークフロー バージョン ディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-192">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>

    ```vb
    'Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    'Add the dynamic update workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v15 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    // Add the dynamic update workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v15 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     <span data-ttu-id="33ae0-193">完成した `WorkflowVersionMap` クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-193">The following example is the completed `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        'v1.5 (Dynamic Update) identities.
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))

            'Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            'Add the dynamic update workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v15 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        // v1.5 (Dynamic Update) identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);

            // Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            // Add the dynamic update workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v15 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

5. <span data-ttu-id="33ae0-194">Ctrl キーと Shift キーを押しながら B キーを押して、プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-194">Press CTRL+SHIFT+B to build the project.</span></span>

### <a name="to-apply-the-dynamic-updates"></a><a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="33ae0-195">動的更新を適用するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-195">To apply the dynamic updates</span></span>

1. <span data-ttu-id="33ae0-196">**ソリューションエクスプローラー** で [ **WF45GettingStartedTutorial** ] を右クリックし、[**追加**]、[**新しいプロジェクト**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-196">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="33ae0-197">[ **インストール済み** ] ノードで、[ **Visual C#**]、[ **windows** ] (または [ **Visual Basic**]、[ **windows**]) のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-197">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="33ae0-198">Visual Studio でのプライマリ言語の構成によっては、[**Visual C#**] または [**Visual Basic**] ノードが [**インストール**] ノードの [**他の言語**] ノードの下になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-198">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

    <span data-ttu-id="33ae0-199">[.NET Framework バージョン] ドロップダウン リストで [**.NET Framework 4.5**] が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-199">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="33ae0-200">**Windows** の一覧から [**コンソールアプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-200">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="33ae0-201">[**名前**] ボックスに「 **Applydynamicupdate** 」と入力し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-201">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="33ae0-202">**ソリューションエクスプローラー** で **applydynamicupdate** を右クリックし、[**参照の追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-202">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="33ae0-203">[ **ソリューション** ] をクリックし、[ **NumberGuessWorkflowHost**] の横のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-203">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="33ae0-204">この参照は、`ApplyDynamicUpdate` で `NumberGuessWorkflowHost.WorkflowVersionMap` クラスを使用できるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="33ae0-204">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>

5. <span data-ttu-id="33ae0-205">[**参照の追加**] ボックスの [**アセンブリ**] ノードで [**フレームワーク**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-205">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="33ae0-206">[**アセンブリの検索**] ボックスに「system.string」と入力し **ます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-206">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="33ae0-207">これにより、アセンブリがフィルター処理され、目的の参照が選択しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-207">This will filter the assemblies and make the desired references easier to select.</span></span>

6. <span data-ttu-id="33ae0-208">[**検索結果**] の一覧で [**システム**] の横のチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-208">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

7. <span data-ttu-id="33ae0-209">[**アセンブリの検索**] ボックスに「**シリアル化**」と入力し、[**検索結果**] の一覧で [system.string]**の横に** あるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-209">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

8. <span data-ttu-id="33ae0-210">[**アセンブリの検索**] ボックスに「 **system.activities.durableinstancing.instances** 」と入力し、**検索結果** の一覧で **system.activities.durableinstancing.instances** と **system.activities.durableinstancing.instances** の横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-210">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>

9. <span data-ttu-id="33ae0-211">[ **OK** ] をクリックして **参照マネージャー** を閉じ、参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-211">Click **OK** to close **Reference Manager** and add the references.</span></span>

10. <span data-ttu-id="33ae0-212">ソリューションエクスプローラーで **Applydynamicupdate** を右クリックし、[ **追加**]、[ **クラス**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-212">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="33ae0-213">`DynamicUpdateInfo`[**名前**] ボックスに「」と入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-213">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>

11. <span data-ttu-id="33ae0-214">`DynamicUpdateInfo` クラスに次の 2 つのメンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-214">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="33ae0-215">完成した `DynamicUpdateInfo` クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-215">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="33ae0-216">このクラスには、ワークフロー インスタンスの更新時に使用された更新マップと新しいワークフロー ID に関する情報が格納されています。</span><span class="sxs-lookup"><span data-stu-id="33ae0-216">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>

    ```vb
    Public Class DynamicUpdateInfo
        Public updateMap As DynamicUpdateMap
        Public newIdentity As WorkflowIdentity
    End Class
    ```

    ```csharp
    class DynamicUpdateInfo
    {
        public DynamicUpdateMap updateMap;
        public WorkflowIdentity newIdentity;
    }
    ```

12. <span data-ttu-id="33ae0-217">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-217">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. <span data-ttu-id="33ae0-218">ソリューションエクスプローラーで、 **Program.cs** **(または** module1.vb) をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-218">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>

14. <span data-ttu-id="33ae0-219">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-219">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowHost
    Imports System.Data.SqlClient
    Imports System.Activities.DynamicUpdate
    Imports System.IO
    Imports System.Runtime.Serialization
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    ```

    ```csharp
    using NumberGuessWorkflowHost;
    using System.Data;
    using System.Data.SqlClient;
    using System.Activities;
    using System.Activities.DynamicUpdate;
    using System.IO;
    using System.Runtime.Serialization;
    using System.Activities.DurableInstancing;
    ```

15. <span data-ttu-id="33ae0-220">`Program` クラス (または `Module1`) に次の接続文字列メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-220">Add the following connection string member to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > <span data-ttu-id="33ae0-221">使用している SQL Server のエディションによって、接続文字列のサーバー名は異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-221">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

16. <span data-ttu-id="33ae0-222">`GetIDs` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-222">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-223">このメソッドは、永続化されたワークフロー インスタンス ID の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-223">This method returns a list of persisted workflow instance ids.</span></span>

    ```vb
    Function GetIds() As IList(Of Guid)
        Dim Ids As New List(Of Guid)
        Dim localCmd = _
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")
        Using localCon = New SqlConnection(connectionString)
            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)
                While reader.Read()
                    'Get the InstanceId of the persisted Workflow
                    Dim id As Guid = Guid.Parse(reader(0).ToString())

                    'Add it to the list.
                    Ids.Add(id)
                End While
            End Using
        End Using

        Return Ids
    End Function
    ```

    ```csharp
    static IList<Guid> GetIds()
    {
        List<Guid> Ids = new List<Guid>();
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");
        using (SqlConnection localCon = new SqlConnection(connectionString))
        {
            SqlCommand cmd = localCon.CreateCommand();
            cmd.CommandText = localCmd;
            localCon.Open();
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
            {
                while (reader.Read())
                {
                    // Get the InstanceId of the persisted Workflow
                    Guid id = Guid.Parse(reader[0].ToString());

                    // Add it to the list.
                    Ids.Add(id);
                }
            }
        }

        return Ids;
    }
    ```

17. <span data-ttu-id="33ae0-224">`LoadMap` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-224">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-225">このメソッドは、更新マップに `v1` ワークフロー ID をマップするディクショナリと、対応する永続化されたワークフロー インスタンスの更新に使用される新しいワークフロー ID を作成します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-225">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>

    ```vb
    Function LoadMap(mapName As String) As DynamicUpdateMap
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)

        Dim map As DynamicUpdateMap
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
            Dim updateMap = serializer.ReadObject(fs)
            If updateMap Is Nothing Then
                Throw New ApplicationException("DynamicUpdateMap is null.")
            End If

            map = updateMap
        End Using

        Return map
    End Function
    ```

    ```csharp
    static DynamicUpdateMap LoadMap(string mapName)
    {
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);

        DynamicUpdateMap map;
        using (FileStream fs = File.Open(path, FileMode.Open))
        {
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
            object updateMap = serializer.ReadObject(fs);
            if (updateMap == null)
            {
                throw new ApplicationException("DynamicUpdateMap is null.");
            }

            map = updateMap as DynamicUpdateMap;
        }

        return map;
    }
    ```

18. <span data-ttu-id="33ae0-226">`LoadMaps` クラス (または `Program`) に次の `Module1` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-226">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="33ae0-227">このメソッドは、3 つの更新マップを読み込み、更新マップに `v1` ワークフロー ID をマップするディクショナリを作成します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-227">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>

    ```vb
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)
        'There are 3 update maps to describe the changes to update v1 workflows,
        'one for reach of the 3 workflow types in the tutorial.
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()

        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")
        Dim sequentialInfo = New DynamicUpdateInfo With
        {
            .updateMap = sequentialMap,
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)

        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")
        Dim stateInfo = New DynamicUpdateInfo With
        {
            .updateMap = stateMap,
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)

        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")
        Dim flowchartInfo = New DynamicUpdateInfo With
        {
            .updateMap = flowchartMap,
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)

        Return maps
    End Function
    ```

    ```csharp
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()
    {
        // There are 3 update maps to describe the changes to update v1 workflows,
        // one for reach of the 3 workflow types in the tutorial.
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();

        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo
        {
            updateMap = sequentialMap,
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);

        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo
        {
            updateMap = stateMap,
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);

        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo
        {
            updateMap = flowchartMap,
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);

        return maps;
    }
    ```

19. <span data-ttu-id="33ae0-228">次のコードを `Main` に追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-228">Add the following code to `Main`.</span></span> <span data-ttu-id="33ae0-229">このコードでは、永続化されたワークフロー インスタンスを反復処理し、それぞれの `WorkflowIdentity` を調べます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-229">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="33ae0-230">`WorkflowIdentity` が `v1` ワークフロー インスタンスにマップされると、`WorkflowApplication` は、更新されたワークフロー定義と更新されたワークフロー ID を使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-230">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="33ae0-231">次に、`WorkflowApplication.Load` がそのインスタンスと更新マップを使用して呼び出され、動的更新マップが適用されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-231">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="33ae0-232">更新が適用されると、更新されたインスタンスは `Unload` の呼び出しによって永続化されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-232">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>

    ```vb
    Dim store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()

    For Each id As Guid In GetIds()
        'Get a proxy to the instance.
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)

        'Only update v1 workflows.
        If Not instance.DefinitionIdentity Is Nothing AndAlso _
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then

            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)

            'Associate the persisted WorkflowApplicationInstance with
            'a WorkflowApplication that is configured with the updated
            'definition and updated WorkflowIdentity.
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)

            'Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap)

            'Persist the updated instance.
            wfApp.Unload()

            Console.WriteLine("Updated to: {0}", info.newIdentity)
        Else
            'Not updating this instance, so unload it.
            instance.Abandon()
        End If
    Next
    ```

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();

    foreach (Guid id in GetIds())
    {
        // Get a proxy to the instance.
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(id, store);

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);

        // Only update v1 workflows.
        if (instance.DefinitionIdentity != null &&
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))
        {
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];

            // Associate the persisted WorkflowApplicationInstance with
            // a WorkflowApplication that is configured with the updated
            // definition and updated WorkflowIdentity.
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);
            WorkflowApplication wfApp =
                new WorkflowApplication(wf, info.newIdentity);

            // Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap);

            // Persist the updated instance.
            wfApp.Unload();

            Console.WriteLine("Updated to: {0}", info.newIdentity);
        }
        else
        {
            // Not updating this instance, so unload it.
            instance.Abandon();
        }
    }
    ```

20. <span data-ttu-id="33ae0-233">**ソリューションエクスプローラー** で **applydynamicupdate** を右クリックし、[**スタートアッププロジェクトに設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-233">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

21. <span data-ttu-id="33ae0-234">Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押して `ApplyDynamicUpdate` アプリケーションを実行して、永続化されたワークフロー インスタンスを更新します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-234">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="33ae0-235">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-235">You should see output similar to the following.</span></span> <span data-ttu-id="33ae0-236">バージョン 1.0.0.0 のワークフローはバージョン 1.5.0.0 に更新されますが、バージョン 2.0.0.0 のワークフローは更新されません。</span><span class="sxs-lookup"><span data-stu-id="33ae0-236">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>

    <span data-ttu-id="33ae0-237">**検査: Statemachinenumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-237">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-238">**更新日: Statemachinenumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-238">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-239">**検査: Statemachinenumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-239">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-240">**更新日: Statemachinenumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-240">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-241">**検査: Flowchartnumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-241">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-242">**更新日: Flowchartnumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-242">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-243">**検査: Flowchartnumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-243">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-244">**更新日: Flowchartnumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-244">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-245">**検査: Sequentialnumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-245">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-246">**更新日: Sequentialnumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-246">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-247">**検査: Sequentialnumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-247">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-248">**更新日: Sequentialnumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-248">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-249">**検査: Sequentialnumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-249">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-250">**更新日: Sequentialnumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-250">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-251">**検査: Statemachinenumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-251">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-252">**更新日: Statemachinenumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-252">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-253">**検査: Flowchartnumberguessworkflow.xaml;バージョン = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-253">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-254">**更新日: Flowchartnumberguessworkflow.xaml;バージョン = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-254">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="33ae0-255">**検査: Statemachinenumberguessworkflow.xaml;Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-255">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-256">**検査: Statemachinenumberguessworkflow.xaml;Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-257">**検査: Flowchartnumberguessworkflow.xaml;Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-257">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-258">**検査: Flowchartnumberguessworkflow.xaml;Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-259">**検査: Sequentialnumberguessworkflow.xaml;Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-259">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-260">**検査: Sequentialnumberguessworkflow.xaml;Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="33ae0-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="33ae0-261">**続行するには、任意のキーを押してください...**</span><span class="sxs-lookup"><span data-stu-id="33ae0-261">**Press any key to continue . . .**</span></span>

### <a name="to-run-the-application-with-the-updated-workflows"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="33ae0-262">更新されたワークフローでアプリケーションを実行するには</span><span class="sxs-lookup"><span data-stu-id="33ae0-262">To run the application with the updated workflows</span></span>

1. <span data-ttu-id="33ae0-263">**ソリューションエクスプローラー** で [ **NumberGuessWorkflowHost** ] を右クリックし、[**スタートアッププロジェクトに設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-263">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="33ae0-264">Ctrl キーを押しながら F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-264">Press CTRL+F5 to run the application.</span></span>

3. <span data-ttu-id="33ae0-265">[ **新しいゲーム** ] をクリックして新しいワークフローを開始し、ワークフローがワークフローであることを示すステータスウィンドウの下にあるバージョン情報を確認し `v2` ます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-265">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>

4. <span data-ttu-id="33ae0-266">`v1`「[方法: ワークフローの複数のバージョンをホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)する」の冒頭で開始したワークフローの1つを選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-266">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="33ae0-267">[状態] ウィンドウの下のバージョン情報は、ワークフローがバージョン **1.5.0.0** ワークフローであることを示しています。</span><span class="sxs-lookup"><span data-stu-id="33ae0-267">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="33ae0-268">前の推定値については、その値が大きすぎるか小さすぎるかという点以外の情報はありません。</span><span class="sxs-lookup"><span data-stu-id="33ae0-268">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>

    <span data-ttu-id="33ae0-269">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-269">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-270">**Your guess is too low.**</span><span class="sxs-lookup"><span data-stu-id="33ae0-270">**Your guess is too low.**</span></span>

5. <span data-ttu-id="33ae0-271">`InstanceId` を書き留めておき、ワークフローが完了するまで推定値を入力します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-271">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="33ae0-272">ステータス ウィンドウには、`WriteLine` アクティビティが動的更新によって更新されたため、推測の内容に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-272">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>

    <span data-ttu-id="33ae0-273">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-273">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-274">**推定値が小さすぎます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-274">**Your guess is too low.**</span></span>\
    <span data-ttu-id="33ae0-275">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-275">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-276">**5が低すぎます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-276">**5 is too low.**</span></span>\
    <span data-ttu-id="33ae0-277">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-277">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-278">**7が高すぎます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-278">**7 is too high.**</span></span>\
    <span data-ttu-id="33ae0-279">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-279">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-280">**Congratulations, you guessed the number in 4 turns.**</span><span class="sxs-lookup"><span data-stu-id="33ae0-280">**Congratulations, you guessed the number in 4 turns.**</span></span>

6. <span data-ttu-id="33ae0-281">エクスプローラーを開き、 **NumberGuessWorkflowHost\bin\debug** フォルダー (プロジェクトの設定によっては **bin\release** ) に移動し、完了したワークフローに対応するメモ帳を使用して追跡ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-281">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="33ae0-282">を書き留めていない場合は、 `InstanceId` Windows エクスプローラーの [ **更新日時** 情報を使用して正しい追跡ファイルを特定できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-282">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="33ae0-283">追跡情報の最後の行には、新しく追加した `WriteLine` アクティビティの出力が含まれます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-283">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>

    <span data-ttu-id="33ae0-284">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-284">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-285">**推定値が小さすぎます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-285">**Your guess is too low.**</span></span>\
    <span data-ttu-id="33ae0-286">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-286">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-287">**5が低すぎます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-287">**5 is too low.**</span></span>\
    <span data-ttu-id="33ae0-288">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-288">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-289">**7が高すぎます。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-289">**7 is too high.**</span></span>\
    <span data-ttu-id="33ae0-290">**1から10までの数値を入力してください**</span><span class="sxs-lookup"><span data-stu-id="33ae0-290">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="33ae0-291">**6は正しいです。4つのターンで推測したとします。**</span><span class="sxs-lookup"><span data-stu-id="33ae0-291">**6 is correct. You guessed it in 4 turns.**</span></span>

### <a name="to-enable-starting-previous-versions-of-the-workflows"></a><a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="33ae0-292">ワークフローの以前のバージョンを開始できるようにするには</span><span class="sxs-lookup"><span data-stu-id="33ae0-292">To enable starting previous versions of the workflows</span></span>

<span data-ttu-id="33ae0-293">更新するワークフローがなくなったら、ワークフローの以前のバージョンを開始できるように `NumberGuessWorkflowHost` アプリケーションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="33ae0-293">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>

1. <span data-ttu-id="33ae0-294">**ソリューションエクスプローラー** で [ **WorkflowHostForm** ] をダブルクリックし、[ **workflowtype** ] コンボボックスを選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-294">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>

2. <span data-ttu-id="33ae0-295">[ **プロパティ** ] ウィンドウで、 **items** プロパティを選択し、省略記号ボタンをクリックして **items** コレクションを編集します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-295">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>

3. <span data-ttu-id="33ae0-296">コレクションに次の 3 つの項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-296">Add the following three items to the collection.</span></span>

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    <span data-ttu-id="33ae0-297">完成した `Items` コレクションには 6 個の項目があります。</span><span class="sxs-lookup"><span data-stu-id="33ae0-297">The completed `Items` collection will have six items.</span></span>

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. <span data-ttu-id="33ae0-298">**ソリューションエクスプローラー** で [ **WorkflowHostForm** ] をダブルクリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-298">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>

5. <span data-ttu-id="33ae0-299">ハンドラーの (または) ステートメントに3つの新しいケースを追加し、 `switch` `Select Case` `NewGame_Click` **workflowtype** コンボボックスの新しい項目を一致するワークフロー id にマップします。</span><span class="sxs-lookup"><span data-stu-id="33ae0-299">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>

    ```vb
    Case "SequentialNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

    Case "StateMachineNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

    Case "FlowchartNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    ```

    ```csharp
    case "SequentialNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
        break;

    case "StateMachineNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
        break;

    case "FlowchartNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
        break;
    ```

    <span data-ttu-id="33ae0-300">完成した `switch` (または `Select Case`) ステートメントを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-300">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>

    ```vb
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity

        Case "SequentialNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

        Case "StateMachineNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

        Case "FlowchartNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    End Select
    ```

    ```csharp
    switch (WorkflowType.SelectedItem.ToString())
    {
        case "SequentialNumberGuessWorkflow":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
            break;

        case "StateMachineNumberGuessWorkflow":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
            break;

        case "FlowchartNumberGuessWorkflow":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
            break;

        case "SequentialNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
            break;

        case "StateMachineNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
            break;

        case "FlowchartNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
            break;
    };
    ```

6. <span data-ttu-id="33ae0-301">Ctrl キーを押しながら F5 キーを押してアプリケーションをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-301">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="33ae0-302">これで、ワークフローの現在のバージョンに加え、`v1` バージョンを開始できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="33ae0-302">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="33ae0-303">これらの新しいインスタンスを動的に更新するには、 **Applydynamicupdate** アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="33ae0-303">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
