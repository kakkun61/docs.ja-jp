---
title: 実行時における DynamicActivity を使用したアクティビティの作成
description: DynamicActivity は、パブリックコンストラクターを持つ具象クラスであり、シールされています。 アクティビティ DOM を使用して、実行時にアクティビティ機能をアセンブルするには、クラスを使用します。
ms.date: 03/30/2017
ms.assetid: 1af85cc6-912d-449e-90c5-c5db3eca5ace
ms.openlocfilehash: b65d7e385690b77d44c73e7a8a4ed38b04f30ea6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242098"
---
# <a name="creating-an-activity-at-runtime-with-dynamicactivity"></a><span data-ttu-id="76d87-104">実行時における DynamicActivity を使用したアクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="76d87-104">Creating an Activity at Runtime with DynamicActivity</span></span>

<span data-ttu-id="76d87-105"><xref:System.Activities.DynamicActivity> は、パブリック コンストラクターを持つ、具体的なシール クラスです。</span><span class="sxs-lookup"><span data-stu-id="76d87-105"><xref:System.Activities.DynamicActivity> is a concrete, sealed class with a public constructor.</span></span> <span data-ttu-id="76d87-106"><xref:System.Activities.DynamicActivity> は、実行時にアクティビティ DOM を使用してアクティビティの機能を構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="76d87-106"><xref:System.Activities.DynamicActivity> can be used to assemble activity functionality at runtime using an activity DOM.</span></span>  
  
## <a name="dynamicactivity-features"></a><span data-ttu-id="76d87-107">DynamicActivity の機能</span><span class="sxs-lookup"><span data-stu-id="76d87-107">DynamicActivity Features</span></span>  

 <span data-ttu-id="76d87-108"><xref:System.Activities.DynamicActivity> は、実行プロパティ、引数、変数にアクセスできますが、子アクティビティのスケジュール設定や追跡などのランタイム サービスにはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="76d87-108"><xref:System.Activities.DynamicActivity> has access to execution properties, arguments and variables, but no access to run-time services such as scheduling child activities or tracking.</span></span>  
  
 <span data-ttu-id="76d87-109">最上位のプロパティは、ワークフローの <xref:System.Activities.Argument> オブジェクトを使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="76d87-109">Top-level properties can be set using workflow <xref:System.Activities.Argument> objects.</span></span> <span data-ttu-id="76d87-110">命令型コードでは、これらの引数は新しい型で CLR プロパティを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="76d87-110">In imperative code, these arguments are created using CLR properties on a new type.</span></span> <span data-ttu-id="76d87-111">XAML では `x:Class` タグおよび `x:Member` タグを使用して、これらの引数が宣言されます。</span><span class="sxs-lookup"><span data-stu-id="76d87-111">In XAML, they are declared using `x:Class` and `x:Member` tags.</span></span>  
  
 <span data-ttu-id="76d87-112"><xref:System.Activities.DynamicActivity> を使用して構築されたアクティビティは、<xref:System.ComponentModel.ICustomTypeDescriptor> を使用してデザイナーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="76d87-112">Activities constructed using <xref:System.Activities.DynamicActivity> interface with the designer using <xref:System.ComponentModel.ICustomTypeDescriptor>.</span></span> <span data-ttu-id="76d87-113">デザイナーで作成されたアクティビティは、次の手順に示すように、<xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> を使用して動的に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="76d87-113">Activities created in the designer can be loaded dynamically using <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>, as demonstrated in the following procedure.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-imperative-code"></a><span data-ttu-id="76d87-114">命令型コードを使用して実行時にアクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="76d87-114">To create an activity at runtime using imperative code</span></span>  
  
1. <span data-ttu-id="76d87-115">OpenVisual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="76d87-115">OpenVisual Studio 2010.</span></span>  
  
