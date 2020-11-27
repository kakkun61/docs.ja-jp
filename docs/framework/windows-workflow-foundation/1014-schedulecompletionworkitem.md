---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 7fd93683851c5a8c4ab253272c3f2129b3f0bb49
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275558"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="a6585-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="a6585-102">1014 - ScheduleCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a6585-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a6585-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a6585-104">ID</span><span class="sxs-lookup"><span data-stu-id="a6585-104">ID</span></span>|<span data-ttu-id="a6585-105">1014</span><span class="sxs-lookup"><span data-stu-id="a6585-105">1014</span></span>|  
|<span data-ttu-id="a6585-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="a6585-106">Keywords</span></span>|<span data-ttu-id="a6585-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a6585-107">WFRuntime</span></span>|  
|<span data-ttu-id="a6585-108">Level</span><span class="sxs-lookup"><span data-stu-id="a6585-108">Level</span></span>|<span data-ttu-id="a6585-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="a6585-109">Verbose</span></span>|  
|<span data-ttu-id="a6585-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a6585-110">Channel</span></span>|<span data-ttu-id="a6585-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a6585-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a6585-112">Description</span><span class="sxs-lookup"><span data-stu-id="a6585-112">Description</span></span>  

 <span data-ttu-id="a6585-113">CompletionWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a6585-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a6585-114">Message</span><span class="sxs-lookup"><span data-stu-id="a6585-114">Message</span></span>  

 <span data-ttu-id="a6585-115">親アクティビティ ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' に対して、完了作業項目がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="a6585-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="a6585-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="a6585-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a6585-117">詳細</span><span class="sxs-lookup"><span data-stu-id="a6585-117">Details</span></span>  
  
|<span data-ttu-id="a6585-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a6585-118">Data Item Name</span></span>|<span data-ttu-id="a6585-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a6585-119">Data Item Type</span></span>|<span data-ttu-id="a6585-120">Description</span><span class="sxs-lookup"><span data-stu-id="a6585-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a6585-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="a6585-121">ParentActivity</span></span>|<span data-ttu-id="a6585-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6585-122">xs:string</span></span>|<span data-ttu-id="a6585-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="a6585-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="a6585-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="a6585-124">ParentDisplayName</span></span>|<span data-ttu-id="a6585-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6585-125">xs:string</span></span>|<span data-ttu-id="a6585-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="a6585-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="a6585-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="a6585-127">ParentInstanceId</span></span>|<span data-ttu-id="a6585-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6585-128">xs:string</span></span>|<span data-ttu-id="a6585-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="a6585-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="a6585-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="a6585-130">CompletedActivity</span></span>|<span data-ttu-id="a6585-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6585-131">xs:string</span></span>|<span data-ttu-id="a6585-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="a6585-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="a6585-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="a6585-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="a6585-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6585-134">xs:string</span></span>|<span data-ttu-id="a6585-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="a6585-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="a6585-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="a6585-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="a6585-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6585-137">xs:string</span></span>|<span data-ttu-id="a6585-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="a6585-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="a6585-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a6585-139">AppDomain</span></span>|<span data-ttu-id="a6585-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="a6585-140">xs:string</span></span>|<span data-ttu-id="a6585-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a6585-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
