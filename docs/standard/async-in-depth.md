---
title: 非同期の詳細
description: .NET のタスクベース非同期モデルを使用して、I/O バインドおよび CPU バインドの非同期コードを簡単に記述する方法について説明します。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.assetid: 1e38f9d9-8f84-46ee-a15f-199aec4f2e34
ms.openlocfilehash: 7fcc41c4ea5037d643402fc722e8f16f28d560ee
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823330"
---
# <a name="async-in-depth"></a><span data-ttu-id="4120b-103">非同期の詳細</span><span class="sxs-lookup"><span data-stu-id="4120b-103">Async in depth</span></span>

<span data-ttu-id="4120b-104">I/O および CPU バインドの非同期コードは、.NET のタスクベース非同期モデルを使用して簡単に記述できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-104">Writing I/O- and CPU-bound asynchronous code is straightforward using the .NET Task-based async model.</span></span> <span data-ttu-id="4120b-105">C# と Visual Basic では、このモデルは `Task` および `Task<T>` 型と、`async` および `await` キーワードによって公開されます</span><span class="sxs-lookup"><span data-stu-id="4120b-105">The model is exposed by the `Task` and `Task<T>` types and the `async` and `await` keywords in C# and Visual Basic.</span></span> <span data-ttu-id="4120b-106">(言語固有のリソースについては、「[関連項目](#see-also)」セクションを参照してください)。この記事では、.NET 非同期を使用する方法について説明し、背後で使用される非同期フレームワークを把握するための情報を示します。</span><span class="sxs-lookup"><span data-stu-id="4120b-106">(Language-specific resources are found in the [See also](#see-also) section.) This article explains how to use .NET async and provides insight into the async framework used under the covers.</span></span>

## <a name="task-and-taskt"></a><span data-ttu-id="4120b-107">Task と Task\<T></span><span class="sxs-lookup"><span data-stu-id="4120b-107">Task and Task\<T></span></span>

