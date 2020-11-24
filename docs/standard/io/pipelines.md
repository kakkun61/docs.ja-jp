---
title: I/O パイプライン - .NET
description: .NET で I/O パイプラインを効率的に使用し、コードの問題を回避する方法について学習します。
ms.date: 08/27/2020
helpviewer_keywords:
- Pipelines
- Pipelines I/O
- I/O [.NET], Pipelines
author: rick-anderson
ms.author: riande
ms.openlocfilehash: 508ae0e2b854f81ee639a63063a8f6d73ae84863
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830637"
---
# <a name="systemiopipelines-in-net"></a><span data-ttu-id="a787e-103">.NET の System.IO.Pipelines</span><span class="sxs-lookup"><span data-stu-id="a787e-103">System.IO.Pipelines in .NET</span></span>

<span data-ttu-id="a787e-104"><xref:System.IO.Pipelines> は、.NET でハイ パフォーマンスの I/O をより簡単に行えるように設計された新しいライブラリです。</span><span class="sxs-lookup"><span data-stu-id="a787e-104"><xref:System.IO.Pipelines> is a new library that is designed to make it easier to do high-performance I/O in .NET.</span></span> <span data-ttu-id="a787e-105">これは、すべての .NET 実装で動作する .NET Standard を対象とするライブラリです。</span><span class="sxs-lookup"><span data-stu-id="a787e-105">It's a library targeting .NET Standard that works on all .NET implementations.</span></span>

<a name="solve"></a>

## <a name="what-problem-does-systemiopipelines-solve"></a><span data-ttu-id="a787e-106">System.IO.Pipelines によって解決される問題</span><span class="sxs-lookup"><span data-stu-id="a787e-106">What problem does System.IO.Pipelines solve</span></span>

<!-- corner case doesn't MT (machine translate)   -->
<span data-ttu-id="a787e-107">ストリーミング データを解析するアプリは、多くの特殊な通常とは異なるコード フローを持つ定型コードで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-107">Apps that parse streaming data are composed of boilerplate code having many specialized and unusual code flows.</span></span> <span data-ttu-id="a787e-108">定型および特殊なケースのコードは複雑で、保守が困難です。</span><span class="sxs-lookup"><span data-stu-id="a787e-108">The boilerplate and special case code is complex and difficult to maintain.</span></span>

<span data-ttu-id="a787e-109">`System.IO.Pipelines` は、以下のようになるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a787e-109">`System.IO.Pipelines` was architected to:</span></span>

* <span data-ttu-id="a787e-110">ハイ パフォーマンスのストリーミング データ解析を実現する。</span><span class="sxs-lookup"><span data-stu-id="a787e-110">Have high performance parsing streaming data.</span></span>
* <span data-ttu-id="a787e-111">コードの複雑さを軽減する。</span><span class="sxs-lookup"><span data-stu-id="a787e-111">Reduce code complexity.</span></span>

<span data-ttu-id="a787e-112">次のコードは、クライアントから (`'\n'` で区切られた) 行区切りメッセージを受信する TCP サーバーでは一般的なものです。</span><span class="sxs-lookup"><span data-stu-id="a787e-112">The following code is typical for a TCP server that receives line-delimited messages (delimited by `'\n'`) from a client:</span></span>

```csharp
async Task ProcessLinesAsync(NetworkStream stream)
{
    var buffer = new byte[1024];
    await stream.ReadAsync(buffer, 0, buffer.Length);

    // Process a single line from the buffer
    ProcessLine(buffer);
}
```

<span data-ttu-id="a787e-113">上記のコードには、以下のようないくつかの問題があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-113">The preceding code has several problems:</span></span>

* <span data-ttu-id="a787e-114">メッセージ全体 (行の終わり) が、`ReadAsync` への 1 回の呼び出しで受信されない場合がある。</span><span class="sxs-lookup"><span data-stu-id="a787e-114">The entire message (end of line) might not be received in a single call to `ReadAsync`.</span></span>
* <span data-ttu-id="a787e-115">`stream.ReadAsync` の結果が無視される。</span><span class="sxs-lookup"><span data-stu-id="a787e-115">It's ignoring the result of `stream.ReadAsync`.</span></span> <span data-ttu-id="a787e-116">`stream.ReadAsync` で、読み取られたデータの量が返される。</span><span class="sxs-lookup"><span data-stu-id="a787e-116">`stream.ReadAsync` returns how much data was read.</span></span>
* <span data-ttu-id="a787e-117">複数の行が 1 回の `ReadAsync` 呼び出しで読み取られるケースが処理されない。</span><span class="sxs-lookup"><span data-stu-id="a787e-117">It doesn't handle the case where multiple lines are read in a single `ReadAsync` call.</span></span>
* <span data-ttu-id="a787e-118">読み取りごとに `byte` 配列が割り当てられる。</span><span class="sxs-lookup"><span data-stu-id="a787e-118">It allocates a `byte` array with each read.</span></span>

<span data-ttu-id="a787e-119">上記の問題を解決するには、次の変更が必要です。</span><span class="sxs-lookup"><span data-stu-id="a787e-119">To fix the preceding problems, the following changes are required:</span></span>

* <span data-ttu-id="a787e-120">改行が検出されるまで、受信データをバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="a787e-120">Buffer the incoming data until a new line is found.</span></span>
* <span data-ttu-id="a787e-121">バッファーで返されたすべての行を解析します。</span><span class="sxs-lookup"><span data-stu-id="a787e-121">Parse all the lines returned in the buffer.</span></span>
* <span data-ttu-id="a787e-122">行が 1 KB (1024 バイト) より大きい可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-122">It's possible that the line is bigger than 1 KB (1024 bytes).</span></span> <span data-ttu-id="a787e-123">コードでは、バッファー内の完全な行に収まるように、区切り記号が見つかるまで入力バッファーのサイズを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-123">The code needs to resize the input buffer until the delimiter is found in order to fit the complete line inside the buffer.</span></span>

  * <span data-ttu-id="a787e-124">バッファーのサイズが変更された場合、入力により長い行が表示されると、より多くのバッファー コピーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-124">If the buffer is resized, more buffer copies are made as longer lines appear in the input.</span></span>
  * <span data-ttu-id="a787e-125">無駄な領域を減らすには、行の読み取りに使用されるバッファーを小さくします。</span><span class="sxs-lookup"><span data-stu-id="a787e-125">To reduce wasted space, compact the buffer used for reading lines.</span></span>

* <span data-ttu-id="a787e-126">メモリが繰り返し割り当てられないようにするために、バッファー プーリングの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="a787e-126">Consider using buffer pooling to avoid allocating memory repeatedly.</span></span>
* <span data-ttu-id="a787e-127">次のコードでは、これらの問題の一部に対処します。</span><span class="sxs-lookup"><span data-stu-id="a787e-127">The following code addresses some of these problems:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ProcessLinesAsync.cs" id="snippet":::

