---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 28c2aca4555d2e4ff498e450deae55ad6a87743c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279039"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="24347-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="24347-102">212 - ParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="24347-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="24347-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24347-104">ID</span><span class="sxs-lookup"><span data-stu-id="24347-104">ID</span></span>|<span data-ttu-id="24347-105">212</span><span class="sxs-lookup"><span data-stu-id="24347-105">212</span></span>|  
|<span data-ttu-id="24347-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="24347-106">Keywords</span></span>|<span data-ttu-id="24347-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="24347-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="24347-108">Level</span><span class="sxs-lookup"><span data-stu-id="24347-108">Level</span></span>|<span data-ttu-id="24347-109">情報</span><span class="sxs-lookup"><span data-stu-id="24347-109">Information</span></span>|  
|<span data-ttu-id="24347-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="24347-110">Channel</span></span>|<span data-ttu-id="24347-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="24347-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="24347-112">Description</span><span class="sxs-lookup"><span data-stu-id="24347-112">Description</span></span>  

 <span data-ttu-id="24347-113">このイベントは、Service Model が `BeforeCall` メソッドを `ParameterInspector` で呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="24347-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="24347-114">Message</span><span class="sxs-lookup"><span data-stu-id="24347-114">Message</span></span>  

 <span data-ttu-id="24347-115">ディスパッチャーが型 '%1' の ParameterInspector で 'BeforeCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="24347-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="24347-116">詳細</span><span class="sxs-lookup"><span data-stu-id="24347-116">Details</span></span>  
  
|<span data-ttu-id="24347-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="24347-117">Data Item Name</span></span>|<span data-ttu-id="24347-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="24347-118">Data Item Type</span></span>|<span data-ttu-id="24347-119">説明</span><span class="sxs-lookup"><span data-stu-id="24347-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="24347-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="24347-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="24347-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="24347-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="24347-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="24347-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="24347-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="24347-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="24347-124">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="24347-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="24347-125">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="24347-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="24347-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="24347-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="24347-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="24347-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
