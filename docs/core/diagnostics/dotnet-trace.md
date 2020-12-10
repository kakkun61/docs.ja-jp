---
title: dotnet-trace 診断ツール - .NET CLI
description: dotnet-trace CLI ツールをインストールして使用し、.NET EventPipe を使って、ネイティブ プロファイラーなしで実行中のプロセスの .NET トレースを収集する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: 6bc5ad449f62ed0080ff6b1f401f1871d90cf5ec
ms.sourcegitcommit: c6de55556add9f92af17e0f8d1da8f356a19a03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2020
ms.locfileid: "96549333"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="8b945-103">dotnet-trace パフォーマンス分析ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="8b945-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="8b945-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="8b945-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="8b945-105">インストール</span><span class="sxs-lookup"><span data-stu-id="8b945-105">Install</span></span>

<span data-ttu-id="8b945-106">`dotnet-trace` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="8b945-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="8b945-107">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="8b945-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="8b945-108">`dotnet-trace` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-trace)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b945-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="8b945-109">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="8b945-109">**Direct download:**</span></span>

  <span data-ttu-id="8b945-110">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="8b945-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="8b945-111">OS</span><span class="sxs-lookup"><span data-stu-id="8b945-111">OS</span></span>  | <span data-ttu-id="8b945-112">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="8b945-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="8b945-113">Windows</span><span class="sxs-lookup"><span data-stu-id="8b945-113">Windows</span></span> | <span data-ttu-id="8b945-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="8b945-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="8b945-115">macOS</span><span class="sxs-lookup"><span data-stu-id="8b945-115">macOS</span></span>   | [<span data-ttu-id="8b945-116">x64</span><span class="sxs-lookup"><span data-stu-id="8b945-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="8b945-117">Linux</span><span class="sxs-lookup"><span data-stu-id="8b945-117">Linux</span></span>   | <span data-ttu-id="8b945-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="8b945-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="8b945-119">構文</span><span class="sxs-lookup"><span data-stu-id="8b945-119">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="8b945-120">説明</span><span class="sxs-lookup"><span data-stu-id="8b945-120">Description</span></span>

<span data-ttu-id="8b945-121">`dotnet-trace` ツール:</span><span class="sxs-lookup"><span data-stu-id="8b945-121">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="8b945-122">クロスプラットフォーム .NET Core ツールです。</span><span class="sxs-lookup"><span data-stu-id="8b945-122">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="8b945-123">ネイティブ プロファイラーなしで実行中のプロセスの .NET Core トレースを回収できます。</span><span class="sxs-lookup"><span data-stu-id="8b945-123">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="8b945-124">.NET Core ランタイムの [`EventPipe`](./eventpipe.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8b945-124">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="8b945-125">Windows、Linux または macOS でも同じエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="8b945-125">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="8b945-126">オプション</span><span class="sxs-lookup"><span data-stu-id="8b945-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="8b945-127">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="8b945-127">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="8b945-128">dotnet-trace ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="8b945-128">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="8b945-129">コマンド</span><span class="sxs-lookup"><span data-stu-id="8b945-129">Commands</span></span>

| <span data-ttu-id="8b945-130">コマンド</span><span class="sxs-lookup"><span data-stu-id="8b945-130">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="8b945-131">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="8b945-131">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="8b945-132">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="8b945-132">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="8b945-133">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="8b945-133">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="8b945-134">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="8b945-134">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="8b945-135">dotnet-trace collect</span><span class="sxs-lookup"><span data-stu-id="8b945-135">dotnet-trace collect</span></span>

<span data-ttu-id="8b945-136">実行中のプロセスから診断トレースを収集します。</span><span class="sxs-lookup"><span data-stu-id="8b945-136">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8b945-137">構文</span><span class="sxs-lookup"><span data-stu-id="8b945-137">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="8b945-138">オプション</span><span class="sxs-lookup"><span data-stu-id="8b945-138">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="8b945-139">メモリ内の循環バッファーのサイズをメガバイトに設定します。</span><span class="sxs-lookup"><span data-stu-id="8b945-139">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="8b945-140">既定は 256 MB です。</span><span class="sxs-lookup"><span data-stu-id="8b945-140">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="8b945-141">生成される CLR イベントの詳細度。</span><span class="sxs-lookup"><span data-stu-id="8b945-141">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="8b945-142">生成する CLR ランタイム イベントの一覧。</span><span class="sxs-lookup"><span data-stu-id="8b945-142">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="8b945-143">トレース ファイルの出力の変換形式を設定します。</span><span class="sxs-lookup"><span data-stu-id="8b945-143">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="8b945-144">既定値は、`NetTrace` です。</span><span class="sxs-lookup"><span data-stu-id="8b945-144">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="8b945-145">トレースを収集するプロセスの名前。</span><span class="sxs-lookup"><span data-stu-id="8b945-145">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="8b945-146">収集されたトレース データの出力パス。</span><span class="sxs-lookup"><span data-stu-id="8b945-146">The output path for the collected trace data.</span></span> <span data-ttu-id="8b945-147">指定しない場合の既定値は `trace.nettrace` です。</span><span class="sxs-lookup"><span data-stu-id="8b945-147">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="8b945-148">トレースを収集するプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="8b945-148">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="8b945-149">共通のトレース シナリオを簡潔に指定できるようにする、事前定義されたプロバイダーの名前付き構成のセット。</span><span class="sxs-lookup"><span data-stu-id="8b945-149">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="8b945-150">次のプロファイルを利用できます。</span><span class="sxs-lookup"><span data-stu-id="8b945-150">The following profiles are available:</span></span>

 | <span data-ttu-id="8b945-151">[プロファイル]</span><span class="sxs-lookup"><span data-stu-id="8b945-151">Profile</span></span> | <span data-ttu-id="8b945-152">説明</span><span class="sxs-lookup"><span data-stu-id="8b945-152">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="8b945-153">CPU 使用率および一般的な .NET ランタイム情報の追跡に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8b945-153">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="8b945-154">プロファイルまたはプロバイダーが指定されていない場合は、これが既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="8b945-154">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="8b945-155">GC コレクションを追跡し、オブジェクトの割り当てをサンプリングします。</span><span class="sxs-lookup"><span data-stu-id="8b945-155">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="8b945-156">オーバーヘッドが非常に低い場合にのみ GC コレクションを追跡します。</span><span class="sxs-lookup"><span data-stu-id="8b945-156">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="8b945-157">有効にする `EventPipe` プロバイダーのコンマ区切りのリスト。</span><span class="sxs-lookup"><span data-stu-id="8b945-157">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="8b945-158">これらのプロバイダーは、`--profile <profile-name>` で示されている任意のプロバイダーを補完します。</span><span class="sxs-lookup"><span data-stu-id="8b945-158">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="8b945-159">特定のプロバイダーに不整合がある場合、この構成がプロファイルの暗黙的な構成に優先されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-159">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="8b945-160">プロバイダーの一覧の形式は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8b945-160">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="8b945-161">`Provider` は、`KnownProviderName[:Flags[:Level][:KeyValueArgs]]` という形式です。</span><span class="sxs-lookup"><span data-stu-id="8b945-161">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="8b945-162">`KeyValueArgs` は、`[key1=value1][;key2=value2]` という形式です。</span><span class="sxs-lookup"><span data-stu-id="8b945-162">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="8b945-163">**`-- <command>` (.NET 5.0 のみを実行しているターゲット アプリケーションの場合)**</span><span class="sxs-lookup"><span data-stu-id="8b945-163">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="8b945-164">ユーザーは、コレクション構成パラメーターの後にまず `--`、次にコマンドを追加すれば、5.0 以降のランタイムで .NET アプリケーションを起動することができます。</span><span class="sxs-lookup"><span data-stu-id="8b945-164">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="8b945-165">これは、起動時のパフォーマンスの問題やアセンブリ ローダーおよびバインダーのエラーなど、プロセスの早い段階で発生する問題を診断するのに役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="8b945-165">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="8b945-166">このオプションを使用すると、ツールに返信する最初の .NET 5.0 プロセスが監視されます。つまり、ご利用のコマンドで複数の .NET アプリケーションが起動される場合、収集されるのは最初のアプリのみとなります。</span><span class="sxs-lookup"><span data-stu-id="8b945-166">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="8b945-167">このため、このオプションについては、自己完結型アプリケーションに対して使用するか、または `dotnet exec <app.dll>` オプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8b945-167">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="8b945-168">dotnet-trace convert</span><span class="sxs-lookup"><span data-stu-id="8b945-168">dotnet-trace convert</span></span>

<span data-ttu-id="8b945-169">`nettrace` トレースを、別のトレース分析ツールで使用するために、別の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="8b945-169">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8b945-170">構文</span><span class="sxs-lookup"><span data-stu-id="8b945-170">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="8b945-171">引数</span><span class="sxs-lookup"><span data-stu-id="8b945-171">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="8b945-172">変換する入力トレース ファイル。</span><span class="sxs-lookup"><span data-stu-id="8b945-172">Input trace file to be converted.</span></span> <span data-ttu-id="8b945-173">既定は *trace.nettrace* です。</span><span class="sxs-lookup"><span data-stu-id="8b945-173">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="8b945-174">オプション</span><span class="sxs-lookup"><span data-stu-id="8b945-174">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="8b945-175">トレース ファイルの出力の変換形式を設定します。</span><span class="sxs-lookup"><span data-stu-id="8b945-175">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="8b945-176">出力ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="8b945-176">Output filename.</span></span> <span data-ttu-id="8b945-177">ターゲットの形式の拡張子が追加されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-177">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="8b945-178">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="8b945-178">dotnet-trace ps</span></span>

 <span data-ttu-id="8b945-179">トレースを収集できる dotnet プロセスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8b945-179">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8b945-180">構文</span><span class="sxs-lookup"><span data-stu-id="8b945-180">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="8b945-181">dotnet-trace list-profiles</span><span class="sxs-lookup"><span data-stu-id="8b945-181">dotnet-trace list-profiles</span></span>

<span data-ttu-id="8b945-182">各プロファイルに含まれるプロバイダーとフィルターの記述と共に、事前に構築されているトレースのプロファイルを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="8b945-182">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="8b945-183">構文</span><span class="sxs-lookup"><span data-stu-id="8b945-183">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="8b945-184">dotnet-trace を使用してトレースを収集する</span><span class="sxs-lookup"><span data-stu-id="8b945-184">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="8b945-185">`dotnet-trace` を使用してトレースを収集するには:</span><span class="sxs-lookup"><span data-stu-id="8b945-185">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="8b945-186">トレースを収集する .NET Core アプリケーションのプロセス識別子 (PID) を取得します。</span><span class="sxs-lookup"><span data-stu-id="8b945-186">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="8b945-187">Windows で、タスク マネージャーや、たとえば、`tasklist` コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b945-187">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="8b945-188">Linux の場合、たとえば、`ps` コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8b945-188">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="8b945-189">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="8b945-189">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="8b945-190">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="8b945-190">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="8b945-191">上のコマンドを実行すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-191">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="8b945-192">`<Enter>` キーを押すと、コレクションが停止します。</span><span class="sxs-lookup"><span data-stu-id="8b945-192">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="8b945-193">`dotnet-trace` では、*trace.nettrace* ファイルにイベントをログ記録する作業が完了します。</span><span class="sxs-lookup"><span data-stu-id="8b945-193">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="8b945-194">子アプリケーションを起動し、そのスタートアップからトレースを dotnet-trace を使用して収集します</span><span class="sxs-lookup"><span data-stu-id="8b945-194">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b945-195">これは、.NET 5.0 以降を実行しているアプリに対してのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="8b945-195">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="8b945-196">場合によっては、プロセスのトレースをそのスタートアップから収集すると便利なことがあります。</span><span class="sxs-lookup"><span data-stu-id="8b945-196">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="8b945-197">.NET 5.0 以降を実行しているアプリでは、dotnet-trace を使用してこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="8b945-197">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="8b945-198">これを使用すると、コマンドライン引数として `arg1` と `arg2` を含む `hello.exe` が起動され、そのランタイム スタートアップからトレースが収集されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-198">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="8b945-199">上のコマンドを実行すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-199">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="8b945-200">トレースの収集を停止するには、`<Enter>` または `<Ctrl + C>` キーを押します。</span><span class="sxs-lookup"><span data-stu-id="8b945-200">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="8b945-201">この操作を行うと、`hello.exe` も終了します。</span><span class="sxs-lookup"><span data-stu-id="8b945-201">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="8b945-202">dotnet-trace を介して `hello.exe` を起動すると、その入力/出力がリダイレクトされ、その stdin/stdout とやりとりができなくなります。</span><span class="sxs-lookup"><span data-stu-id="8b945-202">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="8b945-203">CTRL + C または SIGTERM を介してツールを終了すると、ツールと子プロセスの両方が安全に終了します。</span><span class="sxs-lookup"><span data-stu-id="8b945-203">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="8b945-204">ツールの前に子プロセスが終了すると、ツールも終了し、トレースを安全に表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8b945-204">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="8b945-205">dotnet-trace からキャプチャされたトレースを表示する</span><span class="sxs-lookup"><span data-stu-id="8b945-205">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="8b945-206">Windows の場合、 *.nettrace* ファイルを [PerfView](https://github.com/microsoft/perfview) で表示し、分析できます。他のプラットフォームで収集されたトレースについては、トレース ファイルを Windows コンピューターに移動し、PerfView で表示できます。</span><span class="sxs-lookup"><span data-stu-id="8b945-206">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="8b945-207">Linux の場合、`dotnet-trace` の出力形式を `speedscope` に変更することでトレースを表示できます。</span><span class="sxs-lookup"><span data-stu-id="8b945-207">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="8b945-208">出力ファイル形式は `-f|--format` オプションで変更できます。`-f speedscope` により、`dotnet-trace` で `speedscope` ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-208">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="8b945-209">`nettrace` (既定のオプション) か `speedscope` を選択できます。</span><span class="sxs-lookup"><span data-stu-id="8b945-209">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="8b945-210">`Speedscope` ファイルは <https://www.speedscope.app> で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="8b945-210">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="8b945-211">.NET Core ランタイムにより、`nettrace` 形式でトレースが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-211">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="8b945-212">トレースの完了後、トレースは speedscope に変換されます (指定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="8b945-212">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="8b945-213">変換によってはデータが失われる場合もあるため、元の `nettrace` ファイルが変換されたファイルの横に保持されます。</span><span class="sxs-lookup"><span data-stu-id="8b945-213">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="8b945-214">dotnet-trace を使用して経時的なカウンター値を収集する</span><span class="sxs-lookup"><span data-stu-id="8b945-214">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="8b945-215">`dotnet-trace` でできること:</span><span class="sxs-lookup"><span data-stu-id="8b945-215">`dotnet-trace` can:</span></span>

* <span data-ttu-id="8b945-216">パフォーマンスで左右される環境で基本的な正常性監視を行うには `EventCounter` を使用します。</span><span class="sxs-lookup"><span data-stu-id="8b945-216">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="8b945-217">たとえば、運用環境です。</span><span class="sxs-lookup"><span data-stu-id="8b945-217">For example, in production.</span></span>
* <span data-ttu-id="8b945-218">リアルタイムで表示する必要がないようにトレースを収集します。</span><span class="sxs-lookup"><span data-stu-id="8b945-218">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="8b945-219">たとえば、実行時のパフォーマンス カウンター値を収集するには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="8b945-219">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="8b945-220">先のコマンドでは、正常性の簡易監視を 1 秒ごとに報告するようにランタイム カウンターに命令します。</span><span class="sxs-lookup"><span data-stu-id="8b945-220">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="8b945-221">`EventCounterIntervalSec=1` の値を (60 など) 大きい値に置き換えた場合、カウンター データの細分性の詳細度がより低いトレースをより少数収集できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8b945-221">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="8b945-222">次のコマンドでは、先のコマンドよりオーバーヘッドとトレース サイズが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="8b945-222">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="8b945-223">上のコマンドでは、ランタイム イベントとマネージド スタック プロファイラーが無効になります。</span><span class="sxs-lookup"><span data-stu-id="8b945-223">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="8b945-224">.NET プロバイダー</span><span class="sxs-lookup"><span data-stu-id="8b945-224">.NET Providers</span></span>

<span data-ttu-id="8b945-225">.NET Core ランタイムでは、次の .NET プロバイダーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8b945-225">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="8b945-226">.NET Core では、`Event Tracing for Windows (ETW)` と `EventPipe` トレースの有効化に、いずれも同じキーワードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="8b945-226">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="8b945-227">プロバイダー名</span><span class="sxs-lookup"><span data-stu-id="8b945-227">Provider name</span></span>                            | <span data-ttu-id="8b945-228">情報</span><span class="sxs-lookup"><span data-stu-id="8b945-228">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="8b945-229">ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="8b945-229">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="8b945-230">CLR ランタイム キーワード</span><span class="sxs-lookup"><span data-stu-id="8b945-230">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="8b945-231">ランダウン プロバイダー</span><span class="sxs-lookup"><span data-stu-id="8b945-231">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="8b945-232">CLR ランダウン キーワード</span><span class="sxs-lookup"><span data-stu-id="8b945-232">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="8b945-233">サンプル プロファイラーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8b945-233">Enables the sample profiler.</span></span> |
