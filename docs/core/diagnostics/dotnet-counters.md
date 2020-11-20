---
title: dotnet-counters - .NET Core
description: dotnet-counter コマンドライン ツールをインストールして使用する方法について説明します。
ms.date: 02/26/2020
ms.openlocfilehash: 7ff29ad91ad271afd35e3d38a4d748bc79ad6c03
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507255"
---
# <a name="dotnet-counters"></a><span data-ttu-id="7b2cd-103">dotnet-カウンター</span><span class="sxs-lookup"><span data-stu-id="7b2cd-103">dotnet-counters</span></span>

<span data-ttu-id="7b2cd-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="7b2cd-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="7b2cd-105">dotnet-counters のインストール</span><span class="sxs-lookup"><span data-stu-id="7b2cd-105">Install dotnet-counters</span></span>

<span data-ttu-id="7b2cd-106">`dotnet-counters` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-counters)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="7b2cd-107">構文</span><span class="sxs-lookup"><span data-stu-id="7b2cd-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="7b2cd-108">説明</span><span class="sxs-lookup"><span data-stu-id="7b2cd-108">Description</span></span>

<span data-ttu-id="7b2cd-109">`dotnet-counters` は、アドホックな正常性監視と第 1 レベルのパフォーマンス調査のためのパフォーマンス監視ツールです。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="7b2cd-110"><xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="7b2cd-111">たとえば、CPU 使用率や .NET Core アプリケーションでスローされる例外の発生率などを迅速に監視して、`PerfView` または `dotnet-trace` を使用した、より重大なパフォーマンス調査を開始する前に疑わしいものがあるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="7b2cd-112">オプション</span><span class="sxs-lookup"><span data-stu-id="7b2cd-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="7b2cd-113">dotnet-counters ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7b2cd-114">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="7b2cd-115">コマンド</span><span class="sxs-lookup"><span data-stu-id="7b2cd-115">Commands</span></span>

| <span data-ttu-id="7b2cd-116">コマンド</span><span class="sxs-lookup"><span data-stu-id="7b2cd-116">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="7b2cd-117">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="7b2cd-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="7b2cd-118">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="7b2cd-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="7b2cd-119">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="7b2cd-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="7b2cd-120">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="7b2cd-120">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="7b2cd-121">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="7b2cd-121">dotnet-counters collect</span></span>

