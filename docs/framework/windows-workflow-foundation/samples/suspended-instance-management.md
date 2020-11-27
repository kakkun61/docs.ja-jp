---
title: 中断されたインスタンスの管理
ms.date: 03/30/2017
ms.assetid: f5ca3faa-ba1f-4857-b92c-d927e4b29598
ms.openlocfilehash: 620cd2299a3b08ee9330e13830c714c5d0ebb068
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293651"
---
# <a name="suspended-instance-management"></a><span data-ttu-id="f25c9-102">中断されたインスタンスの管理</span><span class="sxs-lookup"><span data-stu-id="f25c9-102">Suspended Instance Management</span></span>

<span data-ttu-id="f25c9-103">このサンプルでは、中断されているワークフロー インスタンスを管理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-103">This sample demonstrates how to manage workflow instances that have been suspended.</span></span>  <span data-ttu-id="f25c9-104"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> の既定のアクションは `AbandonAndSuspend` です。</span><span class="sxs-lookup"><span data-stu-id="f25c9-104">The default action for <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is `AbandonAndSuspend`.</span></span> <span data-ttu-id="f25c9-105">つまり、既定では、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるワークフロー インスタンスからスローされた未処理の例外により、インスタンスがメモリから破棄され、インスタンスの永続バージョンが中断状態としてマークされることになります。</span><span class="sxs-lookup"><span data-stu-id="f25c9-105">This means that by default, unhandled exceptions thrown from a workflow instance hosted in the <xref:System.ServiceModel.WorkflowServiceHost> will cause the instance to be disposed from memory (abandoned) and the durable/persisted version of the instance to be marked as suspended.</span></span> <span data-ttu-id="f25c9-106">中断されたワークフロー インスタンスは、中断が解除されるまで実行できません。</span><span class="sxs-lookup"><span data-stu-id="f25c9-106">A suspended workflow instance will not be able to run until it has been unsuspended.</span></span>

 <span data-ttu-id="f25c9-107">このサンプルでは、コマンド ライン ユーティリティを実装して、中断されたインスタンスについてクエリを実行する方法、およびユーザーがインスタンスを再開または終了できるようにする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-107">The sample shows how a command-line utility can be implemented to query for suspended instances, and how to give the user the option to resume or terminate the instance.</span></span> <span data-ttu-id="f25c9-108">このサンプルでは、ワークフロー サービスから例外が意図的にスローされ、中断状態になります。</span><span class="sxs-lookup"><span data-stu-id="f25c9-108">In this sample, a workflow service intentionally throws an exception, causing it to become suspended.</span></span> <span data-ttu-id="f25c9-109">その後、コマンド ライン ユーティリティを使用してインスタンスについてクエリを実行し、さらに、インスタンスを再開または終了できます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-109">The command-line utility can then be used to query for the instance and subsequently resume or terminate the instance.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="f25c9-110">対象</span><span class="sxs-lookup"><span data-stu-id="f25c9-110">Demonstrates</span></span>

 <span data-ttu-id="f25c9-111"><xref:System.ServiceModel.WorkflowServiceHost><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>と <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> WINDOWS WORKFLOW FOUNDATION (WF) を使用します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-111"><xref:System.ServiceModel.WorkflowServiceHost> with <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> and <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> in Windows Workflow Foundation (WF).</span></span>

