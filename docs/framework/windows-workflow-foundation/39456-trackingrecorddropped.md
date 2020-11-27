---
title: 39456 - TrackingRecordDropped
ms.date: 03/30/2017
ms.assetid: da13d5bc-1736-47a4-b3fd-064ca8040326
ms.openlocfilehash: d958b506e057bc0d59f954debdc9da6015bf5f1f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273101"
---
# <a name="39456---trackingrecorddropped"></a><span data-ttu-id="ca90d-102">39456 - TrackingRecordDropped</span><span class="sxs-lookup"><span data-stu-id="ca90d-102">39456 - TrackingRecordDropped</span></span>

## <a name="properties"></a><span data-ttu-id="ca90d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ca90d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca90d-104">ID</span><span class="sxs-lookup"><span data-stu-id="ca90d-104">ID</span></span>|<span data-ttu-id="ca90d-105">39456</span><span class="sxs-lookup"><span data-stu-id="ca90d-105">39456</span></span>|  
|<span data-ttu-id="ca90d-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="ca90d-106">Keywords</span></span>|<span data-ttu-id="ca90d-107">WFTracking</span><span class="sxs-lookup"><span data-stu-id="ca90d-107">WFTracking</span></span>|  
|<span data-ttu-id="ca90d-108">Level</span><span class="sxs-lookup"><span data-stu-id="ca90d-108">Level</span></span>|<span data-ttu-id="ca90d-109">警告</span><span class="sxs-lookup"><span data-stu-id="ca90d-109">Warning</span></span>|  
|<span data-ttu-id="ca90d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ca90d-110">Channel</span></span>|<span data-ttu-id="ca90d-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ca90d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ca90d-112">Description</span><span class="sxs-lookup"><span data-stu-id="ca90d-112">Description</span></span>  

 <span data-ttu-id="ca90d-113">サイズが ETW セッション プロバイダーによって許可される最大値を超えているため、追跡レコードが削除されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="ca90d-113">Indicates a tracking record has been dropped because its size exceeds maximum allowed by the ETW session provider.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ca90d-114">Message</span><span class="sxs-lookup"><span data-stu-id="ca90d-114">Message</span></span>  

 <span data-ttu-id="ca90d-115">追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています</span><span class="sxs-lookup"><span data-stu-id="ca90d-115">Size of tracking record %1 exceeds maximum allowed by the ETW session for provider %2</span></span>  
  
## <a name="details"></a><span data-ttu-id="ca90d-116">詳細</span><span class="sxs-lookup"><span data-stu-id="ca90d-116">Details</span></span>  
  
|<span data-ttu-id="ca90d-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ca90d-117">Data Item Name</span></span>|<span data-ttu-id="ca90d-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ca90d-118">Data Item Type</span></span>|<span data-ttu-id="ca90d-119">Description</span><span class="sxs-lookup"><span data-stu-id="ca90d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ca90d-120">例外</span><span class="sxs-lookup"><span data-stu-id="ca90d-120">Exception</span></span>|<span data-ttu-id="ca90d-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca90d-121">xs:string</span></span>|<span data-ttu-id="ca90d-122">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="ca90d-122">The exception details for the exception</span></span>|  
|<span data-ttu-id="ca90d-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ca90d-123">AppDomain</span></span>|<span data-ttu-id="ca90d-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ca90d-124">xs:string</span></span>|<span data-ttu-id="ca90d-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ca90d-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
