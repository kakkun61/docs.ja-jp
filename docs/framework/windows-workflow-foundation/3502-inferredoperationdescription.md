---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 05278067e3f86612ee4aafbe7d5eb66dc934cb85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242111"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="1c869-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="1c869-102">3502 - InferredOperationDescription</span></span>

## <a name="properties"></a><span data-ttu-id="1c869-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="1c869-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1c869-104">ID</span><span class="sxs-lookup"><span data-stu-id="1c869-104">ID</span></span>|<span data-ttu-id="1c869-105">3502</span><span class="sxs-lookup"><span data-stu-id="1c869-105">3502</span></span>|  
|<span data-ttu-id="1c869-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="1c869-106">Keywords</span></span>|<span data-ttu-id="1c869-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1c869-107">WFServices</span></span>|  
|<span data-ttu-id="1c869-108">Level</span><span class="sxs-lookup"><span data-stu-id="1c869-108">Level</span></span>|<span data-ttu-id="1c869-109">情報</span><span class="sxs-lookup"><span data-stu-id="1c869-109">Information</span></span>|  
|<span data-ttu-id="1c869-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="1c869-110">Channel</span></span>|<span data-ttu-id="1c869-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1c869-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1c869-112">Description</span><span class="sxs-lookup"><span data-stu-id="1c869-112">Description</span></span>  

 <span data-ttu-id="1c869-113">OperationDescription が WorkflowService から推論されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="1c869-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1c869-114">Message</span><span class="sxs-lookup"><span data-stu-id="1c869-114">Message</span></span>  

 <span data-ttu-id="1c869-115">コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。</span><span class="sxs-lookup"><span data-stu-id="1c869-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="1c869-116">IsOneWay=%3。</span><span class="sxs-lookup"><span data-stu-id="1c869-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1c869-117">詳細</span><span class="sxs-lookup"><span data-stu-id="1c869-117">Details</span></span>  
  
|<span data-ttu-id="1c869-118">データ項目名</span><span class="sxs-lookup"><span data-stu-id="1c869-118">Data Item Name</span></span>|<span data-ttu-id="1c869-119">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="1c869-119">Data Item Type</span></span>|<span data-ttu-id="1c869-120">Description</span><span class="sxs-lookup"><span data-stu-id="1c869-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1c869-121">OperationName</span><span class="sxs-lookup"><span data-stu-id="1c869-121">OperationName</span></span>|<span data-ttu-id="1c869-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c869-122">xs:string</span></span>|<span data-ttu-id="1c869-123">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="1c869-123">The name of the operation.</span></span>|  
|<span data-ttu-id="1c869-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="1c869-124">ContractName</span></span>|<span data-ttu-id="1c869-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c869-125">xs:string</span></span>|<span data-ttu-id="1c869-126">コントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="1c869-126">The name of the contract.</span></span>|  
|<span data-ttu-id="1c869-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="1c869-127">IsOneWay</span></span>|<span data-ttu-id="1c869-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c869-128">xs:string</span></span>|<span data-ttu-id="1c869-129">True または False はコントラクトが一方向かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="1c869-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="1c869-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1c869-130">AppDomain</span></span>|<span data-ttu-id="1c869-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1c869-131">xs:string</span></span>|<span data-ttu-id="1c869-132">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="1c869-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
