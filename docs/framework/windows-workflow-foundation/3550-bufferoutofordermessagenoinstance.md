---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 61605d666911cce277bcebbb0a2f803e9a5dcfeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261307"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="8c3c2-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="8c3c2-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>

## <a name="properties"></a><span data-ttu-id="8c3c2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8c3c2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c3c2-104">ID</span><span class="sxs-lookup"><span data-stu-id="8c3c2-104">ID</span></span>|<span data-ttu-id="8c3c2-105">3550</span><span class="sxs-lookup"><span data-stu-id="8c3c2-105">3550</span></span>|  
|<span data-ttu-id="8c3c2-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="8c3c2-106">Keywords</span></span>|<span data-ttu-id="8c3c2-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8c3c2-107">WFServices</span></span>|  
|<span data-ttu-id="8c3c2-108">Level</span><span class="sxs-lookup"><span data-stu-id="8c3c2-108">Level</span></span>|<span data-ttu-id="8c3c2-109">情報</span><span class="sxs-lookup"><span data-stu-id="8c3c2-109">Information</span></span>|  
|<span data-ttu-id="8c3c2-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="8c3c2-110">Channel</span></span>|<span data-ttu-id="8c3c2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8c3c2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c3c2-112">Description</span><span class="sxs-lookup"><span data-stu-id="8c3c2-112">Description</span></span>  

 <span data-ttu-id="8c3c2-113">バッファーされた受信機能が失敗したことを示します。</span><span class="sxs-lookup"><span data-stu-id="8c3c2-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="8c3c2-114">サービス インスタンスがこの特定の操作を処理する準備が整った場合、操作が再試行されます。</span><span class="sxs-lookup"><span data-stu-id="8c3c2-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c3c2-115">Message</span><span class="sxs-lookup"><span data-stu-id="8c3c2-115">Message</span></span>  

 <span data-ttu-id="8c3c2-116">操作 '%1' は現時点では実行できません。</span><span class="sxs-lookup"><span data-stu-id="8c3c2-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="8c3c2-117">サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。</span><span class="sxs-lookup"><span data-stu-id="8c3c2-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c3c2-118">詳細</span><span class="sxs-lookup"><span data-stu-id="8c3c2-118">Details</span></span>  
  
|<span data-ttu-id="8c3c2-119">データ項目名</span><span class="sxs-lookup"><span data-stu-id="8c3c2-119">Data Item Name</span></span>|<span data-ttu-id="8c3c2-120">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="8c3c2-120">Data Item Type</span></span>|<span data-ttu-id="8c3c2-121">Description</span><span class="sxs-lookup"><span data-stu-id="8c3c2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c3c2-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="8c3c2-122">OperationName</span></span>|<span data-ttu-id="8c3c2-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c3c2-123">xs:string</span></span>|<span data-ttu-id="8c3c2-124">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="8c3c2-124">The name of the operation.</span></span>|  
|<span data-ttu-id="8c3c2-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c3c2-125">AppDomain</span></span>|<span data-ttu-id="8c3c2-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c3c2-126">xs:string</span></span>|<span data-ttu-id="8c3c2-127">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="8c3c2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
