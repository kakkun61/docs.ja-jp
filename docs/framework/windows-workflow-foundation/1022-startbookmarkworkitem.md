---
title: 1022 - StartBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
ms.openlocfilehash: ca1f4244fb1a5144cb2d86eaacb9b31137d317c2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275337"
---
# <a name="1022---startbookmarkworkitem"></a><span data-ttu-id="de6e2-102">1022 - StartBookmarkWorkItem</span><span class="sxs-lookup"><span data-stu-id="de6e2-102">1022 - StartBookmarkWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="de6e2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="de6e2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="de6e2-104">ID</span><span class="sxs-lookup"><span data-stu-id="de6e2-104">ID</span></span>|<span data-ttu-id="de6e2-105">1022</span><span class="sxs-lookup"><span data-stu-id="de6e2-105">1022</span></span>|  
|<span data-ttu-id="de6e2-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="de6e2-106">Keywords</span></span>|<span data-ttu-id="de6e2-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="de6e2-107">WFRuntime</span></span>|  
|<span data-ttu-id="de6e2-108">Level</span><span class="sxs-lookup"><span data-stu-id="de6e2-108">Level</span></span>|<span data-ttu-id="de6e2-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="de6e2-109">Verbose</span></span>|  
|<span data-ttu-id="de6e2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="de6e2-110">Channel</span></span>|<span data-ttu-id="de6e2-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="de6e2-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="de6e2-112">Description</span><span class="sxs-lookup"><span data-stu-id="de6e2-112">Description</span></span>  

 <span data-ttu-id="de6e2-113">BookmarkWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="de6e2-113">Indicates a BookmarkWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="de6e2-114">Message</span><span class="sxs-lookup"><span data-stu-id="de6e2-114">Message</span></span>  

 <span data-ttu-id="de6e2-115">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' の BookmarkWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="de6e2-115">Starting execution of a BookmarkWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="de6e2-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="de6e2-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="de6e2-117">詳細</span><span class="sxs-lookup"><span data-stu-id="de6e2-117">Details</span></span>  
  
|<span data-ttu-id="de6e2-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="de6e2-118">Data Item Name</span></span>|<span data-ttu-id="de6e2-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="de6e2-119">Data Item Type</span></span>|<span data-ttu-id="de6e2-120">Description</span><span class="sxs-lookup"><span data-stu-id="de6e2-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="de6e2-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="de6e2-121">Activity</span></span>|<span data-ttu-id="de6e2-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="de6e2-122">xs:string</span></span>|<span data-ttu-id="de6e2-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="de6e2-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="de6e2-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="de6e2-124">DisplayName</span></span>|<span data-ttu-id="de6e2-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="de6e2-125">xs:string</span></span>|<span data-ttu-id="de6e2-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="de6e2-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="de6e2-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="de6e2-127">InstanceId</span></span>|<span data-ttu-id="de6e2-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="de6e2-128">xs:string</span></span>|<span data-ttu-id="de6e2-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="de6e2-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="de6e2-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="de6e2-130">BookmarkName</span></span>|<span data-ttu-id="de6e2-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="de6e2-131">xs:string</span></span>|<span data-ttu-id="de6e2-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="de6e2-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="de6e2-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="de6e2-133">BookmarkScope</span></span>|<span data-ttu-id="de6e2-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="de6e2-134">xs:string</span></span>|<span data-ttu-id="de6e2-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="de6e2-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="de6e2-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="de6e2-136">AppDomain</span></span>|<span data-ttu-id="de6e2-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="de6e2-137">xs:string</span></span>|<span data-ttu-id="de6e2-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="de6e2-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
