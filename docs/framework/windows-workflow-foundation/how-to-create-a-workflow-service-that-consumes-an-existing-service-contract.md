---
title: '方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 05c59bde424049eb5bef8f8bd09c472b58eaa9ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248826"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a><span data-ttu-id="10a68-102">方法: 既存のサービス コントラクトを使用するワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="10a68-102">How to: Create a workflow service that consumes an existing service contract</span></span>

<span data-ttu-id="10a68-103">.NET Framework 4.5 では、コントラクト優先ワークフロー開発の形式で web サービスとワークフローの統合が強化されています。</span><span class="sxs-lookup"><span data-stu-id="10a68-103">.NET Framework 4.5 features better integration between web services and workflows in the form of contract-first workflow development.</span></span> <span data-ttu-id="10a68-104">コントラクト優先ワークフローの開発ツールでは、コードのコントラクトを先に設計できます。</span><span class="sxs-lookup"><span data-stu-id="10a68-104">The contract-first workflow development tool allows you to design the contract in code first.</span></span> <span data-ttu-id="10a68-105">その後、ツールボックス内に、コントラクト内の操作用のアクティビティ テンプレートが自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="10a68-105">The tool then automatically generates an activity template in the toolbox for the operations in the contract.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10a68-106">このトピックでは、コントラクト優先ワークフロー サービスを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="10a68-106">This topic provides step-by-step guidance on creating a contract-first workflow service.</span></span> <span data-ttu-id="10a68-107">コントラクト優先ワークフローサービスの開発の詳細については、「 [コントラクトの最初のワークフローサービスの開発](contract-first-workflow-service-development.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10a68-107">For more information about contract-first workflow service development, see [Contract First Workflow Service Development](contract-first-workflow-service-development.md).</span></span>  
  
### <a name="creating-the-workflow-project"></a><span data-ttu-id="10a68-108">ワークフロー プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="10a68-108">Creating the workflow project</span></span>  
  
1. <span data-ttu-id="10a68-109">Visual Studio で、**[ファイル]\*\*\*\*[新しいプロジェクト]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-109">In Visual Studio, select **File**, **New Project**.</span></span> <span data-ttu-id="10a68-110">[**テンプレート**] ツリーで、[ **C#** ] ノードの下にある [ **wcf** ] ノードを選択し、[ **wcf ワークフローサービスアプリケーション**] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-110">Select the **WCF** node under the **C#** node in the **Templates** tree, and select the **WCF Workflow Service Application** template.</span></span>  
  
2. <span data-ttu-id="10a68-111">新しいプロジェクトに名前を指定し、 `ContractFirst` [ **Ok]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-111">Name the new project `ContractFirst` and click **Ok**.</span></span>  
  
### <a name="creating-the-service-contract"></a><span data-ttu-id="10a68-112">サービス コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="10a68-112">Creating the service contract</span></span>  
  
