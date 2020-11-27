---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 97f22a01df84c39915f74fa7677e5dd18154b952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256223"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="c8f74-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="c8f74-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>

<span data-ttu-id="c8f74-103">HTTP チャネルを介したメッセージの受信に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="c8f74-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8f74-104">Description</span><span class="sxs-lookup"><span data-stu-id="c8f74-104">Description</span></span>  

 <span data-ttu-id="c8f74-105">このトレースは、警告またはエラーとして出力されます。</span><span class="sxs-lookup"><span data-stu-id="c8f74-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="c8f74-106">どちらの場合であっても、このトレースは、受信 HTTP 要求に対して互換性のあるリスナーが見つからない場合に出力され、HTTP 要求は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="c8f74-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="c8f74-107">これは、要求の HTTP 動詞が HTTP リスナーによって認識されない、または要求が対象としているアドレスでリッスンしているリスナーがないために発生します。</span><span class="sxs-lookup"><span data-stu-id="c8f74-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="c8f74-108">このトレースは、自己ホスト型の場合は警告を出力し、サービスが IIS でホストされている場合はエラーを出力します。</span><span class="sxs-lookup"><span data-stu-id="c8f74-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8f74-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8f74-109">See also</span></span>

- [<span data-ttu-id="c8f74-110">トレース</span><span class="sxs-lookup"><span data-stu-id="c8f74-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="c8f74-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c8f74-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="c8f74-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="c8f74-112">Administration and Diagnostics</span></span>](../index.md)
