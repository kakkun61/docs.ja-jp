---
title: WCF サービスと Event Tracing for Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b5fcfb34843d1168511141b4ce2b4f956559290a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247838"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a><span data-ttu-id="a27ea-102">WCF サービスと Event Tracing for Windows</span><span class="sxs-lookup"><span data-stu-id="a27ea-102">WCF Services and Event Tracing for Windows</span></span>

<span data-ttu-id="a27ea-103">このサンプルでは、Windows Communication Foundation (WCF) の分析トレースを使用して Windows イベントトレーシング (ETW) でイベントを出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-103">This sample demonstrates how to use the analytic tracing in Windows Communication Foundation (WCF) to emit events in Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="a27ea-104">分析トレースは、運用環境での WCF サービスのトラブルシューティングを可能にする WCF スタックの主要なポイントで生成されるイベントです。</span><span class="sxs-lookup"><span data-stu-id="a27ea-104">The analytic traces are events emitted at key points in the WCF stack that allow troubleshooting of WCF services in production environment.</span></span>

 <span data-ttu-id="a27ea-105">WCF サービスの分析トレースは、パフォーマンスへの影響を最小限に抑えながら運用環境で有効にできるトレースです。</span><span class="sxs-lookup"><span data-stu-id="a27ea-105">Analytic trace in WCF services is tracing that can be turned on in a production environment with minimal impact on performance.</span></span> <span data-ttu-id="a27ea-106">これらのトレースは、ETW セッションにイベントとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-106">These traces are emitted as events to an ETW session.</span></span>

 <span data-ttu-id="a27ea-107">このサンプルには、イベントがサービスからイベントログに出力される基本的な WCF サービスが含まれています。これは、イベントビューアーを使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-107">This sample includes a basic WCF service in which events are emitted from the service to the event log, which can be viewed using Event Viewer.</span></span> <span data-ttu-id="a27ea-108">WCF サービスからのイベントをリッスンする専用の ETW セッションを開始することもできます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-108">It is also possible to start a dedicated ETW session that listens for events from the WCF service.</span></span> <span data-ttu-id="a27ea-109">サンプルには、バイナリ ファイルにイベントを格納する専用の ETW セッションを作成するためのスクリプトが含まれています。このバイナリ ファイルもイベント ビューアーを使用して読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-109">The sample includes a script to create a dedicated ETW session that stores events in a binary file that can be read using Event Viewer.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="a27ea-110">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="a27ea-110">To use this sample</span></span>

1. <span data-ttu-id="a27ea-111">Visual Studio 2012 を使用して、EtwAnalyticTraceSample ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-111">Using Visual Studio 2012, open the EtwAnalyticTraceSample.sln solution file.</span></span>

