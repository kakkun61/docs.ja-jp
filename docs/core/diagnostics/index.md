---
title: 診断ツールの概要 - .NET Core
description: .NET Core アプリケーションの診断に使用できるツールと手法の概要。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: d468ec5b9cc050cc54f6c53f8a4ea4531f8b58f5
ms.sourcegitcommit: 35ca2255c6c86968eaef9e3a251c9739ce8e4288
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2020
ms.locfileid: "97753615"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="d91e6-103">.NET Core で使用できる診断ツール</span><span class="sxs-lookup"><span data-stu-id="d91e6-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="d91e6-104">ソフトウェアは期待どおりに動作するとは限りませんが、.NET Core には、そのような問題を迅速かつ効果的に診断するために役立つツールと API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d91e6-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="d91e6-105">この記事は、必要な各種ツールを見つけるために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="d91e6-106">マネージド デバッガー</span><span class="sxs-lookup"><span data-stu-id="d91e6-106">Managed debuggers</span></span>

<span data-ttu-id="d91e6-107">[マネージド デバッガー](managed-debuggers.md)を使用すると、プログラムと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="d91e6-108">一時停止、段階的な実行、調査、および再開によって、コードの動作を分析できます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="d91e6-109">デバッガーは、簡単に再現できる機能の問題を診断するための最初の選択肢です。</span><span class="sxs-lookup"><span data-stu-id="d91e6-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="d91e6-110">ログとトレース</span><span class="sxs-lookup"><span data-stu-id="d91e6-110">Logging and tracing</span></span>

<span data-ttu-id="d91e6-111">[ログとトレース](logging-tracing.md)は、関連する手法です。</span><span class="sxs-lookup"><span data-stu-id="d91e6-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="d91e6-112">ログ ファイルを作成するためのコードのインストルメント化を指します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="d91e6-113">ファイルには、プログラムの機能の詳細が記録されます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-113">The files record the details of what a program does.</span></span> <span data-ttu-id="d91e6-114">これらの詳細は、複雑度の高い問題を診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="d91e6-115">タイム スタンプと組み合わせると、これらの手法はパフォーマンスの調査にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="metrics"></a><span data-ttu-id="d91e6-116">メトリック</span><span class="sxs-lookup"><span data-stu-id="d91e6-116">Metrics</span></span>

<span data-ttu-id="d91e6-117">[EventCounters](event-counters.md) を使用すると、パフォーマンスの問題を特定して監視するためのメトリックを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-117">[EventCounters](event-counters.md) allows you to write metrics to identify and monitor performance issues.</span></span> <span data-ttu-id="d91e6-118">メトリックを使用すると、トレースと比較してパフォーマンスのオーバーヘッドが低くなるため、常時接続のパフォーマンスの監視に適しています。</span><span class="sxs-lookup"><span data-stu-id="d91e6-118">Metrics incur lower performance overhead compared to tracing, making it more suitable for an always-on performance monitoring.</span></span> <span data-ttu-id="d91e6-119">.NET ランタイムとライブラリでは、いくつかの[既知の EventCounters](available-counters.md) を発行して、同様に監視することができます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-119">The .NET runtime and libraries publish several [well-known EventCounters](available-counters.md) that you can monitor as well.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="d91e6-120">単体テスト</span><span class="sxs-lookup"><span data-stu-id="d91e6-120">Unit testing</span></span>

<span data-ttu-id="d91e6-121">[単体テスト](../testing/index.md)は、高品質のソフトウェアを継続的に統合して展開するための重要なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="d91e6-121">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="d91e6-122">単体テストは、何かを中断するときに早期警告を提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d91e6-122">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="d91e6-123">ダンプ</span><span class="sxs-lookup"><span data-stu-id="d91e6-123">Dumps</span></span>

<span data-ttu-id="d91e6-124">[ダンプ](./dumps.md)は、作成時のプロセスのスナップショットを含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="d91e6-124">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="d91e6-125">これらは、デバッグのためにアプリケーションの状態を調べるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-125">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="symbols"></a><span data-ttu-id="d91e6-126">シンボル</span><span class="sxs-lookup"><span data-stu-id="d91e6-126">Symbols</span></span>

