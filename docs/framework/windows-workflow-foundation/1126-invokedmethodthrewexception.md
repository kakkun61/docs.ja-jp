---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 7caaebe42f49a62fec61ba17a4d3fe3a538e2ab4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262841"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="9ba55-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="9ba55-102">1126 - InvokedMethodThrewException</span></span>

## <a name="properties"></a><span data-ttu-id="9ba55-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="9ba55-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ba55-104">ID</span><span class="sxs-lookup"><span data-stu-id="9ba55-104">ID</span></span>|<span data-ttu-id="9ba55-105">1126</span><span class="sxs-lookup"><span data-stu-id="9ba55-105">1126</span></span>|  
|<span data-ttu-id="9ba55-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="9ba55-106">Keywords</span></span>|<span data-ttu-id="9ba55-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9ba55-107">WFRuntime</span></span>|  
|<span data-ttu-id="9ba55-108">Level</span><span class="sxs-lookup"><span data-stu-id="9ba55-108">Level</span></span>|<span data-ttu-id="9ba55-109">情報</span><span class="sxs-lookup"><span data-stu-id="9ba55-109">Information</span></span>|  
|<span data-ttu-id="9ba55-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="9ba55-110">Channel</span></span>|<span data-ttu-id="9ba55-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9ba55-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9ba55-112">Description</span><span class="sxs-lookup"><span data-stu-id="9ba55-112">Description</span></span>  

 <span data-ttu-id="9ba55-113">InvokeMethod アクティビティによって呼び出されたメソッドにより、例外がスローされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="9ba55-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9ba55-114">Message</span><span class="sxs-lookup"><span data-stu-id="9ba55-114">Message</span></span>  

 <span data-ttu-id="9ba55-115">アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。</span><span class="sxs-lookup"><span data-stu-id="9ba55-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="9ba55-116">%2</span><span class="sxs-lookup"><span data-stu-id="9ba55-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="9ba55-117">詳細</span><span class="sxs-lookup"><span data-stu-id="9ba55-117">Details</span></span>  
  
|<span data-ttu-id="9ba55-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="9ba55-118">Data Item Name</span></span>|<span data-ttu-id="9ba55-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="9ba55-119">Data Item Type</span></span>|<span data-ttu-id="9ba55-120">Description</span><span class="sxs-lookup"><span data-stu-id="9ba55-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9ba55-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="9ba55-121">InvokeMethod</span></span>|<span data-ttu-id="9ba55-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ba55-122">xs:string</span></span>|<span data-ttu-id="9ba55-123">InvokeMethod アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="9ba55-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="9ba55-124">例外</span><span class="sxs-lookup"><span data-stu-id="9ba55-124">Exception</span></span>|<span data-ttu-id="9ba55-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ba55-125">xs:string</span></span>|<span data-ttu-id="9ba55-126">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="9ba55-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="9ba55-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9ba55-127">AppDomain</span></span>|<span data-ttu-id="9ba55-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="9ba55-128">xs:string</span></span>|<span data-ttu-id="9ba55-129">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="9ba55-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
