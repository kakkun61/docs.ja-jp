---
title: 信頼できるメッセージの 1 秒あたりの破棄されたメッセージ
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 1e6db155f21fb2443394bc3a65235d4e9539dab3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276179"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="b9d21-102">信頼できるメッセージの 1 秒あたりの破棄されたメッセージ</span><span class="sxs-lookup"><span data-stu-id="b9d21-102">Reliable Messaging Messages Dropped Per Second</span></span>

<span data-ttu-id="b9d21-103">カウンター名 : 1 秒あたりに破棄された信頼できるメッセージ セッション</span><span class="sxs-lookup"><span data-stu-id="b9d21-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b9d21-104">Description</span><span class="sxs-lookup"><span data-stu-id="b9d21-104">Description</span></span>  

 <span data-ttu-id="b9d21-105">このサービスで 1 秒間に破棄された信頼できるメッセージング メッセージの合計数です。</span><span class="sxs-lookup"><span data-stu-id="b9d21-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="b9d21-106">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="b9d21-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b9d21-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b9d21-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
