---
title: 非同期プログラミング
description: 'F # が、コア関数型プログラミングの概念から派生した言語レベルのプログラミングモデルに基づいて、非同期性のクリーンサポートを提供する方法について説明します。'
ms.date: 08/15/2020
ms.openlocfilehash: 8bf8d6987187377cc1f44e77141b5d70d873f849
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366814"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="958d1-103">F での非同期プログラミング\#</span><span class="sxs-lookup"><span data-stu-id="958d1-103">Async programming in F\#</span></span>

<span data-ttu-id="958d1-104">非同期プログラミングは、さまざまな理由で、最新のアプリケーションに不可欠なメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="958d1-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="958d1-105">ほとんどの開発者が直面する主なユースケースには、次の2つがあります。</span><span class="sxs-lookup"><span data-stu-id="958d1-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="958d1-106">多数の同時受信要求を処理できるサーバープロセスを提示する一方で、要求の処理中に使用されるシステムリソースを最小限に抑えながら、そのプロセスの外部のシステムまたはサービスからの入力を待機します。</span><span class="sxs-lookup"><span data-stu-id="958d1-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="958d1-107">バックグラウンド作業の同時進行中に応答性の高い UI またはメインスレッドを維持する</span><span class="sxs-lookup"><span data-stu-id="958d1-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="958d1-108">多くの場合、バックグラウンド作業には複数のスレッドの使用が含まれますが、非同期性とマルチスレッドの概念を個別に考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="958d1-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="958d1-109">実際には、個別の懸念事項であり、もう一方については意味がありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="958d1-110">この記事では、個別の概念について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="958d1-110">This article describes the separate concepts in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="958d1-111">定義された非同期性</span><span class="sxs-lookup"><span data-stu-id="958d1-111">Asynchrony defined</span></span>

<span data-ttu-id="958d1-112">前の点では、非同期性は複数のスレッドの使用状況に依存していません。もう少し説明しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="958d1-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="958d1-113">関連することがある3つの概念がありますが、厳密に独立しています。</span><span class="sxs-lookup"><span data-stu-id="958d1-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="958d1-114">多重複数の計算が重複する時間間隔で実行される場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="958d1-115">次数複数の計算または1つの計算の一部が同時に実行される場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="958d1-116">非同期性メインプログラムフローとは別に1つ以上の計算を実行する場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="958d1-117">これら3つは直交概念ですが、特に一緒に使用する場合は、簡単にまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="958d1-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="958d1-118">たとえば、複数の非同期計算を並行して実行することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="958d1-119">このリレーションシップは、並列処理または非同期性が互いを意味するという意味ではありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-119">This relationship does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="958d1-120">"非同期" という単語の etymology を検討している場合は、次の2つの部分が関係します。</span><span class="sxs-lookup"><span data-stu-id="958d1-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="958d1-121">"a"、つまり "not" を意味します。</span><span class="sxs-lookup"><span data-stu-id="958d1-121">"a", meaning "not".</span></span>
- <span data-ttu-id="958d1-122">"同期"、つまり "同時に"。</span><span class="sxs-lookup"><span data-stu-id="958d1-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="958d1-123">これらの2つの用語をまとめておくと、"非同期" とは "同時に実行しない" ことを意味します。</span><span class="sxs-lookup"><span data-stu-id="958d1-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="958d1-124">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="958d1-124">That's it!</span></span> <span data-ttu-id="958d1-125">この定義では、同時実行または並列処理には意味がありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="958d1-126">これは実際にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="958d1-126">This is also true in practice.</span></span>

<span data-ttu-id="958d1-127">実際には、F # での非同期計算は、メインプログラムフローとは別に実行するようにスケジュールされています。</span><span class="sxs-lookup"><span data-stu-id="958d1-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="958d1-128">この独立した実行は、同時実行または並列処理を意味しません。また、計算が常にバックグラウンドで発生することも意味しません。</span><span class="sxs-lookup"><span data-stu-id="958d1-128">This independent execution doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="958d1-129">実際、非同期計算は、計算の性質と計算が実行されている環境に応じて、同期的に実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="958d1-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="958d1-130">主な通じ重要は、非同期計算はメインプログラムフローに依存しないことです。</span><span class="sxs-lookup"><span data-stu-id="958d1-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="958d1-131">非同期計算を実行するタイミングと方法については、いくつかの保証はありますが、調整とスケジュール設定にはいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="958d1-132">この記事の残りの部分では、F # 非同期性の主要な概念と、F # に組み込まれている型、関数、および式の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="958d1-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="958d1-133">主要な概念</span><span class="sxs-lookup"><span data-stu-id="958d1-133">Core concepts</span></span>

