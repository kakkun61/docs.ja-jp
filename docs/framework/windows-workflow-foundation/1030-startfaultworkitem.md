---
title: 1030 - StartFaultWorkItem
ms.date: 03/30/2017
ms.assetid: e1601fb9-0bc6-4dbe-816f-f24914063d34
ms.openlocfilehash: 52034f7cc7c6f6749fbbbf06db9267ecb6279ee1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281860"
---
# <a name="1030---startfaultworkitem"></a><span data-ttu-id="552d3-102">1030 - StartFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="552d3-102">1030 - StartFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="552d3-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="552d3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="552d3-104">ID</span><span class="sxs-lookup"><span data-stu-id="552d3-104">ID</span></span>|<span data-ttu-id="552d3-105">1030</span><span class="sxs-lookup"><span data-stu-id="552d3-105">1030</span></span>|  
|<span data-ttu-id="552d3-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="552d3-106">Keywords</span></span>|<span data-ttu-id="552d3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="552d3-107">WFRuntime</span></span>|  
|<span data-ttu-id="552d3-108">Level</span><span class="sxs-lookup"><span data-stu-id="552d3-108">Level</span></span>|<span data-ttu-id="552d3-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="552d3-109">Verbose</span></span>|  
|<span data-ttu-id="552d3-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="552d3-110">Channel</span></span>|<span data-ttu-id="552d3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="552d3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="552d3-112">Description</span><span class="sxs-lookup"><span data-stu-id="552d3-112">Description</span></span>  

 <span data-ttu-id="552d3-113">FaultWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="552d3-113">Indicates a FaultWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="552d3-114">Message</span><span class="sxs-lookup"><span data-stu-id="552d3-114">Message</span></span>  

 <span data-ttu-id="552d3-115">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' の FaultWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="552d3-115">Starting execution of a FaultWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="552d3-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="552d3-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="552d3-117">詳細</span><span class="sxs-lookup"><span data-stu-id="552d3-117">Details</span></span>  
  
|<span data-ttu-id="552d3-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="552d3-118">Data Item Name</span></span>|<span data-ttu-id="552d3-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="552d3-119">Data Item Type</span></span>|<span data-ttu-id="552d3-120">Description</span><span class="sxs-lookup"><span data-stu-id="552d3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="552d3-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="552d3-121">FaultActivity</span></span>|<span data-ttu-id="552d3-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-122">xs:string</span></span>|<span data-ttu-id="552d3-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="552d3-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="552d3-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="552d3-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="552d3-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-125">xs:string</span></span>|<span data-ttu-id="552d3-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="552d3-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="552d3-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="552d3-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="552d3-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-128">xs:string</span></span>|<span data-ttu-id="552d3-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="552d3-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="552d3-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="552d3-130">ExceptionActivity</span></span>|<span data-ttu-id="552d3-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-131">xs:string</span></span>|<span data-ttu-id="552d3-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="552d3-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="552d3-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="552d3-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="552d3-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-134">xs:string</span></span>|<span data-ttu-id="552d3-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="552d3-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="552d3-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="552d3-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="552d3-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-137">xs:string</span></span>|<span data-ttu-id="552d3-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="552d3-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="552d3-139">例外</span><span class="sxs-lookup"><span data-stu-id="552d3-139">Exception</span></span>|<span data-ttu-id="552d3-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-140">xs:string</span></span>|<span data-ttu-id="552d3-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="552d3-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="552d3-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="552d3-142">AppDomain</span></span>|<span data-ttu-id="552d3-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="552d3-143">xs:string</span></span>|<span data-ttu-id="552d3-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="552d3-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
