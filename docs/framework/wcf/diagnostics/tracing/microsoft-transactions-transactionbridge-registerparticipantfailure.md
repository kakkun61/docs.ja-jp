---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: 2f0198d3c288b4c3833cdac8e5f943ba822c22e9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252024"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="734e6-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="734e6-102">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>

<span data-ttu-id="734e6-103">WS-AT プロトコル サービスは、制御プロトコルの参加要素の登録に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="734e6-103">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="734e6-104">Description</span><span class="sxs-lookup"><span data-stu-id="734e6-104">Description</span></span>  

 <span data-ttu-id="734e6-105">MSDTC により無効な登録要求が検出された場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="734e6-105">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="734e6-106">これは、複数の完了登録要求や内部エラーによって発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="734e6-106">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="734e6-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="734e6-107">Troubleshooting</span></span>  

 <span data-ttu-id="734e6-108">完了を複数回登録しないでください。</span><span class="sxs-lookup"><span data-stu-id="734e6-108">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="734e6-109">また、トレース メッセージ内のステータス文字列を調べて、アクション可能な項目が存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="734e6-109">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="734e6-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="734e6-110">See also</span></span>

- [<span data-ttu-id="734e6-111">トレース</span><span class="sxs-lookup"><span data-stu-id="734e6-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="734e6-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="734e6-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="734e6-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="734e6-113">Administration and Diagnostics</span></span>](../index.md)
