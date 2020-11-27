---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: 83bb67f2a5eb1a9353129bce9ec22f18eb382259
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251972"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="faa66-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="faa66-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>

<span data-ttu-id="faa66-103">WS-AT プロトコル サービスは、Register メッセージをコーディネーターに送信できませんでした。</span><span class="sxs-lookup"><span data-stu-id="faa66-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="faa66-104">Description</span><span class="sxs-lookup"><span data-stu-id="faa66-104">Description</span></span>  

 <span data-ttu-id="faa66-105">メッセージを送信できないために、ローカルの TransactionManager がその上位の TransactionManager に登録できない場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="faa66-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="faa66-106">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="faa66-106">Troubleshooting</span></span>  

 <span data-ttu-id="faa66-107">トレース メッセージを調べて、メッセージの送信エラーの原因となった例外を確認してください。</span><span class="sxs-lookup"><span data-stu-id="faa66-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa66-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="faa66-108">See also</span></span>

- [<span data-ttu-id="faa66-109">トレース</span><span class="sxs-lookup"><span data-stu-id="faa66-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="faa66-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="faa66-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="faa66-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="faa66-111">Administration and Diagnostics</span></span>](../index.md)
