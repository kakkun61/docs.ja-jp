---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: b8bf8431c4e2b82c6aac95820eb45de2a404e976
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294275"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="4b96e-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="4b96e-102">1035 - RuntimeTransactionSet</span></span>

## <a name="properties"></a><span data-ttu-id="4b96e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4b96e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b96e-104">ID</span><span class="sxs-lookup"><span data-stu-id="4b96e-104">ID</span></span>|<span data-ttu-id="4b96e-105">1035</span><span class="sxs-lookup"><span data-stu-id="4b96e-105">1035</span></span>|  
|<span data-ttu-id="4b96e-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="4b96e-106">Keywords</span></span>|<span data-ttu-id="4b96e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4b96e-107">WFRuntime</span></span>|  
|<span data-ttu-id="4b96e-108">Level</span><span class="sxs-lookup"><span data-stu-id="4b96e-108">Level</span></span>|<span data-ttu-id="4b96e-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="4b96e-109">Verbose</span></span>|  
|<span data-ttu-id="4b96e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="4b96e-110">Channel</span></span>|<span data-ttu-id="4b96e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4b96e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4b96e-112">Description</span><span class="sxs-lookup"><span data-stu-id="4b96e-112">Description</span></span>  

 <span data-ttu-id="4b96e-113">アクティビティがランタイムのトランザクションを設定したことを示します。</span><span class="sxs-lookup"><span data-stu-id="4b96e-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4b96e-114">Message</span><span class="sxs-lookup"><span data-stu-id="4b96e-114">Message</span></span>  

 <span data-ttu-id="4b96e-115">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' によってランタイムトランザクションが設定されました。</span><span class="sxs-lookup"><span data-stu-id="4b96e-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="4b96e-116">実行がアクティビティ ' %4 '、DisplayName: ' %5 '、InstanceId: ' %6 ' に分離されています。</span><span class="sxs-lookup"><span data-stu-id="4b96e-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4b96e-117">詳細</span><span class="sxs-lookup"><span data-stu-id="4b96e-117">Details</span></span>  
  
|<span data-ttu-id="4b96e-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4b96e-118">Data Item Name</span></span>|<span data-ttu-id="4b96e-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4b96e-119">Data Item Type</span></span>|<span data-ttu-id="4b96e-120">Description</span><span class="sxs-lookup"><span data-stu-id="4b96e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4b96e-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="4b96e-121">Activity</span></span>|<span data-ttu-id="4b96e-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b96e-122">xs:string</span></span>|<span data-ttu-id="4b96e-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="4b96e-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="4b96e-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="4b96e-124">DisplayName</span></span>|<span data-ttu-id="4b96e-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b96e-125">xs:string</span></span>|<span data-ttu-id="4b96e-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4b96e-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="4b96e-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="4b96e-127">InstanceId</span></span>|<span data-ttu-id="4b96e-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b96e-128">xs:string</span></span>|<span data-ttu-id="4b96e-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="4b96e-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4b96e-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="4b96e-130">IsolatedActivity</span></span>|<span data-ttu-id="4b96e-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b96e-131">xs:string</span></span>|<span data-ttu-id="4b96e-132">トランザクションが分離されるアクティビティの型の名前。</span><span class="sxs-lookup"><span data-stu-id="4b96e-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="4b96e-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="4b96e-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="4b96e-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b96e-134">xs:string</span></span>|<span data-ttu-id="4b96e-135">トランザクションが分離されるアクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="4b96e-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="4b96e-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="4b96e-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="4b96e-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b96e-137">xs:string</span></span>|<span data-ttu-id="4b96e-138">トランザクションが分離されるアクティビティのインスタンスの ID。</span><span class="sxs-lookup"><span data-stu-id="4b96e-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="4b96e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4b96e-139">AppDomain</span></span>|<span data-ttu-id="4b96e-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="4b96e-140">xs:string</span></span>|<span data-ttu-id="4b96e-141">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4b96e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
