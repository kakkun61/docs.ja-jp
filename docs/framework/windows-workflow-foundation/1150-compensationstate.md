---
title: 1150 - CompensationState
ms.date: 03/30/2017
ms.assetid: eb015842-cc5a-47be-bce5-6af39e567723
ms.openlocfilehash: 2adb317521b8659c2419e4c04aabf4cf4499b36f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285110"
---
# <a name="1150---compensationstate"></a><span data-ttu-id="c9093-102">1150 - CompensationState</span><span class="sxs-lookup"><span data-stu-id="c9093-102">1150 - CompensationState</span></span>

## <a name="properties"></a><span data-ttu-id="c9093-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c9093-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9093-104">ID</span><span class="sxs-lookup"><span data-stu-id="c9093-104">ID</span></span>|<span data-ttu-id="c9093-105">1150</span><span class="sxs-lookup"><span data-stu-id="c9093-105">1150</span></span>|  
|<span data-ttu-id="c9093-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="c9093-106">Keywords</span></span>|<span data-ttu-id="c9093-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="c9093-107">WFActivities</span></span>|  
|<span data-ttu-id="c9093-108">Level</span><span class="sxs-lookup"><span data-stu-id="c9093-108">Level</span></span>|<span data-ttu-id="c9093-109">情報</span><span class="sxs-lookup"><span data-stu-id="c9093-109">Information</span></span>|  
|<span data-ttu-id="c9093-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c9093-110">Channel</span></span>|<span data-ttu-id="c9093-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c9093-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9093-112">Description</span><span class="sxs-lookup"><span data-stu-id="c9093-112">Description</span></span>  

 <span data-ttu-id="c9093-113">CompensableActivity の状態の変更を示します。</span><span class="sxs-lookup"><span data-stu-id="c9093-113">Indicates a change of state in a CompensableActivity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9093-114">Message</span><span class="sxs-lookup"><span data-stu-id="c9093-114">Message</span></span>  

 <span data-ttu-id="c9093-115">CompensableActivity '%1' は '%2' 状態です。</span><span class="sxs-lookup"><span data-stu-id="c9093-115">CompensableActivity '%1' is in the '%2' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9093-116">詳細</span><span class="sxs-lookup"><span data-stu-id="c9093-116">Details</span></span>  
  
|<span data-ttu-id="c9093-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c9093-117">Data Item Name</span></span>|<span data-ttu-id="c9093-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c9093-118">Data Item Type</span></span>|<span data-ttu-id="c9093-119">Description</span><span class="sxs-lookup"><span data-stu-id="c9093-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9093-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c9093-120">DisplayName</span></span>|<span data-ttu-id="c9093-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9093-121">xs:string</span></span>|<span data-ttu-id="c9093-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="c9093-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="c9093-123">State</span><span class="sxs-lookup"><span data-stu-id="c9093-123">State</span></span>|<span data-ttu-id="c9093-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9093-124">xs:string</span></span>|<span data-ttu-id="c9093-125">補正の状態。</span><span class="sxs-lookup"><span data-stu-id="c9093-125">The compensation state.</span></span>|  
|<span data-ttu-id="c9093-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9093-126">AppDomain</span></span>|<span data-ttu-id="c9093-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c9093-127">xs:string</span></span>|<span data-ttu-id="c9093-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c9093-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
