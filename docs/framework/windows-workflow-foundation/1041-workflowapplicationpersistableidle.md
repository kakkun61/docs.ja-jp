---
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: 9995823753fc78ca3f278cd635fcf6c7d2b84325
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238939"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="f48a8-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="f48a8-102">1041 - WorkflowApplicationPersistableIdle</span></span>

## <a name="properties"></a><span data-ttu-id="f48a8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f48a8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f48a8-104">ID</span><span class="sxs-lookup"><span data-stu-id="f48a8-104">ID</span></span>|<span data-ttu-id="f48a8-105">1041</span><span class="sxs-lookup"><span data-stu-id="f48a8-105">1041</span></span>|  
|<span data-ttu-id="f48a8-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="f48a8-106">Keywords</span></span>|<span data-ttu-id="f48a8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f48a8-107">WFRuntime</span></span>|  
|<span data-ttu-id="f48a8-108">Level</span><span class="sxs-lookup"><span data-stu-id="f48a8-108">Level</span></span>|<span data-ttu-id="f48a8-109">情報</span><span class="sxs-lookup"><span data-stu-id="f48a8-109">Information</span></span>|  
|<span data-ttu-id="f48a8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f48a8-110">Channel</span></span>|<span data-ttu-id="f48a8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f48a8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f48a8-112">Description</span><span class="sxs-lookup"><span data-stu-id="f48a8-112">Description</span></span>  

 <span data-ttu-id="f48a8-113">ワークフロー アプリケーションがアイドル状態のままであることを示します。</span><span class="sxs-lookup"><span data-stu-id="f48a8-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="f48a8-114">ワークフロー アプリケーションはアイドル状態または永続化されます。</span><span class="sxs-lookup"><span data-stu-id="f48a8-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f48a8-115">Message</span><span class="sxs-lookup"><span data-stu-id="f48a8-115">Message</span></span>  

 <span data-ttu-id="f48a8-116">WorkflowApplication Id: ' %1 ' はアイドル状態で、持続可能です。</span><span class="sxs-lookup"><span data-stu-id="f48a8-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="f48a8-117">次のアクションが実行されます: %2。</span><span class="sxs-lookup"><span data-stu-id="f48a8-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f48a8-118">詳細</span><span class="sxs-lookup"><span data-stu-id="f48a8-118">Details</span></span>  
  
|<span data-ttu-id="f48a8-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f48a8-119">Data Item Name</span></span>|<span data-ttu-id="f48a8-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f48a8-120">Data Item Type</span></span>|<span data-ttu-id="f48a8-121">Description</span><span class="sxs-lookup"><span data-stu-id="f48a8-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f48a8-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="f48a8-122">WorkflowApplicationId</span></span>|<span data-ttu-id="f48a8-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="f48a8-123">xs:string</span></span>|<span data-ttu-id="f48a8-124">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="f48a8-124">The workflow application id</span></span>|  
|<span data-ttu-id="f48a8-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="f48a8-125">ActionTaken</span></span>|<span data-ttu-id="f48a8-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="f48a8-126">xs:string</span></span>|<span data-ttu-id="f48a8-127">ワークフロー アプリケーションで実行されるアクション。</span><span class="sxs-lookup"><span data-stu-id="f48a8-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="f48a8-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f48a8-128">AppDomain</span></span>|<span data-ttu-id="f48a8-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="f48a8-129">xs:string</span></span>|<span data-ttu-id="f48a8-130">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f48a8-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
