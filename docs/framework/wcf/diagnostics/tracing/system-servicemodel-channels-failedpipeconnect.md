---
title: System.ServiceModel.Channels.FailedPipeConnect
ms.date: 03/30/2017
ms.assetid: 9a827e0f-fb91-46bb-bd54-926d4b74d8a6
ms.openlocfilehash: b3b34b2f4ab2987360030d614c8e65cd878d4d14
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256249"
---
# <a name="systemservicemodelchannelsfailedpipeconnect"></a><span data-ttu-id="688f9-102">System.ServiceModel.Channels.FailedPipeConnect</span><span class="sxs-lookup"><span data-stu-id="688f9-102">System.ServiceModel.Channels.FailedPipeConnect</span></span>

<span data-ttu-id="688f9-103">名前付きパイプ エンドポイントに接続しようとして失敗しました。</span><span class="sxs-lookup"><span data-stu-id="688f9-103">An attempt to connect to the named pipe endpoint failed.</span></span> <span data-ttu-id="688f9-104">指定されたタイムアウト期間内に再試行します。</span><span class="sxs-lookup"><span data-stu-id="688f9-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="688f9-105">Description</span><span class="sxs-lookup"><span data-stu-id="688f9-105">Description</span></span>  

 <span data-ttu-id="688f9-106">この情報トレースは、名前付きパイプ エンドポイントへの接続に失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="688f9-106">This informational trace indicates a failure to connect to a named pipe endpoint.</span></span> <span data-ttu-id="688f9-107">これは、名前付きパイプ エンドポイントが見つからなかったか、ビジーであった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="688f9-107">This could happen if the named pipe endpoint is not found or is busy.</span></span> <span data-ttu-id="688f9-108">接続に成功するか、OpenTimeout の有効期間が切れるまで、短い間隔を置いて再試行が繰り返されます。</span><span class="sxs-lookup"><span data-stu-id="688f9-108">Additional attempts are made, each separated by a short amount of time, until one succeeds or the OpenTimeout expires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688f9-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="688f9-109">See also</span></span>

- [<span data-ttu-id="688f9-110">トレース</span><span class="sxs-lookup"><span data-stu-id="688f9-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="688f9-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="688f9-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="688f9-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="688f9-112">Administration and Diagnostics</span></span>](../index.md)
