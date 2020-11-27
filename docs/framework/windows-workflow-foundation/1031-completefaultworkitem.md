---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: 557155fab35a37bdbaa45efb26d6bc025ad825c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281834"
---
# <a name="1031---completefaultworkitem"></a><span data-ttu-id="1c5ff-102">1031 - CompleteFaultWorkItem</span><span class="sxs-lookup"><span data-stu-id="1c5ff-102">1031 - CompleteFaultWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="1c5ff-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1c5ff-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c5ff-104">ID</span><span class="sxs-lookup"><span data-stu-id="1c5ff-104">ID</span></span>|<span data-ttu-id="1c5ff-105">1031</span><span class="sxs-lookup"><span data-stu-id="1c5ff-105">1031</span></span>|  
|<span data-ttu-id="1c5ff-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="1c5ff-106">Keywords</span></span>|<span data-ttu-id="1c5ff-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1c5ff-107">WFRuntime</span></span>|  
|<span data-ttu-id="1c5ff-108">Level</span><span class="sxs-lookup"><span data-stu-id="1c5ff-108">Level</span></span>|<span data-ttu-id="1c5ff-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="1c5ff-109">Verbose</span></span>|  
|<span data-ttu-id="1c5ff-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1c5ff-110">Channel</span></span>|<span data-ttu-id="1c5ff-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="1c5ff-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c5ff-112">Description</span><span class="sxs-lookup"><span data-stu-id="1c5ff-112">Description</span></span>  

 <span data-ttu-id="1c5ff-113">FaultWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-113">Indicates a FaultWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c5ff-114">Message</span><span class="sxs-lookup"><span data-stu-id="1c5ff-114">Message</span></span>  

 <span data-ttu-id="1c5ff-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の FaultWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-115">A FaultWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="1c5ff-116">Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-116">The exception was propagated from Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c5ff-117">詳細</span><span class="sxs-lookup"><span data-stu-id="1c5ff-117">Details</span></span>  
  
|<span data-ttu-id="1c5ff-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1c5ff-118">Data Item Name</span></span>|<span data-ttu-id="1c5ff-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1c5ff-119">Data Item Type</span></span>|<span data-ttu-id="1c5ff-120">Description</span><span class="sxs-lookup"><span data-stu-id="1c5ff-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c5ff-121">FaultActivity</span><span class="sxs-lookup"><span data-stu-id="1c5ff-121">FaultActivity</span></span>|<span data-ttu-id="1c5ff-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-122">xs:string</span></span>|<span data-ttu-id="1c5ff-123">エラーとなったアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-123">The type name of the fault activity.</span></span>|  
|<span data-ttu-id="1c5ff-124">FaultActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1c5ff-124">FaultActivityDisplayName</span></span>|<span data-ttu-id="1c5ff-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-125">xs:string</span></span>|<span data-ttu-id="1c5ff-126">エラーとなったアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-126">The display name of the fault activity.</span></span>|  
|<span data-ttu-id="1c5ff-127">FaultActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1c5ff-127">FaultActivityInstanceId</span></span>|<span data-ttu-id="1c5ff-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-128">xs:string</span></span>|<span data-ttu-id="1c5ff-129">エラーとなったアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-129">The instance id of the fault activity.</span></span>|  
|<span data-ttu-id="1c5ff-130">ExceptionActivity</span><span class="sxs-lookup"><span data-stu-id="1c5ff-130">ExceptionActivity</span></span>|<span data-ttu-id="1c5ff-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-131">xs:string</span></span>|<span data-ttu-id="1c5ff-132">例外をスローしたアクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-132">The type name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="1c5ff-133">ExceptionActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="1c5ff-133">ExceptionActivityDisplayName</span></span>|<span data-ttu-id="1c5ff-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-134">xs:string</span></span>|<span data-ttu-id="1c5ff-135">例外をスローしたアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-135">The display name of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="1c5ff-136">ExceptionActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="1c5ff-136">ExceptionActivityInstanceId</span></span>|<span data-ttu-id="1c5ff-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-137">xs:string</span></span>|<span data-ttu-id="1c5ff-138">例外をスローしたアクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-138">The instance id of the activity that threw the exception.</span></span>|  
|<span data-ttu-id="1c5ff-139">例外</span><span class="sxs-lookup"><span data-stu-id="1c5ff-139">Exception</span></span>|<span data-ttu-id="1c5ff-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-140">xs:string</span></span>|<span data-ttu-id="1c5ff-141">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="1c5ff-141">The exception details for the exception</span></span>|  
|<span data-ttu-id="1c5ff-142">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c5ff-142">AppDomain</span></span>|<span data-ttu-id="1c5ff-143">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c5ff-143">xs:string</span></span>|<span data-ttu-id="1c5ff-144">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1c5ff-144">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
