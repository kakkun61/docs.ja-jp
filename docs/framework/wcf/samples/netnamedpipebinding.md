---
title: NetNamedPipeBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net Profile Named Pipe
ms.assetid: e78e845f-c325-46e2-927d-81616f97f7d5
ms.openlocfilehash: 46365c8dbfee66d719b114947f6b04069e0f8870
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235300"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="ef2d1-102">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="ef2d1-102">NetNamedPipeBinding</span></span>

<span data-ttu-id="ef2d1-103">このサンプルでは `netNamedPipeBinding` バインディングについて説明します。このバインディングは、同一コンピュータでのプロセス間通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-103">This sample demonstrates the `netNamedPipeBinding` binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="ef2d1-104">名前付きパイプは、異なるコンピューター間では動作しません。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-104">Named pipes do not work across machines.</span></span> <span data-ttu-id="ef2d1-105">このサンプルは、 [はじめに](getting-started-sample.md) 電卓サービスを基にしています。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-105">This sample is based on The [Getting Started](getting-started-sample.md) calculator service.</span></span>  
  
 <span data-ttu-id="ef2d1-106">このサンプルでは、サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-106">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="ef2d1-107">クライアントとサービスは両方ともコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-107">Both the client and the service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef2d1-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ef2d1-109">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-109">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="ef2d1-110">バインディングの種類は、要素の `binding` または [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) [ \<endpoint> \<client> の](../../configure-apps/file-schema/wcf/endpoint-of-client.md)属性で指定されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-110">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) or [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element, as shown in the following sample configuration:</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="ef2d1-111">前のサンプルでは、`netNamedPipeBinding` バインディングを既定の設定で使用するようエンドポイントを構成する手順を示しました。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-111">The previous sample shows how to configure an endpoint to use the `netNamedPipeBinding` binding with the default settings.</span></span> <span data-ttu-id="ef2d1-112">`netNamedPipeBinding` バインディングを構成してその設定の一部を変更する場合は、バインド構成を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-112">If you want to configure the `netNamedPipeBinding` binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="ef2d1-113">エンドポイントは、バインディング構成を `bindingConfiguration` 属性を使用して名前で参照します。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-113">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span>  
  
```xml  
<endpoint address="net.pipe://localhost/ServiceModelSamples/service"  
          binding="netNamedPipeBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="ef2d1-114">このサンプルでは、バインド構成の名前は `Binding1` です。これは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-114">In this sample, the binding configuration is named `Binding1` and has the following definition:</span></span>  
  
```xml  
<bindings>  
  <!--   
        Following is the expanded configuration section for a NetNamedPipeBinding.  
        Each property is configured with the default value.  
     -->  
  <netNamedPipeBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             maxBufferPoolSize="524288"  
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">  
      <security mode="Transport">  
        <transport protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netNamedPipeBinding>  
</bindings>  
```  
  
 <span data-ttu-id="ef2d1-115">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ef2d1-116">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ef2d1-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="ef2d1-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ef2d1-118">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ef2d1-119">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-119">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ef2d1-120">1台のコンピューター構成でサンプルを実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-120">To run the sample in a single machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ef2d1-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ef2d1-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ef2d1-123">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ef2d1-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ef2d1-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\NamedPipe`  
