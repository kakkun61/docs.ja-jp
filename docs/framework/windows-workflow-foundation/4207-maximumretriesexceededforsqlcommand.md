---
title: 4207 - MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: f724379ef2ea23dcca7aa75caab3f10f7635e419
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251205"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="c30ad-102">4207 - MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="c30ad-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>

## <a name="properties"></a><span data-ttu-id="c30ad-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="c30ad-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c30ad-104">ID</span><span class="sxs-lookup"><span data-stu-id="c30ad-104">ID</span></span>|<span data-ttu-id="c30ad-105">4207</span><span class="sxs-lookup"><span data-stu-id="c30ad-105">4207</span></span>|  
|<span data-ttu-id="c30ad-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="c30ad-106">Keywords</span></span>|<span data-ttu-id="c30ad-107">クオータ、WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="c30ad-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="c30ad-108">Level</span><span class="sxs-lookup"><span data-stu-id="c30ad-108">Level</span></span>|<span data-ttu-id="c30ad-109">情報</span><span class="sxs-lookup"><span data-stu-id="c30ad-109">Information</span></span>|  
|<span data-ttu-id="c30ad-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="c30ad-110">Channel</span></span>|<span data-ttu-id="c30ad-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="c30ad-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c30ad-112">Description</span><span class="sxs-lookup"><span data-stu-id="c30ad-112">Description</span></span>  

 <span data-ttu-id="c30ad-113">再試行が最大実行回数実行されたので、SQL プロバイダーは SQL コマンドの再試行を停止しようとしていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c30ad-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c30ad-114">Message</span><span class="sxs-lookup"><span data-stu-id="c30ad-114">Message</span></span>  

 <span data-ttu-id="c30ad-115">SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。</span><span class="sxs-lookup"><span data-stu-id="c30ad-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c30ad-116">詳細</span><span class="sxs-lookup"><span data-stu-id="c30ad-116">Details</span></span>  
  
|<span data-ttu-id="c30ad-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="c30ad-117">Data Item Name</span></span>|<span data-ttu-id="c30ad-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="c30ad-118">Data Item Type</span></span>|<span data-ttu-id="c30ad-119">Description</span><span class="sxs-lookup"><span data-stu-id="c30ad-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c30ad-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c30ad-120">AppDomain</span></span>|<span data-ttu-id="c30ad-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c30ad-121">xs:string</span></span>|<span data-ttu-id="c30ad-122">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="c30ad-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
