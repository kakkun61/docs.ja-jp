---
title: '方法: メッセージング アクティビティを使用してワークフロー サービスを作成する'
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: 21d08d9c3c78cc8774d038018703ffb0c7ceb1fe
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286319"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a><span data-ttu-id="095ef-102">方法: メッセージング アクティビティを使用してワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="095ef-102">How to: Create a Workflow Service with Messaging Activities</span></span>

<span data-ttu-id="095ef-103">このトピックでは、メッセージング アクティビティを使用して単純なワークフロー サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="095ef-103">This topic describes how to create a simple workflow service using messaging activities.</span></span> <span data-ttu-id="095ef-104">ここでは、メッセージング アクティビティだけで構成されるサービスのワークフロー サービスを作成する機構に重点を置きます。</span><span class="sxs-lookup"><span data-stu-id="095ef-104">This topic focuses on the mechanics of creating a workflow service where the service consists solely of messaging activities.</span></span> <span data-ttu-id="095ef-105">実際のサービスでは、ワークフローに他の多くのアクティビティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="095ef-105">In a real-world service, the workflow contains many other activities.</span></span> <span data-ttu-id="095ef-106">このサービスは、文字列を取得して、それを呼び出し元に返す、Echo という 1 つの操作を実装します。</span><span class="sxs-lookup"><span data-stu-id="095ef-106">The service implements one operation called Echo, which takes a string and returns the string to the caller.</span></span> <span data-ttu-id="095ef-107">このトピックは、一連の 2 つのトピックの最初のものです。</span><span class="sxs-lookup"><span data-stu-id="095ef-107">This topic is the first in a series of two topics.</span></span> <span data-ttu-id="095ef-108">次のトピック「 [方法: ワークフローアプリケーションからサービスにアクセス](how-to-access-a-service-from-a-workflow-application.md) する」では、このトピックで作成したサービスを呼び出すことができるワークフローアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="095ef-108">The next topic [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) discusses how to create a workflow application that can call the service created in this topic.</span></span>  
  
### <a name="to-create-a-workflow-service-project"></a><span data-ttu-id="095ef-109">ワークフロー サービス プロジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="095ef-109">To create a workflow service project</span></span>  
  
1. <span data-ttu-id="095ef-110">Visual Studio 2012 を起動します。</span><span class="sxs-lookup"><span data-stu-id="095ef-110">Start Visual Studio 2012.</span></span>  
  
