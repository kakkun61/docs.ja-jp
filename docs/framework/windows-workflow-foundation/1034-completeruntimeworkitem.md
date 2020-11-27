---
title: 1034 - CompleteRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
ms.openlocfilehash: 837adc9e143060284f2373a049bc9ad9c8cee336
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294288"
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="f05cf-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="f05cf-102">1034 - CompleteRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="f05cf-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f05cf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f05cf-104">ID</span><span class="sxs-lookup"><span data-stu-id="f05cf-104">ID</span></span>|<span data-ttu-id="f05cf-105">1034</span><span class="sxs-lookup"><span data-stu-id="f05cf-105">1034</span></span>|  
|<span data-ttu-id="f05cf-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="f05cf-106">Keywords</span></span>|<span data-ttu-id="f05cf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f05cf-107">WFRuntime</span></span>|  
|<span data-ttu-id="f05cf-108">Level</span><span class="sxs-lookup"><span data-stu-id="f05cf-108">Level</span></span>|<span data-ttu-id="f05cf-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="f05cf-109">Verbose</span></span>|  
|<span data-ttu-id="f05cf-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f05cf-110">Channel</span></span>|<span data-ttu-id="f05cf-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f05cf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f05cf-112">Description</span><span class="sxs-lookup"><span data-stu-id="f05cf-112">Description</span></span>  

 <span data-ttu-id="f05cf-113">RuntimeWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="f05cf-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f05cf-114">Message</span><span class="sxs-lookup"><span data-stu-id="f05cf-114">Message</span></span>  

 <span data-ttu-id="f05cf-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目が完了しました。</span><span class="sxs-lookup"><span data-stu-id="f05cf-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f05cf-116">詳細</span><span class="sxs-lookup"><span data-stu-id="f05cf-116">Details</span></span>  
  
|<span data-ttu-id="f05cf-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f05cf-117">Data Item Name</span></span>|<span data-ttu-id="f05cf-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f05cf-118">Data Item Type</span></span>|<span data-ttu-id="f05cf-119">Description</span><span class="sxs-lookup"><span data-stu-id="f05cf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f05cf-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="f05cf-120">Activity</span></span>|<span data-ttu-id="f05cf-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f05cf-121">xs:string</span></span>|<span data-ttu-id="f05cf-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="f05cf-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f05cf-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f05cf-123">DisplayName</span></span>|<span data-ttu-id="f05cf-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f05cf-124">xs:string</span></span>|<span data-ttu-id="f05cf-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="f05cf-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f05cf-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f05cf-126">InstanceId</span></span>|<span data-ttu-id="f05cf-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f05cf-127">xs:string</span></span>|<span data-ttu-id="f05cf-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="f05cf-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f05cf-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f05cf-129">AppDomain</span></span>|<span data-ttu-id="f05cf-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f05cf-130">xs:string</span></span>|<span data-ttu-id="f05cf-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f05cf-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
