---
title: dotnet-counters 診断ツール - .NET CLI
description: dotnet-counter CLI ツールをインストールし、アドホックな正常性監視と最初のレベルのパフォーマンス調査に使用する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: 44d74cfaca7483b1506fe7ad762818e9b9ed7d63
ms.sourcegitcommit: 0273f8845eb1ea8de64086bef2271b4f22182c91
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2021
ms.locfileid: "98058091"
---
# <a name="investigate-performance-counters-dotnet-counters"></a><span data-ttu-id="338d1-103">パフォーマンス カウンターを調べる (dotnet-counters)</span><span class="sxs-lookup"><span data-stu-id="338d1-103">Investigate performance counters (dotnet-counters)</span></span>

<span data-ttu-id="338d1-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="338d1-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="338d1-105">インストール</span><span class="sxs-lookup"><span data-stu-id="338d1-105">Install</span></span>

<span data-ttu-id="338d1-106">`dotnet-counters` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="338d1-106">There are two ways to download and install `dotnet-counters`:</span></span>

- <span data-ttu-id="338d1-107">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="338d1-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="338d1-108">`dotnet-counters` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-counters)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="338d1-108">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-counters
  ```

- <span data-ttu-id="338d1-109">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="338d1-109">**Direct download:**</span></span>

  <span data-ttu-id="338d1-110">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="338d1-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="338d1-111">OS</span><span class="sxs-lookup"><span data-stu-id="338d1-111">OS</span></span>  | <span data-ttu-id="338d1-112">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="338d1-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="338d1-113">Windows</span><span class="sxs-lookup"><span data-stu-id="338d1-113">Windows</span></span> | <span data-ttu-id="338d1-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="338d1-114">[x86](https://aka.ms/dotnet-counters/win-x86) \| [x64](https://aka.ms/dotnet-counters/win-x64) \| [arm](https://aka.ms/dotnet-counters/win-arm) \| [arm-x64](https://aka.ms/dotnet-counters/win-arm64)</span></span> |
  | <span data-ttu-id="338d1-115">macOS</span><span class="sxs-lookup"><span data-stu-id="338d1-115">macOS</span></span>   | [<span data-ttu-id="338d1-116">x64</span><span class="sxs-lookup"><span data-stu-id="338d1-116">x64</span></span>](https://aka.ms/dotnet-counters/osx-x64) |
  | <span data-ttu-id="338d1-117">Linux</span><span class="sxs-lookup"><span data-stu-id="338d1-117">Linux</span></span>   | <span data-ttu-id="338d1-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="338d1-118">[x64](https://aka.ms/dotnet-counters/linux-x64) \| [arm](https://aka.ms/dotnet-counters/linux-arm) \| [arm64](https://aka.ms/dotnet-counters/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-counters/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-counters/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="338d1-119">構文</span><span class="sxs-lookup"><span data-stu-id="338d1-119">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="338d1-120">説明</span><span class="sxs-lookup"><span data-stu-id="338d1-120">Description</span></span>

<span data-ttu-id="338d1-121">`dotnet-counters` は、アドホックな正常性監視と第 1 レベルのパフォーマンス調査のためのパフォーマンス監視ツールです。</span><span class="sxs-lookup"><span data-stu-id="338d1-121">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="338d1-122"><xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-122">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="338d1-123">たとえば、CPU 使用率や .NET Core アプリケーションでスローされる例外の発生率などを迅速に監視して、`PerfView` または `dotnet-trace` を使用した、より重大なパフォーマンス調査を開始する前に疑わしいものがあるかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="338d1-124">オプション</span><span class="sxs-lookup"><span data-stu-id="338d1-124">Options</span></span>

- **`--version`**

  <span data-ttu-id="338d1-125">dotnet-counters ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="338d1-125">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="338d1-126">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="338d1-126">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="338d1-127">コマンド</span><span class="sxs-lookup"><span data-stu-id="338d1-127">Commands</span></span>

| <span data-ttu-id="338d1-128">コマンド</span><span class="sxs-lookup"><span data-stu-id="338d1-128">Command</span></span>                                             |
|-----------------------------------------------------|
| [<span data-ttu-id="338d1-129">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="338d1-129">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="338d1-130">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="338d1-130">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="338d1-131">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="338d1-131">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="338d1-132">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="338d1-132">dotnet-counters ps</span></span>](#dotnet-counters-ps)           |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="338d1-133">dotnet-counters collect</span><span class="sxs-lookup"><span data-stu-id="338d1-133">dotnet-counters collect</span></span>

<span data-ttu-id="338d1-134">選択されたカウンター値を定期的に収集し、後処理用に指定されたファイル形式にエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="338d1-134">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="338d1-135">構文</span><span class="sxs-lookup"><span data-stu-id="338d1-135">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters <COUNTERS>] [--format] [-o|--output] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="338d1-136">オプション</span><span class="sxs-lookup"><span data-stu-id="338d1-136">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="338d1-137">カウンター データを収集するプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="338d1-137">The ID of the process to be collect counter data from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="338d1-138">カウンター データを収集するプロセスの名前。</span><span class="sxs-lookup"><span data-stu-id="338d1-138">The name of the process to be collect counter data from.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="338d1-139">作成する診断ポートの名前。</span><span class="sxs-lookup"><span data-stu-id="338d1-139">The name of the diagnostic port to create.</span></span> <span data-ttu-id="338d1-140">このオプションを使用し、アプリの起動からカウンターの監視を開始する方法については、「[診断ポートの使用](#using-diagnostic-port)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="338d1-140">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="338d1-141">表示されているカウンターを更新するまでの遅延時間 (秒数)</span><span class="sxs-lookup"><span data-stu-id="338d1-141">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="338d1-142">カウンターのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="338d1-142">A comma-separated list of counters.</span></span> <span data-ttu-id="338d1-143">カウンターは `provider_name[:counter_name]` で指定できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-143">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="338d1-144">`provider_name` をカウンターの限定リストを指定せずに使用した場合、そのプロバイダーのすべてのカウンターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="338d1-144">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="338d1-145">プロバイダーとカウンターの名前を検出するには、[dotnet-counters list](#dotnet-counters-list) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="338d1-145">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="338d1-146">エクスポートされる形式。</span><span class="sxs-lookup"><span data-stu-id="338d1-146">The format to be exported.</span></span> <span data-ttu-id="338d1-147">現在使用可能: csv、json。</span><span class="sxs-lookup"><span data-stu-id="338d1-147">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="338d1-148">出力ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="338d1-148">The name of the output file.</span></span>

- <span data-ttu-id="338d1-149">**`-- <command>` (対象アプリケーションが .NET 5.0 以降を実行している場合のみ)**</span><span class="sxs-lookup"><span data-stu-id="338d1-149">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="338d1-150">ユーザーは、コレクション構成パラメーターの後に `--` を付加し、5.0 以降のランタイムで .NET アプリケーションを起動するコマンドを続けて指定できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-150">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="338d1-151">`dotnet-counters` を使用して、指定したコマンドでプロセスを起動し、要求したメトリックを収集します。</span><span class="sxs-lookup"><span data-stu-id="338d1-151">`dotnet-counters` will launch a process with the provided command and collect the requested metrics.</span></span> <span data-ttu-id="338d1-152">これは、アプリケーションの起動パスのメトリックを収集するのに役立つことが多く、メイン エントリポイントの前または直後に発生する問題を診断または監視するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-152">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="338d1-153">このオプションを使用して、ツールに応答する最初の .NET 5.0 プロセスを監視します。つまり、コマンドから複数の .NET アプリケーションを起動する場合、最初のアプリのみ収集されます。</span><span class="sxs-lookup"><span data-stu-id="338d1-153">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="338d1-154">このため、このオプションについては、自己完結型アプリケーションに対して使用するか、または `dotnet exec <app.dll>` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="338d1-154">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="338d1-155">dotnet-counters を使用して .NET 実行可能ファイルを起動すると、その入力/出力がリダイレクトされ、その stdin/stdout とやりとりができなくなります。</span><span class="sxs-lookup"><span data-stu-id="338d1-155">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="338d1-156">CTRL + C または SIGTERM を介してツールを終了すると、ツールと子プロセスの両方が安全に終了します。</span><span class="sxs-lookup"><span data-stu-id="338d1-156">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="338d1-157">ツールの前に子プロセスが終了すると、ツールも終了し、トレースを安全に表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="338d1-157">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span> <span data-ttu-id="338d1-158">stdin/stdout を使用する必要がある場合は、`--diagnostic-port` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="338d1-158">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="338d1-159">詳細については、「[診断ポートの使用](#using-diagnostic-port)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="338d1-159">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

### <a name="examples"></a><span data-ttu-id="338d1-160">使用例</span><span class="sxs-lookup"><span data-stu-id="338d1-160">Examples</span></span>

- <span data-ttu-id="338d1-161">すべてのカウンターを更新間隔 3 秒で収集し、csv を出力として生成します。</span><span class="sxs-lookup"><span data-stu-id="338d1-161">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

- <span data-ttu-id="338d1-162">子プロセスとして `dotnet mvc.dll` を開始し、起動時からランタイム カウンターと ASP.NET Core ホスティング カウンターの収集を開始し、JSON 出力として保存します。</span><span class="sxs-lookup"><span data-stu-id="338d1-162">Start `dotnet mvc.dll` as a child process and start collecting runtime counters and ASP.NET Core Hosting counters from startup and save it as a JSON output:</span></span>

  ```console
  > dotnet-counters collect --format json --counters System.Runtime,Microsoft.AspNetCore.Hosting -- dotnet mvc.dll
  Starting a counter session. Press Q to quit.
  File saved to counter.json
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="338d1-163">dotnet-counters list</span><span class="sxs-lookup"><span data-stu-id="338d1-163">dotnet-counters list</span></span>