<span data-ttu-id="958d1-134">F # では、非同期プログラミングは次の3つの主要な概念を中心にしています。</span><span class="sxs-lookup"><span data-stu-id="958d1-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="958d1-135">型。これは、 `Async<'T>` コンポーザブルな非同期計算を表します。</span><span class="sxs-lookup"><span data-stu-id="958d1-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="958d1-136">`Async`モジュール関数を使用すると、非同期処理のスケジュール設定、非同期計算の作成、および非同期結果の変換を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="958d1-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="958d1-137">`async { }`[コンピュテーション式](../../language-reference/computation-expressions.md)。非同期計算を構築および制御するための便利な構文を提供します。</span><span class="sxs-lookup"><span data-stu-id="958d1-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="958d1-138">次の例では、これら3つの概念を確認できます。</span><span class="sxs-lookup"><span data-stu-id="958d1-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="958d1-139">この例では、 `printTotalFileBytes` 関数の型は `string -> Async<unit>` です。</span><span class="sxs-lookup"><span data-stu-id="958d1-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="958d1-140">関数を呼び出すと、実際には非同期計算が実行されません。</span><span class="sxs-lookup"><span data-stu-id="958d1-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="958d1-141">代わりに、 `Async<unit>` 非同期的に実行する作業の *仕様* として機能するを返します。</span><span class="sxs-lookup"><span data-stu-id="958d1-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="958d1-142">`Async.AwaitTask`の本体でを呼び出し、の結果を <xref:System.IO.File.ReadAllBytesAsync%2A> 適切な型に変換します。</span><span class="sxs-lookup"><span data-stu-id="958d1-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="958d1-143">もう1つの重要な行は、の呼び出し `Async.RunSynchronously` です。</span><span class="sxs-lookup"><span data-stu-id="958d1-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="958d1-144">これは、実際に F # の非同期計算を実行する場合に呼び出す必要がある非同期モジュール開始関数の1つです。</span><span class="sxs-lookup"><span data-stu-id="958d1-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="958d1-145">これは、プログラミングの C#/Visual Basic スタイルとの基本的な違いです `async` 。</span><span class="sxs-lookup"><span data-stu-id="958d1-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="958d1-146">F # では、非同期計算は **コールドタスク** と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="958d1-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="958d1-147">実際に実行するには、明示的に開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="958d1-148">これにはいくつかの利点があります。これにより、C# または Visual Basic よりもはるかに簡単に、非同期作業を組み合わせてシーケンス処理することができます。</span><span class="sxs-lookup"><span data-stu-id="958d1-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="958d1-149">非同期計算の結合</span><span class="sxs-lookup"><span data-stu-id="958d1-149">Combine asynchronous computations</span></span>

<span data-ttu-id="958d1-150">次に、計算を組み合わせることによって、前の例に基づいて構築する例を示します。</span><span class="sxs-lookup"><span data-stu-id="958d1-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="958d1-151">ご覧のように、関数には `main` さらにいくつかの要素があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-151">As you can see, the `main` function has quite a few more elements.</span></span> <span data-ttu-id="958d1-152">概念的には、次のことが行われます。</span><span class="sxs-lookup"><span data-stu-id="958d1-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="958d1-153">コマンドライン引数を、 `Async<unit>` を使用した計算のシーケンスに変換 `Seq.map` します。</span><span class="sxs-lookup"><span data-stu-id="958d1-153">Transform the command-line arguments into a sequence of `Async<unit>` computations with `Seq.map`.</span></span>
2. <span data-ttu-id="958d1-154">`Async<'T[]>` `printTotalFileBytes` 実行時に並列で計算をスケジュールして実行するを作成します。</span><span class="sxs-lookup"><span data-stu-id="958d1-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="958d1-155">`Async<unit>`並列計算を実行するを作成し、その結果 () を無視し `unit[]` ます。</span><span class="sxs-lookup"><span data-stu-id="958d1-155">Create an `Async<unit>` that will run the parallel computation and ignore its result (which is a `unit[]`).</span></span>
4. <span data-ttu-id="958d1-156">構成された計算全体をで明示的に実行し `Async.RunSynchronously` ます。この処理が完了するまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="958d1-156">Explicitly run the overall composed computation with `Async.RunSynchronously`, blocking until it completes.</span></span>