<span data-ttu-id="d91e6-127">シンボルは、デバッグやその他の診断ツールの基本的な要件です。</span><span class="sxs-lookup"><span data-stu-id="d91e6-127">Symbols are a fundamental requirement for debugging and other diagnostic tools.</span></span> <span data-ttu-id="d91e6-128">シンボル ファイルの内容は、言語、コンパイラ、およびプラットフォームによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d91e6-128">The contents of symbol files vary between languages, compilers, and platforms.</span></span> <span data-ttu-id="d91e6-129">非常に高いレベルのシンボルは、ソース コードとコンパイラによって生成されるバイナリとの間のマッピングです。</span><span class="sxs-lookup"><span data-stu-id="d91e6-129">At a very high level symbols are a mapping between the source code and the binary produced by the compiler.</span></span> <span data-ttu-id="d91e6-130">これらのマッピングは、[Visual Studio](/visualstudio/debugger/what-is-debugging) や [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging) などの診断ツールで、行番号の情報やローカル変数の名前などを提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-130">These mappings are used to provide things like line number information and names of your local variables in diagnostics tools such as [Visual Studio](/visualstudio/debugger/what-is-debugging) and [Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging).</span></span>  <span data-ttu-id="d91e6-131">次のリンクには、Windows の[シンボル](/windows/win32/dxtecharts/debugging-with-symbols)の詳細な説明が含まれていますが、他のプラットフォームにも多くの概念が当てはまります。</span><span class="sxs-lookup"><span data-stu-id="d91e6-131">The following link contains a detailed explanation of [symbols](/windows/win32/dxtecharts/debugging-with-symbols) for Windows, although many of the concepts apply to other platforms as well.</span></span> <span data-ttu-id="d91e6-132">[.NET ポータブル シンボル](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md)には、Windows PDB と同様の "PDB" ファイル拡張子が付いていますが、Windows PDB 形式と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="d91e6-132">[.NET portable symbols](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) have a "PDB" file extension similar to Windows PDB, though are not compatible with the Windows PDB format.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="d91e6-133">コンテナーでの診断の収集</span><span class="sxs-lookup"><span data-stu-id="d91e6-133">Collect diagnostics in containers</span></span>

<span data-ttu-id="d91e6-134">コンテナー化されていない Linux 環境で使用されているのと同じ診断ツールを使用して、[コンテナーで診断を収集](diagnostics-in-containers.md)することもできます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-134">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="d91e6-135">Docker コンテナーでツールを動作させるために必要ないくつかの使用方法が変更されています。</span><span class="sxs-lookup"><span data-stu-id="d91e6-135">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="d91e6-136">.NET Core 診断グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="d91e6-136">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="d91e6-137">dotnet-カウンター</span><span class="sxs-lookup"><span data-stu-id="d91e6-137">dotnet-counters</span></span>

<span data-ttu-id="d91e6-138">[dotnet-カウンター](dotnet-counters.md)は、第 1 レベルの正常性監視とパフォーマンス調査のためのパフォーマンス監視ツールです。</span><span class="sxs-lookup"><span data-stu-id="d91e6-138">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="d91e6-139"><xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-139">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="d91e6-140">たとえば、CPU 使用率や、.NET Core アプリケーションでスローされる例外の発生率などをすばやく監視できます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-140">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="d91e6-141">dotnet-ダンプ</span><span class="sxs-lookup"><span data-stu-id="d91e6-141">dotnet-dump</span></span>

<span data-ttu-id="d91e6-142">[dotnet-ダンプ](dotnet-dump.md) ツールは、ネイティブ デバッガーを使用せずに Windows と Linux のコア ダンプを収集して分析する方法です。</span><span class="sxs-lookup"><span data-stu-id="d91e6-142">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="d91e6-143">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="d91e6-143">dotnet-gcdump</span></span>

<span data-ttu-id="d91e6-144">[dotnet-gcdump](dotnet-gcdump.md) ツールは、ライブ .NET プロセスの GC (ガベージ コレクター) ダンプを収集する手段です。</span><span class="sxs-lookup"><span data-stu-id="d91e6-144">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="d91e6-145">dotnet-トレース</span><span class="sxs-lookup"><span data-stu-id="d91e6-145">dotnet-trace</span></span>

<span data-ttu-id="d91e6-146">.NET Core には、診断データが公開される `EventPipe` と呼ばれるものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d91e6-146">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="d91e6-147">[dotnet-トレース](dotnet-trace.md) ツールを使用すると、アプリから興味深いプロファイル データを使用できます。これは、アプリケーションの実行速度が低下する可能性のあるシナリオに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-147">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="d91e6-148">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="d91e6-148">dotnet-symbol</span></span>

