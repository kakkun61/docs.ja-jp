---
title: ユーザー名クライアントを使用したメッセージ セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: 7168b393bde626c8c413cda3c7422e0eee4ce267
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292871"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="1a293-102">ユーザー名クライアントを使用したメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="1a293-102">Message Security with a User Name Client</span></span>

<span data-ttu-id="1a293-103">次の図は、メッセージレベルのセキュリティを使用してセキュリティで保護された Windows Communication Foundation (WCF) サービスとクライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="1a293-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="1a293-104">サービスは X.509 証明書を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="1a293-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="1a293-105">クライアントはユーザー名とパスワードを使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="1a293-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="1a293-106">サンプルアプリケーションについては、「 [メッセージセキュリティユーザー名](../samples/message-security-user-name.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1a293-106">For a sample application, see [Message Security User Name](../samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="1a293-107">![ユーザー名認証を使用したメッセージ セキュリティ](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="1a293-107">![Message security using username authentication](media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="1a293-108">特徴</span><span class="sxs-lookup"><span data-stu-id="1a293-108">Characteristic</span></span>|<span data-ttu-id="1a293-109">説明</span><span class="sxs-lookup"><span data-stu-id="1a293-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1a293-110">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="1a293-110">Security Mode</span></span>|<span data-ttu-id="1a293-111">Message</span><span class="sxs-lookup"><span data-stu-id="1a293-111">Message</span></span>|  
|<span data-ttu-id="1a293-112">相互運用性</span><span class="sxs-lookup"><span data-stu-id="1a293-112">Interoperability</span></span>|<span data-ttu-id="1a293-113">Windows Communication Foundation (WCF) のみ</span><span class="sxs-lookup"><span data-stu-id="1a293-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="1a293-114">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="1a293-114">Authentication (Server)</span></span>|<span data-ttu-id="1a293-115">初期ネゴシエーションにはサーバー認証が必要</span><span class="sxs-lookup"><span data-stu-id="1a293-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="1a293-116">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="1a293-116">Authentication (Client)</span></span>|<span data-ttu-id="1a293-117">ユーザー名/パスワード</span><span class="sxs-lookup"><span data-stu-id="1a293-117">User name/password</span></span>|  
|<span data-ttu-id="1a293-118">整合性</span><span class="sxs-lookup"><span data-stu-id="1a293-118">Integrity</span></span>|<span data-ttu-id="1a293-119">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="1a293-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="1a293-120">機密情報</span><span class="sxs-lookup"><span data-stu-id="1a293-120">Confidentiality</span></span>|<span data-ttu-id="1a293-121">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="1a293-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="1a293-122">トランスポート</span><span class="sxs-lookup"><span data-stu-id="1a293-122">Transport</span></span>|<span data-ttu-id="1a293-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="1a293-123">HTTP</span></span>|  
|<span data-ttu-id="1a293-124">バインド</span><span class="sxs-lookup"><span data-stu-id="1a293-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="1a293-125">サービス</span><span class="sxs-lookup"><span data-stu-id="1a293-125">Service</span></span>  

 <span data-ttu-id="1a293-126">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="1a293-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="1a293-127">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="1a293-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="1a293-128">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1a293-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="1a293-129">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="1a293-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1a293-130">コード</span><span class="sxs-lookup"><span data-stu-id="1a293-130">Code</span></span>  

 <span data-ttu-id="1a293-131">次のコードは、メッセージ セキュリティを使用するサービス エンドポイントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1a293-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="1a293-132">構成</span><span class="sxs-lookup"><span data-stu-id="1a293-132">Configuration</span></span>  

 <span data-ttu-id="1a293-133">コードの代わりに次の構成を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1a293-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
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
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="1a293-134">クライアント</span><span class="sxs-lookup"><span data-stu-id="1a293-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="1a293-135">コード</span><span class="sxs-lookup"><span data-stu-id="1a293-135">Code</span></span>  

 <span data-ttu-id="1a293-136">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1a293-136">The following code creates the client.</span></span> <span data-ttu-id="1a293-137">バインディングではメッセージ モード セキュリティを使用し、クライアント資格情報の種類は `UserName` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1a293-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="1a293-138">ユーザー名とパスワードの指定はコードを使用する場合に限られます (構成可能ではありません)。</span><span class="sxs-lookup"><span data-stu-id="1a293-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="1a293-139">ユーザー名とパスワードを返すコードは、アプリケーション レベルで実行される必要があるため、ここには示しません。</span><span class="sxs-lookup"><span data-stu-id="1a293-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="1a293-140">たとえば、Windows フォーム ダイアログ ボックスを使用してユーザーにデータを照会します。</span><span class="sxs-lookup"><span data-stu-id="1a293-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="1a293-141">構成</span><span class="sxs-lookup"><span data-stu-id="1a293-141">Configuration</span></span>  

 <span data-ttu-id="1a293-142">クライアントを構成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1a293-142">The following code configures the client.</span></span> <span data-ttu-id="1a293-143">バインディングではメッセージ モード セキュリティを使用し、クライアント資格情報の種類は `UserName` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1a293-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="1a293-144">ユーザー名とパスワードの指定はコードを使用する場合に限られます (構成可能ではありません)。</span><span class="sxs-lookup"><span data-stu-id="1a293-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1a293-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a293-145">See also</span></span>

- [<span data-ttu-id="1a293-146">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="1a293-146">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="1a293-147">メッセージ セキュリティ ユーザー名</span><span class="sxs-lookup"><span data-stu-id="1a293-147">Message Security User Name</span></span>](../samples/message-security-user-name.md)
- [<span data-ttu-id="1a293-148">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="1a293-148">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [\<identity>](../../configure-apps/file-schema/wcf/identity.md)
- <span data-ttu-id="1a293-149">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="1a293-149">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
