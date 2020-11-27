---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 2fc509dac7e13f30f74c24d8b98cba55ed5f8e1d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275116"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="076c8-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="076c8-102">1028 - CompleteTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="076c8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="076c8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="076c8-104">ID</span><span class="sxs-lookup"><span data-stu-id="076c8-104">ID</span></span>|<span data-ttu-id="076c8-105">1028</span><span class="sxs-lookup"><span data-stu-id="076c8-105">1028</span></span>|  
|<span data-ttu-id="076c8-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="076c8-106">Keywords</span></span>|<span data-ttu-id="076c8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="076c8-107">WFRuntime</span></span>|  
|<span data-ttu-id="076c8-108">Level</span><span class="sxs-lookup"><span data-stu-id="076c8-108">Level</span></span>|<span data-ttu-id="076c8-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="076c8-109">Verbose</span></span>|  
|<span data-ttu-id="076c8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="076c8-110">Channel</span></span>|<span data-ttu-id="076c8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="076c8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="076c8-112">Description</span><span class="sxs-lookup"><span data-stu-id="076c8-112">Description</span></span>  

 <span data-ttu-id="076c8-113">TransactionContextWorkItem が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="076c8-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="076c8-114">Message</span><span class="sxs-lookup"><span data-stu-id="076c8-114">Message</span></span>  

 <span data-ttu-id="076c8-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem が完了しました。</span><span class="sxs-lookup"><span data-stu-id="076c8-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="076c8-116">詳細</span><span class="sxs-lookup"><span data-stu-id="076c8-116">Details</span></span>  
  
|<span data-ttu-id="076c8-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="076c8-117">Data Item Name</span></span>|<span data-ttu-id="076c8-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="076c8-118">Data Item Type</span></span>|<span data-ttu-id="076c8-119">Description</span><span class="sxs-lookup"><span data-stu-id="076c8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="076c8-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="076c8-120">Activity</span></span>|<span data-ttu-id="076c8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="076c8-121">xs:string</span></span>|<span data-ttu-id="076c8-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="076c8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="076c8-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="076c8-123">DisplayName</span></span>|<span data-ttu-id="076c8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="076c8-124">xs:string</span></span>|<span data-ttu-id="076c8-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="076c8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="076c8-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="076c8-126">InstanceId</span></span>|<span data-ttu-id="076c8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="076c8-127">xs:string</span></span>|<span data-ttu-id="076c8-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="076c8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="076c8-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="076c8-129">AppDomain</span></span>|<span data-ttu-id="076c8-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="076c8-130">xs:string</span></span>|<span data-ttu-id="076c8-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="076c8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
