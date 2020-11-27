---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ff8a1e099934f5bf71fef0afbb7e54c0d1851fae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267183"
---
# <a name="4211---queuingsqlretry"></a><span data-ttu-id="e196e-102">4211 - QueuingSqlRetry</span><span class="sxs-lookup"><span data-stu-id="e196e-102">4211 - QueuingSqlRetry</span></span>

## <a name="properties"></a><span data-ttu-id="e196e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e196e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e196e-104">ID</span><span class="sxs-lookup"><span data-stu-id="e196e-104">ID</span></span>|<span data-ttu-id="e196e-105">4211</span><span class="sxs-lookup"><span data-stu-id="e196e-105">4211</span></span>|  
|<span data-ttu-id="e196e-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="e196e-106">Keywords</span></span>|<span data-ttu-id="e196e-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="e196e-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="e196e-108">Level</span><span class="sxs-lookup"><span data-stu-id="e196e-108">Level</span></span>|<span data-ttu-id="e196e-109">警告</span><span class="sxs-lookup"><span data-stu-id="e196e-109">Warning</span></span>|  
|<span data-ttu-id="e196e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e196e-110">Channel</span></span>|<span data-ttu-id="e196e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e196e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e196e-112">Description</span><span class="sxs-lookup"><span data-stu-id="e196e-112">Description</span></span>  

 <span data-ttu-id="e196e-113">SQL の再試行をキューに登録していることを示します。</span><span class="sxs-lookup"><span data-stu-id="e196e-113">Indicates queuing SQL retry.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e196e-114">Message</span><span class="sxs-lookup"><span data-stu-id="e196e-114">Message</span></span>  

 <span data-ttu-id="e196e-115">%1 ミリ秒の遅延で SQL の再試行をキューに登録しています。</span><span class="sxs-lookup"><span data-stu-id="e196e-115">Queuing SQL retry with delay %1 milliseconds.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e196e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="e196e-116">Details</span></span>  
  
|<span data-ttu-id="e196e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e196e-117">Data Item Name</span></span>|<span data-ttu-id="e196e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e196e-118">Data Item Type</span></span>|<span data-ttu-id="e196e-119">Description</span><span class="sxs-lookup"><span data-stu-id="e196e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e196e-120">遅延</span><span class="sxs-lookup"><span data-stu-id="e196e-120">Delay</span></span>|<span data-ttu-id="e196e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e196e-121">xs:string</span></span>|<span data-ttu-id="e196e-122">再試行間の遅延。</span><span class="sxs-lookup"><span data-stu-id="e196e-122">The delay between retries.</span></span>|  
|<span data-ttu-id="e196e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e196e-123">AppDomain</span></span>|<span data-ttu-id="e196e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e196e-124">xs:string</span></span>|<span data-ttu-id="e196e-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e196e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
