---
title: 1 秒あたりのコミットされたトランザクション操作
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: deb29820aab09adad8825a299145772892117948
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250009"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="1cbd0-102">1 秒あたりのコミットされたトランザクション操作</span><span class="sxs-lookup"><span data-stu-id="1cbd0-102">Transacted Operations Committed Per Second</span></span>

<span data-ttu-id="1cbd0-103">カウンター名 : 1 秒あたりのコミットされたトランザクション操作。</span><span class="sxs-lookup"><span data-stu-id="1cbd0-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="1cbd0-104">Description</span><span class="sxs-lookup"><span data-stu-id="1cbd0-104">Description</span></span>  

 <span data-ttu-id="1cbd0-105">1 秒あたりに、このサービスでコミットされたトランザクション操作の数です。</span><span class="sxs-lookup"><span data-stu-id="1cbd0-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="1cbd0-106">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="1cbd0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1cbd0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1cbd0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
