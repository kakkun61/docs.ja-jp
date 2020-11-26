---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: dc47aa36b5a409c89aaf7963ce51f11cdf84b0fc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247578"
---
# <a name="499---transferemitted"></a><span data-ttu-id="f2cd1-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="f2cd1-102">499 - TransferEmitted</span></span>

## <a name="properties"></a><span data-ttu-id="f2cd1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f2cd1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2cd1-104">ID</span><span class="sxs-lookup"><span data-stu-id="f2cd1-104">ID</span></span>|<span data-ttu-id="f2cd1-105">499</span><span class="sxs-lookup"><span data-stu-id="f2cd1-105">499</span></span>|  
|<span data-ttu-id="f2cd1-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="f2cd1-106">Keywords</span></span>|<span data-ttu-id="f2cd1-107">Troubleshooting、UserEvents、EndToEndMonitoring、ServiceModel、WFTracking、ServiceHost、WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="f2cd1-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="f2cd1-108">Level</span><span class="sxs-lookup"><span data-stu-id="f2cd1-108">Level</span></span>|<span data-ttu-id="f2cd1-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="f2cd1-109">LogAlways</span></span>|  
|<span data-ttu-id="f2cd1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f2cd1-110">Channel</span></span>|<span data-ttu-id="f2cd1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f2cd1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f2cd1-112">Description</span><span class="sxs-lookup"><span data-stu-id="f2cd1-112">Description</span></span>  

 <span data-ttu-id="f2cd1-113">このイベントは、転送イベントが発生したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="f2cd1-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f2cd1-114">Message</span><span class="sxs-lookup"><span data-stu-id="f2cd1-114">Message</span></span>  

 <span data-ttu-id="f2cd1-115">転送イベントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="f2cd1-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f2cd1-116">詳細</span><span class="sxs-lookup"><span data-stu-id="f2cd1-116">Details</span></span>  
  
|<span data-ttu-id="f2cd1-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f2cd1-117">Data Item Name</span></span>|<span data-ttu-id="f2cd1-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f2cd1-118">Data Item Type</span></span>|<span data-ttu-id="f2cd1-119">Description</span><span class="sxs-lookup"><span data-stu-id="f2cd1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f2cd1-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="f2cd1-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="f2cd1-121">Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。</span><span class="sxs-lookup"><span data-stu-id="f2cd1-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f2cd1-122">この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。</span><span class="sxs-lookup"><span data-stu-id="f2cd1-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f2cd1-123">例: ' 既定の Web サイト/計算 Atorapplication&#124;/電卓&#124;電卓 Atorservice '。</span><span class="sxs-lookup"><span data-stu-id="f2cd1-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f2cd1-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f2cd1-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f2cd1-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f2cd1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
