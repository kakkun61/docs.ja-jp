---
title: トランスポート セキュリティと Windows 認証
description: このシナリオを確認します。これは、Windows セキュリティによって保護された WCF クライアント/サービスを示しています。 この例では、イントラネットサービスは人事情報を表示します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 47f5a2a3b2c8815e2ccb0cc4d4bf3c408f4992e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251738"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="c786d-104">トランスポート セキュリティと Windows 認証</span><span class="sxs-lookup"><span data-stu-id="c786d-104">Transport Security with Windows Authentication</span></span>

<span data-ttu-id="c786d-105">次のシナリオは、Windows セキュリティによって保護された Windows Communication Foundation (WCF) クライアントとサービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="c786d-105">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="c786d-106">プログラミングの詳細については、「 [方法: Windows 資格情報を使用してサービスをセキュリティで保護](../how-to-secure-a-service-with-windows-credentials.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c786d-106">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="c786d-107">イントラネットの Web サービスでは人事情報を表示しています。</span><span class="sxs-lookup"><span data-stu-id="c786d-107">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="c786d-108">クライアントは Windows フォーム アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c786d-108">The client is a Windows Form application.</span></span> <span data-ttu-id="c786d-109">このアプリケーションは、Kerberos コントローラーで保護されたドメインに展開されています。</span><span class="sxs-lookup"><span data-stu-id="c786d-109">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Windows 認証を使用する場合のトランスポート セキュリティ](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="c786d-111">特徴</span><span class="sxs-lookup"><span data-stu-id="c786d-111">Characteristic</span></span>|<span data-ttu-id="c786d-112">説明</span><span class="sxs-lookup"><span data-stu-id="c786d-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c786d-113">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="c786d-113">Security Mode</span></span>|<span data-ttu-id="c786d-114">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c786d-114">Transport</span></span>|  
|<span data-ttu-id="c786d-115">相互運用性</span><span class="sxs-lookup"><span data-stu-id="c786d-115">Interoperability</span></span>|<span data-ttu-id="c786d-116">WCF のみ</span><span class="sxs-lookup"><span data-stu-id="c786d-116">WCF only</span></span>|  
|<span data-ttu-id="c786d-117">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="c786d-117">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="c786d-118">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="c786d-118">Authentication (Client)</span></span>|<span data-ttu-id="c786d-119">○ (Windows 統合認証を使用)</span><span class="sxs-lookup"><span data-stu-id="c786d-119">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="c786d-120">○ (Windows 統合認証を使用)</span><span class="sxs-lookup"><span data-stu-id="c786d-120">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="c786d-121">整合性</span><span class="sxs-lookup"><span data-stu-id="c786d-121">Integrity</span></span>|<span data-ttu-id="c786d-122">はい</span><span class="sxs-lookup"><span data-stu-id="c786d-122">Yes</span></span>|  
|<span data-ttu-id="c786d-123">機密情報</span><span class="sxs-lookup"><span data-stu-id="c786d-123">Confidentiality</span></span>|<span data-ttu-id="c786d-124">はい</span><span class="sxs-lookup"><span data-stu-id="c786d-124">Yes</span></span>|  
|<span data-ttu-id="c786d-125">トランスポート</span><span class="sxs-lookup"><span data-stu-id="c786d-125">Transport</span></span>|<span data-ttu-id="c786d-126">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="c786d-126">NET.TCP</span></span>|  
|<span data-ttu-id="c786d-127">バインド</span><span class="sxs-lookup"><span data-stu-id="c786d-127">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="c786d-128">サービス</span><span class="sxs-lookup"><span data-stu-id="c786d-128">Service</span></span>  

 <span data-ttu-id="c786d-129">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="c786d-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c786d-130">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="c786d-130">Do one of the following:</span></span>  
  
- <span data-ttu-id="c786d-131">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c786d-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="c786d-132">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="c786d-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c786d-133">コード</span><span class="sxs-lookup"><span data-stu-id="c786d-133">Code</span></span>  

 <span data-ttu-id="c786d-134">次のコードは、Windows セキュリティを使用するサービス エンドポイントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c786d-134">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="c786d-135">構成</span><span class="sxs-lookup"><span data-stu-id="c786d-135">Configuration</span></span>  

 <span data-ttu-id="c786d-136">コードの代わりに次の構成を使用して、サービス エンドポイントをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="c786d-136">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="c786d-137">クライアント</span><span class="sxs-lookup"><span data-stu-id="c786d-137">Client</span></span>  

 <span data-ttu-id="c786d-138">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="c786d-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c786d-139">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="c786d-139">Do one of the following:</span></span>  
  
- <span data-ttu-id="c786d-140">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c786d-140">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="c786d-141">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="c786d-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="c786d-142">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="c786d-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="c786d-143">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c786d-143">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="c786d-144">コード</span><span class="sxs-lookup"><span data-stu-id="c786d-144">Code</span></span>  

 <span data-ttu-id="c786d-145">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c786d-145">The following code creates the client.</span></span> <span data-ttu-id="c786d-146">バインディングは、クライアントの資格情報の種類が Windows に設定された、TCP トランスポートによるトランスポート モード セキュリティを使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="c786d-146">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="c786d-147">構成</span><span class="sxs-lookup"><span data-stu-id="c786d-147">Configuration</span></span>  

 <span data-ttu-id="c786d-148">コードの代わりに次の構成を使用して、クライアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c786d-148">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c786d-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="c786d-149">See also</span></span>

- [<span data-ttu-id="c786d-150">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="c786d-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="c786d-151">方法: Windows 資格情報でサービスをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="c786d-151">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="c786d-152">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c786d-152">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
