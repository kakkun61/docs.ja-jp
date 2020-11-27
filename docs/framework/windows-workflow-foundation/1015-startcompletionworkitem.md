---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: c0d8572f192a8faa22327fd671cd9ea49c5054ca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275545"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="c44c2-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="c44c2-102">1015 - StartCompletionWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="c44c2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c44c2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c44c2-104">ID</span><span class="sxs-lookup"><span data-stu-id="c44c2-104">ID</span></span>|<span data-ttu-id="c44c2-105">1015</span><span class="sxs-lookup"><span data-stu-id="c44c2-105">1015</span></span>|  
|<span data-ttu-id="c44c2-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="c44c2-106">Keywords</span></span>|<span data-ttu-id="c44c2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c44c2-107">WFRuntime</span></span>|  
|<span data-ttu-id="c44c2-108">Level</span><span class="sxs-lookup"><span data-stu-id="c44c2-108">Level</span></span>|<span data-ttu-id="c44c2-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="c44c2-109">Verbose</span></span>|  
|<span data-ttu-id="c44c2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c44c2-110">Channel</span></span>|<span data-ttu-id="c44c2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c44c2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c44c2-112">Description</span><span class="sxs-lookup"><span data-stu-id="c44c2-112">Description</span></span>  

 <span data-ttu-id="c44c2-113">CompletionWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="c44c2-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c44c2-114">Message</span><span class="sxs-lookup"><span data-stu-id="c44c2-114">Message</span></span>  

 <span data-ttu-id="c44c2-115">親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="c44c2-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="c44c2-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。</span><span class="sxs-lookup"><span data-stu-id="c44c2-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c44c2-117">詳細</span><span class="sxs-lookup"><span data-stu-id="c44c2-117">Details</span></span>  
  
|<span data-ttu-id="c44c2-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c44c2-118">Data Item Name</span></span>|<span data-ttu-id="c44c2-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c44c2-119">Data Item Type</span></span>|<span data-ttu-id="c44c2-120">Description</span><span class="sxs-lookup"><span data-stu-id="c44c2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c44c2-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="c44c2-121">ParentActivity</span></span>|<span data-ttu-id="c44c2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c44c2-122">xs:string</span></span>|<span data-ttu-id="c44c2-123">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c44c2-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="c44c2-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="c44c2-124">ParentDisplayName</span></span>|<span data-ttu-id="c44c2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c44c2-125">xs:string</span></span>|<span data-ttu-id="c44c2-126">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c44c2-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="c44c2-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="c44c2-127">ParentInstanceId</span></span>|<span data-ttu-id="c44c2-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="c44c2-128">xs:string</span></span>|<span data-ttu-id="c44c2-129">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c44c2-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="c44c2-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="c44c2-130">CompletedActivity</span></span>|<span data-ttu-id="c44c2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="c44c2-131">xs:string</span></span>|<span data-ttu-id="c44c2-132">完了したアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c44c2-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="c44c2-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="c44c2-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="c44c2-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="c44c2-134">xs:string</span></span>|<span data-ttu-id="c44c2-135">完了したアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c44c2-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="c44c2-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="c44c2-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="c44c2-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="c44c2-137">xs:string</span></span>|<span data-ttu-id="c44c2-138">完了したアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c44c2-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="c44c2-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c44c2-139">AppDomain</span></span>|<span data-ttu-id="c44c2-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="c44c2-140">xs:string</span></span>|<span data-ttu-id="c44c2-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c44c2-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
