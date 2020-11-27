---
title: 基本認証でのトランスポート セキュリティ
description: WCF サービスとクライアントの基本認証を示すこの WCF シナリオを確認します。 サービスには、クライアントが信頼する有効な証明書が必要です。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: e821f8ed3996e9119c6f2c06ec6533c575bf75dd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251842"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="66031-104">基本認証でのトランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="66031-104">Transport Security with Basic Authentication</span></span>

<span data-ttu-id="66031-105">次の図は、Windows Communication Foundation (WCF) サービスとクライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="66031-105">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="66031-106">サーバーには、SSL (Secure Sockets Layer) に使用できる有効な X509 証明書が必要であり、クライアントはサーバーの証明書を信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66031-106">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="66031-107">さらに、Web サービスには使用可能な SSL が既に実装されています。</span><span class="sxs-lookup"><span data-stu-id="66031-107">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="66031-108">インターネットインフォメーションサービス (IIS) で基本認証を有効にする方法の詳細については、「」を参照してください <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> 。</span><span class="sxs-lookup"><span data-stu-id="66031-108">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![基本認証を使用したトランスポートセキュリティを示すスクリーンショット。](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="66031-110">特徴</span><span class="sxs-lookup"><span data-stu-id="66031-110">Characteristic</span></span>|<span data-ttu-id="66031-111">説明</span><span class="sxs-lookup"><span data-stu-id="66031-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="66031-112">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="66031-112">Security Mode</span></span>|<span data-ttu-id="66031-113">トランスポート</span><span class="sxs-lookup"><span data-stu-id="66031-113">Transport</span></span>|  
|<span data-ttu-id="66031-114">相互運用性</span><span class="sxs-lookup"><span data-stu-id="66031-114">Interoperability</span></span>|<span data-ttu-id="66031-115">既存の Web サービス クライアントとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="66031-115">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="66031-116">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="66031-116">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="66031-117">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="66031-117">Authentication (Client)</span></span>|<span data-ttu-id="66031-118">○ (HTTPS を使用)</span><span class="sxs-lookup"><span data-stu-id="66031-118">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="66031-119">○ (ユーザー名とパスワードを使用)</span><span class="sxs-lookup"><span data-stu-id="66031-119">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="66031-120">整合性</span><span class="sxs-lookup"><span data-stu-id="66031-120">Integrity</span></span>|<span data-ttu-id="66031-121">はい</span><span class="sxs-lookup"><span data-stu-id="66031-121">Yes</span></span>|  
|<span data-ttu-id="66031-122">機密情報</span><span class="sxs-lookup"><span data-stu-id="66031-122">Confidentiality</span></span>|<span data-ttu-id="66031-123">はい</span><span class="sxs-lookup"><span data-stu-id="66031-123">Yes</span></span>|  
|<span data-ttu-id="66031-124">トランスポート</span><span class="sxs-lookup"><span data-stu-id="66031-124">Transport</span></span>|<span data-ttu-id="66031-125">HTTPS</span><span class="sxs-lookup"><span data-stu-id="66031-125">HTTPS</span></span>|  
|<span data-ttu-id="66031-126">バインド</span><span class="sxs-lookup"><span data-stu-id="66031-126">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="66031-127">サービス</span><span class="sxs-lookup"><span data-stu-id="66031-127">Service</span></span>  

 <span data-ttu-id="66031-128">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="66031-128">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="66031-129">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="66031-129">Do one of the following:</span></span>  
  
- <span data-ttu-id="66031-130">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="66031-130">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="66031-131">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="66031-131">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="66031-132">コード</span><span class="sxs-lookup"><span data-stu-id="66031-132">Code</span></span>  

 <span data-ttu-id="66031-133">次のコードでは、転送セキュリティ用の Windows ドメイン ユーザー名とパスワードを使用するサービス エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="66031-133">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="66031-134">サービスには、クライアントに対する認証を行うための X 509 証明書が必要になります。</span><span class="sxs-lookup"><span data-stu-id="66031-134">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="66031-135">詳細については、「 [証明書の](working-with-certificates.md) 使用」および「 [方法: SSL 証明書を使用してポートを構成する](how-to-configure-a-port-with-an-ssl-certificate.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66031-135">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="66031-136">構成</span><span class="sxs-lookup"><span data-stu-id="66031-136">Configuration</span></span>  

 <span data-ttu-id="66031-137">次の例では、トランスポート レベルのセキュリティの基本認証を使用するサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="66031-137">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="66031-138">クライアント</span><span class="sxs-lookup"><span data-stu-id="66031-138">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="66031-139">コード</span><span class="sxs-lookup"><span data-stu-id="66031-139">Code</span></span>  

 <span data-ttu-id="66031-140">次のコードは、ユーザー名とパスワードが含まれるクライアント コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="66031-140">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="66031-141">ユーザーは、有効な Windows ユーザー名とパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66031-141">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="66031-142">ユーザー名とパスワードを返すコードは、ここに示されていません。</span><span class="sxs-lookup"><span data-stu-id="66031-142">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="66031-143">ダイアログボックスまたは他のインターフェースを使用して、ユーザーにこれらの情報を照会してください。</span><span class="sxs-lookup"><span data-stu-id="66031-143">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66031-144">ユーザー名とパスワードは、コードを使ってのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="66031-144">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="66031-145">構成</span><span class="sxs-lookup"><span data-stu-id="66031-145">Configuration</span></span>  

 <span data-ttu-id="66031-146">次のコードは、クライアントの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="66031-146">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66031-147">構成を使用してユーザー名とパスワードを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="66031-147">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="66031-148">ここに示した構成には、ユーザー名とパスワードを設定するためのコードを補う必要があります。</span><span class="sxs-lookup"><span data-stu-id="66031-148">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="66031-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="66031-149">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="66031-150">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="66031-150">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="66031-151">方法: SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="66031-151">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="66031-152">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="66031-152">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="66031-153">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="66031-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
