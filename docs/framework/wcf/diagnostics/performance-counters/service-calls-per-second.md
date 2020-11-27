---
title: 'サービス : 1 秒あたりの呼び出し数'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 7e702d402909c4a85a2cb42c837e0813c4d9f841
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96252882"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="f9ed3-102">サービス : 1 秒あたりの呼び出し数</span><span class="sxs-lookup"><span data-stu-id="f9ed3-102">Service: Calls Per Second</span></span>

<span data-ttu-id="f9ed3-103">カウンター名 : 1 秒あたりの呼び出し</span><span class="sxs-lookup"><span data-stu-id="f9ed3-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f9ed3-104">Description</span><span class="sxs-lookup"><span data-stu-id="f9ed3-104">Description</span></span>  

 <span data-ttu-id="f9ed3-105">このサービスが 1 秒あたりに呼び出される回数です。</span><span class="sxs-lookup"><span data-stu-id="f9ed3-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="f9ed3-106">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="f9ed3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f9ed3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)。ここで、分子 (N) は最後のサンプル間隔中に実行された操作の数を、分母 (D) は最後のサンプル間隔中に経過したタイマー刻み数を、F はタイマー刻みの頻度をそれぞれ表します。</span><span class="sxs-lookup"><span data-stu-id="f9ed3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
