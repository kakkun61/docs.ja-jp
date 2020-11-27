---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.date: 03/30/2017
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
ms.openlocfilehash: 6e8b134f61d2dc9bd5daf541db4ec81604166baa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260384"
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a><span data-ttu-id="2f472-102">System.ServiceModel.Channels.MsmqMessageDropped</span><span class="sxs-lookup"><span data-stu-id="2f472-102">System.ServiceModel.Channels.MsmqMessageDropped</span></span>

<span data-ttu-id="2f472-103">MSMQ はメッセージを破棄しました。</span><span class="sxs-lookup"><span data-stu-id="2f472-103">MSMQ dropped the message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2f472-104">Description</span><span class="sxs-lookup"><span data-stu-id="2f472-104">Description</span></span>  

 <span data-ttu-id="2f472-105">このトレースは、MSMQ メッセージが破棄されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="2f472-105">The trace indicates that an MSMQ message was dropped.</span></span> <span data-ttu-id="2f472-106">MSMQ メッセージは Windows Communication Foundation (WCF) (NetMsmqBinding または MsmqIntegrationBinding で使用) が処理できない場合に削除できます。</span><span class="sxs-lookup"><span data-stu-id="2f472-106">MSMQ messages can be dropped when Windows Communication Foundation (WCF) (used with either the NetMsmqBinding or MsmqIntegrationBinding) is unable to process them.</span></span> <span data-ttu-id="2f472-107">このようなメッセージは、有害メッセージと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2f472-107">Such messages are referred to as poison messages.</span></span>  
  
 <span data-ttu-id="2f472-108">有害メッセージは、NetMsmqBinding または MsmqIntegrationBinding の `ReceiveErrorHandling` プロパティが `Drop` に設定されていると破棄されます。</span><span class="sxs-lookup"><span data-stu-id="2f472-108">A poison message is dropped when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Drop`.</span></span> <span data-ttu-id="2f472-109">破棄されたメッセージはキューから削除され、元に戻すことはできません。</span><span class="sxs-lookup"><span data-stu-id="2f472-109">A dropped message is removed from the queue and is no longer recoverable.</span></span>  
  
 <span data-ttu-id="2f472-110">メッセージが有害になった場合の詳細、およびメッセージを適切に処理するようにサービスを構成する方法については、「 [有害メッセージの処理](../../feature-details/poison-message-handling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f472-110">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f472-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f472-111">See also</span></span>

- [<span data-ttu-id="2f472-112">トレース</span><span class="sxs-lookup"><span data-stu-id="2f472-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="2f472-113">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2f472-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2f472-114">管理と診断</span><span class="sxs-lookup"><span data-stu-id="2f472-114">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="2f472-115">有害メッセージの処理</span><span class="sxs-lookup"><span data-stu-id="2f472-115">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
