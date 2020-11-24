---
title: バリア
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
ms.openlocfilehash: 4eab74ef07ac56a4d3ff65e67bb9fbd45dbfc9bc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819943"
---
# <a name="barrier"></a><span data-ttu-id="ae4e3-102">バリア</span><span class="sxs-lookup"><span data-stu-id="ae4e3-102">Barrier</span></span>

<span data-ttu-id="ae4e3-103"><xref:System.Threading.Barrier?displayProperty=nameWithType> は、複数のスレッド (*参加要素* と呼ばれる) が段階的に 1 つのアルゴリズムで同時に動作できるようにするユーザー定義の同期プリミティブです。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-103">A <xref:System.Threading.Barrier?displayProperty=nameWithType> is a synchronization primitive that enables multiple threads (known as *participants*) to work concurrently on an algorithm in phases.</span></span> <span data-ttu-id="ae4e3-104">各参加要素は、コードのバリア ポイントに到達するまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-104">Each participant executes until it reaches the barrier point in the code.</span></span> <span data-ttu-id="ae4e3-105">バリアは、作業の 1 つのフェーズの終了を表します。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-105">The barrier represents the end of one phase of work.</span></span> <span data-ttu-id="ae4e3-106">参加要素は、バリアに到達すると、すべての参加要素が同じバリアに到達するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-106">When a participant reaches the barrier, it blocks until all participants have reached the same barrier.</span></span> <span data-ttu-id="ae4e3-107">すべての参加要素がバリアに到達した後、必要に応じて、フェーズ後の処理を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-107">After all participants have reached the barrier, you can optionally invoke a post-phase action.</span></span> <span data-ttu-id="ae4e3-108">フェーズ後の処理を使用すると、他のすべてのスレッドがブロックされた状態のまま 1 つのスレッドでアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-108">This post-phase action can be used to perform actions by a single thread while all other threads are still blocked.</span></span> <span data-ttu-id="ae4e3-109">アクションが実行された後、参加要素のブロックはすべて解除されます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-109">After the action has been executed, the participants are all unblocked.</span></span>  
  
 <span data-ttu-id="ae4e3-110">基本的なバリア パターンを次のコード スニペットに示します。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-110">The following code snippet shows a basic barrier pattern.</span></span>  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 <span data-ttu-id="ae4e3-111">コード例全体については、「[方法: バリアを使用して同時実行操作を同期する](how-to-synchronize-concurrent-operations-with-a-barrier.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-111">For a complete example, see [How to: synchronize concurrent operations with a Barrier](how-to-synchronize-concurrent-operations-with-a-barrier.md).</span></span>  
  
## <a name="adding-and-removing-participants"></a><span data-ttu-id="ae4e3-112">参加要素の追加と削除</span><span class="sxs-lookup"><span data-stu-id="ae4e3-112">Adding and removing participants</span></span>

 <span data-ttu-id="ae4e3-113"><xref:System.Threading.Barrier> インスタンスを作成するときは、参加要素の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-113">When you create a <xref:System.Threading.Barrier> instance, specify the number of participants.</span></span> <span data-ttu-id="ae4e3-114">また、参加要素は、いつでも動的に追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-114">You can also add or remove participants dynamically at any time.</span></span> <span data-ttu-id="ae4e3-115">たとえば、1 つの参加要素がその処理を終えた場合に、結果を保存し、そのスレッドの実行を停止してから、<xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> を呼び出してバリアの参加要素の数を 1 つ減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-115">For example, if one participant solves its part of the problem, you can store the result, stop execution on that thread, and call <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> to decrement the number of participants in the barrier.</span></span> <span data-ttu-id="ae4e3-116"><xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType> を呼び出して参加要素を追加すると、戻り値によって現在のフェーズ数が示されます。この値は、追加した新しい参加要素の作業を初期化するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-116">When you add a participant by calling <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, the return value specifies the current phase number, which may be useful in order to initialize the work of the new participant.</span></span>  
  
## <a name="broken-barriers"></a><span data-ttu-id="ae4e3-117">破損したバリア</span><span class="sxs-lookup"><span data-stu-id="ae4e3-117">Broken barriers</span></span>

 <span data-ttu-id="ae4e3-118">いずれかの参加要素がバリアに到達できない場合、デッドロックが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-118">Deadlocks can occur if one participant fails to reach the barrier.</span></span> <span data-ttu-id="ae4e3-119">このようなデッドロックを避けるには、<xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> メソッドのオーバーロードを使用して、タイムアウト期間とキャンセル トークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-119">To avoid these deadlocks, use the overloads of the <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> method to specify a time-out period and a cancellation token.</span></span> <span data-ttu-id="ae4e3-120">すべての参加要素は、次のフェーズに進む前に、これらのオーバーロードから返されるブール値をチェックできます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-120">These overloads return a Boolean value that every participant can check before it continues to the next phase.</span></span>  
  
## <a name="post-phase-exceptions"></a><span data-ttu-id="ae4e3-121">フェーズ後の例外</span><span class="sxs-lookup"><span data-stu-id="ae4e3-121">Post-phase exceptions</span></span>

 <span data-ttu-id="ae4e3-122">フェーズ後のデリゲートから例外がスローされる場合、その例外は <xref:System.Threading.BarrierPostPhaseException> オブジェクトでラップされ、このオブジェクトがすべての参加要素に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-122">If the post-phase delegate throws an exception, it is wrapped in a <xref:System.Threading.BarrierPostPhaseException> object which is then propagated to all participants.</span></span>  
  
## <a name="barrier-versus-continuewhenall"></a><span data-ttu-id="ae4e3-123">バリアと ContinueWhenAll</span><span class="sxs-lookup"><span data-stu-id="ae4e3-123">Barrier versus ContinueWhenAll</span></span>

 <span data-ttu-id="ae4e3-124">バリアは、スレッドで複数のフェーズをループ処理する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-124">Barriers are especially useful when the threads are performing multiple phases in loops.</span></span> <span data-ttu-id="ae4e3-125">コードで作業のフェーズが 1 つか 2 つしか必要ない場合は、次のような何らかの暗黙的な結合と共に <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> オブジェクトを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-125">If your code requires only one or two phases of work, consider whether to use <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects with any kind of implicit join, including:</span></span>  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="ae4e3-126">詳細については、「[継続タスクを使用したタスクの連結](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae4e3-126">For more information, see [Chaining Tasks by Using Continuation Tasks](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae4e3-127">参照</span><span class="sxs-lookup"><span data-stu-id="ae4e3-127">See also</span></span>

- [<span data-ttu-id="ae4e3-128">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="ae4e3-128">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="ae4e3-129">方法: バリアを使用して同時実行操作を同期する</span><span class="sxs-lookup"><span data-stu-id="ae4e3-129">How to: synchronize concurrent operations with a Barrier</span></span>](how-to-synchronize-concurrent-operations-with-a-barrier.md)
