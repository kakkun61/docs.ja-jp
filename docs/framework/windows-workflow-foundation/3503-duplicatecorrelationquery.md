---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: e1e64824ee9a95757ed7c00aa17fa80898219401
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270329"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="608a8-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="608a8-102">3503 - DuplicateCorrelationQuery</span></span>

## <a name="properties"></a><span data-ttu-id="608a8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="608a8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="608a8-104">ID</span><span class="sxs-lookup"><span data-stu-id="608a8-104">ID</span></span>|<span data-ttu-id="608a8-105">3503</span><span class="sxs-lookup"><span data-stu-id="608a8-105">3503</span></span>|  
|<span data-ttu-id="608a8-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="608a8-106">Keywords</span></span>|<span data-ttu-id="608a8-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="608a8-107">WFServices</span></span>|  
|<span data-ttu-id="608a8-108">Level</span><span class="sxs-lookup"><span data-stu-id="608a8-108">Level</span></span>|<span data-ttu-id="608a8-109">警告</span><span class="sxs-lookup"><span data-stu-id="608a8-109">Warning</span></span>|  
|<span data-ttu-id="608a8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="608a8-110">Channel</span></span>|<span data-ttu-id="608a8-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="608a8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="608a8-112">Description</span><span class="sxs-lookup"><span data-stu-id="608a8-112">Description</span></span>  

 <span data-ttu-id="608a8-113">重複する CorrelationQuery が見つかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="608a8-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="608a8-114">相関の計算時には、重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="608a8-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="608a8-115">Message</span><span class="sxs-lookup"><span data-stu-id="608a8-115">Message</span></span>  

 <span data-ttu-id="608a8-116">Where='%1' で重複する CorrelationQuery が見つかりました。</span><span class="sxs-lookup"><span data-stu-id="608a8-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="608a8-117">相関の計算時には、この重複するクエリは使用されません。</span><span class="sxs-lookup"><span data-stu-id="608a8-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="608a8-118">詳細</span><span class="sxs-lookup"><span data-stu-id="608a8-118">Details</span></span>  
  
|<span data-ttu-id="608a8-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="608a8-119">Data Item Name</span></span>|<span data-ttu-id="608a8-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="608a8-120">Data Item Type</span></span>|<span data-ttu-id="608a8-121">Description</span><span class="sxs-lookup"><span data-stu-id="608a8-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="608a8-122">Where</span><span class="sxs-lookup"><span data-stu-id="608a8-122">Where</span></span>|<span data-ttu-id="608a8-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="608a8-123">xs:string</span></span>|<span data-ttu-id="608a8-124">関連付けクエリの Where 部分。</span><span class="sxs-lookup"><span data-stu-id="608a8-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="608a8-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="608a8-125">AppDomain</span></span>|<span data-ttu-id="608a8-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="608a8-126">xs:string</span></span>|<span data-ttu-id="608a8-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="608a8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
