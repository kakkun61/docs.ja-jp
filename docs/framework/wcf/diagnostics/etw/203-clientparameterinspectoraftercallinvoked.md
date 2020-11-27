---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: b964c26c9684cedef0fbe427bfd9ad232d199f12
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251530"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="f02d8-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="f02d8-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="f02d8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f02d8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f02d8-104">ID</span><span class="sxs-lookup"><span data-stu-id="f02d8-104">ID</span></span>|<span data-ttu-id="f02d8-105">203</span><span class="sxs-lookup"><span data-stu-id="f02d8-105">203</span></span>|  
|<span data-ttu-id="f02d8-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="f02d8-106">Keywords</span></span>|<span data-ttu-id="f02d8-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f02d8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f02d8-108">Level</span><span class="sxs-lookup"><span data-stu-id="f02d8-108">Level</span></span>|<span data-ttu-id="f02d8-109">情報</span><span class="sxs-lookup"><span data-stu-id="f02d8-109">Information</span></span>|  
|<span data-ttu-id="f02d8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f02d8-110">Channel</span></span>|<span data-ttu-id="f02d8-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f02d8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f02d8-112">Description</span><span class="sxs-lookup"><span data-stu-id="f02d8-112">Description</span></span>  

 <span data-ttu-id="f02d8-113">このイベントは、クライアント パラメーター インスペクターで Service Model が `AfterCall` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="f02d8-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f02d8-114">Message</span><span class="sxs-lookup"><span data-stu-id="f02d8-114">Message</span></span>  

 <span data-ttu-id="f02d8-115">ディスパッチャーが型 '%1' の ClientParameterInspector で 'AfterCall' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="f02d8-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f02d8-116">詳細</span><span class="sxs-lookup"><span data-stu-id="f02d8-116">Details</span></span>  
  
|<span data-ttu-id="f02d8-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f02d8-117">Data Item Name</span></span>|<span data-ttu-id="f02d8-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f02d8-118">Data Item Type</span></span>|<span data-ttu-id="f02d8-119">説明</span><span class="sxs-lookup"><span data-stu-id="f02d8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f02d8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="f02d8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="f02d8-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="f02d8-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="f02d8-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f02d8-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f02d8-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="f02d8-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f02d8-124">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="f02d8-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f02d8-125">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="f02d8-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f02d8-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f02d8-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f02d8-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f02d8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
