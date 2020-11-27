---
title: 1029 - ScheduleFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 3a56b29e-f740-459d-8576-d81e58bf5a03
ms.openlocfilehash: 5c109607b2d353d3d4a5a693f29ab66bb76c8398
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275090"
---
# <a name="1029---schedulefaultworkitem"></a><span data-ttu-id="bb7a0-102">1029 - ScheduleFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="bb7a0-102">1029 - ScheduleFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="bb7a0-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bb7a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb7a0-104">ID</span><span class="sxs-lookup"><span data-stu-id="bb7a0-104">ID</span></span>|<span data-ttu-id="bb7a0-105">1029</span><span class="sxs-lookup"><span data-stu-id="bb7a0-105">1029</span></span>|  
|<span data-ttu-id="bb7a0-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="bb7a0-106">Keywords</span></span>|<span data-ttu-id="bb7a0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bb7a0-107">WFRuntime</span></span>|  
|<span data-ttu-id="bb7a0-108">Level</span><span class="sxs-lookup"><span data-stu-id="bb7a0-108">Level</span></span>|<span data-ttu-id="bb7a0-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="bb7a0-109">Verbose</span></span>|  
|<span data-ttu-id="bb7a0-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bb7a0-110">Channel</span></span>|<span data-ttu-id="bb7a0-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bb7a0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bb7a0-112">Description</span><span class="sxs-lookup"><span data-stu-id="bb7a0-112">Description</span></span>  

 <span data-ttu-id="bb7a0-113">FaultWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-113">Indicates a FaultWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bb7a0-114">Message</span><span class="sxs-lookup"><span data-stu-id="bb7a0-114">Message</span></span>  

 <span data-ttu-id="bb7a0-115">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' に対して FaultWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-115">A FaultWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="bb7a0-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bb7a0-117">詳細</span><span class="sxs-lookup"><span data-stu-id="bb7a0-117">Details</span></span>  
  
|<span data-ttu-id="bb7a0-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bb7a0-118">Data Item Name</span></span>|<span data-ttu-id="bb7a0-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bb7a0-119">Data Item Type</span></span>|<span data-ttu-id="bb7a0-120">Description</span><span class="sxs-lookup"><span data-stu-id="bb7a0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bb7a0-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="bb7a0-121">FaultActivity</span></span>|<span data-ttu-id="bb7a0-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-122">xs:string</span></span>|<span data-ttu-id="bb7a0-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="bb7a0-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="bb7a0-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="bb7a0-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-125">xs:string</span></span>|<span data-ttu-id="bb7a0-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="bb7a0-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="bb7a0-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="bb7a0-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-128">xs:string</span></span>|<span data-ttu-id="bb7a0-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="bb7a0-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="bb7a0-130">ExceptionActivity</span></span>|<span data-ttu-id="bb7a0-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-131">xs:string</span></span>|<span data-ttu-id="bb7a0-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="bb7a0-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="bb7a0-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="bb7a0-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-134">xs:string</span></span>|<span data-ttu-id="bb7a0-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="bb7a0-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="bb7a0-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="bb7a0-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-137">xs:string</span></span>|<span data-ttu-id="bb7a0-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="bb7a0-139">例外</span><span class="sxs-lookup"><span data-stu-id="bb7a0-139">Exception</span></span>|<span data-ttu-id="bb7a0-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-140">xs:string</span></span>|<span data-ttu-id="bb7a0-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="bb7a0-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="bb7a0-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bb7a0-142">AppDomain</span></span>|<span data-ttu-id="bb7a0-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb7a0-143">xs:string</span></span>|<span data-ttu-id="bb7a0-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bb7a0-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
