---
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: 4bb76a93ec7a07a735def1f1d5dc79decb7792ad
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239835"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="c9244-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="c9244-102">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="c9244-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c9244-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9244-104">ID</span><span class="sxs-lookup"><span data-stu-id="c9244-104">ID</span></span>|<span data-ttu-id="c9244-105">1006</span><span class="sxs-lookup"><span data-stu-id="c9244-105">1006</span></span>|  
|<span data-ttu-id="c9244-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="c9244-106">Keywords</span></span>|<span data-ttu-id="c9244-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c9244-107">WFRuntime</span></span>|  
|<span data-ttu-id="c9244-108">Level</span><span class="sxs-lookup"><span data-stu-id="c9244-108">Level</span></span>|<span data-ttu-id="c9244-109">エラー</span><span class="sxs-lookup"><span data-stu-id="c9244-109">Error</span></span>|  
|<span data-ttu-id="c9244-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c9244-110">Channel</span></span>|<span data-ttu-id="c9244-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c9244-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c9244-112">Description</span><span class="sxs-lookup"><span data-stu-id="c9244-112">Description</span></span>  

 <span data-ttu-id="c9244-113">ワークフロー アプリケーションでハンドルされない例外が検出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="c9244-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c9244-114">Message</span><span class="sxs-lookup"><span data-stu-id="c9244-114">Message</span></span>  

 <span data-ttu-id="c9244-115">WorkflowInstance Id: ' %1 ' でハンドルされない例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="c9244-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="c9244-116">Activity ' %2 '、DisplayName: ' %3 ' から例外が発生しました。</span><span class="sxs-lookup"><span data-stu-id="c9244-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="c9244-117">次のアクションが実行されます: %4。</span><span class="sxs-lookup"><span data-stu-id="c9244-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c9244-118">詳細</span><span class="sxs-lookup"><span data-stu-id="c9244-118">Details</span></span>  
  
|<span data-ttu-id="c9244-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c9244-119">Data Item Name</span></span>|<span data-ttu-id="c9244-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c9244-120">Data Item Type</span></span>|<span data-ttu-id="c9244-121">Description</span><span class="sxs-lookup"><span data-stu-id="c9244-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c9244-122">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c9244-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="c9244-123">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="c9244-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="c9244-124">例外</span><span class="sxs-lookup"><span data-stu-id="c9244-124">Exception</span></span>|`xs:string`|<span data-ttu-id="c9244-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="c9244-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="c9244-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c9244-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c9244-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c9244-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
