---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 812531d4206dfee20f183b9461330e71263b0bf8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239771"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="5f64a-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="5f64a-102">1009 - ActivityScheduled</span></span>

## <a name="properties"></a><span data-ttu-id="5f64a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5f64a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f64a-104">ID</span><span class="sxs-lookup"><span data-stu-id="5f64a-104">ID</span></span>|<span data-ttu-id="5f64a-105">1009</span><span class="sxs-lookup"><span data-stu-id="5f64a-105">1009</span></span>|  
|<span data-ttu-id="5f64a-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="5f64a-106">Keywords</span></span>|<span data-ttu-id="5f64a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5f64a-107">WFRuntime</span></span>|  
|<span data-ttu-id="5f64a-108">Level</span><span class="sxs-lookup"><span data-stu-id="5f64a-108">Level</span></span>|<span data-ttu-id="5f64a-109">情報</span><span class="sxs-lookup"><span data-stu-id="5f64a-109">Information</span></span>|  
|<span data-ttu-id="5f64a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="5f64a-110">Channel</span></span>|<span data-ttu-id="5f64a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5f64a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5f64a-112">Description</span><span class="sxs-lookup"><span data-stu-id="5f64a-112">Description</span></span>  

 <span data-ttu-id="5f64a-113">アクティビティの実行がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="5f64a-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5f64a-114">Message</span><span class="sxs-lookup"><span data-stu-id="5f64a-114">Message</span></span>  

 <span data-ttu-id="5f64a-115">Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。</span><span class="sxs-lookup"><span data-stu-id="5f64a-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5f64a-116">詳細</span><span class="sxs-lookup"><span data-stu-id="5f64a-116">Details</span></span>  
  
|<span data-ttu-id="5f64a-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5f64a-117">Data Item Name</span></span>|<span data-ttu-id="5f64a-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5f64a-118">Data Item Type</span></span>|<span data-ttu-id="5f64a-119">Description</span><span class="sxs-lookup"><span data-stu-id="5f64a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5f64a-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="5f64a-120">ParentActivity</span></span>|<span data-ttu-id="5f64a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f64a-121">xs:string</span></span>|<span data-ttu-id="5f64a-122">親アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="5f64a-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="5f64a-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="5f64a-123">ParentDisplayName</span></span>|<span data-ttu-id="5f64a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f64a-124">xs:string</span></span>|<span data-ttu-id="5f64a-125">親アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="5f64a-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="5f64a-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="5f64a-126">ParentInstanceId</span></span>|<span data-ttu-id="5f64a-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f64a-127">xs:string</span></span>|<span data-ttu-id="5f64a-128">親アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="5f64a-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="5f64a-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="5f64a-129">ChildActivity</span></span>|<span data-ttu-id="5f64a-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f64a-130">xs:string</span></span>|<span data-ttu-id="5f64a-131">スケジュール済みの子アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="5f64a-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5f64a-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="5f64a-132">ChildDisplayName</span></span>|<span data-ttu-id="5f64a-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f64a-133">xs:string</span></span>|<span data-ttu-id="5f64a-134">スケジュール済みの子アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="5f64a-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5f64a-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="5f64a-135">ChildInstanceId</span></span>|<span data-ttu-id="5f64a-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f64a-136">xs:string</span></span>|<span data-ttu-id="5f64a-137">スケジュール済み子アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="5f64a-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="5f64a-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5f64a-138">AppDomain</span></span>|<span data-ttu-id="5f64a-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="5f64a-139">xs:string</span></span>|<span data-ttu-id="5f64a-140">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5f64a-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
