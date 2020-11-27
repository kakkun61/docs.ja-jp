---
title: System.ServiceModel.Channels.HttpsClientCertificateInvalid
ms.date: 03/30/2017
ms.assetid: 8884dda1-fa0e-4d2a-8079-7042c51b64ef
ms.openlocfilehash: afacbb13f4b193083d22e025cb6e1e97194e1ee4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258115"
---
# <a name="systemservicemodelchannelshttpsclientcertificateinvalid"></a><span data-ttu-id="17306-102">System.ServiceModel.Channels.HttpsClientCertificateInvalid</span><span class="sxs-lookup"><span data-stu-id="17306-102">System.ServiceModel.Channels.HttpsClientCertificateInvalid</span></span>

<span data-ttu-id="17306-103">クライアント証明書が無効です。</span><span class="sxs-lookup"><span data-stu-id="17306-103">Client certificate is invalid.</span></span>  
  
## <a name="description"></a><span data-ttu-id="17306-104">Description</span><span class="sxs-lookup"><span data-stu-id="17306-104">Description</span></span>  

 <span data-ttu-id="17306-105">このトレースは、HTTPS リスナーが、クライアントによって提供された証明書が無効であることを検出したことを示します。</span><span class="sxs-lookup"><span data-stu-id="17306-105">This trace indicates that the certificate provided by the client was found to be invalid by the HTTPS listener.</span></span> <span data-ttu-id="17306-106">HTTPS リスナーは、この証明書を使用してクライアントの信頼性を検証しようとしていました。</span><span class="sxs-lookup"><span data-stu-id="17306-106">The HTTPS listener was attempting to validate the authenticity of the client using this certificate.</span></span> <span data-ttu-id="17306-107">サービスをホストしているサーバーによって証明書の証明機関が認識されないと、証明書は無効になります。</span><span class="sxs-lookup"><span data-stu-id="17306-107">A certificate could be invalid if its Certificate Authority is not recognized by the server hosting the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17306-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="17306-108">See also</span></span>

- [<span data-ttu-id="17306-109">トレース</span><span class="sxs-lookup"><span data-stu-id="17306-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="17306-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="17306-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="17306-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="17306-111">Administration and Diagnostics</span></span>](../index.md)
