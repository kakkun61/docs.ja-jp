---
title: パフォーマンス カウンターの使用
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: d3e6b9805bd0b9c5eea991fce4dde2035f8f5c1b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294912"
---
# <a name="using-performance-counters"></a><span data-ttu-id="02fa6-102">パフォーマンス カウンターの使用</span><span class="sxs-lookup"><span data-stu-id="02fa6-102">Using Performance Counters</span></span>

<span data-ttu-id="02fa6-103">このサンプルでは、Windows Communication Foundation (WCF) パフォーマンスカウンターにアクセスする方法と、ユーザー定義のパフォーマンスカウンターを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="02fa6-104">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="02fa6-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02fa6-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02fa6-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="02fa6-106">このサンプルでは、クライアントが `ICalculator` サービスの 4 つのメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="02fa6-107">この処理は、ユーザーが中断するまで継続して行われます。</span><span class="sxs-lookup"><span data-stu-id="02fa6-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="02fa6-108">サービスは変更されません。</span><span class="sxs-lookup"><span data-stu-id="02fa6-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="02fa6-109">パフォーマンス カウンタは、サービスの Web.config ファイルの診断セクションで有効にします。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02fa6-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="02fa6-110">このタスクは、 [構成エディターツール (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)を使用して行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="02fa6-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="02fa6-111">パフォーマンスカウンターを有効にすると、WCF パフォーマンスカウンターのスイート全体がサービスに対して有効になります。</span><span class="sxs-lookup"><span data-stu-id="02fa6-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="02fa6-112">.NET Framework は、`ServiceModelService`、`ServiceModelEndpoint`、および `ServiceModelOperation` の 3 つのレベルで、パフォーマンス データを自動的に保持します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="02fa6-113">これらの各レベルには、"呼び出し"、"1 秒あたりの呼び出し回数"、"承認されていないセキュリティ呼び出し" などのパフォーマンス カウンタがあります。</span><span class="sxs-lookup"><span data-stu-id="02fa6-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="02fa6-114">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="02fa6-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="02fa6-115">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="02fa6-116">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="02fa6-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="02fa6-117">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="02fa6-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="02fa6-118">パフォーマンス データを表示するには</span><span class="sxs-lookup"><span data-stu-id="02fa6-118">To view performance data</span></span>  
  
1. <span data-ttu-id="02fa6-119">パフォーマンスモニターツールを起動するには、[**スタート**] ボタンをクリックし、[**実行**] をクリックして、enter キーを押します。 `perfmon` または、[コントロールパネル] で [ **OK,** **管理ツール**] を選択し、[**パフォーマンス**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="02fa6-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="02fa6-120">サンプル コードが実行されるまでは、カウンタを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="02fa6-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="02fa6-121">一覧表示されているパフォーマンス カウンタを削除するには、削除するパフォーマンス カウンタを選択して Del キーを押します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="02fa6-122">WCF カウンターを追加するには、グラフペインを右クリックし、[ **カウンターの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="02fa6-123">[ **カウンターの追加** ] ダイアログボックスで、[パフォーマンスオブジェクト] ボックスの一覧の [ **ServiceModelOperation 3.0.0.0、ServiceModelEndpoint 3.0.0.0、または ServiceModelService 3.0.0.0** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="02fa6-124">表示するカウンタを一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="02fa6-125">コンピューターで WCF サービスが実行されていない場合、サービスの WCF パフォーマンスカウンターはありません。</span><span class="sxs-lookup"><span data-stu-id="02fa6-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="02fa6-126">構成エディターを使用してカウンターを有効にするには</span><span class="sxs-lookup"><span data-stu-id="02fa6-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="02fa6-127">SvcConfigEditor.exe のインスタンスを開きます。</span><span class="sxs-lookup"><span data-stu-id="02fa6-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="02fa6-128">[ファイル] メニューの [ **開く** ] をクリックし、[ **構成ファイル...**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="02fa6-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="02fa6-129">サンプル アプリケーションの service フォルダーに移動し、Web.config ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="02fa6-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="02fa6-130">構成ツリーで [ **診断** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="02fa6-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="02fa6-131">[**診断**] ウィンドウの [**パフォーマンスカウンター** ] を [すべて] に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="02fa6-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="02fa6-132">構成ファイルを保存し、エディターを終了します。</span><span class="sxs-lookup"><span data-stu-id="02fa6-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="02fa6-133">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="02fa6-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="02fa6-134">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="02fa6-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="02fa6-135">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="02fa6-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="02fa6-136">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="02fa6-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="02fa6-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="02fa6-137">See also</span></span>

- <span data-ttu-id="02fa6-138">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="02fa6-138">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
