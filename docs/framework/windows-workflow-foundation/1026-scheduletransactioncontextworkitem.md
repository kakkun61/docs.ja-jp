---
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 7ba2ada1fbd5217592b4e4e3cffd813ffbe978ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275246"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="24be9-102">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="24be9-102">1026 - ScheduleTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="24be9-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="24be9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24be9-104">ID</span><span class="sxs-lookup"><span data-stu-id="24be9-104">ID</span></span>|<span data-ttu-id="24be9-105">1026</span><span class="sxs-lookup"><span data-stu-id="24be9-105">1026</span></span>|  
|<span data-ttu-id="24be9-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="24be9-106">Keywords</span></span>|<span data-ttu-id="24be9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="24be9-107">WFRuntime</span></span>|  
|<span data-ttu-id="24be9-108">Level</span><span class="sxs-lookup"><span data-stu-id="24be9-108">Level</span></span>|<span data-ttu-id="24be9-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="24be9-109">Verbose</span></span>|  
|<span data-ttu-id="24be9-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="24be9-110">Channel</span></span>|<span data-ttu-id="24be9-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="24be9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="24be9-112">Description</span><span class="sxs-lookup"><span data-stu-id="24be9-112">Description</span></span>  

 <span data-ttu-id="24be9-113">TransactionContextWorkItem がスケジュールされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="24be9-113">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="24be9-114">Message</span><span class="sxs-lookup"><span data-stu-id="24be9-114">Message</span></span>  

 <span data-ttu-id="24be9-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して TransactionContextWorkItem がスケジュールされました。</span><span class="sxs-lookup"><span data-stu-id="24be9-115">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="24be9-116">詳細</span><span class="sxs-lookup"><span data-stu-id="24be9-116">Details</span></span>  
  
|<span data-ttu-id="24be9-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="24be9-117">Data Item Name</span></span>|<span data-ttu-id="24be9-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="24be9-118">Data Item Type</span></span>|<span data-ttu-id="24be9-119">Description</span><span class="sxs-lookup"><span data-stu-id="24be9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="24be9-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="24be9-120">Activity</span></span>|<span data-ttu-id="24be9-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="24be9-121">xs:string</span></span>|<span data-ttu-id="24be9-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="24be9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="24be9-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="24be9-123">DisplayName</span></span>|<span data-ttu-id="24be9-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="24be9-124">xs:string</span></span>|<span data-ttu-id="24be9-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="24be9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="24be9-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="24be9-126">InstanceId</span></span>|<span data-ttu-id="24be9-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="24be9-127">xs:string</span></span>|<span data-ttu-id="24be9-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="24be9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="24be9-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="24be9-129">AppDomain</span></span>|<span data-ttu-id="24be9-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="24be9-130">xs:string</span></span>|<span data-ttu-id="24be9-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="24be9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