<span data-ttu-id="958d1-157">このプログラムが実行されると、は `printTotalFileBytes` コマンドライン引数ごとに並列で実行されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="958d1-158">非同期計算はプログラムフローとは無関係に実行されるため、情報を出力して実行を終了する順序は定義されていません。</span><span class="sxs-lookup"><span data-stu-id="958d1-158">Because asynchronous computations execute independently of program flow, there is no defined order in which they print their information and finish executing.</span></span> <span data-ttu-id="958d1-159">計算は並列でスケジュールされますが、実行の順序は保証されません。</span><span class="sxs-lookup"><span data-stu-id="958d1-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="958d1-160">シーケンスの非同期計算</span><span class="sxs-lookup"><span data-stu-id="958d1-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="958d1-161">`Async<'T>`は、既に実行されているタスクではなく作業の仕様であるため、より複雑な変換を簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="958d1-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="958d1-162">非同期計算のセットをシーケンス処理して、1つずつ実行する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="958d1-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn $"File {fileName} has %d{bytes.Length} bytes"
    }

[<EntryPoint>]
let main argv =
    argv
    |> Seq.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="958d1-163">これは、 `printTotalFileBytes` 並列でスケジュールするのではなく、の要素の順序で実行するようにスケジュールされ `argv` ます。</span><span class="sxs-lookup"><span data-stu-id="958d1-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="958d1-164">後続の各操作は、前の計算の実行が完了するまではスケジュールされないため、実行中に重複が発生しないように計算がシーケンス処理されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-164">Because each successive operation will not be scheduled until after the preceding computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="958d1-165">重要な非同期モジュール関数</span><span class="sxs-lookup"><span data-stu-id="958d1-165">Important Async module functions</span></span>

<span data-ttu-id="958d1-166">F # で非同期コードを記述する場合は、通常、計算のスケジューリングを処理するフレームワークと対話します。</span><span class="sxs-lookup"><span data-stu-id="958d1-166">When you write async code in F#, you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="958d1-167">ただし、常にそうであるとは限りません。そのため、非同期処理のスケジュール設定に使用できるさまざまな関数について理解しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="958d1-167">However, this is not always the case, so it is good to understand the various functions that can be used to schedule asynchronous work.</span></span>

<span data-ttu-id="958d1-168">F # の非同期計算は、既に実行されている作業の表現ではなく、作業の _仕様_ であるため、開始関数を使用して明示的に開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="958d1-169">さまざまなコンテキストで役に立つ [非同期開始メソッド](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) が多数あります。</span><span class="sxs-lookup"><span data-stu-id="958d1-169">There are many [Async starting methods](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#section0) that are helpful in different contexts.</span></span> <span data-ttu-id="958d1-170">次のセクションでは、より一般的な開始関数のいくつかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="958d1-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="958d1-171">Async. StartChild</span><span class="sxs-lookup"><span data-stu-id="958d1-171">Async.StartChild</span></span>

<span data-ttu-id="958d1-172">非同期計算内で子計算を開始します。</span><span class="sxs-lookup"><span data-stu-id="958d1-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="958d1-173">これにより、複数の非同期計算を同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="958d1-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="958d1-174">子の計算では、キャンセルトークンを親計算と共有します。</span><span class="sxs-lookup"><span data-stu-id="958d1-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="958d1-175">親の計算が取り消された場合は、子の計算も取り消されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="958d1-176">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="958d1-177">使う状況:</span><span class="sxs-lookup"><span data-stu-id="958d1-177">When to use:</span></span>

- <span data-ttu-id="958d1-178">一度に1つずつではなく、複数の非同期計算を同時に実行するが、並列でスケジュールされていない場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="958d1-179">子計算の有効期間を親計算の有効期間に関連付ける場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="958d1-180">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-180">What to watch out for:</span></span>

- <span data-ttu-id="958d1-181">で複数の計算を開始 `Async.StartChild` することは、並列でのスケジュール設定と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="958d1-182">計算を並列でスケジュールする場合は、を使用し `Async.Parallel` ます。</span><span class="sxs-lookup"><span data-stu-id="958d1-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="958d1-183">親計算を取り消すと、開始したすべての子計算の取り消しがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="958d1-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="958d1-184">StartImmediate</span><span class="sxs-lookup"><span data-stu-id="958d1-184">Async.StartImmediate</span></span>

