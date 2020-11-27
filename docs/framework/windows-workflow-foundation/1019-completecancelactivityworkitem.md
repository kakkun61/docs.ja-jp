---
title: 1019 - CompleteCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
ms.openlocfilehash: 903b497fb3f244fd40c6888829ef71dddd455251
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275480"
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="d1dc2-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="d1dc2-102">1019 - CompleteCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="d1dc2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d1dc2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d1dc2-104">ID</span><span class="sxs-lookup"><span data-stu-id="d1dc2-104">ID</span></span>|<span data-ttu-id="d1dc2-105">1019</span><span class="sxs-lookup"><span data-stu-id="d1dc2-105">1019</span></span>|  
|<span data-ttu-id="d1dc2-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="d1dc2-106">Keywords</span></span>|<span data-ttu-id="d1dc2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d1dc2-107">WFRuntime</span></span>|  
|<span data-ttu-id="d1dc2-108">Level</span><span class="sxs-lookup"><span data-stu-id="d1dc2-108">Level</span></span>|<span data-ttu-id="d1dc2-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="d1dc2-109">Verbose</span></span>|  
|<span data-ttu-id="d1dc2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d1dc2-110">Channel</span></span>|<span data-ttu-id="d1dc2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d1dc2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d1dc2-112">Description</span><span class="sxs-lookup"><span data-stu-id="d1dc2-112">Description</span></span>  

 <span data-ttu-id="d1dc2-113">CancelActivityWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d1dc2-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d1dc2-114">Message</span><span class="sxs-lookup"><span data-stu-id="d1dc2-114">Message</span></span>  

 <span data-ttu-id="d1dc2-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d1dc2-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d1dc2-116">詳細</span><span class="sxs-lookup"><span data-stu-id="d1dc2-116">Details</span></span>  
  
|<span data-ttu-id="d1dc2-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d1dc2-117">Data Item Name</span></span>|<span data-ttu-id="d1dc2-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d1dc2-118">Data Item Type</span></span>|<span data-ttu-id="d1dc2-119">Description</span><span class="sxs-lookup"><span data-stu-id="d1dc2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d1dc2-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="d1dc2-120">Activity</span></span>|<span data-ttu-id="d1dc2-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1dc2-121">xs:string</span></span>|<span data-ttu-id="d1dc2-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="d1dc2-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d1dc2-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="d1dc2-123">DisplayName</span></span>|<span data-ttu-id="d1dc2-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1dc2-124">xs:string</span></span>|<span data-ttu-id="d1dc2-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="d1dc2-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d1dc2-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="d1dc2-126">InstanceId</span></span>|<span data-ttu-id="d1dc2-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1dc2-127">xs:string</span></span>|<span data-ttu-id="d1dc2-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="d1dc2-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d1dc2-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d1dc2-129">AppDomain</span></span>|<span data-ttu-id="d1dc2-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="d1dc2-130">xs:string</span></span>|<span data-ttu-id="d1dc2-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d1dc2-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
