---
title: 1020 - CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 8c9c20fd4fb74f80779c1d2ef8f29ac3d44050d9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275376"
---
# <a name="1020---createbookmark"></a><span data-ttu-id="11d03-102">1020 - CreateBookmark</span><span class="sxs-lookup"><span data-stu-id="11d03-102">1020 - CreateBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="11d03-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="11d03-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="11d03-104">ID</span><span class="sxs-lookup"><span data-stu-id="11d03-104">ID</span></span>|<span data-ttu-id="11d03-105">1020</span><span class="sxs-lookup"><span data-stu-id="11d03-105">1020</span></span>|  
|<span data-ttu-id="11d03-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="11d03-106">Keywords</span></span>|<span data-ttu-id="11d03-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="11d03-107">WFRuntime</span></span>|  
|<span data-ttu-id="11d03-108">Level</span><span class="sxs-lookup"><span data-stu-id="11d03-108">Level</span></span>|<span data-ttu-id="11d03-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="11d03-109">Verbose</span></span>|  
|<span data-ttu-id="11d03-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="11d03-110">Channel</span></span>|<span data-ttu-id="11d03-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="11d03-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="11d03-112">Description</span><span class="sxs-lookup"><span data-stu-id="11d03-112">Description</span></span>  

 <span data-ttu-id="11d03-113">あるアクティビティ用のブックマークが作成されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="11d03-113">Indicates a bookmark has been created for an activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="11d03-114">Message</span><span class="sxs-lookup"><span data-stu-id="11d03-114">Message</span></span>  

 <span data-ttu-id="11d03-115">Activity ' %1 '、DisplayName: ' %2 '、InstanceId: ' %3 ' のブックマークが作成されました。</span><span class="sxs-lookup"><span data-stu-id="11d03-115">A Bookmark has been created for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="11d03-116">BookmarkName: %4、BookmarkScope: %5。</span><span class="sxs-lookup"><span data-stu-id="11d03-116">BookmarkName: %4, BookmarkScope: %5.</span></span>  
  
## <a name="details"></a><span data-ttu-id="11d03-117">詳細</span><span class="sxs-lookup"><span data-stu-id="11d03-117">Details</span></span>  
  
|<span data-ttu-id="11d03-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="11d03-118">Data Item Name</span></span>|<span data-ttu-id="11d03-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="11d03-119">Data Item Type</span></span>|<span data-ttu-id="11d03-120">Description</span><span class="sxs-lookup"><span data-stu-id="11d03-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="11d03-121">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="11d03-121">Activity</span></span>|<span data-ttu-id="11d03-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="11d03-122">xs:string</span></span>|<span data-ttu-id="11d03-123">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="11d03-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="11d03-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="11d03-124">DisplayName</span></span>|<span data-ttu-id="11d03-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="11d03-125">xs:string</span></span>|<span data-ttu-id="11d03-126">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="11d03-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="11d03-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="11d03-127">InstanceId</span></span>|<span data-ttu-id="11d03-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="11d03-128">xs:string</span></span>|<span data-ttu-id="11d03-129">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="11d03-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="11d03-130">BookmarkName</span><span class="sxs-lookup"><span data-stu-id="11d03-130">BookmarkName</span></span>|<span data-ttu-id="11d03-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="11d03-131">xs:string</span></span>|<span data-ttu-id="11d03-132">ブックマークの名前。</span><span class="sxs-lookup"><span data-stu-id="11d03-132">The name of the bookmark.</span></span>|  
|<span data-ttu-id="11d03-133">BookmarkScope</span><span class="sxs-lookup"><span data-stu-id="11d03-133">BookmarkScope</span></span>|<span data-ttu-id="11d03-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="11d03-134">xs:string</span></span>|<span data-ttu-id="11d03-135">ブックマークのスコープ。</span><span class="sxs-lookup"><span data-stu-id="11d03-135">The scope of the bookmark.</span></span>|  
|<span data-ttu-id="11d03-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="11d03-136">AppDomain</span></span>|<span data-ttu-id="11d03-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="11d03-137">xs:string</span></span>|<span data-ttu-id="11d03-138">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="11d03-138">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
