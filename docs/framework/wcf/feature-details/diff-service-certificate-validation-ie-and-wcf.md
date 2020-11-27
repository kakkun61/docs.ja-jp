---
title: Internet Explorer と WCF で実行されるサービス証明書の検証の相違点
ms.date: 03/30/2017
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
ms.openlocfilehash: 574a6fa5411bcb662514982923e5c51200f98ae2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272203"
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="64e53-102">Internet Explorer と WCF で実行されるサービス証明書の検証の相違点</span><span class="sxs-lookup"><span data-stu-id="64e53-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>

<span data-ttu-id="64e53-103">HTTPS の使用時に Internet Explorer と Windows Communication Foundation (WCF) がサービス証明書を検証する方法が異なるため、WCF クライアントがサービスエンドポイントにメッセージを正常に送信できる場合でも、Internet Explorer がサービスのヘルプページまたは Web サービス記述言語 (WSDL) にアクセスできない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64e53-103">Because of difference between the way Internet Explorer and Windows Communication Foundation (WCF) validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a WCF client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="64e53-104">これは、Internet Explorer によって、サービス証明書の `ServerAuthentication` 拡張使用フラグにオブジェクト識別子 (OID) があるかどうかが確認されるのに対し、WCF ではこのような制約は適用されないためです。</span><span class="sxs-lookup"><span data-stu-id="64e53-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas WCF does not enforce such a constraint.</span></span> <span data-ttu-id="64e53-105">サービスのサービスヘルプページまたは WSDL にアクセスできない場合は、 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) を使用してサービスメタデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="64e53-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e53-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="64e53-106">See also</span></span>

- [<span data-ttu-id="64e53-107">HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点</span><span class="sxs-lookup"><span data-stu-id="64e53-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](cert-val-diff-https-ssl-over-tcp-and-soap.md)
- [<span data-ttu-id="64e53-108">方法: メタデータの取得および準拠サービスの実装をする</span><span class="sxs-lookup"><span data-stu-id="64e53-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](how-to-retrieve-metadata-and-implement-a-compliant-service.md)