<span data-ttu-id="958d1-185">非同期計算を実行し、現在のオペレーティング システムのスレッドですぐに開始します。</span><span class="sxs-lookup"><span data-stu-id="958d1-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="958d1-186">これは、計算中に呼び出し元のスレッドで何かを更新する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="958d1-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="958d1-187">たとえば、非同期計算で UI を更新する必要がある場合 (進行状況バーを更新するなど) は、を `Async.StartImmediate` 使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="958d1-188">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-188">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="958d1-189">使う状況:</span><span class="sxs-lookup"><span data-stu-id="958d1-189">When to use:</span></span>

- <span data-ttu-id="958d1-190">非同期計算の途中で、呼び出し元のスレッドで何かを更新する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="958d1-191">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-191">What to watch out for:</span></span>

- <span data-ttu-id="958d1-192">非同期計算のコードは、スケジュールされている任意のスレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="958d1-193">これは、そのスレッドが UI スレッドなど、何らかの方法で重要な場合に問題になることがあります。</span><span class="sxs-lookup"><span data-stu-id="958d1-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="958d1-194">このような場合 `Async.StartImmediate` は、を使用するのが不適切である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="958d1-195">Async.startastask</span><span class="sxs-lookup"><span data-stu-id="958d1-195">Async.StartAsTask</span></span>

<span data-ttu-id="958d1-196">スレッド プールで計算を実行します。</span><span class="sxs-lookup"><span data-stu-id="958d1-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="958d1-197"><xref:System.Threading.Tasks.Task%601>計算が終了した後、対応する状態で完了するを返します (結果を生成するか、例外をスローするか、またはキャンセルします)。</span><span class="sxs-lookup"><span data-stu-id="958d1-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="958d1-198">キャンセルトークンが指定されていない場合は、既定のキャンセルトークンが使用されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="958d1-199">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-199">Signature:</span></span>

```fsharp
computation: Async<'T> * taskCreationOptions: ?TaskCreationOptions * cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="958d1-200">使う状況:</span><span class="sxs-lookup"><span data-stu-id="958d1-200">When to use:</span></span>

- <span data-ttu-id="958d1-201"><xref:System.Threading.Tasks.Task%601>非同期計算の結果を表すためにを生成する .NET API を呼び出す必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-201">When you need to call into a .NET API that yields a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="958d1-202">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-202">What to watch out for:</span></span>

- <span data-ttu-id="958d1-203">この呼び出しにより、追加のオブジェクトが割り当てられます `Task` 。これにより、頻繁に使用される場合にオーバーヘッドが増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="958d1-204">Async. Parallel</span><span class="sxs-lookup"><span data-stu-id="958d1-204">Async.Parallel</span></span>

<span data-ttu-id="958d1-205">並列実行される一連の非同期計算をスケジュールし、指定された順序で結果の配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="958d1-205">Schedules a sequence of asynchronous computations to be executed in parallel, yielding an array of results in the order they were supplied.</span></span> <span data-ttu-id="958d1-206">並列処理の次数は、パラメーターを指定することによって、必要に応じてチューニング/調整できます `maxDegreeOfParallelism` 。</span><span class="sxs-lookup"><span data-stu-id="958d1-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreeOfParallelism` parameter.</span></span>

<span data-ttu-id="958d1-207">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> * ?maxDegreeOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="958d1-208">使用するタイミング:</span><span class="sxs-lookup"><span data-stu-id="958d1-208">When to use it:</span></span>

- <span data-ttu-id="958d1-209">一連の計算を同時に実行する必要があり、実行の順序に依存しない場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="958d1-210">すべてが完了するまで並列でスケジュールされた計算結果を必要としない場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="958d1-211">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-211">What to watch out for:</span></span>

- <span data-ttu-id="958d1-212">すべての計算が完了すると、結果として得られる値の配列にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="958d1-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="958d1-213">計算は、スケジュールが設定されると終了するたびに実行されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-213">Computations will be run whenever they end up getting scheduled.</span></span> <span data-ttu-id="958d1-214">この動作は、実行順序に依存できないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="958d1-214">This behavior means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="958d1-215">Async。シーケンシャル</span><span class="sxs-lookup"><span data-stu-id="958d1-215">Async.Sequential</span></span>

