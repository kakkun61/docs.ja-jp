---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 04c5e0f4fbf3b95485e5bf4aae53aa2e4912d893
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294496"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="7a25b-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="7a25b-102">225 - TraceCorrelationKeys</span></span>

## <a name="properties"></a><span data-ttu-id="7a25b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7a25b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7a25b-104">ID</span><span class="sxs-lookup"><span data-stu-id="7a25b-104">ID</span></span>|<span data-ttu-id="7a25b-105">225</span><span class="sxs-lookup"><span data-stu-id="7a25b-105">225</span></span>|  
|<span data-ttu-id="7a25b-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="7a25b-106">Keywords</span></span>|<span data-ttu-id="7a25b-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7a25b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7a25b-108">Level</span><span class="sxs-lookup"><span data-stu-id="7a25b-108">Level</span></span>|<span data-ttu-id="7a25b-109">情報</span><span class="sxs-lookup"><span data-stu-id="7a25b-109">Information</span></span>|  
|<span data-ttu-id="7a25b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7a25b-110">Channel</span></span>|<span data-ttu-id="7a25b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7a25b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7a25b-112">Description</span><span class="sxs-lookup"><span data-stu-id="7a25b-112">Description</span></span>  

 <span data-ttu-id="7a25b-113">このイベントは、ワークフロー サービスでコンテンツ ベースの相関関係が使用されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="7a25b-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="7a25b-114">これには、メッセージとインスタンスの相関関係を定義するために適用されている相関関係キーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a25b-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7a25b-115">Message</span><span class="sxs-lookup"><span data-stu-id="7a25b-115">Message</span></span>  

 <span data-ttu-id="7a25b-116">親スコープ '%3' の値 '%2' を使用して相関関係キー '%1' が計算されました。</span><span class="sxs-lookup"><span data-stu-id="7a25b-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7a25b-117">詳細</span><span class="sxs-lookup"><span data-stu-id="7a25b-117">Details</span></span>  
  
|<span data-ttu-id="7a25b-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7a25b-118">Data Item Name</span></span>|<span data-ttu-id="7a25b-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7a25b-119">Data Item Type</span></span>|<span data-ttu-id="7a25b-120">Description</span><span class="sxs-lookup"><span data-stu-id="7a25b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7a25b-121">Instance Key</span><span class="sxs-lookup"><span data-stu-id="7a25b-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="7a25b-122">相関関係値から生成されたキー。</span><span class="sxs-lookup"><span data-stu-id="7a25b-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="7a25b-123">値</span><span class="sxs-lookup"><span data-stu-id="7a25b-123">Values</span></span>|`xs:string`|<span data-ttu-id="7a25b-124">相関関係インスタンス キーの計算に使用された値。</span><span class="sxs-lookup"><span data-stu-id="7a25b-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="7a25b-125">Parent Scope</span><span class="sxs-lookup"><span data-stu-id="7a25b-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="7a25b-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="7a25b-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="7a25b-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="7a25b-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7a25b-128">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="7a25b-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7a25b-129">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="7a25b-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7a25b-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7a25b-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7a25b-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7a25b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