1. <span data-ttu-id="10a68-113">**ソリューションエクスプローラー** でプロジェクトを右クリックし、[**追加**]、[**新しい項目**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-113">Right-click the project in **Solution Explorer** and select **Add**, **New Item…**.</span></span> <span data-ttu-id="10a68-114">左側の [ **コード** ] ノードを選択し、右側の [ **クラス** ] テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-114">Select the **Code** node on the left, and the **Class** template on the right.</span></span> <span data-ttu-id="10a68-115">新しいクラスにという名前を指定し、 `IBookService` [ **Ok]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-115">Name the new class `IBookService` and click **Ok**.</span></span>  
  
2. <span data-ttu-id="10a68-116">表示されるコード ウィンドウの上部で、`System.Servicemodel` に対する Using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="10a68-116">In the top of the code window that appears, add a Using statement to `System.Servicemodel`.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. <span data-ttu-id="10a68-117">サンプルのクラス定義を次のインターフェイス定義に変更します。</span><span class="sxs-lookup"><span data-stu-id="10a68-117">Change the sample class definition to the following interface definition.</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. <span data-ttu-id="10a68-118">**Ctrl + Shift + B** キーを押してプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="10a68-118">Build the project by pressing **Ctrl+Shift+B**.</span></span>  
  
### <a name="importing-the-service-contract"></a><span data-ttu-id="10a68-119">サービス コントラクトのインポート</span><span class="sxs-lookup"><span data-stu-id="10a68-119">Importing the service contract</span></span>  
  
1. <span data-ttu-id="10a68-120">**ソリューションエクスプローラー** でプロジェクトを右クリックし、[**サービスコントラクトのインポート**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-120">Right-click the project in **Solution Explorer** and select **Import Service Contract**.</span></span> <span data-ttu-id="10a68-121">で **\<Current Project>** 、すべてのサブノードを開き、[ **Ibookservice**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-121">Under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="10a68-122">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-122">Click **OK**.</span></span>  
  
2. <span data-ttu-id="10a68-123">ダイアログが表示され、操作が正常に完了したことと、プロジェクトをビルドすると、生成されたアクティビティがツールボックスに表示されることが示されます。</span><span class="sxs-lookup"><span data-stu-id="10a68-123">A dialog will open, alerting you that the operation completed successfully, and that the generated activities will appear in the toolbox after you build the project.</span></span> <span data-ttu-id="10a68-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-124">Click **OK**.</span></span>  
  
3. <span data-ttu-id="10a68-125">**Ctrl + Shift + B** キーを押してプロジェクトをビルドし、インポートされたアクティビティがツールボックスに表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="10a68-125">Build the project by pressing **Ctrl+Shift+B**, so that the imported activities will appear in the toolbox.</span></span>  
  
4. <span data-ttu-id="10a68-126">**ソリューションエクスプローラー** で、Service1 .xamlx を開きます。</span><span class="sxs-lookup"><span data-stu-id="10a68-126">In **Solution Explorer**, open Service1.xamlx.</span></span> <span data-ttu-id="10a68-127">ワークフロー サービスがデザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="10a68-127">The workflow service will appear in the designer.</span></span>  
  
5. <span data-ttu-id="10a68-128">**Sequence** アクティビティを選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-128">Select the **Sequence** activity.</span></span> <span data-ttu-id="10a68-129">[プロパティウィンドウで、[.. **.** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-129">In the Properties window, click the **…**</span></span> <span data-ttu-id="10a68-130">**ImplementedContract** プロパティのボタン。</span><span class="sxs-lookup"><span data-stu-id="10a68-130">button in the **ImplementedContract** property.</span></span> <span data-ttu-id="10a68-131">[**型コレクションエディター** ] ウィンドウが表示されたら、[**種類**] ドロップダウンをクリックし、[**種類の参照**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-131">In the **Type Collection Editor** window that appears, click the **Type** dropdown, and select the **Browse for Types…**</span></span> <span data-ttu-id="10a68-132">] エントリを探してクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-132">entry.</span></span> <span data-ttu-id="10a68-133">[ **.Net 型の参照と選択** ] ダイアログボックスの [] で、 **\<Current Project>** すべてのサブノードを開き、[ **ibookservice**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="10a68-133">In the **Browse and Select a .NET Type** dialog, under **\<Current Project>**, open all sub-nodes and select **IBookService**.</span></span> <span data-ttu-id="10a68-134">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-134">Click **OK**.</span></span> <span data-ttu-id="10a68-135">[ **型コレクションエディター** ] ダイアログボックスで、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="10a68-135">In the **Type Collection Editor** dialog, click **OK**.</span></span>  
  
6. <span data-ttu-id="10a68-136">**Receiverequest アクティビティ** アクティビティと **sendresponse** アクティビティを選択して削除します。</span><span class="sxs-lookup"><span data-stu-id="10a68-136">Select and delete the **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
7. <span data-ttu-id="10a68-137">[ツールボックス] から、[ **Buy_ReceiveAndSendReply** と **Checkout_Receive** ] アクティビティを [ **シーケンシャルサービス** ] アクティビティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="10a68-137">From the toolbox, drag a **Buy_ReceiveAndSendReply** and a **Checkout_Receive** activity onto the **Sequential Service** activity.</span></span>