<span data-ttu-id="958d1-216">渡された順序で実行される一連の非同期計算をスケジュールします。</span><span class="sxs-lookup"><span data-stu-id="958d1-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="958d1-217">最初の計算が実行され、その後、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="958d1-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="958d1-218">並列では計算は実行されません。</span><span class="sxs-lookup"><span data-stu-id="958d1-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="958d1-219">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="958d1-220">使用するタイミング:</span><span class="sxs-lookup"><span data-stu-id="958d1-220">When to use it:</span></span>

- <span data-ttu-id="958d1-221">複数の計算を順番に実行する必要がある場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="958d1-222">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-222">What to watch out for:</span></span>

- <span data-ttu-id="958d1-223">すべての計算が完了すると、結果として得られる値の配列にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="958d1-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="958d1-224">計算は、この関数に渡される順序で実行されます。そのため、結果が返されるまでに時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="958d1-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="958d1-225">Async. AwaitTask</span><span class="sxs-lookup"><span data-stu-id="958d1-225">Async.AwaitTask</span></span>

<span data-ttu-id="958d1-226">指定されたの完了を待機し、その <xref:System.Threading.Tasks.Task%601> 結果をとして返す非同期計算を返します。 `Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="958d1-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="958d1-227">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-227">Signature:</span></span>

```fsharp
task: Task<'T> -> Async<'T>
```

<span data-ttu-id="958d1-228">使う状況:</span><span class="sxs-lookup"><span data-stu-id="958d1-228">When to use:</span></span>

- <span data-ttu-id="958d1-229"><xref:System.Threading.Tasks.Task%601>F # の非同期計算内でを返す .NET API を使用する場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="958d1-230">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-230">What to watch out for:</span></span>

- <span data-ttu-id="958d1-231">例外は、 <xref:System.AggregateException> タスク並列ライブラリの規則に従ってラップされます。この動作は、F # の非同期で一般的に例外が表面化する方法とは異なります。</span><span class="sxs-lookup"><span data-stu-id="958d1-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library; this behavior is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="958d1-232">Async. Catch</span><span class="sxs-lookup"><span data-stu-id="958d1-232">Async.Catch</span></span>

<span data-ttu-id="958d1-233">指定されたを実行し、を返す非同期計算を作成し `Async<'T>` `Async<Choice<'T, exn>>` ます。</span><span class="sxs-lookup"><span data-stu-id="958d1-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="958d1-234">指定されたが正常に完了した場合は、 `Async<'T>` `Choice1Of2` 結果の値と共にが返されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="958d1-235">完了前に例外がスローされた場合は、発生した `Choice2of2` 例外と共にが返されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="958d1-236">多くの計算で構成され、その計算の1つが例外をスローする非同期計算で使用される場合、外側の計算は完全に停止されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="958d1-237">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="958d1-238">使う状況:</span><span class="sxs-lookup"><span data-stu-id="958d1-238">When to use:</span></span>

- <span data-ttu-id="958d1-239">例外によって失敗する可能性があり、呼び出し元でその例外を処理する必要がある非同期処理を実行する場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="958d1-240">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-240">What to watch out for:</span></span>

- <span data-ttu-id="958d1-241">結合またはシーケンスされた非同期計算を使用する場合、その "内部" 計算の1つが例外をスローすると、外側の計算が完全に停止します。</span><span class="sxs-lookup"><span data-stu-id="958d1-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="958d1-242">Async. Ignore</span><span class="sxs-lookup"><span data-stu-id="958d1-242">Async.Ignore</span></span>

<span data-ttu-id="958d1-243">指定された計算を実行する非同期計算を作成しますが、その結果は削除されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-243">Creates an asynchronous computation that runs the given computation but drops its result.</span></span>

<span data-ttu-id="958d1-244">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="958d1-245">使う状況:</span><span class="sxs-lookup"><span data-stu-id="958d1-245">When to use:</span></span>

- <span data-ttu-id="958d1-246">結果が不要な非同期計算がある場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="958d1-247">これは、非同期で `ignore` ないコードの関数に似ています。</span><span class="sxs-lookup"><span data-stu-id="958d1-247">This is analogous to the `ignore` function for non-asynchronous code.</span></span>

