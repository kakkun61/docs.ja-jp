---
title: System.ServiceModel.TxReleaseServiceInstanceOnCompletion
ms.date: 03/30/2017
ms.assetid: e167bad3-861f-43e4-9e78-9c275cf64a29
ms.openlocfilehash: 31913532c17416cfb8085798bedc8544c7b83793
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295289"
---
# <a name="systemservicemodeltxreleaseserviceinstanceoncompletion"></a><span data-ttu-id="fa694-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span><span class="sxs-lookup"><span data-stu-id="fa694-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span></span>

<span data-ttu-id="fa694-103">ReleaseServiceInstanceOnTransactionComplete の ServiceBehaviorAttribute が true に設定されていたので、トランザクション '{0}' の完了時にサービス インスタンスが解放されました。</span><span class="sxs-lookup"><span data-stu-id="fa694-103">The service instance was released on the completion of the transaction '{0}' because the ReleaseServiceInstanceOnTransactionComplete ServiceBehaviorAttribute was set to true.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fa694-104">Description</span><span class="sxs-lookup"><span data-stu-id="fa694-104">Description</span></span>  

 <span data-ttu-id="fa694-105">現在のアクティブなトランザクションが完了して現在のサービス インスタンスが解放されるか破棄され、ReleaseServiceInstanceOnTransactionComplete が `true` に設定されると、トレースされます。</span><span class="sxs-lookup"><span data-stu-id="fa694-105">Traced when the current service instance is released or disposed due to the completion of the current active transaction and ReleaseServiceInstanceOnTransactionComplete is set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa694-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa694-106">See also</span></span>

- [<span data-ttu-id="fa694-107">トレース</span><span class="sxs-lookup"><span data-stu-id="fa694-107">Tracing</span></span>](index.md)
- [<span data-ttu-id="fa694-108">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fa694-108">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="fa694-109">管理と診断</span><span class="sxs-lookup"><span data-stu-id="fa694-109">Administration and Diagnostics</span></span>](../index.md)
