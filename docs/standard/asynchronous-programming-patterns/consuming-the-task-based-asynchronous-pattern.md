---
title: タスク ベースの非同期パターンの利用
description: 非同期操作を行う場合のタスク ベースの非同期パターン (TAP) の利用について学習します。
ms.date: 03/30/2017
helpviewer_keywords:
- .NET and TAP
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: 312a86f38335f1c16a4286795f04b9a80a9ea03f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678130"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="42b6d-103">タスク ベースの非同期パターンの利用</span><span class="sxs-lookup"><span data-stu-id="42b6d-103">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="42b6d-104">タスク ベースの非同期パターン (TAP) を使用して非同期操作を行うと、コールバックを使用して、ブロックすることなく待機できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-104">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span> <span data-ttu-id="42b6d-105">タスクの場合、これは <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType> などのメソッドによって行われます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-105">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="42b6d-106">言語ベースの非同期サポートが、通常の制御フロー内での非同期操作の待機を許可することで、コールバックを隠し、コンパイラにより生成されたコードはこの同じ API レベルのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-106">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="42b6d-107">Await による実行の中断</span><span class="sxs-lookup"><span data-stu-id="42b6d-107">Suspending Execution with Await</span></span>

<span data-ttu-id="42b6d-108"><xref:System.Threading.Tasks.Task> オブジェクトおよび <xref:System.Threading.Tasks.Task%601> オブジェクトの非同期での待機には、C# では [await](../../csharp/language-reference/operators/await.md) キーワード、Visual Basic では [Await 演算子](../../visual-basic/language-reference/operators/await-operator.md)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-108">You can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="42b6d-109"><xref:System.Threading.Tasks.Task> を待っているとき、`await` 式は型 `void` になります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-109">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="42b6d-110"><xref:System.Threading.Tasks.Task%601> を待っているとき、`await` 式は型 `TResult` になります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-110">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="42b6d-111">`await` 式は、非同期メソッドの本体内に含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-111">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="42b6d-112">(これらの言語機能は .NET Framework 4.5 で導入されました)。</span><span class="sxs-lookup"><span data-stu-id="42b6d-112">(These language features were introduced in .NET Framework 4.5.)</span></span>

 <span data-ttu-id="42b6d-113">待機機能は、隠れた状態で継続を使用してタスクにコールバックをインストールします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-113">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="42b6d-114">このコールバックは中断ポイントから非同期メソッドを再開します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-114">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="42b6d-115">非同期メソッドが再開され、待機していた操作が正常に完了し、<xref:System.Threading.Tasks.Task%601> であった場合に、その `TResult` が返されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-115">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="42b6d-116">待っていた <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> が <xref:System.Threading.Tasks.TaskStatus.Canceled> 状態で終わった場合、<xref:System.OperationCanceledException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="42b6d-117">待っていた <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> が <xref:System.Threading.Tasks.TaskStatus.Faulted> 状態で終わった場合、エラーの原因となった例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-117">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="42b6d-118">`Task` は複数の例外の結果としてエラーになることがありますが、反映されるのはこれらの例外の中の 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="42b6d-118">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="42b6d-119">ただし、<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> プロパティは、すべてのエラーが含まれる <xref:System.AggregateException> 例外を返します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-119">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="42b6d-120">中断時に非同期メソッドを実行していたスレッドに同期コンテキスト (<xref:System.Threading.SynchronizationContext> オブジェクト) が関連付けられている場合 (たとえば、<xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> プロパティが `null` ではない場合)、非同期メソッドは、コンテキストの <xref:System.Threading.SynchronizationContext.Post%2A> メソッドを使用して、その同じ同期コンテキストで再開します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-120">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context's <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="42b6d-121">そのように関連付けられていない場合、中断時に実行されていたタスク スケジューラ (<xref:System.Threading.Tasks.TaskScheduler> オブジェクト) に基づきます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-121">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="42b6d-122">通常、これは既定のタスク スケジューラ (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>) であり、スレッド プールをターゲットにします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-122">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="42b6d-123">このタスク スケジューラによって、待機していた非同期操作が完了した場合に再開するかどうか、または再開のスケジュールを設定するかどうかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-123">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="42b6d-124">既定のスケジューラは、通常、待機していた操作が完了したスレッド上での実行の継続を許可します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-124">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="42b6d-125">非同期メソッドが呼び出された場合、まだ完了していない待機可能なインスタンスの最初の await 式まで、関数の本体を同期をとって実行し、この時点で呼び出しを呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-125">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="42b6d-126">非同期メソッドが `void` を返さない場合、進行中の計算を表す <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> オブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-126">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="42b6d-127">void 以外の非同期メソッドでは、return ステートメントが検出された場合、またはメソッド本体の末尾に到達した場合、タスクが <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> の終了状態で完了します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-127">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="42b6d-128">ハンドルされない例外により、非同期メソッドの本体から制御が離れた場合、タスクは <xref:System.Threading.Tasks.TaskStatus.Faulted> 状態になります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-128">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="42b6d-129">その例外が <xref:System.OperationCanceledException> の場合、タスクは代わりに <xref:System.Threading.Tasks.TaskStatus.Canceled> 状態で終わります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-129">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="42b6d-130">この方法では、結果または例外が最終的に発行されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-130">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="42b6d-131">この動作には、いくつかの重要なバリエーションがあります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-131">There are several important variations of this behavior.</span></span>  <span data-ttu-id="42b6d-132">タスクが待機されるまでに既に完了していた場合は、パフォーマンス上の理由から、制御が明け渡されず、関数が実行を継続します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-132">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="42b6d-133">また、元のコンテキストに戻ることが必ずしも望ましい動作ではない場合は変更されることがあります。これは、次のセクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-133">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="42b6d-134">Yield と ConfigureAwait を使用して中断と再開を構成する</span><span class="sxs-lookup"><span data-stu-id="42b6d-134">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>

 <span data-ttu-id="42b6d-135">いくつかのメソッドでは、非同期メソッドの実行をより詳細に制御できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-135">Several methods provide more control over an asynchronous method's execution.</span></span> <span data-ttu-id="42b6d-136">たとえば、<xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> メソッドを使用し、yield ポイントを非同期メソッドに伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-136">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="42b6d-137">これは、非同期にポストするか、現在のコンテキストにスケジュールを戻すことと同じです。</span><span class="sxs-lookup"><span data-stu-id="42b6d-137">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="42b6d-138"><xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> メソッドを使用することもできます。非同期メソッドでの中断と再開でより優れた制御機能が与えられます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-138">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="42b6d-139">前述のとおり、既定では、現在のコンテキストは、非同期メソッドが中断されたときにキャプチャされ、そのキャプチャされたコンテキストは、再開時に非同期メソッドの継続を呼び出すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-139">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method's continuation upon resumption.</span></span>  <span data-ttu-id="42b6d-140">これは、多くの場合に求められる動作です。</span><span class="sxs-lookup"><span data-stu-id="42b6d-140">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="42b6d-141">その他の場合では、継続のコンテキストが重要でないこともあり、元のコンテキストへのポスト バックを回避することでパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-141">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="42b6d-142">そのためには、<xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> メソッドを使用して、待機操作にコンテキストをキャプチャして再開するのではなく、待機していた非同期操作がどこで完了したかを問わず、実行を継続するように指示できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-142">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="42b6d-143">非同期操作の取り消し</span><span class="sxs-lookup"><span data-stu-id="42b6d-143">Canceling an Asynchronous Operation</span></span>

