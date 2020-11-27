---
title: 診断ツールの概要 - .NET Core
description: .NET Core アプリケーションの診断に使用できるツールと手法の概要。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: c43e661ad8c9f665151e0240bf6b54e61b9acfef
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031918"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="940de-103">.NET Core で使用できる診断ツール</span><span class="sxs-lookup"><span data-stu-id="940de-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="940de-104">ソフトウェアは期待どおりに動作するとは限りませんが、.NET Core には、そのような問題を迅速かつ効果的に診断するために役立つツールと API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="940de-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="940de-105">この記事は、必要な各種ツールを見つけるために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="940de-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="940de-106">マネージド デバッガー</span><span class="sxs-lookup"><span data-stu-id="940de-106">Managed debuggers</span></span>

<span data-ttu-id="940de-107">[マネージド デバッガー](managed-debuggers.md)を使用すると、プログラムと対話することができます。</span><span class="sxs-lookup"><span data-stu-id="940de-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="940de-108">一時停止、段階的な実行、調査、および再開によって、コードの動作を分析できます。</span><span class="sxs-lookup"><span data-stu-id="940de-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="940de-109">デバッガーは、簡単に再現できる機能の問題を診断するための最初の選択肢です。</span><span class="sxs-lookup"><span data-stu-id="940de-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="940de-110">ログとトレース</span><span class="sxs-lookup"><span data-stu-id="940de-110">Logging and tracing</span></span>

<span data-ttu-id="940de-111">[ログとトレース](logging-tracing.md)は、関連する手法です。</span><span class="sxs-lookup"><span data-stu-id="940de-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="940de-112">ログ ファイルを作成するためのコードのインストルメント化を指します。</span><span class="sxs-lookup"><span data-stu-id="940de-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="940de-113">ファイルには、プログラムの機能の詳細が記録されます。</span><span class="sxs-lookup"><span data-stu-id="940de-113">The files record the details of what a program does.</span></span> <span data-ttu-id="940de-114">これらの詳細は、複雑度の高い問題を診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="940de-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="940de-115">タイム スタンプと組み合わせると、これらの手法はパフォーマンスの調査にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="940de-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="940de-116">単体テスト</span><span class="sxs-lookup"><span data-stu-id="940de-116">Unit testing</span></span>

<span data-ttu-id="940de-117">[単体テスト](../testing/index.md)は、高品質のソフトウェアを継続的に統合して展開するための重要なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="940de-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="940de-118">単体テストは、何かを中断するときに早期警告を提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="940de-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="dumps"></a><span data-ttu-id="940de-119">ダンプ</span><span class="sxs-lookup"><span data-stu-id="940de-119">Dumps</span></span>

<span data-ttu-id="940de-120">[ダンプ](./dumps.md)は、作成時のプロセスのスナップショットを含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="940de-120">A [dump](./dumps.md) is a file that contains a snapshot of the process at the time of creation.</span></span> <span data-ttu-id="940de-121">これらは、デバッグのためにアプリケーションの状態を調べるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="940de-121">These can be useful for examining the state of your application for debugging purposes.</span></span>

## <a name="collect-diagnostics-in-containers"></a><span data-ttu-id="940de-122">コンテナーでの診断の収集</span><span class="sxs-lookup"><span data-stu-id="940de-122">Collect diagnostics in containers</span></span>

<span data-ttu-id="940de-123">コンテナー化されていない Linux 環境で使用されているのと同じ診断ツールを使用して、[コンテナーで診断を収集](diagnostics-in-containers.md)することもできます。</span><span class="sxs-lookup"><span data-stu-id="940de-123">The same diagnostics tools that are used in non-containerized Linux environments can also be used to [collect diagnostics in containers](diagnostics-in-containers.md).</span></span> <span data-ttu-id="940de-124">Docker コンテナーでツールを動作させるために必要ないくつかの使用方法が変更されています。</span><span class="sxs-lookup"><span data-stu-id="940de-124">There are just a few usage changes needed to make sure the tools work in a Docker container.</span></span>

