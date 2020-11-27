---
title: 'エンドポイント : 1 秒あたりのトランザクション フロー'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: b814d7ca9e286426289c611b3a6bf5a52c1b2335
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256431"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="3b683-102">エンドポイント : 1 秒あたりのトランザクション フロー</span><span class="sxs-lookup"><span data-stu-id="3b683-102">Endpoint: Transactions Flowed Per Second</span></span>

<span data-ttu-id="3b683-103">カウンター名 : 1 秒あたりのトランザクション フロー。</span><span class="sxs-lookup"><span data-stu-id="3b683-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3b683-104">Description</span><span class="sxs-lookup"><span data-stu-id="3b683-104">Description</span></span>  

 <span data-ttu-id="3b683-105">このエンドポイントでの操作に対して実行された 1 秒あたりのトランザクションの数です。</span><span class="sxs-lookup"><span data-stu-id="3b683-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="3b683-106">このカウンターは、エンドポイントに送信されたメッセージにトランザクション ID が付与されている場合は常にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="3b683-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="3b683-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="3b683-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3b683-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="3b683-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
