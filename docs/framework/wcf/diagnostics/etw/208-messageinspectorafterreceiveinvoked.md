---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 4aa0f41b0b772551d9257920e5c15051961b7332
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267820"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="8b797-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="8b797-102">208 - MessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="8b797-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8b797-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b797-104">ID</span><span class="sxs-lookup"><span data-stu-id="8b797-104">ID</span></span>|<span data-ttu-id="8b797-105">208</span><span class="sxs-lookup"><span data-stu-id="8b797-105">208</span></span>|  
|<span data-ttu-id="8b797-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="8b797-106">Keywords</span></span>|<span data-ttu-id="8b797-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8b797-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8b797-108">Level</span><span class="sxs-lookup"><span data-stu-id="8b797-108">Level</span></span>|<span data-ttu-id="8b797-109">情報</span><span class="sxs-lookup"><span data-stu-id="8b797-109">Information</span></span>|  
|<span data-ttu-id="8b797-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8b797-110">Channel</span></span>|<span data-ttu-id="8b797-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8b797-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8b797-112">Description</span><span class="sxs-lookup"><span data-stu-id="8b797-112">Description</span></span>  

 <span data-ttu-id="8b797-113">このイベントは、メッセージ インスペクターで Service Model が `AfterReceive` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="8b797-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8b797-114">Message</span><span class="sxs-lookup"><span data-stu-id="8b797-114">Message</span></span>  

 <span data-ttu-id="8b797-115">ディスパッチャーが型 '%1' の MessageInspector で 'AfterReceiveReply' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="8b797-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8b797-116">詳細</span><span class="sxs-lookup"><span data-stu-id="8b797-116">Details</span></span>  
  
|<span data-ttu-id="8b797-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8b797-117">Data Item Name</span></span>|<span data-ttu-id="8b797-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8b797-118">Data Item Type</span></span>|<span data-ttu-id="8b797-119">説明</span><span class="sxs-lookup"><span data-stu-id="8b797-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8b797-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="8b797-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="8b797-121">呼び出された `MessageInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="8b797-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="8b797-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="8b797-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="8b797-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="8b797-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8b797-124">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="8b797-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8b797-125">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="8b797-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8b797-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8b797-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8b797-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8b797-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
