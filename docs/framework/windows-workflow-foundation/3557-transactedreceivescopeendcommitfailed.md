---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 4a4979047481687ef0d5c9d5891dec8f2826beed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263660"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="cbd73-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="cbd73-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>

## <a name="properties"></a><span data-ttu-id="cbd73-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cbd73-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cbd73-104">ID</span><span class="sxs-lookup"><span data-stu-id="cbd73-104">ID</span></span>|<span data-ttu-id="cbd73-105">3557</span><span class="sxs-lookup"><span data-stu-id="cbd73-105">3557</span></span>|  
|<span data-ttu-id="cbd73-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="cbd73-106">Keywords</span></span>|<span data-ttu-id="cbd73-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="cbd73-107">WFServices</span></span>|  
|<span data-ttu-id="cbd73-108">Level</span><span class="sxs-lookup"><span data-stu-id="cbd73-108">Level</span></span>|<span data-ttu-id="cbd73-109">情報</span><span class="sxs-lookup"><span data-stu-id="cbd73-109">Information</span></span>|  
|<span data-ttu-id="cbd73-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="cbd73-110">Channel</span></span>|<span data-ttu-id="cbd73-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="cbd73-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cbd73-112">Description</span><span class="sxs-lookup"><span data-stu-id="cbd73-112">Description</span></span>  

 <span data-ttu-id="cbd73-113">CommittableTransaction の EndCommit への呼び出しが TransactionException をスローしたことを示します。</span><span class="sxs-lookup"><span data-stu-id="cbd73-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cbd73-114">Message</span><span class="sxs-lookup"><span data-stu-id="cbd73-114">Message</span></span>  

 <span data-ttu-id="cbd73-115">id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。</span><span class="sxs-lookup"><span data-stu-id="cbd73-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cbd73-116">詳細</span><span class="sxs-lookup"><span data-stu-id="cbd73-116">Details</span></span>  
  
|<span data-ttu-id="cbd73-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="cbd73-117">Data Item Name</span></span>|<span data-ttu-id="cbd73-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="cbd73-118">Data Item Type</span></span>|<span data-ttu-id="cbd73-119">Description</span><span class="sxs-lookup"><span data-stu-id="cbd73-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cbd73-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="cbd73-120">TransactionId</span></span>|<span data-ttu-id="cbd73-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="cbd73-121">xs:string</span></span>|<span data-ttu-id="cbd73-122">CommittableTransaction の ID。</span><span class="sxs-lookup"><span data-stu-id="cbd73-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="cbd73-123">例外</span><span class="sxs-lookup"><span data-stu-id="cbd73-123">Exception</span></span>|<span data-ttu-id="cbd73-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="cbd73-124">xs:string</span></span>|<span data-ttu-id="cbd73-125">例外の詳細</span><span class="sxs-lookup"><span data-stu-id="cbd73-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="cbd73-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cbd73-126">AppDomain</span></span>|<span data-ttu-id="cbd73-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="cbd73-127">xs:string</span></span>|<span data-ttu-id="cbd73-128">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="cbd73-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