<span data-ttu-id="4120b-108">Task は、[Promise Model of Concurrency](https://en.wikipedia.org/wiki/Futures_and_promises) (並行性の Promise 型モデル) として知られるモデルを実装するために使用される構成体です。</span><span class="sxs-lookup"><span data-stu-id="4120b-108">Tasks are constructs used to implement what is known as the [Promise Model of Concurrency](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>  <span data-ttu-id="4120b-109">つまり、今後のある時点で作業が完了することを "約束" し、クリーン API を使用した約束の調整を可能にします。</span><span class="sxs-lookup"><span data-stu-id="4120b-109">In short, they offer you a "promise" that work will be completed at a later point, letting you coordinate with the promise with a clean API.</span></span>

- <span data-ttu-id="4120b-110">`Task` は、値を返さない 1 回の操作を表します。</span><span class="sxs-lookup"><span data-stu-id="4120b-110">`Task` represents a single operation which does not return a value.</span></span>
- <span data-ttu-id="4120b-111">`Task<T>` は、`T` 型の値を返す 1 回の操作を表します。</span><span class="sxs-lookup"><span data-stu-id="4120b-111">`Task<T>` represents a single operation which returns a value of type `T`.</span></span>

<span data-ttu-id="4120b-112">作業の抽象化は非同期に発生し、スレッド処理の抽象化では *ない* ため、タスクについて判断することが重要です。</span><span class="sxs-lookup"><span data-stu-id="4120b-112">It’s important to reason about tasks as abstractions of work happening asynchronously, and *not* an abstraction over threading.</span></span> <span data-ttu-id="4120b-113">既定では、タスクは現在のスレッドで実行され、必要に応じてオペレーティング システムに作業を委任します。</span><span class="sxs-lookup"><span data-stu-id="4120b-113">By default, tasks execute on the current thread and delegate work to the Operating System, as appropriate.</span></span> <span data-ttu-id="4120b-114">必要に応じて、`Task.Run` API を使用して、タスクを別のスレッドで実行することを明示的に要求できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-114">Optionally, tasks can be explicitly requested to run on a separate thread via the `Task.Run` API.</span></span>

<span data-ttu-id="4120b-115">タスクは、タスクの監視、待機、結果値へのアクセス (`Task<T>` の場合) のための API プロトコルを公開しています。</span><span class="sxs-lookup"><span data-stu-id="4120b-115">Tasks expose an API protocol for monitoring, waiting upon and accessing the result value (in the case of `Task<T>`) of a task.</span></span> <span data-ttu-id="4120b-116">`await` キーワードによる言語統合は、タスクを使用するための高度なレベルの抽象化を提供します。</span><span class="sxs-lookup"><span data-stu-id="4120b-116">Language integration, with the `await` keyword, provides a higher-level abstraction for using tasks.</span></span>

<span data-ttu-id="4120b-117">`await` を使用すると、アプリケーションまたはサービスで、タスク完了まで呼び出し元に制御を渡すことによって、タスクの実行中に有用な作業を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-117">Using `await` allows your application or service to perform useful work while a task is running by yielding control to its caller until the task is done.</span></span> <span data-ttu-id="4120b-118">コードは、タスク完了後に実行を続けるために、コールバックまたはイベントに依存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4120b-118">Your code does not need to rely on callbacks or events to continue execution after the task has been completed.</span></span> <span data-ttu-id="4120b-119">言語とタスクの API 統合によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-119">The language and task API integration does that for you.</span></span> <span data-ttu-id="4120b-120">`Task<T>` を使用する場合、`await` キーワードはさらに、タスク完了時に返された値を "ラップ解除" します。</span><span class="sxs-lookup"><span data-stu-id="4120b-120">If you’re using `Task<T>`, the `await` keyword will additionally "unwrap" the value returned when the Task is complete.</span></span>  <span data-ttu-id="4120b-121">この動作の詳細について次に詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="4120b-121">The details of how this works are explained further below.</span></span>

<span data-ttu-id="4120b-122">タスクと、タスクを処理するさまざまな方法については、[タスクベースの非同期パターン (TAP) に関するトピック](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4120b-122">You can learn more about tasks and the different ways to interact with them in the [Task-based Asynchronous Pattern (TAP)](./asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) topic.</span></span>

## <a name="deeper-dive-into-tasks-for-an-io-bound-operation"></a><span data-ttu-id="4120b-123">I/O バインド操作に関するタスクの詳細</span><span class="sxs-lookup"><span data-stu-id="4120b-123">Deeper Dive into Tasks for an I/O-Bound Operation</span></span>

<span data-ttu-id="4120b-124">次のセクションでは、一般的な非同期 I/O 呼び出しで実行される処理の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="4120b-124">The following section describes a 10,000 foot view of what happens with a typical async I/O call.</span></span> <span data-ttu-id="4120b-125">はじめに例を 2 つ示します。</span><span class="sxs-lookup"><span data-stu-id="4120b-125">Let's start with a couple examples.</span></span>

<span data-ttu-id="4120b-126">最初の例では、非同期メソッドを呼び出し、未完了のアクティブなタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="4120b-126">The first example calls an async method and returns an active task, likely yet to complete.</span></span>

```csharp
public Task<string> GetHtmlAsync()
{
    // Execution is synchronous here
    var client = new HttpClient();

    return client.GetStringAsync("https://www.dotnetfoundation.org");
}
```

<span data-ttu-id="4120b-127">2 番目の例では、タスクに対する処理に `async` キーワードと `await` キーワードを追加で使用しています。</span><span class="sxs-lookup"><span data-stu-id="4120b-127">The second example adds the use of the `async` and `await` keywords to operate on the task.</span></span>

```csharp
public async Task<string> GetFirstCharactersCountAsync(string url, int count)
{
    // Execution is synchronous here
    var client = new HttpClient();

    // Execution of GetFirstCharactersCountAsync() is yielded to the caller here
    // GetStringAsync returns a Task<string>, which is *awaited*
    var page = await client.GetStringAsync("https://www.dotnetfoundation.org");

    // Execution resumes when the client.GetStringAsync task completes,
    // becoming synchronous again.

    if (count > page.Length)
    {
        return page;
    }
    else
    {
        return page.Substring(0, count);
    }
}
```

<span data-ttu-id="4120b-128">`GetStringAsync()` を呼び出すと、ネイティブ ネットワーク ライブラリへの P/Invoke interop 呼び出しに到達するまで、下位レベルの .NET ライブラリ (おそらく他の非同期メソッドを呼び出す) を介して呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="4120b-128">The call to `GetStringAsync()` calls through lower-level .NET libraries (perhaps calling other async methods) until it reaches a P/Invoke interop call into a native networking library.</span></span> <span data-ttu-id="4120b-129">ネイティブ ライブラリはその後、システム API 呼び出し (Linux のソケットへの `write()` など) を実行することがあります。</span><span class="sxs-lookup"><span data-stu-id="4120b-129">The native library may subsequently call into a System API call (such as `write()` to a socket on Linux).</span></span> <span data-ttu-id="4120b-130">ネイティブまたはマネージ境界にタスク オブジェクトが作成されます。作成には [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)) が使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4120b-130">A task object will be created at the native/managed boundary, possibly using [TaskCompletionSource](xref:System.Threading.Tasks.TaskCompletionSource%601.SetResult(%600)).</span></span> <span data-ttu-id="4120b-131">タスク オブジェクトは上位レイヤーに渡され、操作が実行される場合もあれば直接返される場合もありますが、最終的に最初の呼び出し元に戻されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-131">The task object will be passed up through the layers, possibly operated on or directly returned, eventually returned to the initial caller.</span></span>

<span data-ttu-id="4120b-132">上記の 2 番目の例で、`Task<T>` オブジェクトが `GetStringAsync` から返されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-132">In the second example above, a `Task<T>` object will be returned from `GetStringAsync`.</span></span> <span data-ttu-id="4120b-133">`await` キーワードを使用すると、メソッドは新しく作成したタスク オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="4120b-133">The use of the `await` keyword causes the method to return a newly created task object.</span></span> <span data-ttu-id="4120b-134">`GetFirstCharactersCountAsync` メソッドのこの場所から呼び出し元に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="4120b-134">Control returns to the caller from this location in the `GetFirstCharactersCountAsync` method.</span></span> <span data-ttu-id="4120b-135">[Task&lt;T&gt;](xref:System.Threading.Tasks.Task%601) オブジェクトのメソッドとプロパティを使用すると、呼び出し元はタスクの進行状況を監視できます。タスクは、GetFirstCharactersCountAsync の残りのコードが実行されれば完了します。</span><span class="sxs-lookup"><span data-stu-id="4120b-135">The methods and properties of the [Task&lt;T&gt;](xref:System.Threading.Tasks.Task%601) object enable callers to monitor the progress of the task, which will complete when the remaining code in GetFirstCharactersCountAsync has executed.</span></span>

<span data-ttu-id="4120b-136">システム API 呼び出しの後、要求はカーネル領域に入り、OS のネットワーク サブシステム (Linux カーネルの `/net` など) に移ります。</span><span class="sxs-lookup"><span data-stu-id="4120b-136">After the System API call, the request is now in kernel space, making its way to the networking subsystem of the OS (such as `/net` in the Linux Kernel).</span></span>  <span data-ttu-id="4120b-137">ここで、OS はネットワーク要求を *非同期的に* 処理します。</span><span class="sxs-lookup"><span data-stu-id="4120b-137">Here the OS will handle the networking request *asynchronously*.</span></span>  <span data-ttu-id="4120b-138">詳細は使用する OS によって異なる場合がありますが (デバイス ドライバーの呼び出しが、ランタイムに返送されるシグナルとしてスケジュールされている場合や、デバイス ドライバー呼び出しが行われた *後* にシグナルが返送される場合があります)、最終的にはネットワーク要求が進行中であることがランタイムに通知されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-138">Details may be different depending on the OS used (the device driver call may be scheduled as a signal sent back to the runtime, or a device driver call may be made and *then* a signal sent back), but eventually the runtime will be informed that the networking request is in progress.</span></span>  <span data-ttu-id="4120b-139">この時点で、デバイス ドライバーに関する処理はスケジュール済み、進行中、または既に完了済み (要求が既に "接続" されていない状態) のいずれかですが、すべてが非同期に発生するため、デバイス ドライバーはすぐに別の処理を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-139">At this time, the work for the device driver will either be scheduled, in-progress, or already finished (the request is already out "over the wire") - but because this is all happening asynchronously, the device driver is able to immediately handle something else!</span></span>

<span data-ttu-id="4120b-140">たとえば、Windows で OS スレッドからネットワーク デバイス ドライバーに呼び出しを行い、操作を表す割り込み要求パケット (IRP) を通じてネットワーク操作の実行を依頼します。</span><span class="sxs-lookup"><span data-stu-id="4120b-140">For example, in Windows an OS thread makes a call to the network device driver and asks it to perform the networking operation via an Interrupt Request Packet (IRP) which represents the operation.</span></span>  <span data-ttu-id="4120b-141">デバイス ドライバーは IRP を受信し、ネットワークへの呼び出しを行い、IRP を "保留中" とマークして OS に戻ります。</span><span class="sxs-lookup"><span data-stu-id="4120b-141">The device driver receives the IRP, makes the call to the network, marks the IRP as "pending", and returns back to the OS.</span></span>  <span data-ttu-id="4120b-142">OS スレッドは IRP が "保留中" であることがわかっているため、このジョブに対してそれ以上行う処理はなく、"戻る" ことによって他の作業を実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4120b-142">Because the OS thread now knows that the IRP is "pending", it doesn't have any more work to do for this job and "returns" back so that it can be used to perform other work.</span></span>

<span data-ttu-id="4120b-143">要求が満たされ、データがデバイス ドライバーに戻ると、新しいデータの受信が割り込みを介して CPU に通知されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-143">When the request is fulfilled and data comes back through the device driver, it notifies the CPU of new data received via an interrupt.</span></span>  <span data-ttu-id="4120b-144">この割り込みが処理される方法は OS によって異なりますが、最終的にデータは OS に渡されてシステム interop 呼び出しに到達します (たとえば、Linux では割り込みハンドラーが IRQ の残り半分をスケジュールし、データを OS に非同期に渡します)。</span><span class="sxs-lookup"><span data-stu-id="4120b-144">How this interrupt gets handled will vary depending on the OS, but eventually the data will be passed through the OS until it reaches a system interop call (for example, in Linux an interrupt handler will schedule the bottom half of the IRQ to pass the data up through the OS asynchronously).</span></span>  <span data-ttu-id="4120b-145">これも *非同期に* 行われることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="4120b-145">Note that this *also* happens asynchronously!</span></span>  <span data-ttu-id="4120b-146">結果は、次の使用可能なスレッドが非同期メソッドを実行して完了したタスクの結果を "ラップ解除" できるようになるまで、キューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="4120b-146">The result is queued up until the next available thread is able to execute the async method and "unwrap" the result of the completed task.</span></span>

<span data-ttu-id="4120b-147">このプロセス全体を通じて、重要なことは、**タスクを実行する専用のスレッドは存在しない** ということです。</span><span class="sxs-lookup"><span data-stu-id="4120b-147">Throughout this entire process, a key takeaway is that **no thread is dedicated to running the task**.</span></span>  <span data-ttu-id="4120b-148">作業は何らかのコンテキストで実行されますが (つまり、OS はデバイス ドライバーにデータを渡し、割り込みに応答する必要があります)、要求からデータが戻るのを *待機* する専用のスレッドは存在しません。</span><span class="sxs-lookup"><span data-stu-id="4120b-148">Although work is executed in some context (that is, the OS does have to pass data to a device driver and respond to an interrupt), there is no thread dedicated to *waiting* for data from the request to come back.</span></span>  <span data-ttu-id="4120b-149">そのため、システムは I/O 呼び出しの完了を待機するのではなく、より大量の作業を処理できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-149">This allows the system to handle a much larger volume of work rather than waiting for some I/O call to finish.</span></span>

<span data-ttu-id="4120b-150">実測時間で考えると、上記の処理には実行する作業が多いように見えるかもしれませんが、実際の I/O 作業の実行にかかる時間に比較すればわずかです。</span><span class="sxs-lookup"><span data-stu-id="4120b-150">Although the above may seem like a lot of work to be done, when measured in terms of wall clock time, it’s miniscule compared to the time it takes to do the actual I/O work.</span></span> <span data-ttu-id="4120b-151">まったくの目安ですが、このような呼び出しの潜在的なタイムラインは次のようなります。</span><span class="sxs-lookup"><span data-stu-id="4120b-151">Although not at all precise, a potential timeline for such a call would look like this:</span></span>

<span data-ttu-id="4120b-152">0-1————————————————————————————————————————————————–2-3</span><span class="sxs-lookup"><span data-stu-id="4120b-152">0-1————————————————————————————————————————————————–2-3</span></span>

- <span data-ttu-id="4120b-153">`0` の時点から `1` の時点までは、非同期メソッドが呼び出し元に制御を渡すまでにかかった時間です。</span><span class="sxs-lookup"><span data-stu-id="4120b-153">Time spent from points `0` to `1` is everything up until an async method yields control to its caller.</span></span>
- <span data-ttu-id="4120b-154">`1` の時点から `2` の時点までは、CPU に負荷をかけずに I/O に費やされた時間です。</span><span class="sxs-lookup"><span data-stu-id="4120b-154">Time spent from points `1` to `2` is the time spent on I/O, with no CPU cost.</span></span>
- <span data-ttu-id="4120b-155">最後に、`2` の時点から `3` の時点までは、非同期メソッドに制御 (および場合によっては値) を戻すまでの時間です。この時点でそのメソッドは再度実行されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-155">Finally, time spent from points `2` to `3` is passing control back (and potentially a value) to the async method, at which point it is executing again.</span></span>

### <a name="what-does-this-mean-for-a-server-scenario"></a><span data-ttu-id="4120b-156">サーバー側のシナリオ</span><span class="sxs-lookup"><span data-stu-id="4120b-156">What does this mean for a server scenario?</span></span>

<span data-ttu-id="4120b-157">このモデルは、標準的なサーバー シナリオのワークロードで問題なく動作します。</span><span class="sxs-lookup"><span data-stu-id="4120b-157">This model works well with a typical server scenario workload.</span></span>  <span data-ttu-id="4120b-158">未完了のタスクでのブロッキング専用のスレッドがないため、サーバー スレッドプールでより大量の Web 要求の処理ができます。</span><span class="sxs-lookup"><span data-stu-id="4120b-158">Because there are no threads dedicated to blocking on unfinished tasks, the server threadpool can service a much higher volume of web requests.</span></span>

<span data-ttu-id="4120b-159">2 種類のサーバーについて考えます。非同期コードを実行しているサーバーと、実行していないサーバーです。</span><span class="sxs-lookup"><span data-stu-id="4120b-159">Consider two servers: one that runs async code, and one that does not.</span></span>  <span data-ttu-id="4120b-160">この例では、各サーバーには、サービス要求に使用できるスレッドが 5 つだけあります。</span><span class="sxs-lookup"><span data-stu-id="4120b-160">For the purpose of this example, each server only has 5 threads available to service requests.</span></span>  <span data-ttu-id="4120b-161">これは非現実的な少ない数であり、デモの目的に限って使用していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4120b-161">Note that these numbers are imaginarily small and serve only in a demonstrative context.</span></span>

<span data-ttu-id="4120b-162">どちらのサーバーも 6 件の同時要求を受信したとします。</span><span class="sxs-lookup"><span data-stu-id="4120b-162">Assume both servers receive 6 concurrent requests.</span></span> <span data-ttu-id="4120b-163">各要求で I/O 操作を 1 回実行します。</span><span class="sxs-lookup"><span data-stu-id="4120b-163">Each request performs an I/O operation.</span></span>  <span data-ttu-id="4120b-164">非同期コードを *使用しない* サーバーは、5 つのスレッドのいずれかが I/O バインドの作業を完了して応答を書き込むまで、6 番目の要求をキューに入れておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4120b-164">The server *without* async code has to queue up the 6th request until one of the 5 threads have finished the I/O-bound work and written a response.</span></span> <span data-ttu-id="4120b-165">サーバーに 20 番目の要求が到着すると、キューが長くなりすぎるため、サーバー速度が低下し始める可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4120b-165">At the point that the 20th request comes in, the server might start to slow down, because the queue is getting too long.</span></span>

<span data-ttu-id="4120b-166">非同期コードを *実行している* サーバーでも、6 番目の要求はキューに入れられますが、`async` と `await` を使用しているため、各スレッドは I/O バインドの作業が完了した時点ではなく、開始した時点で解放されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-166">The server *with* async code running on it still queues up the 6th request, but because it uses `async` and `await`, each of its threads are freed up when the I/O-bound work starts, rather than when it finishes.</span></span>  <span data-ttu-id="4120b-167">20 番目の要求が到着する時点までに受信要求のキューは大幅に短くなり (キューに何らかの要求が格納されている場合)、サーバーの速度低下は発生しません。</span><span class="sxs-lookup"><span data-stu-id="4120b-167">By the time the 20th request comes in, the queue for incoming requests will be far smaller (if it has anything in it at all), and the server won't slow down.</span></span>

<span data-ttu-id="4120b-168">これは架空の例ですが、実際の動作にとても似ています。</span><span class="sxs-lookup"><span data-stu-id="4120b-168">Although this is a contrived example, it works in a very similar fashion in the real world.</span></span>  <span data-ttu-id="4120b-169">実際には、`async` と `await` を使用すると、受信する要求ごとにスレッドを専用にした場合に比べ、1 桁以上多い数の要求をサーバーで処理できると期待できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-169">In fact, you can expect a server to be able to handle an order of magnitude more requests using `async` and `await` than if it were dedicating a thread for each request it receives.</span></span>

### <a name="what-does-this-mean-for-client-scenario"></a><span data-ttu-id="4120b-170">クライアント側のシナリオ</span><span class="sxs-lookup"><span data-stu-id="4120b-170">What does this mean for client scenario?</span></span>

<span data-ttu-id="4120b-171">クライアント アプリに `async` と `await` を使用する最大のメリットは、応答性の向上です。</span><span class="sxs-lookup"><span data-stu-id="4120b-171">The biggest gain for using `async` and `await` for a client app is an increase in responsiveness.</span></span>  <span data-ttu-id="4120b-172">スレッドを手動で作成することによって、アプリの応答性を高めることができます。スレッドを作成することは、単に `async` と `await` を使用する場合に比べ、相対的に負荷の高い操作です。</span><span class="sxs-lookup"><span data-stu-id="4120b-172">Although you can make an app responsive by spawning threads manually, the act of spawning a thread is an expensive operation relative to just using `async` and `await`.</span></span>  <span data-ttu-id="4120b-173">モバイル ゲームなどの場合は特に、I/O に関して UI スレッドへの影響をできるだけ少なくすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="4120b-173">Especially for something like a mobile game, impacting the UI thread as little as possible where I/O is concerned is crucial.</span></span>

<span data-ttu-id="4120b-174">さらに重要なことに、I/O バインドの作業に費やされる CPU 時間が実質的にゼロであるため、ほとんど有用性のない作業の実行に CPU スレッド全体を独占的に使用することは、リソースの使用方法として不適切です。</span><span class="sxs-lookup"><span data-stu-id="4120b-174">More importantly, because I/O-bound work spends virtually no time on the CPU, dedicating an entire CPU thread to perform barely any useful work would be a poor use of resources.</span></span>

<span data-ttu-id="4120b-175">さらに、UI スレッドへの作業の処理依頼 (UI の更新など) は、`async` メソッドを使用すればとても簡単で、余分な作業 (スレッドセーフ デリゲートの呼び出しなど) は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4120b-175">Additionally, dispatching work to the UI thread (such as updating a UI) is very simple with `async` methods, and does not require extra work (such as calling a thread-safe delegate).</span></span>

## <a name="deeper-dive-into-task-and-taskt-for-a-cpu-bound-operation"></a><span data-ttu-id="4120b-176">CPU バインド操作の Task と Task\<T> の詳細</span><span class="sxs-lookup"><span data-stu-id="4120b-176">Deeper Dive into Task and Task\<T> for a CPU-Bound Operation</span></span>

<span data-ttu-id="4120b-177">CPU バインドの `async` コードは、I/O バインドの `async` コードとは少し異なります。</span><span class="sxs-lookup"><span data-stu-id="4120b-177">CPU-bound `async` code is a bit different than I/O-bound `async` code.</span></span>  <span data-ttu-id="4120b-178">作業は CPU で実行されるため、スレッドを計算専用にすることを避ける方法はありません。</span><span class="sxs-lookup"><span data-stu-id="4120b-178">Because the work is done on the CPU, there's no way to get around dedicating a thread to the computation.</span></span>  <span data-ttu-id="4120b-179">`async` と `await` を使用すると、バックグラウンドのスレッドをクリーンな方法で使用でき、非同期メソッドの呼び出し元の応答性を維持できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-179">The use of `async` and `await` provides you with a clean way to interact with a background thread and keep the caller of the async method responsive.</span></span>  <span data-ttu-id="4120b-180">これにより共有データに対する保護は提供されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4120b-180">Note that this does not provide any protection for shared data.</span></span>  <span data-ttu-id="4120b-181">共有データを使用している場合は、適切な同期戦略を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4120b-181">If you are using shared data, you will still need to apply an appropriate synchronization strategy.</span></span>

<span data-ttu-id="4120b-182">CPU バインドの非同期呼び出しの概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4120b-182">Here's a 10,000 foot view of a CPU-bound async call:</span></span>

```csharp
public async Task<int> CalculateResult(InputData data)
{
    // This queues up the work on the threadpool.
    var expensiveResultTask = Task.Run(() => DoExpensiveCalculation(data));

    // Note that at this point, you can do some other work concurrently,
    // as CalculateResult() is still executing!

    // Execution of CalculateResult is yielded here!
    var result = await expensiveResultTask;

    return result;
}
```

<span data-ttu-id="4120b-183">`CalculateResult()` が、呼び出されたスレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-183">`CalculateResult()` executes on the thread it was called on.</span></span>  <span data-ttu-id="4120b-184">`Task.Run` の呼び出し時に、負荷の高い CPU バインド操作 `DoExpensiveCalculation()` をスレッドプールでキューに入れ、`Task<int>` ハンドルを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="4120b-184">When it calls `Task.Run`, it queues the expensive CPU-bound operation, `DoExpensiveCalculation()`, on the thread pool and receives a `Task<int>` handle.</span></span>  <span data-ttu-id="4120b-185">`DoExpensiveCalculation()` は最終的に次の使用可能なスレッドで (通常は別の CPU コアで) 同時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-185">`DoExpensiveCalculation()` is eventually run concurrently on the next available thread, likely on another CPU core.</span></span>  <span data-ttu-id="4120b-186">`CalculateResult()` を呼び出したスレッドがまだ実行中であるために、`DoExpensiveCalculation()` が別のスレッドでビジー状態のときに、同時処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4120b-186">It's possible to do concurrent work while `DoExpensiveCalculation()` is busy on another thread, because the thread which called `CalculateResult()` is still executing.</span></span>

<span data-ttu-id="4120b-187">`await` が検出されると、`CalculateResult()` の実行は呼び出し元に任され、`DoExpensiveCalculation()` が結果を生成している間に、現在のスレッドで他の作業を実行できます。</span><span class="sxs-lookup"><span data-stu-id="4120b-187">Once `await` is encountered, the execution of `CalculateResult()` is yielded to its caller, allowing other work to be done with the current thread while `DoExpensiveCalculation()` is churning out a result.</span></span>  <span data-ttu-id="4120b-188">その作業が完了すると、結果はキューに入れられ、メイン スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-188">Once it has finished, the result is queued up to run on the main thread.</span></span>  <span data-ttu-id="4120b-189">最終的に、メイン スレッドが `CalculateResult()` の実行に戻り、その時点で `DoExpensiveCalculation()` の結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="4120b-189">Eventually, the main thread will return to executing `CalculateResult()`, at which point it will have the result of `DoExpensiveCalculation()`.</span></span>

### <a name="why-does-async-help-here"></a><span data-ttu-id="4120b-190">async が役に立つ理由</span><span class="sxs-lookup"><span data-stu-id="4120b-190">Why does async help here?</span></span>

<span data-ttu-id="4120b-191">`async` と `await` は、応答性を必要とする場合に CPU バインドの作業を管理する際のベスト プラクティスです。</span><span class="sxs-lookup"><span data-stu-id="4120b-191">`async` and `await` are the best practice for managing CPU-bound work when you need responsiveness.</span></span> <span data-ttu-id="4120b-192">CPU バインドの作業で async を使用するには、複数のパターンがあります。</span><span class="sxs-lookup"><span data-stu-id="4120b-192">There are multiple patterns for using async with CPU-bound work.</span></span> <span data-ttu-id="4120b-193">async を使用すると小さいながらも負荷がかかるため、厳密なループ処理にはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="4120b-193">It's important to note that there is a small cost to using async and it's not recommended for tight loops.</span></span>  <span data-ttu-id="4120b-194">この新しい機能を利用してコードを記述するかどうかは、ユーザーの判断に任されます。</span><span class="sxs-lookup"><span data-stu-id="4120b-194">It's up to you to determine how you write your code around this new capability.</span></span>

## <a name="see-also"></a><span data-ttu-id="4120b-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="4120b-195">See also</span></span>

- [<span data-ttu-id="4120b-196">C# の非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="4120b-196">Asynchronous programming in C#</span></span>](../csharp/async.md)
- [<span data-ttu-id="4120b-197">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="4120b-197">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="4120b-198">F# の非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="4120b-198">Async Programming in F#</span></span>](../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="4120b-199">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4120b-199">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../visual-basic/programming-guide/concepts/async/index.md)
