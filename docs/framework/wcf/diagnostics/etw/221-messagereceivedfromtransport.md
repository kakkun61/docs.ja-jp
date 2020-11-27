---
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 47e871b70e3ef2419543b4710c2988736665cb46
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263101"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="84781-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="84781-102">221 - MessageReceivedFromTransport</span></span>

## <a name="properties"></a><span data-ttu-id="84781-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="84781-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84781-104">ID</span><span class="sxs-lookup"><span data-stu-id="84781-104">ID</span></span>|<span data-ttu-id="84781-105">221</span><span class="sxs-lookup"><span data-stu-id="84781-105">221</span></span>|  
|<span data-ttu-id="84781-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="84781-106">Keywords</span></span>|<span data-ttu-id="84781-107">EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="84781-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="84781-108">Level</span><span class="sxs-lookup"><span data-stu-id="84781-108">Level</span></span>|<span data-ttu-id="84781-109">情報</span><span class="sxs-lookup"><span data-stu-id="84781-109">Information</span></span>|  
|<span data-ttu-id="84781-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="84781-110">Channel</span></span>|<span data-ttu-id="84781-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="84781-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="84781-112">Description</span><span class="sxs-lookup"><span data-stu-id="84781-112">Description</span></span>  

 <span data-ttu-id="84781-113">このイベントは、サービス モデルがトランスポートからメッセージを受信すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="84781-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="84781-114">Message</span><span class="sxs-lookup"><span data-stu-id="84781-114">Message</span></span>  

 <span data-ttu-id="84781-115">ディスパッチャーがトランスポートからメッセージを受信しました。</span><span class="sxs-lookup"><span data-stu-id="84781-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="84781-116">関連付け ID == '%1'。</span><span class="sxs-lookup"><span data-stu-id="84781-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="84781-117">詳細</span><span class="sxs-lookup"><span data-stu-id="84781-117">Details</span></span>  
  
|<span data-ttu-id="84781-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="84781-118">Data Item Name</span></span>|<span data-ttu-id="84781-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="84781-119">Data Item Type</span></span>|<span data-ttu-id="84781-120">Description</span><span class="sxs-lookup"><span data-stu-id="84781-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="84781-121">関連付け ID</span><span class="sxs-lookup"><span data-stu-id="84781-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="84781-122">サービスまたはクライアントからの `MessageSentToTransport` イベントを、反対側の対応する `MessageReceivedFromTransport` と関連付けるのに使用する、アクティビティ ID。</span><span class="sxs-lookup"><span data-stu-id="84781-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="84781-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="84781-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="84781-124">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="84781-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="84781-125">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="84781-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="84781-126">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="84781-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="84781-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="84781-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="84781-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="84781-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
