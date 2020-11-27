---
title: 4212 - LockRetryTimeout
ms.date: 03/30/2017
ms.assetid: d4ad415a-9871-49fc-85b8-8ee2ea149b1d
ms.openlocfilehash: 43ec434064f768fc976232c6d3013f17c80fe053
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267170"
---
# <a name="4212---lockretrytimeout"></a><span data-ttu-id="0426d-102">4212 - LockRetryTimeout</span><span class="sxs-lookup"><span data-stu-id="0426d-102">4212 - LockRetryTimeout</span></span>

## <a name="properties"></a><span data-ttu-id="0426d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0426d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0426d-104">ID</span><span class="sxs-lookup"><span data-stu-id="0426d-104">ID</span></span>|<span data-ttu-id="0426d-105">4212</span><span class="sxs-lookup"><span data-stu-id="0426d-105">4212</span></span>|  
|<span data-ttu-id="0426d-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="0426d-106">Keywords</span></span>|<span data-ttu-id="0426d-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="0426d-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="0426d-108">Level</span><span class="sxs-lookup"><span data-stu-id="0426d-108">Level</span></span>|<span data-ttu-id="0426d-109">警告</span><span class="sxs-lookup"><span data-stu-id="0426d-109">Warning</span></span>|  
|<span data-ttu-id="0426d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0426d-110">Channel</span></span>|<span data-ttu-id="0426d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="0426d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0426d-112">Description</span><span class="sxs-lookup"><span data-stu-id="0426d-112">Description</span></span>  

 <span data-ttu-id="0426d-113">SQL プロバイダーはインスタンス ロックを取得しようとしてタイムアウトを検出しました。</span><span class="sxs-lookup"><span data-stu-id="0426d-113">SQL provider encountered a timeout trying to acquire the instance lock.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0426d-114">Message</span><span class="sxs-lookup"><span data-stu-id="0426d-114">Message</span></span>  

 <span data-ttu-id="0426d-115">インスタンスのロックを取得しようとしてタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0426d-115">Timeout trying to acquire the instance lock.</span></span>  <span data-ttu-id="0426d-116">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="0426d-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="0426d-117">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0426d-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0426d-118">詳細</span><span class="sxs-lookup"><span data-stu-id="0426d-118">Details</span></span>  
  
|<span data-ttu-id="0426d-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0426d-119">Data Item Name</span></span>|<span data-ttu-id="0426d-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0426d-120">Data Item Type</span></span>|<span data-ttu-id="0426d-121">Description</span><span class="sxs-lookup"><span data-stu-id="0426d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0426d-122">遅延</span><span class="sxs-lookup"><span data-stu-id="0426d-122">Delay</span></span>|<span data-ttu-id="0426d-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="0426d-123">xs:string</span></span>|<span data-ttu-id="0426d-124">再試行間の遅延。</span><span class="sxs-lookup"><span data-stu-id="0426d-124">The delay between retries.</span></span>|  
|<span data-ttu-id="0426d-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0426d-125">AppDomain</span></span>|<span data-ttu-id="0426d-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="0426d-126">xs:string</span></span>|<span data-ttu-id="0426d-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0426d-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
