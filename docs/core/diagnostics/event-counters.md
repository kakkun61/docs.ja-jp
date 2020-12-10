---
title: .NET Core の EventCounters
description: この記事では、EventCounters の概要とその実装方法および使用方法について学習します。
ms.date: 08/07/2020
ms.openlocfilehash: 68c831713eed8c49d24ebf93da301ef68d213bf9
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437821"
---
# <a name="eventcounters-in-net-core"></a><span data-ttu-id="37bd8-103">.NET Core の EventCounters</span><span class="sxs-lookup"><span data-stu-id="37bd8-103">EventCounters in .NET Core</span></span>

<span data-ttu-id="37bd8-104">**この記事の対象: ✔️** .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="37bd8-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="37bd8-105">EventCounters は、軽量でクロスプラットフォームであり、ほぼリアルタイムのパフォーマンス メトリックの収集に使用される .NET Core API です。</span><span class="sxs-lookup"><span data-stu-id="37bd8-105">EventCounters are .NET Core APIs used for lightweight, cross-platform, and near real-time performance metric collection.</span></span> <span data-ttu-id="37bd8-106">EventCounters は、Windows 上の .NET Framework の "パフォーマンス カウンター" に代わるクロスプラットフォームとして追加されました。</span><span class="sxs-lookup"><span data-stu-id="37bd8-106">EventCounters were added as a cross-platform alternative to the "performance counters" of the .NET Framework on Windows.</span></span> <span data-ttu-id="37bd8-107">この記事では、EventCounters の概要とその実装方法および使用方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-107">In this article you'll learn what EventCounters are, how to implement them, and how to consume them.</span></span>

<span data-ttu-id="37bd8-108">.Net Core ランタイムといくつかの .NET ライブラリにより、.NET Core 3.0 以降の EventCounters が使用され、基本的な診断情報が公開されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-108">The .NET Core runtime and a few .NET libraries publish basic diagnostics information using EventCounters starting in .NET Core 3.0.</span></span> <span data-ttu-id="37bd8-109">.NET ランタイムによって提供される EventCounters とは別に、独自の EventCounters を実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-109">Apart from the EventCounters that are provided by the .NET runtime, you may choose to implement your own EventCounters.</span></span> <span data-ttu-id="37bd8-110">EventCounters を使用して、さまざまなメトリックを追跡できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-110">EventCounters can be used to track various metrics.</span></span>

