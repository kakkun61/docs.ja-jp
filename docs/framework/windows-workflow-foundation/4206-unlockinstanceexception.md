---
title: 4206 - UnlockInstanceException
ms.date: 03/30/2017
ms.assetid: 5a46dc5f-d517-4135-8905-25a42f01206b
ms.openlocfilehash: 48182d7c5fe8f29842a17f28c0ea296f93b31089
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251257"
---
# <a name="4206---unlockinstanceexception"></a><span data-ttu-id="68b6e-102">4206 - UnlockInstanceException</span><span class="sxs-lookup"><span data-stu-id="68b6e-102">4206 - UnlockInstanceException</span></span>

## <a name="properties"></a><span data-ttu-id="68b6e-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="68b6e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="68b6e-104">ID</span><span class="sxs-lookup"><span data-stu-id="68b6e-104">ID</span></span>|<span data-ttu-id="68b6e-105">4206</span><span class="sxs-lookup"><span data-stu-id="68b6e-105">4206</span></span>|  
|<span data-ttu-id="68b6e-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="68b6e-106">Keywords</span></span>|<span data-ttu-id="68b6e-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="68b6e-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="68b6e-108">Level</span><span class="sxs-lookup"><span data-stu-id="68b6e-108">Level</span></span>|<span data-ttu-id="68b6e-109">エラー</span><span class="sxs-lookup"><span data-stu-id="68b6e-109">Error</span></span>|  
|<span data-ttu-id="68b6e-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="68b6e-110">Channel</span></span>|<span data-ttu-id="68b6e-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="68b6e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="68b6e-112">Description</span><span class="sxs-lookup"><span data-stu-id="68b6e-112">Description</span></span>  

 <span data-ttu-id="68b6e-113">インスタンスのロックを解除しようとしているときに例外が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="68b6e-113">Indicates an exception was encountered while trying to unlock an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="68b6e-114">Message</span><span class="sxs-lookup"><span data-stu-id="68b6e-114">Message</span></span>  

 <span data-ttu-id="68b6e-115">インスタンスのロックを解除しようとして、例外 %1 が発生しました。</span><span class="sxs-lookup"><span data-stu-id="68b6e-115">Encountered exception %1 while attempting to unlock instance.</span></span>  
  
## <a name="details"></a><span data-ttu-id="68b6e-116">詳細</span><span class="sxs-lookup"><span data-stu-id="68b6e-116">Details</span></span>  
  
|<span data-ttu-id="68b6e-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="68b6e-117">Data Item Name</span></span>|<span data-ttu-id="68b6e-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="68b6e-118">Data Item Type</span></span>|<span data-ttu-id="68b6e-119">Description</span><span class="sxs-lookup"><span data-stu-id="68b6e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="68b6e-120">ExceptionMessage</span><span class="sxs-lookup"><span data-stu-id="68b6e-120">ExceptionMessage</span></span>|<span data-ttu-id="68b6e-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="68b6e-121">xs:string</span></span>|<span data-ttu-id="68b6e-122">SQL 例外からのメッセージ。</span><span class="sxs-lookup"><span data-stu-id="68b6e-122">The message from the SQL exception.</span></span>|  
|<span data-ttu-id="68b6e-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="68b6e-123">AppDomain</span></span>|<span data-ttu-id="68b6e-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="68b6e-124">xs:string</span></span>|<span data-ttu-id="68b6e-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="68b6e-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