<span data-ttu-id="338d1-164">カウンターの名前と説明の一覧をプロバイダー別にグループ化して表示します。</span><span class="sxs-lookup"><span data-stu-id="338d1-164">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="338d1-165">構文</span><span class="sxs-lookup"><span data-stu-id="338d1-165">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="338d1-166">例</span><span class="sxs-lookup"><span data-stu-id="338d1-166">Example</span></span>

```console
> dotnet-counters list
Showing well-known counters only. Specific processes may support additional counters.

System.Runtime
    cpu-usage                                    Amount of time the process has utilized the CPU (ms)
    working-set                                  Amount of working set used by the process (MB)
    gc-heap-size                                 Total heap size reported by the GC (MB)
    gen-0-gc-count                               Number of Gen 0 GCs per interval
    gen-1-gc-count                               Number of Gen 1 GCs per interval
    gen-2-gc-count                               Number of Gen 2 GCs per interval
    time-in-gc                                   % time in GC since the last GC
    gen-0-size                                   Gen 0 Heap Size
    gen-1-size                                   Gen 1 Heap Size
    gen-2-size                                   Gen 2 Heap Size
    loh-size                                     LOH Heap Size
    alloc-rate                                   Allocation Rate
    assembly-count                               Number of Assemblies Loaded
    exception-count                              Number of Exceptions per interval
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
> <span data-ttu-id="338d1-167">`Microsoft.AspNetCore.Hosting` カウンターは、そのようなカウンターをサポートするプロセスが特定されたときに表示されます。たとえば、ホスト マシンで ASP.NET Core アプリケーションが実行されているときです。</span><span class="sxs-lookup"><span data-stu-id="338d1-167">The `Microsoft.AspNetCore.Hosting` counters are displayed when there are processes identified that support these counters, for example; when an ASP.NET Core application is running on the host machine.</span></span>

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="338d1-168">dotnet-counters monitor</span><span class="sxs-lookup"><span data-stu-id="338d1-168">dotnet-counters monitor</span></span>

<span data-ttu-id="338d1-169">選択したカウンターの定期的に更新される値を表示します。</span><span class="sxs-lookup"><span data-stu-id="338d1-169">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="338d1-170">構文</span><span class="sxs-lookup"><span data-stu-id="338d1-170">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [-n|--name] [--diagnostic-port] [--refresh-interval] [--counters] [-- <command>]
```

