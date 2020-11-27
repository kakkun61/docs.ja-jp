---
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: e549a8aabd0a54022000515050cde19dc4f20dd3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294067"
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="86ccb-102">401- StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="86ccb-102">401- StopSignPostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="86ccb-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="86ccb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="86ccb-104">ID</span><span class="sxs-lookup"><span data-stu-id="86ccb-104">ID</span></span>|<span data-ttu-id="86ccb-105">401</span><span class="sxs-lookup"><span data-stu-id="86ccb-105">401</span></span>|  
|<span data-ttu-id="86ccb-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="86ccb-106">Keywords</span></span>|<span data-ttu-id="86ccb-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="86ccb-107">Troubleshooting</span></span>|  
|<span data-ttu-id="86ccb-108">Level</span><span class="sxs-lookup"><span data-stu-id="86ccb-108">Level</span></span>|<span data-ttu-id="86ccb-109">情報</span><span class="sxs-lookup"><span data-stu-id="86ccb-109">Information</span></span>|  
|<span data-ttu-id="86ccb-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="86ccb-110">Channel</span></span>|<span data-ttu-id="86ccb-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="86ccb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="86ccb-112">Description</span><span class="sxs-lookup"><span data-stu-id="86ccb-112">Description</span></span>  

 <span data-ttu-id="86ccb-113">このイベントは、エンド ツー エンド アクティビティの終了を示します。</span><span class="sxs-lookup"><span data-stu-id="86ccb-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="86ccb-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="86ccb-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="86ccb-115">Message</span><span class="sxs-lookup"><span data-stu-id="86ccb-115">Message</span></span>  

 <span data-ttu-id="86ccb-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="86ccb-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="86ccb-117">詳細</span><span class="sxs-lookup"><span data-stu-id="86ccb-117">Details</span></span>  
  
|<span data-ttu-id="86ccb-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="86ccb-118">Data Item Name</span></span>|<span data-ttu-id="86ccb-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="86ccb-119">Data Item Type</span></span>|<span data-ttu-id="86ccb-120">Description</span><span class="sxs-lookup"><span data-stu-id="86ccb-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="86ccb-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="86ccb-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="86ccb-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="86ccb-122">The name of the activity.</span></span>|  
|<span data-ttu-id="86ccb-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="86ccb-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="86ccb-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="86ccb-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
