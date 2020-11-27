---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: 088754cb15c2e55faa1d43a1da1c79ddcddd69f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280417"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="4f341-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="4f341-102">4208 - RetryingSqlCommandDueToSqlError</span></span>

## <a name="properties"></a><span data-ttu-id="4f341-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4f341-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4f341-104">ID</span><span class="sxs-lookup"><span data-stu-id="4f341-104">ID</span></span>|<span data-ttu-id="4f341-105">4208</span><span class="sxs-lookup"><span data-stu-id="4f341-105">4208</span></span>|  
|<span data-ttu-id="4f341-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="4f341-106">Keywords</span></span>|<span data-ttu-id="4f341-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="4f341-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="4f341-108">Level</span><span class="sxs-lookup"><span data-stu-id="4f341-108">Level</span></span>|<span data-ttu-id="4f341-109">情報</span><span class="sxs-lookup"><span data-stu-id="4f341-109">Information</span></span>|  
|<span data-ttu-id="4f341-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="4f341-110">Channel</span></span>|<span data-ttu-id="4f341-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="4f341-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4f341-112">Description</span><span class="sxs-lookup"><span data-stu-id="4f341-112">Description</span></span>  

 <span data-ttu-id="4f341-113">SQL プロバイダーは SQL エラーのために SQL コマンドを再試行していることを示します。</span><span class="sxs-lookup"><span data-stu-id="4f341-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4f341-114">Message</span><span class="sxs-lookup"><span data-stu-id="4f341-114">Message</span></span>  

 <span data-ttu-id="4f341-115">SQL エラー番号 %1 のため、SQL コマンドを再試行します。</span><span class="sxs-lookup"><span data-stu-id="4f341-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4f341-116">詳細</span><span class="sxs-lookup"><span data-stu-id="4f341-116">Details</span></span>  
  
|<span data-ttu-id="4f341-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="4f341-117">Data Item Name</span></span>|<span data-ttu-id="4f341-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="4f341-118">Data Item Type</span></span>|<span data-ttu-id="4f341-119">Description</span><span class="sxs-lookup"><span data-stu-id="4f341-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4f341-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="4f341-120">ErrorNumber</span></span>|<span data-ttu-id="4f341-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f341-121">xs:string</span></span>|<span data-ttu-id="4f341-122">SQL エラー番号。</span><span class="sxs-lookup"><span data-stu-id="4f341-122">The SQL error number.</span></span>|  
|<span data-ttu-id="4f341-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4f341-123">AppDomain</span></span>|<span data-ttu-id="4f341-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="4f341-124">xs:string</span></span>|<span data-ttu-id="4f341-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="4f341-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
