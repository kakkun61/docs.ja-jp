---
title: 1007 - WorkflowApplicationPersisted
ms.date: 03/30/2017
ms.assetid: f4ea4452-28e3-4e66-93c6-eb12ee29bcb1
ms.openlocfilehash: aa4c7b2c98924eb43f78ab23a145b93906e302fc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239810"
---
# <a name="1007---workflowapplicationpersisted"></a><span data-ttu-id="99517-102">1007 - WorkflowApplicationPersisted</span><span class="sxs-lookup"><span data-stu-id="99517-102">1007 - WorkflowApplicationPersisted</span></span>

## <a name="properties"></a><span data-ttu-id="99517-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="99517-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="99517-104">ID</span><span class="sxs-lookup"><span data-stu-id="99517-104">ID</span></span>|<span data-ttu-id="99517-105">1007</span><span class="sxs-lookup"><span data-stu-id="99517-105">1007</span></span>|  
|<span data-ttu-id="99517-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="99517-106">Keywords</span></span>|<span data-ttu-id="99517-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="99517-107">WFRuntime</span></span>|  
|<span data-ttu-id="99517-108">Level</span><span class="sxs-lookup"><span data-stu-id="99517-108">Level</span></span>|<span data-ttu-id="99517-109">情報</span><span class="sxs-lookup"><span data-stu-id="99517-109">Information</span></span>|  
|<span data-ttu-id="99517-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="99517-110">Channel</span></span>|<span data-ttu-id="99517-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="99517-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="99517-112">Description</span><span class="sxs-lookup"><span data-stu-id="99517-112">Description</span></span>  

 <span data-ttu-id="99517-113">ワークフロー アプリケーションが永続化されていることを示します。</span><span class="sxs-lookup"><span data-stu-id="99517-113">Indicates a workflow application has persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="99517-114">Message</span><span class="sxs-lookup"><span data-stu-id="99517-114">Message</span></span>  

 <span data-ttu-id="99517-115">WorkflowApplication ID: %1 が永続化されました。</span><span class="sxs-lookup"><span data-stu-id="99517-115">WorkflowApplication Id: '%1' was Persisted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="99517-116">詳細</span><span class="sxs-lookup"><span data-stu-id="99517-116">Details</span></span>  
  
|<span data-ttu-id="99517-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="99517-117">Data Item Name</span></span>|<span data-ttu-id="99517-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="99517-118">Data Item Type</span></span>|<span data-ttu-id="99517-119">Description</span><span class="sxs-lookup"><span data-stu-id="99517-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="99517-120">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="99517-120">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="99517-121">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="99517-121">The workflow application id</span></span>|  
|<span data-ttu-id="99517-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="99517-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="99517-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="99517-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