## <a name="debug-linux-dumps"></a><span data-ttu-id="940de-125">Linux ダンプのデバッグ</span><span class="sxs-lookup"><span data-stu-id="940de-125">Debug Linux dumps</span></span>

<span data-ttu-id="940de-126">「[Linux ダンプのデバッグ](debug-linux-dumps.md)」では、Linux でダンプを収集して分析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="940de-126">[Debug Linux dumps](debug-linux-dumps.md) explains how to collect and analyze dumps on Linux.</span></span>

## <a name="net-core-diagnostic-global-tools"></a><span data-ttu-id="940de-127">.NET Core 診断グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="940de-127">.NET Core diagnostic global tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="940de-128">dotnet-カウンター</span><span class="sxs-lookup"><span data-stu-id="940de-128">dotnet-counters</span></span>

<span data-ttu-id="940de-129">[dotnet-カウンター](dotnet-counters.md)は、第 1 レベルの正常性監視とパフォーマンス調査のためのパフォーマンス監視ツールです。</span><span class="sxs-lookup"><span data-stu-id="940de-129">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="940de-130"><xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視します。</span><span class="sxs-lookup"><span data-stu-id="940de-130">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="940de-131">たとえば、CPU 使用率や、.NET Core アプリケーションでスローされる例外の発生率などをすばやく監視できます。</span><span class="sxs-lookup"><span data-stu-id="940de-131">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="940de-132">dotnet-ダンプ</span><span class="sxs-lookup"><span data-stu-id="940de-132">dotnet-dump</span></span>

<span data-ttu-id="940de-133">[dotnet-ダンプ](dotnet-dump.md) ツールは、ネイティブ デバッガーを使用せずに Windows と Linux のコア ダンプを収集して分析する方法です。</span><span class="sxs-lookup"><span data-stu-id="940de-133">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-gcdump"></a><span data-ttu-id="940de-134">dotnet-gcdump</span><span class="sxs-lookup"><span data-stu-id="940de-134">dotnet-gcdump</span></span>

<span data-ttu-id="940de-135">[dotnet-gcdump](dotnet-gcdump.md) ツールは、ライブ .NET プロセスの GC (ガベージ コレクター) ダンプを収集する手段です。</span><span class="sxs-lookup"><span data-stu-id="940de-135">The [dotnet-gcdump](dotnet-gcdump.md) tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="940de-136">dotnet-トレース</span><span class="sxs-lookup"><span data-stu-id="940de-136">dotnet-trace</span></span>

<span data-ttu-id="940de-137">.NET Core には、診断データが公開される `EventPipe` と呼ばれるものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="940de-137">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="940de-138">[dotnet-トレース](dotnet-trace.md) ツールを使用すると、アプリから興味深いプロファイル データを使用できます。これは、アプリケーションの実行速度が低下する可能性のあるシナリオに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="940de-138">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

### <a name="dotnet-symbol"></a><span data-ttu-id="940de-139">dotnet-symbol</span><span class="sxs-lookup"><span data-stu-id="940de-139">dotnet-symbol</span></span>

<span data-ttu-id="940de-140">[dotnet-symbol](dotnet-symbol.md) によって、コア ダンプまたはミニダンプを開くために必要なファイル (シンボル、DAC/DBI、ホスト ファイルなど) をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="940de-140">[dotnet-symbol](dotnet-symbol.md) downloads files (symbols, DAC/DBI, host files, etc.) needed to open a core dump or minidump.</span></span> <span data-ttu-id="940de-141">別のコンピューターでキャプチャされたダンプ ファイルをデバッグするためにシンボルとモジュールが必要な場合は、このツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="940de-141">Use this tool if you need symbols and modules to debug a dump file captured on a different machine.</span></span>