<span data-ttu-id="958d1-248">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-248">What to watch out for:</span></span>

- <span data-ttu-id="958d1-249">またはを必要とする別の関数を使用するためにを使用する必要がある場合は `Async.Ignore` `Async.Start` `Async<unit>` 、結果を破棄するかどうかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="958d1-249">If you must use `Async.Ignore` because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay.</span></span> <span data-ttu-id="958d1-250">型シグネチャに一致するように結果を破棄しないでください。</span><span class="sxs-lookup"><span data-stu-id="958d1-250">Avoid discarding results just to fit a type signature.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="958d1-251">Async. RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="958d1-251">Async.RunSynchronously</span></span>

<span data-ttu-id="958d1-252">非同期計算を実行し、呼び出し元のスレッドでその結果を待機します。</span><span class="sxs-lookup"><span data-stu-id="958d1-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="958d1-253">計算によって例外が生成されるように、例外を伝達します。</span><span class="sxs-lookup"><span data-stu-id="958d1-253">Propagates an exception should the computation yield one.</span></span> <span data-ttu-id="958d1-254">この呼び出しはブロックされています。</span><span class="sxs-lookup"><span data-stu-id="958d1-254">This call is blocking.</span></span>

<span data-ttu-id="958d1-255">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-255">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int * cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="958d1-256">使用するタイミング:</span><span class="sxs-lookup"><span data-stu-id="958d1-256">When to use it:</span></span>

- <span data-ttu-id="958d1-257">必要に応じて、実行可能ファイルのエントリポイントで、アプリケーション内で1回だけ使用します。</span><span class="sxs-lookup"><span data-stu-id="958d1-257">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="958d1-258">パフォーマンスを気にせずに、他の一連の非同期操作を一度に実行する場合。</span><span class="sxs-lookup"><span data-stu-id="958d1-258">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="958d1-259">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-259">What to watch out for:</span></span>

- <span data-ttu-id="958d1-260">を呼び出す `Async.RunSynchronously` と、実行が完了するまで呼び出し元のスレッドがブロックされます。</span><span class="sxs-lookup"><span data-stu-id="958d1-260">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="958d1-261">Async。開始</span><span class="sxs-lookup"><span data-stu-id="958d1-261">Async.Start</span></span>

<span data-ttu-id="958d1-262">スレッドプールでを返す非同期計算を開始 `unit` します。</span><span class="sxs-lookup"><span data-stu-id="958d1-262">Starts an asynchronous computation that returns `unit` in the thread pool.</span></span> <span data-ttu-id="958d1-263">は、完了するのを待たず、または例外の結果を観察します。</span><span class="sxs-lookup"><span data-stu-id="958d1-263">Doesn't wait for its completion and/or observe an exception outcome.</span></span> <span data-ttu-id="958d1-264">で開始した入れ子になった計算 `Async.Start` は、それらを呼び出した親計算とは無関係に開始されます。有効期間は親計算に関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="958d1-264">Nested computations started with `Async.Start` are started independently of the parent computation that called them; their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="958d1-265">親計算が取り消された場合、子計算は取り消されません。</span><span class="sxs-lookup"><span data-stu-id="958d1-265">If the parent computation is canceled, no child computations are canceled.</span></span>

<span data-ttu-id="958d1-266">署名:</span><span class="sxs-lookup"><span data-stu-id="958d1-266">Signature:</span></span>

