---
title: '方法: PLINQ のマージ オプションを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: 91c5ac91538942368b66399bf0bc0132a15bf667
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825599"
---
# <a name="how-to-specify-merge-options-in-plinq"></a><span data-ttu-id="28060-102">方法: PLINQ のマージ オプションを指定する</span><span class="sxs-lookup"><span data-stu-id="28060-102">How to: Specify Merge Options in PLINQ</span></span>
<span data-ttu-id="28060-103">この例では、PLINQ クエリの後続のすべての演算子に適用されるマージ オプションを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="28060-103">This example shows how to specify the merge options that will apply to all subsequent operators in a PLINQ query.</span></span> <span data-ttu-id="28060-104">マージ オプションを明示的に設定する必要はありませんが、設定することでパフォーマンスが向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28060-104">You do not have to set merge options explicitly, but doing so may improve performance.</span></span> <span data-ttu-id="28060-105">マージ オプションの詳細については、「[PLINQ のマージ オプション](merge-options-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28060-105">For more information about merge options, see [Merge Options in PLINQ](merge-options-in-plinq.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="28060-106">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28060-106">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="28060-107">高速化の詳細については、「[PLINQ での高速化について](understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28060-107">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28060-108">例</span><span class="sxs-lookup"><span data-stu-id="28060-108">Example</span></span>  
 <span data-ttu-id="28060-109">次の例では、順序付けされていないソースがあり、すべての要素に負荷が大きい関数を適用する基本的なシナリオでのマージ オプションの動作を示します。</span><span class="sxs-lookup"><span data-stu-id="28060-109">The following example demonstrates the behavior of merge options in a basic scenario that has an unordered source and applies an expensive function to every element.</span></span>  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 <span data-ttu-id="28060-110">最初の要素が生成される前に <xref:System.Linq.ParallelMergeOptions.AutoBuffered> オプションで望ましくない待機時間が発生した場合は、結果要素をより速く、よりスムーズに生成するために <xref:System.Linq.ParallelMergeOptions.NotBuffered> オプションを試してください。</span><span class="sxs-lookup"><span data-stu-id="28060-110">In cases where the <xref:System.Linq.ParallelMergeOptions.AutoBuffered> option incurs an undesirable latency before the first element is yielded, try the <xref:System.Linq.ParallelMergeOptions.NotBuffered> option to yield result elements faster and more smoothly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28060-111">参照</span><span class="sxs-lookup"><span data-stu-id="28060-111">See also</span></span>

- <xref:System.Linq.ParallelMergeOptions>
- [<span data-ttu-id="28060-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="28060-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
