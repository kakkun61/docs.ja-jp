---
title: 4209 - TimeoutOpeningSqlConnection
ms.date: 03/30/2017
ms.assetid: f0e56518-9758-41dc-a760-50d1a10fba6e
ms.openlocfilehash: 9aa8cdffebb0cdf8b1e8225a394edf78ecf032b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238679"
---
# <a name="4209---timeoutopeningsqlconnection"></a><span data-ttu-id="16d68-102">4209 - TimeoutOpeningSqlConnection</span><span class="sxs-lookup"><span data-stu-id="16d68-102">4209 - TimeoutOpeningSqlConnection</span></span>

## <a name="properties"></a><span data-ttu-id="16d68-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="16d68-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16d68-104">ID</span><span class="sxs-lookup"><span data-stu-id="16d68-104">ID</span></span>|<span data-ttu-id="16d68-105">4209</span><span class="sxs-lookup"><span data-stu-id="16d68-105">4209</span></span>|  
|<span data-ttu-id="16d68-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="16d68-106">Keywords</span></span>|<span data-ttu-id="16d68-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="16d68-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="16d68-108">Level</span><span class="sxs-lookup"><span data-stu-id="16d68-108">Level</span></span>|<span data-ttu-id="16d68-109">エラー</span><span class="sxs-lookup"><span data-stu-id="16d68-109">Error</span></span>|  
|<span data-ttu-id="16d68-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="16d68-110">Channel</span></span>|<span data-ttu-id="16d68-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="16d68-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16d68-112">Description</span><span class="sxs-lookup"><span data-stu-id="16d68-112">Description</span></span>  

 <span data-ttu-id="16d68-113">SQL 接続を開こうとしてタイムアウトが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="16d68-113">Indicates a timeout was encountered when trying to open a SQL connection.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16d68-114">Message</span><span class="sxs-lookup"><span data-stu-id="16d68-114">Message</span></span>  

 <span data-ttu-id="16d68-115">SQL 接続を開こうとしてタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="16d68-115">Timeout trying to open a SQL connection.</span></span> <span data-ttu-id="16d68-116">割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="16d68-116">The operation did not complete within the allotted timeout of %1.</span></span> <span data-ttu-id="16d68-117">この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="16d68-117">The time allotted to this operation may have been a portion of a longer timeout.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16d68-118">詳細</span><span class="sxs-lookup"><span data-stu-id="16d68-118">Details</span></span>  
  
|<span data-ttu-id="16d68-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="16d68-119">Data Item Name</span></span>|<span data-ttu-id="16d68-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="16d68-120">Data Item Type</span></span>|<span data-ttu-id="16d68-121">Description</span><span class="sxs-lookup"><span data-stu-id="16d68-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16d68-122">タイムアウト</span><span class="sxs-lookup"><span data-stu-id="16d68-122">Timeout</span></span>|<span data-ttu-id="16d68-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="16d68-123">xs:string</span></span>|<span data-ttu-id="16d68-124">SQL 接続を開く場合のタイムアウト値。</span><span class="sxs-lookup"><span data-stu-id="16d68-124">The timeout value for opening the SQL connection.</span></span>|  
|<span data-ttu-id="16d68-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="16d68-125">AppDomain</span></span>|<span data-ttu-id="16d68-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="16d68-126">xs:string</span></span>|<span data-ttu-id="16d68-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="16d68-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
