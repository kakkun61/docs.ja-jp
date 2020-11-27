---
title: 1016 - CompleteCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 246929fb-6f14-440a-814b-cd8349350644
ms.openlocfilehash: a192ffe19777ca3e2e9784f6506a0c2929ced000
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275532"
---
# <a name="1016---completecompletionworkitem"></a><span data-ttu-id="e5a23-102">1016 - CompleteCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="e5a23-102">1016 - CompleteCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="e5a23-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e5a23-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5a23-104">ID</span><span class="sxs-lookup"><span data-stu-id="e5a23-104">ID</span></span>|<span data-ttu-id="e5a23-105">1016</span><span class="sxs-lookup"><span data-stu-id="e5a23-105">1016</span></span>|  
|<span data-ttu-id="e5a23-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="e5a23-106">Keywords</span></span>|<span data-ttu-id="e5a23-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e5a23-107">WFRuntime</span></span>|  
|<span data-ttu-id="e5a23-108">Level</span><span class="sxs-lookup"><span data-stu-id="e5a23-108">Level</span></span>|<span data-ttu-id="e5a23-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="e5a23-109">Verbose</span></span>|  
|<span data-ttu-id="e5a23-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e5a23-110">Channel</span></span>|<span data-ttu-id="e5a23-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e5a23-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5a23-112">Description</span><span class="sxs-lookup"><span data-stu-id="e5a23-112">Description</span></span>  

 <span data-ttu-id="e5a23-113">CompletionWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="e5a23-113">Indicates a CompletionWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5a23-114">Message</span><span class="sxs-lookup"><span data-stu-id="e5a23-114">Message</span></span>  

 <span data-ttu-id="e5a23-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="e5a23-115">A CompletionWorkItem has completed for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="e5a23-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="e5a23-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5a23-117">詳細</span><span class="sxs-lookup"><span data-stu-id="e5a23-117">Details</span></span>  
  
|<span data-ttu-id="e5a23-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e5a23-118">Data Item Name</span></span>|<span data-ttu-id="e5a23-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e5a23-119">Data Item Type</span></span>|<span data-ttu-id="e5a23-120">Description</span><span class="sxs-lookup"><span data-stu-id="e5a23-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e5a23-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="e5a23-121">ParentActivity</span></span>|<span data-ttu-id="e5a23-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5a23-122">xs:string</span></span>|<span data-ttu-id="e5a23-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="e5a23-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="e5a23-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="e5a23-124">ParentDisplayName</span></span>|<span data-ttu-id="e5a23-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5a23-125">xs:string</span></span>|<span data-ttu-id="e5a23-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="e5a23-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="e5a23-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="e5a23-127">ParentInstanceId</span></span>|<span data-ttu-id="e5a23-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5a23-128">xs:string</span></span>|<span data-ttu-id="e5a23-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="e5a23-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="e5a23-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="e5a23-130">CompletedActivity</span></span>|<span data-ttu-id="e5a23-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5a23-131">xs:string</span></span>|<span data-ttu-id="e5a23-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="e5a23-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="e5a23-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="e5a23-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="e5a23-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5a23-134">xs:string</span></span>|<span data-ttu-id="e5a23-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="e5a23-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="e5a23-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="e5a23-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="e5a23-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5a23-137">xs:string</span></span>|<span data-ttu-id="e5a23-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="e5a23-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="e5a23-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e5a23-139">AppDomain</span></span>|<span data-ttu-id="e5a23-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="e5a23-140">xs:string</span></span>|<span data-ttu-id="e5a23-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e5a23-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
