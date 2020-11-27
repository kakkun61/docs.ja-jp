---
title: トレースとメッセージ ログ
description: この WFC サンプルを使用して、サービストレースビューアーツール (SvcTraceViewer.exe) を使用してトレースとメッセージログを表示する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: ec29ac03e8930bd30ccd7e90dce3993ca9e7443a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255417"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="1a0a3-103">トレースとメッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="1a0a3-103">Tracing and Message Logging</span></span>

<span data-ttu-id="1a0a3-104">このサンプルでは、トレースとメッセージ ログを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-104">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="1a0a3-105">結果のトレースとメッセージログは、 [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)を使用して表示されます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-105">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="1a0a3-106">このサンプルは、 [はじめに](getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-106">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a0a3-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="1a0a3-108">トレース</span><span class="sxs-lookup"><span data-stu-id="1a0a3-108">Tracing</span></span>  

 <span data-ttu-id="1a0a3-109">Windows Communication Foundation (WCF) は、名前空間で定義されているトレース機構を使用し <xref:System.Diagnostics> ます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-109">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="1a0a3-110">このトレース モデルのトレース データは、アプリケーションが実装するトレース ソースによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-110">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="1a0a3-111">各ソースは、名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-111">Each source is identified by a name.</span></span> <span data-ttu-id="1a0a3-112">トレース コンシューマでは、情報を取得するトレース ソースのトレース リスナが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-112">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="1a0a3-113">トレース データを受け取るには、トレース ソースのリスナを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-113">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="1a0a3-114">WCF では、サービスモデルのトレースソースを設定することによって、サービスまたはクライアントの構成ファイルに次のコードを追加することで、これを行うことができ `switchValue` ます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-114">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="1a0a3-115">トレースソースの詳細については、「トレースの [構成](../diagnostics/tracing/configuring-tracing.md) 」トピックの「トレースソース」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-115">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="1a0a3-116">アクティビティのトレースと伝達</span><span class="sxs-lookup"><span data-stu-id="1a0a3-116">Activity Tracing and Propagation</span></span>  

 <span data-ttu-id="1a0a3-117">`ActivityTracing` `propagateActivity` クライアントとサービスの両方のトレースソースに対してを有効にし、をに設定すると、 `true` `system.ServiceModel` 処理の論理単位 (アクティビティ) 内のトレース、エンドポイント内のアクティビティ間 (アクティビティの転送を通じて)、および複数のエンドポイントにまたがるアクティビティ (アクティビティ ID の伝達を通じて) の相関関係が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-117">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="1a0a3-118">3 つの機構 (アクティビティ、転送、および伝達) により、サービス トレース ビューア ツールを使用してエラーの根本原因をより迅速に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-118">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="1a0a3-119">詳細については、「 [サービストレースビューアーを使用した相関トレースの表示」および「トラブルシューティング](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-119">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="1a0a3-120">ユーザー定義のアクティビティ トレースを作成することにより、サービス モデルによって提供されるトレースを拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-120">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="1a0a3-121">ユーザー定義のアクティビティ トレースによって、次の操作を可能にするトレース アクティビティを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-121">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="1a0a3-122">複数のトレースを作業の論理単位ごとにグループ化します。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-122">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="1a0a3-123">転送や伝達を利用してアクティビティを相互に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-123">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="1a0a3-124">WCF トレース (ログファイルのディスク領域コストなど) のパフォーマンスコストを軽減します。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-124">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="1a0a3-125">ユーザー定義のアクティビティトレースの詳細については、「 [トレースの拡張](extending-tracing.md) 」サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-125">For more information about user-defined activity trace, please see the [Extending Tracing](extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="1a0a3-126">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="1a0a3-126">Message Logging</span></span>  

 <span data-ttu-id="1a0a3-127">メッセージログは、任意の WCF アプリケーションのクライアントとサービスの両方で有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-127">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="1a0a3-128">メッセージ ログを有効にするには、クライアントとサービスのどちらかに次のコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-128">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="1a0a3-129">メッセージが記録されるときのトレースの種類は、そのメッセージがクライアントでトレースされるか、またはサーバーでトレースされるかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-129">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="1a0a3-130">たとえば、クライアントに送信される "Add" メッセージは、クライアントでは "TransportWrite" カテゴリの下でトレースされるのに対し、サービスでは同じメッセージが "TransportRead" カテゴリの下でトレースされます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-130">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="1a0a3-131">クライアントの App.config ファイルまたはサービスの Web.config ファイルの <xref:System.Diagnostics> セクションに次のコードを追加して、トレース リスナを構成します。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-131">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="1a0a3-132">メッセージは、構成ファイルで指定された対象ディレクトリ内に XML 形式で記録されます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-132">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a0a3-133">最初にログ ディレクトリが作成されていないと、トレース ファイルは作成されません。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-133">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="1a0a3-134">ディレクトリ C:\logs\ が存在することを確認するか、またはリスナの構成でログ記録用の代替ディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-134">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="1a0a3-135">詳細については、このドキュメントの最後にある初期セットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-135">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="1a0a3-136">メッセージログの詳細については、「 [メッセージログの構成](../diagnostics/configuring-message-logging.md) 」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-136">For more information about message logging, see the [Configuring Message Logging](../diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1a0a3-137">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="1a0a3-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1a0a3-138">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1a0a3-139">トレースとメッセージ ログのサンプルを実行する前に、サービスによって .svclog ファイルが書き込まれるディレクトリ C:\logs\ を作成します。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-139">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="1a0a3-140">このディレクトリ名は、トレースとメッセージがログ記録されるパスとして、構成ファイル内で定義されます。この名前は変更可能です。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-140">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="1a0a3-141">ユーザー Network Service に、そのログ ディレクトリへの書き込みアクセスを与えます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-141">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="1a0a3-142">ソリューションの C#、C++、または Visual Basic .NET エディションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-142">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="1a0a3-143">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1a0a3-144">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1a0a3-145">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-145">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1a0a3-146">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1a0a3-147">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1a0a3-147">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="1a0a3-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a0a3-148">See also</span></span>

- [<span data-ttu-id="1a0a3-149">トレース</span><span class="sxs-lookup"><span data-stu-id="1a0a3-149">Tracing</span></span>](../diagnostics/tracing/index.md)
- <span data-ttu-id="1a0a3-150">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1a0a3-150">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
