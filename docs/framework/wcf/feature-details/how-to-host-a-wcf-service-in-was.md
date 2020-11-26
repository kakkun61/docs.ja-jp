---
title: '方法: WAS で WCF サービスをホストする'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 640cfdd7525fb9877c6f3551a1456fed29c99b8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244406"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="4db0f-102">方法: WAS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="4db0f-102">How to: Host a WCF Service in WAS</span></span>

<span data-ttu-id="4db0f-103">このトピックでは、Windows プロセスアクティブ化サービス (WAS) でホストされる Windows Communication Foundation (WCF) サービスを作成するために必要な基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="4db0f-104">WAS は、HTTP 以外のトランスポート プロトコルで動作するインターネット インフォメーション サービス (IIS) 機能を一般化した新しいプロセス アクティブ化サービスです。</span><span class="sxs-lookup"><span data-stu-id="4db0f-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="4db0f-105">WCF では、リスナーアダプターインターフェイスを使用して、WCF でサポートされている HTTP 以外のプロトコル (TCP、名前付きパイプ、メッセージキューなど) を介して受信されるアクティブ化要求を伝達します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="4db0f-106">このホスト オプションでは、WAS アクティブ化コンポーネントのインストールと構成が正しく行われている必要がありますが、アプリケーションの一部としてホスト コードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4db0f-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="4db0f-107">WAS のインストールと構成の詳細については、「 [方法: WCF アクティブ化コンポーネントをインストールおよび構成](how-to-install-and-configure-wcf-activation-components.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db0f-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="4db0f-108">Web サーバーの要求処理パイプラインをクラシック モードに設定すると、WAS のアクティブ化がサポートされません。</span><span class="sxs-lookup"><span data-stu-id="4db0f-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="4db0f-109">WAS のアクティブ化を使用する場合は、Web サーバーの要求処理パイプラインを統合モードに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4db0f-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="4db0f-110">WCF サービスが WAS でホストされている場合、標準のバインドが通常の方法で使用されます。</span><span class="sxs-lookup"><span data-stu-id="4db0f-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="4db0f-111">ただし、WAS でホストされるサービスを <xref:System.ServiceModel.NetTcpBinding> や <xref:System.ServiceModel.NetNamedPipeBinding> を使用して構成する場合は、制限を遵守する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4db0f-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="4db0f-112">つまり、異なるエンドポイントが同じトランスポートを使用する場合、次の 7 つのプロパティでバインディング設定が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4db0f-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="4db0f-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="4db0f-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="4db0f-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="4db0f-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="4db0f-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="4db0f-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="4db0f-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="4db0f-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="4db0f-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="4db0f-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="4db0f-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="4db0f-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="4db0f-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="4db0f-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="4db0f-120">バインディングの設定が一致しない場合、これらのプロパティの値は常に最初に初期化されたエンドポイントによって決定されるため、後で追加されるエンドポイントは <xref:System.ServiceModel.ServiceActivationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="4db0f-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="4db0f-121">この例のソースコピーについては、「 [TCP Activation](../samples/tcp-activation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db0f-121">For the source copy of this example, see [TCP Activation](../samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="4db0f-122">WAS でホストされる基本サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="4db0f-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="4db0f-123">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="4db0f-124">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="4db0f-125">アドレス情報とバインディング情報はサービスの実装内では指定されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4db0f-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="4db0f-126">同様に、コードは構成ファイルから情報を取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4db0f-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="4db0f-127"><xref:System.ServiceModel.NetTcpBinding> エンドポイントによって使用される `CalculatorService` バインディングを定義する Web.config ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="4db0f-128">次のコードを含む Service.svc ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="4db0f-129">IIS 仮想ディレクトリに Service.svc ファイルを配置します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="4db0f-130">サービスを使用するクライアントを作成するには</span><span class="sxs-lookup"><span data-stu-id="4db0f-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="4db0f-131">コマンドラインから [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、サービスメタデータからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="4db0f-132">生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4db0f-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="4db0f-133">生成されたクライアント アプリケーションは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="4db0f-134">このサービスの実装では、アドレス情報とバインディング情報が指定されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4db0f-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="4db0f-135">同様に、コードは構成ファイルから情報を取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4db0f-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="4db0f-136"><xref:System.ServiceModel.NetTcpBinding> を使用するクライアントの構成は、Svcutil.exe で生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4db0f-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="4db0f-137">Visual Studio を使用する場合は、このファイルの名前は App.config ファイル内で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4db0f-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="4db0f-138">アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="4db0f-139">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="4db0f-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db0f-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="4db0f-140">See also</span></span>

- [<span data-ttu-id="4db0f-141">TCP アクティベーション</span><span class="sxs-lookup"><span data-stu-id="4db0f-141">TCP Activation</span></span>](../samples/tcp-activation.md)
- <span data-ttu-id="4db0f-142">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="4db0f-142">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
