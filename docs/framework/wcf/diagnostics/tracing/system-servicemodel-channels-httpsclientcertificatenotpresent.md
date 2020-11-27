---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 9ec25138130311f8cdd9af8fb32a3e80fb33ed68
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258089"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="9f245-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="9f245-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>

<span data-ttu-id="9f245-103">クライアント証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="9f245-103">Client certificate is required.</span></span> <span data-ttu-id="9f245-104">要求内で証明書が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="9f245-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9f245-105">Description</span><span class="sxs-lookup"><span data-stu-id="9f245-105">Description</span></span>  

 <span data-ttu-id="9f245-106">このトレースは、HTTPS リスナーがクライアント証明書に関連付けられていない HTTPS 要求を受信したことを示します。</span><span class="sxs-lookup"><span data-stu-id="9f245-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="9f245-107">リスナーはすべての HTTPS 要求においてクライアント証明書を必要とするように構成されているため、リスナーによるクライアントの信頼性の検証は失敗します。</span><span class="sxs-lookup"><span data-stu-id="9f245-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f245-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="9f245-108">See also</span></span>

- [<span data-ttu-id="9f245-109">トレース</span><span class="sxs-lookup"><span data-stu-id="9f245-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="9f245-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="9f245-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9f245-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="9f245-111">Administration and Diagnostics</span></span>](../index.md)
