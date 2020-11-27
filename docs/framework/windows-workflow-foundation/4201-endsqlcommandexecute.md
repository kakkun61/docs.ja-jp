---
title: 4201 - EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 0d6326889077e36ad49aa6267ae7285849c6818d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275867"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="ec298-102">4201 - EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="ec298-102">4201 - EndSqlCommandExecute</span></span>

## <a name="properties"></a><span data-ttu-id="ec298-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ec298-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ec298-104">ID</span><span class="sxs-lookup"><span data-stu-id="ec298-104">ID</span></span>|<span data-ttu-id="ec298-105">4201</span><span class="sxs-lookup"><span data-stu-id="ec298-105">4201</span></span>|  
|<span data-ttu-id="ec298-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="ec298-106">Keywords</span></span>|<span data-ttu-id="ec298-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="ec298-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="ec298-108">Level</span><span class="sxs-lookup"><span data-stu-id="ec298-108">Level</span></span>|<span data-ttu-id="ec298-109">"詳細"</span><span class="sxs-lookup"><span data-stu-id="ec298-109">Verbose</span></span>|  
|<span data-ttu-id="ec298-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="ec298-110">Channel</span></span>|<span data-ttu-id="ec298-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="ec298-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ec298-112">Description</span><span class="sxs-lookup"><span data-stu-id="ec298-112">Description</span></span>  

 <span data-ttu-id="ec298-113">SQL コマンドの実行が完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="ec298-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ec298-114">Message</span><span class="sxs-lookup"><span data-stu-id="ec298-114">Message</span></span>  

 <span data-ttu-id="ec298-115">SQL コマンドの実行を終了します: %1</span><span class="sxs-lookup"><span data-stu-id="ec298-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="ec298-116">詳細</span><span class="sxs-lookup"><span data-stu-id="ec298-116">Details</span></span>  
  
|<span data-ttu-id="ec298-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="ec298-117">Data Item Name</span></span>|<span data-ttu-id="ec298-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="ec298-118">Data Item Type</span></span>|<span data-ttu-id="ec298-119">Description</span><span class="sxs-lookup"><span data-stu-id="ec298-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ec298-120">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="ec298-120">SqlCommand</span></span>|<span data-ttu-id="ec298-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec298-121">xs:string</span></span>|<span data-ttu-id="ec298-122">実行された SQL コマンド。</span><span class="sxs-lookup"><span data-stu-id="ec298-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="ec298-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ec298-123">AppDomain</span></span>|<span data-ttu-id="ec298-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="ec298-124">xs:string</span></span>|<span data-ttu-id="ec298-125">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="ec298-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
