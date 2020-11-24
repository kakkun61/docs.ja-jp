---
title: '方法: Parallel.For または ForEach ループを取り消す'
description: ParallelOptions パラメーターのメソッドにキャンセル トークン オブジェクトを指定することによって、.NET で Parallel.For ループまたは Parallel.ForEach ループをキャンセルします。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: d5deeeab6c332d29f3fa667d6211e8fb4b0eae50
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817316"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="92585-103">方法: Parallel.For または ForEach ループを取り消す</span><span class="sxs-lookup"><span data-stu-id="92585-103">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="92585-104"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> および <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> メソッドでは、キャンセル トークンを使用した取り消し処理がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="92585-104">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="92585-105">一般的な取り消し処理の詳細については、「[キャンセル](../threading/cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92585-105">For more information about cancellation in general, see [Cancellation](../threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="92585-106">並列ループでは、<xref:System.Threading.Tasks.ParallelOptions> パラメーターのメソッドに <xref:System.Threading.CancellationToken> を指定してから、try-catch ブロックで並列呼び出しを囲みます。</span><span class="sxs-lookup"><span data-stu-id="92585-106">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92585-107">例</span><span class="sxs-lookup"><span data-stu-id="92585-107">Example</span></span>  
 <span data-ttu-id="92585-108">次の例は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> の呼び出しを取り消す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="92585-108">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="92585-109"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 呼び出しに同じ方法を適用できます。</span><span class="sxs-lookup"><span data-stu-id="92585-109">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="92585-110">取り消しを通知するトークンが <xref:System.Threading.Tasks.ParallelOptions> インスタンスで指定されているのと同じトークンである場合、並列ループは取り消し時に単一の <xref:System.OperationCanceledException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="92585-110">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="92585-111">その他のいくつかのトークンによって取り消しが行われた場合、ループは InnerException として <xref:System.OperationCanceledException> と共に <xref:System.AggregateException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="92585-111">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92585-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="92585-112">See also</span></span>

- [<span data-ttu-id="92585-113">データの並列化</span><span class="sxs-lookup"><span data-stu-id="92585-113">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="92585-114">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="92585-114">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
