---
title: 4202 - StartSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: 4559f64f-c824-4075-9e7e-4710bf30f805
ms.openlocfilehash: d3f27c6ed28efe9d099dcedfc676b839ae9b1dee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275841"
---
# <a name="4202---startsqlcommandexecute"></a><span data-ttu-id="04cf5-102">4202 - StartSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="04cf5-102">4202 - StartSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="04cf5-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="04cf5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="04cf5-104">ID</span><span class="sxs-lookup"><span data-stu-id="04cf5-104">ID</span></span>|<span data-ttu-id="04cf5-105">4202</span><span class="sxs-lookup"><span data-stu-id="04cf5-105">4202</span></span>|  
|<span data-ttu-id="04cf5-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="04cf5-106">Keywords</span></span>|<span data-ttu-id="04cf5-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="04cf5-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="04cf5-108">Level</span><span class="sxs-lookup"><span data-stu-id="04cf5-108">Level</span></span>|<span data-ttu-id="04cf5-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="04cf5-109">Verbose</span></span>|  
|<span data-ttu-id="04cf5-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="04cf5-110">Channel</span></span>|<span data-ttu-id="04cf5-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="04cf5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="04cf5-112">Description</span><span class="sxs-lookup"><span data-stu-id="04cf5-112">Description</span></span>  

 <span data-ttu-id="04cf5-113">SQL コマンドが実行されることを示します。</span><span class="sxs-lookup"><span data-stu-id="04cf5-113">Indicates a SQL command is being executed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="04cf5-114">Message</span><span class="sxs-lookup"><span data-stu-id="04cf5-114">Message</span></span>  

 <span data-ttu-id="04cf5-115">SQL コマンドの実行を開始します: %1</span><span class="sxs-lookup"><span data-stu-id="04cf5-115">Starting SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="04cf5-116">詳細</span><span class="sxs-lookup"><span data-stu-id="04cf5-116">Details</span></span>  
  
|<span data-ttu-id="04cf5-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="04cf5-117">Data Item Name</span></span>|<span data-ttu-id="04cf5-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="04cf5-118">Data Item Type</span></span>|<span data-ttu-id="04cf5-119">Description</span><span class="sxs-lookup"><span data-stu-id="04cf5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="04cf5-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="04cf5-120">SqlCommand</span></span>|<span data-ttu-id="04cf5-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="04cf5-121">xs:string</span></span>|<span data-ttu-id="04cf5-122">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="04cf5-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="04cf5-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="04cf5-123">AppDomain</span></span>|<span data-ttu-id="04cf5-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="04cf5-124">xs:string</span></span>|<span data-ttu-id="04cf5-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="04cf5-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