<span data-ttu-id="d91e6-149">[dotnet-symbol](dotnet-symbol.md) によって、コア ダンプまたはミニダンプを開くために必要なファイル (シンボル、DAC/DBI、ホスト ファイルなど) をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-149">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="d91e6-150">別のコンピューターでキャプチャされたダンプ ファイルをデバッグするためにシンボルとモジュールが必要な場合は、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-150">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="d91e6-151">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="d91e6-151">dotnet-sos</span></span>

<span data-ttu-id="d91e6-152">[dotnet-sos](dotnet-sos.md) によって、Linux と macOS に [SOS デバッグ拡張機能](sos-debugging-extension.md) がインストールされます ([Windbg/cdb](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools) を使用している場合は Windows でも)。</span><span class="sxs-lookup"><span data-stu-id="d91e6-152">[dotnet-sos](dotnet-sos.md) installs the [SOS debugging extension](sos-debugging-extension.md) on Linux and macOS (and on Windows if you're using [Windbg/cdb](https://docs.microsoft.com/windows-hardware/drivers/debugger/debugger-download-tools)).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="d91e6-153">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="d91e6-153">PerfCollect</span></span>

<span data-ttu-id="d91e6-154">[PerfCollect](trace-perfcollect-lttng.md) は、Linux ディストリビューションで実行されている .NET アプリのより詳細なパフォーマンス分析を行うために `perf` と `LTTng` でトレースを収集するために使用できる bash スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="d91e6-154">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="d91e6-155">.NET Core 診断チュートリアル</span><span class="sxs-lookup"><span data-stu-id="d91e6-155">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="d91e6-156">メモリ リークをデバッグする</span><span class="sxs-lookup"><span data-stu-id="d91e6-156">Debug a memory leak</span></span>

<span data-ttu-id="d91e6-157">[チュートリアル: メモリ リークをデバッグする](debug-memory-leak.md)では、メモリ リークを検出する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-157">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="d91e6-158">リークを確認するには [dotnet-counters](dotnet-counters.md) ツールを使用し、リークを診断するには [dotnet-dump](dotnet-dump.md) ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-158">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="d91e6-159">高い CPU 使用率をデバッグする</span><span class="sxs-lookup"><span data-stu-id="d91e6-159">Debug high CPU usage</span></span>

<span data-ttu-id="d91e6-160">[チュートリアル: 高い CPU 使用率をデバッグする](debug-highcpu.md) に関するページに、高い CPU 使用率の調査方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="d91e6-160">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="d91e6-161">高い CPU 使用率を確認するために、[dotnet-counters](dotnet-counters.md) ツールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d91e6-161">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="d91e6-162">次に、[パフォーマンス分析ユーティリティ (`dotnet-trace`) 用のトレース](dotnet-trace.md)または Linux `perf` を使用して、CPU 使用率プロファイルを収集および表示する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-162">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="d91e6-163">デッドロックをデバッグする</span><span class="sxs-lookup"><span data-stu-id="d91e6-163">Debug deadlock</span></span>

<span data-ttu-id="d91e6-164">[チュートリアル: デッドロックのデバッグ](debug-deadlock.md)に関するページに、[dotnet-dump](dotnet-dump.md) ツールを使用してスレッドとロックを調査する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="d91e6-164">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="debug-a-stackoverflow"></a><span data-ttu-id="d91e6-165">スタック オーバーフローのデバッグ</span><span class="sxs-lookup"><span data-stu-id="d91e6-165">Debug a StackOverflow</span></span>

<span data-ttu-id="d91e6-166">[チュートリアル: スタック オーバーフローのデバッグ](debug-stackoverflow.md)」は、Linux で <xref:System.StackOverflowException> をデバッグする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-166">[Tutorial: Debug a StackOverflow](debug-stackoverflow.md) demonstrates how to debug a <xref:System.StackOverflowException> on Linux.</span></span>

### <a name="debug-linux-dumps"></a><span data-ttu-id="d91e6-167">Linux ダンプのデバッグ</span><span class="sxs-lookup"><span data-stu-id="d91e6-167">Debug Linux dumps</span></span>

<span data-ttu-id="d91e6-168">「[Linux ダンプのデバッグ](debug-linux-dumps.md)」では、Linux でダンプを収集して分析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-168">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="d91e6-169">EventCounters を使用してパフォーマンスを測定する</span><span class="sxs-lookup"><span data-stu-id="d91e6-169">Measure performance using EventCounters</span></span>

<span data-ttu-id="d91e6-170">[チュートリアル: .NET で EventCounters を使用してパフォーマンスを測定する](event-counter-perf.md)」は、<xref:System.Diagnostics.Tracing.EventCounter> API を使用して .NET アプリのパフォーマンスを測定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d91e6-170">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
