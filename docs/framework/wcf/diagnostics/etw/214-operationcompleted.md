---
title: 214 - OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: 6147c70448efb122cb43a2b42a1e9b59980fab29
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278948"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="6ce5e-102">214 - OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="6ce5e-102">214 - OperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="6ce5e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6ce5e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6ce5e-104">ID</span><span class="sxs-lookup"><span data-stu-id="6ce5e-104">ID</span></span>|<span data-ttu-id="6ce5e-105">214</span><span class="sxs-lookup"><span data-stu-id="6ce5e-105">214</span></span>|  
|<span data-ttu-id="6ce5e-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="6ce5e-106">Keywords</span></span>|<span data-ttu-id="6ce5e-107">HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6ce5e-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6ce5e-108">Level</span><span class="sxs-lookup"><span data-stu-id="6ce5e-108">Level</span></span>|<span data-ttu-id="6ce5e-109">情報</span><span class="sxs-lookup"><span data-stu-id="6ce5e-109">Information</span></span>|  
|<span data-ttu-id="6ce5e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6ce5e-110">Channel</span></span>|<span data-ttu-id="6ce5e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6ce5e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6ce5e-112">Description</span><span class="sxs-lookup"><span data-stu-id="6ce5e-112">Description</span></span>  

 <span data-ttu-id="6ce5e-113">このイベントは、サービス モデルの既定の `OperationInvoker` が、メソッドから例外がスローされることなく、メソッドへの呼び出しを完了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6ce5e-114">Message</span><span class="sxs-lookup"><span data-stu-id="6ce5e-114">Message</span></span>  

 <span data-ttu-id="6ce5e-115">OperationInvoker がメソッド '%1' への呼び出しを完了しました。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="6ce5e-116">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6ce5e-117">詳細</span><span class="sxs-lookup"><span data-stu-id="6ce5e-117">Details</span></span>  
  
|<span data-ttu-id="6ce5e-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6ce5e-118">Data Item Name</span></span>|<span data-ttu-id="6ce5e-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6ce5e-119">Data Item Type</span></span>|<span data-ttu-id="6ce5e-120">Description</span><span class="sxs-lookup"><span data-stu-id="6ce5e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6ce5e-121">メソッド名</span><span class="sxs-lookup"><span data-stu-id="6ce5e-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="6ce5e-122">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="6ce5e-123">Duration</span><span class="sxs-lookup"><span data-stu-id="6ce5e-123">Duration</span></span>|`xs:long`|<span data-ttu-id="6ce5e-124">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="6ce5e-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="6ce5e-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="6ce5e-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6ce5e-127">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6ce5e-128">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6ce5e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6ce5e-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6ce5e-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6ce5e-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
