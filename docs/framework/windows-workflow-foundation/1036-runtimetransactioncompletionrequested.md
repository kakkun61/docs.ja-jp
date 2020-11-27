---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 96ea253fd61652a3719eaf8b1a4d31aa88337eeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294262"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="bb95c-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="bb95c-102">1036 - RuntimeTransactionCompletionRequested</span></span>

## <a name="properties"></a><span data-ttu-id="bb95c-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="bb95c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bb95c-104">ID</span><span class="sxs-lookup"><span data-stu-id="bb95c-104">ID</span></span>|<span data-ttu-id="bb95c-105">1036</span><span class="sxs-lookup"><span data-stu-id="bb95c-105">1036</span></span>|  
|<span data-ttu-id="bb95c-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="bb95c-106">Keywords</span></span>|<span data-ttu-id="bb95c-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bb95c-107">WFRuntime</span></span>|  
|<span data-ttu-id="bb95c-108">Level</span><span class="sxs-lookup"><span data-stu-id="bb95c-108">Level</span></span>|<span data-ttu-id="bb95c-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="bb95c-109">Verbose</span></span>|  
|<span data-ttu-id="bb95c-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="bb95c-110">Channel</span></span>|<span data-ttu-id="bb95c-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="bb95c-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bb95c-112">Description</span><span class="sxs-lookup"><span data-stu-id="bb95c-112">Description</span></span>  

 <span data-ttu-id="bb95c-113">アクティビティがランタイムのトランザクションの完了をスケジュールしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="bb95c-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bb95c-114">Message</span><span class="sxs-lookup"><span data-stu-id="bb95c-114">Message</span></span>  

 <span data-ttu-id="bb95c-115">Activity '%1'、DisplayName: '%2'、InstanceId: '%3' はランタイム トランザクションの完了をスケジュールしました。</span><span class="sxs-lookup"><span data-stu-id="bb95c-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bb95c-116">詳細</span><span class="sxs-lookup"><span data-stu-id="bb95c-116">Details</span></span>  
  
|<span data-ttu-id="bb95c-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="bb95c-117">Data Item Name</span></span>|<span data-ttu-id="bb95c-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="bb95c-118">Data Item Type</span></span>|<span data-ttu-id="bb95c-119">Description</span><span class="sxs-lookup"><span data-stu-id="bb95c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bb95c-120">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="bb95c-120">Activity</span></span>|<span data-ttu-id="bb95c-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb95c-121">xs:string</span></span>|<span data-ttu-id="bb95c-122">アクティビティの型名。</span><span class="sxs-lookup"><span data-stu-id="bb95c-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bb95c-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="bb95c-123">DisplayName</span></span>|<span data-ttu-id="bb95c-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb95c-124">xs:string</span></span>|<span data-ttu-id="bb95c-125">アクティビティの表示名。</span><span class="sxs-lookup"><span data-stu-id="bb95c-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bb95c-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="bb95c-126">InstanceId</span></span>|<span data-ttu-id="bb95c-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb95c-127">xs:string</span></span>|<span data-ttu-id="bb95c-128">アクティビティのインスタンス ID。</span><span class="sxs-lookup"><span data-stu-id="bb95c-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bb95c-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bb95c-129">AppDomain</span></span>|<span data-ttu-id="bb95c-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="bb95c-130">xs:string</span></span>|<span data-ttu-id="bb95c-131">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="bb95c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
