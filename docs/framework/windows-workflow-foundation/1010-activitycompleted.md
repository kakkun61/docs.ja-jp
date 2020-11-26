---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: d0ebf32ec1d5fe5b34ffe650d5547891be0eb665
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239914"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="41aab-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="41aab-102">1010 - ActivityCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="41aab-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="41aab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="41aab-104">ID</span><span class="sxs-lookup"><span data-stu-id="41aab-104">ID</span></span>|<span data-ttu-id="41aab-105">1010</span><span class="sxs-lookup"><span data-stu-id="41aab-105">1010</span></span>|  
|<span data-ttu-id="41aab-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="41aab-106">Keywords</span></span>|<span data-ttu-id="41aab-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="41aab-107">WFRuntime</span></span>|  
|<span data-ttu-id="41aab-108">Level</span><span class="sxs-lookup"><span data-stu-id="41aab-108">Level</span></span>|<span data-ttu-id="41aab-109">情報</span><span class="sxs-lookup"><span data-stu-id="41aab-109">Information</span></span>|  
|<span data-ttu-id="41aab-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="41aab-110">Channel</span></span>|<span data-ttu-id="41aab-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="41aab-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="41aab-112">Description</span><span class="sxs-lookup"><span data-stu-id="41aab-112">Description</span></span>  

 <span data-ttu-id="41aab-113">アクティビティが実行を完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="41aab-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="41aab-114">Message</span><span class="sxs-lookup"><span data-stu-id="41aab-114">Message</span></span>  

 <span data-ttu-id="41aab-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' が状態 '%4' で完了しました。</span><span class="sxs-lookup"><span data-stu-id="41aab-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="41aab-116">詳細</span><span class="sxs-lookup"><span data-stu-id="41aab-116">Details</span></span>  
  
|<span data-ttu-id="41aab-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="41aab-117">Data Item Name</span></span>|<span data-ttu-id="41aab-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="41aab-118">Data Item Type</span></span>|<span data-ttu-id="41aab-119">Description</span><span class="sxs-lookup"><span data-stu-id="41aab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="41aab-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="41aab-120">Activity</span></span>|<span data-ttu-id="41aab-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="41aab-121">xs:string</span></span>|<span data-ttu-id="41aab-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="41aab-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="41aab-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="41aab-123">DisplayName</span></span>|<span data-ttu-id="41aab-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="41aab-124">xs:string</span></span>|<span data-ttu-id="41aab-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="41aab-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="41aab-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="41aab-126">InstanceId</span></span>|<span data-ttu-id="41aab-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="41aab-127">xs:string</span></span>|<span data-ttu-id="41aab-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="41aab-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="41aab-129">State</span><span class="sxs-lookup"><span data-stu-id="41aab-129">State</span></span>|<span data-ttu-id="41aab-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="41aab-130">xs:string</span></span>|<span data-ttu-id="41aab-131">アクティビティの状態。</span><span class="sxs-lookup"><span data-stu-id="41aab-131">The state of the activity.</span></span>|  
|<span data-ttu-id="41aab-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="41aab-132">AppDomain</span></span>|<span data-ttu-id="41aab-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="41aab-133">xs:string</span></span>|<span data-ttu-id="41aab-134">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="41aab-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
