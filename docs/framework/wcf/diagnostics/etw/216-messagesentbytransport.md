---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: b3e9e1a48951ad5a2e5e7820dc1828c20e310635
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278909"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="4adad-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="4adad-102">216 - MessageSentByTransport</span></span>

## <a name="properties"></a><span data-ttu-id="4adad-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4adad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4adad-104">ID</span><span class="sxs-lookup"><span data-stu-id="4adad-104">ID</span></span>|<span data-ttu-id="4adad-105">216</span><span class="sxs-lookup"><span data-stu-id="4adad-105">216</span></span>|  
|<span data-ttu-id="4adad-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="4adad-106">Keywords</span></span>|<span data-ttu-id="4adad-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4adad-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4adad-108">Level</span><span class="sxs-lookup"><span data-stu-id="4adad-108">Level</span></span>|<span data-ttu-id="4adad-109">情報</span><span class="sxs-lookup"><span data-stu-id="4adad-109">Information</span></span>|  
|<span data-ttu-id="4adad-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="4adad-110">Channel</span></span>|<span data-ttu-id="4adad-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="4adad-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4adad-112">Description</span><span class="sxs-lookup"><span data-stu-id="4adad-112">Description</span></span>  

 <span data-ttu-id="4adad-113">このイベントは、TCP ベースのトランスポートがメッセージを送信するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="4adad-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="4adad-114">トランスポート レベルでは、1 つの操作に対して複数のメッセージが、クライアントとサービス間で交換されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4adad-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="4adad-115">これはインフラストラクチャの動作によるもので、セキュリティがその一例です。</span><span class="sxs-lookup"><span data-stu-id="4adad-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="4adad-116">このため、出力さ **れるイベントの** 数は、サービスのバインドとその構成によって異なります。</span><span class="sxs-lookup"><span data-stu-id="4adad-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4adad-117">Message</span><span class="sxs-lookup"><span data-stu-id="4adad-117">Message</span></span>  

 <span data-ttu-id="4adad-118">トランスポートが '%1' にメッセージを送信しました。</span><span class="sxs-lookup"><span data-stu-id="4adad-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4adad-119">詳細</span><span class="sxs-lookup"><span data-stu-id="4adad-119">Details</span></span>  
  
|<span data-ttu-id="4adad-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4adad-120">Data Item Name</span></span>|<span data-ttu-id="4adad-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4adad-121">Data Item Type</span></span>|<span data-ttu-id="4adad-122">Description</span><span class="sxs-lookup"><span data-stu-id="4adad-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4adad-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="4adad-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="4adad-124">要求メッセージが送信されたアドレス。</span><span class="sxs-lookup"><span data-stu-id="4adad-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="4adad-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="4adad-125">HostReference</span></span>|<span data-ttu-id="4adad-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="4adad-126">xs:string</span></span>|<span data-ttu-id="4adad-127">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="4adad-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4adad-128">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="4adad-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4adad-129">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="4adad-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4adad-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4adad-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4adad-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4adad-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
