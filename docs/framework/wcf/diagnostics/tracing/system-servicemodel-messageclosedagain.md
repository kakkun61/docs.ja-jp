---
title: System.ServiceModel.MessageClosedAgain
ms.date: 03/30/2017
ms.assetid: 24c274d4-65cd-4c91-9869-bc6eb34ef979
ms.openlocfilehash: a8aa5e600789df1b64a8a3f1a6355aaae6a6cf4b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294431"
---
# <a name="systemservicemodelmessageclosedagain"></a><span data-ttu-id="2b6cf-102">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="2b6cf-102">System.ServiceModel.MessageClosedAgain</span></span>

<span data-ttu-id="2b6cf-103">System.ServiceModel.MessageClosedAgain</span><span class="sxs-lookup"><span data-stu-id="2b6cf-103">System.ServiceModel.MessageClosedAgain</span></span>  
  
## <a name="description"></a><span data-ttu-id="2b6cf-104">Description</span><span class="sxs-lookup"><span data-stu-id="2b6cf-104">Description</span></span>  

 <span data-ttu-id="2b6cf-105">メッセージがもう一度閉じられました。</span><span class="sxs-lookup"><span data-stu-id="2b6cf-105">A message was closed again.</span></span>  
  
 <span data-ttu-id="2b6cf-106">メッセージを閉じることができるのは一度だけです。</span><span class="sxs-lookup"><span data-stu-id="2b6cf-106">A message should be closed only once.</span></span> <span data-ttu-id="2b6cf-107">このトレースがユーザー拡張コード内で出力されている場合は、ユーザー拡張コードは既に閉じられているメッセージをさらに閉じようとしていることが示されています。</span><span class="sxs-lookup"><span data-stu-id="2b6cf-107">If this trace is being emitted in user extension code, it indicates that the user extension code is closing a message that has already been closed.</span></span> <span data-ttu-id="2b6cf-108">このトレースが製品のコード内で出力されている場合は、ユーザー拡張コードがメッセージを閉じるのが早すぎる可能性があることが示されています。</span><span class="sxs-lookup"><span data-stu-id="2b6cf-108">If this trace is being emitted through product code, it indicates that the user extension code could potentially be closing a message too early.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b6cf-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b6cf-109">See also</span></span>

- [<span data-ttu-id="2b6cf-110">トレース</span><span class="sxs-lookup"><span data-stu-id="2b6cf-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="2b6cf-111">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2b6cf-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2b6cf-112">管理と診断</span><span class="sxs-lookup"><span data-stu-id="2b6cf-112">Administration and Diagnostics</span></span>](../index.md)
