---
title: 1002 - WorkflowApplicationTerminated
ms.date: 03/30/2017
ms.assetid: 4e8b111f-79dc-4898-bb4a-e9b36f69420f
ms.openlocfilehash: e7c92dcc9ce472c50af6f0aa26c59f55d62fbb9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239940"
---
# <a name="1002---workflowapplicationterminated"></a><span data-ttu-id="96a88-102">1002 - WorkflowApplicationTerminated</span><span class="sxs-lookup"><span data-stu-id="96a88-102">1002 - WorkflowApplicationTerminated</span></span>

## <a name="properties"></a><span data-ttu-id="96a88-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="96a88-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="96a88-104">ID</span><span class="sxs-lookup"><span data-stu-id="96a88-104">ID</span></span>|<span data-ttu-id="96a88-105">1002</span><span class="sxs-lookup"><span data-stu-id="96a88-105">1002</span></span>|  
|<span data-ttu-id="96a88-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="96a88-106">Keywords</span></span>|<span data-ttu-id="96a88-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="96a88-107">WFRuntime</span></span>|  
|<span data-ttu-id="96a88-108">Level</span><span class="sxs-lookup"><span data-stu-id="96a88-108">Level</span></span>|<span data-ttu-id="96a88-109">情報</span><span class="sxs-lookup"><span data-stu-id="96a88-109">Information</span></span>|  
|<span data-ttu-id="96a88-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="96a88-110">Channel</span></span>|<span data-ttu-id="96a88-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="96a88-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="96a88-112">Description</span><span class="sxs-lookup"><span data-stu-id="96a88-112">Description</span></span>  

 <span data-ttu-id="96a88-113">例外が発生し、ワークフロー アプリケーションが Faulted 状態で終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="96a88-113">Indicates a workflow application has terminated in the Faulted state with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="96a88-114">Message</span><span class="sxs-lookup"><span data-stu-id="96a88-114">Message</span></span>  

 <span data-ttu-id="96a88-115">WorkflowApplication ID: %1 は中止されました。</span><span class="sxs-lookup"><span data-stu-id="96a88-115">WorkflowApplication Id: '%1' was terminated.</span></span> <span data-ttu-id="96a88-116">例外により Faulted 状態で完了しました。</span><span class="sxs-lookup"><span data-stu-id="96a88-116">It has completed in the Faulted state with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="96a88-117">詳細</span><span class="sxs-lookup"><span data-stu-id="96a88-117">Details</span></span>  
  
|<span data-ttu-id="96a88-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="96a88-118">Data Item Name</span></span>|<span data-ttu-id="96a88-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="96a88-119">Data Item Type</span></span>|<span data-ttu-id="96a88-120">Description</span><span class="sxs-lookup"><span data-stu-id="96a88-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="96a88-121">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="96a88-121">WorkflowApplicationId</span></span>|`xs:string`|<span data-ttu-id="96a88-122">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="96a88-122">The workflow application id</span></span>|  
|<span data-ttu-id="96a88-123">例外</span><span class="sxs-lookup"><span data-stu-id="96a88-123">Exception</span></span>|`xs:string`|<span data-ttu-id="96a88-124">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="96a88-124">The exception details for the exception</span></span>|  
|<span data-ttu-id="96a88-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="96a88-125">AppDomain</span></span>|`xs:string`|<span data-ttu-id="96a88-126">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="96a88-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
