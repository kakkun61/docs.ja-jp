---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 1b63877998ea7942886c83d8795fe5ee49fdf053
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241929"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="686ec-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="686ec-102">220 - MessageSentToTransport</span></span>

## <a name="properties"></a><span data-ttu-id="686ec-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="686ec-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="686ec-104">Id</span><span class="sxs-lookup"><span data-stu-id="686ec-104">Id</span></span>|<span data-ttu-id="686ec-105">220</span><span class="sxs-lookup"><span data-stu-id="686ec-105">220</span></span>|  
|<span data-ttu-id="686ec-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="686ec-106">Keywords</span></span>|<span data-ttu-id="686ec-107">EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="686ec-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="686ec-108">Level</span><span class="sxs-lookup"><span data-stu-id="686ec-108">Level</span></span>|<span data-ttu-id="686ec-109">情報</span><span class="sxs-lookup"><span data-stu-id="686ec-109">Information</span></span>|  
|<span data-ttu-id="686ec-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="686ec-110">Channel</span></span>|<span data-ttu-id="686ec-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="686ec-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="686ec-112">Description</span><span class="sxs-lookup"><span data-stu-id="686ec-112">Description</span></span>  

 <span data-ttu-id="686ec-113">このイベントは、サービス モデルがトランスポートにメッセージを送信すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="686ec-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="686ec-114">一方向トランスポートでは、このイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="686ec-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="686ec-115">Message</span><span class="sxs-lookup"><span data-stu-id="686ec-115">Message</span></span>  

 <span data-ttu-id="686ec-116">ディスパッチャーがトランスポートにメッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="686ec-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="686ec-117">関連付け ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="686ec-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="686ec-118">詳細</span><span class="sxs-lookup"><span data-stu-id="686ec-118">Details</span></span>  
  
|<span data-ttu-id="686ec-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="686ec-119">Data Item Name</span></span>|<span data-ttu-id="686ec-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="686ec-120">Data Item Type</span></span>|<span data-ttu-id="686ec-121">Description</span><span class="sxs-lookup"><span data-stu-id="686ec-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="686ec-122">関連付け ID</span><span class="sxs-lookup"><span data-stu-id="686ec-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="686ec-123">サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。</span><span class="sxs-lookup"><span data-stu-id="686ec-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="686ec-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="686ec-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="686ec-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="686ec-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="686ec-126">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="686ec-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="686ec-127">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="686ec-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="686ec-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="686ec-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="686ec-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="686ec-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
