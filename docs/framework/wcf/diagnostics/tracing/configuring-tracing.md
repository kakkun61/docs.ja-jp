---
title: トレースの構成
description: トレースを有効にする方法、トレースソースを構成する方法、アクティビティのトレースと伝達を設定する方法、およびトレースリスナーを WCF のトレースにアクセスするように設定する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 35ac2dded5b3c727391fcad3ca950c2de4dbea64
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254442"
---
# <a name="configuring-tracing"></a><span data-ttu-id="a6806-103">トレースの構成</span><span class="sxs-lookup"><span data-stu-id="a6806-103">Configuring Tracing</span></span>

<span data-ttu-id="a6806-104">ここでは、トレースを有効にする方法、トレースを出力し、トレース レベルを設定するようにトレース ソースを構成する方法、エンドツーエンドのトレース相関をサポートするようにアクティビティ トレースと伝達を設定する方法、およびトレースにアクセスするようにトレース リスナーを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6806-104">This topic describes how you can enable tracing, configure trace sources to emit traces and set trace levels, set activity tracing and propagation to support end-to-end trace correlation, and set trace listeners to access traces.</span></span>  
  
 <span data-ttu-id="a6806-105">運用環境またはデバッグ環境でのトレース設定の推奨事項については、「 [トレースとメッセージログの推奨設定](recommended-settings-for-tracing-and-message-logging.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6806-105">For tracing settings recommendations in production or debugging environment, refer to [Recommended Settings for Tracing and Message Logging](recommended-settings-for-tracing-and-message-logging.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a6806-106">Windows 8 でアプリケーションによるトレース ログの生成を行うには、アプリケーションを権限の高い状態で実行 (管理者として実行) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-106">On Windows 8 you must run your application elevated (Run as Administrator) in order for your application to generate trace logs.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="a6806-107">トレースの有効化</span><span class="sxs-lookup"><span data-stu-id="a6806-107">Enabling Tracing</span></span>  

 <span data-ttu-id="a6806-108">Windows Communication Foundation (WCF) は、診断トレース用に次のデータを出力します。</span><span class="sxs-lookup"><span data-stu-id="a6806-108">Windows Communication Foundation (WCF) outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="a6806-109">操作呼び出し、コード例外、警告、その他の重要な処理イベントなど、アプリケーションのすべてのコンポーネントにわたるプロセスマイルストーンのトレース。</span><span class="sxs-lookup"><span data-stu-id="a6806-109">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings, and other significant processing events.</span></span>  
  
- <span data-ttu-id="a6806-110">トレース機能が正しく動作しないときの Windows エラー イベント。</span><span class="sxs-lookup"><span data-stu-id="a6806-110">Windows error events when the tracing feature malfunctions.</span></span> <span data-ttu-id="a6806-111">「 [イベントログ](../event-logging/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6806-111">See [Event Logging](../event-logging/index.md).</span></span>  
  
 <span data-ttu-id="a6806-112">WCF トレースは、の上に構築されてい <xref:System.Diagnostics> ます。</span><span class="sxs-lookup"><span data-stu-id="a6806-112">WCF tracing is built on top of <xref:System.Diagnostics>.</span></span> <span data-ttu-id="a6806-113">トレースを使用するには、構成ファイルまたはコードでトレース ソースを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-113">To use tracing, you should define trace sources in the configuration file or in code.</span></span> <span data-ttu-id="a6806-114">WCF は、WCF アセンブリごとにトレースソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="a6806-114">WCF defines a trace source for each WCF assembly.</span></span> <span data-ttu-id="a6806-115">`System.ServiceModel`トレースソースは、最も一般的な wcf トレースソースであり、wcf 通信スタック全体にわたる処理マイルストーンを記録します。これは、ユーザーコードを入力したり、そのままにしたりするためにトランスポートから移動する操作です。</span><span class="sxs-lookup"><span data-stu-id="a6806-115">The `System.ServiceModel` trace source is the most general WCF trace source, and records processing milestones across the WCF communication stack, from entering/leaving transport to entering/leaving user code.</span></span> <span data-ttu-id="a6806-116">`System.ServiceModel.MessageLogging` トレース ソースは、システムを通過するすべてのメッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="a6806-116">The `System.ServiceModel.MessageLogging` trace source records all messages that flow through the system.</span></span>  
  
 <span data-ttu-id="a6806-117">既定では、トレースは無効です。</span><span class="sxs-lookup"><span data-stu-id="a6806-117">Tracing is not enabled by default.</span></span> <span data-ttu-id="a6806-118">トレースを有効にするには、トレースリスナーを作成し、構成で選択したトレースソースに対して "Off" 以外のトレースレベルを設定する必要があります。それ以外の場合、WCF はトレースを生成しません。</span><span class="sxs-lookup"><span data-stu-id="a6806-118">To activate tracing, you must create a trace listener and set a trace level other than "Off" for the selected trace source in configuration; otherwise, WCF does not generate any traces.</span></span> <span data-ttu-id="a6806-119">リスナーを指定しないと、トレースは自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="a6806-119">If you do not specify a listener, tracing is automatically disabled.</span></span> <span data-ttu-id="a6806-120">リスナーを定義してもトレース レベルを指定しないと、トレース レベルは既定で "Off" に設定され、トレースが出力されなくなります。</span><span class="sxs-lookup"><span data-stu-id="a6806-120">If a listener is defined, but no level is specified, the level is set to "Off" by default, which means that no trace is emitted.</span></span>  
  
 <span data-ttu-id="a6806-121">カスタム操作の呼び出し元などの WCF 機能拡張ポイントを使用する場合は、独自のトレースを生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-121">If you use WCF extensibility points such as custom operation invokers, you should emit your own traces.</span></span> <span data-ttu-id="a6806-122">これは、機能拡張ポイントを実装すると、WCF は既定のパスに標準のトレースを出力できなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="a6806-122">This is because if you implement an extensibility point, WCF can no longer emit the standard traces in the default path.</span></span> <span data-ttu-id="a6806-123">トレースを出力することで手動トレースのサポートを実装しない場合、予測したトレースが得られない場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-123">If you do not implement manual tracing support by emitting traces, you may not see the traces you expect.</span></span>  
  
 <span data-ttu-id="a6806-124">トレースを構成するには、アプリケーションの構成ファイル (Web ホストアプリケーションの場合は Web.config) を編集するか、自己ホスト型アプリケーションの場合は Appname.exe.config します。</span><span class="sxs-lookup"><span data-stu-id="a6806-124">You can configure tracing by editing the application's configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted applications.</span></span> <span data-ttu-id="a6806-125">以下は、このような編集の例です。</span><span class="sxs-lookup"><span data-stu-id="a6806-125">The following is an example of such edit.</span></span> <span data-ttu-id="a6806-126">これらの設定の詳細については、「トレースを使用するためのトレースリスナーの構成」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6806-126">For more information on these settings, see the "Configuring Trace Listeners to Consume Traces" section.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"
                   type="System.Diagnostics.XmlWriterTraceListener"
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
> <span data-ttu-id="a6806-127">Visual Studio で WCF サービスプロジェクトの構成ファイルを編集するには、アプリケーションの構成ファイル (Web ホストアプリケーションの場合は Web.config) を右クリックし、自己ホスト型アプリケーションの場合は **ソリューションエクスプローラー** で Appname.exe.config します。</span><span class="sxs-lookup"><span data-stu-id="a6806-127">To edit the configuration file of a WCF service project in Visual Studio, right click the application's configuration file—either Web.config for Web-hosted applications, or Appname.exe.config for self-hosted application in **Solution Explorer**.</span></span> <span data-ttu-id="a6806-128">次に、[ **WCF 構成の編集** ] コンテキストメニュー項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="a6806-128">Then choose the **Edit WCF Configuration** context menu item.</span></span> <span data-ttu-id="a6806-129">これにより、 [構成エディターツール (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md)が起動されます。これにより、グラフィカルユーザーインターフェイスを使用して WCF サービスの構成設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-129">This launches the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md), which enables you to modify configuration settings for WCF services using a graphical user interface.</span></span>  
  
## <a name="configuring-trace-sources-to-emit-traces"></a><span data-ttu-id="a6806-130">トレースを出力するためのトレース ソースの構成</span><span class="sxs-lookup"><span data-stu-id="a6806-130">Configuring Trace Sources to Emit Traces</span></span>  

 <span data-ttu-id="a6806-131">WCF は、アセンブリごとにトレースソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="a6806-131">WCF defines a trace source for each assembly.</span></span> <span data-ttu-id="a6806-132">アセンブリ内で生成されたトレースは、該当するソースで定義されているリスナーによってアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="a6806-132">Traces generated within an assembly are accessed by the listeners defined for that source.</span></span> <span data-ttu-id="a6806-133">次のトレース ソースが定義されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-133">The following trace sources are defined:</span></span>  
  
- <span data-ttu-id="a6806-134">System.servicemodel: WCF 処理のすべての段階をログに記録します。構成が読み込まれるたびに、メッセージがトランスポートで処理され、セキュリティ処理が行われ、ユーザーコードでメッセージがディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="a6806-134">System.ServiceModel: Logs all stages of WCF processing, whenever configuration is read, a message is processed in transport, security processing, a message is dispatched in user code, and so on.</span></span>  
  
- <span data-ttu-id="a6806-135">System.ServiceModel.MessageLogging: システムを通過するすべてのメッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="a6806-135">System.ServiceModel.MessageLogging: Logs all messages that flow through the system.</span></span>  
  
- <span data-ttu-id="a6806-136">System.IdentityModel</span><span class="sxs-lookup"><span data-stu-id="a6806-136">System.IdentityModel.</span></span>  
  
- <span data-ttu-id="a6806-137">System.ServiceModel.Activation</span><span class="sxs-lookup"><span data-stu-id="a6806-137">System.ServiceModel.Activation.</span></span>  
  
- <span data-ttu-id="a6806-138">System.IO.Log: Common Log File System (CLFS) への .NET Framework インターフェイスを記録します。</span><span class="sxs-lookup"><span data-stu-id="a6806-138">System.IO.Log: Logging for the .NET Framework interface to the Common Log File System (CLFS).</span></span>  
  
- <span data-ttu-id="a6806-139">System.Runtime.Serialization: オブジェクトの読み取りまたは書き込みを記録します。</span><span class="sxs-lookup"><span data-stu-id="a6806-139">System.Runtime.Serialization: Logs when objects are read or written.</span></span>  
  
- <span data-ttu-id="a6806-140">CardSpace</span><span class="sxs-lookup"><span data-stu-id="a6806-140">CardSpace.</span></span>  
  
 <span data-ttu-id="a6806-141">各トレース ソースは、次の構成例に示すように同じ (共有) リスナーを使用するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-141">You can configure each trace source to use the same (shared) listener, as indicated in the following configuration example.</span></span>  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="a6806-142">さらに、次の例に示すように、ユーザー定義のトレース ソースを追加してユーザー コード トレースを出力することもできます。</span><span class="sxs-lookup"><span data-stu-id="a6806-142">In addition, you can add user-defined trace sources, as demonstrated by the following example, to emit user code traces.</span></span>  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />
</system.diagnostics>  
```  
  
 <span data-ttu-id="a6806-143">ユーザー定義トレースソースの作成の詳細については、「 [トレースの拡張](../../samples/extending-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6806-143">For more information about creating user-defined trace sources, see [Extending Tracing](../../samples/extending-tracing.md).</span></span>  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a><span data-ttu-id="a6806-144">トレースを使用するためのトレース リスナーの構成</span><span class="sxs-lookup"><span data-stu-id="a6806-144">Configuring Trace Listeners to Consume Traces</span></span>  

 <span data-ttu-id="a6806-145">実行時に、WCF はデータを処理するリスナーにトレースデータをフィードします。</span><span class="sxs-lookup"><span data-stu-id="a6806-145">At runtime, WCF feeds trace data to the listeners, which process the data.</span></span> <span data-ttu-id="a6806-146">WCF には、の定義済みリスナーがいくつか用意されて <xref:System.Diagnostics> います。これは、出力に使用する形式が異なります。</span><span class="sxs-lookup"><span data-stu-id="a6806-146">WCF provides several predefined listeners for <xref:System.Diagnostics>, which differ in the format they use for output.</span></span> <span data-ttu-id="a6806-147">カスタム リスナーの種類を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="a6806-147">You can also add custom listener types.</span></span>  
  
 <span data-ttu-id="a6806-148">`add` を使用して、使用するトレース リスナーの名前と種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-148">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="a6806-149">この例の構成では、リスナーに `traceListener` という名前を付け、使用する種類として標準の .NET Framework トレース リスナー (`System.Diagnostics.XmlWriterTraceListener`) を追加しています。</span><span class="sxs-lookup"><span data-stu-id="a6806-149">In our example configuration, we named the Listener `traceListener` and added the standard .NET Framework trace listener (`System.Diagnostics.XmlWriterTraceListener`) as the type we want to use.</span></span> <span data-ttu-id="a6806-150">ソースごとに任意の数のトレース リスナーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-150">You can add any number of trace listeners for each source.</span></span> <span data-ttu-id="a6806-151">トレース リスナーがトレースをファイルに出力する場合は、構成ファイルで出力ファイルの場所と名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-151">If the trace listener emits the trace to a file, you must specify the output file location and name in the configuration file.</span></span> <span data-ttu-id="a6806-152">指定するには、`initializeData` をそのリスナーのファイルの名前に設定します。</span><span class="sxs-lookup"><span data-stu-id="a6806-152">This is done by setting `initializeData` to the name of the file for that listener.</span></span> <span data-ttu-id="a6806-153">ファイル名を指定しないと、使用するリスナーの種類に基づいて任意のファイル名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-153">If you do not specify a file name, a random file name is generated based on the listener type used.</span></span> <span data-ttu-id="a6806-154"><xref:System.Diagnostics.XmlWriterTraceListener> を使用した場合は、拡張子のないファイル名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-154">If <xref:System.Diagnostics.XmlWriterTraceListener> is used, a file name with no extension is generated.</span></span> <span data-ttu-id="a6806-155">カスタム リスナーを実装した場合は、この属性を使用して、ファイル名以外の初期化データを受け取ることもできます。</span><span class="sxs-lookup"><span data-stu-id="a6806-155">If you implement a custom listener, you can also use this attribute to receive initialization data other than a filename.</span></span> <span data-ttu-id="a6806-156">たとえば、この属性にデータベース識別子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-156">For example, you can specify a database identifier for this attribute.</span></span>  
  
 <span data-ttu-id="a6806-157">カスタム トレース リスナーは、ネットワーク上のリモート データベースなどにトレースを送信するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-157">You can configure a custom trace listener to send traces on the wire, for example, to a remote database.</span></span> <span data-ttu-id="a6806-158">アプリケーションを展開するユーザーは、リモート コンピューターのトレース ログに適切なアクセス制御を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-158">As an application deployer, you should enforce proper access control on the trace logs in the remote machine.</span></span>  
  
 <span data-ttu-id="a6806-159">また、トレース リスナーはプログラムによって構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a6806-159">You can also configure a trace listener programmatically.</span></span> <span data-ttu-id="a6806-160">詳細については、「 [方法: トレースリスナーを作成および初期化](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) する」および「 [カスタム TraceListener の作成](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6806-160">For more information, see [How to: Create and Initialize Trace Listeners](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) and [Creating a Custom TraceListener](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a6806-161">`System.Diagnostics.XmlWriterTraceListener` はスレッド セーフではないため、トレース ソースは、トレースを出力するときにリソースを排他的にロックする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-161">Because `System.Diagnostics.XmlWriterTraceListener` is not thread-safe, the trace source may lock resources exclusively when outputting traces.</span></span> <span data-ttu-id="a6806-162">このリスナーを使用するように構成されたトレース ソースに多くのスレッドがトレースを出力すると、リソースの競合が発生し、パフォーマンスに重大な問題が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-162">When many threads output traces to a trace source configured to use this listener, resource contention may occur, which results in a significant performance issue.</span></span> <span data-ttu-id="a6806-163">この問題を解決するには、スレッド セーフなカスタム リスナーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-163">To resolve this problem, you should implement a custom listener that is thread-safe.</span></span>  
  
## <a name="trace-level"></a><span data-ttu-id="a6806-164">トレース レベル</span><span class="sxs-lookup"><span data-stu-id="a6806-164">Trace Level</span></span>  

 <span data-ttu-id="a6806-165">トレース レベルは、トレース ソースの `switchValue` 設定で制御します。</span><span class="sxs-lookup"><span data-stu-id="a6806-165">The tracing level is controlled by the `switchValue` setting of the trace source.</span></span> <span data-ttu-id="a6806-166">使用できるトレース レベルを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a6806-166">The available tracing levels are described in the following table.</span></span>  
  
|<span data-ttu-id="a6806-167">トレース レベル</span><span class="sxs-lookup"><span data-stu-id="a6806-167">Trace Level</span></span>|<span data-ttu-id="a6806-168">追跡イベントの性質</span><span class="sxs-lookup"><span data-stu-id="a6806-168">Nature of the Tracked Events</span></span>|<span data-ttu-id="a6806-169">追跡イベントの内容</span><span class="sxs-lookup"><span data-stu-id="a6806-169">Content of the Tracked Events</span></span>|<span data-ttu-id="a6806-170">追跡イベント</span><span class="sxs-lookup"><span data-stu-id="a6806-170">Tracked Events</span></span>|<span data-ttu-id="a6806-171">対象ユーザー</span><span class="sxs-lookup"><span data-stu-id="a6806-171">User Target</span></span>|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|<span data-ttu-id="a6806-172">オフ</span><span class="sxs-lookup"><span data-stu-id="a6806-172">Off</span></span>|<span data-ttu-id="a6806-173">該当なし</span><span class="sxs-lookup"><span data-stu-id="a6806-173">N/A</span></span>|<span data-ttu-id="a6806-174">該当なし</span><span class="sxs-lookup"><span data-stu-id="a6806-174">N/A</span></span>|<span data-ttu-id="a6806-175">トレースは出力されません。</span><span class="sxs-lookup"><span data-stu-id="a6806-175">No traces are emitted.</span></span>|<span data-ttu-id="a6806-176">該当なし</span><span class="sxs-lookup"><span data-stu-id="a6806-176">N/A</span></span>|  
|<span data-ttu-id="a6806-177">Critical</span><span class="sxs-lookup"><span data-stu-id="a6806-177">Critical</span></span>|<span data-ttu-id="a6806-178">"否定的な" イベント: 予期しない処理またはエラー状態を示すイベント。</span><span class="sxs-lookup"><span data-stu-id="a6806-178">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>||<span data-ttu-id="a6806-179">次の例を含む未処理の例外が記録されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-179">Unhandled exceptions including the following are logged:</span></span><br /><br /> <span data-ttu-id="a6806-180">-OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="a6806-180">-   OutOfMemoryException</span></span><br /><span data-ttu-id="a6806-181">-ThreadAbortException (CLR は任意の ThreadAbortExceptionHandler を呼び出します)</span><span class="sxs-lookup"><span data-stu-id="a6806-181">-   ThreadAbortException (the CLR invokes any ThreadAbortExceptionHandler)</span></span><br /><span data-ttu-id="a6806-182">-StackOverflowException (キャッチできません)</span><span class="sxs-lookup"><span data-stu-id="a6806-182">-   StackOverflowException (cannot be caught)</span></span><br /><span data-ttu-id="a6806-183">-System.configuration.configurationerrorsexception</span><span class="sxs-lookup"><span data-stu-id="a6806-183">-   ConfigurationErrorsException</span></span><br /><span data-ttu-id="a6806-184">-SEHException</span><span class="sxs-lookup"><span data-stu-id="a6806-184">-   SEHException</span></span><br /><span data-ttu-id="a6806-185">-アプリケーション開始エラー</span><span class="sxs-lookup"><span data-stu-id="a6806-185">-   Application start errors</span></span><br /><span data-ttu-id="a6806-186">-Failfast イベント</span><span class="sxs-lookup"><span data-stu-id="a6806-186">-   Failfast events</span></span><br /><span data-ttu-id="a6806-187">-システムがハングする</span><span class="sxs-lookup"><span data-stu-id="a6806-187">-   System hangs</span></span><br /><span data-ttu-id="a6806-188">-有害メッセージ: アプリケーションが失敗する原因となるメッセージトレース。</span><span class="sxs-lookup"><span data-stu-id="a6806-188">-   Poison messages: message traces that cause the application to fail.</span></span>|<span data-ttu-id="a6806-189">管理者</span><span class="sxs-lookup"><span data-stu-id="a6806-189">Administrators</span></span><br /><br /> <span data-ttu-id="a6806-190">アプリケーション開発者</span><span class="sxs-lookup"><span data-stu-id="a6806-190">Application developers</span></span>|  
|<span data-ttu-id="a6806-191">エラー</span><span class="sxs-lookup"><span data-stu-id="a6806-191">Error</span></span>|<span data-ttu-id="a6806-192">"否定的な" イベント: 予期しない処理またはエラー状態を示すイベント。</span><span class="sxs-lookup"><span data-stu-id="a6806-192">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="a6806-193">予期しない処理が発生した。</span><span class="sxs-lookup"><span data-stu-id="a6806-193">Unexpected processing has happened.</span></span> <span data-ttu-id="a6806-194">アプリケーションが、タスクを正常に実行できなかった。</span><span class="sxs-lookup"><span data-stu-id="a6806-194">The application was not able to perform a task as expected.</span></span> <span data-ttu-id="a6806-195">ただし、アプリケーションは依然として動作している。</span><span class="sxs-lookup"><span data-stu-id="a6806-195">However, the application is still up and running.</span></span>|<span data-ttu-id="a6806-196">すべての例外がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-196">All exceptions are logged.</span></span>|<span data-ttu-id="a6806-197">管理者</span><span class="sxs-lookup"><span data-stu-id="a6806-197">Administrators</span></span><br /><br /> <span data-ttu-id="a6806-198">アプリケーション開発者</span><span class="sxs-lookup"><span data-stu-id="a6806-198">Application developers</span></span>|  
|<span data-ttu-id="a6806-199">警告</span><span class="sxs-lookup"><span data-stu-id="a6806-199">Warning</span></span>|<span data-ttu-id="a6806-200">"否定的な" イベント: 予期しない処理またはエラー状態を示すイベント。</span><span class="sxs-lookup"><span data-stu-id="a6806-200">"Negative" events: events that indicate an unexpected processing or an error condition.</span></span>|<span data-ttu-id="a6806-201">問題が発生したか、発生する可能性があるが、アプリケーションは正常に動作している。</span><span class="sxs-lookup"><span data-stu-id="a6806-201">A possible problem has occurred or may occur, but the application still functions correctly.</span></span> <span data-ttu-id="a6806-202">ただし、正常な動作を継続できなくなる可能性がある。</span><span class="sxs-lookup"><span data-stu-id="a6806-202">However, it may not continue to work properly.</span></span>|<span data-ttu-id="a6806-203">-アプリケーションは、制限設定によって許可されているよりも多くの要求を受信しています。</span><span class="sxs-lookup"><span data-stu-id="a6806-203">-   The application is receiving more requests than its throttling settings allow.</span></span><br /><span data-ttu-id="a6806-204">-受信キューが、構成されている最大容量に近づいています。</span><span class="sxs-lookup"><span data-stu-id="a6806-204">-   The receiving queue is near its maximum configured capacity.</span></span><br /><span data-ttu-id="a6806-205">-タイムアウトを超えました。</span><span class="sxs-lookup"><span data-stu-id="a6806-205">-   Timeout has exceeded.</span></span><br /><span data-ttu-id="a6806-206">-資格情報は拒否されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-206">-   Credentials are rejected.</span></span>|<span data-ttu-id="a6806-207">管理者</span><span class="sxs-lookup"><span data-stu-id="a6806-207">Administrators</span></span><br /><br /> <span data-ttu-id="a6806-208">アプリケーション開発者</span><span class="sxs-lookup"><span data-stu-id="a6806-208">Application developers</span></span>|  
|<span data-ttu-id="a6806-209">情報</span><span class="sxs-lookup"><span data-stu-id="a6806-209">Information</span></span>|<span data-ttu-id="a6806-210">"肯定的な" イベント: 成功したマイルストーンをマークするイベント</span><span class="sxs-lookup"><span data-stu-id="a6806-210">"Positive" events: events that mark successful milestones</span></span>|<span data-ttu-id="a6806-211">アプリケーションが正常に動作しているかどうかとは無関係の、アプリケーションの実行に関する重要で正常なマイルストーン。</span><span class="sxs-lookup"><span data-stu-id="a6806-211">Important and successful milestones of application execution, regardless of whether the application is working properly or not.</span></span>|<span data-ttu-id="a6806-212">一般に、システム ステータスの監視と診断、パフォーマンスの計測、またはプロファイリングに有用なメッセージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-212">In general, messages helpful for monitoring and diagnosing system status, measuring performance or profiling are generated.</span></span> <span data-ttu-id="a6806-213">この情報は、キャパシティ プランニングやパフォーマンス管理のために利用できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-213">You can use such information for capacity planning and performance management:</span></span><br /><br /> <span data-ttu-id="a6806-214">-チャネルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-214">-   Channels are created.</span></span><br /><span data-ttu-id="a6806-215">-エンドポイントリスナーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-215">-   Endpoint listeners are created.</span></span><br /><span data-ttu-id="a6806-216">-Message はトランスポートに出入りします。</span><span class="sxs-lookup"><span data-stu-id="a6806-216">-   Message enters/leaves transport.</span></span><br /><span data-ttu-id="a6806-217">-セキュリティトークンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-217">-   Security token is retrieved.</span></span><br /><span data-ttu-id="a6806-218">-構成設定が読み取られます。</span><span class="sxs-lookup"><span data-stu-id="a6806-218">-   Configuration setting is read.</span></span>|<span data-ttu-id="a6806-219">管理者</span><span class="sxs-lookup"><span data-stu-id="a6806-219">Administrators</span></span><br /><br /> <span data-ttu-id="a6806-220">アプリケーション開発者</span><span class="sxs-lookup"><span data-stu-id="a6806-220">Application developers</span></span><br /><br /> <span data-ttu-id="a6806-221">製品開発者。</span><span class="sxs-lookup"><span data-stu-id="a6806-221">Product developers.</span></span>|  
|<span data-ttu-id="a6806-222">"詳細"</span><span class="sxs-lookup"><span data-stu-id="a6806-222">Verbose</span></span>|<span data-ttu-id="a6806-223">"肯定的な" イベント: 成功したマイルストーンをマークするイベント。</span><span class="sxs-lookup"><span data-stu-id="a6806-223">"Positive" events: events that mark successful milestones.</span></span>|<span data-ttu-id="a6806-224">ユーザーコードとサービスの両方に対する低レベルのイベントが出力されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-224">Low-level events for both user code and servicing are emitted.</span></span>|<span data-ttu-id="a6806-225">一般に、このレベルはデバッグやアプリケーションの最適化に利用できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-225">In general, you can use this level for debugging or application optimization.</span></span><br /><br /> <span data-ttu-id="a6806-226">-メッセージヘッダーを認識しています。</span><span class="sxs-lookup"><span data-stu-id="a6806-226">-   Understood message header.</span></span>|<span data-ttu-id="a6806-227">管理者</span><span class="sxs-lookup"><span data-stu-id="a6806-227">Administrators</span></span><br /><br /> <span data-ttu-id="a6806-228">アプリケーション開発者</span><span class="sxs-lookup"><span data-stu-id="a6806-228">Application developers</span></span><br /><br /> <span data-ttu-id="a6806-229">製品開発者。</span><span class="sxs-lookup"><span data-stu-id="a6806-229">Product developers.</span></span>|  
|<span data-ttu-id="a6806-230">ActivityTracing</span><span class="sxs-lookup"><span data-stu-id="a6806-230">ActivityTracing</span></span>||<span data-ttu-id="a6806-231">処理アクティビティとコンポーネント間のフロー イベント。</span><span class="sxs-lookup"><span data-stu-id="a6806-231">Flow events between processing activities and components.</span></span>|<span data-ttu-id="a6806-232">このレベルを使用すると、管理者と開発者は同じアプリケーション ドメイン内のアプリケーションの相関関係を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="a6806-232">This level allows administrators and developers to correlate applications in the same application domain:</span></span><br /><br /> <span data-ttu-id="a6806-233">-開始/停止などのアクティビティ境界のトレース。</span><span class="sxs-lookup"><span data-stu-id="a6806-233">-   Traces for activity boundaries, such as start/stop.</span></span><br /><span data-ttu-id="a6806-234">-転送のトレース。</span><span class="sxs-lookup"><span data-stu-id="a6806-234">-   Traces for transfers.</span></span>|<span data-ttu-id="a6806-235">すべて</span><span class="sxs-lookup"><span data-stu-id="a6806-235">All</span></span>|  
|<span data-ttu-id="a6806-236">すべて</span><span class="sxs-lookup"><span data-stu-id="a6806-236">All</span></span>||<span data-ttu-id="a6806-237">アプリケーションが正常に動作している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-237">Application may function properly.</span></span> <span data-ttu-id="a6806-238">すべてのイベントが出力されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-238">All events are emitted.</span></span>|<span data-ttu-id="a6806-239">前のすべてのイベント。</span><span class="sxs-lookup"><span data-stu-id="a6806-239">All previous events.</span></span>|<span data-ttu-id="a6806-240">すべて</span><span class="sxs-lookup"><span data-stu-id="a6806-240">All</span></span>|  
  
 <span data-ttu-id="a6806-241">Verbose から Critical までのレベルは相互にスタックされます。つまり、各トレース レベルには、そのレベルよりも上位のすべてのレベルが含まれます (Off レベルを除く)。</span><span class="sxs-lookup"><span data-stu-id="a6806-241">The levels from Verbose to Critical are stacked on top of each other, that is, each trace level includes all levels above it except the Off level.</span></span> <span data-ttu-id="a6806-242">たとえば、Warning レベルでリッスンしているリスナーは、Critical、Error、Warning の各トレースを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a6806-242">For example, a listener listening at the Warning level receives Critical, Error, and Warning traces.</span></span> <span data-ttu-id="a6806-243">All レベルには、Verbose から Critical までのイベントとアクティビティ トレース イベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6806-243">The All level includes events from Verbose to Critical and Activity tracing events.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="a6806-244">Information、Verbose、および ActivityTracing の各レベルは、多くのトレースを生成するため、コンピューターで利用可能なすべてのリソースを使い果たした場合は、メッセージ スループットに悪影響を及ぼす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a6806-244">The Information, Verbose, and ActivityTracing levels generate a lot of traces, which may negatively impact message throughput if you have used up all available resources on the machine.</span></span>  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a><span data-ttu-id="a6806-245">アクティビティ トレースと伝達の関連付けの構成</span><span class="sxs-lookup"><span data-stu-id="a6806-245">Configuring Activity Tracing and Propagation for Correlation</span></span>  

 <span data-ttu-id="a6806-246">`activityTracing` 属性に指定する `switchValue` 値を使用してアクティビティ トレースを有効にし、エンドポイント内のアクティビティの境界と転送のトレースを出力できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-246">The `activityTracing` value specified for the `switchValue` attribute is used to enable activity tracing, which emits traces for activity boundaries and transfers within endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6806-247">WCF で特定の機能拡張機能を使用する場合、 <xref:System.NullReferenceException> アクティビティトレースが有効になっていると、が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="a6806-247">When you use certain extensibility features in WCF, you might get a <xref:System.NullReferenceException> when activity tracing is enabled.</span></span> <span data-ttu-id="a6806-248">この問題を解決するには、アプリケーションの構成ファイルを調べて、トレース ソースの `switchValue` 属性が `activityTracing` に設定されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="a6806-248">To fix this problem, check your application's configuration file and ensure that the `switchValue` attribute for your trace source is not set to `activityTracing`.</span></span>  
  
 <span data-ttu-id="a6806-249">`propagateActivity` 属性は、メッセージ交換に参加している他のエンドポイントにアクティビティを伝達する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a6806-249">The `propagateActivity` attribute indicates whether the activity should be propagated to other endpoints that participate in the message exchange.</span></span> <span data-ttu-id="a6806-250">この値を `true` に設定すると、任意の 2 つのエンドポイントで生成されたトレース ファイルを取得し、一方のエンドポイントのトレース セットがもう一方のエンドポイントのトレース セットにどのように転送されるかを監視できます。</span><span class="sxs-lookup"><span data-stu-id="a6806-250">By setting this value to `true`, you can take trace files generated by any two endpoints and observe how a set of traces on one endpoint flowed to a set of traces on another endpoint.</span></span>  
  
 <span data-ttu-id="a6806-251">アクティビティのトレースと伝達の詳細については、「 [伝達](propagation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6806-251">For more information about activity tracing and propagation, see [Propagation](propagation.md).</span></span>  
  
 <span data-ttu-id="a6806-252">`propagateActivity`と `ActivityTracing` ブール値は両方とも System.servicemodel tracesource に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-252">Both `propagateActivity` and `ActivityTracing` Boolean values apply to the System.ServiceModel TraceSource.</span></span> <span data-ttu-id="a6806-253">この `ActivityTracing` 値は、WCF またはユーザー定義のトレースソースを含む任意のトレースソースにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="a6806-253">The `ActivityTracing` value also applies to any trace source, including WCF or user-defined ones.</span></span>  
  
 <span data-ttu-id="a6806-254">ユーザー定義のトレース ソースでは、`propagateActivity` 属性を使用できません。</span><span class="sxs-lookup"><span data-stu-id="a6806-254">You cannot use the `propagateActivity` attribute with user-defined trace sources.</span></span> <span data-ttu-id="a6806-255">ユーザー コード アクティビティ ID の伝達では、ServiceModel `ActivityTracing` 属性を `propagateActivity` に設定しているときは、ServiceModel `true` を設定しないでください。</span><span class="sxs-lookup"><span data-stu-id="a6806-255">For user code activity ID propagation, make sure you do not set ServiceModel `ActivityTracing`, while still having ServiceModel `propagateActivity` attribute set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6806-256">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6806-256">See also</span></span>

- [<span data-ttu-id="a6806-257">トレース</span><span class="sxs-lookup"><span data-stu-id="a6806-257">Tracing</span></span>](index.md)
- [<span data-ttu-id="a6806-258">管理と診断</span><span class="sxs-lookup"><span data-stu-id="a6806-258">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="a6806-259">方法: トレース リスナーを作成し初期化する</span><span class="sxs-lookup"><span data-stu-id="a6806-259">How to: Create and Initialize Trace Listeners</span></span>](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [<span data-ttu-id="a6806-260">カスタム TraceListener の作成</span><span class="sxs-lookup"><span data-stu-id="a6806-260">Creating a Custom TraceListener</span></span>](/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