<span data-ttu-id="a787e-128">上記のコードは複雑で、特定されたすべての問題には対処していません。</span><span class="sxs-lookup"><span data-stu-id="a787e-128">The previous code is complex and doesn't address all the problems identified.</span></span> <span data-ttu-id="a787e-129">ハイ パフォーマンス ネットワークは、通常、パフォーマンスを最大化するために非常に複雑なコードを記述することを意味します。</span><span class="sxs-lookup"><span data-stu-id="a787e-129">High-performance networking usually means writing very complex code to maximize performance.</span></span> <span data-ttu-id="a787e-130">`System.IO.Pipelines` は、この種のコードをより簡単に記述できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a787e-130">`System.IO.Pipelines` was designed to make writing this type of code easier.</span></span>

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="pipe"></a><span data-ttu-id="a787e-131">パイプ</span><span class="sxs-lookup"><span data-stu-id="a787e-131">Pipe</span></span>

<span data-ttu-id="a787e-132"><xref:System.IO.Pipelines.Pipe> クラスを使用して、`PipeWriter/PipeReader` ペアを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-132">The <xref:System.IO.Pipelines.Pipe> class can be used to create a `PipeWriter/PipeReader` pair.</span></span> <span data-ttu-id="a787e-133">`PipeWriter` に書き込まれたすべてのデータは、`PipeReader` で利用できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-133">All data written into the `PipeWriter` is available in the `PipeReader`:</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet2":::

<a name="pbu"></a>

### <a name="pipe-basic-usage"></a><span data-ttu-id="a787e-134">パイプの基本的な使用方法</span><span class="sxs-lookup"><span data-stu-id="a787e-134">Pipe basic usage</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Pipe.cs" id="snippet":::

<span data-ttu-id="a787e-135">次の 2 つのループがあります。</span><span class="sxs-lookup"><span data-stu-id="a787e-135">There are two loops:</span></span>

* <span data-ttu-id="a787e-136">`FillPipeAsync` では `Socket` から読み取り、`PipeWriter` に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a787e-136">`FillPipeAsync` reads from the `Socket` and writes to the `PipeWriter`.</span></span>
* <span data-ttu-id="a787e-137">`ReadPipeAsync` では `PipeReader` から読み取り、受信行を解析します。</span><span class="sxs-lookup"><span data-stu-id="a787e-137">`ReadPipeAsync` reads from the `PipeReader` and parses incoming lines.</span></span>

<span data-ttu-id="a787e-138">明示的なバッファーは割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="a787e-138">There are no explicit buffers allocated.</span></span> <span data-ttu-id="a787e-139">すべてのバッファー管理は、`PipeReader` と `PipeWriter` の実装に委任されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-139">All buffer management is delegated to the `PipeReader` and `PipeWriter` implementations.</span></span> <span data-ttu-id="a787e-140">バッファー管理を委任することで、ビジネス ロジックのみに焦点を当てるコードがより簡単に消費されるようになります。</span><span class="sxs-lookup"><span data-stu-id="a787e-140">Delegating buffer management makes it easier for consuming code to focus solely on the business logic.</span></span>

<span data-ttu-id="a787e-141">最初のループでは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a787e-141">In the first loop:</span></span>

* <span data-ttu-id="a787e-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> は、基になるライターからメモリを取得するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-142"><xref:System.IO.Pipelines.PipeWriter.GetMemory(System.Int32)?displayProperty=nameWithType> is called to get memory from the underlying writer.</span></span>
* <span data-ttu-id="a787e-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> は、バッファーに書き込まれたデータの量を `PipeWriter` に示すために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-143"><xref:System.IO.Pipelines.PipeWriter.Advance(System.Int32)?displayProperty=nameWithType> is called to tell the `PipeWriter` how much data was written to the buffer.</span></span>
* <span data-ttu-id="a787e-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> は、データを `PipeReader` で使用できるようにするために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-144"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType> is called to make the data available to the `PipeReader`.</span></span>

<span data-ttu-id="a787e-145">2 番目のループでは、`PipeWriter` によって書き込まれたバッファーが `PipeReader` で消費されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-145">In the second loop, the `PipeReader` consumes the buffers written by `PipeWriter`.</span></span> <span data-ttu-id="a787e-146">バッファーはソケットから取得されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-146">The buffers come from the socket.</span></span> <span data-ttu-id="a787e-147">`PipeReader.ReadAsync` の呼び出しでは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a787e-147">The call to `PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="a787e-148">次の 2 つの重要な情報を含む、<xref:System.IO.Pipelines.ReadResult> を返します。</span><span class="sxs-lookup"><span data-stu-id="a787e-148">Returns a <xref:System.IO.Pipelines.ReadResult> that contains two important pieces of information:</span></span>

  * <span data-ttu-id="a787e-149">`ReadOnlySequence<byte>` の形式で読み取られたデータ。</span><span class="sxs-lookup"><span data-stu-id="a787e-149">The data that was read in the form of `ReadOnlySequence<byte>`.</span></span>
  * <span data-ttu-id="a787e-150">データの終わり (EOF) に到達したかどうかを示すブール値 `IsCompleted`。</span><span class="sxs-lookup"><span data-stu-id="a787e-150">A boolean `IsCompleted` that indicates if the end of data (EOF) has been reached.</span></span>

<span data-ttu-id="a787e-151">行の終わり (EOL) の区切り記号が検出され、行が解析された後は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a787e-151">After finding the end of line (EOL) delimiter and parsing the line:</span></span>

* <span data-ttu-id="a787e-152">ロジックでバッファーが処理され、既に処理されているものがスキップされます。</span><span class="sxs-lookup"><span data-stu-id="a787e-152">The logic processes the buffer to skip what's already processed.</span></span>
* <span data-ttu-id="a787e-153">`PipeReader.AdvanceTo` は、どのくらいの量のデータが使用され、検査されたかを `PipeReader` に示すために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-153">`PipeReader.AdvanceTo` is called to tell the `PipeReader` how much data has been consumed and examined.</span></span>

<span data-ttu-id="a787e-154">リーダーとライターのループは、`Complete` を呼び出すことによって終了します。</span><span class="sxs-lookup"><span data-stu-id="a787e-154">The reader and writer loops end by calling `Complete`.</span></span> <span data-ttu-id="a787e-155">`Complete` は、基になるパイプで割り当てられたメモリを解放できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a787e-155">`Complete` lets the underlying Pipe release the memory it allocated.</span></span>

### <a name="backpressure-and-flow-control"></a><span data-ttu-id="a787e-156">バックプレッシャとフロー制御</span><span class="sxs-lookup"><span data-stu-id="a787e-156">Backpressure and flow control</span></span>

<span data-ttu-id="a787e-157">読み取りと解析を連動させるのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="a787e-157">Ideally, reading and parsing work together:</span></span>

* <span data-ttu-id="a787e-158">書き込みスレッドでは、ネットワークからのデータを消費し、それをバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="a787e-158">The writing thread consumes data from the network and puts it in buffers.</span></span>
* <span data-ttu-id="a787e-159">解析スレッドでは、適切なデータ構造の構築を担当します。</span><span class="sxs-lookup"><span data-stu-id="a787e-159">The parsing thread is responsible for constructing the appropriate data structures.</span></span>

<span data-ttu-id="a787e-160">通常、解析には、ネットワークからデータのブロックをコピーするだけの場合より、時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="a787e-160">Typically, parsing takes more time than just copying blocks of data from the network:</span></span>

