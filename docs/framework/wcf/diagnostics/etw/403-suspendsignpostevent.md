---
title: 403 - SuspendSignpostEvent
ms.date: 03/30/2017
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
ms.openlocfilehash: 66251141cdf66c18ad0c1334f6f3e6c0629b4b33
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241058"
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="ed2da-102">403 - SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="ed2da-102">403 - SuspendSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="ed2da-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ed2da-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ed2da-104">ID</span><span class="sxs-lookup"><span data-stu-id="ed2da-104">ID</span></span>|<span data-ttu-id="ed2da-105">403</span><span class="sxs-lookup"><span data-stu-id="ed2da-105">403</span></span>|  
|<span data-ttu-id="ed2da-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="ed2da-106">Keywords</span></span>|<span data-ttu-id="ed2da-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ed2da-107">Troubleshooting</span></span>|  
|<span data-ttu-id="ed2da-108">Level</span><span class="sxs-lookup"><span data-stu-id="ed2da-108">Level</span></span>|<span data-ttu-id="ed2da-109">情報</span><span class="sxs-lookup"><span data-stu-id="ed2da-109">Information</span></span>|  
|<span data-ttu-id="ed2da-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ed2da-110">Channel</span></span>|<span data-ttu-id="ed2da-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ed2da-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ed2da-112">Description</span><span class="sxs-lookup"><span data-stu-id="ed2da-112">Description</span></span>  

 <span data-ttu-id="ed2da-113">このイベントは、エンド ツー エンド アクティビティの中断を示します。</span><span class="sxs-lookup"><span data-stu-id="ed2da-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="ed2da-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="ed2da-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ed2da-115">Message</span><span class="sxs-lookup"><span data-stu-id="ed2da-115">Message</span></span>  

 <span data-ttu-id="ed2da-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="ed2da-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ed2da-117">詳細</span><span class="sxs-lookup"><span data-stu-id="ed2da-117">Details</span></span>  
  
|<span data-ttu-id="ed2da-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ed2da-118">Data Item Name</span></span>|<span data-ttu-id="ed2da-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ed2da-119">Data Item Type</span></span>|<span data-ttu-id="ed2da-120">Description</span><span class="sxs-lookup"><span data-stu-id="ed2da-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ed2da-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="ed2da-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="ed2da-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="ed2da-122">The name of the activity.</span></span>|  
|<span data-ttu-id="ed2da-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ed2da-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ed2da-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ed2da-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