<span data-ttu-id="7b2cd-122">選択されたカウンター値を定期的に収集し、後処理用に指定されたファイル形式にエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b2cd-123">構文</span><span class="sxs-lookup"><span data-stu-id="7b2cd-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="7b2cd-124">オプション</span><span class="sxs-lookup"><span data-stu-id="7b2cd-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="7b2cd-125">監視するプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="7b2cd-126">表示されているカウンターを更新するまでの遅延時間 (秒数)</span><span class="sxs-lookup"><span data-stu-id="7b2cd-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="7b2cd-127">カウンターのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-127">A comma-separated list of counters.</span></span> <span data-ttu-id="7b2cd-128">カウンターは `provider_name[:counter_name]` で指定できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="7b2cd-129">`provider_name` をカウンターの限定リストを指定せずに使用した場合、そのプロバイダーのすべてのカウンターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-129">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="7b2cd-130">プロバイダーとカウンターの名前を検出するには、[dotnet-counters list](#dotnet-counters-list) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="7b2cd-131">エクスポートされる形式。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-131">The format to be exported.</span></span> <span data-ttu-id="7b2cd-132">現在使用可能: csv、json。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="7b2cd-133">出力ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-133">The name of the output file.</span></span>

- <span data-ttu-id="7b2cd-134">**`-- <command>` (対象アプリケーションが .NET 5.0 以降を実行している場合のみ)**</span><span class="sxs-lookup"><span data-stu-id="7b2cd-134">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="7b2cd-135">ユーザーは、コレクション構成パラメーターの後に `--` を付加し、5.0 以降のランタイムで .NET アプリケーションを起動するコマンドを続けて指定できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-135">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="7b2cd-136">`dotnet-counters` を使用して、指定したコマンドでプロセスを起動し、要求したメトリックを収集します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-136">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="7b2cd-137">これは、アプリケーションの起動パスのメトリックを収集するのに役立つことが多く、メイン エントリポイントの前または直後に発生する問題を診断または監視するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-137">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

> [!NOTE]
> <span data-ttu-id="7b2cd-138">このオプションを使用して、ツールに応答する最初の .NET 5.0 プロセスを監視します。つまり、コマンドから複数の .NET アプリケーションを起動する場合、最初のアプリのみ収集されます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-138">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="7b2cd-139">このため、このオプションを自己完結型アプリケーションで使用するか、`dotnet exec <app.dll>` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-139">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="7b2cd-140">使用例</span><span class="sxs-lookup"><span data-stu-id="7b2cd-140">Examples</span></span>

- <span data-ttu-id="7b2cd-141">すべてのカウンターを更新間隔 3 秒で収集し、csv を出力として生成します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-141">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="7b2cd-142">子プロセスとして `dotnet mvc.dll` を開始し、起動時からランタイム カウンターと ASP.NET Core ホスティング カウンターの収集を開始し、JSON 出力として保存します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-142">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="7b2cd-143">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="7b2cd-143">dotnet-counters list</span></span>

<span data-ttu-id="7b2cd-144">カウンターの名前と説明の一覧をプロバイダー別にグループ化して表示します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-144">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b2cd-145">構文</span><span class="sxs-lookup"><span data-stu-id="7b2cd-145">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="7b2cd-146">例</span><span class="sxs-lookup"><span data-stu-id="7b2cd-146">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs / min
    gen-1-gc-count                               Number of Gen 1 GCs / min
    gen-2-gc-count                               Number of Gen 2 GCs / min
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions / sec
    threadpool-thread-count                      Number of ThreadPool Threads
    monitor-lock-contention-count                Monitor Lock Contention Count
    threadpool-queue-length                      ThreadPool Work Items Queue Length
    threadpool-completed-items-count             ThreadPool Completed Work Items Count
    active-timer-count                           Active Timers Count

Microsoft.AspNetCore.Hosting
    requests-per-second                  Request rate
    total-requests                       Total number of requests
    current-requests                     Current number of requests
    failed-requests                      Failed number of requests
```

> [!NOTE]
> <span data-ttu-id="7b2cd-147">`Microsoft.AspNetCore.Hosting` カウンターは、そのようなカウンターをサポートするプロセスが特定されたときに表示されます。たとえば、ホスト マシンで ASP.NET Core アプリケーションが実行されているときです。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-147">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="7b2cd-148">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="7b2cd-148">dotnet-counters monitor</span></span>

<span data-ttu-id="7b2cd-149">選択したカウンターの定期的に更新される値を表示します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-149">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b2cd-150">構文</span><span class="sxs-lookup"><span data-stu-id="7b2cd-150">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="7b2cd-151">オプション</span><span class="sxs-lookup"><span data-stu-id="7b2cd-151">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="7b2cd-152">監視するプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-152">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="7b2cd-153">表示されているカウンターを更新するまでの遅延時間 (秒数)</span><span class="sxs-lookup"><span data-stu-id="7b2cd-153">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="7b2cd-154">カウンターのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-154">A comma-separated list of counters.</span></span> <span data-ttu-id="7b2cd-155">カウンターは `provider_name[:counter_name]` で指定できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-155">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="7b2cd-156">`provider_name` をカウンターの限定リストを指定せずに使用した場合、そのプロバイダーのすべてのカウンターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-156">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="7b2cd-157">プロバイダーとカウンターの名前を検出するには、[dotnet-counters list](#dotnet-counters-list) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-157">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="7b2cd-158">**`-- <command>` (対象アプリケーションが .NET 5.0 以降を実行している場合のみ)**</span><span class="sxs-lookup"><span data-stu-id="7b2cd-158">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="7b2cd-159">ユーザーは、コレクション構成パラメーターの後に `--` を付加し、5.0 以降のランタイムで .NET アプリケーションを起動するコマンドを続けて指定できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-159">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="7b2cd-160">`dotnet-counters` を使用して、指定したコマンドでプロセスを起動し、要求したメトリックを監視します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-160">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="7b2cd-161">これは、アプリケーションの起動パスのメトリックを収集するのに役立つことが多く、メイン エントリポイントの前または直後に発生する問題を診断または監視するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-161">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="7b2cd-162">このオプションを使用して、ツールに応答する最初の .NET 5.0 プロセスを監視します。つまり、コマンドから複数の .NET アプリケーションを起動する場合、最初のアプリのみ収集されます。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-162">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="7b2cd-163">このため、このオプションを自己完結型アプリケーションで使用するか、`dotnet exec <app.dll>` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-163">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

### <a name="examples"></a><span data-ttu-id="7b2cd-164">例</span><span class="sxs-lookup"><span data-stu-id="7b2cd-164">Examples</span></span>

- <span data-ttu-id="7b2cd-165">3 秒の更新間隔で `System.Runtime` のすべてのカウンターを監視します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-165">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 --counters System.Runtime
  Press p to pause, r to resume, q to quit.
      Status: Running

  [System.Runtime]
      % Time in GC since last GC (%)                                 0
      Allocation Rate (B / 1 sec)                                5,376
      CPU Usage (%)                                                  0
      Exception Count (Count / 1 sec)                                0
      GC Fragmentation (%)                                          48.467
      GC Heap Size (MB)                                              0
      Gen 0 GC Count (Count / 1 sec)                                 1
      Gen 0 Size (B)                                                24
      Gen 1 GC Count (Count / 1 sec)                                 1
      Gen 1 Size (B)                                                24
      Gen 2 GC Count (Count / 1 sec)                                 1
      Gen 2 Size (B)                                           272,000
      IL Bytes Jitted (B)                                       19,449
      LOH Size (B)                                              19,640
      Monitor Lock Contention Count (Count / 1 sec)                  0
      Number of Active Timers                                        0
      Number of Assemblies Loaded                                    7
      Number of Methods Jitted                                     166
      POH (Pinned Object Heap) Size (B)                             24
      ThreadPool Completed Work Item Count (Count / 1 sec)           0
      ThreadPool Queue Length                                        0
      ThreadPool Thread Count                                        2
      Working Set (MB)                                              19
  ```

- <span data-ttu-id="7b2cd-166">`System.Runtime` から CPU 使用率と GC ヒープ サイズのみを監視します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-166">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="7b2cd-167">ユーザー定義の `EventSource` の `EventCounter` 値を監視します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-167">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="7b2cd-168">詳しくは、「[チュートリアル: .NET Core で EventCounters を使用してパフォーマンスを測定する](event-counter-perf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-168">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="7b2cd-169">`my-aspnet-server.exe` を起動し、起動時から読み込まれるアセンブリの数を監視します (.NET 5.0 以降のみ)。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-169">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="7b2cd-170">注:これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-170">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="7b2cd-171">コマンドライン引数に `arg1` と `arg2` を指定して `my-aspnet-server.exe` を起動し、その動作セットと起動時の GC ヒープ サイズを監視します (.NET 5.0 以降のみ)。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-171">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  <span data-ttu-id="7b2cd-172">注:これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-172">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[working-set,gc-heap-size] -- my-aspnet-server.exe arg1 arg2
  ```

  ```console
  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      GC Heap Size (MB)                                 39
      Working Set (MB)                                  59
  ```

## <a name="dotnet-counters-ps"></a><span data-ttu-id="7b2cd-173">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="7b2cd-173">dotnet-counters ps</span></span>

<span data-ttu-id="7b2cd-174">監視できる dotnet プロセスの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="7b2cd-174">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b2cd-175">概要</span><span class="sxs-lookup"><span data-stu-id="7b2cd-175">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="7b2cd-176">例</span><span class="sxs-lookup"><span data-stu-id="7b2cd-176">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
