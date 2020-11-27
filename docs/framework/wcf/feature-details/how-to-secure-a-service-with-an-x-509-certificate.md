---
title: '方法: X.509 証明書を使用してサービスをセキュリティで保護する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: bf498ee373f2d637a7a93fbc36225a38ff7744c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293898"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a><span data-ttu-id="b7e3b-102">方法: X.509 証明書を使用してサービスをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="b7e3b-102">How to: Secure a Service with an X.509 Certificate</span></span>

<span data-ttu-id="b7e3b-103">X.509 証明書を使用してサービスをセキュリティで保護することは、Windows Communication Foundation (WCF) のほとんどのバインディングで使用される基本的な手法です。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-103">Securing a service with an X.509 certificate is a basic technique that most bindings in Windows Communication Foundation (WCF) use.</span></span> <span data-ttu-id="b7e3b-104">ここでは、X.509 証明書を使用して自己ホスト サービスを構成する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-104">This topic walks through the steps of configuring a self-hosted service with an X.509 certificate.</span></span>  
  
 <span data-ttu-id="b7e3b-105">サーバーの認証に使用できる有効な証明書があることが前提条件になります。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-105">A prerequisite is a valid certificate that can be used to authenticate the server.</span></span> <span data-ttu-id="b7e3b-106">この証明書は、信頼された証明機関によってサーバーに対して発行される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-106">The certificate must be issued to the server by a trusted certificate authority.</span></span> <span data-ttu-id="b7e3b-107">証明書が無効な場合、サービスの使用を試みるすべてのクライアントがサービスを信頼しなくなるため、接続が作成されません。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-107">If the certificate is not valid, any client trying to use the service will not trust the service, and consequently no connection will be made.</span></span> <span data-ttu-id="b7e3b-108">証明書の使用方法の詳細については、「 [証明書の](working-with-certificates.md)使用」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-108">For more information about using certificates, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a><span data-ttu-id="b7e3b-109">コードにより証明書を使用してサービスを構成するには</span><span class="sxs-lookup"><span data-stu-id="b7e3b-109">To configure a service with a certificate using code</span></span>  
  
1. <span data-ttu-id="b7e3b-110">サービス コントラクトを作成し、サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-110">Create the service contract and the implemented service.</span></span> <span data-ttu-id="b7e3b-111">詳細については、「 [サービスの設計と実装](../designing-and-implementing-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-111">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md).</span></span>  
  
2. <span data-ttu-id="b7e3b-112">次のコードに示すように、<xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、そのセキュリティ モードを <xref:System.ServiceModel.SecurityMode.Message> に設定します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-112">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. <span data-ttu-id="b7e3b-113">次のコードに示すように、2 つの <xref:System.Type> 変数を作成し、それぞれコントラクト型と実装されたコントラクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-113">Create two <xref:System.Type> variables, one each for the contract type and the implemented contract, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. <span data-ttu-id="b7e3b-114">サービスのベース アドレス用に <xref:System.Uri> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-114">Create an instance of the <xref:System.Uri> class for the base address of the service.</span></span> <span data-ttu-id="b7e3b-115">は `WSHttpBinding` HTTP トランスポートを使用するため、Uniform Resource Identifier (URI) はそのスキーマで始まる必要があります。または、サービスを開いたときに Windows Communication Foundation (WCF) によって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-115">Because the `WSHttpBinding` uses the HTTP transport, the Uniform Resource Identifier (URI) must begin with that schema, or Windows Communication Foundation (WCF) will throw an exception when the service is opened.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. <span data-ttu-id="b7e3b-116">実装したコントラクト型変数と URI を使用して <xref:System.ServiceModel.ServiceHost> クラスの新しいインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-116">Create a new instance of the <xref:System.ServiceModel.ServiceHost> class with the implemented contract type variable and the URI.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. <span data-ttu-id="b7e3b-117"><xref:System.ServiceModel.Description.ServiceEndpoint> メソッドを使用して、サービスに <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> を追加します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-117">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> to the service using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span> <span data-ttu-id="b7e3b-118">次のコードに示すように、コントラクト、バインディング、およびエンドポイント アドレスをコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-118">Pass the contract, binding, and an endpoint address to the constructor, as shown in the following code.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. <span data-ttu-id="b7e3b-119">任意。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-119">Optional.</span></span> <span data-ttu-id="b7e3b-120">サービスからメタデータを取得するには、新しい <xref:System.ServiceModel.Description.ServiceMetadataBehavior> オブジェクトを作成し、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-120">To retrieve metadata from the service, create a new <xref:System.ServiceModel.Description.ServiceMetadataBehavior> object and set the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. <span data-ttu-id="b7e3b-121"><xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> メソッドを使用して、有効な証明書をサービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-121">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to add the valid certificate to the service.</span></span> <span data-ttu-id="b7e3b-122">このメソッドでは、いくつかある方法の 1 つを使用して証明書を見つけます。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-122">The method can use one of several methods to find a certificate.</span></span> <span data-ttu-id="b7e3b-123">この例では、<xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> 列挙体を使用します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-123">This example uses the <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> enumeration.</span></span> <span data-ttu-id="b7e3b-124">この列挙体では、提供された値が証明書の発行先のエンティティの名前であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-124">The enumeration specifies that the supplied value is the name of the entity that the certificate was issued to.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. <span data-ttu-id="b7e3b-125"><xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> メソッドを呼び出して、サービスのリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-125">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service listening.</span></span> <span data-ttu-id="b7e3b-126">コンソール アプリケーションを作成する場合は、<xref:System.Console.ReadLine%2A> メソッドを呼び出して、サービスをリッスン状態に保持します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-126">If you are creating a console application, call the <xref:System.Console.ReadLine%2A> method to keep the service in the listening state.</span></span>  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="b7e3b-127">例</span><span class="sxs-lookup"><span data-stu-id="b7e3b-127">Example</span></span>  

 <span data-ttu-id="b7e3b-128">次の例では、<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> メソッドを使用して、X.509 証明書でサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-128">The following example uses the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method to configure a service with an X.509 certificate.</span></span>  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b7e3b-129">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b7e3b-129">Compiling the Code</span></span>  

 <span data-ttu-id="b7e3b-130">コードのコンパイルには次の名前空間が必要です。</span><span class="sxs-lookup"><span data-stu-id="b7e3b-130">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a><span data-ttu-id="b7e3b-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7e3b-131">See also</span></span>

- [<span data-ttu-id="b7e3b-132">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="b7e3b-132">Working with Certificates</span></span>](working-with-certificates.md)
