---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: be97991be9b61908a23486da0ef255ebfbdc5485
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239953"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="5fdf8-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="5fdf8-102">1001 - WorkflowApplicationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="5fdf8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="5fdf8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fdf8-104">ID</span><span class="sxs-lookup"><span data-stu-id="5fdf8-104">ID</span></span>|<span data-ttu-id="5fdf8-105">1001</span><span class="sxs-lookup"><span data-stu-id="5fdf8-105">1001</span></span>|  
|<span data-ttu-id="5fdf8-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="5fdf8-106">Keywords</span></span>|<span data-ttu-id="5fdf8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5fdf8-107">WFRuntime</span></span>|  
|<span data-ttu-id="5fdf8-108">Level</span><span class="sxs-lookup"><span data-stu-id="5fdf8-108">Level</span></span>|<span data-ttu-id="5fdf8-109">情報</span><span class="sxs-lookup"><span data-stu-id="5fdf8-109">Information</span></span>|  
|<span data-ttu-id="5fdf8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="5fdf8-110">Channel</span></span>|<span data-ttu-id="5fdf8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="5fdf8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5fdf8-112">Description</span><span class="sxs-lookup"><span data-stu-id="5fdf8-112">Description</span></span>  

 <span data-ttu-id="5fdf8-113">ワークフロー アプリケーションが Closed 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="5fdf8-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5fdf8-114">Message</span><span class="sxs-lookup"><span data-stu-id="5fdf8-114">Message</span></span>  

 <span data-ttu-id="5fdf8-115">WorkflowInstance ID: %1 は Closed 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="5fdf8-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5fdf8-116">詳細</span><span class="sxs-lookup"><span data-stu-id="5fdf8-116">Details</span></span>  
  
|<span data-ttu-id="5fdf8-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="5fdf8-117">Data Item Name</span></span>|<span data-ttu-id="5fdf8-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="5fdf8-118">Data Item Type</span></span>|<span data-ttu-id="5fdf8-119">Description</span><span class="sxs-lookup"><span data-stu-id="5fdf8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5fdf8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="5fdf8-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="5fdf8-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="5fdf8-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="5fdf8-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5fdf8-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5fdf8-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="5fdf8-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
