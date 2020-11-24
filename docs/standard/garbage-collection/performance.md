---
title: ガベージ コレクションとパフォーマンス
description: ガベージ コレクションとメモリ使用に関連する問題について確認します。 アプリケーションに対するガベージ コレクションの影響を最小限に抑える方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 15ca3fd06bb607a4f0257b4c5cd62f9c935c6913
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827543"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="11fd0-104">ガベージ コレクションとパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="11fd0-104">Garbage Collection and Performance</span></span>

<span data-ttu-id="11fd0-105">ここでは、ガベージ コレクションおよびメモリ使用に関連する問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-105">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="11fd0-106">マネージド ヒープに関する問題について取り上げ、ガベージ コレクションによるアプリケーションに対する影響を最小限に抑える方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-106">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="11fd0-107">問題を調査するために使用できる手順のリンクを問題ごとに示してあります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-107">Each issue has links to procedures that you can use to investigate problems.</span></span>

## <a name="performance-analysis-tools"></a><span data-ttu-id="11fd0-108">パフォーマンス分析ツール</span><span class="sxs-lookup"><span data-stu-id="11fd0-108">Performance Analysis Tools</span></span>

<span data-ttu-id="11fd0-109">以下のセクションでは、メモリ使用とガベージ コレクションに関する問題を調査するために使用できるツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-109">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="11fd0-110">このトピックの後半で説明する[手順](#performance-check-procedures)では、これらのツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-110">The [procedures](#performance-check-procedures) provided later in this topic refer to these tools.</span></span>

### <a name="memory-performance-counters"></a><span data-ttu-id="11fd0-111">メモリ パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="11fd0-111">Memory Performance Counters</span></span>

<span data-ttu-id="11fd0-112">パフォーマンス カウンターを使用してパフォーマンス データを収集できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-112">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="11fd0-113">手順については、「[ランタイム プロファイリング](../../framework/debug-trace-profile/runtime-profiling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-113">For instructions, see [Runtime Profiling](../../framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="11fd0-114">ガベージ コレクターに関する情報は、.NET CLR Memory カテゴリのパフォーマンス カウンターから提供されます。詳細については、[.NET のパフォーマンス カウンター](../../framework/debug-trace-profile/performance-counters.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-114">The .NET CLR Memory category of performance counters, as described in [Performance Counters in .NET](../../framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

### <a name="debugging-with-sos"></a><span data-ttu-id="11fd0-115">SOS キーを使ったデバッグ</span><span class="sxs-lookup"><span data-stu-id="11fd0-115">Debugging with SOS</span></span>

<span data-ttu-id="11fd0-116">[Windows デバッガー (WinDbg)](/windows-hardware/drivers/debugger/index) を使用して、マネージド ヒープのオブジェクトを検査できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-116">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="11fd0-117">WinDbg をインストールするには、「[Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools)」 (Windows 用デバッグ ツールのダウンロード) ページから Windows 用デバッグ ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="11fd0-117">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="11fd0-118">ガベージ コレクション ETW イベント</span><span class="sxs-lookup"><span data-stu-id="11fd0-118">Garbage Collection ETW Events</span></span>

<span data-ttu-id="11fd0-119">Windows イベント トレーシング (ETW) は、.NET のプロファイリングとデバッグのサポートを補足するトレース システムです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-119">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by .NET.</span></span> <span data-ttu-id="11fd0-120">.NET Framework 4 以降では、[ガベージ コレクション ETW イベント](../../framework/performance/garbage-collection-etw-events.md)により、統計的な観点からマネージド ヒープを分析するために役立つ情報が得られるようになりました。</span><span class="sxs-lookup"><span data-stu-id="11fd0-120">Starting with .NET Framework 4, [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="11fd0-121">たとえば、ガベージ コレクションの発生前に発生する `GCStart_V1` イベントでは、次の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-121">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="11fd0-122">収集されるオブジェクトのジェネレーション</span><span class="sxs-lookup"><span data-stu-id="11fd0-122">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="11fd0-123">ガベージ コレクションが発生した理由</span><span class="sxs-lookup"><span data-stu-id="11fd0-123">What triggered the garbage collection.</span></span>

- <span data-ttu-id="11fd0-124">ガベージ コレクションの種類 (同時実行または非同時実行)</span><span class="sxs-lookup"><span data-stu-id="11fd0-124">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="11fd0-125">ETW イベント ログは効率的であり、ガベージ コレクションに関連するパフォーマンスの問題がマスクされることはありません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-125">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="11fd0-126">ETW イベントと組み合わせてプロセス独自のイベントを提供できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-126">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="11fd0-127">ログを記録すると、アプリケーションのイベントとガベージ コレクションのイベントの両方を相互に関連付けて、ヒープの問題がいつどのようにして発生するかを特定できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-127">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="11fd0-128">たとえば、サーバー アプリケーションでは、クライアント要求の開始時と終了時にイベントを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-128">For example, a server application could provide events at the start and end of a client request.</span></span>

### <a name="the-profiling-api"></a><span data-ttu-id="11fd0-129">プロファイル API</span><span class="sxs-lookup"><span data-stu-id="11fd0-129">The Profiling API</span></span>

<span data-ttu-id="11fd0-130">共通言語ランタイム (CLR) のプロファイル インターフェイスは、ガベージ コレクションの影響を受けたオブジェクトに関する詳細な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-130">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="11fd0-131">プロファイラーでは、ガベージ コレクションの開始時と終了時に通知を受け取り、</span><span class="sxs-lookup"><span data-stu-id="11fd0-131">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="11fd0-132">各ジェネレーションにおけるオブジェクトの識別情報など、マネージド ヒープのオブジェクトに関するレポートを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-132">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="11fd0-133">詳細については、「[プロファイルの概要](../../framework/unmanaged-api/profiling/profiling-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-133">For more information, see [Profiling Overview](../../framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="11fd0-134">プロファイラーでは包括的な情報を提供できますが、</span><span class="sxs-lookup"><span data-stu-id="11fd0-134">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="11fd0-135">複雑なプロファイラーを使用すると、アプリケーションの動作が変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-135">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="11fd0-136">アプリケーション ドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="11fd0-136">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="11fd0-137">.NET Framework 4 以降では、アプリケーション ドメインのリソース監視 (ARM) によって、ホストで CPU とメモリのアプリケーション ドメインによる使用状況を監視できるようになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-137">Starting with .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="11fd0-138">詳細については、「[アプリケーション ドメインのリソース監視](app-domain-resource-monitoring.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-138">For more information, see [Application Domain Resource Monitoring](app-domain-resource-monitoring.md).</span></span>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="11fd0-139">パフォーマンスに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="11fd0-139">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="11fd0-140">最初に、[本当にガベージ コレクションの問題なのかどうかを確認します](#IsGC)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-140">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="11fd0-141">ガベージ コレクションの問題であることがわかったら、次の一覧から問題を選択してトラブルシューティングを行います。</span><span class="sxs-lookup"><span data-stu-id="11fd0-141">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="11fd0-142">メモリ不足の例外がスローされる</span><span class="sxs-lookup"><span data-stu-id="11fd0-142">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="11fd0-143">プロセスによるメモリ使用量が多すぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-143">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="11fd0-144">ガベージ コレクターによるオブジェクトの解放に時間がかかる</span><span class="sxs-lookup"><span data-stu-id="11fd0-144">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="11fd0-145">マネージド ヒープが過度に断片化される</span><span class="sxs-lookup"><span data-stu-id="11fd0-145">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="11fd0-146">ガベージ コレクションの一時停止が長すぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-146">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="11fd0-147">ジェネレーション 0 が大きすぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-147">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="11fd0-148">ガベージ コレクションの実行時の CPU 使用率が高すぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-148">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="11fd0-149">問題:メモリ不足の例外がスローされる</span><span class="sxs-lookup"><span data-stu-id="11fd0-149">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="11fd0-150"><xref:System.OutOfMemoryException> マネージド例外がスローされる正当な状況としては、次の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-150">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="11fd0-151">仮想メモリが不足している。</span><span class="sxs-lookup"><span data-stu-id="11fd0-151">Running out of virtual memory.</span></span>

  <span data-ttu-id="11fd0-152">ガベージ コレクターは、サイズがあらかじめ決められたセグメント単位でシステムのメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-152">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="11fd0-153">割り当てで追加のセグメントが必要になっとときに、プロセスの仮想メモリ空間に連続する空きブロックが残っていなければ、マネージド ヒープの割り当ては失敗します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-153">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="11fd0-154">十分な物理メモリを確保できない。</span><span class="sxs-lookup"><span data-stu-id="11fd0-154">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="11fd0-155">パフォーマンス チェック</span><span class="sxs-lookup"><span data-stu-id="11fd0-155">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="11fd0-156">メモリ不足の例外がマネージド例外かどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-156">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="11fd0-157">予約できる仮想メモリの量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-157">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="11fd0-158">十分な物理メモリがあるかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-158">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="11fd0-159">例外が正当なものでないと判断した場合は、マイクロソフト カスタマー サポート サービスにお問い合わせください。その際、次の情報をご連絡ください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-159">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="11fd0-160">メモリ不足のマネージド例外を含む履歴</span><span class="sxs-lookup"><span data-stu-id="11fd0-160">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="11fd0-161">完全なメモリ ダンプ</span><span class="sxs-lookup"><span data-stu-id="11fd0-161">Full memory dump.</span></span>

- <span data-ttu-id="11fd0-162">メモリ不足の例外が正当なものでないことを証明するデータ (仮想メモリまたは物理メモリに問題がないことを示すデータなど)</span><span class="sxs-lookup"><span data-stu-id="11fd0-162">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="11fd0-163">問題:プロセスによるメモリ使用量が多すぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-163">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="11fd0-164">一般的な前提として、メモリ使用量が多すぎる場合については、Windows タスク マネージャーの **[パフォーマンス]** タブのメモリ使用量の表示で確認できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-164">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="11fd0-165">ただし、この表示はワーキング セットに関するもので、仮想メモリの使用量に関する情報ではありません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-165">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="11fd0-166">マネージド ヒープが原因であると判断した場合は、一定の期間にわたってマネージド ヒープを測定し、パターンを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-166">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="11fd0-167">マネージド ヒープが原因でないと判断した場合は、ネイティブ デバッグを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-167">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="11fd0-168">パフォーマンス チェック</span><span class="sxs-lookup"><span data-stu-id="11fd0-168">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="11fd0-169">予約できる仮想メモリの量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-169">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="11fd0-170">マネージド ヒープでコミットしているメモリの量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-170">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="11fd0-171">マネージド ヒープで予約されているメモリの量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-171">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="11fd0-172">ジェネレーション 2 の大きいオブジェクトを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-172">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="11fd0-173">オブジェクトへの参照を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-173">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="11fd0-174">問題:ガベージ コレクターによるオブジェクトの解放に時間がかかる</span><span class="sxs-lookup"><span data-stu-id="11fd0-174">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="11fd0-175">ガベージ コレクションでオブジェクトが通常どおりに解放されていないように見える場合は、それらのオブジェクトに対する強い参照がないかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-175">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="11fd0-176">この問題は、死んだ状態のオブジェクトを含むジェネレーションに対してガベージ コレクションが行われていない場合にも発生します。死んだ状態のオブジェクトは、そのオブジェクトのファイナライザーが実行されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-176">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="11fd0-177">たとえば、シングルスレッド アパートメント (STA) のアプリケーションを実行している場合に、ファイナライザー キューを処理するスレッドがファイナライザーの呼び出しに失敗すると、この状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-177">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="11fd0-178">パフォーマンス チェック</span><span class="sxs-lookup"><span data-stu-id="11fd0-178">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="11fd0-179">オブジェクトへの参照を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-179">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="11fd0-180">ファイナライザーが実行されたかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-180">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="11fd0-181">終了待機中のオブジェクトがないかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-181">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="11fd0-182">問題:マネージド ヒープが過度に断片化される</span><span class="sxs-lookup"><span data-stu-id="11fd0-182">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="11fd0-183">断片化レベルは、ジェネレーションに割り当てられたメモリの合計に占める空き領域の割合として計算されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-183">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="11fd0-184">ジェネレーション 2 の場合、許容される断片化レベルは 20% 以下です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-184">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="11fd0-185">ジェネレーション 2 は非常に大きくなる可能性があるため、断片化の割合の方が絶対値より重要になります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-185">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="11fd0-186">ジェネレーション 0 は、新しいオブジェクトが割り当てられるジェネレーションなので、空き領域が多くても問題はありません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-186">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="11fd0-187">断片化は常に大きなオブジェクト ヒープで発生します。大きなオブジェクト ヒープは圧縮されないからです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-187">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="11fd0-188">隣接する空きオブジェクトは、大きなオブジェクトの割り当て要求を満たすために必然的に 1 つの領域にまとめられます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-188">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="11fd0-189">断片化が問題になるのは、ジェネレーション 1 とジェネレーション 2 です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-189">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="11fd0-190">これらのジェネレーションで、ガベージ コレクションの終了後に大量の空き領域ある場合は、アプリケーションのオブジェクトの使用方法を変更する必要がある可能性があります。長期間のオブジェクトの有効期間を再評価することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-190">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="11fd0-191">オブジェクトの固定が過度に行われていると断片化レベルが高くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-191">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="11fd0-192">断片化レベルが高い場合は、固定されているオブジェクトが多すぎる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-192">If fragmentation is high, too many objects could have been pinned.</span></span>

<span data-ttu-id="11fd0-193">仮想メモリの断片化によってガベージ コレクターがセグメントを追加できなくなっている場合、次のような原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-193">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="11fd0-194">多数の小さなアセンブリの読み込みとアンロードが頻繁に行われている。</span><span class="sxs-lookup"><span data-stu-id="11fd0-194">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="11fd0-195">アンマネージ コードとの相互運用時に保持される COM オブジェクトへの参照が多すぎる。</span><span class="sxs-lookup"><span data-stu-id="11fd0-195">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="11fd0-196">大きな一時オブジェクトが作成されているために、大きなオブジェクト ヒープでヒープ セグメントの割り当てと解放が頻繁に行われている。</span><span class="sxs-lookup"><span data-stu-id="11fd0-196">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="11fd0-197">アプリケーションで CLR をホストする際には、セグメントを保持するようにガベージ コレクターに要求することができます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-197">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="11fd0-198">これにより、セグメント割り当ての頻度が減少します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-198">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="11fd0-199">そのためには、[STARTUP_FLAGS 列挙型](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md)の STARTUP_HOARD_GC_VM フラグを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-199">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="11fd0-200">パフォーマンス チェック</span><span class="sxs-lookup"><span data-stu-id="11fd0-200">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="11fd0-201">マネージド ヒープの空き領域の容量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-201">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="11fd0-202">固定されたオブジェクトの数を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-202">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="11fd0-203">正当な理由もないのに断片化が発生していると思われる場合は、マイクロソフト カスタマー サポート サービスにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-203">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="11fd0-204">問題:ガベージ コレクションの一時停止が長すぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-204">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="11fd0-205">ガベージ コレクションはソフト リアルタイムで動作するため、アプリケーションはある程度の一時停止に耐えられなければなりません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-205">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="11fd0-206">ソフト リアルタイムの基準では、95% の操作が時間どおりに完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-206">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="11fd0-207">同時実行ガベージ コレクションでは、コレクションの実行中もマネージド スレッドを実行できるため、一時停止は最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-207">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="11fd0-208">短期ガベージ コレクション (ジェネレーション 0 および 1) は数ミリ秒しかかからないため、一般に一時停止を減らすことは不可能です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-208">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="11fd0-209">一方、ジェネレーション 2 のコレクションでは、アプリケーションによる割り当て要求のパターンを変更することによって一時停止を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-209">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="11fd0-210">より正確な方法として、[ガベージ コレクション ETW イベント](../../framework/performance/garbage-collection-etw-events.md)を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-210">Another, more accurate, method is to use [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="11fd0-211">一連のイベントにタイム スタンプを追加して区別することにより、コレクションのタイミングを特定できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-211">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="11fd0-212">コレクションのシーケンス全体には、実行エンジンの中断、ガベージ コレクション自体、および実行エンジンの再開が含まれます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-212">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="11fd0-213">[ガベージ コレクションの通知](notifications.md)を使用すると、サーバーでジェネレーション 2 のコレクションが発生しそうかどうか、要求を別のサーバーに再ルーティングすることで一時停止の問題を緩和できるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-213">You can use [Garbage Collection Notifications](notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="11fd0-214">パフォーマンス チェック</span><span class="sxs-lookup"><span data-stu-id="11fd0-214">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="11fd0-215">ガベージ コレクションの継続時間を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-215">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="11fd0-216">ガベージ コレクションが発生した原因を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-216">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="11fd0-217">問題:ジェネレーション 0 が大きすぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-217">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="11fd0-218">64 ビット システムでは、ジェネレーション 0 のオブジェクトの数が増える傾向があります。ワークステーションのガベージ コレクションではなくサーバーのガベージ コレクションを使用している場合は特にその傾向が強くなります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-218">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="11fd0-219">それらの環境では、ジェネレーション 0 のガベージ コレクションをトリガーするしきい値が高いので、ジェネレーション 0 のコレクションが非常に大きくなる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-219">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="11fd0-220">アプリケーションで、ガベージ コレクションがトリガーされる前により多くのメモリを割り当てると、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-220">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="11fd0-221">問題:ガベージ コレクションの実行時の CPU 使用率が高すぎる</span><span class="sxs-lookup"><span data-stu-id="11fd0-221">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="11fd0-222">ガベージ コレクションの実行時には CPU 使用率が高くなります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-222">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="11fd0-223">ガベージ コレクションに大量の処理時間が費やされている場合は、コレクションの発生頻度が高すぎるか、コレクションの継続時間が長すぎます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-223">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="11fd0-224">マネージド ヒープに対するオブジェクトの割り当ての速度を上げるとガベージ コレクションの発生頻度が高くなります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-224">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="11fd0-225">割り当ての速度を下げるとガベージ コレクションの発生頻度が低くなります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-225">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="11fd0-226">割り当ての速度を監視するには、`Allocated Bytes/second` パフォーマンス カウンターを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-226">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="11fd0-227">詳細については、[.NET のパフォーマンス カウンター](../../framework/debug-trace-profile/performance-counters.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-227">For more information, see [Performance Counters in .NET](../../framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="11fd0-228">コレクションの継続時間は、主に、割り当て後に残ったオブジェクトの数によって決まります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-228">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="11fd0-229">コレクションの対象となるオブジェクトが数多く残っていると、ガベージ コレクターが大量のメモリを処理しなければならなくなります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-229">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="11fd0-230">残存オブジェクトの圧縮には時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-230">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="11fd0-231">コレクションの実行中に処理されたオブジェクトの数を確認するには、デバッガーで特定のジェネレーションのガベージ コレクションの終了時にブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-231">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="11fd0-232">パフォーマンス チェック</span><span class="sxs-lookup"><span data-stu-id="11fd0-232">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="11fd0-233">CPU の使用率が高いのはガベージ コレクションのためかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-233">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="11fd0-234">ガベージ コレクションの終了時にブレークポイントを設定する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-234">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="11fd0-235">トラブルシューティングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="11fd0-235">Troubleshooting Guidelines</span></span>

<span data-ttu-id="11fd0-236">ここでは、調査を開始するときに考慮する必要があるガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-236">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="11fd0-237">ワークステーションのガベージ コレクションかサーバーのガベージ コレクションか</span><span class="sxs-lookup"><span data-stu-id="11fd0-237">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="11fd0-238">使用しているガベージ コレクションの種類が正しいかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-238">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="11fd0-239">アプリケーションで複数のスレッドおよびオブジェクト インスタンスを使用する場合は、ワークステーションのガベージ コレクションではなくサーバーのガベージ コレクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-239">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="11fd0-240">サーバーのガベージ コレクションは複数のスレッドで動作しますが、ワークステーションのガベージ コレクションでは、アプリケーションの複数のインスタンスでそれぞれ専用のガベージ コレクション スレッドを実行する必要があるため、CPU 時間の競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-240">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="11fd0-241">負荷が低く、バックグラウンドでタスクを実行することの少ないアプリケーション (サービスなど) では、同時実行ガベージ コレクションを無効にしてワークステーションのガベージ コレクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-241">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="11fd0-242">いつマネージド ヒープのサイズを測定するか</span><span class="sxs-lookup"><span data-stu-id="11fd0-242">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="11fd0-243">プロファイラーを使用しない場合、パフォーマンスの問題を効果的に診断するには、一貫した測定パターンを確立する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-243">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="11fd0-244">スケジュールを確立する際の考慮事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-244">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="11fd0-245">ジェネレーション 2 のガベージ コレクションの後に測定する場合は、マネージド ヒープ全体からガベージ (死んだ状態のオブジェクト) がなくなっています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-245">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="11fd0-246">ジェネレーション 0 のガベージ コレクションの直後に測定する場合は、ジェネレーション 1 と 2 のオブジェクトのコレクションはまだ行われていません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-246">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="11fd0-247">ガベージ コレクションの直前に測定する場合は、どのくらいの割り当てが行われるとガベージ コレクションが開始されるのかが測定されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-247">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="11fd0-248">ガベージ コレクションの実行中に測定するのには問題があります。ガベージ コレクターのデータ構造が走査可能な状態になっていないので、完全な結果が得られない可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-248">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="11fd0-249">これは仕様に基づく制限事項です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-249">This is by design.</span></span>

- <span data-ttu-id="11fd0-250">同時実行ガベージ コレクションを有効にしてワークステーションのガベージ コレクションを使用している場合は、解放されたオブジェクトが圧縮されないため、ヒープ サイズが変わらなかったり大きくなっていたりすることがあります (断片化のために大きく見えることがあります)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-250">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="11fd0-251">ジェネレーション 2 の同時実行ガベージ コレクションは、物理メモリの負荷が高すぎると延期されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-251">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="11fd0-252">マネージド ヒープを測定するためのブレークポイントを設定する方法を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-252">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="11fd0-253">ガベージ コレクションの終了時にブレークポイントを設定するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-253">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="11fd0-254">SOS デバッガー拡張が読み込まれた WinDbg で、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-254">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="11fd0-255">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span><span class="sxs-lookup"><span data-stu-id="11fd0-255">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="11fd0-256">**GcCondemnedGeneration** は、目的のジェネレーションに設定します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-256">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="11fd0-257">このコマンドにはプライベート シンボルが必要です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-257">This command requires private symbols.</span></span>

  <span data-ttu-id="11fd0-258">これにより、ジェネレーション 2 のオブジェクトがガベージ コレクションのために解放された後に **RestartEE** が実行されると、実行が中断されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-258">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="11fd0-259">サーバーのガベージ コレクションでは、**RestartEE** を呼び出すスレッドは 1 つだけなので、ジェネレーション 2 のガベージ コレクションの実行中に 1 回だけブレークポイントが発生します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-259">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

## <a name="performance-check-procedures"></a><span data-ttu-id="11fd0-260">パフォーマンス チェックの手順</span><span class="sxs-lookup"><span data-stu-id="11fd0-260">Performance Check Procedures</span></span>

<span data-ttu-id="11fd0-261">ここでは、パフォーマンスの問題の原因を切り分けるための以下の手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-261">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="11fd0-262">問題の原因がガベージ コレクションにあるかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-262">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="11fd0-263">メモリ不足の例外がマネージド例外かどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-263">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="11fd0-264">予約できる仮想メモリの量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-264">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="11fd0-265">十分な物理メモリがあるかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-265">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="11fd0-266">マネージド ヒープでコミットしているメモリの量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-266">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="11fd0-267">マネージド ヒープで予約されているメモリの量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-267">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="11fd0-268">ジェネレーション 2 の大きいオブジェクトを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-268">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="11fd0-269">オブジェクトへの参照を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-269">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="11fd0-270">ファイナライザーが実行されたかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-270">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="11fd0-271">終了待機中のオブジェクトがないかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-271">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="11fd0-272">マネージド ヒープの空き領域の容量を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-272">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="11fd0-273">固定されたオブジェクトの数を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-273">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="11fd0-274">ガベージ コレクションの継続時間を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-274">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="11fd0-275">ガベージ コレクションが発生した原因を確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-275">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="11fd0-276">CPU の使用率が高いのはガベージ コレクションのためかどうかを確認する。</span><span class="sxs-lookup"><span data-stu-id="11fd0-276">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="11fd0-277">問題の原因がガベージ コレクションにあるかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-277">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="11fd0-278">次の 2 つのメモリ パフォーマンス カウンターを調べます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-278">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="11fd0-279">**% Time in GC**。</span><span class="sxs-lookup"><span data-stu-id="11fd0-279">**% Time in GC**.</span></span> <span data-ttu-id="11fd0-280">前回のガベージ コレクション サイクルの後にガベージ コレクションの実行に費やされた経過時間の割合を表示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-280">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="11fd0-281">このカウンターを使用すると、ガベージ コレクターがマネージド ヒープの領域を確保するために費やしている時間が長すぎないかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-281">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="11fd0-282">ガベージ コレクションに費やされている時間が比較的短い場合は、マネージド ヒープ以外のリソースに問題があると考えられます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-282">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="11fd0-283">このカウンターは、同時実行ガベージ コレクションやバックグラウンド ガベージ コレクションでは正確な値が得られない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-283">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="11fd0-284">**# Total committed Bytes**。</span><span class="sxs-lookup"><span data-stu-id="11fd0-284">**# Total committed Bytes**.</span></span> <span data-ttu-id="11fd0-285">ガベージ コレクターによって現在コミットされている仮想メモリの量を表示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-285">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="11fd0-286">このカウンターを使用すると、アプリケーションが使用しているメモリのうちガベージ コレクターによって消費されているメモリが多すぎないかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-286">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="11fd0-287">ほとんどのメモリ パフォーマンス カウンターは、各ガベージ コレクションの終了時に更新されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-287">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="11fd0-288">そのため、情報を得ようとしている時点の状態が反映されていない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-288">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="11fd0-289">メモリ不足の例外がマネージド例外かどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-289">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="11fd0-290">SOS デバッガー拡張が読み込まれた WinDbg または Visual Studio デバッガーで、**pe** (print exception) コマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-290">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="11fd0-291">**!pe**</span><span class="sxs-lookup"><span data-stu-id="11fd0-291">**!pe**</span></span>

    <span data-ttu-id="11fd0-292">マネージド例外の場合は、次の例のように、<xref:System.OutOfMemoryException> が例外の種類として表示されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-292">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="11fd0-293">出力に例外が明記されていない場合は、メモリ不足の例外が発生したスレッドを特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-293">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="11fd0-294">デバッガーで次のコマンドを入力して、すべてのスレッドとその呼び出し履歴を表示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-294">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="11fd0-295">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="11fd0-295">**~\*kb**</span></span>

    <span data-ttu-id="11fd0-296">履歴に例外の呼び出しが含まれているスレッドは、`RaiseTheException` 引数によって示されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-296">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="11fd0-297">これはマネージド例外オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-297">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="11fd0-298">次のコマンドを使用して、入れ子になった例外をダンプします。</span><span class="sxs-lookup"><span data-stu-id="11fd0-298">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="11fd0-299">**!pe -nested**</span><span class="sxs-lookup"><span data-stu-id="11fd0-299">**!pe -nested**</span></span>

    <span data-ttu-id="11fd0-300">例外が見つからない場合、そのメモリ不足の例外は、アンマネージ コードで発生した例外です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-300">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="11fd0-301">予約できる仮想メモリの量を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-301">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="11fd0-302">SOS デバッガー拡張が読み込まれた WinDbg で次のコマンドを入力して、最も大きな空き領域を取得します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-302">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="11fd0-303">**!address -summary**</span><span class="sxs-lookup"><span data-stu-id="11fd0-303">**!address -summary**</span></span>

  <span data-ttu-id="11fd0-304">次の例のように、最も大きな空き領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-304">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="11fd0-305">この例では、最も大きな空き領域のサイズは約 24000 KB (16 進形式では 3A980) です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-305">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="11fd0-306">これは、ガベージ コレクターのセグメントに必要なサイズよりはるかに小さいサイズです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-306">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="11fd0-307">\- または -</span><span class="sxs-lookup"><span data-stu-id="11fd0-307">-or-</span></span>

- <span data-ttu-id="11fd0-308">**vmstat** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-308">Use the **vmstat** command:</span></span>

  <span data-ttu-id="11fd0-309">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="11fd0-309">**!vmstat**</span></span>

  <span data-ttu-id="11fd0-310">MAXIMUM 列の最大値が最も大きな空き領域です。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-310">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="11fd0-311">十分な物理メモリがあるかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-311">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="11fd0-312">Windows タスク マネージャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-312">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="11fd0-313">**[パフォーマンス]** タブで、コミットの値を確認します</span><span class="sxs-lookup"><span data-stu-id="11fd0-313">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="11fd0-314">(Windows 7 では **[システム]** の **[コミット (KB)]** )。</span><span class="sxs-lookup"><span data-stu-id="11fd0-314">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="11fd0-315">**[合計]** が **[制限値]** に近い場合は、物理メモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-315">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="11fd0-316">マネージド ヒープでコミットしているメモリの量を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-316">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="11fd0-317">マネージド ヒープでコミットしているバイト数を確認するには、`# Total committed bytes` メモリ パフォーマンス カウンターを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-317">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="11fd0-318">ガベージ コレクターは、セグメントのチャンクを必要に応じてコミットします。すべてを同時にコミットするのではありません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-318">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="11fd0-319">`# Bytes in all Heaps` パフォーマンス カウンターは使用しないでください。このパフォーマンス カウンターによって表されるのは、マネージド ヒープの実際のメモリ使用量ではありません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-319">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="11fd0-320">この値にはジェネレーションのサイズが含まれますが、それは、実質的にはジェネレーションのしきい値 (ジェネレーションがオブジェクトでいっぱいになった場合にガベージ コレクションが発生するサイズ) です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-320">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="11fd0-321">したがって、この値は、通常は 0 になります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-321">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="11fd0-322">マネージド ヒープで予約されているメモリの量を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-322">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="11fd0-323">`# Total reserved bytes` メモリ パフォーマンス カウンターを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-323">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="11fd0-324">ガベージ コレクターはメモリをセグメント単位で予約します。セグメントの開始位置を特定するには **eeheap** コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-324">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="11fd0-325">ガベージ コレクターが各セグメントに割り当てるメモリ量を判別することは可能ですが、セグメント サイズは実装に固有であり、定期的な更新プログラムによる場合を含め、いつでも変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-325">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="11fd0-326">アプリでは、セグメント サイズを推測することや、特定のセグメント サイズに依存することを絶対に避けてください。また、セグメントの割り当てに使用可能なメモリの量を構成しようとしてもなりません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-326">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="11fd0-327">SOS デバッガー拡張が読み込まれた WinDbg または Visual Studio デバッガーで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-327">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="11fd0-328">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="11fd0-328">**!eeheap -gc**</span></span>

  <span data-ttu-id="11fd0-329">この結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-329">The result is as follows.</span></span>

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  <span data-ttu-id="11fd0-330">"segment" によって示されるアドレスがセグメントの開始アドレスです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-330">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="11fd0-331">ジェネレーション 2 の大きいオブジェクトを確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-331">To determine large objects in generation 2</span></span>

- <span data-ttu-id="11fd0-332">SOS デバッガー拡張が読み込まれた WinDbg または Visual Studio デバッガーで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-332">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="11fd0-333">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="11fd0-333">**!dumpheap –stat**</span></span>

  <span data-ttu-id="11fd0-334">**dumpheap** は、マネージド ヒープが大きいと完了までにしばらくかかります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-334">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="11fd0-335">最も多くの領域を使用しているオブジェクトは出力の最後の数行に表示されるため、そこを分析します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-335">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="11fd0-336">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-336">For example:</span></span>

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  <span data-ttu-id="11fd0-337">最後の行のオブジェクトは文字列で、最も多くの領域を占有しています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-337">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="11fd0-338">したがって、アプリケーションで文字列オブジェクトを最適化する方法を調べます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-338">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="11fd0-339">サイズが 150 ～ 200 バイトの文字列を表示するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-339">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="11fd0-340">**!dumpheap -type System.String -min 150 -max 200**</span><span class="sxs-lookup"><span data-stu-id="11fd0-340">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="11fd0-341">結果の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-341">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="11fd0-342">ID に文字列の代わりに整数を使用すると、効率を改善できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-342">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="11fd0-343">同じ文字列が何千回も繰り返し使用されている場合は、文字列インターンの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-343">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="11fd0-344">文字列インターンの詳細については、<xref:System.String.Intern%2A?displayProperty=nameWithType> メソッドのリファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-344">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="11fd0-345">オブジェクトへの参照を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-345">To determine references to objects</span></span>

- <span data-ttu-id="11fd0-346">SOS デバッガー拡張が読み込まれた WinDbg で次のコマンドを入力して、オブジェクトへの参照を表示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-346">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="11fd0-347">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="11fd0-347">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="11fd0-348">特定のオブジェクトの参照を確認するには、アドレスを含めます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-348">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="11fd0-349">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="11fd0-349">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="11fd0-350">履歴で見つかるルートは誤検出である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-350">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="11fd0-351">詳細については、コマンド `!help gcroot` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="11fd0-351">For more information, use the command `!help gcroot`.</span></span>

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  <span data-ttu-id="11fd0-352">**gcroot** コマンドは、完了までに時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-352">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="11fd0-353">ガベージ コレクションによって解放されないオブジェクトはライブ オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-353">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="11fd0-354">したがって、そのオブジェクトを直接的または間接的に参照しているルートがあるため、**gcroot** でそのオブジェクトへのパス情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-354">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="11fd0-355">返されたグラフを調べて、それらのオブジェクトがまだ参照されている理由を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-355">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="11fd0-356">ファイナライザーが実行されたかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-356">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="11fd0-357">次のコードを含むテスト プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-357">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="11fd0-358">このテストで問題が解決される場合は、ファイナライザーが実行されていないためにガベージ コレクターによって解放されないオブジェクトがあったことになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-358">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="11fd0-359"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> メソッドを使用すると、ファイナライザーがタスクを完了できるようになるため、問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-359">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="11fd0-360">終了待機中のオブジェクトがないかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-360">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="11fd0-361">SOS デバッガー拡張が読み込まれた WinDbg または Visual Studio デバッガーで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-361">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="11fd0-362">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="11fd0-362">**!finalizequeue**</span></span>

    <span data-ttu-id="11fd0-363">終了準備が完了しているオブジェクトの数を確認します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-363">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="11fd0-364">その数が多い場合は、それらのファイナライザーが実行されない理由、または実行が遅れている理由を調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-364">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="11fd0-365">スレッドの出力を取得するには、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-365">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="11fd0-366">**threads -special**</span><span class="sxs-lookup"><span data-stu-id="11fd0-366">**threads -special**</span></span>

    <span data-ttu-id="11fd0-367">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-367">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="11fd0-368">ファイナライザー スレッドは、現在実行されているファイナライザーを示します (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-368">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="11fd0-369">実行中のファイナライザー スレッドが存在しない場合は、処理の開始を通知するイベントを待機しています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-369">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="11fd0-370">ファイナライザー スレッドは、ほとんどの場合この状態にあります。THREAD_HIGHEST_PRIORITY で実行されるので、実行するファイナライザーがあればすぐに実行されるためです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-370">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="11fd0-371">マネージド ヒープの空き領域の容量を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-371">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="11fd0-372">SOS デバッガー拡張が読み込まれた WinDbg または Visual Studio デバッガーで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-372">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="11fd0-373">**!dumpheap -type Free -stat**</span><span class="sxs-lookup"><span data-stu-id="11fd0-373">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="11fd0-374">このコマンドは、次の例に示すように、マネージド ヒープのすべての空きオブジェクトの合計サイズを表示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-374">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="11fd0-375">ジェネレーション 0 の空き領域を確認するには、次のコマンドを入力して、ジェネレーション別のメモリ消費情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-375">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="11fd0-376">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="11fd0-376">**!eeheap -gc**</span></span>

  <span data-ttu-id="11fd0-377">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-377">This command displays output similar to the following.</span></span> <span data-ttu-id="11fd0-378">最後の行には短期セグメントが表示されています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-378">The last line shows the ephemeral segment.</span></span>

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- <span data-ttu-id="11fd0-379">ジェネレーション 0 によって使用されている領域を計算します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-379">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="11fd0-380">**?49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="11fd0-380">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="11fd0-381">この結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-381">The result is as follows.</span></span> <span data-ttu-id="11fd0-382">ジェネレーション 0 は約 9 MB です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-382">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="11fd0-383">次のコマンドは、ジェネレーション 0 の範囲にある空き領域をダンプします。</span><span class="sxs-lookup"><span data-stu-id="11fd0-383">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="11fd0-384">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="11fd0-384">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="11fd0-385">この結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-385">The result is as follows.</span></span>

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  <span data-ttu-id="11fd0-386">この出力は、ヒープのジェネレーション 0 の部分で 9 MB の領域がオブジェクトに使用されていて、7 MB が空いていることを示しています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-386">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="11fd0-387">この分析から、ジェネレーション 0 がどの程度断片化に関与しているのかがわかります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-387">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="11fd0-388">この分のヒープ使用量は、長期間のオブジェクトによる断片化の原因となる合計容量から除外する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-388">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="11fd0-389">固定されたオブジェクトの数を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-389">To determine the number of pinned objects</span></span>

- <span data-ttu-id="11fd0-390">SOS デバッガー拡張が読み込まれた WinDbg または Visual Studio デバッガーで、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-390">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="11fd0-391">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="11fd0-391">**!gchandles**</span></span>

  <span data-ttu-id="11fd0-392">次の例に示すように、固定ハンドルの数を含む統計情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-392">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="11fd0-393">ガベージ コレクションの継続時間を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-393">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="11fd0-394">`% Time in GC` メモリ パフォーマンス カウンターを調べます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-394">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="11fd0-395">この値は、サンプル間隔の時間を使用して計算します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-395">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="11fd0-396">このカウンターは各ガベージ コレクションの終了時に更新されるため、サンプル間隔の間にコレクションが発生しなかった場合は前のサンプルと同じ値になります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-396">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="11fd0-397">コレクションの時間は、サンプル間隔の時間にパーセント値を掛けて計算します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-397">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="11fd0-398">次のデータには 4 つのサンプリング間隔が示されています。サンプリング間隔の時間は 2 秒で、8 秒間にわたって調査が行われています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-398">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="11fd0-399">`Gen0`、`Gen1`、`Gen2` の各列には、そのジェネレーションでその間隔の間に発生したガベージ コレクションの番号が表示されています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-399">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="11fd0-400">この情報からは、ガベージ コレクションが発生した時間はわかりませんが、特定の時間間隔の間に発生したガベージ コレクションの番号を特定できます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-400">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="11fd0-401">最悪のケースでは、ジェネレーション 0 の 10 番目のガベージ コレクションが間隔 2 の開始時に終了し、ジェネレーション 0 の 11 番目のガベージ コレクションが間隔 5 の終了時に終了したことになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-401">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="11fd0-402">10 番目のガベージ コレクションが終了してから 11 番目のガベージ コレクションが終了するまでの時間は約 2 秒で、パフォーマンス カウンターの値は 3% になっているため、ジェネレーション 0 の 11 番目のガベージ コレクションの継続時間は 60 ミリ秒 (2 秒 \* 3%) になります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-402">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="11fd0-403">次の例には 5 つの間隔があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-403">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="11fd0-404">ジェネレーション 2 の 2 番目のガベージ コレクションは、間隔 3 の間に開始され、間隔 5 で終了しています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-404">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="11fd0-405">最悪のケースでは、このガベージ コレクションの前のガベージ コレクションは、間隔 2 の開始時に終了したジェネレーション 0 のコレクションで、このジェネレーション 2 のガベージ コレクション自体は、間隔 5 の終了時に終了したことになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-405">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="11fd0-406">したがって、そのジェネレーション 0 のガベージ コレクションが終了してからこのジェネレーション 2 のガベージ コレクションが終了するまでの時間は 4 秒になります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-406">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="11fd0-407">`% Time in GC` カウンターの値は 20% なので、このジェネレーション 2 のガベージ コレクションの継続時間は最大で 800 ミリ秒 (4 秒 \* 20%) になります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-407">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="11fd0-408">[ガベージ コレクション ETW イベント](../../framework/performance/garbage-collection-etw-events.md)を使用してガベージ コレクションの長さを確認し、その情報を分析してガベージ コレクションの継続時間を特定することもできます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-408">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="11fd0-409">たとえば、次のデータは、非同時実行ガベージ コレクションの実行中に発生したイベント シーケンスを示しています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-409">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="11fd0-410">マネージド スレッドの中断に 26 マイクロ秒かかっています (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-410">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="11fd0-411">実際のガベージ コレクションに 4.8 ミリ秒かかっています (`GCEnd_V1` – `GCStart_V1`)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-411">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="11fd0-412">マネージド スレッドの再開に 21 マイクロ秒かかっています (`GCRestartEEEnd` – `GCRestartEEBegin`)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-412">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="11fd0-413">次の例は、バックグラウンド ガベージ コレクションの出力を示しています。この出力には、process、thread、および event field が含まれています</span><span class="sxs-lookup"><span data-stu-id="11fd0-413">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="11fd0-414">(すべてのデータが示されているわけではありません)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-414">(Not all data is shown.)</span></span>

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  <span data-ttu-id="11fd0-415">42504816 の `GCStart_V1` イベントは、前のフィールドが `1` であるため、バックグラウンド ガベージ コレクションを示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-415">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="11fd0-416">これは、次の番号のガベージ コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-416">This becomes garbage collection No.</span></span> <span data-ttu-id="11fd0-417">102019.</span><span class="sxs-lookup"><span data-stu-id="11fd0-417">102019.</span></span>

  <span data-ttu-id="11fd0-418">バックグラウンド ガベージ コレクションを開始する前に短期ガベージ コレクションを実行する必要があるため、`GCStart` イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-418">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="11fd0-419">これは、次の番号のガベージ コレクションになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-419">This becomes garbage collection No.</span></span> <span data-ttu-id="11fd0-420">102020.</span><span class="sxs-lookup"><span data-stu-id="11fd0-420">102020.</span></span>

  <span data-ttu-id="11fd0-421">42514170 の時点で、ガベージ コレクションの番号は</span><span class="sxs-lookup"><span data-stu-id="11fd0-421">At 42514170, garbage collection No.</span></span> <span data-ttu-id="11fd0-422">102020 になり、終了します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-422">102020 finishes.</span></span> <span data-ttu-id="11fd0-423">この時点でマネージド スレッドが再開されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-423">The managed threads are restarted at this point.</span></span> <span data-ttu-id="11fd0-424">スレッド 4372 で以上の処理が完了すると、バックグラウンド ガベージ コレクションがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-424">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="11fd0-425">スレッド 4744 で中断が発生します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-425">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="11fd0-426">このバックグラウンド ガベージ コレクションによってマネージド スレッドが中断されるのはこのときだけです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-426">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="11fd0-427">この中断の期間は約 99 ミリ秒です ((63784407-63685394)/1000)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-427">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="11fd0-428">バックグラウンド ガベージ コレクションの `GCEnd` イベントは 89931423 で発生しています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-428">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="11fd0-429">したがって、このバックグラウンド ガベージ コレクションの継続時間は約 47 秒になります ((89931423-42504816)/1000)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-429">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="11fd0-430">マネージド スレッドの実行中には短期ガベージ コレクションが何度も発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-430">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="11fd0-431">ガベージ コレクションが発生した原因を確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-431">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="11fd0-432">SOS デバッガー拡張が読み込まれた WinDbg または Visual Studio デバッガーで次のコマンドを入力して、すべてのスレッドとその呼び出し履歴を表示します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-432">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="11fd0-433">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="11fd0-433">**~\*kb**</span></span>

  <span data-ttu-id="11fd0-434">次のような出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-434">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="11fd0-435">オペレーティング システムからのメモリ不足の通知によってガベージ コレクションが発生した場合も同じような呼び出し履歴になりますが、その場合はスレッドがファイナライザー スレッドになります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-435">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="11fd0-436">ファイナライザー スレッドは、非同期のメモリ不足の通知を受け取って、ガベージ コレクションを発生させます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-436">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="11fd0-437">メモリの割り当てによってガベージ コレクションが発生した場合は、次のような履歴になります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-437">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  <span data-ttu-id="11fd0-438">最終的に Just-In-Time ヘルパー (`JIT_New*`) が `GCHeap::GarbageCollectGeneration` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-438">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="11fd0-439">ジェネレーション 2 のガベージ コレクションが割り当てによって発生していると判断された場合は、ジェネレーション 2 のガベージ コレクションの対象になっているオブジェクトを確認し、それを回避する方法を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-439">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="11fd0-440">そのためには、ジェネレーション 2 のガベージ コレクションの開始時と終了時の違いを確認し、ジェネレーション 2 のコレクションを発生させたオブジェクトを特定します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-440">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="11fd0-441">たとえば、ジェネレーション 2 のコレクションの開始時の情報を表示するには、デバッガーで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-441">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="11fd0-442">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="11fd0-442">**!dumpheap –stat**</span></span>

  <span data-ttu-id="11fd0-443">出力の例を以下に示します (最も多くの領域を使用しているオブジェクトのみが示されています)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-443">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  <span data-ttu-id="11fd0-444">ジェネレーション 2 の終了時にも同じコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-444">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="11fd0-445">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="11fd0-445">**!dumpheap –stat**</span></span>

  <span data-ttu-id="11fd0-446">出力の例を以下に示します (最も多くの領域を使用しているオブジェクトのみが示されています)。</span><span class="sxs-lookup"><span data-stu-id="11fd0-446">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  <span data-ttu-id="11fd0-447">出力の末尾から `double[]` オブジェクトがなくなっているため、これらがコレクションの対象になったことがわかります。</span><span class="sxs-lookup"><span data-stu-id="11fd0-447">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="11fd0-448">これらのオブジェクトは約 70 MB を占めています。</span><span class="sxs-lookup"><span data-stu-id="11fd0-448">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="11fd0-449">その他のオブジェクトはあまり変更されていません。</span><span class="sxs-lookup"><span data-stu-id="11fd0-449">The remaining objects did not change much.</span></span> <span data-ttu-id="11fd0-450">したがって、これらの `double[]` オブジェクトが、このジェネレーション 2 のガベージ コレクションが発生した原因です。</span><span class="sxs-lookup"><span data-stu-id="11fd0-450">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="11fd0-451">ガベージ コレクションが発生した原因がわかったら、今度は、これらの `double[]` オブジェクトが存在する理由と、死んだ状態になった理由を特定します。</span><span class="sxs-lookup"><span data-stu-id="11fd0-451">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="11fd0-452">コードの開発者にたずねることも、**gcroot** コマンドを使用して確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-452">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="11fd0-453">CPU の使用率が高いのはガベージ コレクションのためかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="11fd0-453">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="11fd0-454">`% Time in GC` メモリ パフォーマンス カウンターの値と処理時間を互いに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-454">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="11fd0-455">`% Time in GC` の値と処理時間が同時に急激に増加している場合は、CPU の使用率が高いのはガベージ コレクションのためです。</span><span class="sxs-lookup"><span data-stu-id="11fd0-455">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="11fd0-456">それ以外の場合は、アプリケーションのプロファイリングを実行して、使用率の高い箇所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="11fd0-456">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="11fd0-457">関連項目</span><span class="sxs-lookup"><span data-stu-id="11fd0-457">See also</span></span>

- [<span data-ttu-id="11fd0-458">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="11fd0-458">Garbage Collection</span></span>](index.md)