* <span data-ttu-id="a787e-161">読み取りスレッドは解析スレッドより前になります。</span><span class="sxs-lookup"><span data-stu-id="a787e-161">The reading thread gets ahead of the parsing thread.</span></span>
* <span data-ttu-id="a787e-162">読み取りスレッドの速度を落とすか、解析スレッド用のデータを格納するためにより多くのメモリを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-162">The reading thread has to either slow down or allocate more memory to store the data for the parsing thread.</span></span>

<span data-ttu-id="a787e-163">最適なパフォーマンスが得られるように、頻繁な一時停止間のバランスが保たれ、より多くのメモリが割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="a787e-163">For optimal performance, there's a balance between frequent pauses and allocating more memory.</span></span>

<span data-ttu-id="a787e-164">この問題を解決するために、`Pipe` には、データのフローを制御するための次の 2 つの設定があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-164">To solve the preceding problem, the `Pipe` has two settings to control the flow of data:</span></span>

* <span data-ttu-id="a787e-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>:<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> の呼び出しが一時停止する前に、バッファーに格納する必要があるデータ量を判別します。</span><span class="sxs-lookup"><span data-stu-id="a787e-165"><xref:System.IO.Pipelines.PipeOptions.PauseWriterThreshold>: Determines how much data should be buffered before calls to <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> pause.</span></span>
* <span data-ttu-id="a787e-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>:`PipeWriter.FlushAsync` の呼び出しが再開される前に、リーダーが監視する必要があるデータの量を判別します。</span><span class="sxs-lookup"><span data-stu-id="a787e-166"><xref:System.IO.Pipelines.PipeOptions.ResumeWriterThreshold>: Determines how much data the reader has to observe before calls to `PipeWriter.FlushAsync` resume.</span></span>

![ResumeWriterThreshold と PauseWriterThreshold を含む図](media/pipelines/resume-pause.png)

<span data-ttu-id="a787e-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="a787e-168"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="a787e-169">`Pipe` のデータ量が `PauseWriterThreshold` を超えたときに、不完全な `ValueTask<FlushResult>` を返します。</span><span class="sxs-lookup"><span data-stu-id="a787e-169">Returns an incomplete `ValueTask<FlushResult>` when the amount of data in the `Pipe` crosses `PauseWriterThreshold`.</span></span>
* <span data-ttu-id="a787e-170">`ResumeWriterThreshold` より低くなったときに、`ValueTask<FlushResult>` を完了します。</span><span class="sxs-lookup"><span data-stu-id="a787e-170">Completes `ValueTask<FlushResult>` when it becomes lower than `ResumeWriterThreshold`.</span></span>

<span data-ttu-id="a787e-171">2 つの値は、1 つの値が使用された場合に発生する可能性がある、急速な循環を防ぐために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-171">Two values are used to prevent rapid cycling, which can occur if one value is used.</span></span>

### <a name="examples"></a><span data-ttu-id="a787e-172">使用例</span><span class="sxs-lookup"><span data-stu-id="a787e-172">Examples</span></span>

```csharp
// The Pipe will start returning incomplete tasks from FlushAsync until
// the reader examines at least 5 bytes.
var options = new PipeOptions(pauseWriterThreshold: 10, resumeWriterThreshold: 5);
var pipe = new Pipe(options);
```

### <a name="pipescheduler"></a><span data-ttu-id="a787e-173">PipeScheduler</span><span class="sxs-lookup"><span data-stu-id="a787e-173">PipeScheduler</span></span>

<span data-ttu-id="a787e-174">通常、`async` および `await` を使用する場合、非同期コードは <xref:System.Threading.Tasks.TaskScheduler> または現在の <xref:System.Threading.SynchronizationContext> で再開されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-174">Typically when using `async` and `await`, asynchronous code resumes on either on a <xref:System.Threading.Tasks.TaskScheduler> or on the current <xref:System.Threading.SynchronizationContext>.</span></span>

<span data-ttu-id="a787e-175">I/O を行う場合は、I/O が実行される場所をきめ細かく制御することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a787e-175">When doing I/O, it's important to have fine-grained control over where the I/O is performed.</span></span> <span data-ttu-id="a787e-176">この制御により、CPU キャッシュを効果的に利用できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-176">This control allows taking advantage of CPU caches effectively.</span></span> <span data-ttu-id="a787e-177">効率的なキャッシュは、Web サーバーなどのハイ パフォーマンス アプリに不可欠です。</span><span class="sxs-lookup"><span data-stu-id="a787e-177">Efficient caching is critical for high-performance apps like web servers.</span></span> <span data-ttu-id="a787e-178"><xref:System.IO.Pipelines.PipeScheduler> では、非同期コールバックが実行される場所を制御できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-178"><xref:System.IO.Pipelines.PipeScheduler> provides control over where asynchronous callbacks run.</span></span> <span data-ttu-id="a787e-179">既定では:</span><span class="sxs-lookup"><span data-stu-id="a787e-179">By default:</span></span>

* <span data-ttu-id="a787e-180">現在の <xref:System.Threading.SynchronizationContext> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-180">The current <xref:System.Threading.SynchronizationContext> is used.</span></span>
* <span data-ttu-id="a787e-181">`SynchronizationContext` がない場合は、スレッド プールを使用してコールバックを実行します。</span><span class="sxs-lookup"><span data-stu-id="a787e-181">If there's no `SynchronizationContext`, it uses the thread pool to run callbacks.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/Program.cs" id="snippet":::

<span data-ttu-id="a787e-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) は、スレッド プールへのコールバックをキューに登録する <xref:System.IO.Pipelines.PipeScheduler> の実装です。</span><span class="sxs-lookup"><span data-stu-id="a787e-182">[PipeScheduler.ThreadPool](xref:System.IO.Pipelines.PipeScheduler.ThreadPool) is the <xref:System.IO.Pipelines.PipeScheduler> implementation that queues callbacks to the thread pool.</span></span> <span data-ttu-id="a787e-183">`PipeScheduler.ThreadPool` は既定値であり、一般的に最適な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="a787e-183">`PipeScheduler.ThreadPool` is the default and generally the best choice.</span></span> <span data-ttu-id="a787e-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) を使用すると、デッドロックなどの意図しない結果となる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-184">[PipeScheduler.Inline](xref:System.IO.Pipelines.PipeScheduler.Inline) can cause unintended consequences such as deadlocks.</span></span>

### <a name="pipe-reset"></a><span data-ttu-id="a787e-185">パイプのリセット</span><span class="sxs-lookup"><span data-stu-id="a787e-185">Pipe reset</span></span>

<span data-ttu-id="a787e-186">多くの場合、`Pipe` オブジェクトを再利用するのが効率的です。</span><span class="sxs-lookup"><span data-stu-id="a787e-186">It's frequently efficient to reuse the `Pipe` object.</span></span> <span data-ttu-id="a787e-187">パイプをリセットするには、`PipeReader` と `PipeWriter` の両方が完了したときに <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a787e-187">To reset the pipe, call <xref:System.IO.Pipelines.PipeReader> <xref:System.IO.Pipelines.Pipe.Reset%2A> when both the `PipeReader` and `PipeWriter` are complete.</span></span>

