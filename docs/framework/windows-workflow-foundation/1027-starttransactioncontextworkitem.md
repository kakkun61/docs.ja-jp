---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: cb5671ce7a30a7096104ba0ca6c4f36bed6b93f9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275233"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="aefd1-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="aefd1-102">1027 - StartTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="aefd1-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="aefd1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aefd1-104">ID</span><span class="sxs-lookup"><span data-stu-id="aefd1-104">ID</span></span>|<span data-ttu-id="aefd1-105">1027</span><span class="sxs-lookup"><span data-stu-id="aefd1-105">1027</span></span>|  
|<span data-ttu-id="aefd1-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="aefd1-106">Keywords</span></span>|<span data-ttu-id="aefd1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="aefd1-107">WFRuntime</span></span>|  
|<span data-ttu-id="aefd1-108">Level</span><span class="sxs-lookup"><span data-stu-id="aefd1-108">Level</span></span>|<span data-ttu-id="aefd1-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="aefd1-109">Verbose</span></span>|  
|<span data-ttu-id="aefd1-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="aefd1-110">Channel</span></span>|<span data-ttu-id="aefd1-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="aefd1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aefd1-112">Description</span><span class="sxs-lookup"><span data-stu-id="aefd1-112">Description</span></span>  

 <span data-ttu-id="aefd1-113">TransactionContextWorkItem が実行を開始していることを示します。</span><span class="sxs-lookup"><span data-stu-id="aefd1-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aefd1-114">Message</span><span class="sxs-lookup"><span data-stu-id="aefd1-114">Message</span></span>  

 <span data-ttu-id="aefd1-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem の実行を開始しています。</span><span class="sxs-lookup"><span data-stu-id="aefd1-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aefd1-116">詳細</span><span class="sxs-lookup"><span data-stu-id="aefd1-116">Details</span></span>  
  
|<span data-ttu-id="aefd1-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="aefd1-117">Data Item Name</span></span>|<span data-ttu-id="aefd1-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="aefd1-118">Data Item Type</span></span>|<span data-ttu-id="aefd1-119">Description</span><span class="sxs-lookup"><span data-stu-id="aefd1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aefd1-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="aefd1-120">Activity</span></span>|<span data-ttu-id="aefd1-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="aefd1-121">xs:string</span></span>|<span data-ttu-id="aefd1-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="aefd1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="aefd1-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="aefd1-123">DisplayName</span></span>|<span data-ttu-id="aefd1-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="aefd1-124">xs:string</span></span>|<span data-ttu-id="aefd1-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="aefd1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="aefd1-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="aefd1-126">InstanceId</span></span>|<span data-ttu-id="aefd1-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="aefd1-127">xs:string</span></span>|<span data-ttu-id="aefd1-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="aefd1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="aefd1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aefd1-129">AppDomain</span></span>|<span data-ttu-id="aefd1-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="aefd1-130">xs:string</span></span>|<span data-ttu-id="aefd1-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="aefd1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
