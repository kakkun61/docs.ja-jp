---
title: WCF サービスの簡略化された構成
description: WCF を使用して、一般的なサービスとクライアントを実装して構成する方法について説明します。 サービスは、構成ファイルで指定されたエンドポイントを使用して通信します。
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 087618d603ea1c7df75ab5383f6c95b781dca847
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290024"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="77e62-104">WCF サービスの簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="77e62-104">Simplified Configuration for WCF Services</span></span>

<span data-ttu-id="77e62-105">このサンプルでは、Windows Communication Foundation (WCF) を使用して、一般的なサービスとクライアントを実装して構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="77e62-105">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="77e62-106">このサンプルは、他のすべての基本的な技術サンプルの基礎になります。</span><span class="sxs-lookup"><span data-stu-id="77e62-106">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="77e62-107">このサービスは、サービスと通信するためのエンドポイントを公開し、.NET Framework 4 の簡略化された構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="77e62-107">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="77e62-108">.NET Framework 4 より前の場合、エンドポイントは通常、次の構成コード例に示すように、構成ファイル (Web.config) で定義されます。</span><span class="sxs-lookup"><span data-stu-id="77e62-108">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="77e62-109">.NET Framework 4 では、 `<service>` 要素は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="77e62-109">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="77e62-110">サービスでエンドポイントが定義されていない場合、各ベース アドレスのエンドポイントと実装されたコントラクトがサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="77e62-110">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="77e62-111">このベース アドレスがコントラクト名に追加されてエンドポイントが決定され、バインドがアドレス スキームで決定されます。</span><span class="sxs-lookup"><span data-stu-id="77e62-111">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="77e62-112">次のコード例は、簡略化された構成ファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="77e62-112">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="77e62-113">構成されているように、 `http://localhost/servicemodelsamples/service.svc` 同じコンピューター上のクライアントからサービスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="77e62-113">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="77e62-114">リモート コンピューター上のクライアントがサービスにアクセスするには、localhost の代わりに完全修飾ドメイン名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77e62-114">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="77e62-115">既定では、サービスはメタデータを公開しません。</span><span class="sxs-lookup"><span data-stu-id="77e62-115">The service does not expose metadata by default.</span></span> <span data-ttu-id="77e62-116">そのため、サービスは <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 動作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="77e62-116">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="77e62-117">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="77e62-117">To use this sample</span></span>  
  
1. <span data-ttu-id="77e62-118">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="77e62-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="77e62-119">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="77e62-119">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="77e62-120">次の手順に従ってサンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="77e62-120">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="77e62-121">**サービス** プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] をクリックして、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="77e62-121">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="77e62-122">コンソール出力でサービスが動作していることが確認されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="77e62-122">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="77e62-123">**クライアント** プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] をクリックして、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="77e62-123">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77e62-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="77e62-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="77e62-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="77e62-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="77e62-126">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="77e62-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77e62-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="77e62-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="77e62-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="77e62-128">See also</span></span>

- <span data-ttu-id="77e62-129">[AppFabric の管理のサンプル](/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="77e62-129">[AppFabric Management Samples](/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="77e62-130">簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="77e62-130">Simplified Configuration</span></span>](../simplified-configuration.md)
