---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: 7027b6557520a9ccb587f8d383d3598571da5838
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279065"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="acd44-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="acd44-102">211 - ParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="acd44-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="acd44-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="acd44-104">ID</span><span class="sxs-lookup"><span data-stu-id="acd44-104">ID</span></span>|<span data-ttu-id="acd44-105">211</span><span class="sxs-lookup"><span data-stu-id="acd44-105">211</span></span>|  
|<span data-ttu-id="acd44-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="acd44-106">Keywords</span></span>|<span data-ttu-id="acd44-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="acd44-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="acd44-108">Level</span><span class="sxs-lookup"><span data-stu-id="acd44-108">Level</span></span>|<span data-ttu-id="acd44-109">情報</span><span class="sxs-lookup"><span data-stu-id="acd44-109">Information</span></span>|  
|<span data-ttu-id="acd44-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="acd44-110">Channel</span></span>|<span data-ttu-id="acd44-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="acd44-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="acd44-112">Description</span><span class="sxs-lookup"><span data-stu-id="acd44-112">Description</span></span>  

 <span data-ttu-id="acd44-113">このイベントは、Service Model が `AfterCall` メソッドを `ParameterInspector` で呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="acd44-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="acd44-114">Message</span><span class="sxs-lookup"><span data-stu-id="acd44-114">Message</span></span>  

 <span data-ttu-id="acd44-115">ディスパッチャーが型 '%1' の ParameterInspector で 'AfterCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="acd44-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="acd44-116">詳細</span><span class="sxs-lookup"><span data-stu-id="acd44-116">Details</span></span>  
  
|<span data-ttu-id="acd44-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="acd44-117">Data Item Name</span></span>|<span data-ttu-id="acd44-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="acd44-118">Data Item Type</span></span>|<span data-ttu-id="acd44-119">Description</span><span class="sxs-lookup"><span data-stu-id="acd44-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="acd44-120">種類名</span><span class="sxs-lookup"><span data-stu-id="acd44-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="acd44-121">呼び出された `ParameterInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="acd44-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="acd44-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="acd44-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="acd44-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="acd44-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="acd44-124">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="acd44-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="acd44-125">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="acd44-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="acd44-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="acd44-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="acd44-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="acd44-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
