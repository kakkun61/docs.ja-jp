---
title: 相関関係
ms.date: 03/30/2017
ms.assetid: 60151f6c-19b7-47af-9cdc-76c2ac95f301
ms.openlocfilehash: 1a357dd9469d7428af56772d3241e59766429990
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286774"
---
# <a name="correlation"></a><span data-ttu-id="b2242-102">相関関係</span><span class="sxs-lookup"><span data-stu-id="b2242-102">Correlation</span></span>

<span data-ttu-id="b2242-103">ワークフロー サービス アプリケーションが他のサービスと通信するときには、やり取りされるメッセージが、適切なワークフロー インスタンスにディスパッチされることが重要です。</span><span class="sxs-lookup"><span data-stu-id="b2242-103">When workflow service applications communicate with other services, it is important that messages between them are dispatched to the appropriate workflow instance.</span></span> <span data-ttu-id="b2242-104">相関関係によって、これを実現する機構が提供されます。</span><span class="sxs-lookup"><span data-stu-id="b2242-104">Correlation provides the mechanism for this.</span></span> <span data-ttu-id="b2242-105">このセクションの各トピックでは、相関関係の概要を示し、さまざまなワークフロー サービス シナリオで相関関係を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2242-105">The topics in this section provide an overview of correlation and how to use it in different workflow service scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2242-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b2242-106">In This Section</span></span>  

 [<span data-ttu-id="b2242-107">相関関係の概要</span><span class="sxs-lookup"><span data-stu-id="b2242-107">Correlation Overview</span></span>](correlation-overview.md)  
 <span data-ttu-id="b2242-108">[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] で使用可能な相関関係の種類の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="b2242-108">Provides an overview of the types of correlation available in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="b2242-109">永続的な二重</span><span class="sxs-lookup"><span data-stu-id="b2242-109">Durable Duplex</span></span>](durable-duplex-correlation.md)  
 <span data-ttu-id="b2242-110">永続的な二重の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2242-110">Describes durable duplex correlation.</span></span>
  
 [<span data-ttu-id="b2242-111">要求/応答</span><span class="sxs-lookup"><span data-stu-id="b2242-111">Request-Reply</span></span>](request-reply-correlation.md)  
 <span data-ttu-id="b2242-112">要求/応答の相関関係について説明します。</span><span class="sxs-lookup"><span data-stu-id="b2242-112">Describes request-reply correlation.</span></span>  
  
 [<span data-ttu-id="b2242-113">相関関係のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b2242-113">Troubleshooting Correlation</span></span>](troubleshooting-correlation.md)  
 <span data-ttu-id="b2242-114">相関関係のトラブルシューティング方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b2242-114">Provides methods for troubleshooting correlation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2242-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2242-115">See also</span></span>

- <xref:System.ServiceModel.Activities.CorrelationHandle>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.Receive>
- <xref:System.ServiceModel.CorrelationQuery>
