---
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 2c3ff1905a1d17413211246f5b3cc156bcbb7320
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243457"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="bb73d-102">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="bb73d-102">301 - UserDefinedErrorOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="bb73d-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bb73d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb73d-104">ID</span><span class="sxs-lookup"><span data-stu-id="bb73d-104">ID</span></span>|<span data-ttu-id="bb73d-105">301</span><span class="sxs-lookup"><span data-stu-id="bb73d-105">301</span></span>|  
|<span data-ttu-id="bb73d-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="bb73d-106">Keywords</span></span>|<span data-ttu-id="bb73d-107">Troubleshooting、HealthMonitoring、UserEvents、ServiceModel、EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="bb73d-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="bb73d-108">Level</span><span class="sxs-lookup"><span data-stu-id="bb73d-108">Level</span></span>|<span data-ttu-id="bb73d-109">エラー</span><span class="sxs-lookup"><span data-stu-id="bb73d-109">Error</span></span>|  
|<span data-ttu-id="bb73d-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bb73d-110">Channel</span></span>|<span data-ttu-id="bb73d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="bb73d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bb73d-112">Description</span><span class="sxs-lookup"><span data-stu-id="bb73d-112">Description</span></span>  

 <span data-ttu-id="bb73d-113">このイベントは、ユーザー コードから生成されます。</span><span class="sxs-lookup"><span data-stu-id="bb73d-113">This event is emitted from user code.</span></span> <span data-ttu-id="bb73d-114">開発者は、カスタム定義のエラー イベントがサービスで発生したときに、このイベントを生成できます。</span><span class="sxs-lookup"><span data-stu-id="bb73d-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="bb73d-115">これは、<xref:System.Diagnostics.Eventing> API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="bb73d-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="bb73d-116">また、その API をラップし、このイベントを適切に生成する方法を示す、WCF サンプルもあります。</span><span class="sxs-lookup"><span data-stu-id="bb73d-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bb73d-117">Message</span><span class="sxs-lookup"><span data-stu-id="bb73d-117">Message</span></span>  

 <span data-ttu-id="bb73d-118">名前:'%1'、参照:'%2'、ペイロード:%3</span><span class="sxs-lookup"><span data-stu-id="bb73d-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="bb73d-119">詳細</span><span class="sxs-lookup"><span data-stu-id="bb73d-119">Details</span></span>  
  
|<span data-ttu-id="bb73d-120">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bb73d-120">Data Item Name</span></span>|<span data-ttu-id="bb73d-121">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bb73d-121">Data Item Type</span></span>|<span data-ttu-id="bb73d-122">Description</span><span class="sxs-lookup"><span data-stu-id="bb73d-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bb73d-123">名前</span><span class="sxs-lookup"><span data-stu-id="bb73d-123">Name</span></span>|`xs:string`|<span data-ttu-id="bb73d-124">イベントのユーザー定義名。</span><span class="sxs-lookup"><span data-stu-id="bb73d-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="bb73d-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="bb73d-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="bb73d-126">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="bb73d-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="bb73d-127">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="bb73d-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="bb73d-128">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="bb73d-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="bb73d-129">ペイロード</span><span class="sxs-lookup"><span data-stu-id="bb73d-129">Payload</span></span>|`xs:string`|<span data-ttu-id="bb73d-130">イベントのユーザー定義ペイロード。</span><span class="sxs-lookup"><span data-stu-id="bb73d-130">The user-defined payload of the event.</span></span>|
