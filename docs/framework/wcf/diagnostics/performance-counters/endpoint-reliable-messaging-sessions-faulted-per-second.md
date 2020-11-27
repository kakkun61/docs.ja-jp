---
title: 'エンドポイント : 1 秒あたりのエラーとなった信頼できるメッセージ セッション'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: b9aa0e62aaf3a7e44f90c37a8611733321969ded
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290830"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="c6088-102">エンドポイント : 1 秒あたりのエラーとなった信頼できるメッセージ セッション</span><span class="sxs-lookup"><span data-stu-id="c6088-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>

<span data-ttu-id="c6088-103">カウンター名 : 1 秒あたりのエラーとなった信頼できるメッセージ セッション</span><span class="sxs-lookup"><span data-stu-id="c6088-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c6088-104">Description</span><span class="sxs-lookup"><span data-stu-id="c6088-104">Description</span></span>  

 <span data-ttu-id="c6088-105">1 秒以内にこのエンドポイントでエラーになった信頼できるメッセージ セッション数。</span><span class="sxs-lookup"><span data-stu-id="c6088-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="c6088-106">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="c6088-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c6088-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c6088-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
