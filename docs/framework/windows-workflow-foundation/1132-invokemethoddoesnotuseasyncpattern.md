---
title: 1132 - InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 9249bdd0fe996ee7c1b04783ac8fef2c48063cc0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294158"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a><span data-ttu-id="bc19a-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span><span class="sxs-lookup"><span data-stu-id="bc19a-102">1132 - InvokeMethodDoesNotUseAsyncPattern</span></span>

## <a name="properties"></a><span data-ttu-id="bc19a-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bc19a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc19a-104">ID</span><span class="sxs-lookup"><span data-stu-id="bc19a-104">ID</span></span>|<span data-ttu-id="bc19a-105">1132</span><span class="sxs-lookup"><span data-stu-id="bc19a-105">1132</span></span>|  
|<span data-ttu-id="bc19a-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="bc19a-106">Keywords</span></span>|<span data-ttu-id="bc19a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bc19a-107">WFRuntime</span></span>|  
|<span data-ttu-id="bc19a-108">Level</span><span class="sxs-lookup"><span data-stu-id="bc19a-108">Level</span></span>|<span data-ttu-id="bc19a-109">情報</span><span class="sxs-lookup"><span data-stu-id="bc19a-109">Information</span></span>|  
|<span data-ttu-id="bc19a-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bc19a-110">Channel</span></span>|<span data-ttu-id="bc19a-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bc19a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc19a-112">Description</span><span class="sxs-lookup"><span data-stu-id="bc19a-112">Description</span></span>  

 <span data-ttu-id="bc19a-113">CacheMetadata 手順内で、InvokeMethod アクティビティがメソッドを呼び出すときに非同期パターンを使用しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="bc19a-113">During CacheMetadata step, InvokeMethod activity indicates that it is not using the async pattern when invoking the method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc19a-114">Message</span><span class="sxs-lookup"><span data-stu-id="bc19a-114">Message</span></span>  

 <span data-ttu-id="bc19a-115">InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="bc19a-115">InvokeMethod '%1' - method does not use asynchronous pattern.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc19a-116">詳細</span><span class="sxs-lookup"><span data-stu-id="bc19a-116">Details</span></span>  
  
|<span data-ttu-id="bc19a-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bc19a-117">Data Item Name</span></span>|<span data-ttu-id="bc19a-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bc19a-118">Data Item Type</span></span>|<span data-ttu-id="bc19a-119">Description</span><span class="sxs-lookup"><span data-stu-id="bc19a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc19a-120">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="bc19a-120">InvokeMethod</span></span>|<span data-ttu-id="bc19a-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc19a-121">xs:string</span></span>|<span data-ttu-id="bc19a-122">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bc19a-122">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="bc19a-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bc19a-123">AppDomain</span></span>|<span data-ttu-id="bc19a-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bc19a-124">xs:string</span></span>|<span data-ttu-id="bc19a-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bc19a-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
