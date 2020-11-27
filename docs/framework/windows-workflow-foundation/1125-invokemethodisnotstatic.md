---
title: 1125 - InvokeMethodIsNotStatic
ms.date: 03/30/2017
ms.assetid: ea2b3827-63da-497b-b2c3-d5cebefe57a1
ms.openlocfilehash: 0405b4e1207db5c056fbd478b98c408258daf0c3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294210"
---
# <a name="1125---invokemethodisnotstatic"></a><span data-ttu-id="ef9a5-102">1125 - InvokeMethodIsNotStatic</span><span class="sxs-lookup"><span data-stu-id="ef9a5-102">1125 - InvokeMethodIsNotStatic</span></span>

## <a name="properties"></a><span data-ttu-id="ef9a5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ef9a5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef9a5-104">ID</span><span class="sxs-lookup"><span data-stu-id="ef9a5-104">ID</span></span>|<span data-ttu-id="ef9a5-105">1125</span><span class="sxs-lookup"><span data-stu-id="ef9a5-105">1125</span></span>|  
|<span data-ttu-id="ef9a5-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="ef9a5-106">Keywords</span></span>|<span data-ttu-id="ef9a5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="ef9a5-107">WFRuntime</span></span>|  
|<span data-ttu-id="ef9a5-108">Level</span><span class="sxs-lookup"><span data-stu-id="ef9a5-108">Level</span></span>|<span data-ttu-id="ef9a5-109">情報</span><span class="sxs-lookup"><span data-stu-id="ef9a5-109">Information</span></span>|  
|<span data-ttu-id="ef9a5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ef9a5-110">Channel</span></span>|<span data-ttu-id="ef9a5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ef9a5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef9a5-112">Description</span><span class="sxs-lookup"><span data-stu-id="ef9a5-112">Description</span></span>  

 <span data-ttu-id="ef9a5-113">CacheMetadata の手順では、InvokeMethod アクティビティは、呼び出すメソッドが静的ではないことを示します。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-113">During CacheMetadata step, InvokeMethod activity indicates the method to be invoked is not static.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef9a5-114">Message</span><span class="sxs-lookup"><span data-stu-id="ef9a5-114">Message</span></span>  

 <span data-ttu-id="ef9a5-115">InvokeMethod '%1' - メソッドは Static ではありません。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-115">InvokeMethod '%1' - method is not Static.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef9a5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="ef9a5-116">Details</span></span>  
  
|<span data-ttu-id="ef9a5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ef9a5-117">Data Item Name</span></span>|<span data-ttu-id="ef9a5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ef9a5-118">Data Item Type</span></span>|<span data-ttu-id="ef9a5-119">Description</span><span class="sxs-lookup"><span data-stu-id="ef9a5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef9a5-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="ef9a5-120">InvokeMethod</span></span>|<span data-ttu-id="ef9a5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef9a5-121">xs:string</span></span>|<span data-ttu-id="ef9a5-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="ef9a5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef9a5-123">AppDomain</span></span>|<span data-ttu-id="ef9a5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef9a5-124">xs:string</span></span>|<span data-ttu-id="ef9a5-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ef9a5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
