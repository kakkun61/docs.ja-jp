---
title: dotnet-trace 診断ツール - .NET CLI
description: dotnet-trace CLI ツールをインストールして使用し、.NET EventPipe を使って、ネイティブ プロファイラーなしで実行中のプロセスの .NET トレースを収集する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: 868ce7828eee6bd7f2101d5d6a65c7f7bf87fe24
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009535"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="35523-103">dotnet-trace パフォーマンス分析ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="35523-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="35523-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="35523-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="35523-105">インストール</span><span class="sxs-lookup"><span data-stu-id="35523-105">Install</span></span>

<span data-ttu-id="35523-106">`dotnet-trace` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="35523-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="35523-107">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="35523-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="35523-108">`dotnet-trace` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-trace)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="35523-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="35523-109">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="35523-109">**Direct download:**</span></span>

  <span data-ttu-id="35523-110">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="35523-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="35523-111">OS</span><span class="sxs-lookup"><span data-stu-id="35523-111">OS</span></span>  | <span data-ttu-id="35523-112">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="35523-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="35523-113">Windows</span><span class="sxs-lookup"><span data-stu-id="35523-113">Windows</span></span> | <span data-ttu-id="35523-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="35523-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="35523-115">macOS</span><span class="sxs-lookup"><span data-stu-id="35523-115">macOS</span></span>   | [<span data-ttu-id="35523-116">x64</span><span class="sxs-lookup"><span data-stu-id="35523-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="35523-117">Linux</span><span class="sxs-lookup"><span data-stu-id="35523-117">Linux</span></span>   | <span data-ttu-id="35523-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="35523-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="35523-119">構文</span><span class="sxs-lookup"><span data-stu-id="35523-119">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="35523-120">説明</span><span class="sxs-lookup"><span data-stu-id="35523-120">Description</span></span>

<span data-ttu-id="35523-121">`dotnet-trace` ツール:</span><span class="sxs-lookup"><span data-stu-id="35523-121">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="35523-122">クロスプラットフォーム .NET Core ツールです。</span><span class="sxs-lookup"><span data-stu-id="35523-122">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="35523-123">ネイティブ プロファイラーなしで実行中のプロセスの .NET Core トレースを回収できます。</span><span class="sxs-lookup"><span data-stu-id="35523-123">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="35523-124">.NET Core ランタイムの [`EventPipe`](./eventpipe.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="35523-124">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="35523-125">Windows、Linux または macOS でも同じエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="35523-125">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="35523-126">オプション</span><span class="sxs-lookup"><span data-stu-id="35523-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="35523-127">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="35523-127">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="35523-128">dotnet-trace ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="35523-128">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="35523-129">コマンド</span><span class="sxs-lookup"><span data-stu-id="35523-129">Commands</span></span>

| <span data-ttu-id="35523-130">コマンド</span><span class="sxs-lookup"><span data-stu-id="35523-130">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="35523-131">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="35523-131">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="35523-132">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="35523-132">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="35523-133">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="35523-133">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="35523-134">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="35523-134">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="35523-135">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="35523-135">dotnet-trace collect</span></span>

<span data-ttu-id="35523-136">実行中のプロセスから診断トレースを収集します。</span><span class="sxs-lookup"><span data-stu-id="35523-136">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="35523-137">構文</span><span class="sxs-lookup"><span data-stu-id="35523-137">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="35523-138">オプション</span><span class="sxs-lookup"><span data-stu-id="35523-138">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="35523-139">メモリ内の循環バッファーのサイズをメガバイトに設定します。</span><span class="sxs-lookup"><span data-stu-id="35523-139">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="35523-140">既定は 256 MB です。</span><span class="sxs-lookup"><span data-stu-id="35523-140">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="35523-141">生成される CLR イベントの詳細度。</span><span class="sxs-lookup"><span data-stu-id="35523-141">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="35523-142">生成する CLR ランタイム イベントの一覧。</span><span class="sxs-lookup"><span data-stu-id="35523-142">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="35523-143">トレース ファイルの出力の変換形式を設定します。</span><span class="sxs-lookup"><span data-stu-id="35523-143">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="35523-144">既定値は、`NetTrace` です。</span><span class="sxs-lookup"><span data-stu-id="35523-144">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="35523-145">トレースを収集するプロセスの名前。</span><span class="sxs-lookup"><span data-stu-id="35523-145">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="35523-146">作成する診断ポートの名前。</span><span class="sxs-lookup"><span data-stu-id="35523-146">The name of the diagnostic port to create.</span></span> <span data-ttu-id="35523-147">このオプションを使用してアプリの起動からトレースを収集する方法については、「[診断ポートを使用してアプリの起動からトレースを収集する](#use-diagnostic-port-to-collect-a-trace-from-app-startup)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35523-147">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="35523-148">収集されたトレース データの出力パス。</span><span class="sxs-lookup"><span data-stu-id="35523-148">The output path for the collected trace data.</span></span> <span data-ttu-id="35523-149">指定しない場合の既定値は `trace.nettrace` です。</span><span class="sxs-lookup"><span data-stu-id="35523-149">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="35523-150">トレースを収集するプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="35523-150">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="35523-151">共通のトレース シナリオを簡潔に指定できるようにする、事前定義されたプロバイダーの名前付き構成のセット。</span><span class="sxs-lookup"><span data-stu-id="35523-151">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="35523-152">次のプロファイルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="35523-152">The following profiles are available:</span></span>

 | <span data-ttu-id="35523-153">[プロファイル]</span><span class="sxs-lookup"><span data-stu-id="35523-153">Profile</span></span> | <span data-ttu-id="35523-154">説明</span><span class="sxs-lookup"><span data-stu-id="35523-154">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="35523-155">CPU 使用率および一般的な .NET ランタイム情報の追跡に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="35523-155">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="35523-156">プロファイルまたはプロバイダーが指定されていない場合は、これが既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="35523-156">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="35523-157">GC コレクションを追跡し、オブジェクトの割り当てをサンプリングします。</span><span class="sxs-lookup"><span data-stu-id="35523-157">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="35523-158">オーバーヘッドが非常に低い場合にのみ GC コレクションを追跡します。</span><span class="sxs-lookup"><span data-stu-id="35523-158">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="35523-159">有効にする `EventPipe` プロバイダーのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="35523-159">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="35523-160">これらのプロバイダーは、`--profile <profile-name>` で示されている任意のプロバイダーを補完します。</span><span class="sxs-lookup"><span data-stu-id="35523-160">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="35523-161">特定のプロバイダーに不整合がある場合、この構成がプロファイルの暗黙的な構成に優先されます。</span><span class="sxs-lookup"><span data-stu-id="35523-161">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="35523-162">プロバイダーの一覧の形式は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35523-162">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="35523-163">`Provider` は、`KnownProviderName[:Flags[:Level][:KeyValueArgs]]` という形式です。</span><span class="sxs-lookup"><span data-stu-id="35523-163">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="35523-164">`KeyValueArgs` は、`[key1=value1][;key2=value2]` という形式です。</span><span class="sxs-lookup"><span data-stu-id="35523-164">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="35523-165">**`-- <command>` (.NET 5.0 のみを実行しているターゲット アプリケーションの場合)**</span><span class="sxs-lookup"><span data-stu-id="35523-165">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="35523-166">ユーザーは、コレクション構成パラメーターの後にまず `--`、次にコマンドを追加すれば、5.0 以降のランタイムで .NET アプリケーションを起動することができます。</span><span class="sxs-lookup"><span data-stu-id="35523-166">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="35523-167">これは、起動時のパフォーマンスの問題やアセンブリ ローダーおよびバインダーのエラーなど、プロセスの早い段階で発生する問題を診断するのに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="35523-167">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="35523-168">このオプションを使用すると、ツールに返信する最初の .NET 5.0 プロセスが監視されます。つまり、ご利用のコマンドで複数の .NET アプリケーションが起動される場合、収集されるのは最初のアプリのみとなります。</span><span class="sxs-lookup"><span data-stu-id="35523-168">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="35523-169">このため、このオプションについては、自己完結型アプリケーションに対して使用するか、または `dotnet exec <app.dll>` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35523-169">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="35523-170">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="35523-170">dotnet-trace convert</span></span>

<span data-ttu-id="35523-171">`nettrace` トレースを、別のトレース分析ツールで使用するために、別の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="35523-171">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="35523-172">構文</span><span class="sxs-lookup"><span data-stu-id="35523-172">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="35523-173">引数</span><span class="sxs-lookup"><span data-stu-id="35523-173">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="35523-174">変換する入力トレース ファイル。</span><span class="sxs-lookup"><span data-stu-id="35523-174">Input trace file to be converted.</span></span> <span data-ttu-id="35523-175">既定は *trace.nettrace* です。</span><span class="sxs-lookup"><span data-stu-id="35523-175">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="35523-176">オプション</span><span class="sxs-lookup"><span data-stu-id="35523-176">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="35523-177">トレース ファイルの出力の変換形式を設定します。</span><span class="sxs-lookup"><span data-stu-id="35523-177">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="35523-178">出力ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="35523-178">Output filename.</span></span> <span data-ttu-id="35523-179">ターゲットの形式の拡張子が追加されます。</span><span class="sxs-lookup"><span data-stu-id="35523-179">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="35523-180">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="35523-180">dotnet-trace ps</span></span>

 <span data-ttu-id="35523-181">トレースを収集できる dotnet プロセスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35523-181">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="35523-182">構文</span><span class="sxs-lookup"><span data-stu-id="35523-182">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="35523-183">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="35523-183">dotnet-trace list-profiles</span></span>

<span data-ttu-id="35523-184">各プロファイルに含まれるプロバイダーとフィルターの記述と共に、事前に構築されているトレースのプロファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="35523-184">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="35523-185">構文</span><span class="sxs-lookup"><span data-stu-id="35523-185">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="35523-186">dotnet-trace を使用してトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="35523-186">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="35523-187">`dotnet-trace` を使用してトレースを収集するには:</span><span class="sxs-lookup"><span data-stu-id="35523-187">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="35523-188">トレースを収集する .NET Core アプリケーションのプロセス識別子 (PID) を取得します。</span><span class="sxs-lookup"><span data-stu-id="35523-188">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="35523-189">Windows で、タスク マネージャーや、たとえば、`tasklist` コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35523-189">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="35523-190">Linux の場合、たとえば、`ps` コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35523-190">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="35523-191">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="35523-191">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="35523-192">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="35523-192">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="35523-193">上のコマンドを実行すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="35523-193">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="35523-194">`<Enter>` キーを押すと、コレクションが停止します。</span><span class="sxs-lookup"><span data-stu-id="35523-194">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="35523-195">`dotnet-trace` では、*trace.nettrace* ファイルにイベントをログ記録する作業が完了します。</span><span class="sxs-lookup"><span data-stu-id="35523-195">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="35523-196">子アプリケーションを起動し、そのスタートアップからトレースを dotnet-trace を使用して収集します</span><span class="sxs-lookup"><span data-stu-id="35523-196">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35523-197">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="35523-197">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="35523-198">場合によっては、プロセスのトレースをそのスタートアップから収集すると便利なことがあります。</span><span class="sxs-lookup"><span data-stu-id="35523-198">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="35523-199">.NET 5.0 以降を実行しているアプリでは、dotnet-trace を使用してこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35523-199">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="35523-200">これを使用すると、コマンドライン引数として `arg1` と `arg2` を含む `hello.exe` が起動され、そのランタイム スタートアップからトレースが収集されます。</span><span class="sxs-lookup"><span data-stu-id="35523-200">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="35523-201">上のコマンドを実行すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="35523-201">The preceding command generates output similar to the following:</span></span>

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

<span data-ttu-id="35523-202">トレースの収集を停止するには、`<Enter>` または `<Ctrl + C>` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="35523-202">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="35523-203">この操作を行うと、`hello.exe` も終了します。</span><span class="sxs-lookup"><span data-stu-id="35523-203">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="35523-204">dotnet-trace を介して `hello.exe` を起動すると、その入力/出力がリダイレクトされ、その stdin/stdout とやりとりができなくなります。</span><span class="sxs-lookup"><span data-stu-id="35523-204">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="35523-205">CTRL + C または SIGTERM を介してツールを終了すると、ツールと子プロセスの両方が安全に終了します。</span><span class="sxs-lookup"><span data-stu-id="35523-205">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="35523-206">ツールの前に子プロセスが終了すると、ツールも終了し、トレースを安全に表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="35523-206">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="35523-207">診断ポートを使用してアプリの起動からトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="35523-207">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="35523-208">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="35523-208">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="35523-209">診断ポートは、.NET 5 で追加された新しいランタイム機能で、アプリの起動からトレースを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="35523-209">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="35523-210">`dotnet-trace` を使用してこれを行うには、上記の例の説明に従って `dotnet-trace collect -- <command>` を使用するか、`--diagnostic-port` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="35523-210">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="35523-211">起動からすばやくトレースする方法としては、アプリケーションを子プロセスとして起動するために `dotnet-trace <collect|monitor> -- <command>` を使用するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="35523-211">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="35523-212">ただし、(アプリを最初の 10 分だけ監視し、実行を継続するなど) トレースしているアプリの有効期間をより細かく制御する場合、または CLI を使用してアプリと対話する必要がある場合は、`--diagnostic-port` オプションを使用すると、監視対象アプリと `dotnet-trace` の両方を制御できます。</span><span class="sxs-lookup"><span data-stu-id="35523-212">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="35523-213">次のコマンドにより、`dotnet-trace` で `myport.sock` という名前の診断ソケットを作成し、接続を待機します。</span><span class="sxs-lookup"><span data-stu-id="35523-213">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="35523-214">出力:</span><span class="sxs-lookup"><span data-stu-id="35523-214">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="35523-215">別のコンソールで、`dotnet-trace` の出力値に設定された環境変数 `DOTNET_DiagnosticPorts` を使用して対象アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="35523-215">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="35523-216">これにより、`dotnet-trace` による `my-dotnet-app` のトレースが開始します。</span><span class="sxs-lookup"><span data-stu-id="35523-216">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="35523-217">`dotnet run` を使用してアプリを起動すると、dotnet CLI によってお使いのアプリのものではない子プロセスが多数生成され、お使いのアプリよりも先にそれらが `dotnet-trace` に接続されてしまい、実行時にお使いのアプリが中断されることで、問題が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="35523-217">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="35523-218">アプリケーションの起動には、アプリの自己完結型バージョンを直接使用するか、`dotnet exec` を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35523-218">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="35523-219">dotnet-trace からキャプチャされたトレースを表示する</span><span class="sxs-lookup"><span data-stu-id="35523-219">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="35523-220">Windows の場合、 *.nettrace* ファイルを [PerfView](https://github.com/microsoft/perfview) で表示し、分析できます。他のプラットフォームで収集されたトレースについては、トレース ファイルを Windows コンピューターに移動し、PerfView で表示できます。</span><span class="sxs-lookup"><span data-stu-id="35523-220">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="35523-221">Linux の場合、`dotnet-trace` の出力形式を `speedscope` に変更することでトレースを表示できます。</span><span class="sxs-lookup"><span data-stu-id="35523-221">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="35523-222">出力ファイル形式は `-f|--format` オプションで変更できます。`-f speedscope` により、`dotnet-trace` で `speedscope` ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="35523-222">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="35523-223">`nettrace` (既定のオプション) か `speedscope` を選択できます。</span><span class="sxs-lookup"><span data-stu-id="35523-223">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="35523-224">`Speedscope` ファイルは <https://www.speedscope.app> で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="35523-224">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="35523-225">.NET Core ランタイムにより、`nettrace` 形式でトレースが生成されます。</span><span class="sxs-lookup"><span data-stu-id="35523-225">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="35523-226">トレースの完了後、トレースは speedscope に変換されます (指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="35523-226">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="35523-227">変換によってはデータが失われる場合もあるため、元の `nettrace` ファイルが変換されたファイルの横に保持されます。</span><span class="sxs-lookup"><span data-stu-id="35523-227">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="35523-228">dotnet-trace を使用して経時的なカウンター値を収集する</span><span class="sxs-lookup"><span data-stu-id="35523-228">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="35523-229">`dotnet-trace` でできること:</span><span class="sxs-lookup"><span data-stu-id="35523-229">`dotnet-trace` can:</span></span>

* <span data-ttu-id="35523-230">パフォーマンスで左右される環境で基本的な正常性監視を行うには `EventCounter` を使用します。</span><span class="sxs-lookup"><span data-stu-id="35523-230">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="35523-231">たとえば、運用環境です。</span><span class="sxs-lookup"><span data-stu-id="35523-231">For example, in production.</span></span>
* <span data-ttu-id="35523-232">リアルタイムで表示する必要がないようにトレースを収集します。</span><span class="sxs-lookup"><span data-stu-id="35523-232">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="35523-233">たとえば、実行時のパフォーマンス カウンター値を収集するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="35523-233">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="35523-234">先のコマンドでは、正常性の簡易監視を 1 秒ごとに報告するようにランタイム カウンターに命令します。</span><span class="sxs-lookup"><span data-stu-id="35523-234">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="35523-235">`EventCounterIntervalSec=1` の値を (60 など) 大きい値に置き換えた場合、カウンター データの細分性の詳細度がより低いトレースをより少数収集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="35523-235">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="35523-236">次のコマンドでは、先のコマンドよりオーバーヘッドとトレース サイズが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="35523-236">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="35523-237">上のコマンドでは、ランタイム イベントとマネージド スタック プロファイラーが無効になります。</span><span class="sxs-lookup"><span data-stu-id="35523-237">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="35523-238">.NET プロバイダー</span><span class="sxs-lookup"><span data-stu-id="35523-238">.NET Providers</span></span>

<span data-ttu-id="35523-239">.NET Core ランタイムでは、次の .NET プロバイダーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="35523-239">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="35523-240">.NET Core では、`Event Tracing for Windows (ETW)` と `EventPipe` トレースの有効化に、いずれも同じキーワードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="35523-240">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="35523-241">プロバイダー名</span><span class="sxs-lookup"><span data-stu-id="35523-241">Provider name</span></span>                            | <span data-ttu-id="35523-242">情報</span><span class="sxs-lookup"><span data-stu-id="35523-242">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="35523-243">ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="35523-243">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="35523-244">CLR ランタイム キーワード</span><span class="sxs-lookup"><span data-stu-id="35523-244">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="35523-245">ランダウン プロバイダー</span><span class="sxs-lookup"><span data-stu-id="35523-245">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="35523-246">CLR ランダウン キーワード</span><span class="sxs-lookup"><span data-stu-id="35523-246">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="35523-247">サンプル プロファイラーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="35523-247">Enables the sample profiler.</span></span> |