## <a name="pipereader"></a><span data-ttu-id="a787e-188">PipeReader</span><span class="sxs-lookup"><span data-stu-id="a787e-188">PipeReader</span></span>

<span data-ttu-id="a787e-189"><xref:System.IO.Pipelines.PipeReader> では、呼び出し元の代わりにメモリを管理します。</span><span class="sxs-lookup"><span data-stu-id="a787e-189"><xref:System.IO.Pipelines.PipeReader> manages memory on the caller's behalf.</span></span> <span data-ttu-id="a787e-190"><xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType> を呼び出した後に、**常に**<xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a787e-190">**Always** call <xref:System.IO.Pipelines.PipeReader.AdvanceTo%2A?displayProperty=nameWithType> after calling <xref:System.IO.Pipelines.PipeReader.ReadAsync%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a787e-191">これにより、`PipeReader` では、呼び出し元がメモリを使用して実行されるタイミングを把握し、追跡できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a787e-191">This lets the `PipeReader` know when the caller is done with the memory so that it can be tracked.</span></span> <span data-ttu-id="a787e-192">`PipeReader.ReadAsync` から返された `ReadOnlySequence<byte>` が有効なのは、`PipeReader.AdvanceTo` が呼び出されるまでのみとなります。</span><span class="sxs-lookup"><span data-stu-id="a787e-192">The `ReadOnlySequence<byte>` returned from `PipeReader.ReadAsync` is only valid until the call the `PipeReader.AdvanceTo`.</span></span> <span data-ttu-id="a787e-193">`PipeReader.AdvanceTo` を呼び出した後、`ReadOnlySequence<byte>` を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a787e-193">It's illegal to use `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo`.</span></span>

<span data-ttu-id="a787e-194">`PipeReader.AdvanceTo` では、次の 2 つの <xref:System.SequencePosition> 引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a787e-194">`PipeReader.AdvanceTo` takes two <xref:System.SequencePosition> arguments:</span></span>

* <span data-ttu-id="a787e-195">最初の引数では、消費されたメモリの量を判別します。</span><span class="sxs-lookup"><span data-stu-id="a787e-195">The first argument determines how much memory was consumed.</span></span>
* <span data-ttu-id="a787e-196">2 番目の引数では、監視されたバッファーの量を判別します。</span><span class="sxs-lookup"><span data-stu-id="a787e-196">The second argument determines how much of the buffer was observed.</span></span>

<span data-ttu-id="a787e-197">データを消費済みとしてマークすることは、パイプでメモリを基になるバッファープ ールに返すことができることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a787e-197">Marking data as consumed means that the pipe can return the memory to the underlying buffer pool.</span></span> <span data-ttu-id="a787e-198">データを監視済みとしてマークすると、`PipeReader.ReadAsync` の次の呼び出しで行われる内容が制御されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-198">Marking data as observed controls what the next call to `PipeReader.ReadAsync` does.</span></span> <span data-ttu-id="a787e-199">すべてを監視済みとしてマークすることは、パイプにデータがさらに書き込まれるまで、`PipeReader.ReadAsync` の次の呼び出しでは何も返されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a787e-199">Marking everything as observed means that the next call to `PipeReader.ReadAsync` won't return until there's more data written to the pipe.</span></span> <span data-ttu-id="a787e-200">それ以外の値を指定すると、`PipeReader.ReadAsync` の次の呼び出しで、監視されたデータ *と* 監視されていないデータがすぐに返されますが、既に消費されているデータは除きます。</span><span class="sxs-lookup"><span data-stu-id="a787e-200">Any other value will make the next call to `PipeReader.ReadAsync` return immediately with the observed *and* unobserved data, but not data that has already been consumed.</span></span>

### <a name="read-streaming-data-scenarios"></a><span data-ttu-id="a787e-201">ストリーミング データの読み取りシナリオ</span><span class="sxs-lookup"><span data-stu-id="a787e-201">Read streaming data scenarios</span></span>

<span data-ttu-id="a787e-202">ストリーミング データを読み取ろうとすると発生する、一般的なパターンがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="a787e-202">There are a couple of typical patterns that emerge when trying to read streaming data:</span></span>

* <span data-ttu-id="a787e-203">指定したデータのストリームで、1 つのメッセージを解析する。</span><span class="sxs-lookup"><span data-stu-id="a787e-203">Given a stream of data, parse a single message.</span></span>
* <span data-ttu-id="a787e-204">指定したデータのストリームで、使用可能なメッセージをすべて解析する。</span><span class="sxs-lookup"><span data-stu-id="a787e-204">Given a stream of data, parse all available messages.</span></span>

<span data-ttu-id="a787e-205">次の例では、`ReadOnlySequence<byte>` からのメッセージを解析するために `TryParseMessage` メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="a787e-205">The following examples use the `TryParseMessage` method for parsing messages from a `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="a787e-206">`TryParseMessage`では 1 つのメッセージを解析し、入力バッファーを更新して、解析されたメッセージをバッファーからトリミングします。</span><span class="sxs-lookup"><span data-stu-id="a787e-206">`TryParseMessage` parses a single message and update the input buffer to trim the parsed message from the buffer.</span></span> <span data-ttu-id="a787e-207">`TryParseMessage` は .NET の一部ではありません。これは、次のセクションで使用されるユーザーが記述するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="a787e-207">`TryParseMessage` is not part of .NET, it's a user written method used in the following sections.</span></span>

```csharp
bool TryParseMessage(ref ReadOnlySequence<byte> buffer, out Message message);
```

### <a name="read-a-single-message"></a><span data-ttu-id="a787e-208">1 つのメッセージを読み取る</span><span class="sxs-lookup"><span data-stu-id="a787e-208">Read a single message</span></span>

<span data-ttu-id="a787e-209">次のコードでは、`PipeReader` からの 1 つのメッセージを読み取り、呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="a787e-209">The following code reads a single message from a `PipeReader` and returns it to the caller.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/ReadSingleMsg.cs" id="snippet":::

<span data-ttu-id="a787e-210">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="a787e-210">The preceding code:</span></span>

* <span data-ttu-id="a787e-211">1 つのメッセージを解析します。</span><span class="sxs-lookup"><span data-stu-id="a787e-211">Parses a single message.</span></span>
* <span data-ttu-id="a787e-212">消費された `SequencePosition` と検査された `SequencePosition` を更新し、トリミングされた入力バッファーの先頭を指すようにします。</span><span class="sxs-lookup"><span data-stu-id="a787e-212">Updates the consumed `SequencePosition` and examined `SequencePosition` to point to the start of the trimmed input buffer.</span></span>

<span data-ttu-id="a787e-213">2 つの `SequencePosition` 引数が更新されます。これは、`TryParseMessage` で解析されたメッセージが入力バッファーから削除されるためです。</span><span class="sxs-lookup"><span data-stu-id="a787e-213">The two `SequencePosition` arguments are updated because `TryParseMessage` removes the parsed message from the input buffer.</span></span> <span data-ttu-id="a787e-214">一般に、バッファーからの 1 つのメッセージを解析する場合、検査位置は次のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-214">Generally, when parsing a single message from the buffer, the examined position should be one of the following:</span></span>

* <span data-ttu-id="a787e-215">メッセージの終わり。</span><span class="sxs-lookup"><span data-stu-id="a787e-215">The end of the message.</span></span>
* <span data-ttu-id="a787e-216">メッセージが検出されなかった場合は、受信されたバッファーの終わり。</span><span class="sxs-lookup"><span data-stu-id="a787e-216">The end of the received buffer if no message was found.</span></span>

<span data-ttu-id="a787e-217">1 つのメッセージ ケースでは、エラーが発生する可能性が最も高くなります。</span><span class="sxs-lookup"><span data-stu-id="a787e-217">The single message case has the most potential for errors.</span></span> <span data-ttu-id="a787e-218">*examined* に間違った値を渡すと、メモリ不足の例外または無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-218">Passing the wrong values to *examined* can result in an out of memory exception or an infinite loop.</span></span> <span data-ttu-id="a787e-219">詳細については、この記事の「[PipeReader の一般的な問題](#gotchas)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a787e-219">For more information, see the [PipeReader common problems](#gotchas) section in this article.</span></span>

### <a name="reading-multiple-messages"></a><span data-ttu-id="a787e-220">複数のメッセージの読み取り</span><span class="sxs-lookup"><span data-stu-id="a787e-220">Reading multiple messages</span></span>

<span data-ttu-id="a787e-221">次のコードでは、`PipeReader` からのすべてのメッセージを読み取り、それぞれに対して `ProcessMessageAsync` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a787e-221">The following code reads all messages from a `PipeReader` and calls `ProcessMessageAsync` on each.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection1.cs" id="snippet":::

### <a name="cancellation"></a><span data-ttu-id="a787e-222">キャンセル</span><span class="sxs-lookup"><span data-stu-id="a787e-222">Cancellation</span></span>

<span data-ttu-id="a787e-223">`PipeReader.ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="a787e-223">`PipeReader.ReadAsync`:</span></span>

