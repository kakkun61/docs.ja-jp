---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: e4466df2ce96760db4790b6545484704c22f0842
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254299"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="3dd07-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="3dd07-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>

<span data-ttu-id="3dd07-103">処理されない実行例外が発生したため、指定された操作の指定されたトランザクションが完了しました。</span><span class="sxs-lookup"><span data-stu-id="3dd07-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3dd07-104">Description</span><span class="sxs-lookup"><span data-stu-id="3dd07-104">Description</span></span>  

 <span data-ttu-id="3dd07-105">現在のトランザクションを完了しようとしているときにエラーが発生した場合にトレースされます。</span><span class="sxs-lookup"><span data-stu-id="3dd07-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="3dd07-106">これは、応答またはエラーが呼び出し元に送信される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="3dd07-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="3dd07-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3dd07-107">Troubleshooting</span></span>  

 <span data-ttu-id="3dd07-108">トレース メッセージを調べて、例外メッセージとアクション可能な項目を確認してください。</span><span class="sxs-lookup"><span data-stu-id="3dd07-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd07-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dd07-109">See also</span></span>

- [<span data-ttu-id="3dd07-110">トレース</span><span class="sxs-lookup"><span data-stu-id="3dd07-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="3dd07-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="3dd07-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="3dd07-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="3dd07-112">Administration and Diagnostics</span></span>](../index.md)
