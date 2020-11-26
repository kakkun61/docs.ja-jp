---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: b9cfceb12d56f93c0f9726849e34f4333f1399ac
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239641"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="f9c00-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="f9c00-102">1012 - StartExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="f9c00-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f9c00-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9c00-104">ID</span><span class="sxs-lookup"><span data-stu-id="f9c00-104">ID</span></span>|<span data-ttu-id="f9c00-105">1012</span><span class="sxs-lookup"><span data-stu-id="f9c00-105">1012</span></span>|  
|<span data-ttu-id="f9c00-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="f9c00-106">Keywords</span></span>|<span data-ttu-id="f9c00-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f9c00-107">WFRuntime</span></span>|  
|<span data-ttu-id="f9c00-108">Level</span><span class="sxs-lookup"><span data-stu-id="f9c00-108">Level</span></span>|<span data-ttu-id="f9c00-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="f9c00-109">Verbose</span></span>|  
|<span data-ttu-id="f9c00-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f9c00-110">Channel</span></span>|<span data-ttu-id="f9c00-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f9c00-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f9c00-112">Description</span><span class="sxs-lookup"><span data-stu-id="f9c00-112">Description</span></span>  

 <span data-ttu-id="f9c00-113">ExecuteActivityWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="f9c00-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f9c00-114">Message</span><span class="sxs-lookup"><span data-stu-id="f9c00-114">Message</span></span>  

 <span data-ttu-id="f9c00-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="f9c00-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f9c00-116">詳細</span><span class="sxs-lookup"><span data-stu-id="f9c00-116">Details</span></span>  
  
|<span data-ttu-id="f9c00-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f9c00-117">Data Item Name</span></span>|<span data-ttu-id="f9c00-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f9c00-118">Data Item Type</span></span>|<span data-ttu-id="f9c00-119">Description</span><span class="sxs-lookup"><span data-stu-id="f9c00-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f9c00-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="f9c00-120">Activity</span></span>|<span data-ttu-id="f9c00-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="f9c00-121">xs:string</span></span>|<span data-ttu-id="f9c00-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="f9c00-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f9c00-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="f9c00-123">DisplayName</span></span>|<span data-ttu-id="f9c00-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="f9c00-124">xs:string</span></span>|<span data-ttu-id="f9c00-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="f9c00-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f9c00-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="f9c00-126">InstanceId</span></span>|<span data-ttu-id="f9c00-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="f9c00-127">xs:string</span></span>|<span data-ttu-id="f9c00-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="f9c00-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f9c00-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f9c00-129">AppDomain</span></span>|<span data-ttu-id="f9c00-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="f9c00-130">xs:string</span></span>|<span data-ttu-id="f9c00-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f9c00-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