* <span data-ttu-id="a787e-224"><xref:System.Threading.CancellationToken> を渡すことをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a787e-224">Supports passing a <xref:System.Threading.CancellationToken>.</span></span>
* <span data-ttu-id="a787e-225">読み取りが保留中のときに `CancellationToken` が取り消された場合は、<xref:System.OperationCanceledException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="a787e-225">Throws an <xref:System.OperationCanceledException> if the `CancellationToken` is canceled while there's a read pending.</span></span>
* <span data-ttu-id="a787e-226"><xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType> を使用して現在の読み取り操作を取り消す方法をサポートします。これにより、例外の発生を回避できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-226">Supports a way to cancel the current read operation via <xref:System.IO.Pipelines.PipeReader.CancelPendingRead%2A?displayProperty=nameWithType>, which avoids raising an exception.</span></span> <span data-ttu-id="a787e-227">`PipeReader.CancelPendingRead` を呼び出すと、`PipeReader.ReadAsync` の現在の呼び出しまたは次の呼び出しで、`IsCanceled` が `true` に設定された <xref:System.IO.Pipelines.ReadResult> が返されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-227">Calling `PipeReader.CancelPendingRead` causes the current or next call to `PipeReader.ReadAsync` to return a <xref:System.IO.Pipelines.ReadResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="a787e-228">これは、既存の読み取りループを非破壊的で非例外的な方法で停止する際に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-228">This can be useful for halting the existing read loop in a non-destructive and non-exceptional way.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyConnection.cs" id="snippet":::

<a name="gotchas"></a>

### <a name="pipereader-common-problems"></a><span data-ttu-id="a787e-229">PipeReader の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="a787e-229">PipeReader common problems</span></span>

* <span data-ttu-id="a787e-230">`consumed` または `examined` に間違った値を渡すと、既に読み取られているデータが読み取られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-230">Passing the wrong values to `consumed` or `examined` may result in reading already read data.</span></span>
* <span data-ttu-id="a787e-231">`buffer.End` を検査済みとして渡すと、次のようになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-231">Passing `buffer.End` as examined may result in:</span></span>

  * <span data-ttu-id="a787e-232">データが停止する</span><span class="sxs-lookup"><span data-stu-id="a787e-232">Stalled data</span></span>
  * <span data-ttu-id="a787e-233">データが消費されていない場合、最終的にメモリ不足 (OOM) 例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-233">Possibly an eventual Out of Memory (OOM) exception if data isn't consumed.</span></span> <span data-ttu-id="a787e-234">たとえば、バッファーから一度に 1 つのメッセージを処理する場合は、`PipeReader.AdvanceTo(position, buffer.End)` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-234">For example, `PipeReader.AdvanceTo(position, buffer.End)` when processing a single message at a time from the buffer.</span></span>

* <span data-ttu-id="a787e-235">`consumed` または `examined` に間違った値を渡すと、無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-235">Passing the wrong values to `consumed` or `examined` may result in an infinite loop.</span></span> <span data-ttu-id="a787e-236">たとえば、`buffer.Start` が変更されていない場合、`PipeReader.AdvanceTo(buffer.Start)` では、新しいデータが到着する直前に `PipeReader.ReadAsync` への次の呼び出しで制御が返されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-236">For example, `PipeReader.AdvanceTo(buffer.Start)` if `buffer.Start` hasn't changed will cause the next call to `PipeReader.ReadAsync` to return immediately before new data arrives.</span></span>
* <span data-ttu-id="a787e-237">`consumed` または `examined` に間違った値を渡すと、無限バッファーリング (最終的には OOM) が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-237">Passing the wrong values to `consumed` or `examined` may result in infinite buffering (eventual OOM).</span></span>
* <span data-ttu-id="a787e-238">`PipeReader.AdvanceTo` を呼び出した後に `ReadOnlySequence<byte>` を使用すると、メモリが破損する可能性があります (解放後使用)。</span><span class="sxs-lookup"><span data-stu-id="a787e-238">Using the `ReadOnlySequence<byte>` after calling `PipeReader.AdvanceTo` may result in memory corruption (use after free).</span></span>
* <span data-ttu-id="a787e-239">`PipeReader.Complete/CompleteAsync` を呼び出せないと、メモリ リークが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-239">Failing to call `PipeReader.Complete/CompleteAsync` may result in a memory leak.</span></span>
* <span data-ttu-id="a787e-240">バッファーを処理する前に <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> を確認し、読み取りロジックを終了すると、データが失われます。</span><span class="sxs-lookup"><span data-stu-id="a787e-240">Checking <xref:System.IO.Pipelines.ReadResult.IsCompleted?displayProperty=nameWithType> and exiting the reading logic before processing the buffer results in data loss.</span></span> <span data-ttu-id="a787e-241">ループの終了条件は、`ReadResult.Buffer.IsEmpty` および `ReadResult.IsCompleted` に基づいている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-241">The loop exit condition should be based on `ReadResult.Buffer.IsEmpty` and `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="a787e-242">これを誤って実行すると、無限ループになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-242">Doing this incorrectly could result in an infinite loop.</span></span>

#### <a name="problematic-code"></a><span data-ttu-id="a787e-243">問題のあるコード</span><span class="sxs-lookup"><span data-stu-id="a787e-243">Problematic code</span></span>

