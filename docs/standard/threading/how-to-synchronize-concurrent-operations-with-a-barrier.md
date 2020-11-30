---
title: '方法: バリアを使用して同時実行操作を同期する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
ms.openlocfilehash: dc0955ba6194dd936da19c634ada797d6cbd3720
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716474"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a><span data-ttu-id="f7e64-102">方法: バリアを使用して同時実行操作を同期する</span><span class="sxs-lookup"><span data-stu-id="f7e64-102">How to: Synchronize Concurrent Operations with a Barrier</span></span>

<span data-ttu-id="f7e64-103">次の例は、<xref:System.Threading.Barrier> を使用して同時実行タスクを同期する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f7e64-103">The following example shows how to synchronize concurrent tasks with a <xref:System.Threading.Barrier>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7e64-104">例</span><span class="sxs-lookup"><span data-stu-id="f7e64-104">Example</span></span>  

 <span data-ttu-id="f7e64-105">次のプログラムの目的は、単語を再シャッフルするためにランダム化アルゴリズムを使用して、同じフェーズで 2 つのスレッドのそれぞれのソリューションの半分を検索するのに必要な反復 (またはフェーズ) の数をカウントすることです。</span><span class="sxs-lookup"><span data-stu-id="f7e64-105">The purpose of the following program is to count how many iterations (or phases) are required for two threads to each find their half of the solution on the same phase by using a randomizing algorithm to reshuffle the words.</span></span> <span data-ttu-id="f7e64-106">各スレッドで単語をシャッフルした後、バリアのフェーズ後操作で 2 つの結果が比較され、完全な文が正しい語順でレンダリングされているかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="f7e64-106">After each thread has shuffled its words, the barrier post-phase operation compares the two results to see if the complete sentence has been rendered in correct word order.</span></span>  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 <span data-ttu-id="f7e64-107"><xref:System.Threading.Barrier> はオブジェクトであり、すべてのタスクがバリアに到達するまで、並列操作の個々のタスクが続行されないようにします。</span><span class="sxs-lookup"><span data-stu-id="f7e64-107">A <xref:System.Threading.Barrier> is an object that prevents individual tasks in a parallel operation from continuing until all tasks reach the barrier.</span></span> <span data-ttu-id="f7e64-108">これは、並列操作を段階的に行う場合、および各フェーズでタスク間の同期が必要な場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f7e64-108">It is useful when a parallel operation occurs in phases, and each phase requires synchronization between tasks.</span></span> <span data-ttu-id="f7e64-109">この例では、2 つの操作フェーズがあります。</span><span class="sxs-lookup"><span data-stu-id="f7e64-109">In this example, there are two phases to the operation.</span></span> <span data-ttu-id="f7e64-110">最初のフェーズでは、各タスクでバッファーのセクションにデータが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f7e64-110">In the first phase, each task fills its section of the buffer with data.</span></span> <span data-ttu-id="f7e64-111">各タスクでそのセクションへの読み込みが終了すると、タスクは続行する準備ができていることをバリアに通知してから、待機します。</span><span class="sxs-lookup"><span data-stu-id="f7e64-111">When each task finishes filling its section, the task signals the barrier that it is ready to continue, and then waits.</span></span> <span data-ttu-id="f7e64-112">すべてのタスクがバリアに通知した時点で、ブロックが解除され、2 番目のフェーズが開始されます。</span><span class="sxs-lookup"><span data-stu-id="f7e64-112">When all tasks have signaled the barrier, they are unblocked and the second phase starts.</span></span> <span data-ttu-id="f7e64-113">2 番目のフェーズでは、各タスクがこれまでに生成されたすべてのデータにアクセスできる必要があるため、バリアが必要です。</span><span class="sxs-lookup"><span data-stu-id="f7e64-113">The barrier is necessary because the second phase requires that each task have access to all the data that has been generated to this point.</span></span> <span data-ttu-id="f7e64-114">バリアがないと、実行する最初のタスクで、他のタスクによってまだデータが読み込まれていないバッファーからの読み取りが試行される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7e64-114">Without the barrier, the first tasks to complete might try to read from buffers that have not been filled in yet by other tasks.</span></span> <span data-ttu-id="f7e64-115">このように任意の数のフェーズを同期することができます。</span><span class="sxs-lookup"><span data-stu-id="f7e64-115">You can synchronize any number of phases in this manner.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7e64-116">参照</span><span class="sxs-lookup"><span data-stu-id="f7e64-116">See also</span></span>

- [<span data-ttu-id="f7e64-117">並列プログラミングのデータ構造</span><span class="sxs-lookup"><span data-stu-id="f7e64-117">Data Structures for Parallel Programming</span></span>](../parallel-programming/data-structures-for-parallel-programming.md)
