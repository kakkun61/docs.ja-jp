---
title: 440 - StartSignpostEvent1
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 1e0278d665a961afab21445ab8490e3e5a94987c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293456"
---
# <a name="440---startsignpostevent1"></a><span data-ttu-id="03aa8-102">440 - StartSignpostEvent1</span><span class="sxs-lookup"><span data-stu-id="03aa8-102">440 - StartSignpostEvent1</span></span>

## <a name="properties"></a><span data-ttu-id="03aa8-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="03aa8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="03aa8-104">ID</span><span class="sxs-lookup"><span data-stu-id="03aa8-104">ID</span></span>|<span data-ttu-id="03aa8-105">440</span><span class="sxs-lookup"><span data-stu-id="03aa8-105">440</span></span>|  
|<span data-ttu-id="03aa8-106">Keywords</span><span class="sxs-lookup"><span data-stu-id="03aa8-106">Keywords</span></span>|<span data-ttu-id="03aa8-107">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="03aa8-107">Troubleshooting</span></span>|  
|<span data-ttu-id="03aa8-108">Level</span><span class="sxs-lookup"><span data-stu-id="03aa8-108">Level</span></span>|<span data-ttu-id="03aa8-109">情報</span><span class="sxs-lookup"><span data-stu-id="03aa8-109">Information</span></span>|  
|<span data-ttu-id="03aa8-110">チャネル</span><span class="sxs-lookup"><span data-stu-id="03aa8-110">Channel</span></span>|<span data-ttu-id="03aa8-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="03aa8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="03aa8-112">Description</span><span class="sxs-lookup"><span data-stu-id="03aa8-112">Description</span></span>  

 <span data-ttu-id="03aa8-113">アクティビティ トレースでは、送信または受信においてメッセージがアクティビティの境界を越え始めたことを示します。</span><span class="sxs-lookup"><span data-stu-id="03aa8-113">In activity tracing, indicates a message has started crossing an activity boundary in send or receive.</span></span>  
  
## <a name="message"></a><span data-ttu-id="03aa8-114">Message</span><span class="sxs-lookup"><span data-stu-id="03aa8-114">Message</span></span>  

 <span data-ttu-id="03aa8-115">アクティビティの境界</span><span class="sxs-lookup"><span data-stu-id="03aa8-115">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="03aa8-116">詳細</span><span class="sxs-lookup"><span data-stu-id="03aa8-116">Details</span></span>  
  
|<span data-ttu-id="03aa8-117">データ項目名</span><span class="sxs-lookup"><span data-stu-id="03aa8-117">Data Item Name</span></span>|<span data-ttu-id="03aa8-118">データ項目の型</span><span class="sxs-lookup"><span data-stu-id="03aa8-118">Data Item Type</span></span>|<span data-ttu-id="03aa8-119">Description</span><span class="sxs-lookup"><span data-stu-id="03aa8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="03aa8-120">ExtendedData</span><span class="sxs-lookup"><span data-stu-id="03aa8-120">ExtendedData</span></span>|`xs:string`|<span data-ttu-id="03aa8-121">アクティビティの名前。</span><span class="sxs-lookup"><span data-stu-id="03aa8-121">The name of the activity.</span></span>|  
|<span data-ttu-id="03aa8-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="03aa8-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="03aa8-123">AppDomain.CurrentDomain.FriendlyName で返される文字列。</span><span class="sxs-lookup"><span data-stu-id="03aa8-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
