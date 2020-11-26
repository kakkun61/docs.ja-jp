---
title: HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点
description: HTTPS または TCP に加えて WCF が提供するメッセージ層 (SOAP) セキュリティを使用した証明書と、そのような証明書を WCF で検証する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
ms.openlocfilehash: 9be640f892fd1fcc21711114415902335f9031bd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244849"
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="44258-103">HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点</span><span class="sxs-lookup"><span data-stu-id="44258-103">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>

<span data-ttu-id="44258-104">Windows Communication Foundation (WCF) の証明書は、トランスポート層セキュリティ (TLS) over HTTP (HTTPS) または TCP に加えて、メッセージ層 (SOAP) セキュリティと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="44258-104">You can use certificates in Windows Communication Foundation (WCF) with message-layer (SOAP) security in addition to transport-layer security (TLS) over HTTP (HTTPS) or TCP.</span></span> <span data-ttu-id="44258-105">ここでは、このような証明書の検証方法の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="44258-105">This topic describes differences in the way such certificates are validated.</span></span>  
  
## <a name="validation-of-https-client-certificates"></a><span data-ttu-id="44258-106">HTTPS クライアント証明書の検証</span><span class="sxs-lookup"><span data-stu-id="44258-106">Validation of HTTPS Client Certificates</span></span>  

 <span data-ttu-id="44258-107">HTTPS を使用してクライアントとサービス間で通信を行う場合、サービスに対して認証を行うためにクライアントが使用する証明書はチェーン信頼をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="44258-107">When using HTTPS to communicate between a client and a service, the certificate that the client uses to authenticate to the service must support chain trust.</span></span> <span data-ttu-id="44258-108">つまり、信頼されたルート証明機関にチェーンされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="44258-108">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="44258-109">それ以外の場合は、HTTP 層によってが発生し、 <xref:System.Net.WebException> "リモートサーバーがエラーを返しました: (403) 許可されていません" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="44258-109">If not, the HTTP layer raises a <xref:System.Net.WebException> with the message "The remote server returned an error: (403) Forbidden."</span></span> <span data-ttu-id="44258-110">WCF は、この例外をとして公開 <xref:System.ServiceModel.Security.MessageSecurityException> します。</span><span class="sxs-lookup"><span data-stu-id="44258-110">WCF surfaces this exception as a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span>  
  
## <a name="validation-of-https-service-certificates"></a><span data-ttu-id="44258-111">HTTP サービス証明書の検証</span><span class="sxs-lookup"><span data-stu-id="44258-111">Validation of HTTPS Service Certificates</span></span>  

 <span data-ttu-id="44258-112">HTTPS を使用してクライアントとサービス間で通信を行う場合、サーバーが認証に使用する証明書は既定でチェーン信頼をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="44258-112">When using HTTPS to communicate between a client and a service, the certificate that the server authenticates with must support chain trust by default.</span></span> <span data-ttu-id="44258-113">つまり、信頼されたルート証明機関にチェーンされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="44258-113">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="44258-114">証明書が失効しているかどうかを確認するためのオンライン チェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="44258-114">No online check is performed to see whether the certificate has been revoked.</span></span> <span data-ttu-id="44258-115">この動作は、<xref:System.Net.Security.RemoteCertificateValidationCallback> コールバックを登録することによってオーバーライドできます。コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="44258-115">You can override this behavior by registering a <xref:System.Net.Security.RemoteCertificateValidationCallback> callback, as shown in the following code.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)]
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 <span data-ttu-id="44258-116">`ValidateServerCertificate` の署名は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="44258-116">where the signature for `ValidateServerCertificate` is as follows:</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 <span data-ttu-id="44258-117">`ValidateServerCertificate` を実装すると、サービス証明書を検証するために必要であるとクライアント アプリケーションの開発者が考える、すべてのチェックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="44258-117">Implementing `ValidateServerCertificate` can perform any checks that the client application developer deems necessary to validate the service certificate.</span></span>  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a><span data-ttu-id="44258-118">SSL over TCP または SOAP セキュリティにおけるクライアント証明書の検証</span><span class="sxs-lookup"><span data-stu-id="44258-118">Validation of Client Certificates in SSL over TCP or SOAP Security</span></span>  

 <span data-ttu-id="44258-119">SSL (Secure Sockets Layer) over TCP またはメッセージ (SOAP) セキュリティを使用する場合、クライアント証明書は <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> プロパティ値に従って検証されます。</span><span class="sxs-lookup"><span data-stu-id="44258-119">When using Secure Sockets Layer (SSL) over TCP or message (SOAP) security, client certificates are validated according to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="44258-120">プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="44258-120">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span> <span data-ttu-id="44258-121">失効チェックは <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> プロパティの値に応じて実行されます。</span><span class="sxs-lookup"><span data-stu-id="44258-121">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="44258-122">プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="44258-122">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="44258-123">SSL over TCP および SOAP セキュリティにおけるサービス証明書の検証</span><span class="sxs-lookup"><span data-stu-id="44258-123">Validation of Service Certificate in SSL over TCP and SOAP Security</span></span>  

 <span data-ttu-id="44258-124">SSL over TCP またはメッセージ (SOAP) セキュリティを使用する場合、サービス証明書は <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> プロパティ値に従って検証されます。</span><span class="sxs-lookup"><span data-stu-id="44258-124">When using SSL over TCP or (SOAP) message security, service certificates are validated according to the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="44258-125">プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="44258-125">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span>  
  
 <span data-ttu-id="44258-126">失効チェックは <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> プロパティの値に応じて実行されます。</span><span class="sxs-lookup"><span data-stu-id="44258-126">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="44258-127">プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="44258-127">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="44258-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="44258-128">See also</span></span>

- <xref:System.Net.Security.RemoteCertificateValidationCallback>
- [<span data-ttu-id="44258-129">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="44258-129">Working with Certificates</span></span>](working-with-certificates.md)