2. <span data-ttu-id="095ef-111">[ **ファイル** ] メニューの [ **新規作成**] をポイントし、[ **プロジェクト** ] をクリックして [ **新しいプロジェクト] ダイアログ** を表示します。</span><span class="sxs-lookup"><span data-stu-id="095ef-111">Click the **File** menu, select **New**, and then **Project** to display the **New Project Dialog**.</span></span> <span data-ttu-id="095ef-112">プロジェクトの種類の一覧から、インストールされているテンプレートと **WCF ワークフローサービスアプリケーション** の一覧から [**ワークフロー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="095ef-112">Select **Workflow** from the list of installed templates and **WCF Workflow Service Application** from the list of project types.</span></span> <span data-ttu-id="095ef-113">次の図に示すように、プロジェクトにという名前 `MyWFService` を付け、既定の場所を使用します。</span><span class="sxs-lookup"><span data-stu-id="095ef-113">Name the project `MyWFService` and use the default location as shown in the following illustration.</span></span>  
  
     <span data-ttu-id="095ef-114">[ **OK** ] ボタンをクリックして、[ **新しいプロジェクト] ダイアログボックス** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="095ef-114">Click the **OK** button to dismiss the **New Project Dialog**.</span></span>  
  
3. <span data-ttu-id="095ef-115">プロジェクトが作成されると、次の図に示すように、Service1.xamlx ファイルがデザイナーで開かれます。</span><span class="sxs-lookup"><span data-stu-id="095ef-115">When the project is created, the Service1.xamlx file is opened in the designer as shown in the following illustration.</span></span>  
  
     ![スクリーンショットは、デザイナーで開かれている Service1 .xamlx ファイルを示しています。](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     <span data-ttu-id="095ef-117">[ **シーケンシャルサービス** ] というラベルの付いたアクティビティを右クリックし、[ **削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="095ef-117">Right-click the activity labeled **Sequential Service** and select **Delete**.</span></span>  
  
### <a name="to-implement-the-workflow-service"></a><span data-ttu-id="095ef-118">ワークフロー サービスを実装するには</span><span class="sxs-lookup"><span data-stu-id="095ef-118">To implement the workflow service</span></span>  
  
1. <span data-ttu-id="095ef-119">画面の左側にある [ **ツールボックス** ] タブを選択してツールボックスを表示し、プッシュピンをクリックしてウィンドウを開いたままにします。</span><span class="sxs-lookup"><span data-stu-id="095ef-119">Select the **Toolbox** tab on the left side of the screen to display the toolbox and click the pushpin to keep the window open.</span></span> <span data-ttu-id="095ef-120">次の図に示すように、[ツールボックス] の [ **メッセージング** ] セクションを展開して、メッセージングアクティビティとメッセージングアクティビティテンプレートを表示します。</span><span class="sxs-lookup"><span data-stu-id="095ef-120">Expand the **Messaging** section of the toolbox to display the messaging activities and the messaging activity templates as shown in the following illustration.</span></span>  
  
     ![メッセージングセクションが展開されたツールボックスを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2. <span data-ttu-id="095ef-122">**Receiveandsendreply** テンプレートをワークフローデザイナーにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="095ef-122">Drag and drop a **ReceiveAndSendReply** template to the workflow designer.</span></span> <span data-ttu-id="095ef-123">これに <xref:System.Activities.Statements.Sequence> より、次の図に示すように、 **Receive** アクティビティの後にアクティビティが作成さ <xref:System.ServiceModel.Activities.SendReply> れます。</span><span class="sxs-lookup"><span data-stu-id="095ef-123">This creates a <xref:System.Activities.Statements.Sequence> activity with a **Receive** activity followed by a <xref:System.ServiceModel.Activities.SendReply> activity as shown in the following illustration.</span></span>  
  
     ![ReceiveAndSendReply テンプレートを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     <span data-ttu-id="095ef-125"><xref:System.ServiceModel.Activities.SendReply> アクティビティの <xref:System.ServiceModel.Activities.SendReply.Request%2A> プロパティは `Receive` に設定されています。これは、<xref:System.ServiceModel.Activities.Receive> アクティビティが応答する <xref:System.ServiceModel.Activities.SendReply> アクティビティの名前です。</span><span class="sxs-lookup"><span data-stu-id="095ef-125">Notice that the <xref:System.ServiceModel.Activities.SendReply> activity’s <xref:System.ServiceModel.Activities.SendReply.Request%2A> property is set to `Receive`, the name of the <xref:System.ServiceModel.Activities.Receive> activity to which the <xref:System.ServiceModel.Activities.SendReply> activity is replying.</span></span>  
  
3. <span data-ttu-id="095ef-126">アクティビティの <xref:System.ServiceModel.Activities.Receive> 種類で、 `Echo` **OperationName** という名前のテキストボックスに入力します。</span><span class="sxs-lookup"><span data-stu-id="095ef-126">In the <xref:System.ServiceModel.Activities.Receive> activity type `Echo` into the textbox labeled **OperationName**.</span></span> <span data-ttu-id="095ef-127">これにより、サービスが実装する操作の名前が定義されます。</span><span class="sxs-lookup"><span data-stu-id="095ef-127">This defines the name of the operation the service implements.</span></span>  
  
     ![操作名を指定する場所を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4. <span data-ttu-id="095ef-129">アクティビティを選択した状態で、 <xref:System.ServiceModel.Activities.Receive> まだ開いていない場合は [ **表示** ] メニューの [ **プロパティウィンドウ]** をクリックして、[プロパティ] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="095ef-129">With the <xref:System.ServiceModel.Activities.Receive> activity selected, open the properties window if not already open by clicking the **View** menu and selecting **Properties Window**.</span></span> <span data-ttu-id="095ef-130">[ **プロパティ] ウィンドウ** で、次の図に示すように、 **CanCreateInstance** が表示されるまで下にスクロールし、チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="095ef-130">In the **Properties Window** scroll down until you see **CanCreateInstance** and click the checkbox as shown in the following illustration.</span></span> <span data-ttu-id="095ef-131">この設定によって、ワークフロー サービス ホストはメッセージが受信されると (必要に応じて) サービスの新しいインスタンスを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="095ef-131">This setting enables the workflow service host to create a new instance of the service (if needed) when a message is received.</span></span>  
  
     ![CanCreateInstance プロパティを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5. <span data-ttu-id="095ef-133">アクティビティを選択し、 <xref:System.Activities.Statements.Sequence> デザイナーの左下隅にある [ **変数** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="095ef-133">Select the <xref:System.Activities.Statements.Sequence> activity and click the **Variables** button in the lower left corner of the designer.</span></span> <span data-ttu-id="095ef-134">これにより、変数エディターが開かれます。</span><span class="sxs-lookup"><span data-stu-id="095ef-134">This displays the variables editor.</span></span> <span data-ttu-id="095ef-135">[ **変数の作成** ] リンクをクリックして、操作に送信される文字列を格納する変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="095ef-135">Click the **Create Variable** link to add a variable to store the string sent to the operation.</span></span> <span data-ttu-id="095ef-136">次の図に示すように、変数にという名前 `msg` を付け、その **変数** の型を String に設定します。</span><span class="sxs-lookup"><span data-stu-id="095ef-136">Name the variable `msg` and set its **Variable** type to String as shown in the following illustration.</span></span>  
  
     ![変数を追加する方法を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     <span data-ttu-id="095ef-138">[ **変数** ] ボタンをもう一度クリックして、変数エディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="095ef-138">Click the **Variables** button again to close the variables editor.</span></span>  
  
6. <span data-ttu-id="095ef-139">[定義] をクリックし **ます**。</span><span class="sxs-lookup"><span data-stu-id="095ef-139">Click the **Define..**</span></span> <span data-ttu-id="095ef-140">[コンテンツ定義] ダイアログボックスを表示するには、アクティビティの [**コンテンツ**] テキストボックス内のリンクを選択し <xref:System.ServiceModel.Activities.Receive> ます。 **Content Definition**</span><span class="sxs-lookup"><span data-stu-id="095ef-140">link in the **Content** text box in the <xref:System.ServiceModel.Activities.Receive> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="095ef-141">[**パラメーター** ] オプションボタンを選択し、[**新しいパラメーターの追加**] リンクをクリックし、[名前] テキストボックスに「」と入力し `inMsg` **name** ます。次の図に示すように、[**型**] ボックスで [**文字列**] を選択し、[ `msg` **割り当て先**] テキストボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="095ef-141">Select the **Parameters** radio button, click the **Add new Parameter** link, type `inMsg` in the **name** text box, select **String** in the **Type** drop down list box, and type `msg` in the **Assign To** text box as shown in the following illustration.</span></span>  
  
     ![パラメーターの内容の追加を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     <span data-ttu-id="095ef-143">これにより、Receive アクティビティが文字列パラメーターを受け取り、そのデータが `msg` 変数にバインドされるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="095ef-143">This specifies that the Receive activity receives string parameter and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="095ef-144">[ **OK** ] をクリックして、[ **コンテンツ定義** ] ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="095ef-144">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
7. <span data-ttu-id="095ef-145">アクティビティの [**コンテンツ**] ボックスの [**定義...** ] リンクをクリックして <xref:System.ServiceModel.Activities.SendReply> 、[**コンテンツ定義**] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="095ef-145">Click the **Define...** link in the **Content** box in the <xref:System.ServiceModel.Activities.SendReply> activity to display the **Content Definition** dialog.</span></span> <span data-ttu-id="095ef-146">[**パラメーター** ] オプションボタンを選択し、[**新しいパラメーターの追加**] リンクをクリックします。次の図に示すように、[名前] ボックスに「」と入力し、[ `outMsg` **型**] ドロップダウンリストボックスで [**文字列**] を選択し、[ **name** `msg` **値**] テキストボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="095ef-146">Select the **Parameters** radio button, click the **Add new Parameter** link, type `outMsg` in the **name** textbox, select **String** in the **Type** dropdown list box, and `msg` in the **Value** text box as shown in the following illustration.</span></span>  
  
     ![OutMsg パラメーターを追加する方法を示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     <span data-ttu-id="095ef-148">これにより、<xref:System.ServiceModel.Activities.SendReply> アクティビティがメッセージまたはメッセージ コントラクト型を送信し、そのデータが `msg` 変数にバインドされるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="095ef-148">This specifies that the <xref:System.ServiceModel.Activities.SendReply> activity sends a message or message contract type and that data is bound to the `msg` variable.</span></span> <span data-ttu-id="095ef-149">これは <xref:System.ServiceModel.Activities.SendReply> アクティビティであるため、`msg` のデータは、アクティビティがクライアントに送り返すメッセージの設定に使用されます。</span><span class="sxs-lookup"><span data-stu-id="095ef-149">Because this is a <xref:System.ServiceModel.Activities.SendReply> activity, this means the data in `msg` is used to populate the message the activity sends back to the client.</span></span> <span data-ttu-id="095ef-150">[ **OK** ] をクリックして、[ **コンテンツ定義** ] ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="095ef-150">Click **OK** to close the **Content Definition** dialog.</span></span>  
  
8. <span data-ttu-id="095ef-151">[ **ビルド** ] メニューの [ **ソリューションのビルド**] をクリックして、ソリューションを保存してビルドします。</span><span class="sxs-lookup"><span data-stu-id="095ef-151">Save and build the solution by clicking the **Build** menu and selecting **Build Solution**.</span></span>  
  
## <a name="configure-the-workflow-service-project"></a><span data-ttu-id="095ef-152">ワークフロー サービス プロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="095ef-152">Configure the Workflow Service Project</span></span>  

 <span data-ttu-id="095ef-153">ワークフロー サービスは完成しました。</span><span class="sxs-lookup"><span data-stu-id="095ef-153">The workflow service is complete.</span></span> <span data-ttu-id="095ef-154">ここでは、ホストと実行を容易にするように、ワークフロー サービス ソリューションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="095ef-154">This section explains how to configure the workflow service solution to make it easy to host and run.</span></span> <span data-ttu-id="095ef-155">このソリューションでは、ASP.NET 開発サーバーを使用してサービスをホストします。</span><span class="sxs-lookup"><span data-stu-id="095ef-155">This solution uses the ASP.NET Development Server to host the service.</span></span>  
  
#### <a name="to-set-project-start-up-options"></a><span data-ttu-id="095ef-156">プロジェクトのスタートアップ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="095ef-156">To set project start up options</span></span>  
  
1. <span data-ttu-id="095ef-157">**ソリューションエクスプローラー** で、[ **myのサービス**] を右クリックし、[**プロパティ**] をクリックして、[**プロジェクトのプロパティ**] ダイアログボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="095ef-157">In the **Solution Explorer**, right-click **MyWFService** and select **Properties** to display the **Project Properties** dialog.</span></span>  
  
2. <span data-ttu-id="095ef-158">[ **Web** ] タブを選択し、[**開始動作**] で [**特定のページ**] を選択し、 `Service1.xamlx` 次の図に示すように、テキストボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="095ef-158">Select the **Web** tab and select **Specific Page** under **Start Action** and type `Service1.xamlx` in the text box as shown in the following illustration.</span></span>  
  
     ![[プロジェクトのプロパティ] ダイアログボックスが表示されるスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     <span data-ttu-id="095ef-160">これにより、ASP.NET 開発サーバーの Service1.xamlx で定義されたサービスがホストされます。</span><span class="sxs-lookup"><span data-stu-id="095ef-160">This hosts the service defined in Service1.xamlx in the ASP.NET Development Server.</span></span>  
  
3. <span data-ttu-id="095ef-161">Ctrl キーを押しながら F5 キーを押して、サービスを起動します。</span><span class="sxs-lookup"><span data-stu-id="095ef-161">Press Ctrl + F5 to launch the service.</span></span> <span data-ttu-id="095ef-162">次の図に示すように、ASP.NET 開発サーバーのアイコンが、デスクトップの右下側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="095ef-162">The ASP.NET Development Server icon is displayed in the lower right side of the desktop as shown in the following image.</span></span>  
  
     ![ASP.NET Developer サーバーアイコンを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     <span data-ttu-id="095ef-164">また、Internet Explorer に、サービスの WCF サービス ヘルプ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="095ef-164">In addition, Internet Explorer displays the WCF Service Help Page for the service.</span></span>  
  
     ![WCF サービスのヘルプページを示すスクリーンショット。](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4. <span data-ttu-id="095ef-166">「 [方法: ワークフローアプリケーションからサービスにアクセス](how-to-access-a-service-from-a-workflow-application.md) する」のトピックに進み、このサービスを呼び出すワークフロークライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="095ef-166">Continue on to the [How To: Access a Service From a Workflow Application](how-to-access-a-service-from-a-workflow-application.md) topic to create a workflow client that calls this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="095ef-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="095ef-167">See also</span></span>

- [<span data-ttu-id="095ef-168">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="095ef-168">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="095ef-169">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="095ef-169">Hosting Workflow Services Overview</span></span>](hosting-workflow-services-overview.md)
- [<span data-ttu-id="095ef-170">メッセージング アクティビティ</span><span class="sxs-lookup"><span data-stu-id="095ef-170">Messaging Activities</span></span>](messaging-activities.md)
