---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: d84f6c6f38868f7915caaaf87e15885099b65456
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266676"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="3a320-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="3a320-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="3a320-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="3a320-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3a320-104">ID</span><span class="sxs-lookup"><span data-stu-id="3a320-104">ID</span></span>|<span data-ttu-id="3a320-105">201</span><span class="sxs-lookup"><span data-stu-id="3a320-105">201</span></span>|  
|<span data-ttu-id="3a320-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="3a320-106">Keywords</span></span>|<span data-ttu-id="3a320-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3a320-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3a320-108">Level</span><span class="sxs-lookup"><span data-stu-id="3a320-108">Level</span></span>|<span data-ttu-id="3a320-109">情報</span><span class="sxs-lookup"><span data-stu-id="3a320-109">Information</span></span>|  
|<span data-ttu-id="3a320-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="3a320-110">Channel</span></span>|<span data-ttu-id="3a320-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="3a320-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3a320-112">Description</span><span class="sxs-lookup"><span data-stu-id="3a320-112">Description</span></span>  

 <span data-ttu-id="3a320-113">このイベントは、クライアント メッセージ インスペクターで Service Model が `AfterReceiveReply` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="3a320-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3a320-114">Message</span><span class="sxs-lookup"><span data-stu-id="3a320-114">Message</span></span>  

 <span data-ttu-id="3a320-115">ディスパッチャーが型 '%1' の ClientMessageInspector で 'AfterReceiveReply' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="3a320-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3a320-116">詳細</span><span class="sxs-lookup"><span data-stu-id="3a320-116">Details</span></span>  
  
|<span data-ttu-id="3a320-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="3a320-117">Data Item Name</span></span>|<span data-ttu-id="3a320-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="3a320-118">Data Item Type</span></span>|<span data-ttu-id="3a320-119">説明</span><span class="sxs-lookup"><span data-stu-id="3a320-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3a320-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="3a320-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="3a320-121">呼び出されたインスペクターの型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="3a320-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="3a320-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="3a320-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="3a320-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="3a320-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3a320-124">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="3a320-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3a320-125">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="3a320-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3a320-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3a320-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3a320-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="3a320-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
