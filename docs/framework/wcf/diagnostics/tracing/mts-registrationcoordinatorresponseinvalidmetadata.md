---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorResponseInvalidMetadata
ms.date: 03/30/2017
ms.assetid: a174bbf5-0ffe-4fda-969d-e7fbd1996123
ms.openlocfilehash: 65c82541e04bba71bf786681757f07efc1df41ca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236664"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorresponseinvalidmetadata"></a><span data-ttu-id="d8c0a-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorResponseInvalidMetadata</span><span class="sxs-lookup"><span data-stu-id="d8c0a-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorResponseInvalidMetadata</span></span>

<span data-ttu-id="d8c0a-103">WS-AtomicTransaction プロトコル サービスは、無効または互換性のないメタデータのあるエンドポイント参照を含むそのコーディネーターから、RegisterResponse メッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="d8c0a-103">The WS-Atomic Transaction protocol service received a RegisterResponse message from its coordinator that contains an endpoint reference with invalid or incompatible metadata.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d8c0a-104">Description</span><span class="sxs-lookup"><span data-stu-id="d8c0a-104">Description</span></span>  

 <span data-ttu-id="d8c0a-105">ローカルのトランザクション マネージャーが、その上位のトランザクション マネージャーに登録を試み、上位のトランザクション マネージャーが、RegisterResponse メッセージ内の無効なアドレスを返すときにトレースされます。</span><span class="sxs-lookup"><span data-stu-id="d8c0a-105">Traced when the local Transaction Manager tries to register with its superior Transaction Manager and the superior returns an invalid address within the RegisterResponse message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c0a-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8c0a-106">See also</span></span>

- [<span data-ttu-id="d8c0a-107">トレース</span><span class="sxs-lookup"><span data-stu-id="d8c0a-107">Tracing</span></span>](index.md)
- [<span data-ttu-id="d8c0a-108">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d8c0a-108">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d8c0a-109">管理と診断</span><span class="sxs-lookup"><span data-stu-id="d8c0a-109">Administration and Diagnostics</span></span>](../index.md)
