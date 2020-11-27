---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: 33c68984e88eaa5e3028899a7c3066c94a65e8eb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96271240"
---
# <a name="2577---trycatchexceptionduringcancelation"></a><span data-ttu-id="0f531-102">2577 - TryCatchExceptionDuringCancelation</span><span class="sxs-lookup"><span data-stu-id="0f531-102">2577 - TryCatchExceptionDuringCancelation</span></span>

## <a name="properties"></a><span data-ttu-id="0f531-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0f531-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f531-104">ID</span><span class="sxs-lookup"><span data-stu-id="0f531-104">ID</span></span>|<span data-ttu-id="0f531-105">2577</span><span class="sxs-lookup"><span data-stu-id="0f531-105">2577</span></span>|  
|<span data-ttu-id="0f531-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="0f531-106">Keywords</span></span>|<span data-ttu-id="0f531-107">WFActivities</span><span class="sxs-lookup"><span data-stu-id="0f531-107">WFActivities</span></span>|  
|<span data-ttu-id="0f531-108">Level</span><span class="sxs-lookup"><span data-stu-id="0f531-108">Level</span></span>|<span data-ttu-id="0f531-109">警告</span><span class="sxs-lookup"><span data-stu-id="0f531-109">Warning</span></span>|  
|<span data-ttu-id="0f531-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0f531-110">Channel</span></span>|<span data-ttu-id="0f531-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0f531-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0f531-112">Description</span><span class="sxs-lookup"><span data-stu-id="0f531-112">Description</span></span>  

 <span data-ttu-id="0f531-113">TryCatch アクティビティの子アクティビティが取り消し中に例外をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="0f531-113">Indicates a child activity of the TryCatch activity has thrown an exception during cancelation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0f531-114">Message</span><span class="sxs-lookup"><span data-stu-id="0f531-114">Message</span></span>  

 <span data-ttu-id="0f531-115">TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。</span><span class="sxs-lookup"><span data-stu-id="0f531-115">A child activity of the TryCatch activity '%1' has thrown an exception during cancelation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0f531-116">詳細</span><span class="sxs-lookup"><span data-stu-id="0f531-116">Details</span></span>  
  
|<span data-ttu-id="0f531-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0f531-117">Data Item Name</span></span>|<span data-ttu-id="0f531-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0f531-118">Data Item Type</span></span>|<span data-ttu-id="0f531-119">Description</span><span class="sxs-lookup"><span data-stu-id="0f531-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0f531-120">DisplayName</span><span class="sxs-lookup"><span data-stu-id="0f531-120">DisplayName</span></span>|<span data-ttu-id="0f531-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="0f531-121">xs:string</span></span>|<span data-ttu-id="0f531-122">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="0f531-122">The display name of the activity.</span></span>|  
|<span data-ttu-id="0f531-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0f531-123">AppDomain</span></span>|<span data-ttu-id="0f531-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="0f531-124">xs:string</span></span>|<span data-ttu-id="0f531-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0f531-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
