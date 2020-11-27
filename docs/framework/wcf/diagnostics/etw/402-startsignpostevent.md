---
title: 402 - StartSignpostEvent
ms.date: 03/30/2017
ms.assetid: 5e5be126-765d-4ac9-88e7-008e9ef4f0e5
ms.openlocfilehash: ff32c900f4e357b7f1eca669a0ea60f80ea24b19
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258323"
---
# <a name="402---startsignpostevent"></a><span data-ttu-id="581e3-102">402 - StartSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="581e3-102">402 - StartSignpostEvent</span></span>

## <a name="properties"></a><span data-ttu-id="581e3-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="581e3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="581e3-104">ID</span><span class="sxs-lookup"><span data-stu-id="581e3-104">ID</span></span>|<span data-ttu-id="581e3-105">402</span><span class="sxs-lookup"><span data-stu-id="581e3-105">402</span></span>|  
|<span data-ttu-id="581e3-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="581e3-106">Keywords</span></span>|<span data-ttu-id="581e3-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="581e3-107">Troubleshooting</span></span>|  
|<span data-ttu-id="581e3-108">Level</span><span class="sxs-lookup"><span data-stu-id="581e3-108">Level</span></span>|<span data-ttu-id="581e3-109">情報</span><span class="sxs-lookup"><span data-stu-id="581e3-109">Information</span></span>|  
|<span data-ttu-id="581e3-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="581e3-110">Channel</span></span>|<span data-ttu-id="581e3-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="581e3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="581e3-112">Description</span><span class="sxs-lookup"><span data-stu-id="581e3-112">Description</span></span>  

 <span data-ttu-id="581e3-113">このイベントは、エンド ツー エンド アクティビティの開始を示します。</span><span class="sxs-lookup"><span data-stu-id="581e3-113">This event marks the beginning of an end-to-end activity.</span></span> <span data-ttu-id="581e3-114">ここにはアクティビティの名前が指定されています。</span><span class="sxs-lookup"><span data-stu-id="581e3-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="581e3-115">Message</span><span class="sxs-lookup"><span data-stu-id="581e3-115">Message</span></span>  

 <span data-ttu-id="581e3-116">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="581e3-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="581e3-117">詳細</span><span class="sxs-lookup"><span data-stu-id="581e3-117">Details</span></span>  
  
|<span data-ttu-id="581e3-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="581e3-118">Data Item Name</span></span>|<span data-ttu-id="581e3-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="581e3-119">Data Item Type</span></span>|<span data-ttu-id="581e3-120">Description</span><span class="sxs-lookup"><span data-stu-id="581e3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="581e3-121">Extended Data</span><span class="sxs-lookup"><span data-stu-id="581e3-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="581e3-122">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="581e3-122">The name of the activity.</span></span>|  
|<span data-ttu-id="581e3-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="581e3-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="581e3-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="581e3-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
