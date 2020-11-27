---
title: 1021 - ScheduleBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
ms.openlocfilehash: 42ed23654622e29df8ffc210c8d5ba572fa69fd4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275350"
---
# <a name="1021---schedulebookmarkworkitem"></a><span data-ttu-id="a3bd0-102">1021 - ScheduleBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="a3bd0-102">1021 - ScheduleBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a3bd0-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a3bd0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a3bd0-104">ID</span><span class="sxs-lookup"><span data-stu-id="a3bd0-104">ID</span></span>|<span data-ttu-id="a3bd0-105">1021</span><span class="sxs-lookup"><span data-stu-id="a3bd0-105">1021</span></span>|  
|<span data-ttu-id="a3bd0-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="a3bd0-106">Keywords</span></span>|<span data-ttu-id="a3bd0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a3bd0-107">WFRuntime</span></span>|  
|<span data-ttu-id="a3bd0-108">Level</span><span class="sxs-lookup"><span data-stu-id="a3bd0-108">Level</span></span>|<span data-ttu-id="a3bd0-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="a3bd0-109">Verbose</span></span>|  
|<span data-ttu-id="a3bd0-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a3bd0-110">Channel</span></span>|<span data-ttu-id="a3bd0-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a3bd0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a3bd0-112">Description</span><span class="sxs-lookup"><span data-stu-id="a3bd0-112">Description</span></span>  

 <span data-ttu-id="a3bd0-113">BookmarkWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-113">Indicates a BookmarkWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a3bd0-114">Message</span><span class="sxs-lookup"><span data-stu-id="a3bd0-114">Message</span></span>  

 <span data-ttu-id="a3bd0-115">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' に対して BookmarkWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-115">A BookmarkWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="a3bd0-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a3bd0-117">詳細</span><span class="sxs-lookup"><span data-stu-id="a3bd0-117">Details</span></span>  
  
|<span data-ttu-id="a3bd0-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a3bd0-118">Data Item Name</span></span>|<span data-ttu-id="a3bd0-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a3bd0-119">Data Item Type</span></span>|<span data-ttu-id="a3bd0-120">Description</span><span class="sxs-lookup"><span data-stu-id="a3bd0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a3bd0-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a3bd0-121">Activity</span></span>|<span data-ttu-id="a3bd0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3bd0-122">xs:string</span></span>|<span data-ttu-id="a3bd0-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="a3bd0-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a3bd0-124">DisplayName</span></span>|<span data-ttu-id="a3bd0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3bd0-125">xs:string</span></span>|<span data-ttu-id="a3bd0-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="a3bd0-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a3bd0-127">InstanceId</span></span>|<span data-ttu-id="a3bd0-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3bd0-128">xs:string</span></span>|<span data-ttu-id="a3bd0-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a3bd0-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="a3bd0-130">BookmarkName</span></span>|<span data-ttu-id="a3bd0-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3bd0-131">xs:string</span></span>|<span data-ttu-id="a3bd0-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="a3bd0-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="a3bd0-133">BookmarkScope</span></span>|<span data-ttu-id="a3bd0-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3bd0-134">xs:string</span></span>|<span data-ttu-id="a3bd0-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="a3bd0-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a3bd0-136">AppDomain</span></span>|<span data-ttu-id="a3bd0-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="a3bd0-137">xs:string</span></span>|<span data-ttu-id="a3bd0-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a3bd0-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
