---
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 50a9424f445781cac70d7d7fde58beea10231cfa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267755"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="0fdaa-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="0fdaa-102">209 - MessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="0fdaa-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="0fdaa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0fdaa-104">ID</span><span class="sxs-lookup"><span data-stu-id="0fdaa-104">ID</span></span>|<span data-ttu-id="0fdaa-105">209</span><span class="sxs-lookup"><span data-stu-id="0fdaa-105">209</span></span>|  
|<span data-ttu-id="0fdaa-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="0fdaa-106">Keywords</span></span>|<span data-ttu-id="0fdaa-107">Troubleshooting、ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0fdaa-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0fdaa-108">Level</span><span class="sxs-lookup"><span data-stu-id="0fdaa-108">Level</span></span>|<span data-ttu-id="0fdaa-109">情報</span><span class="sxs-lookup"><span data-stu-id="0fdaa-109">Information</span></span>|  
|<span data-ttu-id="0fdaa-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="0fdaa-110">Channel</span></span>|<span data-ttu-id="0fdaa-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0fdaa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0fdaa-112">Description</span><span class="sxs-lookup"><span data-stu-id="0fdaa-112">Description</span></span>  

 <span data-ttu-id="0fdaa-113">このイベントは、メッセージ インスペクターで Service Model が `BeforeSend` メソッドを呼び出した後に生成されます。</span><span class="sxs-lookup"><span data-stu-id="0fdaa-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0fdaa-114">Message</span><span class="sxs-lookup"><span data-stu-id="0fdaa-114">Message</span></span>  

 <span data-ttu-id="0fdaa-115">ディスパッチャーが型 '%1' の MessageInspector で 'BeforeSendRequest' を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="0fdaa-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0fdaa-116">詳細</span><span class="sxs-lookup"><span data-stu-id="0fdaa-116">Details</span></span>  
  
|<span data-ttu-id="0fdaa-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="0fdaa-117">Data Item Name</span></span>|<span data-ttu-id="0fdaa-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="0fdaa-118">Data Item Type</span></span>|<span data-ttu-id="0fdaa-119">説明</span><span class="sxs-lookup"><span data-stu-id="0fdaa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0fdaa-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="0fdaa-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="0fdaa-121">呼び出された `MessageInspector` の型の CLR FullName。</span><span class="sxs-lookup"><span data-stu-id="0fdaa-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="0fdaa-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="0fdaa-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="0fdaa-123">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="0fdaa-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0fdaa-124">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="0fdaa-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0fdaa-125">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="0fdaa-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0fdaa-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0fdaa-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0fdaa-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="0fdaa-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
