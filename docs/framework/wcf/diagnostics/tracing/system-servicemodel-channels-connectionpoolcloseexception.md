---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: d8edb8e916578247e62e3a3eb3b11b80f93416cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286956"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="54bf6-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="54bf6-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>

<span data-ttu-id="54bf6-103">この接続プールの接続を閉じている間に例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="54bf6-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="54bf6-104">Description</span><span class="sxs-lookup"><span data-stu-id="54bf6-104">Description</span></span>  

 <span data-ttu-id="54bf6-105">このエラーレベルのトレースは、Windows Communication Foundation (WCF) の接続プール機能によって使用される接続プールを閉じるときにエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="54bf6-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="54bf6-106">このエラーの原因としては、プールされた接続を閉じることに失敗した、またはプールされた接続で CloseTimeout が設定されていることが考えられます。</span><span class="sxs-lookup"><span data-stu-id="54bf6-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="54bf6-107">この例外がスローされると、このプール内でまだ閉じられていない接続はすべて中断され、他のプールにある閉じられていない接続は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="54bf6-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54bf6-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="54bf6-108">See also</span></span>

- [<span data-ttu-id="54bf6-109">トレース</span><span class="sxs-lookup"><span data-stu-id="54bf6-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="54bf6-110">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="54bf6-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="54bf6-111">管理と診断</span><span class="sxs-lookup"><span data-stu-id="54bf6-111">Administration and Diagnostics</span></span>](../index.md)
