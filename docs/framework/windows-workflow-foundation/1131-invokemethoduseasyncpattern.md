---
title: 1131 - InvokeMethodUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: eca50fa7-5276-4759-ad1c-e490b9bd1f82
ms.openlocfilehash: 2192b63b8a08657b69f6e3984f898bd6baddbc5f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294184"
---
# <a name="1131---invokemethoduseasyncpattern"></a><span data-ttu-id="e9236-102">1131 - InvokeMethodUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="e9236-102">1131 - InvokeMethodUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="e9236-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="e9236-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e9236-104">ID</span><span class="sxs-lookup"><span data-stu-id="e9236-104">ID</span></span>|<span data-ttu-id="e9236-105">1131</span><span class="sxs-lookup"><span data-stu-id="e9236-105">1131</span></span>|  
|<span data-ttu-id="e9236-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="e9236-106">Keywords</span></span>|<span data-ttu-id="e9236-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e9236-107">WFRuntime</span></span>|  
|<span data-ttu-id="e9236-108">Level</span><span class="sxs-lookup"><span data-stu-id="e9236-108">Level</span></span>|<span data-ttu-id="e9236-109">情報</span><span class="sxs-lookup"><span data-stu-id="e9236-109">Information</span></span>|  
|<span data-ttu-id="e9236-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="e9236-110">Channel</span></span>|<span data-ttu-id="e9236-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="e9236-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e9236-112">Description</span><span class="sxs-lookup"><span data-stu-id="e9236-112">Description</span></span>  

 <span data-ttu-id="e9236-113">CacheMetadata の手順では、InvokeMethod アクティビティはメソッドを呼び出すときの非同期パターンを使用していることを示します。</span><span class="sxs-lookup"><span data-stu-id="e9236-113">During CacheMetadata step, InvokeMethod activity indicates that it is using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e9236-114">Message</span><span class="sxs-lookup"><span data-stu-id="e9236-114">Message</span></span>  

 <span data-ttu-id="e9236-115">InvokeMethod '%1' - メソッドでは '%2' および '%3' の非同期パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="e9236-115">InvokeMethod '%1' - method uses asynchronous pattern of '%2' and '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e9236-116">詳細</span><span class="sxs-lookup"><span data-stu-id="e9236-116">Details</span></span>  
  
|<span data-ttu-id="e9236-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="e9236-117">Data Item Name</span></span>|<span data-ttu-id="e9236-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="e9236-118">Data Item Type</span></span>|<span data-ttu-id="e9236-119">Description</span><span class="sxs-lookup"><span data-stu-id="e9236-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e9236-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="e9236-120">InvokeMethod</span></span>|<span data-ttu-id="e9236-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9236-121">xs:string</span></span>|<span data-ttu-id="e9236-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="e9236-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="e9236-123">BeginMethod</span><span class="sxs-lookup"><span data-stu-id="e9236-123">BeginMethod</span></span>|<span data-ttu-id="e9236-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9236-124">xs:string</span></span>|<span data-ttu-id="e9236-125">begin メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="e9236-125">The name of the begin method.</span></span>|  
|<span data-ttu-id="e9236-126">EndMethod</span><span class="sxs-lookup"><span data-stu-id="e9236-126">EndMethod</span></span>|<span data-ttu-id="e9236-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9236-127">xs:string</span></span>|<span data-ttu-id="e9236-128">end メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="e9236-128">The name of the end method.</span></span>|  
|<span data-ttu-id="e9236-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e9236-129">AppDomain</span></span>|<span data-ttu-id="e9236-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="e9236-130">xs:string</span></span>|<span data-ttu-id="e9236-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="e9236-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
