---
title: System.ServiceModel.ManualFlowThrottleLimitReached
ms.date: 03/30/2017
ms.assetid: 9aba851f-1830-493b-8e3e-60f454eb923e
ms.openlocfilehash: 180a06efc94acba40806e1f5d661553127549596
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248488"
---
# <a name="systemservicemodelmanualflowthrottlelimitreached"></a><span data-ttu-id="0477c-102">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="0477c-102">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>

<span data-ttu-id="0477c-103">System.ServiceModel.ManualFlowThrottleLimitReached</span><span class="sxs-lookup"><span data-stu-id="0477c-103">System.ServiceModel.ManualFlowThrottleLimitReached</span></span>  
  
## <a name="description"></a><span data-ttu-id="0477c-104">Description</span><span class="sxs-lookup"><span data-stu-id="0477c-104">Description</span></span>  

 <span data-ttu-id="0477c-105">システムは ManualFlowControlLimit スロットルに設定された制限値に達しました。</span><span class="sxs-lookup"><span data-stu-id="0477c-105">The system reached the limit set for the ManualFlowControlLimit throttle.</span></span> <span data-ttu-id="0477c-106">スロットル値を変更するには、ServiceHost または InstanceContext の ManualFlowControlLimit プロパティを適宜変更します。</span><span class="sxs-lookup"><span data-stu-id="0477c-106">The throttle value can be changed by modifying the ManualFlowControlLimit property on either the ServiceHost or InstanceContext, as applicable.</span></span>  
  
 <span data-ttu-id="0477c-107">このトレースは、マニュアル フロー制御制限が初めて 0 に減少したときに出力されます。</span><span class="sxs-lookup"><span data-stu-id="0477c-107">This trace is emitted when the manual flow control limit is initially reduced to 0.</span></span> <span data-ttu-id="0477c-108">それ以降は、0 に変更されてもトレースされません。</span><span class="sxs-lookup"><span data-stu-id="0477c-108">Subsequent changes to 0 are not traced.</span></span> <span data-ttu-id="0477c-109">インスタンス コンテキストに対するフロー制御制限は、コンテキストごとに 1 回トレースされます。</span><span class="sxs-lookup"><span data-stu-id="0477c-109">Flow control limit on the instance context is traced once for each context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0477c-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="0477c-110">See also</span></span>

- [<span data-ttu-id="0477c-111">トレース</span><span class="sxs-lookup"><span data-stu-id="0477c-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="0477c-112">トレースを使用したアプリケーションのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0477c-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0477c-113">管理と診断</span><span class="sxs-lookup"><span data-stu-id="0477c-113">Administration and Diagnostics</span></span>](../index.md)
