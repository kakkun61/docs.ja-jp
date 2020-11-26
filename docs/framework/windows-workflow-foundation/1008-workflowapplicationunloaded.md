---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 6ea121e7901d877d4f0d8f9f5bfd259c2f93696d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239822"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="f3cbb-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="f3cbb-102">1008 - WorkflowApplicationUnloaded</span></span>

## <a name="properties"></a><span data-ttu-id="f3cbb-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f3cbb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3cbb-104">ID</span><span class="sxs-lookup"><span data-stu-id="f3cbb-104">ID</span></span>|<span data-ttu-id="f3cbb-105">1008</span><span class="sxs-lookup"><span data-stu-id="f3cbb-105">1008</span></span>|  
|<span data-ttu-id="f3cbb-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="f3cbb-106">Keywords</span></span>|<span data-ttu-id="f3cbb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f3cbb-107">WFRuntime</span></span>|  
|<span data-ttu-id="f3cbb-108">Level</span><span class="sxs-lookup"><span data-stu-id="f3cbb-108">Level</span></span>|<span data-ttu-id="f3cbb-109">情報</span><span class="sxs-lookup"><span data-stu-id="f3cbb-109">Information</span></span>|  
|<span data-ttu-id="f3cbb-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="f3cbb-110">Channel</span></span>|<span data-ttu-id="f3cbb-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="f3cbb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3cbb-112">Description</span><span class="sxs-lookup"><span data-stu-id="f3cbb-112">Description</span></span>  

 <span data-ttu-id="f3cbb-113">ワークフロー アプリケーションがアンロードしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="f3cbb-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3cbb-114">Message</span><span class="sxs-lookup"><span data-stu-id="f3cbb-114">Message</span></span>  

 <span data-ttu-id="f3cbb-115">WorkflowInstance ID: '%1' がアンロードされました。</span><span class="sxs-lookup"><span data-stu-id="f3cbb-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3cbb-116">詳細</span><span class="sxs-lookup"><span data-stu-id="f3cbb-116">Details</span></span>  
  
|<span data-ttu-id="f3cbb-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="f3cbb-117">Data Item Name</span></span>|<span data-ttu-id="f3cbb-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="f3cbb-118">Data Item Type</span></span>|<span data-ttu-id="f3cbb-119">Description</span><span class="sxs-lookup"><span data-stu-id="f3cbb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3cbb-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="f3cbb-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="f3cbb-121">ワークフローのインスタンス ID</span><span class="sxs-lookup"><span data-stu-id="f3cbb-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="f3cbb-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3cbb-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f3cbb-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="f3cbb-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
