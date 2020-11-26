---
title: メッセージ セキュリティと相互の証明書
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: 521b2a887792d41dd28342ca4bfe7be71ceba4b7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237379"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="7006a-102">メッセージ セキュリティと相互の証明書</span><span class="sxs-lookup"><span data-stu-id="7006a-102">Message Security with Mutual Certificates</span></span>

<span data-ttu-id="7006a-103">次のシナリオは、メッセージセキュリティモードを使用してセキュリティで保護された Windows Communication Foundation (WCF) サービスとクライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="7006a-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="7006a-104">クライアントとサービスは、証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="7006a-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="7006a-105">このシナリオは、X.509 証明書トークン プロファイルと共に WS-Security を使用するため、相互運用性があります。</span><span class="sxs-lookup"><span data-stu-id="7006a-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7006a-106">このシナリオでは、サービス証明書のネゴシエーションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="7006a-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="7006a-107">通信を開始する前に、サービス証明書をクライアントに提供しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="7006a-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="7006a-108">サーバー証明書は、アプリケーションと共に配布したり、帯域外通信で提供できます。</span><span class="sxs-lookup"><span data-stu-id="7006a-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="7006a-109">![相互証明書を使用したメッセージセキュリティ](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="7006a-109">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="7006a-110">特徴</span><span class="sxs-lookup"><span data-stu-id="7006a-110">Characteristic</span></span>|<span data-ttu-id="7006a-111">説明</span><span class="sxs-lookup"><span data-stu-id="7006a-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7006a-112">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="7006a-112">Security Mode</span></span>|<span data-ttu-id="7006a-113">Message</span><span class="sxs-lookup"><span data-stu-id="7006a-113">Message</span></span>|  
|<span data-ttu-id="7006a-114">相互運用性</span><span class="sxs-lookup"><span data-stu-id="7006a-114">Interoperability</span></span>|<span data-ttu-id="7006a-115">○ WS-Security および X.509 証明書トークン プロファイルと互換性があるクライアントとサービスで相互運用性があります。</span><span class="sxs-lookup"><span data-stu-id="7006a-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="7006a-116">認証</span><span class="sxs-lookup"><span data-stu-id="7006a-116">Authentication</span></span>|<span data-ttu-id="7006a-117">サーバーとクライアントの相互認証</span><span class="sxs-lookup"><span data-stu-id="7006a-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="7006a-118">整合性</span><span class="sxs-lookup"><span data-stu-id="7006a-118">Integrity</span></span>|<span data-ttu-id="7006a-119">はい</span><span class="sxs-lookup"><span data-stu-id="7006a-119">Yes</span></span>|  
|<span data-ttu-id="7006a-120">機密情報</span><span class="sxs-lookup"><span data-stu-id="7006a-120">Confidentiality</span></span>|<span data-ttu-id="7006a-121">はい</span><span class="sxs-lookup"><span data-stu-id="7006a-121">Yes</span></span>|  
|<span data-ttu-id="7006a-122">トランスポート</span><span class="sxs-lookup"><span data-stu-id="7006a-122">Transport</span></span>|<span data-ttu-id="7006a-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="7006a-123">HTTP</span></span>|  
|<span data-ttu-id="7006a-124">バインド</span><span class="sxs-lookup"><span data-stu-id="7006a-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="7006a-125">サービス</span><span class="sxs-lookup"><span data-stu-id="7006a-125">Service</span></span>  

 <span data-ttu-id="7006a-126">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="7006a-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7006a-127">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7006a-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="7006a-128">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="7006a-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="7006a-129">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="7006a-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7006a-130">コード</span><span class="sxs-lookup"><span data-stu-id="7006a-130">Code</span></span>  

 <span data-ttu-id="7006a-131">次のコードでは、メッセージ セキュリティを使用するサービス エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7006a-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="7006a-132">サービスには、自身を認証するための証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="7006a-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="7006a-133">構成</span><span class="sxs-lookup"><span data-stu-id="7006a-133">Configuration</span></span>  

 <span data-ttu-id="7006a-134">コードの代わりに次の構成を使用して、同じサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7006a-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="7006a-135">クライアント</span><span class="sxs-lookup"><span data-stu-id="7006a-135">Client</span></span>  

 <span data-ttu-id="7006a-136">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="7006a-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7006a-137">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7006a-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="7006a-138">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7006a-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="7006a-139">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="7006a-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="7006a-140">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="7006a-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="7006a-141">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="7006a-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="7006a-142">コード</span><span class="sxs-lookup"><span data-stu-id="7006a-142">Code</span></span>  

 <span data-ttu-id="7006a-143">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7006a-143">The following code creates the client.</span></span> <span data-ttu-id="7006a-144">セキュリティ モードは Message に設定され、クライアント資格情報の種類は Certificate に設定されています。</span><span class="sxs-lookup"><span data-stu-id="7006a-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="7006a-145">構成</span><span class="sxs-lookup"><span data-stu-id="7006a-145">Configuration</span></span>  

 <span data-ttu-id="7006a-146">次のコードは、クライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="7006a-146">The following configures the client.</span></span> <span data-ttu-id="7006a-147">クライアント証明書は、を使用して指定する必要があり [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="7006a-147">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="7006a-148">また、サービス証明書はを使用して指定され [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="7006a-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7006a-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="7006a-149">See also</span></span>

- [<span data-ttu-id="7006a-150">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="7006a-150">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="7006a-151">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7006a-151">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="7006a-152">[方法: 開発時にトランスポートセキュリティのために WCF で一時的な証明書を作成およびインストールする](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="7006a-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