```fsharp
computation: Async<unit> * cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="958d1-267">次の場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="958d1-267">Use only when:</span></span>

- <span data-ttu-id="958d1-268">非同期計算によって結果が得られないか、または処理が必要ありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="958d1-269">非同期計算がいつ完了するかを知る必要はありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="958d1-270">非同期計算を実行するスレッドを気にする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="958d1-271">実行の結果として発生した例外を認識したりレポートしたりする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-271">You don't have any need to be aware of or report exceptions resulting from the execution.</span></span>

<span data-ttu-id="958d1-272">注意事項:</span><span class="sxs-lookup"><span data-stu-id="958d1-272">What to watch out for:</span></span>

- <span data-ttu-id="958d1-273">で開始された計算によって発生した例外 `Async.Start` は、呼び出し元に反映されません。</span><span class="sxs-lookup"><span data-stu-id="958d1-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="958d1-274">呼び出し履歴は完全にアンワインドされます。</span><span class="sxs-lookup"><span data-stu-id="958d1-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="958d1-275">で開始された作業 (を呼び出した場合など `printfn` ) で `Async.Start` は、プログラムの実行のメインスレッドで効果が発生しません。</span><span class="sxs-lookup"><span data-stu-id="958d1-275">Any work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="958d1-276">.NET との相互運用</span><span class="sxs-lookup"><span data-stu-id="958d1-276">Interoperate with .NET</span></span>

<span data-ttu-id="958d1-277">[Async/await](../../../standard/async.md)スタイルの非同期プログラミングを使用する .net ライブラリまたは C# のコードベースを使用する場合があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="958d1-278">C# およびほとんどの .NET ライブラリでは、との型は、で <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> はなく、の中核となる抽象化として使用されるため `Async<'T>` 、これら2つの方法の間の境界を非同期性に越える必要があります。</span><span class="sxs-lookup"><span data-stu-id="958d1-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="958d1-279">.NET async およびを使用する方法 `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="958d1-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="958d1-280">を使用する .NET 非同期ライブラリおよびコードベースの操作 <xref:System.Threading.Tasks.Task%601> (つまり、戻り値を持つ非同期計算) は簡単で、F # を使用した組み込みのサポートがあります。</span><span class="sxs-lookup"><span data-stu-id="958d1-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="958d1-281">関数を使用すると、 `Async.AwaitTask` .net の非同期計算を待機できます。</span><span class="sxs-lookup"><span data-stu-id="958d1-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="958d1-282">関数を使用すると、 `Async.StartAsTask` 非同期計算を .net 呼び出し元に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="958d1-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="958d1-283">.NET async およびを使用する方法 `Task`</span><span class="sxs-lookup"><span data-stu-id="958d1-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="958d1-284">(つまり、値を返さない .NET 非同期計算) を使用する Api を操作するには、を <xref:System.Threading.Tasks.Task> に変換する関数を追加する必要があり `Async<'T>` <xref:System.Threading.Tasks.Task> ます。</span><span class="sxs-lookup"><span data-stu-id="958d1-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="958d1-285">`Async.AwaitTask`を入力として受け取るが既に存在し <xref:System.Threading.Tasks.Task> ます。</span><span class="sxs-lookup"><span data-stu-id="958d1-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="958d1-286">これと以前に定義された関数を使用すると、 `startTaskFromAsyncUnit` <xref:System.Threading.Tasks.Task> F # の非同期計算から型を開始および待機できます。</span><span class="sxs-lookup"><span data-stu-id="958d1-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="958d1-287">マルチスレッドとの関係</span><span class="sxs-lookup"><span data-stu-id="958d1-287">Relationship to multi-threading</span></span>

<span data-ttu-id="958d1-288">この記事ではスレッド処理について説明していますが、次の2つの重要な点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="958d1-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="958d1-289">現在のスレッドで明示的に開始されている場合を除き、非同期計算とスレッド間の関係はありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="958d1-290">F # での非同期プログラミングは、マルチスレッドの抽象的なものではありません。</span><span class="sxs-lookup"><span data-stu-id="958d1-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="958d1-291">たとえば、作業の性質に応じて、実際には、呼び出し元のスレッドで計算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="958d1-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="958d1-292">また、計算では、スレッド間の "ジャンプ" によって、"待機中" の期間 (ネットワーク呼び出しが転送中の場合など) の間に有用な作業を行うために、スレッド間を "移動" できます。</span><span class="sxs-lookup"><span data-stu-id="958d1-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="958d1-293">F # では、現在のスレッドで (または現在のスレッドではなく) 非同期計算を開始する機能が提供されますが、非同期性は通常、特定のスレッド処理方法に関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="958d1-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="958d1-294">関連項目</span><span class="sxs-lookup"><span data-stu-id="958d1-294">See also</span></span>

- [<span data-ttu-id="958d1-295">F # の非同期プログラミングモデル</span><span class="sxs-lookup"><span data-stu-id="958d1-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="958d1-296">Jet .com の F # 非同期ガイド</span><span class="sxs-lookup"><span data-stu-id="958d1-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="958d1-297">楽しいと利益の非同期プログラミングガイドの F #</span><span class="sxs-lookup"><span data-stu-id="958d1-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="958d1-298">C# および F # での Async: C での非同期の課題#</span><span class="sxs-lookup"><span data-stu-id="958d1-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
