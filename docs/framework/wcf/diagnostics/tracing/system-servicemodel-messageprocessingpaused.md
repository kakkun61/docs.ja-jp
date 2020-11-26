---
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: e4c8040d2350e3824b5d68dc6f32376007792a7f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235117"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="4f645-102">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="4f645-102">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="4f645-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="4f645-103">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="4f645-104">Description</span><span class="sxs-lookup"><span data-stu-id="4f645-104">Description</span></span>  

 <span data-ttu-id="4f645-105">メッセージの処理中にスレッドが切り替わりました。</span><span class="sxs-lookup"><span data-stu-id="4f645-105">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="4f645-106">メッセージ処理は、次の理由によって一時停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="4f645-106">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="4f645-107">ConcurrencyMode が単一または再入可能で、サービスが別のメッセージを処理している。</span><span class="sxs-lookup"><span data-stu-id="4f645-107">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="4f645-108">トランザクションが有効で、サービスが別のトランザクションを処理している。</span><span class="sxs-lookup"><span data-stu-id="4f645-108">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="4f645-109">同期コンテキストが最新ではない。</span><span class="sxs-lookup"><span data-stu-id="4f645-109">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f645-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f645-110">See also</span></span>

- [<span data-ttu-id="4f645-111">トレース</span><span class="sxs-lookup"><span data-stu-id="4f645-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="4f645-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="4f645-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4f645-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="4f645-113">Administration and Diagnostics</span></span>](../index.md)
