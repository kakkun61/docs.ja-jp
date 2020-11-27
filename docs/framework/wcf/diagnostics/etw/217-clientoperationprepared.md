---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: e8aaf65bdff0718e932d07937e052541b7134f11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278883"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="be673-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="be673-102">217 - ClientOperationPrepared</span></span>

## <a name="properties"></a><span data-ttu-id="be673-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="be673-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="be673-104">ID</span><span class="sxs-lookup"><span data-stu-id="be673-104">ID</span></span>|<span data-ttu-id="be673-105">217</span><span class="sxs-lookup"><span data-stu-id="be673-105">217</span></span>|  
|<span data-ttu-id="be673-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="be673-106">Keywords</span></span>|<span data-ttu-id="be673-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be673-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="be673-108">Level</span><span class="sxs-lookup"><span data-stu-id="be673-108">Level</span></span>|<span data-ttu-id="be673-109">情報</span><span class="sxs-lookup"><span data-stu-id="be673-109">Information</span></span>|  
|<span data-ttu-id="be673-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="be673-110">Channel</span></span>|<span data-ttu-id="be673-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="be673-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="be673-112">Description</span><span class="sxs-lookup"><span data-stu-id="be673-112">Description</span></span>  

 <span data-ttu-id="be673-113">このイベントは、操作がサービスに送信される直前に、クライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="be673-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="be673-114">Message</span><span class="sxs-lookup"><span data-stu-id="be673-114">Message</span></span>  

 <span data-ttu-id="be673-115">クライアントは '%2' コントラクトと関連付けられている Action '%1' を実行しています。</span><span class="sxs-lookup"><span data-stu-id="be673-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="be673-116">メッセージは '%3' に送信されます。</span><span class="sxs-lookup"><span data-stu-id="be673-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="be673-117">詳細</span><span class="sxs-lookup"><span data-stu-id="be673-117">Details</span></span>  
  
|<span data-ttu-id="be673-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="be673-118">Data Item Name</span></span>|<span data-ttu-id="be673-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="be673-119">Data Item Type</span></span>|<span data-ttu-id="be673-120">説明</span><span class="sxs-lookup"><span data-stu-id="be673-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="be673-121">アクション</span><span class="sxs-lookup"><span data-stu-id="be673-121">Action</span></span>|`xs:string`|<span data-ttu-id="be673-122">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="be673-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="be673-123">Contract Name</span><span class="sxs-lookup"><span data-stu-id="be673-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="be673-124">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="be673-124">The name of the contract.</span></span> <span data-ttu-id="be673-125">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="be673-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="be673-126">宛先</span><span class="sxs-lookup"><span data-stu-id="be673-126">Destination</span></span>|`xs:string`|<span data-ttu-id="be673-127">メッセージの送信先となるサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="be673-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="be673-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="be673-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="be673-129">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="be673-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="be673-130">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="be673-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="be673-131">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="be673-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="be673-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="be673-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="be673-133">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="be673-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