### <a name="dotnet-sos"></a><span data-ttu-id="940de-142">dotnet-sos</span><span class="sxs-lookup"><span data-stu-id="940de-142">dotnet-sos</span></span>

<span data-ttu-id="940de-143">[dotnet-sos](dotnet-sos.md) を使用すると、Linux または MacOS (または、以前のデバッグ ツールを使用している場合は Windows) に [SOS デバッガー拡張](../../framework/tools/sos-dll-sos-debugging-extension.md)をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="940de-143">[dotnet-sos](dotnet-sos.md) is used to install the [SOS debugging extension](../../framework/tools/sos-dll-sos-debugging-extension.md) on Linux or MacOS (or on Windows if using older debugging tools).</span></span>

### <a name="perfcollect"></a><span data-ttu-id="940de-144">PerfCollect</span><span class="sxs-lookup"><span data-stu-id="940de-144">PerfCollect</span></span>

<span data-ttu-id="940de-145">[PerfCollect](trace-perfcollect-lttng.md) は、Linux ディストリビューションで実行されている .NET アプリのより詳細なパフォーマンス分析を行うために `perf` と `LTTng` でトレースを収集するために使用できる bash スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="940de-145">[PerfCollect](trace-perfcollect-lttng.md) is a bash script you can use to collect traces with `perf` and `LTTng` for a more in-depth performance analysis of .NET apps running on Linux distributions.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="940de-146">.NET Core 診断チュートリアル</span><span class="sxs-lookup"><span data-stu-id="940de-146">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="940de-147">メモリ リークをデバッグする</span><span class="sxs-lookup"><span data-stu-id="940de-147">Debug a memory leak</span></span>

<span data-ttu-id="940de-148">[チュートリアル: メモリ リークをデバッグする](debug-memory-leak.md)では、メモリ リークを検出する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="940de-148">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="940de-149">リークを確認するには [dotnet-counters](dotnet-counters.md) ツールを使用し、リークを診断するには [dotnet-dump](dotnet-dump.md) ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="940de-149">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="940de-150">高い CPU 使用率をデバッグする</span><span class="sxs-lookup"><span data-stu-id="940de-150">Debug high CPU usage</span></span>

<span data-ttu-id="940de-151">[チュートリアル: 高い CPU 使用率をデバッグする](debug-highcpu.md) に関するページに、高い CPU 使用率の調査方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="940de-151">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="940de-152">高い CPU 使用率を確認するために、[dotnet-counters](dotnet-counters.md) ツールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="940de-152">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="940de-153">次に、[パフォーマンス分析ユーティリティ (`dotnet-trace`) 用のトレース](dotnet-trace.md)または Linux `perf` を使用して、CPU 使用率プロファイルを収集および表示する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="940de-153">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="940de-154">デッドロックをデバッグする</span><span class="sxs-lookup"><span data-stu-id="940de-154">Debug deadlock</span></span>

<span data-ttu-id="940de-155">[チュートリアル: デッドロックのデバッグ](debug-deadlock.md)に関するページに、[dotnet-dump](dotnet-dump.md) ツールを使用してスレッドとロックを調査する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="940de-155">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>

### <a name="measure-performance-using-eventcounters"></a><span data-ttu-id="940de-156">EventCounters を使用してパフォーマンスを測定する</span><span class="sxs-lookup"><span data-stu-id="940de-156">Measure performance using EventCounters</span></span>

<span data-ttu-id="940de-157">[チュートリアル: .NET で EventCounters を使用してパフォーマンスを測定する](event-counter-perf.md)」は、<xref:System.Diagnostics.Tracing.EventCounter> API を使用して .NET アプリのパフォーマンスを測定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="940de-157">[Tutorial: Measure performance using EventCounters in .NET](event-counter-perf.md) shows you how to use the <xref:System.Diagnostics.Tracing.EventCounter> API to measure performance in your .NET app.</span></span>
