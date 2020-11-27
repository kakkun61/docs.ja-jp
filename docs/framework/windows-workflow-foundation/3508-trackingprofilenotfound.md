---
title: 3508 - TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 23262427c3da730eaf930a8b483c7c4d4ec3a3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289842"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="7c735-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="7c735-102">3508 - TrackingProfileNotFound</span></span>

## <a name="properties"></a><span data-ttu-id="7c735-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7c735-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7c735-104">ID</span><span class="sxs-lookup"><span data-stu-id="7c735-104">ID</span></span>|<span data-ttu-id="7c735-105">3508</span><span class="sxs-lookup"><span data-stu-id="7c735-105">3508</span></span>|  
|<span data-ttu-id="7c735-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="7c735-106">Keywords</span></span>|<span data-ttu-id="7c735-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="7c735-107">WFServices</span></span>|  
|<span data-ttu-id="7c735-108">Level</span><span class="sxs-lookup"><span data-stu-id="7c735-108">Level</span></span>|<span data-ttu-id="7c735-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="7c735-109">Verbose</span></span>|  
|<span data-ttu-id="7c735-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7c735-110">Channel</span></span>|<span data-ttu-id="7c735-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7c735-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7c735-112">Description</span><span class="sxs-lookup"><span data-stu-id="7c735-112">Description</span></span>  

 <span data-ttu-id="7c735-113">構成ファイル内に TrackingProfile がないか、または ActivityDefinitionId がプロファイルと一致していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="7c735-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7c735-114">Message</span><span class="sxs-lookup"><span data-stu-id="7c735-114">Message</span></span>  

 <span data-ttu-id="7c735-115">ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。</span><span class="sxs-lookup"><span data-stu-id="7c735-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="7c735-116">config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。</span><span class="sxs-lookup"><span data-stu-id="7c735-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7c735-117">詳細</span><span class="sxs-lookup"><span data-stu-id="7c735-117">Details</span></span>  
  
|<span data-ttu-id="7c735-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7c735-118">Data Item Name</span></span>|<span data-ttu-id="7c735-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7c735-119">Data Item Type</span></span>|<span data-ttu-id="7c735-120">Description</span><span class="sxs-lookup"><span data-stu-id="7c735-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7c735-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="7c735-121">TrackingProfile</span></span>|<span data-ttu-id="7c735-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c735-122">xs:string</span></span>|<span data-ttu-id="7c735-123">追跡プロファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="7c735-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="7c735-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="7c735-124">ActivityDefinitionId</span></span>|<span data-ttu-id="7c735-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c735-125">xs:string</span></span>|<span data-ttu-id="7c735-126">アクティビティ定義 ID。</span><span class="sxs-lookup"><span data-stu-id="7c735-126">The activity definition id.</span></span>|  
|<span data-ttu-id="7c735-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7c735-127">AppDomain</span></span>|<span data-ttu-id="7c735-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="7c735-128">xs:string</span></span>|<span data-ttu-id="7c735-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7c735-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
