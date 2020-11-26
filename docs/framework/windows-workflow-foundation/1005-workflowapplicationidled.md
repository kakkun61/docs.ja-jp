---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 3b7210246b7fb754145c8aa6128da3183cea9f91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239862"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="7d8b8-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="7d8b8-102">1005 - WorkflowApplicationIdled</span></span>

## <a name="properties"></a><span data-ttu-id="7d8b8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="7d8b8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d8b8-104">ID</span><span class="sxs-lookup"><span data-stu-id="7d8b8-104">ID</span></span>|<span data-ttu-id="7d8b8-105">1005</span><span class="sxs-lookup"><span data-stu-id="7d8b8-105">1005</span></span>|  
|<span data-ttu-id="7d8b8-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="7d8b8-106">Keywords</span></span>|<span data-ttu-id="7d8b8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7d8b8-107">WFRuntime</span></span>|  
|<span data-ttu-id="7d8b8-108">Level</span><span class="sxs-lookup"><span data-stu-id="7d8b8-108">Level</span></span>|<span data-ttu-id="7d8b8-109">情報</span><span class="sxs-lookup"><span data-stu-id="7d8b8-109">Information</span></span>|  
|<span data-ttu-id="7d8b8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="7d8b8-110">Channel</span></span>|<span data-ttu-id="7d8b8-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="7d8b8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7d8b8-112">Description</span><span class="sxs-lookup"><span data-stu-id="7d8b8-112">Description</span></span>  

 <span data-ttu-id="7d8b8-113">ワークフロー アプリケーションがアイドル状態になったことを示します。</span><span class="sxs-lookup"><span data-stu-id="7d8b8-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7d8b8-114">Message</span><span class="sxs-lookup"><span data-stu-id="7d8b8-114">Message</span></span>  

 <span data-ttu-id="7d8b8-115">WorkflowApplication ID: '%1' がアイドル状態になりました。</span><span class="sxs-lookup"><span data-stu-id="7d8b8-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7d8b8-116">詳細</span><span class="sxs-lookup"><span data-stu-id="7d8b8-116">Details</span></span>  
  
|<span data-ttu-id="7d8b8-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="7d8b8-117">Data Item Name</span></span>|<span data-ttu-id="7d8b8-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="7d8b8-118">Data Item Type</span></span>|<span data-ttu-id="7d8b8-119">Description</span><span class="sxs-lookup"><span data-stu-id="7d8b8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7d8b8-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="7d8b8-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="7d8b8-121">ワークフロー アプリケーション ID</span><span class="sxs-lookup"><span data-stu-id="7d8b8-121">The workflow application id</span></span>|  
|<span data-ttu-id="7d8b8-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7d8b8-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7d8b8-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="7d8b8-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
