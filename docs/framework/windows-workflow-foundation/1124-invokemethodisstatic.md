---
title: 1124 - InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: d7ad99131f9813c2102f52784fc33605bed37557
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242124"
---
# <a name="1124---invokemethodisstatic"></a><span data-ttu-id="aa24f-102">1124 - InvokeMethodIsStatic</span><span class="sxs-lookup"><span data-stu-id="aa24f-102">1124 - InvokeMethodIsStatic</span></span>

## <a name="properties"></a><span data-ttu-id="aa24f-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="aa24f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa24f-104">ID</span><span class="sxs-lookup"><span data-stu-id="aa24f-104">ID</span></span>|<span data-ttu-id="aa24f-105">1124</span><span class="sxs-lookup"><span data-stu-id="aa24f-105">1124</span></span>|  
|<span data-ttu-id="aa24f-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="aa24f-106">Keywords</span></span>|<span data-ttu-id="aa24f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aa24f-107">WFRuntime</span></span>|  
|<span data-ttu-id="aa24f-108">Level</span><span class="sxs-lookup"><span data-stu-id="aa24f-108">Level</span></span>|<span data-ttu-id="aa24f-109">情報</span><span class="sxs-lookup"><span data-stu-id="aa24f-109">Information</span></span>|  
|<span data-ttu-id="aa24f-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="aa24f-110">Channel</span></span>|<span data-ttu-id="aa24f-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="aa24f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aa24f-112">Description</span><span class="sxs-lookup"><span data-stu-id="aa24f-112">Description</span></span>  

 <span data-ttu-id="aa24f-113">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的であることを示します。</span><span class="sxs-lookup"><span data-stu-id="aa24f-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aa24f-114">Message</span><span class="sxs-lookup"><span data-stu-id="aa24f-114">Message</span></span>  

 <span data-ttu-id="aa24f-115">InvokeMethod '%1' - メソッドは Static です。</span><span class="sxs-lookup"><span data-stu-id="aa24f-115">InvokeMethod '%1' - method is Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aa24f-116">詳細</span><span class="sxs-lookup"><span data-stu-id="aa24f-116">Details</span></span>  
  
|<span data-ttu-id="aa24f-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="aa24f-117">Data Item Name</span></span>|<span data-ttu-id="aa24f-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="aa24f-118">Data Item Type</span></span>|<span data-ttu-id="aa24f-119">Description</span><span class="sxs-lookup"><span data-stu-id="aa24f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aa24f-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="aa24f-120">InvokeMethod</span></span>|<span data-ttu-id="aa24f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="aa24f-121">xs:string</span></span>|<span data-ttu-id="aa24f-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="aa24f-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="aa24f-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aa24f-123">AppDomain</span></span>|<span data-ttu-id="aa24f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="aa24f-124">xs:string</span></span>|<span data-ttu-id="aa24f-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="aa24f-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
