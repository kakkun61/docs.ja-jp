---
title: 224 - MessageThrottleAtSeventyPercent
ms.date: 03/30/2017
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
ms.openlocfilehash: 26b860b88313a971960a65b599562ef1ccb4e7da
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243522"
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="a2197-102">224 - MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="a2197-102">224 - MessageThrottleAtSeventyPercent</span></span>

## <a name="properties"></a><span data-ttu-id="a2197-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a2197-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2197-104">ID</span><span class="sxs-lookup"><span data-stu-id="a2197-104">ID</span></span>|<span data-ttu-id="a2197-105">224</span><span class="sxs-lookup"><span data-stu-id="a2197-105">224</span></span>|  
|<span data-ttu-id="a2197-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="a2197-106">Keywords</span></span>|<span data-ttu-id="a2197-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a2197-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a2197-108">Level</span><span class="sxs-lookup"><span data-stu-id="a2197-108">Level</span></span>|<span data-ttu-id="a2197-109">警告</span><span class="sxs-lookup"><span data-stu-id="a2197-109">Warning</span></span>|  
|<span data-ttu-id="a2197-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a2197-110">Channel</span></span>|<span data-ttu-id="a2197-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a2197-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a2197-112">Description</span><span class="sxs-lookup"><span data-stu-id="a2197-112">Description</span></span>  

 <span data-ttu-id="a2197-113">`MessageThrottleExceeded` イベントは、主要なサービス スロットルの 1 つを超過したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2197-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="a2197-114">アクティビティの急増が緩やかになり、スロットルの現在の値が現在の制限の 70% である場合は、このイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2197-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="a2197-115">このイベントは、アクティビティが緩やかになったときに一度だけ生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2197-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="a2197-116">現在の値が 70% の基準付近を上下している (70、69、70、71、70、69 など) 場合は、最初に 70% に達したときにイベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2197-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="a2197-117">このイベントが生成された後にスロットル制限を超えた場合は、`MessageThrottleExceeded` イベントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2197-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a2197-118">Message</span><span class="sxs-lookup"><span data-stu-id="a2197-118">Message</span></span>  

 <span data-ttu-id="a2197-119">スロットル '%1' の '%2' の制限は 70%% です。</span><span class="sxs-lookup"><span data-stu-id="a2197-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a2197-120">詳細</span><span class="sxs-lookup"><span data-stu-id="a2197-120">Details</span></span>  
  
|<span data-ttu-id="a2197-121">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a2197-121">Data Item Name</span></span>|<span data-ttu-id="a2197-122">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a2197-122">Data Item Type</span></span>|<span data-ttu-id="a2197-123">Description</span><span class="sxs-lookup"><span data-stu-id="a2197-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a2197-124">Throttle Name</span><span class="sxs-lookup"><span data-stu-id="a2197-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="a2197-125">超過したスロットルの名前。</span><span class="sxs-lookup"><span data-stu-id="a2197-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="a2197-126">`MaxConcurrentCalls`、`MaxConcurrentInstances`、または `MaxConcurrentSessions`。</span><span class="sxs-lookup"><span data-stu-id="a2197-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="a2197-127">制限</span><span class="sxs-lookup"><span data-stu-id="a2197-127">Limit</span></span>|`xs:long`|<span data-ttu-id="a2197-128">現在構成されている、スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="a2197-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="a2197-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="a2197-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="a2197-130">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="a2197-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a2197-131">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="a2197-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a2197-132">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="a2197-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a2197-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a2197-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a2197-134">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a2197-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