## <a name="discussion"></a><span data-ttu-id="f25c9-112">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="f25c9-112">Discussion</span></span>

 <span data-ttu-id="f25c9-113">このサンプルに実装されているコマンド ライン ユーティリティは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] に用意されている SQL インスタンス ストアの実装に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="f25c9-113">The command-line utility implemented in this sample is specific to the SQL instance store implementation that ships in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="f25c9-114">インスタンス ストアのカスタム実装がある場合は、サンプルの `WorkflowInstanceCommand` の実装を、使用しているインスタンス ストアに固有の実装に置き換えることで、このユーティリティを調整できます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-114">If you have a custom implementation of the instance store, then you can adapt this utility by replacing the `WorkflowInstanceCommand` implementations in the sample with implementations that are specific to your instance store.</span></span>

 <span data-ttu-id="f25c9-115">用意されている実装では、SQL インスタンス ストアに対して SQL コマンドを直接実行して、中断されたインスタンスのリストを取得し、<xref:System.ServiceModel.Activities.WorkflowControlEndpoint> に追加された <xref:System.ServiceModel.WorkflowServiceHost> を使用して、インスタンスを再開または終了できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f25c9-115">The provided implementation runs SQL commands against the SQL instance store directly to list suspended instances, and it relies on a <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> added to the <xref:System.ServiceModel.WorkflowServiceHost> in order to resume or terminate the instances.</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f25c9-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="f25c9-116">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f25c9-117">このサンプルでは、次の Windows コンポーネントが有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f25c9-117">This sample requires that the following Windows components are enabled:</span></span>

    1. <span data-ttu-id="f25c9-118">Microsoft メッセージ キュー (MSMQ) サーバー</span><span class="sxs-lookup"><span data-stu-id="f25c9-118">Microsoft Message Queues (MSMQ) Server</span></span>

    2. <span data-ttu-id="f25c9-119">SQL Server Express</span><span class="sxs-lookup"><span data-stu-id="f25c9-119">SQL Server Express</span></span>

2. <span data-ttu-id="f25c9-120">SQL Server データベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-120">Set up the SQL Server database.</span></span>

    1. <span data-ttu-id="f25c9-121">Visual Studio 2010 のコマンドプロンプトで、SuspendedInstanceManagement サンプルディレクトリから "setup.exe" を実行します。これにより、次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-121">From a Visual Studio 2010 command prompt, run "setup.cmd" from the SuspendedInstanceManagement sample directory, which does the following:</span></span>

        1. <span data-ttu-id="f25c9-122">SQL Server Express を使用して永続性データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-122">Creates a persistence database using SQL Server Express.</span></span> <span data-ttu-id="f25c9-123">永続性データベースが既に存在する場合、データベースは削除され、再作成されます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-123">If the persistence database already exists, then it is dropped and re-created</span></span>

        2. <span data-ttu-id="f25c9-124">永続化のためにデータベースを設定します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-124">Sets up the database for persistence.</span></span>

        3. <span data-ttu-id="f25c9-125">IIS APPPOOL\DefaultAppPool および NT AUTHORITY\Network Service を、永続化のためにデータベースを設定するときに定義された InstanceStoreUsers ロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-125">Adds IIS APPPOOL\DefaultAppPool and NT AUTHORITY\Network Service to the InstanceStoreUsers role that was defined when setting up the database for persistence.</span></span>

