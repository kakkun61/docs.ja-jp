---
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: da35201f2b3e3bc07e0b9139b0584ce37011e168
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294314"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="8306c-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="8306c-102">1032 - ScheduleRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="8306c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8306c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8306c-104">ID</span><span class="sxs-lookup"><span data-stu-id="8306c-104">ID</span></span>|<span data-ttu-id="8306c-105">1032</span><span class="sxs-lookup"><span data-stu-id="8306c-105">1032</span></span>|  
|<span data-ttu-id="8306c-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="8306c-106">Keywords</span></span>|<span data-ttu-id="8306c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8306c-107">WFRuntime</span></span>|  
|<span data-ttu-id="8306c-108">Level</span><span class="sxs-lookup"><span data-stu-id="8306c-108">Level</span></span>|<span data-ttu-id="8306c-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="8306c-109">Verbose</span></span>|  
|<span data-ttu-id="8306c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8306c-110">Channel</span></span>|<span data-ttu-id="8306c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="8306c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8306c-112">Description</span><span class="sxs-lookup"><span data-stu-id="8306c-112">Description</span></span>  

 <span data-ttu-id="8306c-113">RuntimeWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="8306c-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8306c-114">Message</span><span class="sxs-lookup"><span data-stu-id="8306c-114">Message</span></span>  

 <span data-ttu-id="8306c-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対してランタイム作業項目がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="8306c-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8306c-116">詳細</span><span class="sxs-lookup"><span data-stu-id="8306c-116">Details</span></span>  
  
|<span data-ttu-id="8306c-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8306c-117">Data Item Name</span></span>|<span data-ttu-id="8306c-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8306c-118">Data Item Type</span></span>|<span data-ttu-id="8306c-119">Description</span><span class="sxs-lookup"><span data-stu-id="8306c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8306c-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="8306c-120">Activity</span></span>|<span data-ttu-id="8306c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8306c-121">xs:string</span></span>|<span data-ttu-id="8306c-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="8306c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="8306c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8306c-123">DisplayName</span></span>|<span data-ttu-id="8306c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8306c-124">xs:string</span></span>|<span data-ttu-id="8306c-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="8306c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="8306c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="8306c-126">InstanceId</span></span>|<span data-ttu-id="8306c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8306c-127">xs:string</span></span>|<span data-ttu-id="8306c-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="8306c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8306c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8306c-129">AppDomain</span></span>|<span data-ttu-id="8306c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8306c-130">xs:string</span></span>|<span data-ttu-id="8306c-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8306c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
