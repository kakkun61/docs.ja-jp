---
title: Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing
ms.date: 03/30/2017
ms.assetid: 10ef3876-6f8e-4d4e-8444-f47847b64795
ms.openlocfilehash: bfa279887339f025e4cb7c9c455fd25098684073
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236612"
---
# <a name="microsofttransactionstransactionbridgedurableparticipantreplaywhilepreparing"></a><span data-ttu-id="73546-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span><span class="sxs-lookup"><span data-stu-id="73546-102">Microsoft.Transactions.TransactionBridge.DurableParticipantReplayWhilePreparing</span></span>

<span data-ttu-id="73546-103">WS-AT プロトコル サービスは、準備メッセージに応答していない永続的な参加要素から、リプレイ メッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="73546-103">The WS-AT protocol service received a Replay message from a durable participant, which did not respond to Prepare.</span></span> <span data-ttu-id="73546-104">そのため、トランザクションが中止されました。</span><span class="sxs-lookup"><span data-stu-id="73546-104">Consequently, the transaction was aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="73546-105">Description</span><span class="sxs-lookup"><span data-stu-id="73546-105">Description</span></span>  

 <span data-ttu-id="73546-106">永続的な参加要素がまだ準備している間にリプレイ メッセージが受信された場合は、トレースされます。</span><span class="sxs-lookup"><span data-stu-id="73546-106">Traced if a Replay message is received while a Durable participant is still Preparing.</span></span> <span data-ttu-id="73546-107">これは、この状態に対して無効なメッセージであり、トランザクションは中止されます。</span><span class="sxs-lookup"><span data-stu-id="73546-107">This is an illegal message for this state and the transaction is going to be aborted.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="73546-108">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="73546-108">Troubleshooting</span></span>

<span data-ttu-id="73546-109">このエラーを受信すると、永続参加要素 (従属トランザクションマネージャーを含む) が障害から回復したことを示している可能性があります。ただし、トランザクションの結果が不明であるため、その状態を要求します。</span><span class="sxs-lookup"><span data-stu-id="73546-109">Receiving this error can indicate that a Durable participant (including Subordinate TransactionManagers) has recovered from failure; however, it is unsure of the transaction outcome and requests its status.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73546-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="73546-110">See also</span></span>

- [<span data-ttu-id="73546-111">トレース</span><span class="sxs-lookup"><span data-stu-id="73546-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="73546-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="73546-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="73546-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="73546-113">Administration and Diagnostics</span></span>](../index.md)