3. <span data-ttu-id="f25c9-126">サービス キューを設定します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-126">Set up the service queue.</span></span>

    1. <span data-ttu-id="f25c9-127">Visual Studio 2010 で、 **Sampleworkflowapp** プロジェクトを右クリックし、[ **スタートアッププロジェクトに設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f25c9-127">In Visual Studio 2010, right-click the **SampleWorkflowApp** project and click **Set as Startup Project**.</span></span>

    2. <span data-ttu-id="f25c9-128">**F5** キーを押して SampleWorkflowApp をコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-128">Compile and run the SampleWorkflowApp by pressing **F5**.</span></span> <span data-ttu-id="f25c9-129">これにより、必要なキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-129">This will create the required queue.</span></span>

    3. <span data-ttu-id="f25c9-130">**Enter** キーを押して SampleWorkflowApp を停止します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-130">Press **Enter** to stop the SampleWorkflowApp.</span></span>

    4. <span data-ttu-id="f25c9-131">コマンド プロンプトから Compmgmt.msc を実行して、[コンピューターの管理] コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-131">Open the Computer Management console by running Compmgmt.msc from a command prompt.</span></span>

    5. <span data-ttu-id="f25c9-132">[ **サービスとアプリケーション**]、[ **メッセージキュー**]、[ **専用キュー**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-132">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

    6. <span data-ttu-id="f25c9-133">**[Receivetx]** キューを右クリックし、[**プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-133">Right click the **ReceiveTx** queue and select **Properties**.</span></span>

    7. <span data-ttu-id="f25c9-134">[ **セキュリティ** ] タブを選択し、 **すべてのユーザー** に **メッセージの受信**、メッセージの **ピーク**、および **メッセージの送信** を許可します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-134">Select the **Security** tab and allow **Everyone** to have permissions to **Receive Message**, **Peek Message**, and **Send Message**.</span></span>

4. <span data-ttu-id="f25c9-135">サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-135">Now, run the sample.</span></span>

    1. <span data-ttu-id="f25c9-136">Visual Studio 2010 で、Ctrl キーを押し **ながら F5** キーを押して、SampleWorkflowApp プロジェクトをデバッグなしでもう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-136">In Visual Studio 2010, run the SampleWorkflowApp project again without debugging by pressing **Ctrl+F5**.</span></span> <span data-ttu-id="f25c9-137">2 つのエンドポイント アドレスがコンソール ウィンドウに出力されます。1 つはアプリケーション エンドポイントのアドレスで、もう 1 つは <xref:System.ServiceModel.Activities.WorkflowControlEndpoint> のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="f25c9-137">Two endpoint addresses will be printed in the console window: one for the application endpoint and then other from the <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>.</span></span> <span data-ttu-id="f25c9-138">その後、ワークフロー インスタンスが作成され、そのインスタンスの追跡レコードがコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-138">A workflow instance is then created, and tracking records for that instance will appear in the console window.</span></span> <span data-ttu-id="f25c9-139">ワークフロー インスタンスから例外がスローされ、インスタンスは中断されて中止されます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-139">The workflow instance will throw an exception causing the instance to be suspended and aborted.</span></span>

    2. <span data-ttu-id="f25c9-140">次に、コマンド ライン ユーティリティを使用して、これらのインスタンスに対してさらに操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-140">The command-line utility can then be used to take further action on any of these instances.</span></span> <span data-ttu-id="f25c9-141">コマンド ライン引数の構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f25c9-141">The syntax for command line arguments is as follows::</span></span>

         `SuspendedInstanceManagement -Command:[CommandName] -Server:[ServerName] -Database:[DatabaseName] -InstanceId:[InstanceId]`

         <span data-ttu-id="f25c9-142">サポートされるコマンドは、`Query`、`Resume`、および `Terminate` です。</span><span class="sxs-lookup"><span data-stu-id="f25c9-142">The supported commands are: `Query`, `Resume`, and `Terminate`.</span></span>  <span data-ttu-id="f25c9-143">InstanceId スイッチを指定する必要があるのは、`Resume` 操作および `Terminate` 操作だけです。</span><span class="sxs-lookup"><span data-stu-id="f25c9-143">The InstanceId switch is only required for `Resume` and `Terminate` operations.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="f25c9-144">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="f25c9-144">To cleanup (Optional)</span></span>

1. <span data-ttu-id="f25c9-145">`vs2010` コマンド プロンプトから Compmgmt.msc を実行して、[コンピューターの管理] コンソールを開きます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-145">Open the Computer Management console by running Compmgmt.msc from a `vs2010` command prompt.</span></span>

2. <span data-ttu-id="f25c9-146">[ **サービスとアプリケーション**]、[ **メッセージキュー**]、[ **専用キュー**] の順に展開します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-146">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>

3. <span data-ttu-id="f25c9-147">**[Receivetx]** キューを削除します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-147">Delete the **ReceiveTx** queue.</span></span>

4. <span data-ttu-id="f25c9-148">永続性データベースを削除するには、cleanup.cmd を実行します。</span><span class="sxs-lookup"><span data-stu-id="f25c9-148">To remove the persistence database, run cleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f25c9-149">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f25c9-149">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f25c9-150">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f25c9-150">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f25c9-151">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="f25c9-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f25c9-152">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f25c9-152">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\SuspendedInstanceManagement`
