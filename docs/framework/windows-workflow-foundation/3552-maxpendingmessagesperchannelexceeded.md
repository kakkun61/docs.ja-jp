---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: bd3e7539922e6c430c4ffe5bd96ef1ac7dbd098f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261164"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="c3524-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="c3524-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="c3524-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c3524-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c3524-104">ID</span><span class="sxs-lookup"><span data-stu-id="c3524-104">ID</span></span>|<span data-ttu-id="c3524-105">3552</span><span class="sxs-lookup"><span data-stu-id="c3524-105">3552</span></span>|  
|<span data-ttu-id="c3524-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="c3524-106">Keywords</span></span>|<span data-ttu-id="c3524-107">クォータ、WFServices</span><span class="sxs-lookup"><span data-stu-id="c3524-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="c3524-108">Level</span><span class="sxs-lookup"><span data-stu-id="c3524-108">Level</span></span>|<span data-ttu-id="c3524-109">警告</span><span class="sxs-lookup"><span data-stu-id="c3524-109">Warning</span></span>|  
|<span data-ttu-id="c3524-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c3524-110">Channel</span></span>|<span data-ttu-id="c3524-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c3524-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c3524-112">Description</span><span class="sxs-lookup"><span data-stu-id="c3524-112">Description</span></span>  

 <span data-ttu-id="c3524-113">スロットル 'MaxPendingMessagesPerChannel' の制限に達したことを示します。</span><span class="sxs-lookup"><span data-stu-id="c3524-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c3524-114">Message</span><span class="sxs-lookup"><span data-stu-id="c3524-114">Message</span></span>  

 <span data-ttu-id="c3524-115">'%1' のスロットル 'MaxPendingMessagesPerChannel' の制限に達しました。</span><span class="sxs-lookup"><span data-stu-id="c3524-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="c3524-116">この制限を引き上げるには、BufferedReceiveServiceBehavior の MaxPendingMessagesPerChannel プロパティを調整してください。</span><span class="sxs-lookup"><span data-stu-id="c3524-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c3524-117">詳細</span><span class="sxs-lookup"><span data-stu-id="c3524-117">Details</span></span>  
  
|<span data-ttu-id="c3524-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c3524-118">Data Item Name</span></span>|<span data-ttu-id="c3524-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c3524-119">Data Item Type</span></span>|<span data-ttu-id="c3524-120">Description</span><span class="sxs-lookup"><span data-stu-id="c3524-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c3524-121">制限</span><span class="sxs-lookup"><span data-stu-id="c3524-121">Limit</span></span>|<span data-ttu-id="c3524-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3524-122">xs:string</span></span>|<span data-ttu-id="c3524-123">MaxPendingMessagesPerChannel スロットルの制限。</span><span class="sxs-lookup"><span data-stu-id="c3524-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="c3524-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c3524-124">AppDomain</span></span>|<span data-ttu-id="c3524-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="c3524-125">xs:string</span></span>|<span data-ttu-id="c3524-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c3524-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
