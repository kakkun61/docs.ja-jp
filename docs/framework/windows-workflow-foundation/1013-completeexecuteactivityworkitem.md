---
title: 1013 - CompleteExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
ms.openlocfilehash: 654f961088c371ab53e4a81f40e3c63335efb1a8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239589"
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="c839e-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="c839e-102">1013 - CompleteExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="c839e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c839e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c839e-104">ID</span><span class="sxs-lookup"><span data-stu-id="c839e-104">ID</span></span>|<span data-ttu-id="c839e-105">1013</span><span class="sxs-lookup"><span data-stu-id="c839e-105">1013</span></span>|  
|<span data-ttu-id="c839e-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="c839e-106">Keywords</span></span>|<span data-ttu-id="c839e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c839e-107">WFRuntime</span></span>|  
|<span data-ttu-id="c839e-108">Level</span><span class="sxs-lookup"><span data-stu-id="c839e-108">Level</span></span>|<span data-ttu-id="c839e-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="c839e-109">Verbose</span></span>|  
|<span data-ttu-id="c839e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c839e-110">Channel</span></span>|<span data-ttu-id="c839e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c839e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c839e-112">Description</span><span class="sxs-lookup"><span data-stu-id="c839e-112">Description</span></span>  

 <span data-ttu-id="c839e-113">ExecuteActivityWorkItem が完了したことを示します</span><span class="sxs-lookup"><span data-stu-id="c839e-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="c839e-114">Message</span><span class="sxs-lookup"><span data-stu-id="c839e-114">Message</span></span>  

 <span data-ttu-id="c839e-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="c839e-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c839e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="c839e-116">Details</span></span>  
  
|<span data-ttu-id="c839e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c839e-117">Data Item Name</span></span>|<span data-ttu-id="c839e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c839e-118">Data Item Type</span></span>|<span data-ttu-id="c839e-119">Description</span><span class="sxs-lookup"><span data-stu-id="c839e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c839e-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="c839e-120">Activity</span></span>|<span data-ttu-id="c839e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c839e-121">xs:string</span></span>|<span data-ttu-id="c839e-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="c839e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c839e-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c839e-123">DisplayName</span></span>|<span data-ttu-id="c839e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c839e-124">xs:string</span></span>|<span data-ttu-id="c839e-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c839e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c839e-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c839e-126">InstanceId</span></span>|<span data-ttu-id="c839e-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c839e-127">xs:string</span></span>|<span data-ttu-id="c839e-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="c839e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c839e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c839e-129">AppDomain</span></span>|<span data-ttu-id="c839e-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c839e-130">xs:string</span></span>|<span data-ttu-id="c839e-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c839e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
