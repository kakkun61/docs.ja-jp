---
title: クライアント構成
description: WCF クライアント構成を使用して、サービスへの接続に使用されるエンドポイントのアドレス、バインディング、動作、およびコントラクトを指定する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 5da5bd3b-65d9-43b7-91b9-cc9e989b1350
ms.openlocfilehash: af9101be0067311fb1a3c0e6e575f186e8ccf161
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265974"
---
# <a name="client-configuration"></a><span data-ttu-id="0ad1f-103">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="0ad1f-103">Client Configuration</span></span>

<span data-ttu-id="0ad1f-104">Windows Communication Foundation (WCF) クライアント構成を使用して、クライアントエンドポイントの "ABC" プロパティであるアドレス、バインド、動作、およびコントラクトを指定できます。このプロパティは、クライアントがサービスエンドポイントに接続するために使用します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-104">You can use the Windows Communication Foundation (WCF) client configuration to specify the address, binding, behavior, and contract, the "ABC" properties of the client endpoint, which clients use to connect to service endpoints.</span></span> <span data-ttu-id="0ad1f-105">[\<client>](../../configure-apps/file-schema/wcf/client.md)要素には、 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) エンドポイント abcs を構成するために使用される属性を持つ要素があります。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-105">The [\<client>](../../configure-apps/file-schema/wcf/client.md) element has an [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element whose attributes are used to configure the endpoint ABCs.</span></span> <span data-ttu-id="0ad1f-106">これらの属性については、「 [エンドポイントの構成](#configuring-endpoints) 」セクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-106">These attributes are discussed in the [Configuring Endpoints](#configuring-endpoints) section.</span></span>  
  
 <span data-ttu-id="0ad1f-107">要素には、 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) メタデータのインポートとエクスポートの設定を指定するために使用される要素、 [\<headers>](../../configure-apps/file-schema/wcf/headers.md) カスタムアドレスヘッダーのコレクションを格納する要素、および [\<identity>](../../configure-apps/file-schema/wcf/identity.md) メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする要素も含まれます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-107">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element also contains a [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element that is used to specify settings for importing and exporting metadata, a [\<headers>](../../configure-apps/file-schema/wcf/headers.md) element that contains a collection of custom address headers, and an [\<identity>](../../configure-apps/file-schema/wcf/identity.md) element that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span> <span data-ttu-id="0ad1f-108">[\<headers>](../../configure-apps/file-schema/wcf/headers.md)要素と [\<identity>](../../configure-apps/file-schema/wcf/identity.md) 要素は、の一部 <xref:System.ServiceModel.EndpointAddress> であり、[アドレス](endpoint-addresses.md)に関する記事で説明されています。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-108">The [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are discussed in the [Addresses](endpoint-addresses.md) article.</span></span> <span data-ttu-id="0ad1f-109">メタデータ拡張機能の使用方法について説明するトピックへのリンクについては、「 [メタデータの構成](#configuring-metadata) 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-109">Links to topics that explain the use of metadata extensions are provided in the [Configuring Metadata](#configuring-metadata) section.</span></span>  
  
## <a name="configuring-endpoints"></a><span data-ttu-id="0ad1f-110">エンドポイントの構成</span><span class="sxs-lookup"><span data-stu-id="0ad1f-110">Configuring Endpoints</span></span>  

 <span data-ttu-id="0ad1f-111">クライアント構成は、クライアントが1つまたは複数のエンドポイントを指定できるように設計されています。各エンドポイントには、それぞれ独自の名前、アドレス、およびコントラクトがあり、各エンドポイントは、 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) そのエンドポイントを構成するために使用されるクライアント構成の要素と要素を参照します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-111">The client configuration is designed to allow the client to specify one or more endpoints, each with its own name, address, and contract, with each referencing the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) and [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) elements in the client configuration to be used to configure that endpoint.</span></span> <span data-ttu-id="0ad1f-112">クライアント構成ファイルは、WCF ランタイムが想定している名前であるため、"App.config" という名前にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-112">The client configuration file should be named "App.config" because this is the name that the WCF runtime expects.</span></span> <span data-ttu-id="0ad1f-113">クライアント構成ファイルの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-113">The following example shows a client configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
        <client>  
          <endpoint  
            name="endpoint1"  
            address="http://localhost/ServiceModelSamples/service.svc"  
            binding="wsHttpBinding"  
            bindingConfiguration="WSHttpBinding_IHello"  
            behaviorConfiguration="IHello_Behavior"  
            contract="IHello" >  
  
            <metadata>  
              <wsdlImporters>  
                <extension  
                  type="Microsoft.ServiceModel.Samples.WsdlDocumentationImporter, WsdlDocumentation"/>  
              </wsdlImporters>  
            </metadata>  
  
            <identity>  
              <servicePrincipalName value="host/localhost" />  
            </identity>  
          </endpoint>  
            <!-- Add another endpoint by adding another <endpoint> element. -->
          <endpoint  
            name="endpoint2">  
           //Configure another endpoint here.  
          </endpoint>  
        </client>  
  
//The bindings section references by the bindingConfiguration endpoint attribute.  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_IHello"
                 bypassProxyOnLocal="false"
                 hostNameComparisonMode="StrongWildcard">  
          <readerQuotas maxDepth="32"/>  
          <reliableSession ordered="true"
                           enabled="false" />  
          <security mode="Message">  
           //Security settings go here.  
          </security>  
        </binding>  
        <binding name="Another Binding"  
          <!-- Configure this binding here. -->  
        </binding>  
          </wsHttpBinding>  
     </bindings>  
  
//The behavior section references by the behaviorConfiguration endpoint attribute.  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name=" IHello_Behavior ">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0ad1f-114">省略可能な `name` 属性は、特定のコントラクトのエンドポイントを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-114">The optional `name` attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="0ad1f-115">この属性は、サービスへのチャネルの作成時に、クライアント構成のどのエンドポイントをターゲットとし、読み込む必要があるかを指定するために、<xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> または <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> が使用します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-115">It is used by the <xref:System.ServiceModel.ChannelFactory%601.%23ctor%2A> or by the <xref:System.ServiceModel.ClientBase%601.%23ctor%2A> to specify which endpoint in the client configuration is being targeted and must be loaded when a channel is created to service.</span></span> <span data-ttu-id="0ad1f-116">ワイルドカードエンドポイント構成名 " \* " を使用できます。また、 <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> 使用可能なエンドポイントが1つある場合は、その構成をファイルに読み込む必要があることをメソッドに示します。それ以外の場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-116">A wildcard endpoint configuration name "\*" is available and indicates to the <xref:System.ServiceModel.ChannelFactory.ApplyConfiguration%2A> method that it should load any endpoint configuration in the file, provided there is precisely one available, and otherwise throws an exception.</span></span> <span data-ttu-id="0ad1f-117">この属性が省略されている場合、指定されたコントラクトの種類に関連する既定のエンドポイントとして、対応するエンドポイントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-117">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified contract type.</span></span> <span data-ttu-id="0ad1f-118">`name` 属性の既定値は、他の名前と同様に一致する空の文字列です。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-118">The default value for the `name` attribute is an empty string which is matched like any other name.</span></span>  
  
 <span data-ttu-id="0ad1f-119">すべてのエンドポイントには、エンドポイントを検索および識別するために、アドレスが関連付けられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-119">Every endpoint must have an address associated with it to locate and identify the endpoint.</span></span> <span data-ttu-id="0ad1f-120">`address` 属性は、エンドポイントの場所を示す URL を指定するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-120">The `address` attribute can be used to specify the URL that provides the location of the endpoint.</span></span> <span data-ttu-id="0ad1f-121">ただし、サービス エンドポイントのアドレスは、コードで指定することもできます。その場合は、URI (Uniform Resource Identifier) を作成し、<xref:System.ServiceModel.ServiceHost> メソッドのいずれかを使用して、この URI を <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-121">But the address for a service endpoint can also be specified in code by creating a Uniform Resource Identifier (URI) and is added to the <xref:System.ServiceModel.ServiceHost> using one of the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> methods.</span></span> <span data-ttu-id="0ad1f-122">詳細については、「 [アドレス](endpoint-addresses.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-122">For more information, see [Addresses](endpoint-addresses.md).</span></span> <span data-ttu-id="0ad1f-123">概要を示すように、 [\<headers>](../../configure-apps/file-schema/wcf/headers.md) 要素と要素はの一部であり、 [\<identity>](../../configure-apps/file-schema/wcf/identity.md) <xref:System.ServiceModel.EndpointAddress> 「 [アドレス](endpoint-addresses.md) 」のトピックでも説明されています。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-123">As the introduction indicates, the [\<headers>](../../configure-apps/file-schema/wcf/headers.md) and [\<identity>](../../configure-apps/file-schema/wcf/identity.md) elements are part of the <xref:System.ServiceModel.EndpointAddress> and are also discussed in the [Addresses](endpoint-addresses.md) topic.</span></span>  
  
 <span data-ttu-id="0ad1f-124">`binding` 属性は、エンドポイントがサービスに接続する際に使用するバインディングの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-124">The `binding` attribute indicates the type of binding the endpoint expects to use when connecting to a service.</span></span> <span data-ttu-id="0ad1f-125">参照できるようにするには、種類は登録された構成セクションを持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-125">The type must have a registered configuration section if it is to be referenced.</span></span> <span data-ttu-id="0ad1f-126">前の例では、これがセクションです。これは、 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) エンドポイントがを使用することを示し <xref:System.ServiceModel.WSHttpBinding> ます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-126">In the previous example, this is the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) section, which indicates that the endpoint uses a <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="0ad1f-127">ただし、エンドポイントが使用できる、指定された種類のバインディングが複数存在することもあります。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-127">But there may be more than one binding of a given type that the endpoint can use.</span></span> <span data-ttu-id="0ad1f-128">これらのそれぞれには [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) 、(binding) type 要素内に独自の要素があります。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-128">Each of these has its own [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element within the (binding) type element.</span></span> <span data-ttu-id="0ad1f-129">`bindingconfiguration` 属性は、同じ種類のバインディングを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-129">The `bindingconfiguration` attribute is used to distinguish between bindings of the same type.</span></span> <span data-ttu-id="0ad1f-130">この値は、 `name` 要素の属性と一致 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-130">Its value is matched with the `name` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span> <span data-ttu-id="0ad1f-131">構成を使用してクライアントバインディングを構成する方法の詳細については、「 [方法: 構成でクライアントバインディングを指定](../how-to-specify-a-client-binding-in-configuration.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-131">For more information about how to configure a client binding using configuration, see [How to: Specify a Client Binding in Configuration](../how-to-specify-a-client-binding-in-configuration.md).</span></span>  
  
 <span data-ttu-id="0ad1f-132">`behaviorConfiguration`属性は、 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) エンドポイントで使用するを指定するために使用され [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) ます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-132">The `behaviorConfiguration` attribute is used to specify which [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) of the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) the endpoint should use.</span></span> <span data-ttu-id="0ad1f-133">この値は、 `name` 要素の属性と一致 [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-133">Its value is matched with the `name` attribute of the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element.</span></span> <span data-ttu-id="0ad1f-134">構成を使用してクライアントの動作を指定する例については、「 [クライアントの動作の構成](../configuring-client-behaviors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-134">For an example of using configuration to specify client behaviors, see [Configuring Client Behaviors](../configuring-client-behaviors.md).</span></span>  
  
 <span data-ttu-id="0ad1f-135">`contract` 属性は、エンドポイントが公開するコントラクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-135">The `contract` attribute specifies which contract the endpoint is exposing.</span></span> <span data-ttu-id="0ad1f-136">この値は、<xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> の <xref:System.ServiceModel.ServiceContractAttribute> にマップされます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-136">This value maps to the <xref:System.ServiceModel.ServiceContractAttribute.ConfigurationName%2A> of the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span> <span data-ttu-id="0ad1f-137">既定値は、サービスを実装するクラスの完全な型名です。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-137">The default value is the full type name of the class that implements the service.</span></span>  
  
### <a name="configuring-metadata"></a><span data-ttu-id="0ad1f-138">メタデータの構成</span><span class="sxs-lookup"><span data-stu-id="0ad1f-138">Configuring Metadata</span></span>  

 <span data-ttu-id="0ad1f-139">[\<metadata>](../../configure-apps/file-schema/wcf/metadata.md)要素は、メタデータのインポート拡張を登録するために使用される設定を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-139">The [\<metadata>](../../configure-apps/file-schema/wcf/metadata.md) element is used to specify settings used to register metadata import extensions.</span></span> <span data-ttu-id="0ad1f-140">メタデータシステムの拡張の詳細については、「 [メタデータシステムの拡張](../extending/extending-the-metadata-system.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ad1f-140">For more information about extending the metadata system, see [Extending the Metadata System](../extending/extending-the-metadata-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad1f-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ad1f-141">See also</span></span>

- [<span data-ttu-id="0ad1f-142">エンドポイント:アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="0ad1f-142">Endpoints: Addresses, Bindings, and Contracts</span></span>](endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="0ad1f-143">クライアントの動作の構成</span><span class="sxs-lookup"><span data-stu-id="0ad1f-143">Configuring Client Behaviors</span></span>](../configuring-client-behaviors.md)
