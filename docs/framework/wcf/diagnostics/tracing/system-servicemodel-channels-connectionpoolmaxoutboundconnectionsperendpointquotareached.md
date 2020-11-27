---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 3e4e1ff7ea8d8768c8d902dc09bd3b78646c2caf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256327"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="44732-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="44732-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>

<span data-ttu-id="44732-103">WS-AT プロトコル サービスは、指定されたコーディネーション コンテキストを使用してトランザクションに参加することができませんでした。</span><span class="sxs-lookup"><span data-stu-id="44732-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="44732-104">Description</span><span class="sxs-lookup"><span data-stu-id="44732-104">Description</span></span>  

 <span data-ttu-id="44732-105">指定された 2PC プロトコルのトランザクションに MSDTC が参加できない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="44732-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="44732-106">これは、トランザクションが存在しなくなった場合、参加が許可されなくなった場合、または既に参加が多すぎる場合に発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="44732-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="44732-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="44732-107">Troubleshooting</span></span>  

 <span data-ttu-id="44732-108">トレース メッセージ内のステータス文字列を調べて、アクション可能な項目が存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="44732-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44732-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="44732-109">See also</span></span>

- [<span data-ttu-id="44732-110">トレース</span><span class="sxs-lookup"><span data-stu-id="44732-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="44732-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="44732-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="44732-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="44732-112">Administration and Diagnostics</span></span>](../index.md)
