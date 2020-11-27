---
title: 57398 - MaxInstancesExceeded
ms.date: 03/30/2017
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
ms.openlocfilehash: bd490aad24fba4550bc778799cd6f836dcfd466c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289179"
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="b8da1-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="b8da1-102">57398 - MaxInstancesExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="b8da1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="b8da1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b8da1-104">ID</span><span class="sxs-lookup"><span data-stu-id="b8da1-104">ID</span></span>|<span data-ttu-id="b8da1-105">57398</span><span class="sxs-lookup"><span data-stu-id="b8da1-105">57398</span></span>|  
|<span data-ttu-id="b8da1-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="b8da1-106">Keywords</span></span>|<span data-ttu-id="b8da1-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="b8da1-107">WFServices</span></span>|  
|<span data-ttu-id="b8da1-108">Level</span><span class="sxs-lookup"><span data-stu-id="b8da1-108">Level</span></span>|<span data-ttu-id="b8da1-109">警告</span><span class="sxs-lookup"><span data-stu-id="b8da1-109">Warning</span></span>|  
|<span data-ttu-id="b8da1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="b8da1-110">Channel</span></span>|<span data-ttu-id="b8da1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b8da1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b8da1-112">Description</span><span class="sxs-lookup"><span data-stu-id="b8da1-112">Description</span></span>  

 <span data-ttu-id="b8da1-113">システムがスロットル 'MaxConcurrentInstances' に設定された制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="b8da1-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b8da1-114">Message</span><span class="sxs-lookup"><span data-stu-id="b8da1-114">Message</span></span>  

 <span data-ttu-id="b8da1-115">システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="b8da1-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="b8da1-116">このスロットルの制限は %1 に設定されました。</span><span class="sxs-lookup"><span data-stu-id="b8da1-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="b8da1-117">スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b8da1-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b8da1-118">詳細</span><span class="sxs-lookup"><span data-stu-id="b8da1-118">Details</span></span>  
  
|<span data-ttu-id="b8da1-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="b8da1-119">Data Item Name</span></span>|<span data-ttu-id="b8da1-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="b8da1-120">Data Item Type</span></span>|<span data-ttu-id="b8da1-121">Description</span><span class="sxs-lookup"><span data-stu-id="b8da1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b8da1-122">名前</span><span class="sxs-lookup"><span data-stu-id="b8da1-122">Name</span></span>|<span data-ttu-id="b8da1-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8da1-123">xs:string</span></span>|<span data-ttu-id="b8da1-124">項目の名前。</span><span class="sxs-lookup"><span data-stu-id="b8da1-124">The name of the item.</span></span>|  
|<span data-ttu-id="b8da1-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b8da1-125">AppDomain</span></span>|<span data-ttu-id="b8da1-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="b8da1-126">xs:string</span></span>|<span data-ttu-id="b8da1-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="b8da1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
