---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: dc209fc41dc6b076dfb897880f753be51f7fb0ce
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239693"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="66e4d-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="66e4d-102">1011 - ScheduleExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="66e4d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="66e4d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66e4d-104">ID</span><span class="sxs-lookup"><span data-stu-id="66e4d-104">ID</span></span>|<span data-ttu-id="66e4d-105">1011</span><span class="sxs-lookup"><span data-stu-id="66e4d-105">1011</span></span>|  
|<span data-ttu-id="66e4d-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="66e4d-106">Keywords</span></span>|<span data-ttu-id="66e4d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="66e4d-107">WFRuntime</span></span>|  
|<span data-ttu-id="66e4d-108">Level</span><span class="sxs-lookup"><span data-stu-id="66e4d-108">Level</span></span>|<span data-ttu-id="66e4d-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="66e4d-109">Verbose</span></span>|  
|<span data-ttu-id="66e4d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="66e4d-110">Channel</span></span>|<span data-ttu-id="66e4d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="66e4d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="66e4d-112">Description</span><span class="sxs-lookup"><span data-stu-id="66e4d-112">Description</span></span>  

 <span data-ttu-id="66e4d-113">ExecuteActivityWorkItem がスケジュールされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="66e4d-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="66e4d-114">Message</span><span class="sxs-lookup"><span data-stu-id="66e4d-114">Message</span></span>  

 <span data-ttu-id="66e4d-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="66e4d-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="66e4d-116">詳細</span><span class="sxs-lookup"><span data-stu-id="66e4d-116">Details</span></span>  
  
|<span data-ttu-id="66e4d-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="66e4d-117">Data Item Name</span></span>|<span data-ttu-id="66e4d-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="66e4d-118">Data Item Type</span></span>|<span data-ttu-id="66e4d-119">Description</span><span class="sxs-lookup"><span data-stu-id="66e4d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="66e4d-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="66e4d-120">Activity</span></span>|<span data-ttu-id="66e4d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="66e4d-121">xs:string</span></span>|<span data-ttu-id="66e4d-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="66e4d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="66e4d-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="66e4d-123">DisplayName</span></span>|<span data-ttu-id="66e4d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="66e4d-124">xs:string</span></span>|<span data-ttu-id="66e4d-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="66e4d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="66e4d-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="66e4d-126">InstanceId</span></span>|<span data-ttu-id="66e4d-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="66e4d-127">xs:string</span></span>|<span data-ttu-id="66e4d-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="66e4d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="66e4d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="66e4d-129">AppDomain</span></span>|<span data-ttu-id="66e4d-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="66e4d-130">xs:string</span></span>|<span data-ttu-id="66e4d-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="66e4d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
