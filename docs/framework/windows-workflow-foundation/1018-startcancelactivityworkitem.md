---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: c1558e19b0de2dc5d22d4356b0f80c35e5b4fbc1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275506"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="3d7ae-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="3d7ae-102">1018 - StartCancelActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="3d7ae-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3d7ae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d7ae-104">ID</span><span class="sxs-lookup"><span data-stu-id="3d7ae-104">ID</span></span>|<span data-ttu-id="3d7ae-105">1018</span><span class="sxs-lookup"><span data-stu-id="3d7ae-105">1018</span></span>|  
|<span data-ttu-id="3d7ae-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="3d7ae-106">Keywords</span></span>|<span data-ttu-id="3d7ae-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3d7ae-107">WFRuntime</span></span>|  
|<span data-ttu-id="3d7ae-108">Level</span><span class="sxs-lookup"><span data-stu-id="3d7ae-108">Level</span></span>|<span data-ttu-id="3d7ae-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="3d7ae-109">Verbose</span></span>|  
|<span data-ttu-id="3d7ae-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="3d7ae-110">Channel</span></span>|<span data-ttu-id="3d7ae-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="3d7ae-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d7ae-112">Description</span><span class="sxs-lookup"><span data-stu-id="3d7ae-112">Description</span></span>  

 <span data-ttu-id="3d7ae-113">CancelActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="3d7ae-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d7ae-114">Message</span><span class="sxs-lookup"><span data-stu-id="3d7ae-114">Message</span></span>  

 <span data-ttu-id="3d7ae-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="3d7ae-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d7ae-116">詳細</span><span class="sxs-lookup"><span data-stu-id="3d7ae-116">Details</span></span>  
  
|<span data-ttu-id="3d7ae-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3d7ae-117">Data Item Name</span></span>|<span data-ttu-id="3d7ae-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3d7ae-118">Data Item Type</span></span>|<span data-ttu-id="3d7ae-119">Description</span><span class="sxs-lookup"><span data-stu-id="3d7ae-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d7ae-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="3d7ae-120">Activity</span></span>|<span data-ttu-id="3d7ae-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d7ae-121">xs:string</span></span>|<span data-ttu-id="3d7ae-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="3d7ae-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3d7ae-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="3d7ae-123">DisplayName</span></span>|<span data-ttu-id="3d7ae-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d7ae-124">xs:string</span></span>|<span data-ttu-id="3d7ae-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="3d7ae-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3d7ae-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="3d7ae-126">InstanceId</span></span>|<span data-ttu-id="3d7ae-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d7ae-127">xs:string</span></span>|<span data-ttu-id="3d7ae-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="3d7ae-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3d7ae-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3d7ae-129">AppDomain</span></span>|<span data-ttu-id="3d7ae-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="3d7ae-130">xs:string</span></span>|<span data-ttu-id="3d7ae-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3d7ae-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