<span data-ttu-id="a787e-244">❌ **データ損失**</span><span class="sxs-lookup"><span data-stu-id="a787e-244">❌ **Data loss**</span></span>

<span data-ttu-id="a787e-245">`IsCompleted` が `true` に設定されている場合、`ReadResult` でデータの最終セグメントを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a787e-245">The `ReadResult` can return the final segment of data when `IsCompleted` is set to `true`.</span></span> <span data-ttu-id="a787e-246">読み取りループを終了する前にデータを読み取らないと、データが失われます。</span><span class="sxs-lookup"><span data-stu-id="a787e-246">Not reading that data before exiting the read loop will result in data loss.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="a787e-247">❌ **無限ループ**</span><span class="sxs-lookup"><span data-stu-id="a787e-247">❌ **Infinite loop**</span></span>

<span data-ttu-id="a787e-248">次のロジックでは、`Result.IsCompleted` が `true` でも、バッファー内に完全なメッセージがない場合は、無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-248">The following logic may result in an infinite loop if the `Result.IsCompleted` is `true` but there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet2":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="a787e-249">同じ問題があるもう 1 つのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="a787e-249">Here's another piece of code with the same problem.</span></span> <span data-ttu-id="a787e-250">`ReadResult.IsCompleted` を確認する前に、空でないバッファーがあるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-250">It's checking for a non-empty buffer before checking `ReadResult.IsCompleted`.</span></span> <span data-ttu-id="a787e-251">これは `else if` にあるため、バッファー内に完全なメッセージがない場合は、無限にループされます。</span><span class="sxs-lookup"><span data-stu-id="a787e-251">Because it's in an `else if`, it will loop forever if there's never a complete message in the buffer.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet3":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="a787e-252">❌ **予期しないハング**</span><span class="sxs-lookup"><span data-stu-id="a787e-252">❌ **Unexpected Hang**</span></span>

<span data-ttu-id="a787e-253">`examined` の位置で `buffer.End` を使用して `PipeReader.AdvanceTo` を無条件に呼び出すと、1 つのメッセージを解析するときにハングが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-253">Unconditionally calling `PipeReader.AdvanceTo` with `buffer.End` in the `examined` position may result in hangs when parsing a single message.</span></span> <span data-ttu-id="a787e-254">`PipeReader.AdvanceTo` の次の呼び出しでは、以下のようになるまで何も返されません。</span><span class="sxs-lookup"><span data-stu-id="a787e-254">The next call to `PipeReader.AdvanceTo` won't return until:</span></span>

* <span data-ttu-id="a787e-255">パイプにさらにデータが書き込まれている。</span><span class="sxs-lookup"><span data-stu-id="a787e-255">There's more data written to the pipe.</span></span>
* <span data-ttu-id="a787e-256">また、新しいデータが以前に検査されていない。</span><span class="sxs-lookup"><span data-stu-id="a787e-256">And the new data wasn't previously examined.</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet4":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="a787e-257">❌ **メモリ不足 (OOM)**</span><span class="sxs-lookup"><span data-stu-id="a787e-257">❌ **Out of Memory (OOM)**</span></span>

<span data-ttu-id="a787e-258">次のような状況の場合、以下のコードでは、<xref:System.OutOfMemoryException> が発生するまでバッファーが保持されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-258">With the following conditions, the following code keeps buffering until an <xref:System.OutOfMemoryException> occurs:</span></span>

* <span data-ttu-id="a787e-259">最大メッセージ サイズがない。</span><span class="sxs-lookup"><span data-stu-id="a787e-259">There's no maximum message size.</span></span>
* <span data-ttu-id="a787e-260">`PipeReader` から返されたデータで、完全なメッセージが作成されない。</span><span class="sxs-lookup"><span data-stu-id="a787e-260">The data returned from the `PipeReader` doesn't make a complete message.</span></span> <span data-ttu-id="a787e-261">たとえば、他の側で大きなメッセージ (4 GB のメッセージなど) を書き込んでいるため、完全なメッセージが作成されていない。</span><span class="sxs-lookup"><span data-stu-id="a787e-261">For example, it doesn't make a complete message because the other side is writing a large message (For example, a 4-GB message).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet5":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

<span data-ttu-id="a787e-262">❌ **メモリの破損**</span><span class="sxs-lookup"><span data-stu-id="a787e-262">❌ **Memory Corruption**</span></span>

<span data-ttu-id="a787e-263">バッファーを読み取るヘルパーを記述するときは、返されたすべてのペイロードをコピーしてから `Advance` を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-263">When writing helpers that read the buffer, any returned payload should be copied before calling `Advance`.</span></span> <span data-ttu-id="a787e-264">次の例では、`Pipe` で破棄されたメモリを返し、次の操作 (読み取り/書き込み) でそれを再利用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-264">The following example will return memory that the `Pipe` has discarded and may reuse it for the next operation (read/write).</span></span>

[!INCLUDE [pipelines-do-not-use-1](../../../includes/pipelines-do-not-use-1.md)]

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippetMessage":::

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/DoNotUse.cs" id="snippet6":::

[!INCLUDE [pipelines-do-not-use-2](../../../includes/pipelines-do-not-use-2.md)]

## <a name="pipewriter"></a><span data-ttu-id="a787e-265">PipeWriter</span><span class="sxs-lookup"><span data-stu-id="a787e-265">PipeWriter</span></span>

<span data-ttu-id="a787e-266"><xref:System.IO.Pipelines.PipeWriter> では、呼び出し元の代わりに書き込むバッファーを管理します。</span><span class="sxs-lookup"><span data-stu-id="a787e-266">The <xref:System.IO.Pipelines.PipeWriter> manages buffers for writing on the caller's behalf.</span></span> <span data-ttu-id="a787e-267">`PipeWriter` では、[`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601) を実装します。</span><span class="sxs-lookup"><span data-stu-id="a787e-267">`PipeWriter` implements [`IBufferWriter<byte>`](xref:System.Buffers.IBufferWriter%601).</span></span> <span data-ttu-id="a787e-268">`IBufferWriter<byte>` は、バッファーのコピーを追加せずに、書き込みを実行するためにバッファーにアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="a787e-268">`IBufferWriter<byte>` makes it possible to get access to buffers to perform writes without additional buffer copies.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet":::

<span data-ttu-id="a787e-269">上記のコードでは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a787e-269">The previous code:</span></span>

* <span data-ttu-id="a787e-270"><xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> を使用して、`PipeWriter` から少なくとも 5 バイトのバッファーを要求します。</span><span class="sxs-lookup"><span data-stu-id="a787e-270">Requests a buffer of at least 5 bytes from the `PipeWriter` using <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A>.</span></span>
* <span data-ttu-id="a787e-271">ASCII 文字列である `"Hello"` のバイトを、返された `Memory<byte>` に書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a787e-271">Writes bytes for the ASCII string `"Hello"` to the returned `Memory<byte>`.</span></span>
* <span data-ttu-id="a787e-272"><xref:System.IO.Pipelines.PipeWriter.Advance%2A> を呼び出して、バッファーに書き込まれたバイト数を示します。</span><span class="sxs-lookup"><span data-stu-id="a787e-272">Calls <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to indicate how many bytes were written to the buffer.</span></span>
* <span data-ttu-id="a787e-273">基になるデバイスにバイトを送信する、`PipeWriter` をフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="a787e-273">Flushes the `PipeWriter`, which sends the bytes to the underlying device.</span></span>

