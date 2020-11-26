---
title: '方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 0a03902c9a0d36ebd6e2c38f4a827737cacec447
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245033"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a><span data-ttu-id="d6a2f-102">方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)</span><span class="sxs-lookup"><span data-stu-id="d6a2f-102">How to: Specify the Certificate Authority Certificate Chain Used to Verify Signatures (WCF)</span></span>

<span data-ttu-id="d6a2f-103">Windows Communication Foundation (WCF) は、x.509 証明書を使用して署名された SOAP メッセージを受信すると、x.509 証明書が信頼された証明機関によって発行されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-103">When Windows Communication Foundation (WCF) receives a SOAP message signed using an X.509 certificate, by default it verifies that the X.509 certificate was issued by a trusted certification authority.</span></span> <span data-ttu-id="d6a2f-104">これは、証明書ストアを検索し、その証明機関の証明書が信頼された証明書として指定されているかどうかを確認することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-104">This is done by looking in a certificate store and determining if the certificate for that certification authority has been designated as trusted.</span></span> <span data-ttu-id="d6a2f-105">WCF がこの判断を行うためには、証明機関の証明書チェーンが正しい証明書ストアにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-105">In order for WCF to make this determination, the certification authority certificate chain must be installed in the correct certificate store.</span></span>  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a><span data-ttu-id="d6a2f-106">証明機関証明書チェーンをインストールするには</span><span class="sxs-lookup"><span data-stu-id="d6a2f-106">To install a certification authority certificate chain</span></span>  
  
- <span data-ttu-id="d6a2f-107">SOAP メッセージの受信者によって発行された x.509 証明書を信頼する証明機関ごとに、証明機関の証明書チェーンを、WCF が x.509 証明書を取得するように構成されている証明書ストアにインストールします。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-107">For each certification authority that a SOAP message recipient intends to trust X.509 certificates issued from, install the certification authority certificate chain into the certificate store that WCF is configured to retrieve X.509 certificates from.</span></span>  
  
     <span data-ttu-id="d6a2f-108">たとえば、SOAP メッセージの受信者が Microsoft によって発行された x.509 証明書を信頼する場合、WCF が x.509 証明書を検索するように設定されている証明書ストアに、Microsoft の証明機関証明書チェーンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-108">For instance, if a SOAP message recipient intends to trust X.509 certificates issued by Microsoft, the certification authority certificate chain for Microsoft must be installed in the certificate store that WCF is set up to look for X.509 certificates from.</span></span> <span data-ttu-id="d6a2f-109">WCF が x.509 証明書を検索する証明書ストアは、コードまたは構成で指定できます。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-109">The certificate store in which WCF looks for X.509 certificates can be specified in code or configuration.</span></span> <span data-ttu-id="d6a2f-110">たとえば、これは、メソッドを使用してコードで指定することも、を含むいくつかの方法で構成することもでき <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-110">For example, this can be specified in code using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method or in configuration a few ways, including the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span></span>  
  
     <span data-ttu-id="d6a2f-111">Windows には、信頼された証明機関の既定の証明書チェーンのセットが用意されているため、一部の CA については証明書チェーンをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-111">Because Windows ships with a set of default certificate chains for trusted certificate authorities, it may not be necessary to install the certificate chain for all certificate authorities.</span></span>  
  
    1. <span data-ttu-id="d6a2f-112">証明機関証明書チェーンをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-112">Export the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="d6a2f-113">正確なエクスポート方法は、証明機関によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-113">Exactly how this is done depends on the certification authority.</span></span> <span data-ttu-id="d6a2f-114">証明機関が Microsoft 証明書サービスを実行している場合は、[ **ca 証明書、証明書チェーン、または CRL をダウンロードする**] を選択し、[ **ca 証明書のダウンロード**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-114">If the certification authority is running Microsoft Certificate Services, select **Download a CA certificate, certificate chain, or CRL**, and then choose **Download CA certificate**.</span></span>  
  
    2. <span data-ttu-id="d6a2f-115">証明機関証明書チェーンをインポートします。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-115">Import the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="d6a2f-116">Microsoft 管理コンソール (MMC: Microsoft Management Console) で、証明書スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-116">In the Microsoft Management Console (MMC), open the Certificates snap-in.</span></span> <span data-ttu-id="d6a2f-117">WCF が x.509 証明書を取得するように構成されている証明書ストアについて、[**信頼されたルート\*\*\*\*証明機関**] フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-117">For the certificate store that WCF is configured to retrieve X.509 certificates from, select the **Trusted Root** **Certification Authorities** folder.</span></span> <span data-ttu-id="d6a2f-118">[ **信頼されたルート証明機関** ] フォルダーの下で、[ **証明書** ] フォルダーを右クリックし、[ **すべてのタスク**] をポイントして、[ **インポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-118">Under the **Trusted Root Certification Authorities** folder, right-click the **Certificates** folder, point to **All Tasks**, and then click **Import**.</span></span> <span data-ttu-id="d6a2f-119">手順 a. でエクスポートしたファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-119">Provide the file exported in step a.</span></span>  
  
         <span data-ttu-id="d6a2f-120">MMC で証明書スナップインを使用する方法の詳細については、「 [方法: Mmc スナップインを使用して証明書を表示する](how-to-view-certificates-with-the-mmc-snap-in.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6a2f-120">For more information about using the Certificates snap-in with MMC, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a2f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6a2f-121">See also</span></span>

- [<span data-ttu-id="d6a2f-122">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="d6a2f-122">Working with Certificates</span></span>](working-with-certificates.md)
