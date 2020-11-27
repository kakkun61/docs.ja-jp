---
title: WF 内のエラー処理アクティビティ
ms.date: 03/30/2017
ms.assetid: 24b68bd3-cef5-4413-ab82-2e2625f209aa
ms.openlocfilehash: 332e16b4c399341151761a4bce2d47198779ad64
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280313"
---
# <a name="error-handling-activities-in-wf"></a><span data-ttu-id="a5c41-102">WF 内のエラー処理アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a5c41-102">Error Handling Activities in WF</span></span>

[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a5c41-103">には、エラーの処理および回復を実装するためのシステム標準のアクティビティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a5c41-103">provides several system-provided activities for implementing error handling and recovery.</span></span> <span data-ttu-id="a5c41-104">詳細については、「 [例外](exceptions.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。</span><span class="sxs-lookup"><span data-stu-id="a5c41-104">For more information, see [Exceptions](exceptions.md).</span></span>  
  
## <a name="error-handling-activities"></a><span data-ttu-id="a5c41-105">エラー処理アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a5c41-105">Error handling activities</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.Rethrow>|<span data-ttu-id="a5c41-106">`TryCatch` アクティビティ内からスローされた最後の例外を再スローします。</span><span class="sxs-lookup"><span data-stu-id="a5c41-106">Rethrows the last exception thrown from within a `TryCatch` activity.</span></span>|  
|<xref:System.Activities.Statements.Throw>|<span data-ttu-id="a5c41-107">例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="a5c41-107">Throws an exception.</span></span>|  
|<xref:System.Activities.Statements.TryCatch>|<span data-ttu-id="a5c41-108">例外処理を実装します。</span><span class="sxs-lookup"><span data-stu-id="a5c41-108">Implements exception handling.</span></span>|