<span data-ttu-id="a787e-274">上記の書き込みメソッドでは、`PipeWriter` によって提供されるバッファーが使用されています。</span><span class="sxs-lookup"><span data-stu-id="a787e-274">The previous method of writing uses the buffers provided by the `PipeWriter`.</span></span> <span data-ttu-id="a787e-275">あるいは、<xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType> では次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a787e-275">Alternatively, <xref:System.IO.Pipelines.PipeWriter.WriteAsync%2A?displayProperty=nameWithType>:</span></span>

* <span data-ttu-id="a787e-276">既存のバッファーを `PipeWriter` にコピーします。</span><span class="sxs-lookup"><span data-stu-id="a787e-276">Copies the existing buffer to the `PipeWriter`.</span></span>
* <span data-ttu-id="a787e-277">`GetSpan` を呼び出し、必要に応じて `Advance` を呼び出してから、<xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a787e-277">Calls `GetSpan`, `Advance` as appropriate and calls <xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A>.</span></span>

:::code language="csharp" source="~/samples/snippets/csharp/pipelines/MyPipeWriter.cs" id="snippet2":::

### <a name="cancellation"></a><span data-ttu-id="a787e-278">キャンセル</span><span class="sxs-lookup"><span data-stu-id="a787e-278">Cancellation</span></span>

<span data-ttu-id="a787e-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> では、<xref:System.Threading.CancellationToken> を渡すことがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a787e-279"><xref:System.IO.Pipelines.PipeWriter.FlushAsync%2A> supports passing a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="a787e-280">`CancellationToken` を渡すと、フラッシュの保留中にトークンが取り消された場合に、`OperationCanceledException` となります。</span><span class="sxs-lookup"><span data-stu-id="a787e-280">Passing a `CancellationToken` results in an `OperationCanceledException` if the token is canceled while there's a flush pending.</span></span> <span data-ttu-id="a787e-281">`PipeWriter.FlushAsync` では、例外を発生させることなく、<xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> を使用して、現在のフラッシュ操作を取り消す方法がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a787e-281">`PipeWriter.FlushAsync` supports a way to cancel the current flush operation via <xref:System.IO.Pipelines.PipeWriter.CancelPendingFlush%2A?displayProperty=nameWithType> without raising an exception.</span></span> <span data-ttu-id="a787e-282">`PipeWriter.CancelPendingFlush` を呼び出すと、`PipeWriter.FlushAsync` または `PipeWriter.WriteAsync` の現在の呼び出しあるいは次の呼び出しで、`IsCanceled` が `true` に設定された <xref:System.IO.Pipelines.FlushResult> が返されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-282">Calling `PipeWriter.CancelPendingFlush` causes the current or next call to `PipeWriter.FlushAsync` or `PipeWriter.WriteAsync` to return a <xref:System.IO.Pipelines.FlushResult> with `IsCanceled` set to `true`.</span></span> <span data-ttu-id="a787e-283">これは、非破壊的で非例外的な方法で生成されるフラッシュを停止する際に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-283">This can be useful for halting the yielding flush in a non-destructive and non-exceptional way.</span></span>

<a name="pwcp"></a>

### <a name="pipewriter-common-problems"></a><span data-ttu-id="a787e-284">PipeWriter の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="a787e-284">PipeWriter common problems</span></span>

* <span data-ttu-id="a787e-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> および <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> では、少なくとも要求された量のメモリを持つバッファーを返します。</span><span class="sxs-lookup"><span data-stu-id="a787e-285"><xref:System.IO.Pipelines.PipeWriter.GetSpan%2A> and <xref:System.IO.Pipelines.PipeWriter.GetMemory%2A> return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="a787e-286">正確なバッファー サイズを想定 **しないでください**。</span><span class="sxs-lookup"><span data-stu-id="a787e-286">**Don't** assume exact buffer sizes.</span></span>
* <span data-ttu-id="a787e-287">連続する呼び出しで同じバッファーまたは同じサイズのバッファーが返される保証はありません。</span><span class="sxs-lookup"><span data-stu-id="a787e-287">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
* <span data-ttu-id="a787e-288">さらにデータの書き込みを続行するには、<xref:System.IO.Pipelines.PipeWriter.Advance%2A> を呼び出した後に新しいバッファーを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-288">A new buffer must be requested after calling <xref:System.IO.Pipelines.PipeWriter.Advance%2A> to continue writing more data.</span></span> <span data-ttu-id="a787e-289">以前に取得したバッファーに書き込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="a787e-289">The previously acquired buffer can't be written to.</span></span>
* <span data-ttu-id="a787e-290">`FlushAsync` の呼び出しが不完全な場合に `GetMemory` または `GetSpan` を呼び出すのは安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="a787e-290">Calling `GetMemory` or `GetSpan` while there's an incomplete call to `FlushAsync` isn't safe.</span></span>
* <span data-ttu-id="a787e-291">フラッシュされていないデータがある場合に `Complete` または `CompleteAsync` を呼び出すと、メモリが破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-291">Calling `Complete` or `CompleteAsync` while there's unflushed data can result in memory corruption.</span></span>

## <a name="iduplexpipe"></a><span data-ttu-id="a787e-292">IDuplexPipe</span><span class="sxs-lookup"><span data-stu-id="a787e-292">IDuplexPipe</span></span>

<span data-ttu-id="a787e-293"><xref:System.IO.Pipelines.IDuplexPipe> は、読み取りと書き込みの両方をサポートする種類のコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="a787e-293">The <xref:System.IO.Pipelines.IDuplexPipe> is a contract for types that support both reading and writing.</span></span> <span data-ttu-id="a787e-294">たとえば、ネットワーク接続は `IDuplexPipe` によって表されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-294">For example, a network connection would be represented by an `IDuplexPipe`.</span></span>

 <span data-ttu-id="a787e-295">`PipeReader` と `PipeWriter` を含む `Pipe` とは異なり、`IDuplexPipe` は全二重接続の片側を表します。</span><span class="sxs-lookup"><span data-stu-id="a787e-295">Unlike `Pipe`, which contains a `PipeReader` and a `PipeWriter`, `IDuplexPipe` represents a single side of a full duplex connection.</span></span> <span data-ttu-id="a787e-296">つまり、`PipeWriter` に書き込まれるものは、`PipeReader` からは読み取られません。</span><span class="sxs-lookup"><span data-stu-id="a787e-296">That means what is written to the `PipeWriter` will not be read from the `PipeReader`.</span></span>

## <a name="streams"></a><span data-ttu-id="a787e-297">ストリーム</span><span class="sxs-lookup"><span data-stu-id="a787e-297">Streams</span></span>

