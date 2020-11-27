---
title: 39458 - TrackingRecordTruncated
ms.date: 03/30/2017
ms.assetid: 5352f0eb-d571-454a-bab5-e2162888b218
ms.openlocfilehash: f02a34673c51be6e0b127a64e4622131575d836f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275893"
---
# <a name="39458---trackingrecordtruncated"></a><span data-ttu-id="9a44e-102">39458 - TrackingRecordTruncated</span><span class="sxs-lookup"><span data-stu-id="9a44e-102">39458 - TrackingRecordTruncated</span></span>

## <a name="properties"></a><span data-ttu-id="9a44e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9a44e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a44e-104">ID</span><span class="sxs-lookup"><span data-stu-id="9a44e-104">ID</span></span>|<span data-ttu-id="9a44e-105">39458</span><span class="sxs-lookup"><span data-stu-id="9a44e-105">39458</span></span>|  
|<span data-ttu-id="9a44e-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="9a44e-106">Keywords</span></span>|<span data-ttu-id="9a44e-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="9a44e-107">WFTracking</span></span>|  
|<span data-ttu-id="9a44e-108">Level</span><span class="sxs-lookup"><span data-stu-id="9a44e-108">Level</span></span>|<span data-ttu-id="9a44e-109">警告</span><span class="sxs-lookup"><span data-stu-id="9a44e-109">Warning</span></span>|  
|<span data-ttu-id="9a44e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="9a44e-110">Channel</span></span>|<span data-ttu-id="9a44e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9a44e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a44e-112">Description</span><span class="sxs-lookup"><span data-stu-id="9a44e-112">Description</span></span>  

 <span data-ttu-id="9a44e-113">追跡レコードが省略されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="9a44e-113">Indicates a tracking record has been truncated.</span></span> <span data-ttu-id="9a44e-114">変数、注釈、ユーザー データは削除されています。</span><span class="sxs-lookup"><span data-stu-id="9a44e-114">Variables/annotations/user data have been removed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a44e-115">Message</span><span class="sxs-lookup"><span data-stu-id="9a44e-115">Message</span></span>  

 <span data-ttu-id="9a44e-116">プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。</span><span class="sxs-lookup"><span data-stu-id="9a44e-116">Truncated tracking record %1 written to ETW session with provider %2.</span></span> <span data-ttu-id="9a44e-117">変数/注釈/ユーザー データは削除されました</span><span class="sxs-lookup"><span data-stu-id="9a44e-117">Variables/annotations/user data have been removed</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a44e-118">詳細</span><span class="sxs-lookup"><span data-stu-id="9a44e-118">Details</span></span>  
  
|<span data-ttu-id="9a44e-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9a44e-119">Data Item Name</span></span>|<span data-ttu-id="9a44e-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9a44e-120">Data Item Type</span></span>|<span data-ttu-id="9a44e-121">Description</span><span class="sxs-lookup"><span data-stu-id="9a44e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a44e-122">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="9a44e-122">RecordNumber</span></span>|<span data-ttu-id="9a44e-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a44e-123">xs:string</span></span>|<span data-ttu-id="9a44e-124">追跡レコード番号。</span><span class="sxs-lookup"><span data-stu-id="9a44e-124">The tracking record number.</span></span>|  
|<span data-ttu-id="9a44e-125">ProviderId</span><span class="sxs-lookup"><span data-stu-id="9a44e-125">ProviderId</span></span>|<span data-ttu-id="9a44e-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a44e-126">xs:string</span></span>|<span data-ttu-id="9a44e-127">ETW プロバイダー ID。</span><span class="sxs-lookup"><span data-stu-id="9a44e-127">The ETW provider id.</span></span>|  
|<span data-ttu-id="9a44e-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a44e-128">AppDomain</span></span>|<span data-ttu-id="9a44e-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="9a44e-129">xs:string</span></span>|<span data-ttu-id="9a44e-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9a44e-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