2. <span data-ttu-id="76d87-116">[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-116">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="76d87-117">[**プロジェクトの種類**] ウィンドウの [ **Visual C#** ] で [**ワークフロー 4.0** ] を選択し、[ **v2010** ] ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-117">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="76d87-118">[**テンプレート**] ウィンドウで [**シーケンシャルワークフローコンソールアプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-118">Select **Sequential Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="76d87-119">新しいプロジェクトに DynamicActivitySample という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="76d87-119">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="76d87-120">HelloActivity プロジェクトで Workflow1.xaml を右クリックし、[ **削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-120">Right-click Workflow1.xaml in the HelloActivity project and select **Delete**.</span></span>  
  
4. <span data-ttu-id="76d87-121">Program.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="76d87-121">Open Program.cs.</span></span> <span data-ttu-id="76d87-122">次のディレクティブをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="76d87-122">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
5. <span data-ttu-id="76d87-123">1 つの `Main` アクティビティを含む <xref:System.Activities.Statements.Sequence> アクティビティを作成する次のコードで <xref:System.Activities.Statements.WriteLine> メソッドの内容を置き換え、新しい動的アクティビティの <xref:System.Activities.DynamicActivity.Implementation%2A> プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="76d87-123">Replace the contents of the `Main` method with the following code, which creates a <xref:System.Activities.Statements.Sequence> activity that contains a single <xref:System.Activities.Statements.WriteLine> activity and assigns it to the <xref:System.Activities.DynamicActivity.Implementation%2A> property of a new dynamic activity.</span></span>  
  
    ```csharp  
    //Define the input argument for the activity  
    var textOut = new InArgument<string>();  
    //Create the activity, property, and implementation  
                Activity dynamicWorkflow = new DynamicActivity()  
                {  
                    Properties =
                    {  
                        new DynamicActivityProperty  
                        {  
                            Name = "Text",  
                            Type = typeof(InArgument<String>),  
                            Value = textOut  
                        }  
                    },  
                    Implementation = () => new Sequence()  
                    {  
                        Activities =
                        {  
                            new WriteLine()  
                            {  
                                Text = new InArgument<string>(env => textOut.Get(env))  
                            }  
                        }  
                    }  
                };  
    //Execute the activity with a parameter dictionary  
                WorkflowInvoker.Invoke(dynamicWorkflow, new Dictionary<string, object> { { "Text", "Hello World!" } });  
                Console.ReadLine();  
    ```  
  
6. <span data-ttu-id="76d87-124">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="76d87-124">Execute the application.</span></span> <span data-ttu-id="76d87-125">"Hello World!" というテキストが表示されたコンソールウィンドウ</span><span class="sxs-lookup"><span data-stu-id="76d87-125">A console window with the text "Hello World!"</span></span> <span data-ttu-id="76d87-126">ヲ.</span><span class="sxs-lookup"><span data-stu-id="76d87-126">displays.</span></span>  
  
#### <a name="to-create-an-activity-at-runtime-using-xaml"></a><span data-ttu-id="76d87-127">XAML を使用して実行時にアクティビティを作成するには</span><span class="sxs-lookup"><span data-stu-id="76d87-127">To create an activity at runtime using XAML</span></span>  
  
1. <span data-ttu-id="76d87-128">Visual Studio 2010 を開きます。</span><span class="sxs-lookup"><span data-stu-id="76d87-128">Open Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="76d87-129">[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-129">Select **File**, **New**, **Project**.</span></span> <span data-ttu-id="76d87-130">[**プロジェクトの種類**] ウィンドウの [ **Visual C#** ] で [**ワークフロー 4.0** ] を選択し、[ **v2010** ] ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-130">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="76d87-131">[**テンプレート**] ウィンドウで [**ワークフローコンソールアプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-131">Select  **Workflow Console Application** in the **Templates** window.</span></span> <span data-ttu-id="76d87-132">新しいプロジェクトに DynamicActivitySample という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="76d87-132">Name the new project DynamicActivitySample.</span></span>  
  
3. <span data-ttu-id="76d87-133">HelloActivity プロジェクトの Workflow1.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="76d87-133">Open Workflow1.xaml in the HelloActivity project.</span></span> <span data-ttu-id="76d87-134">デザイナーの下部にある [ **引数** ] オプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="76d87-134">Click the **Arguments** option at the bottom of the designer.</span></span> <span data-ttu-id="76d87-135">`String` 型の `TextToWrite` という新しい `In` 引数を作成します。</span><span class="sxs-lookup"><span data-stu-id="76d87-135">Create a new `In` argument called `TextToWrite` of type `String`.</span></span>  
  
4. <span data-ttu-id="76d87-136">ツールボックスの [**プリミティブ**] セクションから、 **WriteLine** アクティビティをデザイナー画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="76d87-136">Drag a **WriteLine** activity from the **Primitives** section of the toolbox onto the designer surface.</span></span> <span data-ttu-id="76d87-137">`TextToWrite`アクティビティの **Text** プロパティに値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="76d87-137">Assign the value `TextToWrite` to the **Text** property of the activity.</span></span>  
  
5. <span data-ttu-id="76d87-138">Program.cs を開きます。</span><span class="sxs-lookup"><span data-stu-id="76d87-138">Open Program.cs.</span></span> <span data-ttu-id="76d87-139">次のディレクティブをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="76d87-139">Add the following directive to the top of the file.</span></span>  
  
    ```csharp  
    using System.Activities.XamlIntegration;  
    ```  
  
6. <span data-ttu-id="76d87-140">`Main` メソッドの内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="76d87-140">Replace the contents of the `Main` method with the following code.</span></span>  
  
    ```csharp  
    Activity act2 = ActivityXamlServices.Load(@"Workflow1.xaml");  
                    results = WorkflowInvoker.Invoke(act2, new Dictionary<string, object> { { "TextToWrite", "HelloWorld!" } });  
    Console.ReadLine();  
    ```  
  
7. <span data-ttu-id="76d87-141">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="76d87-141">Execute the application.</span></span> <span data-ttu-id="76d87-142">"Hello World!" というテキストが表示されたコンソールウィンドウ</span><span class="sxs-lookup"><span data-stu-id="76d87-142">A console window with the text "Hello World!"</span></span> <span data-ttu-id="76d87-143"> が表示されます。</span><span class="sxs-lookup"><span data-stu-id="76d87-143">appears.</span></span>  
  
8. <span data-ttu-id="76d87-144">**ソリューションエクスプローラー** で workflow1.xaml ファイルを右クリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="76d87-144">Right-click the Workflow1.xaml file in the **Solution Explorer** and select **View Code**.</span></span> <span data-ttu-id="76d87-145">アクティビティ クラスが `x:Class` を使用して作成され、プロパティが `x:Property` を使用して作成されています。</span><span class="sxs-lookup"><span data-stu-id="76d87-145">Note that the activity class is created with `x:Class` and the property is created with `x:Property`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d87-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="76d87-146">See also</span></span>

- [<span data-ttu-id="76d87-147">命令型コードを使用してワークフロー、アクティビティ、および式を作成する方法</span><span class="sxs-lookup"><span data-stu-id="76d87-147">Authoring Workflows, Activities, and Expressions Using Imperative Code</span></span>](authoring-workflows-activities-and-expressions-using-imperative-code.md)