<span data-ttu-id="a787e-298">ストリーム データの読み取りまたは書き込みを行う場合、通常は、デシリアライザーを使用してデータを読み取り、シリアライザーを使用してデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a787e-298">When reading or writing stream data, you typically read data using a de-serializer and write data using a serializer.</span></span> <span data-ttu-id="a787e-299">これらの読み取りおよび書き込みストリーム API のほとんどに、`Stream` パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="a787e-299">Most of these read and write stream APIs have a `Stream` parameter.</span></span> <span data-ttu-id="a787e-300">これらの既存の API との統合をより容易にするために、`PipeReader` および `PipeWriter` で <xref:System.IO.Pipelines.PipeReader.AsStream%2A> メソッドが公開されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-300">To make it easier to integrate with these existing APIs, `PipeReader` and `PipeWriter` expose an <xref:System.IO.Pipelines.PipeReader.AsStream%2A> method.</span></span> <span data-ttu-id="a787e-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> では、`PipeReader` または `PipeWriter` に関する `Stream` 実装を返します。</span><span class="sxs-lookup"><span data-stu-id="a787e-301"><xref:System.IO.Pipelines.PipeWriter.AsStream%2A> returns a `Stream` implementation around the `PipeReader` or `PipeWriter`.</span></span>

### <a name="stream-example"></a><span data-ttu-id="a787e-302">ストリームの例</span><span class="sxs-lookup"><span data-stu-id="a787e-302">Stream example</span></span>

<span data-ttu-id="a787e-303">`PipeReader` および `PipeWriter` インスタンスは、静的な `Create` メソッドを使用し、<xref:System.IO.Stream> オブジェクトとそれに対応する任意の作成オプションを指定して作成できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-303">`PipeReader` and `PipeWriter` instances can be created using the static `Create` methods given a <xref:System.IO.Stream> object and optional corresponding creation options.</span></span>

<span data-ttu-id="a787e-304"><xref:System.IO.Pipelines.StreamPipeReaderOptions> では、次のパラメーターを使用して `PipeReader` インスタンスの作成を制御できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-304">The <xref:System.IO.Pipelines.StreamPipeReaderOptions> allow for control over the creation of the `PipeReader` instance with the following parameters:</span></span>

- <span data-ttu-id="a787e-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> はプールからメモリを借りるときに使用される最小バッファー サイズ (バイト単位) であり、既定値は `4096` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-305"><xref:System.IO.Pipelines.StreamPipeReaderOptions.BufferSize?displayProperty=nameWithType> is the minimum buffer size in bytes used when renting memory from the pool, and defaults to `4096`.</span></span>
- <span data-ttu-id="a787e-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> フラグによって、`PipeReader` の完了後、基礎となるストリームを開いたままにするかどうかが決定されます。既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-306"><xref:System.IO.Pipelines.StreamPipeReaderOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeReader` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="a787e-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> は、新しいバッファーが割り当てられる前のバッファー内に残るバイト数のしきい値を表します。既定値は `1024` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-307"><xref:System.IO.Pipelines.StreamPipeReaderOptions.MinimumReadSize?displayProperty=nameWithType> represents the threshold of remaining bytes in the buffer before a new buffer is allocated, and defaults to `1024`.</span></span>
- <span data-ttu-id="a787e-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> はメモリを割り当てるときに使用される `MemoryPool<byte>` であり、既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-308"><xref:System.IO.Pipelines.StreamPipeReaderOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

<span data-ttu-id="a787e-309"><xref:System.IO.Pipelines.StreamPipeWriterOptions> では、次のパラメーターを使用して `PipeWriter` インスタンスの作成を制御できます。</span><span class="sxs-lookup"><span data-stu-id="a787e-309">The <xref:System.IO.Pipelines.StreamPipeWriterOptions> allow for control over the creation of the `PipeWriter` instance with the following parameters:</span></span>

- <span data-ttu-id="a787e-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> フラグによって、`PipeWriter` の完了後、基礎となるストリームを開いたままにするかどうかが決定されます。既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-310"><xref:System.IO.Pipelines.StreamPipeWriterOptions.LeaveOpen?displayProperty=nameWithType> flag determines whether or not the underlying stream is left open after the `PipeWriter` completes, and defaults to `false`.</span></span>
- <span data-ttu-id="a787e-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> は、<xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool> からメモリをレンタルしているときに使用する最小バッファー サイズを表します。既定値は `4096` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-311"><xref:System.IO.Pipelines.StreamPipeWriterOptions.MinimumBufferSize?displayProperty=nameWithType> represents the minimum buffer size to use when renting memory from the <xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool>, and defaults to `4096`.</span></span>
- <span data-ttu-id="a787e-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> はメモリを割り当てるときに使用される `MemoryPool<byte>` であり、既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="a787e-312"><xref:System.IO.Pipelines.StreamPipeWriterOptions.Pool?displayProperty=nameWithType> is the `MemoryPool<byte>` used when allocating memory, and defaults to `null`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a787e-313">`Create` メソッドを使用して `PipeReader` および `PipeWriter` インスタンスを作成するとき、`Stream` オブジェクトの有効期間を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-313">When creating `PipeReader` and `PipeWriter` instances using the `Create` methods, you need to consider the `Stream` object lifetime.</span></span> <span data-ttu-id="a787e-314">リーダーまたはライターでストリームの利用が終わった後にストリームにアクセスする必要がある場合、作成オプションで `LeaveOpen` フラグを `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a787e-314">If you need access to the stream after the reader or writer is done with it, you'll need to set the `LeaveOpen` flag to `true` on the creation options.</span></span> <span data-ttu-id="a787e-315">設定しない場合、ストリームは閉じられます。</span><span class="sxs-lookup"><span data-stu-id="a787e-315">Otherwise, the stream will be closed.</span></span>

<span data-ttu-id="a787e-316">次のコードでは、ストリームからの `Create` メソッドを利用し、`PipeReader` および `PipeWriter` インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-316">The following code demonstrates the creation of `PipeReader` and `PipeWriter` instances using the `Create` methods from a stream.</span></span>

:::code language="csharp" source="snippets/pipelines/Program.cs":::

<span data-ttu-id="a787e-317">このアプリケーションによって <xref:System.IO.StreamReader> が使用され、ストリームとして *lorem-ipsum.txt* ファイルが読み取られます。</span><span class="sxs-lookup"><span data-stu-id="a787e-317">The application uses a <xref:System.IO.StreamReader> to read the *lorem-ipsum.txt* file as a stream.</span></span> <span data-ttu-id="a787e-318"><xref:System.IO.FileStream> は、`PipeReader` オブジェクトをインスタンス化する <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType> に渡されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-318">The <xref:System.IO.FileStream> is passed to <xref:System.IO.Pipelines.PipeReader.Create%2A?displayProperty=nameWithType>, which instantiates a `PipeReader` object.</span></span> <span data-ttu-id="a787e-319">次に、コンソール アプリケーションから <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType> を使用して <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> にその標準出力ストリームが渡されます。</span><span class="sxs-lookup"><span data-stu-id="a787e-319">The console application then passes its standard output stream to <xref:System.IO.Pipelines.PipeWriter.Create%2A?displayProperty=nameWithType> using <xref:System.Console.OpenStandardOutput?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a787e-320">この例では[キャンセル](#cancellation)がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a787e-320">The example supports [cancellation](#cancellation).</span></span>
