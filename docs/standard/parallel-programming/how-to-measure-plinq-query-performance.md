---
title: '方法: PLINQ クエリのパフォーマンスを測定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 2cbd178d5004d28120ab701a777a474a7e78e09e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734440"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="460a5-102">方法: PLINQ クエリのパフォーマンスを測定する</span><span class="sxs-lookup"><span data-stu-id="460a5-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="460a5-103">この例では、<xref:System.Diagnostics.Stopwatch> クラスを使用して、PLINQ クエリの実行にかかる時間を測定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="460a5-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="460a5-104">例</span><span class="sxs-lookup"><span data-stu-id="460a5-104">Example</span></span>  

 <span data-ttu-id="460a5-105">この例では、空の `foreach` ループ (Visual Basic では `For Each`) を使用して、クエリの実行にかかる時間を計測します。</span><span class="sxs-lookup"><span data-stu-id="460a5-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="460a5-106">実際のコードでは、ループには通常、クエリの合計実行時間への加算という追加の処理手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="460a5-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="460a5-107">ループでクエリの実行が開始されるため、ループの直前までストップウォッチが開始されないことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="460a5-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="460a5-108">さらにきめ細かい測定値が必要な場合は、`ElapsedMilliseconds` ではなく、`ElapsedTicks` プロパティを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="460a5-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="460a5-109">合計実行時間は、クエリの実装を試すときに便利なメトリックですが、これだけでは全貌が明らかにならない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="460a5-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="460a5-110">クエリ スレッド同士およびクエリ スレッドと他の実行中のプロセスとのやり取りをより深くより豊かに視覚化するには、[コンカレンシー ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)を使用します。</span><span class="sxs-lookup"><span data-stu-id="460a5-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="460a5-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="460a5-111">See also</span></span>

- [<span data-ttu-id="460a5-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="460a5-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
