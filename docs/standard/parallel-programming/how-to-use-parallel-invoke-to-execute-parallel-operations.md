---
title: '方法: Parallel.Invoke を使用して並列操作を実行する'
description: タスク並列ライブラリ (TPL) で Parallel.Invoke を使用する方法を確認します。これにより、.NET で共有データ ソースに対して並列操作が行われます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 6ec8f03216cc6225e909f5dc3128469047826166
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825482"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="eed6c-103">方法: Parallel.Invoke を使用して並列操作を実行する</span><span class="sxs-lookup"><span data-stu-id="eed6c-103">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>

<span data-ttu-id="eed6c-104">この例では、タスク並列ライブラリの <xref:System.Threading.Tasks.Parallel.Invoke%2A> を使用して操作を並列化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eed6c-104">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="eed6c-105">共有データ ソースで 3 つの操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="eed6c-105">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="eed6c-106">この操作は、操作でソースが変更されることがないため、簡単に並列実行できます。</span><span class="sxs-lookup"><span data-stu-id="eed6c-106">The operations can be executed in parallel in a straightforward manner, because none of them modifies the source.</span></span>

> [!NOTE]
> <span data-ttu-id="eed6c-107">ここでは、ラムダ式を使用して TPL でデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="eed6c-107">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="eed6c-108">C# または Visual Basic のラムダ式に精通していない場合は、「[PLINQ および TPL のラムダ式](lambda-expressions-in-plinq-and-tpl.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed6c-108">If you aren't familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="eed6c-109">例</span><span class="sxs-lookup"><span data-stu-id="eed6c-109">Example</span></span>

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

<span data-ttu-id="eed6c-110"><xref:System.Threading.Tasks.Parallel.Invoke%2A> を使用すると、どの操作を同時に実行するかを示すだけで、ランタイムによりすべてのスレッドのスケジュール詳細が処理され、ホスト コンピューター上のコア数も自動的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="eed6c-110">With <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>

<span data-ttu-id="eed6c-111">この例では、データではなく操作を並列化します。</span><span class="sxs-lookup"><span data-stu-id="eed6c-111">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="eed6c-112">別の方法としては、PLINQ を使用して LINQ クエリを並列化し、クエリを順番に実行できます。</span><span class="sxs-lookup"><span data-stu-id="eed6c-112">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="eed6c-113">また、PLINQ を使用してデータを並列化することもできます。</span><span class="sxs-lookup"><span data-stu-id="eed6c-113">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="eed6c-114">もう 1 つのオプションとしては、クエリとタスクの両方を並列化する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="eed6c-114">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="eed6c-115">プロセッサの数が比較的少ないホスト コンピューターでは、オーバーヘッドの発生によってパフォーマンスが低下しますが、プロセッサ数の多いコンピューターではパフォーマンスは適切に調整されます。</span><span class="sxs-lookup"><span data-stu-id="eed6c-115">Although the resulting overhead might degrade performance on host computers with relatively few processors, it scales better on computers with many processors.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="eed6c-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="eed6c-116">Compile the Code</span></span>

<span data-ttu-id="eed6c-117">この例の全体をコピーして、Microsoft Visual Studio プロジェクトに貼り付けて **F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="eed6c-117">Copy and paste the entire example into a Microsoft Visual Studio project and press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="eed6c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="eed6c-118">See also</span></span>

- [<span data-ttu-id="eed6c-119">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="eed6c-119">Parallel Programming</span></span>](index.md)
- [<span data-ttu-id="eed6c-120">方法: タスクとその子を取り消す</span><span class="sxs-lookup"><span data-stu-id="eed6c-120">How to: Cancel a Task and Its Children</span></span>](how-to-cancel-a-task-and-its-children.md)
- [<span data-ttu-id="eed6c-121">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="eed6c-121">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
