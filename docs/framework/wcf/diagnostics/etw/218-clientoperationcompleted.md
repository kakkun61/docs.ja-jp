---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: d74aa77aff7b45b50f6891c999889011d9e03381
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278857"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="52ff0-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="52ff0-102">218 - ClientOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="52ff0-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52ff0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="52ff0-104">ID</span><span class="sxs-lookup"><span data-stu-id="52ff0-104">ID</span></span>|<span data-ttu-id="52ff0-105">218</span><span class="sxs-lookup"><span data-stu-id="52ff0-105">218</span></span>|  
|<span data-ttu-id="52ff0-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="52ff0-106">Keywords</span></span>|<span data-ttu-id="52ff0-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="52ff0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="52ff0-108">Level</span><span class="sxs-lookup"><span data-stu-id="52ff0-108">Level</span></span>|<span data-ttu-id="52ff0-109">情報</span><span class="sxs-lookup"><span data-stu-id="52ff0-109">Information</span></span>|  
|<span data-ttu-id="52ff0-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="52ff0-110">Channel</span></span>|<span data-ttu-id="52ff0-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="52ff0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="52ff0-112">Description</span><span class="sxs-lookup"><span data-stu-id="52ff0-112">Description</span></span>  

 <span data-ttu-id="52ff0-113">このイベントは、ある操作が完了した直後にクライアントによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="52ff0-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="52ff0-114">一方向の操作の場合は、メッセージが正常に送信された直後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="52ff0-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="52ff0-115">要求 - 応答の操作の場合は、応答の受信後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="52ff0-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="52ff0-116">Message</span><span class="sxs-lookup"><span data-stu-id="52ff0-116">Message</span></span>  

 <span data-ttu-id="52ff0-117">クライアントは '%2' コントラクトと関連付けられている Action '%1' の実行を完了しました。</span><span class="sxs-lookup"><span data-stu-id="52ff0-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="52ff0-118">メッセージは '%3' に送信されました。</span><span class="sxs-lookup"><span data-stu-id="52ff0-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="52ff0-119">詳細</span><span class="sxs-lookup"><span data-stu-id="52ff0-119">Details</span></span>  
  
|<span data-ttu-id="52ff0-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="52ff0-120">Data Item Name</span></span>|<span data-ttu-id="52ff0-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="52ff0-121">Data Item Type</span></span>|<span data-ttu-id="52ff0-122">説明</span><span class="sxs-lookup"><span data-stu-id="52ff0-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="52ff0-123">アクション</span><span class="sxs-lookup"><span data-stu-id="52ff0-123">Action</span></span>|<span data-ttu-id="52ff0-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="52ff0-124">xs:string</span></span>|<span data-ttu-id="52ff0-125">送信メッセージの SOAP アクション ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="52ff0-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="52ff0-126">Contract Name</span><span class="sxs-lookup"><span data-stu-id="52ff0-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="52ff0-127">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="52ff0-127">The name of the contract.</span></span> <span data-ttu-id="52ff0-128">例: ICalculator。</span><span class="sxs-lookup"><span data-stu-id="52ff0-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="52ff0-129">宛先</span><span class="sxs-lookup"><span data-stu-id="52ff0-129">Destination</span></span>|`xs:string`|<span data-ttu-id="52ff0-130">メッセージの送信先のサービス エンドポイントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="52ff0-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="52ff0-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="52ff0-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="52ff0-132">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="52ff0-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="52ff0-133">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="52ff0-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="52ff0-134">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="52ff0-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="52ff0-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="52ff0-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="52ff0-136">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="52ff0-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
