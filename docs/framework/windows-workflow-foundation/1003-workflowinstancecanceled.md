---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: bd8abf173ab6588d4a35ba59c6cd14fb53445e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239901"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="cebe4-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="cebe4-102">1003 - WorkflowInstanceCanceled</span></span>

## <a name="properties"></a><span data-ttu-id="cebe4-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cebe4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cebe4-104">ID</span><span class="sxs-lookup"><span data-stu-id="cebe4-104">ID</span></span>|<span data-ttu-id="cebe4-105">1003</span><span class="sxs-lookup"><span data-stu-id="cebe4-105">1003</span></span>|  
|<span data-ttu-id="cebe4-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="cebe4-106">Keywords</span></span>|<span data-ttu-id="cebe4-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="cebe4-107">WFRuntime</span></span>|  
|<span data-ttu-id="cebe4-108">Level</span><span class="sxs-lookup"><span data-stu-id="cebe4-108">Level</span></span>|<span data-ttu-id="cebe4-109">情報</span><span class="sxs-lookup"><span data-stu-id="cebe4-109">Information</span></span>|  
|<span data-ttu-id="cebe4-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="cebe4-110">Channel</span></span>|<span data-ttu-id="cebe4-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="cebe4-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cebe4-112">Description</span><span class="sxs-lookup"><span data-stu-id="cebe4-112">Description</span></span>  

 <span data-ttu-id="cebe4-113">ワークフロー インスタンスが Canceled 状態で完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cebe4-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cebe4-114">Message</span><span class="sxs-lookup"><span data-stu-id="cebe4-114">Message</span></span>  

 <span data-ttu-id="cebe4-115">WorkflowInstance ID: %1 は Canceled 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="cebe4-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cebe4-116">詳細</span><span class="sxs-lookup"><span data-stu-id="cebe4-116">Details</span></span>  
  
|<span data-ttu-id="cebe4-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="cebe4-117">Data Item Name</span></span>|<span data-ttu-id="cebe4-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="cebe4-118">Data Item Type</span></span>|<span data-ttu-id="cebe4-119">Description</span><span class="sxs-lookup"><span data-stu-id="cebe4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cebe4-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="cebe4-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="cebe4-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="cebe4-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="cebe4-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cebe4-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cebe4-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="cebe4-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
