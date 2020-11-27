---
title: 1017 - ScheduleCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
ms.openlocfilehash: 6aed9773aa45251075520a0f955e9d71234f1357
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275620"
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="a1fe3-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="a1fe3-102">1017 - ScheduleCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a1fe3-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1fe3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1fe3-104">ID</span><span class="sxs-lookup"><span data-stu-id="a1fe3-104">ID</span></span>|<span data-ttu-id="a1fe3-105">1017</span><span class="sxs-lookup"><span data-stu-id="a1fe3-105">1017</span></span>|  
|<span data-ttu-id="a1fe3-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="a1fe3-106">Keywords</span></span>|<span data-ttu-id="a1fe3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a1fe3-107">WFRuntime</span></span>|  
|<span data-ttu-id="a1fe3-108">Level</span><span class="sxs-lookup"><span data-stu-id="a1fe3-108">Level</span></span>|<span data-ttu-id="a1fe3-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="a1fe3-109">Verbose</span></span>|  
|<span data-ttu-id="a1fe3-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="a1fe3-110">Channel</span></span>|<span data-ttu-id="a1fe3-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="a1fe3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a1fe3-112">Description</span><span class="sxs-lookup"><span data-stu-id="a1fe3-112">Description</span></span>  

 <span data-ttu-id="a1fe3-113">CancelActivityWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a1fe3-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a1fe3-114">Message</span><span class="sxs-lookup"><span data-stu-id="a1fe3-114">Message</span></span>  

 <span data-ttu-id="a1fe3-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して CancelActivityWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="a1fe3-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a1fe3-116">詳細</span><span class="sxs-lookup"><span data-stu-id="a1fe3-116">Details</span></span>  
  
|<span data-ttu-id="a1fe3-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="a1fe3-117">Data Item Name</span></span>|<span data-ttu-id="a1fe3-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="a1fe3-118">Data Item Type</span></span>|<span data-ttu-id="a1fe3-119">Description</span><span class="sxs-lookup"><span data-stu-id="a1fe3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a1fe3-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a1fe3-120">Activity</span></span>|<span data-ttu-id="a1fe3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fe3-121">xs:string</span></span>|<span data-ttu-id="a1fe3-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="a1fe3-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a1fe3-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a1fe3-123">DisplayName</span></span>|<span data-ttu-id="a1fe3-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fe3-124">xs:string</span></span>|<span data-ttu-id="a1fe3-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="a1fe3-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a1fe3-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a1fe3-126">InstanceId</span></span>|<span data-ttu-id="a1fe3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fe3-127">xs:string</span></span>|<span data-ttu-id="a1fe3-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="a1fe3-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a1fe3-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a1fe3-129">AppDomain</span></span>|<span data-ttu-id="a1fe3-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="a1fe3-130">xs:string</span></span>|<span data-ttu-id="a1fe3-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="a1fe3-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
