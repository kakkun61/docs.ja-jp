---
title: 4210 - SqlExceptionCaught
ms.date: 03/30/2017
ms.assetid: f0ce8af3-eb4c-48c8-b3d9-dd2f94b5574b
ms.openlocfilehash: 1dab44e3fb97d74a2146f5bf992225222bc93d50
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280378"
---
# <a name="4210---sqlexceptioncaught"></a><span data-ttu-id="5b9c5-102">4210 - SqlExceptionCaught</span><span class="sxs-lookup"><span data-stu-id="5b9c5-102">4210 - SqlExceptionCaught</span></span>

## <a name="properties"></a><span data-ttu-id="5b9c5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5b9c5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5b9c5-104">ID</span><span class="sxs-lookup"><span data-stu-id="5b9c5-104">ID</span></span>|<span data-ttu-id="5b9c5-105">4210</span><span class="sxs-lookup"><span data-stu-id="5b9c5-105">4210</span></span>|  
|<span data-ttu-id="5b9c5-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="5b9c5-106">Keywords</span></span>|<span data-ttu-id="5b9c5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="5b9c5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="5b9c5-108">Level</span><span class="sxs-lookup"><span data-stu-id="5b9c5-108">Level</span></span>|<span data-ttu-id="5b9c5-109">警告</span><span class="sxs-lookup"><span data-stu-id="5b9c5-109">Warning</span></span>|  
|<span data-ttu-id="5b9c5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="5b9c5-110">Channel</span></span>|<span data-ttu-id="5b9c5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5b9c5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5b9c5-112">Description</span><span class="sxs-lookup"><span data-stu-id="5b9c5-112">Description</span></span>  

 <span data-ttu-id="5b9c5-113">SQL 例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5b9c5-113">Indicates a SQL exception was caught.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5b9c5-114">Message</span><span class="sxs-lookup"><span data-stu-id="5b9c5-114">Message</span></span>  

 <span data-ttu-id="5b9c5-115">SQL 例外番号 %1 メッセージ %2 がキャッチされました。</span><span class="sxs-lookup"><span data-stu-id="5b9c5-115">Caught SQL Exception number %1 message %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5b9c5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="5b9c5-116">Details</span></span>  
  
|<span data-ttu-id="5b9c5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5b9c5-117">Data Item Name</span></span>|<span data-ttu-id="5b9c5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5b9c5-118">Data Item Type</span></span>|<span data-ttu-id="5b9c5-119">Description</span><span class="sxs-lookup"><span data-stu-id="5b9c5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5b9c5-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="5b9c5-120">ErrorNumber</span></span>|<span data-ttu-id="5b9c5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5b9c5-121">xs:string</span></span>|<span data-ttu-id="5b9c5-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="5b9c5-122">The SQL error number.</span></span>|  
|<span data-ttu-id="5b9c5-123">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="5b9c5-123">ExceptionMessage</span></span>|<span data-ttu-id="5b9c5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5b9c5-124">xs:string</span></span>|<span data-ttu-id="5b9c5-125">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="5b9c5-125">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="5b9c5-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5b9c5-126">AppDomain</span></span>|<span data-ttu-id="5b9c5-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5b9c5-127">xs:string</span></span>|<span data-ttu-id="5b9c5-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5b9c5-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
