---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 87a98d30f5ecde6f81580a95e337df22341c23d4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279026"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="e396b-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="e396b-102">213 - ServiceHostStarted</span></span>

## <a name="properties"></a><span data-ttu-id="e396b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e396b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e396b-104">ID</span><span class="sxs-lookup"><span data-stu-id="e396b-104">ID</span></span>|<span data-ttu-id="e396b-105">213</span><span class="sxs-lookup"><span data-stu-id="e396b-105">213</span></span>|  
|<span data-ttu-id="e396b-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="e396b-106">Keywords</span></span>|<span data-ttu-id="e396b-107">EndToEndMonitoring、HealthMonitoring、Troubleshooting、ServiceHost</span><span class="sxs-lookup"><span data-stu-id="e396b-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="e396b-108">Level</span><span class="sxs-lookup"><span data-stu-id="e396b-108">Level</span></span>|<span data-ttu-id="e396b-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="e396b-109">LogAlways</span></span>|  
|<span data-ttu-id="e396b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e396b-110">Channel</span></span>|<span data-ttu-id="e396b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e396b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e396b-112">Description</span><span class="sxs-lookup"><span data-stu-id="e396b-112">Description</span></span>  

 <span data-ttu-id="e396b-113">このイベントは、Web でホストされているサービス ホストが起動されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="e396b-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="e396b-114">通常、サービスがメッセージによってアクティブにされた時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="e396b-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="e396b-115">また、サービスが自動的に開始するように構成されている場合も発生します。</span><span class="sxs-lookup"><span data-stu-id="e396b-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e396b-116">Message</span><span class="sxs-lookup"><span data-stu-id="e396b-116">Message</span></span>  

 <span data-ttu-id="e396b-117">ServiceHost は '%1' で開始されています。</span><span class="sxs-lookup"><span data-stu-id="e396b-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e396b-118">詳細</span><span class="sxs-lookup"><span data-stu-id="e396b-118">Details</span></span>  
  
|<span data-ttu-id="e396b-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e396b-119">Data Item Name</span></span>|<span data-ttu-id="e396b-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e396b-120">Data Item Type</span></span>|<span data-ttu-id="e396b-121">Description</span><span class="sxs-lookup"><span data-stu-id="e396b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e396b-122">Service Type Name</span><span class="sxs-lookup"><span data-stu-id="e396b-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="e396b-123">サービス実装の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="e396b-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="e396b-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="e396b-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="e396b-125">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="e396b-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e396b-126">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="e396b-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e396b-127">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="e396b-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e396b-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e396b-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e396b-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e396b-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
