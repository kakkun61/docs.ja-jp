---
title: '方法: 単純な PLINQ クエリを作成して実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 67863346046b0c400529b87355c11f97d0c3f01f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827088"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a><span data-ttu-id="7ce56-102">方法: 単純な PLINQ クエリを作成して実行する</span><span class="sxs-lookup"><span data-stu-id="7ce56-102">How to: Create and Execute a Simple PLINQ Query</span></span>

<span data-ttu-id="7ce56-103">この記事の例では、ソース シーケンスに対する <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> 拡張メソッドを使用して単純な並列統合言語クエリ (LINQ) クエリを作成し、<xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> メソッドを使用して、そのクエリを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ce56-103">The example in this article shows how to create a simple Parallel Language Integrated Query (LINQ) query by using the <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> extension method on the source sequence and executing the query by using the <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ce56-104">ここでは、ラムダ式を使用して PLINQ でデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="7ce56-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="7ce56-105">C# または Visual Basic のラムダ式についての情報が必要な場合は、「[Lambda Expressions in PLINQ and TPL (PLINQ および TPL のラムダ式)](lambda-expressions-in-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce56-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ce56-106">例</span><span class="sxs-lookup"><span data-stu-id="7ce56-106">Example</span></span>  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 <span data-ttu-id="7ce56-107">この例では、結果シーケンスの順序付けが重要ではない場合に、並列 LINQ クエリを作成して実行する基本的なパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="7ce56-107">This example demonstrates the basic pattern for creating and executing any Parallel LINQ query when the ordering of the result sequence is not important.</span></span> <span data-ttu-id="7ce56-108">通常、順序なしのクエリは、順序ありのクエリより高速です。</span><span class="sxs-lookup"><span data-stu-id="7ce56-108">Unordered queries are generally faster than ordered queries.</span></span> <span data-ttu-id="7ce56-109">このクエリはソースを、複数のスレッドで非同期的に実行した複数のタスクにパーティション分割します。</span><span class="sxs-lookup"><span data-stu-id="7ce56-109">The query partitions the source into tasks that are executed asynchronously on multiple threads.</span></span> <span data-ttu-id="7ce56-110">各タスクが完了する順序は、その特定のパーティションに含まれる要素を処理するために必要な作業量だけでなく、オペレーティング システムが各スレッドをどのようにスケジュールするかといった外部要因にも依存します。</span><span class="sxs-lookup"><span data-stu-id="7ce56-110">The order in which each task completes depends not only on the amount of work involved to process the elements in the partition, but also on external factors such as how the operating system schedules each thread.</span></span> <span data-ttu-id="7ce56-111">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7ce56-111">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="7ce56-112">高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce56-112">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span> <span data-ttu-id="7ce56-113">クエリに含まれる要素の順序を保持する方法の詳細については、「[方法: PLINQ クエリの順序を制御する](how-to-control-ordering-in-a-plinq-query.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce56-113">For more information about how to preserve the ordering of elements in a query, see [How to: Control Ordering in a PLINQ Query](how-to-control-ordering-in-a-plinq-query.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce56-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ce56-114">See also</span></span>

- [<span data-ttu-id="7ce56-115">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7ce56-115">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