2. <span data-ttu-id="a27ea-112">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-112">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="a27ea-113">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-113">To run the solution, press CTRL+F5.</span></span>

     <span data-ttu-id="a27ea-114">Web ブラウザーで、[ **Calculator .svc**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a27ea-114">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="a27ea-115">サービスの WSDL ドキュメントの URI がブラウザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-115">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="a27ea-116">その URI をコピーします。</span><span class="sxs-lookup"><span data-stu-id="a27ea-116">Copy that URI.</span></span>

     <span data-ttu-id="a27ea-117">既定では、サービスはポート1378で要求のリッスンを開始し `http://localhost:1378/Calculator.svc` ます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-117">By default, the service starts listening for requests on port 1378 `http://localhost:1378/Calculator.svc`.</span></span>

4. <span data-ttu-id="a27ea-118">WCF テストクライアント (WcfTestClient.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-118">Run the WCF test client (WcfTestClient.exe).</span></span>

     <span data-ttu-id="a27ea-119">WCF テストクライアント (WcfTestClient.exe) は、にあり `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe` ます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-119">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span>  <span data-ttu-id="a27ea-120">既定の Visual Studio 2012 インストールディレクトリは `C:\Program Files\Microsoft Visual Studio 10.0` です。</span><span class="sxs-lookup"><span data-stu-id="a27ea-120">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>

5. <span data-ttu-id="a27ea-121">WCF テストクライアント内で、[ **ファイル**] を選択し、[ **サービスの追加**] をクリックしてサービスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-121">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>

     <span data-ttu-id="a27ea-122">入力ボックスにエンドポイントのアドレスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-122">Add the endpoint address in the input box.</span></span> <span data-ttu-id="a27ea-123">既定値は、`http://localhost:1378/Calculator.svc` です。</span><span class="sxs-lookup"><span data-stu-id="a27ea-123">The default is `http://localhost:1378/Calculator.svc`.</span></span>

6. <span data-ttu-id="a27ea-124">イベント ビューアー アプリケーションを開きます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-124">Open the Event Viewer application.</span></span>

     <span data-ttu-id="a27ea-125">サービスを呼び出す前に、イベントビューアーを開始し、WCF サービスから生成された追跡イベントをイベントログがリッスンしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-125">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>

7. <span data-ttu-id="a27ea-126">[ **スタート** ] メニューから [ **管理ツール**] を選択し、 **イベントビューアー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a27ea-126">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span>  <span data-ttu-id="a27ea-127">**分析** ログと **デバッグ** ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a27ea-127">Enable the **Analytic** and **Debug** logs.</span></span>

8. <span data-ttu-id="a27ea-128">イベントビューアーのツリービューで、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-128">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="a27ea-129">[ **アプリケーションサーバー-アプリケーション**] を右クリックし、[ **表示**] をクリックして、[ **分析およびデバッグログ] を表示** します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-129">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>

     <span data-ttu-id="a27ea-130">[ **分析とデバッグログを表示** する] オプションがオンになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-130">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span>

9. <span data-ttu-id="a27ea-131">**分析** ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a27ea-131">Enable the **Analytic** log.</span></span>

     <span data-ttu-id="a27ea-132">イベントビューアーのツリービューで、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-132">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="a27ea-133">[ **分析** ] を右クリックし、[ **ログを有効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-133">Right-click **Analytic** and select **Enable Log**.</span></span>

#### <a name="to-test-the-service"></a><span data-ttu-id="a27ea-134">サービスをテストするには</span><span class="sxs-lookup"><span data-stu-id="a27ea-134">To test the service</span></span>

1. <span data-ttu-id="a27ea-135">WCF テストクライアントに戻り、をダブルクリック `Divide` し、既定値をそのまま使用します。既定値では、分母が0に指定されています。</span><span class="sxs-lookup"><span data-stu-id="a27ea-135">Switch back to WCF test client and double-click `Divide` and keep the default values, which specify a denominator of 0.</span></span>

     <span data-ttu-id="a27ea-136">分母が 0 の場合、サービスからエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-136">If the denominator is 0, then the service throws a fault.</span></span>

2. <span data-ttu-id="a27ea-137">サービスから出力されたイベントを確認します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-137">Observe the events emitted from the service.</span></span>

     <span data-ttu-id="a27ea-138">イベントビューアーに戻り、[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーションサーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-138">Switch back to Event Viewer and navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="a27ea-139">[ **分析** ] を右クリックし、[ **更新**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-139">Right-click **Analytic** and select **Refresh**.</span></span>

     <span data-ttu-id="a27ea-140">WCF 分析トレースのイベントがイベント ビューアーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-140">The WCF analytic trace events are displayed in the event viewer.</span></span> <span data-ttu-id="a27ea-141">サービスからエラーがスローされたため、イベント ビューアーにエラー トレース イベントが表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a27ea-141">Notice that because a fault was thrown by the service an error trace event is displayed in the event viewer.</span></span>

3. <span data-ttu-id="a27ea-142">手順 1. と 2. を繰り返します。ただし、今度は有効な入力値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-142">Repeat steps 1 and 2, but with valid inputs.</span></span> <span data-ttu-id="a27ea-143">`N2` パラメーターの値は、0 以外であれば任意の数字でかまいません。</span><span class="sxs-lookup"><span data-stu-id="a27ea-143">The value of the `N2` parameter can be any number other than 0.</span></span>

     <span data-ttu-id="a27ea-144">分析チャネルを更新して、WCF イベントにエラー イベントが含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-144">Refresh the analytic channel to view the WCF events do not include any error events.</span></span>

 <span data-ttu-id="a27ea-145">このサンプルでは、WCF サービスから出力される分析トレース イベントを示します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-145">The sample demonstrates the analytic trace events emitted from a WCF service.</span></span>

#### <a name="to-cleanup-optional"></a><span data-ttu-id="a27ea-146">クリーンアップするには (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a27ea-146">To cleanup (Optional)</span></span>

1. <span data-ttu-id="a27ea-147">イベント ビューアーを開きます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-147">Open Event Viewer.</span></span>

2. <span data-ttu-id="a27ea-148">[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーション-サーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-148">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="a27ea-149">[ **分析** ] を右クリックし、[ **ログを無効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-149">Right-click **Analytic** and select **Disable Log**.</span></span>

3. <span data-ttu-id="a27ea-150">[ **イベントビューアー**]、[ **アプリケーションとサービスログ**]、[ **Microsoft**]、[ **Windows**]、[ **アプリケーション-サーバー-アプリケーション**] の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-150">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="a27ea-151">[ **分析** ] を右クリックし、[ **ログの消去**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-151">Right-click **Analytic** and select **Clear Log**.</span></span>

4. <span data-ttu-id="a27ea-152">[ **クリア** ] オプションを選択して、イベントを消去します。</span><span class="sxs-lookup"><span data-stu-id="a27ea-152">Choose the **Clear** option to clear the events.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a27ea-153">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a27ea-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a27ea-154">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a27ea-154">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a27ea-155">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="a27ea-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a27ea-156">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a27ea-156">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a><span data-ttu-id="a27ea-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="a27ea-157">See also</span></span>

- <span data-ttu-id="a27ea-158">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a27ea-158">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