<span data-ttu-id="42b6d-144">.NET Framework 4 以降、取り消しをサポートする TAP メソッドには、取り消しトークン (<xref:System.Threading.CancellationToken> オブジェクト) を受け取るオーバーロードが少なくとも 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-144">Starting with .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="42b6d-145">キャンセル トークンは、キャンセル トークンのソース (<xref:System.Threading.CancellationTokenSource> オブジェクト) によって作成されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-145">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="42b6d-146">ソースの <xref:System.Threading.CancellationTokenSource.Token%2A> プロパティからキャンセル トークンが返され、ソースの <xref:System.Threading.CancellationTokenSource.Cancel%2A> メソッドが呼び出されたときにこのトークンに信号が送られます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-146">The source's <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="42b6d-147">たとえば、単一の Web ページをダウンロードする際に操作を取り消せるようにする場合は、<xref:System.Threading.CancellationTokenSource> オブジェクトを作成し、TAP メソッドにそのオブジェクトのトークンを渡し、操作を取り消す準備ができたらソースの <xref:System.Threading.CancellationTokenSource.Cancel%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-147">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="42b6d-148">複数の非同期呼び出しを取り消す場合は、すべての呼び出しに同じトークンを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-148">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="42b6d-149">または、操作の一部を選択して同じトークンを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-149">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="42b6d-150">取り消し要求は任意のスレッドから開始することができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-150">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="42b6d-151">取り消しが要求されないことを示すために、キャンセル トークンを受け取るすべてのメソッドに <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> 値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-151">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="42b6d-152">これで <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> プロパティが `false` を返します。呼び出されたメソッドは適宜最適化できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-152">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="42b6d-153">テストのためには、トークンが既に取り消された状態か取り消し不可能な状態で開始するかどうかを示すブール値を受け取るコンストラクターを使用してインスタンス化した、事前に取り消されたキャンセル トークンを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-153">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="42b6d-154">この取り消し方法には、いくつか利点があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-154">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="42b6d-155">同じキャンセル トークンを、任意の数の同期操作および非同期操作に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-155">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="42b6d-156">同じ取り消し要求を、任意の数のリスナーに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-156">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="42b6d-157">取り消しが要求されるかどうか、およびそれがいつ実行されるかは、非同期 API の開発者が完全に制御します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-157">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="42b6d-158">API を使用するコードにより、取り消し要求が反映される非同期呼び出しが選択され、決定されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-158">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="42b6d-159">進行状況の監視</span><span class="sxs-lookup"><span data-stu-id="42b6d-159">Monitoring Progress</span></span>

 <span data-ttu-id="42b6d-160">一部の非同期メソッドは、非同期メソッドに渡される進行状況インターフェイスを通じて進行状況を公開します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-160">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="42b6d-161">たとえば、テキスト文字列を非同期的にダウンロードし、その過程で、これまでに完了したダウンロードの割合を含む進行状況の更新を発生させる関数があるとします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-161">For example, consider a function that asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="42b6d-162">このようなメソッドは、Windows Presentation Foundation (WPF) アプリケーションでは次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-162">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>

## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="42b6d-163">タスク ベースの組み込み連結子の使用</span><span class="sxs-lookup"><span data-stu-id="42b6d-163">Using the Built-in Task-based Combinators</span></span>

 <span data-ttu-id="42b6d-164"><xref:System.Threading.Tasks> 名前空間には、タスクを構成および使用するための複数のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-164">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="42b6d-165">Task.Run</span><span class="sxs-lookup"><span data-stu-id="42b6d-165">Task.Run</span></span>

 <span data-ttu-id="42b6d-166"><xref:System.Threading.Tasks.Task> クラスには、<xref:System.Threading.Tasks.Task.Run%2A> メソッドがいくつか含まれています。このメソッドでは、次のように、<xref:System.Threading.Tasks.Task> や <xref:System.Threading.Tasks.Task%601> のような作業の負荷をスレッド プールに簡単に移すことができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-166">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="42b6d-167"><xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> オーバーロードなど、これらの <xref:System.Threading.Tasks.Task.Run%2A> メソッドの一部は <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> メソッドの短縮形として存在します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-167">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="42b6d-168"><xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> など、他のオーバーロードでは、次のように、負荷分散される作業内で await を使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-168">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="42b6d-169">このようなオーバーロードは論理的に、タスク並列ライブラリの <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 拡張メソッドとの連動で <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> メソッドを使用することと等しくなります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-169">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="42b6d-170">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="42b6d-170">Task.FromResult</span></span>

 <span data-ttu-id="42b6d-171">データが既に利用でき、単に <xref:System.Threading.Tasks.Task%601> にリフトされたタスクを返すメソッドから返す必要があるシナリオでは、<xref:System.Threading.Tasks.Task.FromResult%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-171">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="42b6d-172">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="42b6d-172">Task.WhenAll</span></span>

 <span data-ttu-id="42b6d-173"><xref:System.Threading.Tasks.Task.WhenAll%2A> メソッドは、タスクとして表される複数の非同期操作で非同期に待機するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-173">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="42b6d-174">メソッドには、一連の非ジェネリック タスクまたは不均一な一連のジェネリック タスク (複数の void を返す操作を非同期に待機したり、各値の型が異なる複数の値を返すメソッドを非同期に待機するなど) に加えて、均一な一連のジェネリック タスク (複数の `TResult` を返すメソッドを非同期に待機するなど) をサポートする複数のオーバーロードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-174">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="42b6d-175">複数の顧客に電子メール メッセージを送信するとします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-175">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="42b6d-176">このような場合、1 つのメッセージの送信完了を待たずに次のメッセージを送信するような、メッセージのオーバーラップ送信が可能です。</span><span class="sxs-lookup"><span data-stu-id="42b6d-176">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="42b6d-177">送信操作がいつ完了したか、またエラーが発生したかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-177">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="42b6d-178">このコードは発生する可能性がある例外を明示的に処理せず、<xref:System.Threading.Tasks.Task.WhenAll%2A> の結果のタスクの `await` から例外を反映します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-178">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="42b6d-179">例外を処理するには、次のようなコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-179">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="42b6d-180">この例では、非同期の操作が失敗した場合、すべての例外が <xref:System.AggregateException> 例外で連結され、<xref:System.Threading.Tasks.Task.WhenAll%2A> メソッドから返される <xref:System.Threading.Tasks.Task> に格納されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-180">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="42b6d-181">ただし、これらの例外の 1 つだけが `await` キーワードによって反映されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-181">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="42b6d-182">すべての例外を調べる場合は、上記のコードを次のように書き直します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-182">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="42b6d-183">Web から複数のファイルを非同期にダウンロードする例を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-183">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="42b6d-184">この場合、すべての非同期操作の結果の型が同種で、結果に簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-184">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="42b6d-185">前の void を返す場合で説明したのと同じ例外処理手法を使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-185">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task<string> [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="42b6d-186">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="42b6d-186">Task.WhenAny</span></span>

 <span data-ttu-id="42b6d-187"><xref:System.Threading.Tasks.Task.WhenAny%2A> メソッドを使用して、完了するタスクとして表される複数の非同期操作の 1 つのみを非同期に待機できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-187">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="42b6d-188">このメソッドは、次の 4 つの主なユース ケースで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-188">This method serves four primary use cases:</span></span>

- <span data-ttu-id="42b6d-189">冗長性:1 つの操作を複数回実行し、最初に完了したものを選択する (たとえば、1 つの結果を生成する複数の株価情報 Web サービスに問い合わせて、最も速く完了したものを選択する)。</span><span class="sxs-lookup"><span data-stu-id="42b6d-189">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="42b6d-190">インターリーブ:複数の操作を起動してそのすべてが完了するまで待機するが、処理は各完了時点で行う。</span><span class="sxs-lookup"><span data-stu-id="42b6d-190">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="42b6d-191">調整:他が完了した時点で、追加の操作を開始できる。</span><span class="sxs-lookup"><span data-stu-id="42b6d-191">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="42b6d-192">これは、インターリーブのシナリオを拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="42b6d-192">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="42b6d-193">初期のエスケープ:たとえば、タスク t1 が表す操作を別のタスク t2 と共に <xref:System.Threading.Tasks.Task.WhenAny%2A> タスクでグループにまとめ、<xref:System.Threading.Tasks.Task.WhenAny%2A> タスク上で待機できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-193">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="42b6d-194">タスク t2 は、タイムアウトか取り消し、または <xref:System.Threading.Tasks.Task.WhenAny%2A> タスクを t1 の前に完了するようなその他のシグナルを表す場合があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-194">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="42b6d-195">冗長性</span><span class="sxs-lookup"><span data-stu-id="42b6d-195">Redundancy</span></span>

 <span data-ttu-id="42b6d-196">株式を購入するかどうかを決定するとします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-196">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="42b6d-197">信頼できるいくつかの株式推薦 Web サービスがありますが、日常的な負荷によっては、時に応じて各サービスがかなり遅くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-197">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="42b6d-198"><xref:System.Threading.Tasks.Task.WhenAny%2A> メソッドを使用すると、いずれかの操作が完了したときに通知を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-198">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="42b6d-199">正常に完了したすべてのタスクの結果をラップせずに返す <xref:System.Threading.Tasks.Task.WhenAll%2A> とは異なり、<xref:System.Threading.Tasks.Task.WhenAny%2A> は完了したタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-199">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="42b6d-200">タスクが失敗した場合は、それを把握することが重要です。タスクが成功した場合は、戻り値が関連付けられているタスクを把握することが重要です。</span><span class="sxs-lookup"><span data-stu-id="42b6d-200">If a task fails, it's important to know that it failed, and if a task succeeds, it's important to know which task the return value is associated with.</span></span>  <span data-ttu-id="42b6d-201">そのため、この例で示すように、返されるタスクの結果にアクセスするか、引き続き待機する必要があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-201">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="42b6d-202"><xref:System.Threading.Tasks.Task.WhenAll%2A> と同様に、例外に対応できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-202">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="42b6d-203">完了したタスクを受け取るので、適切に `try/catch` で囲んで、エラーが反映されて返されるタスクを待機できます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-203">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="42b6d-204">さらに、最初のタスクが正常に完了しても、以降のタスクが失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-204">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="42b6d-205">この時点で、例外を処理する方法はいくつかあります。起動したすべてのタスクが完了するまで待機できます。その場合は、<xref:System.Threading.Tasks.Task.WhenAll%2A> メソッドを使用するか、あるいは、すべての例外が重要であり、ログに記録する必要があると指定してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="42b6d-205">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="42b6d-206">そのためには、継続を使用してタスクが非同期に完了した時点で通知を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-206">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="42b6d-207">または</span><span class="sxs-lookup"><span data-stu-id="42b6d-207">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="42b6d-208">または、以下のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-208">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="42b6d-209">最後に、残りのすべての操作を取り消すこともできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-209">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="42b6d-210">インターリーブ</span><span class="sxs-lookup"><span data-stu-id="42b6d-210">Interleaving</span></span>

 <span data-ttu-id="42b6d-211">Web からイメージをダウンロードして、各イメージを処理するとします (イメージを UI コントロールに追加するなど)。</span><span class="sxs-lookup"><span data-stu-id="42b6d-211">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span> <span data-ttu-id="42b6d-212">UI スレッドで順次イメージを処理しても、イメージはできるだけ同時にダウンロードしたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="42b6d-212">You process the images sequentially on the UI thread, but want to download the images as concurrently as possible.</span></span> <span data-ttu-id="42b6d-213">また、すべてダウンロードされるまで、UI へのイメージの追加を保留したくないと考えています。</span><span class="sxs-lookup"><span data-stu-id="42b6d-213">Also, you don't want to hold up adding the images to the UI until they're all downloaded.</span></span> <span data-ttu-id="42b6d-214">代わりに、それらを完了時に追加したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="42b6d-214">Instead, you want to add them as they complete.</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="42b6d-215">次のように、ダウンロードしたイメージの <xref:System.Threading.ThreadPool> でコンピューター処理を集中して行うことが必要になるシナリオでも、インターリーブを適用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-215">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="42b6d-216">調整</span><span class="sxs-lookup"><span data-stu-id="42b6d-216">Throttling</span></span>

 <span data-ttu-id="42b6d-217">インターリーブの例ではユーザーが多くのイメージをダウンロードするため、このダウンロード数を絞り込み、たとえば、特定の数のダウンロードだけを同時実行する必要がある場合を考えます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-217">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="42b6d-218">これを行うには、非同期操作のサブセットを開始します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-218">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="42b6d-219">操作が完了したら、追加操作を開始して、完了した操作に代えて実行します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-219">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="42b6d-220">初期のエスケープ</span><span class="sxs-lookup"><span data-stu-id="42b6d-220">Early Bailout</span></span>

 <span data-ttu-id="42b6d-221">ユーザーの取り消し要求 (キャンセル ボタンがクリックされたなど) に同時に対応できるようにしながら、1 つの操作の完了を非同期に待機するとします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-221">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user's cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="42b6d-222">このシナリオのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-222">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="42b6d-223">この実装は、エスケープを決めた直後にユーザー インターフェイスを再度使用できるようにしますが、基になる非同期操作は取り消しません。</span><span class="sxs-lookup"><span data-stu-id="42b6d-223">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span> <span data-ttu-id="42b6d-224">別の方法として、エスケープを決めたときに保留中の操作を取り消すことがありますが、取り消し要求のために途中で終了する場合など、操作が完了するまでユーザー インターフェイスを再確立しません。</span><span class="sxs-lookup"><span data-stu-id="42b6d-224">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="42b6d-225">初期のエスケープのもう 1 つの例では、次のセクションで説明する <xref:System.Threading.Tasks.Task.Delay%2A> メソッドと連動で <xref:System.Threading.Tasks.Task.WhenAny%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-225">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="42b6d-226">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="42b6d-226">Task.Delay</span></span>

 <span data-ttu-id="42b6d-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> メソッドを使用して、非同期メソッドの実行を一時停止できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-227">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method's execution.</span></span>  <span data-ttu-id="42b6d-228">これは、ポーリング ループのビルド、あらかじめ指定された期間にわたるユーザー入力処理の遅延など、さまざまな機能に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-228">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="42b6d-229"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> メソッドは、<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> との連動で使用し、待機にタイムアウトを実装する場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="42b6d-229">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="42b6d-230">大規模な非同期操作 (ASP.NET Web サービスなど) の一部であるタスクが完了するまで時間がかかる場合 (特に操作が完了しない場合) には、操作全般に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-230">If a task that's part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="42b6d-231">そのため、非同期操作を待機するときにタイムアウトできるようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="42b6d-231">For this reason, it's important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="42b6d-232">同期の <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> メソッドはタイムアウト値を受け取りますが、対応する <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> と前述の <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> メソッドは受け取りません。</span><span class="sxs-lookup"><span data-stu-id="42b6d-232">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="42b6d-233">代わりに、<xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> と <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> を併用し、タイムアウトを実装できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-233">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="42b6d-234">たとえば、UI アプリケーションで、イメージをダウンロードし、そのダウンロード中は UI を無効にするとします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-234">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="42b6d-235">ただし、ダウンロードに時間がかかりすぎる場合には、UI を再び有効にしてダウンロードを破棄します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-235">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="42b6d-236">複数のダウンロードにも同じことが当てはまります。次のように、<xref:System.Threading.Tasks.Task.WhenAll%2A> がタスクを返すためです。</span><span class="sxs-lookup"><span data-stu-id="42b6d-236">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads.Result) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="42b6d-237">タスク ベースの連結子のビルド</span><span class="sxs-lookup"><span data-stu-id="42b6d-237">Building Task-based Combinators</span></span>

 <span data-ttu-id="42b6d-238">タスクは、非同期操作を完全に表現し、操作の結合、その結果の取得などの同期機能と非同期機能を提供することができるため、大きなパターンをビルドするためのタスクを構成する有益な連結子ライブラリを構築できるようになります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-238">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span> <span data-ttu-id="42b6d-239">前のセクションで説明したとおり、.NET には、いくつか連結子が組み込まれていますが、自分独自のものをビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-239">As discussed in the previous section, .NET includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="42b6d-240">以下のセクションでは、有効な連結子メソッドと型の例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-240">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="42b6d-241">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="42b6d-241">RetryOnFault</span></span>

 <span data-ttu-id="42b6d-242">多くの状況では、前の操作が失敗した場合に再試行することが望まれます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-242">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="42b6d-243">同期コードの場合は、次の例のように `RetryOnFault` などのヘルパー メソッドをビルドしてこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-243">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="42b6d-244">非同期操作の場合も、ほとんど同じヘルパー メソッドをビルドでき、TAP を使用して非同期操作を実装し、タスクを返します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-244">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="42b6d-245">その後、次のように、この連結子を使用してアプリケーションのロジックに再試行をエンコードできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-245">You can then use this combinator to encode retries into the application's logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="42b6d-246">`RetryOnFault` 関数をさらに拡張できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-246">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="42b6d-247">たとえば、この関数は別の `Func<Task>` を受け取り、次のように再試行のタイミングを判断するために、再試行の間に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-247">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="42b6d-248">次の関数を使用して、操作を再試行する前に 1 秒待機するようにできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-248">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="42b6d-249">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="42b6d-249">NeedOnlyOne</span></span>

 <span data-ttu-id="42b6d-250">操作の待機時間を改善し、成功の確率を高めるために、冗長性を活用できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-250">Sometimes, you can take advantage of redundancy to improve an operation's latency and chances for success.</span></span>  <span data-ttu-id="42b6d-251">株価情報を提供する複数の Web サービスがあるとします。しかし、時間によって、各サービスの品質レベルと応答時間が変化します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-251">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="42b6d-252">この変動に対応するには、すべての Web サービスに要求を出し、最初の応答を取得した時点で残りの要求を取り消します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-252">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="42b6d-253">複数の操作を起動し、応答を待機し、残りの操作を取り消すというこの一般的なパターンの実装は、ヘルパー関数を実装して簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-253">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="42b6d-254">次の例の `NeedOnlyOne` 関数は、このシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-254">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="42b6d-255">この関数は次のように使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-255">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="42b6d-256">インターリーブされた操作</span><span class="sxs-lookup"><span data-stu-id="42b6d-256">Interleaved Operations</span></span>

 <span data-ttu-id="42b6d-257">多数のタスクを使用する際に、インターリーブのシナリオをサポートするために <xref:System.Threading.Tasks.Task.WhenAny%2A> メソッドを使用すると、パフォーマンスの問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-257">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with large sets of tasks.</span></span> <span data-ttu-id="42b6d-258"><xref:System.Threading.Tasks.Task.WhenAny%2A> を呼び出すたびに、継続が各タスクに登録されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-258">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="42b6d-259">タスクの数を N とすると、インターリーブ操作の有効期間に作成された O (N<sup>2</sup>) の継続になります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-259">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="42b6d-260">多数のタスクを使用する場合は、連結子 (次の例の `Interleaved`) を使用してパフォーマンスの問題に対処できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-260">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="42b6d-261">タスクが完了すると、たとえば次のように、連結子を使用してタスクの結果を処理できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-261">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="42b6d-262">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="42b6d-262">WhenAllOrFirstException</span></span>

 <span data-ttu-id="42b6d-263">特定のスキャッター/ギャザー シナリオでは、すべてのタスクの完了を待機することが考えられますが、そのうちの 1 つがエラーになった場合には、例外の発生時点で待機を停止することが望まれます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-263">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="42b6d-264">これは、次の例の `WhenAllOrFirstException` などの連結子メソッドを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-264">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="42b6d-265">タスク ベースのデータ構造のビルド</span><span class="sxs-lookup"><span data-stu-id="42b6d-265">Building Task-based Data Structures</span></span>

 <span data-ttu-id="42b6d-266">カスタム タスク ベースの連結子をビルドする機能に加えて、非同期操作の結果と、結合する必要な同期の両方を表す <xref:System.Threading.Tasks.Task> および <xref:System.Threading.Tasks.Task%601> 内にデータ構造を配置することで、非同期シナリオに使用するカスタム データ構造をビルドするための強力な型になります。</span><span class="sxs-lookup"><span data-stu-id="42b6d-266">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="42b6d-267">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="42b6d-267">AsyncCache</span></span>

 <span data-ttu-id="42b6d-268">タスクの重要な側面の 1 つに、タスクを待機する複数のコンシューマーに渡し、タスクに継続を登録し、その結果または例外を取得できることなどがあります (<xref:System.Threading.Tasks.Task%601> の場合)。</span><span class="sxs-lookup"><span data-stu-id="42b6d-268">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="42b6d-269">これで <xref:System.Threading.Tasks.Task> と <xref:System.Threading.Tasks.Task%601> が非同期キャッシュ インフラストラクチャで使用できるように調整されます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-269">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="42b6d-270">以下に、<xref:System.Threading.Tasks.Task%601> 上にビルドした小さいながらも強力な非同期キャッシュの例を示します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-270">Here's an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="42b6d-271">[AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) クラスは、コンストラクターへのデリゲートとして `TKey` を受け取る関数を受け入れ、<xref:System.Threading.Tasks.Task%601> を返します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-271">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="42b6d-272">以前にキャッシュからアクセスした値は内部ディクショナリに格納され、`AsyncCache` によって、キャッシュに同時にアクセスしてもキーごとにタスクが 1 つしか生成されないようにします。</span><span class="sxs-lookup"><span data-stu-id="42b6d-272">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="42b6d-273">たとえば、次のようにダウンロードされた Web ページのキャッシュをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-273">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="42b6d-274">Web ページのコンテンツが必要なときはいつでも、非同期メソッドでこのキャッシュを使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-274">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="42b6d-275">`AsyncCache` クラスによって、できるだけ少ない数のページが確実にダウンロードされるようになり、結果がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-275">The `AsyncCache` class ensures that you're downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="42b6d-276">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="42b6d-276">AsyncProducerConsumerCollection</span></span>

 <span data-ttu-id="42b6d-277">タスクは、非同期アクティビティを調整するためのデータ構造のビルドにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-277">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="42b6d-278">プロデューサー/コンシューマーというクラシックな並列設計パターンの 1 つについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-278">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="42b6d-279">このパターンでは、コンシューマーによって使用されるデータをプロデューサーが生成し、プロデューサーおよびコンシューマーは並列に実行できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-279">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="42b6d-280">たとえば、コンシューマーは、項目 2 を生成中のプロデューサーが以前に生成した項目 1 を処理します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-280">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="42b6d-281">プロデューサー/コンシューマー パターンでは、新しいデータについてコンシューマーに通知され、そのデータが使用可能な場合にコンシューマーが見つけられるように、プロデューサーが作成した作業を格納するデータ構造が必ず必要です。</span><span class="sxs-lookup"><span data-stu-id="42b6d-281">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="42b6d-282">プロデューサーおよびコンシューマーとして使用する非同期メソッドを有効にする、タスク上にビルドされた単純なデータ構造を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-282">Here's a simple data structure, built on top of tasks, that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="42b6d-283">このデータ構造を使用すると、次のようなコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-283">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="42b6d-284"><xref:System.Threading.Tasks.Dataflow> 名前空間には <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 型が含まれます。これは同様に使用できますが、カスタムのコレクション型をビルドする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="42b6d-284">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="42b6d-285"><xref:System.Threading.Tasks.Dataflow> 名前空間は、NuGet パッケージとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="42b6d-285">The <xref:System.Threading.Tasks.Dataflow> namespace is available as a NuGet package.</span></span> <span data-ttu-id="42b6d-286"><xref:System.Threading.Tasks.Dataflow> 名前空間が含まれるアセンブリをインストールするには、Visual Studio で自分のプロジェクトを開き、[プロジェクト] メニューの **[NuGet パッケージの管理]** を選択し、`System.Threading.Tasks.Dataflow` パッケージをオンライン検索します。</span><span class="sxs-lookup"><span data-stu-id="42b6d-286">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the `System.Threading.Tasks.Dataflow` package.</span></span>

## <a name="see-also"></a><span data-ttu-id="42b6d-287">関連項目</span><span class="sxs-lookup"><span data-stu-id="42b6d-287">See also</span></span>

- [<span data-ttu-id="42b6d-288">タスク ベースの非同期パターン (TAP)</span><span class="sxs-lookup"><span data-stu-id="42b6d-288">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="42b6d-289">タスク ベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="42b6d-289">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="42b6d-290">他の非同期パターンと型との相互運用</span><span class="sxs-lookup"><span data-stu-id="42b6d-290">Interop with Other Asynchronous Patterns and Types</span></span>](interop-with-other-asynchronous-patterns-and-types.md)
