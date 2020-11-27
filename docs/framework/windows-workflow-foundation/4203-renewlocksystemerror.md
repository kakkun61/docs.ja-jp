---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 17617e25c5cf8cecae608438529e9ce1a7d506f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251270"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="d6b9b-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="d6b9b-102">4203 - RenewLockSystemError</span></span>

## <a name="properties"></a><span data-ttu-id="d6b9b-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="d6b9b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6b9b-104">ID</span><span class="sxs-lookup"><span data-stu-id="d6b9b-104">ID</span></span>|<span data-ttu-id="d6b9b-105">4203</span><span class="sxs-lookup"><span data-stu-id="d6b9b-105">4203</span></span>|  
|<span data-ttu-id="d6b9b-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="d6b9b-106">Keywords</span></span>|<span data-ttu-id="d6b9b-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="d6b9b-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="d6b9b-108">Level</span><span class="sxs-lookup"><span data-stu-id="d6b9b-108">Level</span></span>|<span data-ttu-id="d6b9b-109">エラー</span><span class="sxs-lookup"><span data-stu-id="d6b9b-109">Error</span></span>|  
|<span data-ttu-id="d6b9b-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="d6b9b-110">Channel</span></span>|<span data-ttu-id="d6b9b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="d6b9b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6b9b-112">Description</span><span class="sxs-lookup"><span data-stu-id="d6b9b-112">Description</span></span>  

 <span data-ttu-id="d6b9b-113">ロックの有効期限が既に過ぎているか、またはロック所有者が削除されたために、SQL プロバイダーはロックの有効期限を延長できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="d6b9b-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="d6b9b-114">SqlWorkflowInstanceStore は中止されます。</span><span class="sxs-lookup"><span data-stu-id="d6b9b-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6b9b-115">Message</span><span class="sxs-lookup"><span data-stu-id="d6b9b-115">Message</span></span>  

 <span data-ttu-id="d6b9b-116">ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。</span><span class="sxs-lookup"><span data-stu-id="d6b9b-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="d6b9b-117">SqlWorkflowInstanceStore を中止します。</span><span class="sxs-lookup"><span data-stu-id="d6b9b-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6b9b-118">詳細</span><span class="sxs-lookup"><span data-stu-id="d6b9b-118">Details</span></span>  
  
|<span data-ttu-id="d6b9b-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="d6b9b-119">Data Item Name</span></span>|<span data-ttu-id="d6b9b-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="d6b9b-120">Data Item Type</span></span>|<span data-ttu-id="d6b9b-121">Description</span><span class="sxs-lookup"><span data-stu-id="d6b9b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6b9b-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d6b9b-122">AppDomain</span></span>|<span data-ttu-id="d6b9b-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="d6b9b-123">xs:string</span></span>|<span data-ttu-id="d6b9b-124">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="d6b9b-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
