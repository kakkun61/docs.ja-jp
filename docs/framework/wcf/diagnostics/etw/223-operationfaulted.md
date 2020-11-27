---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: 310e91320d27dd9817302fc14ef088d180152b73
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263075"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="6389f-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="6389f-102">223 - OperationFaulted</span></span>

## <a name="properties"></a><span data-ttu-id="6389f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="6389f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6389f-104">ID</span><span class="sxs-lookup"><span data-stu-id="6389f-104">ID</span></span>|<span data-ttu-id="6389f-105">223</span><span class="sxs-lookup"><span data-stu-id="6389f-105">223</span></span>|  
|<span data-ttu-id="6389f-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="6389f-106">Keywords</span></span>|<span data-ttu-id="6389f-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6389f-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6389f-108">Level</span><span class="sxs-lookup"><span data-stu-id="6389f-108">Level</span></span>|<span data-ttu-id="6389f-109">警告</span><span class="sxs-lookup"><span data-stu-id="6389f-109">Warning</span></span>|  
|<span data-ttu-id="6389f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="6389f-110">Channel</span></span>|<span data-ttu-id="6389f-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6389f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6389f-112">Description</span><span class="sxs-lookup"><span data-stu-id="6389f-112">Description</span></span>  

 <span data-ttu-id="6389f-113">このイベントは、サービス モデルの既定の `OperationInvoker` が、そのメソッドを呼び出している間に `FaultException` から派生する例外に遭遇すると生成されます。</span><span class="sxs-lookup"><span data-stu-id="6389f-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6389f-114">Message</span><span class="sxs-lookup"><span data-stu-id="6389f-114">Message</span></span>  

 <span data-ttu-id="6389f-115">OperationInvoker によって呼び出されたメソッド '%1' で FaultException がスローされました。</span><span class="sxs-lookup"><span data-stu-id="6389f-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="6389f-116">メソッド呼び出し時間は '%2' ミリ秒でした。</span><span class="sxs-lookup"><span data-stu-id="6389f-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6389f-117">詳細</span><span class="sxs-lookup"><span data-stu-id="6389f-117">Details</span></span>  
  
|<span data-ttu-id="6389f-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="6389f-118">Data Item Name</span></span>|<span data-ttu-id="6389f-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="6389f-119">Data Item Type</span></span>|<span data-ttu-id="6389f-120">Description</span><span class="sxs-lookup"><span data-stu-id="6389f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6389f-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="6389f-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="6389f-122">`OperationInvoker` によって呼び出されたメソッドの CLR 名。</span><span class="sxs-lookup"><span data-stu-id="6389f-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="6389f-123">Duration</span><span class="sxs-lookup"><span data-stu-id="6389f-123">Duration</span></span>|`xs:long`|<span data-ttu-id="6389f-124">`OperationInvoker` でメソッドを呼び出すのにかかった時間 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="6389f-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="6389f-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="6389f-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="6389f-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="6389f-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6389f-127">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="6389f-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6389f-128">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="6389f-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6389f-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6389f-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6389f-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="6389f-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
