---
title: Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished
ms.date: 03/30/2017
ms.assetid: 54b677f7-03ad-40f2-9c5d-297a8ad9bf90
ms.openlocfilehash: bd6c9124e6346437e2bb35df620e00bad13b60f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258947"
---
# <a name="microsofttransactionstransactionbridgeparticipantstatemachinefinished"></a><span data-ttu-id="e2344-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span><span class="sxs-lookup"><span data-stu-id="e2344-102">Microsoft.Transactions.TransactionBridge.ParticipantStateMachineFinished</span></span>

<span data-ttu-id="e2344-103">参加要素の登録リストのステート マシンは完了状態になりました。</span><span class="sxs-lookup"><span data-stu-id="e2344-103">The state machine for a participant enlistment entered the finished state.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e2344-104">Description</span><span class="sxs-lookup"><span data-stu-id="e2344-104">Description</span></span>  

 <span data-ttu-id="e2344-105">下位参加要素登録リストの 2PC 処理が完了したときにトレースされます。</span><span class="sxs-lookup"><span data-stu-id="e2344-105">Traced when a subordinate participant enlistment has completed 2pc processing.</span></span> <span data-ttu-id="e2344-106">登録リストの結果は、Committed または Aborted のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="e2344-106">The outcome for the enlistment can be Committed or Aborted.</span></span> <span data-ttu-id="e2344-107">準備中、すべての参加要素を読み取り専用にする場合にもトレースされます。</span><span class="sxs-lookup"><span data-stu-id="e2344-107">It is also traced if any participant votes ReadOnly during Prepare.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2344-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2344-108">See also</span></span>

- [<span data-ttu-id="e2344-109">トレース</span><span class="sxs-lookup"><span data-stu-id="e2344-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="e2344-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e2344-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e2344-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="e2344-111">Administration and Diagnostics</span></span>](../index.md)