### <a name="options"></a><span data-ttu-id="338d1-171">オプション</span><span class="sxs-lookup"><span data-stu-id="338d1-171">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="338d1-172">監視するプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="338d1-172">The ID of the process to be monitored.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="338d1-173">監視するプロセスの名前。</span><span class="sxs-lookup"><span data-stu-id="338d1-173">The name of the process to be monitored.</span></span>

- **`--diagnostic-port`**

  <span data-ttu-id="338d1-174">作成する診断ポートの名前。</span><span class="sxs-lookup"><span data-stu-id="338d1-174">The name of the diagnostic port to create.</span></span> <span data-ttu-id="338d1-175">このオプションを使用し、アプリの起動からカウンターの監視を開始する方法については、「[診断ポートの使用](#using-diagnostic-port)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="338d1-175">See [using diagnostic port](#using-diagnostic-port) for how to use this option to start monitoring counters from app startup.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="338d1-176">表示されているカウンターを更新するまでの遅延時間 (秒数)</span><span class="sxs-lookup"><span data-stu-id="338d1-176">The number of seconds to delay between updating the displayed counters</span></span>

- **`--counters <COUNTERS>`**

  <span data-ttu-id="338d1-177">カウンターのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="338d1-177">A comma-separated list of counters.</span></span> <span data-ttu-id="338d1-178">カウンターは `provider_name[:counter_name]` で指定できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-178">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="338d1-179">`provider_name` をカウンターの限定リストを指定せずに使用した場合、そのプロバイダーのすべてのカウンターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="338d1-179">If the `provider_name` is used without a qualifying list of counters, then all counters from the provider are shown.</span></span> <span data-ttu-id="338d1-180">プロバイダーとカウンターの名前を検出するには、[dotnet-counters list](#dotnet-counters-list) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="338d1-180">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

 <span data-ttu-id="338d1-181">**`-- <command>` (対象アプリケーションが .NET 5.0 以降を実行している場合のみ)**</span><span class="sxs-lookup"><span data-stu-id="338d1-181">**`-- <command>` (for target applications running .NET 5.0 or later only)**</span></span>

  <span data-ttu-id="338d1-182">ユーザーは、コレクション構成パラメーターの後に `--` を付加し、5.0 以降のランタイムで .NET アプリケーションを起動するコマンドを続けて指定できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-182">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="338d1-183">`dotnet-counters` を使用して、指定したコマンドでプロセスを起動し、要求したメトリックを監視します。</span><span class="sxs-lookup"><span data-stu-id="338d1-183">`dotnet-counters` will launch a process with the provided command and monitor the requested metrics.</span></span> <span data-ttu-id="338d1-184">これは、アプリケーションの起動パスのメトリックを収集するのに役立つことが多く、メイン エントリポイントの前または直後に発生する問題を診断または監視するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-184">This is often useful to collect metrics for the application's startup path and can be used to diagnose or monitor issues that happen early before or shortly after the main entrypoint.</span></span>

  > [!NOTE]
  > <span data-ttu-id="338d1-185">このオプションを使用して、ツールに応答する最初の .NET 5.0 プロセスを監視します。つまり、コマンドから複数の .NET アプリケーションを起動する場合、最初のアプリのみ収集されます。</span><span class="sxs-lookup"><span data-stu-id="338d1-185">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="338d1-186">このため、このオプションについては、自己完結型アプリケーションに対して使用するか、または `dotnet exec <app.dll>` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="338d1-186">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

  > [!NOTE]
  > <span data-ttu-id="338d1-187">dotnet-counters を使用して .NET 実行可能ファイルを起動すると、その入力/出力がリダイレクトされ、その stdin/stdout とやりとりができなくなります。</span><span class="sxs-lookup"><span data-stu-id="338d1-187">Launching a .NET executable via dotnet-counters will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span> <span data-ttu-id="338d1-188">CTRL + C または SIGTERM を介してツールを終了すると、ツールと子プロセスの両方が安全に終了します。</span><span class="sxs-lookup"><span data-stu-id="338d1-188">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span> <span data-ttu-id="338d1-189">ツールの前に子プロセスが終了すると、ツールも終了します。</span><span class="sxs-lookup"><span data-stu-id="338d1-189">If the child process exits before the tool, the tool will exit as well.</span></span> <span data-ttu-id="338d1-190">stdin/stdout を使用する必要がある場合は、`--diagnostic-port` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="338d1-190">If you need to use stdin/stdout, you can use the `--diagnostic-port` option.</span></span> <span data-ttu-id="338d1-191">詳細については、「[診断ポートの使用](#using-diagnostic-port)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="338d1-191">See [Using diagnostic port](#using-diagnostic-port) for more information.</span></span>

### <a name="examples"></a><span data-ttu-id="338d1-192">例</span><span class="sxs-lookup"><span data-stu-id="338d1-192">Examples</span></span>

- <span data-ttu-id="338d1-193">3 秒の更新間隔で `System.Runtime` のすべてのカウンターを監視します。</span><span class="sxs-lookup"><span data-stu-id="338d1-193">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="338d1-194">`System.Runtime` から CPU 使用率と GC ヒープ サイズのみを監視します。</span><span class="sxs-lookup"><span data-stu-id="338d1-194">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="338d1-195">ユーザー定義の `EventSource` の `EventCounter` 値を監視します。</span><span class="sxs-lookup"><span data-stu-id="338d1-195">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="338d1-196">詳しくは、「[チュートリアル: .NET Core で EventCounters を使用してパフォーマンスを測定する](event-counter-perf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="338d1-196">For more information, see [Tutorial: Measure performance using EventCounters in .NET Core](event-counter-perf.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 --counters Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```

- <span data-ttu-id="338d1-197">`dotnet-counters` で利用できるすべての既知のカウンターを表示する:</span><span class="sxs-lookup"><span data-stu-id="338d1-197">View all well-known counters that are available in `dotnet-counters`:</span></span>

  ```console
  > dotnet-counters list

  Showing well-known counters for .NET (Core) version 3.1 only. Specific processes may support additional counters.
  System.Runtime              
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active

  Microsoft.AspNetCore.Hosting
      requests-per-second                Number of requests between update intervals
      total-requests                     Total number of requests
      current-requests                   Current number of requests
      failed-requests                    Failed number of requests
  ```

- <span data-ttu-id="338d1-198">.NET 5 アプリに対して `dotnet-counters` で利用できるすべての既知のカウンターを表示する:</span><span class="sxs-lookup"><span data-stu-id="338d1-198">View all well-known counters that are available in `dotnet-counters` for .NET 5 apps:</span></span>

  ```console
  > dotnet-counters list --runtime-version 5.0

  Showing well-known counters for .NET (Core) version 5.0 only. Specific processes may support additional counters.
  System.Runtime                     
      cpu-usage                          The percent of process' CPU usage relative to all of the system CPU resources [0-100]
      working-set                        Amount of working set used by the process (MB)
      gc-heap-size                       Total heap size reported by the GC (MB)
      gen-0-gc-count                     Number of Gen 0 GCs between update intervals
      gen-1-gc-count                     Number of Gen 1 GCs between update intervals
      gen-2-gc-count                     Number of Gen 2 GCs between update intervals
      time-in-gc                         % time in GC since the last GC
      gen-0-size                         Gen 0 Heap Size
      gen-1-size                         Gen 1 Heap Size
      gen-2-size                         Gen 2 Heap Size
      loh-size                           LOH Size
      poh-size                           POH (Pinned Object Heap) Size
      alloc-rate                         Number of bytes allocated in the managed heap between update intervals
      gc-fragmentation                   GC Heap Fragmentation
      assembly-count                     Number of Assemblies Loaded
      exception-count                    Number of Exceptions / sec
      threadpool-thread-count            Number of ThreadPool Threads
      monitor-lock-contention-count      Number of times there were contention when trying to take the monitor lock between update intervals
      threadpool-queue-length            ThreadPool Work Items Queue Length
      threadpool-completed-items-count   ThreadPool Completed Work Items Count
      active-timer-count                 Number of timers that are currently active
      il-bytes-jitted                    Total IL bytes jitted
      methods-jitted-count               Number of methods jitted

  Microsoft.AspNetCore.Hosting       
      requests-per-second   Number of requests between update intervals
      total-requests        Total number of requests
      current-requests      Current number of requests
      failed-requests       Failed number of requests

  Microsoft-AspNetCore-Server-Kestrel
      connections-per-second      Number of connections between update intervals
      total-connections           Total Connections
      tls-handshakes-per-second   Number of TLS Handshakes made between update intervals
      total-tls-handshakes        Total number of TLS handshakes made
      current-tls-handshakes      Number of currently active TLS handshakes
      failed-tls-handshakes       Total number of failed TLS handshakes
      current-connections         Number of current connections
      connection-queue-length     Length of Kestrel Connection Queue
      request-queue-length        Length total HTTP request queue

  System.Net.Http                    
      requests-started        Total Requests Started
      requests-started-rate   Number of Requests Started between update intervals
      requests-aborted        Total Requests Aborted
      requests-aborted-rate   Number of Requests Aborted between update intervals
      current-requests        Current Requests
  ```

- <span data-ttu-id="338d1-199">`my-aspnet-server.exe` を起動し、起動時から読み込まれるアセンブリの数を監視します (.NET 5.0 以降のみ)。</span><span class="sxs-lookup"><span data-stu-id="338d1-199">Launch `my-aspnet-server.exe` and monitor the # of assemblies loaded from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="338d1-200">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="338d1-200">This works for apps running .NET 5.0 or later only.</span></span>

  ```console
  > dotnet-counters monitor --counters System.Runtime[assembly-count] -- my-aspnet-server.exe

  Press p to pause, r to resume, q to quit.
    Status: Running

  [System.Runtime]
      Number of Assemblies Loaded                   24
  ```
  
- <span data-ttu-id="338d1-201">コマンドライン引数に `arg1` と `arg2` を指定して `my-aspnet-server.exe` を起動し、その動作セットと起動時の GC ヒープ サイズを監視します (.NET 5.0 以降のみ)。</span><span class="sxs-lookup"><span data-stu-id="338d1-201">Launch `my-aspnet-server.exe` with `arg1` and `arg2` as command-line arguments and monitor its working set and GC heap size from its startup (.NET 5.0 or later only):</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="338d1-202">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="338d1-202">This works for apps running .NET 5.0 or later only.</span></span>

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

## <a name="dotnet-counters-ps"></a><span data-ttu-id="338d1-203">dotnet-counters ps</span><span class="sxs-lookup"><span data-stu-id="338d1-203">dotnet-counters ps</span></span>

<span data-ttu-id="338d1-204">監視できる dotnet プロセスの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="338d1-204">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="338d1-205">概要</span><span class="sxs-lookup"><span data-stu-id="338d1-205">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="338d1-206">例</span><span class="sxs-lookup"><span data-stu-id="338d1-206">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/user/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```

## <a name="using-diagnostic-port"></a><span data-ttu-id="338d1-207">診断ポートの使用</span><span class="sxs-lookup"><span data-stu-id="338d1-207">Using diagnostic port</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="338d1-208">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="338d1-208">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="338d1-209">診断ポートは、監視やカウンターの収集をアプリの起動から開始できる、.NET 5 で追加された新しいランタイム機能です。</span><span class="sxs-lookup"><span data-stu-id="338d1-209">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start monitoring or collecting counters from app startup.</span></span> <span data-ttu-id="338d1-210">`dotnet-counters` を使用してこれを行うには、上記の例の説明に従って `dotnet-counters <collect|monitor> -- <command>` を使用するか、`--diagnostic-port` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="338d1-210">To do this using `dotnet-counters`, you can either use `dotnet-counters <collect|monitor> -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="338d1-211">起動からすぐにアプリケーションを監視するには、`dotnet-counters <collect|monitor> -- <command>` を使用して子プロセスとしてアプリケーションを起動するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="338d1-211">Using `dotnet-counters <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly monitor it from its startup.</span></span>

<span data-ttu-id="338d1-212">ただし、(アプリを最初の 10 分だけ監視し、実行を継続するなど) 監視しているアプリの有効期間をより細かく制御する場合、または CLI を使用してアプリと対話する必要がある場合は、`--diagnostic-port` オプションを使用すると、監視対象アプリと `dotnet-counters` の両方を制御できます。</span><span class="sxs-lookup"><span data-stu-id="338d1-212">However, when you want to gain a finer control over the lifetime of the app being monitored (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-counters`.</span></span>

1. <span data-ttu-id="338d1-213">次のコマンドにより、dotnet-counters は `myport.sock` という名前の診断ソケットを作成し、接続を待機します。</span><span class="sxs-lookup"><span data-stu-id="338d1-213">The command below makes dotnet-counters create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-counters collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="338d1-214">出力:</span><span class="sxs-lookup"><span data-stu-id="338d1-214">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="338d1-215">別のコンソールで、`dotnet-counters` の出力値に設定された環境変数 `DOTNET_DiagnosticPorts` を使用して対象アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="338d1-215">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-counters` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="338d1-216">これにより、`dotnet-counters` が `my-dotnet-app` でカウンターを収集し始めます。</span><span class="sxs-lookup"><span data-stu-id="338d1-216">This should then enable `dotnet-counters` to start collecting counters on `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="338d1-217">`dotnet run` を使用してアプリを起動すると、dotnet CLI によってお使いのアプリのものではない子プロセスが多数生成され、お使いのアプリに先立ってそれらが `dotnet-counters` に接続されてしまい、実行時にお使いのアプリが中断されることで、問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="338d1-217">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-counters` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="338d1-218">アプリケーションの起動には、アプリの自己完結型バージョンを直接使用するか、`dotnet exec` を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="338d1-218">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>