<span data-ttu-id="37bd8-111">EventCounters は <xref:System.Diagnostics.Tracing.EventSource> の一部として存在し、定期的にリスナー ツールに自動的にプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-111">EventCounters live as a part of an <xref:System.Diagnostics.Tracing.EventSource>, and are automatically pushed to listener tools on a regular basis.</span></span> <span data-ttu-id="37bd8-112"><xref:System.Diagnostics.Tracing.EventSource> の他のすべてのイベントと同様に、<xref:System.Diagnostics.Tracing.EventListener> と [EventPipe](./eventpipe.md) を介してインプロセスとアウトプロセスの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-112">Like all other events on an <xref:System.Diagnostics.Tracing.EventSource>, they can be consumed both in-proc and out-of-proc via <xref:System.Diagnostics.Tracing.EventListener> and [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="37bd8-113">この記事では、EventCounters のクロスプラットフォーム機能に焦点を当てています。PerfView と ETW (Event Trace for Windows) は意図的に除外していますが、両方とも EventCounters で使用できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-113">This article focuses on the cross-platform capabilities of EventCounters, and intentionally excludes PerfView and ETW (Event Tracing for Windows) - although both can be used with EventCounters.</span></span>

![EventCounters のインプロセスとアウトプロセスの図のイメージ](media/event-counters.svg)

[!INCLUDE [available-counters](includes/available-counters.md)]

## <a name="eventcounter-api-overview"></a><span data-ttu-id="37bd8-115">EventCounter API の概要</span><span class="sxs-lookup"><span data-stu-id="37bd8-115">EventCounter API overview</span></span>

<span data-ttu-id="37bd8-116">カウンターには主に 2 つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-116">There are two primary categories of counters.</span></span> <span data-ttu-id="37bd8-117">一部のカウンターは、例外の合計数、GC の合計数、要求の合計数などの "比率" の値用です。</span><span class="sxs-lookup"><span data-stu-id="37bd8-117">Some counters are for "rate" values, such as total number of exceptions, total number of GCs, and total number of requests.</span></span> <span data-ttu-id="37bd8-118">その他のカウンターは、ヒープ使用率、CPU 使用率、ワーキング セット サイズなどの "スナップショット" の値です。</span><span class="sxs-lookup"><span data-stu-id="37bd8-118">Other counters are "snapshot" values, such as heap usage, CPU usage, and working set size.</span></span> <span data-ttu-id="37bd8-119">これらのカウンターの各カテゴリ内には、値の取得方法によって異なる 2 種類のカウンターがあります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-119">Within each of these categories of counters, there are two types of counters that vary by how they get their value.</span></span> <span data-ttu-id="37bd8-120">ポーリング カウンターによって、コールバックを介して値が取得され、ポーリング以外のカウンターの値は、カウンター インスタンスで直接設定されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-120">Polling counters retrieve their value via a callback, and non-polling counters have their values directly set on the counter instance.</span></span>

<span data-ttu-id="37bd8-121">これらのカウンターは、次の実装によって表されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-121">The counters are represented by the following implementations:</span></span>

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

<span data-ttu-id="37bd8-122">イベント リスナーによって、測定間隔の長さが指定されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-122">An event listener specifies how long measurement intervals are.</span></span> <span data-ttu-id="37bd8-123">各間隔の最後に、各カウンターのリスナーに値が送信されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-123">At the end of each interval a value is transmitted to the listener for each counter.</span></span> <span data-ttu-id="37bd8-124">カウンターの実装によって、各間隔の値を生成するために使用される API と計算が決まります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-124">The implementations of a counter determine what APIs and calculations are used to produce the value each interval.</span></span>

1. <span data-ttu-id="37bd8-125"><xref:System.Diagnostics.Tracing.EventCounter> によって、値のセットが記録されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-125">The <xref:System.Diagnostics.Tracing.EventCounter> records a set of values.</span></span> <span data-ttu-id="37bd8-126"><xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> メソッドによって、新しい値がセットに追加されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-126">The <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> method adds a new value to the set.</span></span> <span data-ttu-id="37bd8-127">各間隔では、最小値、最大値、平均値など、セットの統計概要が計算されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-127">With each interval, a statistical summary for the set is computed, such as the min, max, and mean.</span></span> <span data-ttu-id="37bd8-128">[dotnet-counters](dotnet-counters.md) ツールによって、常に平均値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-128">The [dotnet-counters](dotnet-counters.md) tool will always display the mean value.</span></span> <span data-ttu-id="37bd8-129"><xref:System.Diagnostics.Tracing.EventCounter> は、個別の操作セットを記述する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-129">The <xref:System.Diagnostics.Tracing.EventCounter> is useful to describe a discrete set of operations.</span></span> <span data-ttu-id="37bd8-130">一般的な用途には、最近の IO 操作の平均サイズ (バイト単位) や、金融取引セットの平均額の監視が含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-130">Common usage may include monitoring the average size in bytes of recent IO operations, or the average monetary value of a set of financial transactions.</span></span>

1. <span data-ttu-id="37bd8-131"><xref:System.Diagnostics.Tracing.IncrementingEventCounter> によって、各時間間隔の累計が記録されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-131">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> records a running total for each time interval.</span></span> <span data-ttu-id="37bd8-132"><xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> メソッドによって、合計に加算されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-132">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> method adds to the total.</span></span> <span data-ttu-id="37bd8-133">たとえば、値が `1`、`2`、および `5` に指定され、1 つの間隔で `Increment()` が 3 回呼び出された場合、`8` の累計は、この間隔のカウンター値として報告されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-133">For example, if `Increment()` is called three times during one interval with values `1`, `2`, and `5`, then the running total of `8` will be reported as the counter value for this interval.</span></span> <span data-ttu-id="37bd8-134">[dotnet-counters](dotnet-counters.md) ツールにより、記録された合計/時間として比率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-134">The [dotnet-counters](dotnet-counters.md) tool will display the rate as the recorded total / time.</span></span> <span data-ttu-id="37bd8-135"><xref:System.Diagnostics.Tracing.IncrementingEventCounter> は、1 秒あたりに処理された要求の数など、アクションの発生頻度を測定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-135">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> is useful to measure how frequently an action is occurring, such as the number of requests processed per second.</span></span>

1. <span data-ttu-id="37bd8-136"><xref:System.Diagnostics.Tracing.PollingCounter> によってコールバックが使用され、報告される値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-136">The <xref:System.Diagnostics.Tracing.PollingCounter> uses a callback to determine the value that is reported.</span></span> <span data-ttu-id="37bd8-137">各時間間隔で、ユーザーが指定したコールバック関数が呼び出され、戻り値がカウンター値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-137">With each time interval, the user provided callback function is invoked and the return value is used as the counter value.</span></span> <span data-ttu-id="37bd8-138"><xref:System.Diagnostics.Tracing.PollingCounter> を使用すると、ディスク上の現在の空きバイト数を取得するなど、外部ソースからのメトリックに対してクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-138">A <xref:System.Diagnostics.Tracing.PollingCounter> can be used to query a metric from an external source, for example getting the current free bytes on a disk.</span></span> <span data-ttu-id="37bd8-139">また、アプリケーションで要求時に計算できるカスタム統計を報告するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-139">It can also be used to report custom statistics that can be computed on demand by an application.</span></span> <span data-ttu-id="37bd8-140">たとえば、最近の要求待機時間の 95 パーセンタイルや、キャッシュの現在のヒットまたはミス率の報告などです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-140">Examples include reporting the 95th percentile of recent request latencies, or the current hit or miss ratio of a cache.</span></span>

1. <span data-ttu-id="37bd8-141"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter> によってコールバックが使用され、報告される増分値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-141">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses a callback to determine the reported increment value.</span></span> <span data-ttu-id="37bd8-142">各時間間隔で、コールバックが呼び出され、現在の呼び出しと最後の呼び出しの差が報告される値となります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-142">With each time interval, the callback is invoked, and then the difference between the current invocation, and the last invocation is the reported value.</span></span> <span data-ttu-id="37bd8-143">[dotnet-counters](dotnet-counters.md) ツールにより、比率 (報告された値/時間) として常に差が表示されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-143">The [dotnet-counters](dotnet-counters.md) tool will always display the difference as a rate, the reported value / time.</span></span> <span data-ttu-id="37bd8-144">このカウンターは、発生のたびに API を呼び出すことができない場合に便利ですが、発生の合計回数に対してクエリを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-144">This counter is useful when it isn't feasible to call an API on each occurrence, but it's possible to query the total number of occurrences.</span></span> <span data-ttu-id="37bd8-145">たとえば、バイトが書き込まれるたびに通知しなくても、1 秒あたりにファイルに書き込まれたバイト数を報告することができます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-145">For example, you could report the number of bytes written to a file per second, even without a notification each time a byte is written.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="37bd8-146">EventSource を実装する</span><span class="sxs-lookup"><span data-stu-id="37bd8-146">Implement an EventSource</span></span>

<span data-ttu-id="37bd8-147">次のコードにより、名前付きの `"Sample.EventCounter.Minimal"` プロバイダーとして公開されるサンプルの <xref:System.Diagnostics.Tracing.EventSource> が実装されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-147">The following code implements a sample <xref:System.Diagnostics.Tracing.EventSource> exposed as the named `"Sample.EventCounter.Minimal"` provider.</span></span> <span data-ttu-id="37bd8-148">このソースには、要求の処理時間を表す <xref:System.Diagnostics.Tracing.EventCounter> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="37bd8-148">This source contains an <xref:System.Diagnostics.Tracing.EventCounter> representing request processing time.</span></span> <span data-ttu-id="37bd8-149">このようなカウンターには、名前 (つまり、ソースのその一意の ID) と表示名があり、両方とも [dotnet-counter](dotnet-counters.md) などのリスナー ツールで使用されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-149">Such a counter has a name (that is, its unique ID in the source) and a display name, both used by listener tools such as [dotnet-counter](dotnet-counters.md).</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="37bd8-150">監視できる .NET プロセスの一覧を表示するには、`dotnet-counters ps` を使用します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-150">You use `dotnet-counters ps` to display a list of .NET processes that can be monitored:</span></span>

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

<span data-ttu-id="37bd8-151">カウンターの監視を開始するには、<xref:System.Diagnostics.Tracing.EventSource> の名前を `--counters` オプションに渡します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-151">Pass the <xref:System.Diagnostics.Tracing.EventSource> name to the `--counters` option to start monitoring your counter:</span></span>

```console
dotnet-counters monitor --process-id 1400180 --counters Sample.EventCounter.Minimal
```

<span data-ttu-id="37bd8-152">次の例は監視出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="37bd8-152">The following example shows monitor output:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

<span data-ttu-id="37bd8-153">監視コマンドを停止するには、<kbd>q</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-153">Press <kbd>q</kbd> to stop the monitoring command.</span></span>

#### <a name="conditional-counters"></a><span data-ttu-id="37bd8-154">条件付きカウンター</span><span class="sxs-lookup"><span data-stu-id="37bd8-154">Conditional counters</span></span>

<span data-ttu-id="37bd8-155"><xref:System.Diagnostics.Tracing.EventSource> を実装する場合、<xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> の値として `EventCommand.Enable` を指定して、<xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> メソッドが呼び出されると、格納先のカウンターを条件付きでインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-155">When implementing an <xref:System.Diagnostics.Tracing.EventSource>, the containing counters can be conditionally instantiated when the <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> method is called with a <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> value of `EventCommand.Enable`.</span></span> <span data-ttu-id="37bd8-156">`null` である場合にのみ、カウンター インスタンスを安全にインスタンス化するには、[null 合体代入演算子](../../csharp/language-reference/operators/null-coalescing-operator.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-156">To safely instantiate a counter instance only if it is `null`, use the [null-coalescing assignment operator](../../csharp/language-reference/operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="37bd8-157">さらに、カスタム メソッドで <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> メソッドを評価して、現在のイベント ソースが有効になっているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-157">Additionally, custom methods can evaluate the <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> method to determine whether or not the current event source is enabled.</span></span>

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> <span data-ttu-id="37bd8-158">条件付きカウンターは、条件付きでインスタンス化 (マイクロ最適化) されるカウンターです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-158">Conditional counters are counters that are conditionally instantiated, a micro-optimization.</span></span> <span data-ttu-id="37bd8-159">ランタイムにより、わずかな時間を節約するために、通常はカウンターが使用されないシナリオでこのパターンが採用されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-159">The runtime adopts this pattern for scenarios where counters are normally not used, to save a fraction of a millisecond.</span></span>

### <a name="net-core-runtime-example-counters"></a><span data-ttu-id="37bd8-160">.NET Core ランタイムのカウンター例</span><span class="sxs-lookup"><span data-stu-id="37bd8-160">.NET Core runtime example counters</span></span>

<span data-ttu-id="37bd8-161">.NET Core ランタイムには、多くの優れた実装例があります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-161">There are many great example implementations in the .NET Core runtime.</span></span> <span data-ttu-id="37bd8-162">アプリケーションのワーキング セット サイズを追跡するカウンターのランタイム実装を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-162">Here is the runtime implementation for the counter that tracks the working set size of the application.</span></span>

```csharp
var workingSetCounter = new PollingCounter(
    "working-set",
    this,
    () => (double)(Environment.WorkingSet / 1_000_000))
{
    DisplayName = "Working Set",
    DisplayUnits = "MB"
};
```

<span data-ttu-id="37bd8-163"><xref:System.Diagnostics.Tracing.PollingCounter> により、アプリのプロセス (ワーキング セット) にマップされる物理メモリの現在の量が報告されます。これは、ある時点のメトリックがキャプチャされるためです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-163">The <xref:System.Diagnostics.Tracing.PollingCounter> reports the current amount of physical memory mapped to the process (working set) of the app, since it captures a metric at a moment in time.</span></span> <span data-ttu-id="37bd8-164">値をポーリングするためのコールバックは、指定されたラムダ式であり、単に <xref:System.Environment.WorkingSet?displayProperty=fullName> API の呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-164">The callback for polling a value is the provided lambda expression, which is just a call to the <xref:System.Environment.WorkingSet?displayProperty=fullName> API.</span></span> <span data-ttu-id="37bd8-165"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> および <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> は、カウンターのコンシューマー側でより明確に値を表示するのに役立つように設定できる省略可能なプロパティです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-165"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> and <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> are optional properties that can be set to help the consumer side of the counter to display the value more clearly.</span></span> <span data-ttu-id="37bd8-166">たとえば、よりわかりやすいバージョンのカウンター名を表示するために、[dotnet-counters](dotnet-counters.md) によってこれらのプロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-166">For example, [dotnet-counters](dotnet-counters.md) uses these properties to display the more display-friendly version of the counter names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="37bd8-167">`DisplayName` のプロパティはローカライズされません。</span><span class="sxs-lookup"><span data-stu-id="37bd8-167">The `DisplayName` properties are not localized.</span></span>

<span data-ttu-id="37bd8-168"><xref:System.Diagnostics.Tracing.PollingCounter>、および <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> では、他に何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="37bd8-168">For the <xref:System.Diagnostics.Tracing.PollingCounter>, and the <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>, nothing else needs to be done.</span></span> <span data-ttu-id="37bd8-169">いずれの場合も、コンシューマーによって要求された間隔で値自体がポーリングされます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-169">They both poll the values themselves at an interval requested by the consumer.</span></span>

<span data-ttu-id="37bd8-170"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter> を使用して実装されたランタイム カウンターの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-170">Here is an example of a runtime counter implemented using <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>.</span></span>

```csharp
var monitorContentionCounter = new IncrementingPollingCounter(
    "monitor-lock-contention-count",
    this,
    () => Monitor.LockContentionCount
)
{
    DisplayName = "Monitor Lock Contention Count",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

<span data-ttu-id="37bd8-171">ロック競合の合計数の増加を報告するために、<xref:System.Diagnostics.Tracing.IncrementingPollingCounter> によって <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API が使用されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-171">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses the <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API to report the increment of the total lock contention count.</span></span> <span data-ttu-id="37bd8-172"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> プロパティは省略可能ですが、これを使用すると、カウンターが最適に表示される時間間隔に関するヒントを提供できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-172">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> property is optional, but when used it can provide a hint for what time interval the counter is best displayed at.</span></span> <span data-ttu-id="37bd8-173">たとえば、ロック競合数は、"_1 秒あたりの数_" として最適に表示されるので、その <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> は 1 秒に設定されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-173">For example, the lock contention count is best displayed as _count per second_, so its <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is set to one second.</span></span> <span data-ttu-id="37bd8-174">表示率は、さまざまな種類の比率カウンターに合わせて調整できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-174">The display rate can be adjusted for different types of rate counters.</span></span>

> [!NOTE]
> <span data-ttu-id="37bd8-175"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> は [dotnet-counters](dotnet-counters.md) によって使用 "_されません_"。また、それを使用するためにイベント リスナーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="37bd8-175">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is _not_ used by [dotnet-counters](dotnet-counters.md), and event listeners are not required to use it.</span></span>

<span data-ttu-id="37bd8-176">[.NET ランタイム](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) リポジトリで参照として使用するカウンター実装は他にもあります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-176">There are more counter implementations to use as a reference in the [.NET runtime](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) repo.</span></span>

## <a name="concurrency"></a><span data-ttu-id="37bd8-177">コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="37bd8-177">Concurrency</span></span>

> [!TIP]
> <span data-ttu-id="37bd8-178">EventCounters API によるスレッド セーフは保証されません。</span><span class="sxs-lookup"><span data-stu-id="37bd8-178">The EventCounters API does not guarantee thread safety.</span></span> <span data-ttu-id="37bd8-179"><xref:System.Diagnostics.Tracing.PollingCounter> または <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> インスタンスに渡された委任が複数のスレッドによって呼び出された場合、委任のスレッドセーフを保証するのはお客様の責任となります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-179">When the delegates passed to <xref:System.Diagnostics.Tracing.PollingCounter> or <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> instances are called by multiple threads, it's your responsibility to guarantee the delegates' thread-safety.</span></span>

<span data-ttu-id="37bd8-180">たとえば、要求を追跡する以下の <xref:System.Diagnostics.Tracing.EventSource> について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-180">For example, consider the following <xref:System.Diagnostics.Tracing.EventSource> to keep track of requests.</span></span>

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

<span data-ttu-id="37bd8-181">`AddRequest()` メソッドは要求ハンドラーから呼び出すことができ、カウンターのコンシューマーによって指定された間隔で、`RequestRateCounter` により値がポーリングされます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-181">The `AddRequest()` method can be called from a request handler, and the `RequestRateCounter` polls the value at the interval specified by the consumer of the counter.</span></span> <span data-ttu-id="37bd8-182">しかし、`AddRequest()` メソッドは、一度に複数のスレッドによって呼び出すことができ、`_requestCount` で競合状態が発生します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-182">However, the `AddRequest()` method can be called by multiple threads at once, putting a race condition on `_requestCount`.</span></span> <span data-ttu-id="37bd8-183">`_requestCount` を増分させるスレッドセーフな別の方法は、<xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> を使用することです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-183">A thread-safe alternative way to increment the `_requestCount` is to use <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span>

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

<span data-ttu-id="37bd8-184">(32 ビット アーキテクチャでの) `long`-field `_requestCount` の読み取りの欠落を防ぐには、<xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-184">To prevent torn reads (on 32-bit architectures) of the `long`-field `_requestCount` use <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType>.</span></span>

```csharp
_requestRateCounter = new IncrementingPollingCounter("request-rate", this, () => Interlocked.Read(ref _requestCount))
{
    DisplayName = "Request Rate",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

## <a name="consume-eventcounters"></a><span data-ttu-id="37bd8-185">EventCounters を使用する</span><span class="sxs-lookup"><span data-stu-id="37bd8-185">Consume EventCounters</span></span>

<span data-ttu-id="37bd8-186">EventCounters を使用する場合、インプロセスとアウトプロセスという 2 つの主な方法があります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-186">There are two primary ways of consuming EventCounters, either in-proc, or out-of-proc.</span></span> <span data-ttu-id="37bd8-187">EventCounters の使用は、さまざまな使用テクノロジの 3 つの層に分類できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-187">The consumption of EventCounters can be distinguished into three layers of various consuming technologies.</span></span>

- <span data-ttu-id="37bd8-188">ETW または EventPipe を介した生のストリームでのイベントの転送:</span><span class="sxs-lookup"><span data-stu-id="37bd8-188">Transporting events in a raw stream via ETW or EventPipe:</span></span>
  - <span data-ttu-id="37bd8-189">ETW API は Windows OS に付属しています。EventPipe には [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console)、または診断 [IPC プロトコル](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)としてアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-189">ETW APIs come with the Windows OS, and EventPipe is accessible as a [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console), or the diagnostic [IPC protocol](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).</span></span>
- <span data-ttu-id="37bd8-190">バイナリ イベント ストリームのイベントへのデコード:</span><span class="sxs-lookup"><span data-stu-id="37bd8-190">Decoding the binary event stream into events:</span></span>
  - <span data-ttu-id="37bd8-191">[TraceEvent ライブラリ](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent)により、ETW と EventPipe の両方のストリーム形式が処理されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-191">The [TraceEvent library](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) handles both ETW and EventPipe stream formats.</span></span>
- <span data-ttu-id="37bd8-192">コマンド ラインと GUI ツール:</span><span class="sxs-lookup"><span data-stu-id="37bd8-192">Command-line and GUI tools:</span></span>
  - <span data-ttu-id="37bd8-193">PerfView (ETW または EventPipe)、dotnet-counters (EventPipe のみ)、dotnet-monitor (EventPipe のみ) などのツール。</span><span class="sxs-lookup"><span data-stu-id="37bd8-193">Tools like PerfView (ETW or EventPipe), dotnet-counters (EventPipe only), and dotnet-monitor (EventPipe only).</span></span>

### <a name="consume-out-of-proc"></a><span data-ttu-id="37bd8-194">アウトプロセスで使用する</span><span class="sxs-lookup"><span data-stu-id="37bd8-194">Consume out-of-proc</span></span>

<span data-ttu-id="37bd8-195">EventCounters をアウトプロセスで使用することは、非常に一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="37bd8-195">Consuming EventCounters out-of-proc is a very common approach.</span></span> <span data-ttu-id="37bd8-196">[dotnet-counters](dotnet-counters.md) を使って、EventPipe を介してクロスプラットフォーム方式でそれらを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-196">You can use [dotnet-counters](dotnet-counters.md) to consume them in a cross-platform manner via an EventPipe.</span></span> <span data-ttu-id="37bd8-197">`dotnet-counters` ツールは、カウンターの値を監視するために使用できるクロスプラットフォームの dotnet CLI グローバル ツールです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-197">The `dotnet-counters` tool is a cross-platform dotnet CLI global tool that can be used to monitor the counter values.</span></span> <span data-ttu-id="37bd8-198">`dotnet-counters` を使用してカウンターを監視する方法を確認する場合は、「[dotnet-counters](dotnet-counters.md)」を参照するか、[EventCounters を使用するパフォーマンスの測定](event-counter-perf.md)に関するチュートリアルを実行してください。</span><span class="sxs-lookup"><span data-stu-id="37bd8-198">To find out how to use `dotnet-counters` to monitor your counters, see [dotnet-counters](dotnet-counters.md), or work through the [Measure performance using EventCounters](event-counter-perf.md) tutorial.</span></span>

#### <a name="dotnet-trace"></a><span data-ttu-id="37bd8-199">dotnet-トレース</span><span class="sxs-lookup"><span data-stu-id="37bd8-199">dotnet-trace</span></span>

<span data-ttu-id="37bd8-200">`dotnet-trace` ツールを使って、EventPipe を介してカウンター データを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-200">The `dotnet-trace` tool can be used to consume the counter data through an EventPipe.</span></span> <span data-ttu-id="37bd8-201">カウンター データを収集するために `dotnet-trace` を使用する例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-201">Here is an example using `dotnet-trace` to collect counter data.</span></span>

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

<span data-ttu-id="37bd8-202">経時的なカウンター値を収集する方法の詳細については、[dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37bd8-202">For more information on how to collect counter values over time, see the [dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) documentation.</span></span>

#### <a name="azure-application-insights"></a><span data-ttu-id="37bd8-203">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="37bd8-203">Azure Application Insights</span></span>

<span data-ttu-id="37bd8-204">EventCounters は Azure Monitor、つまり、Azure Application Insights で使用できます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-204">EventCounters can be consumed by Azure Monitor, specifically Azure Application Insights.</span></span> <span data-ttu-id="37bd8-205">カウンターを追加したり、削除したりすることができます。また、カスタム カウンターや既知のカウンターを自由に指定することができます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-205">Counters can be added and removed, and you're free to specify custom counters, or well-known counters.</span></span> <span data-ttu-id="37bd8-206">詳細については、「[収集されるカウンターのカスタマイズ](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37bd8-206">For more information, see [Customizing counters to be collected](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).</span></span>

#### <a name="dotnet-monitor"></a><span data-ttu-id="37bd8-207">dotnet-monitor</span><span class="sxs-lookup"><span data-stu-id="37bd8-207">dotnet-monitor</span></span>

<span data-ttu-id="37bd8-208">`dotnet-monitor` ツールは、.NET プロセスでの診断情報へのアクセスを容易にする実験用のツールです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-208">The `dotnet-monitor` tool is an experimental tool that makes it easier to get access to diagnostics information in a .NET process.</span></span> <span data-ttu-id="37bd8-209">このツールは、すべての診断ツールのスーパーセットとして機能します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-209">The tool serves as a superset of all diagnostics tools.</span></span> <span data-ttu-id="37bd8-210">トレースに加えて、メトリックの監視、メモリ ダンプの収集、および GC ダンプの収集を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-210">In addition to traces, it can monitor metrics, collect memory dumps, and collect GC dumps.</span></span> <span data-ttu-id="37bd8-211">CLI ツールと Docker イメージの両方として配布されます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-211">It's distributed as both a CLI tool and a docker image.</span></span> <span data-ttu-id="37bd8-212">これによって REST API が公開され、診断アーティファクトの収集は REST 呼び出しを介して行われます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-212">It exposes a REST API, and the collection of diagnostic artifacts occurs through REST calls.</span></span>

<span data-ttu-id="37bd8-213">詳細については、「[実験用のツール、dotnet-monitor の概要](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37bd8-213">For more information, see [Introducing dotnet-monitor, an experimental tool](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).</span></span>

### <a name="consume-in-proc"></a><span data-ttu-id="37bd8-214">インプロセスで使用する</span><span class="sxs-lookup"><span data-stu-id="37bd8-214">Consume in-proc</span></span>

<span data-ttu-id="37bd8-215"><xref:System.Diagnostics.Tracing.EventListener> API を介して、カウンター値を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-215">You can consume the counter values via the <xref:System.Diagnostics.Tracing.EventListener> API.</span></span> <span data-ttu-id="37bd8-216"><xref:System.Diagnostics.Tracing.EventListener> は、アプリケーション内の <xref:System.Diagnostics.Tracing.EventSource> のすべてのインスタンスによって書き込まれるすべてのイベントを使用するインプロセスの方法です。</span><span class="sxs-lookup"><span data-stu-id="37bd8-216">An <xref:System.Diagnostics.Tracing.EventListener> is an in-proc way of consuming any events written by all instances of an <xref:System.Diagnostics.Tracing.EventSource> in your application.</span></span> <span data-ttu-id="37bd8-217">`EventListener` API の使用方法の詳細については、<xref:System.Diagnostics.Tracing.EventListener> に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37bd8-217">For more information on how to use the `EventListener` API, see <xref:System.Diagnostics.Tracing.EventListener>.</span></span>

<span data-ttu-id="37bd8-218">まず、カウンター値を生成する <xref:System.Diagnostics.Tracing.EventSource> を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-218">First, the <xref:System.Diagnostics.Tracing.EventSource> that produces the counter value needs to be enabled.</span></span> <span data-ttu-id="37bd8-219"><xref:System.Diagnostics.Tracing.EventSource> が作成されたときに通知を受け取るように <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> メソッドをオーバーライドします。これが EventCounters に適切な <xref:System.Diagnostics.Tracing.EventSource> である場合は、それに対して <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="37bd8-219">Override the <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> method to get a notification when an <xref:System.Diagnostics.Tracing.EventSource> is created, and if this is the correct <xref:System.Diagnostics.Tracing.EventSource> with your EventCounters, then you can call <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> on it.</span></span> <span data-ttu-id="37bd8-220">オーバーライドの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="37bd8-220">Here is an example override:</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="16-27":::

#### <a name="sample-code"></a><span data-ttu-id="37bd8-221">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="37bd8-221">Sample code</span></span>

<span data-ttu-id="37bd8-222">以下は、内部カウンター (`System.Runtime`) を一定の間隔で公開するために、.NET ランタイムの <xref:System.Diagnostics.Tracing.EventSource> からすべてのカウンターの名前と値を出力する <xref:System.Diagnostics.Tracing.EventListener> クラスのサンプルです。</span><span class="sxs-lookup"><span data-stu-id="37bd8-222">Here is a sample <xref:System.Diagnostics.Tracing.EventListener> class that prints out all the counter names and values from the .NET runtime's <xref:System.Diagnostics.Tracing.EventSource>, for publishing its internal counters (`System.Runtime`) at some interval.</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

<span data-ttu-id="37bd8-223">前述のように、<xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A> を呼び出す場合は、`filterPayload` 引数に `"EventCounterIntervalSec"` 引数が設定されていることを確認する "_必要があります_"。</span><span class="sxs-lookup"><span data-stu-id="37bd8-223">As shown above, you _must_ make sure the `"EventCounterIntervalSec"` argument is set in the `filterPayload` argument when calling <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A>.</span></span> <span data-ttu-id="37bd8-224">そうしないと、カウンターによってフラッシュする必要がある間隔が把握されないため、値をフラッシュできなくなります。</span><span class="sxs-lookup"><span data-stu-id="37bd8-224">Otherwise the counters will not be able to flush out values since it doesn't know at which interval it should be getting flushed out.</span></span>

## <a name="see-also"></a><span data-ttu-id="37bd8-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="37bd8-225">See also</span></span>

- [<span data-ttu-id="37bd8-226">dotnet-カウンター</span><span class="sxs-lookup"><span data-stu-id="37bd8-226">dotnet-counters</span></span>](dotnet-counters.md)
- [<span data-ttu-id="37bd8-227">dotnet-トレース</span><span class="sxs-lookup"><span data-stu-id="37bd8-227">dotnet-trace</span></span>](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
