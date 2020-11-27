---
title: 1033 - StartRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
ms.openlocfilehash: 46a3dc8d313ec72ac90abc2e2e333b274dad2e4c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294301"
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="29ebe-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="29ebe-102">1033 - StartRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="29ebe-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="29ebe-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29ebe-104">ID</span><span class="sxs-lookup"><span data-stu-id="29ebe-104">ID</span></span>|<span data-ttu-id="29ebe-105">1033</span><span class="sxs-lookup"><span data-stu-id="29ebe-105">1033</span></span>|  
|<span data-ttu-id="29ebe-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="29ebe-106">Keywords</span></span>|<span data-ttu-id="29ebe-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="29ebe-107">WFRuntime</span></span>|  
|<span data-ttu-id="29ebe-108">Level</span><span class="sxs-lookup"><span data-stu-id="29ebe-108">Level</span></span>|<span data-ttu-id="29ebe-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="29ebe-109">Verbose</span></span>|  
|<span data-ttu-id="29ebe-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="29ebe-110">Channel</span></span>|<span data-ttu-id="29ebe-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="29ebe-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="29ebe-112">Description</span><span class="sxs-lookup"><span data-stu-id="29ebe-112">Description</span></span>  

 <span data-ttu-id="29ebe-113">RuntimeWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="29ebe-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="29ebe-114">Message</span><span class="sxs-lookup"><span data-stu-id="29ebe-114">Message</span></span>  

 <span data-ttu-id="29ebe-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="29ebe-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="29ebe-116">詳細</span><span class="sxs-lookup"><span data-stu-id="29ebe-116">Details</span></span>  
  
|<span data-ttu-id="29ebe-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="29ebe-117">Data Item Name</span></span>|<span data-ttu-id="29ebe-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="29ebe-118">Data Item Type</span></span>|<span data-ttu-id="29ebe-119">Description</span><span class="sxs-lookup"><span data-stu-id="29ebe-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="29ebe-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="29ebe-120">Activity</span></span>|<span data-ttu-id="29ebe-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="29ebe-121">xs:string</span></span>|<span data-ttu-id="29ebe-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="29ebe-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="29ebe-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="29ebe-123">DisplayName</span></span>|<span data-ttu-id="29ebe-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="29ebe-124">xs:string</span></span>|<span data-ttu-id="29ebe-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="29ebe-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="29ebe-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="29ebe-126">InstanceId</span></span>|<span data-ttu-id="29ebe-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="29ebe-127">xs:string</span></span>|<span data-ttu-id="29ebe-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="29ebe-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="29ebe-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="29ebe-129">AppDomain</span></span>|<span data-ttu-id="29ebe-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="29ebe-130">xs:string</span></span>|<span data-ttu-id="29ebe-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="29ebe-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
