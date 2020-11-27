---
title: 'エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 5b289d7e026b481576bd7de186364773a57c17bc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256522"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="b778f-102">エンドポイント : 1 秒あたりの承認されていないセキュリティ呼び出し</span><span class="sxs-lookup"><span data-stu-id="b778f-102">Endpoint: Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="b778f-103">カウンター名 : 1 秒あたりの承認されていないセキュリティ呼び出し。</span><span class="sxs-lookup"><span data-stu-id="b778f-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b778f-104">Description</span><span class="sxs-lookup"><span data-stu-id="b778f-104">Description</span></span>  

 <span data-ttu-id="b778f-105">有効なユーザーから適切な保護を適用して送信されたが、特定のタスクの実行がユーザーに許可されていない、受信メッセージの 1 秒あたりの数です。</span><span class="sxs-lookup"><span data-stu-id="b778f-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="b778f-106">このカウンターは <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> メソッドで `false` が返された場合にインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="b778f-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="b778f-107">このカウンターは、次の式を使用して計算された値を持つ、パフォーマンスカウンターの種類 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))です。</span><span class="sxs-lookup"><span data-stu-id="b778f-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b778f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b778f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
