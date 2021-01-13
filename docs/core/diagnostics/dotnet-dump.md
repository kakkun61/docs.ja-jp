---
title: dotnet-dump 診断ツール - .NET CLI
description: dotnet-dump CLI ツールをインストールして使用し、ネイティブ デバッガーなしで Windows と Linux のダンプを収集して分析する方法について学習します。
ms.date: 11/17/2020
ms.openlocfilehash: eaffbb1f2959dba5c25a603b6f785c7480e4a8c0
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765047"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="89db0-103">ダンプの収集と分析のユーティリティ (dotnet-dump)</span><span class="sxs-lookup"><span data-stu-id="89db0-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="89db0-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="89db0-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="89db0-105">macOS の `dotnet-dump` は、.NET 5.0 以降のバージョンでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="89db0-105">`dotnet-dump` for macOS is only supported with .NET 5.0 and later versions.</span></span>

## <a name="install"></a><span data-ttu-id="89db0-106">インストール</span><span class="sxs-lookup"><span data-stu-id="89db0-106">Install</span></span>

<span data-ttu-id="89db0-107">`dotnet-dump` をダウンロードしてインストールするには、次の 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="89db0-107">There are two ways to download and install `dotnet-dump`:</span></span>

- <span data-ttu-id="89db0-108">**dotnet グローバル ツール:**</span><span class="sxs-lookup"><span data-stu-id="89db0-108">**dotnet global tool:**</span></span>

  <span data-ttu-id="89db0-109">`dotnet-dump` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-dump)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="89db0-109">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- <span data-ttu-id="89db0-110">**直接ダウンロード:**</span><span class="sxs-lookup"><span data-stu-id="89db0-110">**Direct download:**</span></span>

  <span data-ttu-id="89db0-111">ご利用のプラットフォームに適したツールの実行可能ファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="89db0-111">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="89db0-112">OS</span><span class="sxs-lookup"><span data-stu-id="89db0-112">OS</span></span>  | <span data-ttu-id="89db0-113">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="89db0-113">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="89db0-114">Windows</span><span class="sxs-lookup"><span data-stu-id="89db0-114">Windows</span></span> | <span data-ttu-id="89db0-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="89db0-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span></span> |
  | <span data-ttu-id="89db0-116">macOS</span><span class="sxs-lookup"><span data-stu-id="89db0-116">macOS</span></span>   | [<span data-ttu-id="89db0-117">x64</span><span class="sxs-lookup"><span data-stu-id="89db0-117">x64</span></span>](https://aka.ms/dotnet-dump/osx-x64) |
  | <span data-ttu-id="89db0-118">Linux</span><span class="sxs-lookup"><span data-stu-id="89db0-118">Linux</span></span>   | <span data-ttu-id="89db0-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="89db0-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="89db0-120">構文</span><span class="sxs-lookup"><span data-stu-id="89db0-120">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="89db0-121">説明</span><span class="sxs-lookup"><span data-stu-id="89db0-121">Description</span></span>

<span data-ttu-id="89db0-122">`dotnet-dump` グローバル ツールを使用すると、Linux の `lldb` などの任意のネイティブ デバッガーを使用せずに、Windows と Linux のダンプを収集して分析できます。</span><span class="sxs-lookup"><span data-stu-id="89db0-122">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="89db0-123">このツールは、`lldb` が完全に動作しない Alpine Linux などのプラットフォームで重要です。</span><span class="sxs-lookup"><span data-stu-id="89db0-123">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="89db0-124">`dotnet-dump` ツールでは、SOS コマンドを実行してクラッシュとガベージ コレクター (GC) を分析できますが、これはネイティブのデバッガーではないため、ネイティブ スタック フレームの表示などの操作はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="89db0-124">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="89db0-125">オプション</span><span class="sxs-lookup"><span data-stu-id="89db0-125">Options</span></span>

- **`--version`**

  <span data-ttu-id="89db0-126">dotnet-dump ユーティリティのバージョンを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-126">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="89db0-127">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-127">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="89db0-128">コマンド</span><span class="sxs-lookup"><span data-stu-id="89db0-128">Commands</span></span>

| <span data-ttu-id="89db0-129">コマンド</span><span class="sxs-lookup"><span data-stu-id="89db0-129">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="89db0-130">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="89db0-130">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="89db0-131">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="89db0-131">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="89db0-132">dotnet-dump collect</span><span class="sxs-lookup"><span data-stu-id="89db0-132">dotnet-dump collect</span></span>

<span data-ttu-id="89db0-133">プロセスからダンプをキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="89db0-133">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="89db0-134">構文</span><span class="sxs-lookup"><span data-stu-id="89db0-134">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="89db0-135">オプション</span><span class="sxs-lookup"><span data-stu-id="89db0-135">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="89db0-136">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-136">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="89db0-137">ダンプを収集するプロセスの ID 番号を指定します。</span><span class="sxs-lookup"><span data-stu-id="89db0-137">Specifies the process ID number to collect a dump from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="89db0-138">ダンプを収集するプロセスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="89db0-138">Specifies the name of the process to collect a dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="89db0-139">プロセスから収集する情報の種類を決定する、ダンプの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="89db0-139">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="89db0-140">次の 3 種類があります。</span><span class="sxs-lookup"><span data-stu-id="89db0-140">There are three types:</span></span>

  - <span data-ttu-id="89db0-141">`Full` - モジュール イメージを含むメモリをすべて含む最大のダンプ。</span><span class="sxs-lookup"><span data-stu-id="89db0-141">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="89db0-142">`Heap`: モジュールの一覧、スレッドの一覧、すべてのスタック、例外情報、ハンドル情報、およびマップされたイメージを除くすべてのメモリを含む、大規模で比較的包括的なダンプです。</span><span class="sxs-lookup"><span data-stu-id="89db0-142">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="89db0-143">`Mini`: モジュールの一覧、スレッドの一覧、例外情報、およびすべてのスタックを含む小さいダンプです。</span><span class="sxs-lookup"><span data-stu-id="89db0-143">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="89db0-144">指定しない場合の既定は、`Full` です。</span><span class="sxs-lookup"><span data-stu-id="89db0-144">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="89db0-145">収集したダンプを書き込む完全なパスとファイル名。</span><span class="sxs-lookup"><span data-stu-id="89db0-145">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="89db0-146">指定していない場合は、次になります。</span><span class="sxs-lookup"><span data-stu-id="89db0-146">If not specified:</span></span>

  - <span data-ttu-id="89db0-147">Windows での既定は、 *.\dump_YYYYMMDD_HHMMSS.dmp* です。</span><span class="sxs-lookup"><span data-stu-id="89db0-147">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="89db0-148">Linux での既定は、 *./core_YYYYMMDD_HHMMSS* です。</span><span class="sxs-lookup"><span data-stu-id="89db0-148">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="89db0-149">YYYYMMDD は、年/月/日で、HHMMSS は時間/分/秒です。</span><span class="sxs-lookup"><span data-stu-id="89db0-149">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="89db0-150">ダンプの収集の診断ログを有効にします。</span><span class="sxs-lookup"><span data-stu-id="89db0-150">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="89db0-151">dotnet-dump analyze</span><span class="sxs-lookup"><span data-stu-id="89db0-151">dotnet-dump analyze</span></span>

<span data-ttu-id="89db0-152">ダンプを検索する対話型シェルを開始します。</span><span class="sxs-lookup"><span data-stu-id="89db0-152">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="89db0-153">このシェルでは、さまざまな [SOS コマンド](#analyze-sos-commands)を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="89db0-153">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="89db0-154">構文</span><span class="sxs-lookup"><span data-stu-id="89db0-154">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="89db0-155">引数</span><span class="sxs-lookup"><span data-stu-id="89db0-155">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="89db0-156">分析のためにファイルをダンプするパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="89db0-156">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="89db0-157">オプション</span><span class="sxs-lookup"><span data-stu-id="89db0-157">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="89db0-158">起動時にシェルで実行する[コマンド](#analyze-sos-commands)を指定します。</span><span class="sxs-lookup"><span data-stu-id="89db0-158">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="89db0-159">SOS コマンドを分析する</span><span class="sxs-lookup"><span data-stu-id="89db0-159">Analyze SOS commands</span></span>

| <span data-ttu-id="89db0-160">コマンド</span><span class="sxs-lookup"><span data-stu-id="89db0-160">Command</span></span>                             | <span data-ttu-id="89db0-161">関数</span><span class="sxs-lookup"><span data-stu-id="89db0-161">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="89db0-162">使用可能なコマンドをすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-162">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="89db0-163">指定したコマンドを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-163">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="89db0-164">対話モードを終了します。</span><span class="sxs-lookup"><span data-stu-id="89db0-164">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="89db0-165">マネージド コードのみのスタック トレースを提供します。</span><span class="sxs-lookup"><span data-stu-id="89db0-165">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="89db0-166">実行中のマネージド スレッドを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-166">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="89db0-167">ガベージ コレクトされたヒープ上の非同期状態のマシンに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-167">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="89db0-168">指定されたアドレスにあるアセンブリに関する詳細を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-168">Displays details about the assembly at the specified address.</span></span>                                 |
| `dumpclass <arguments>`             | <span data-ttu-id="89db0-169">指定されたアドレスにある `EEClass` 構造体に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-169">Displays information about the `EEClass` structure at the specified address.</span></span>                  |
| `dumpdelegate <arguments>`          | <span data-ttu-id="89db0-170">指定されたアドレスにあるデリゲートに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-170">Displays information about the delegate at the specified address.</span></span>                             |
| `dumpdomain <arguments>`            | <span data-ttu-id="89db0-171">すべての AppDomain と、指定されたドメイン内のすべてのアセンブリに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-171">Displays information all the AppDomains and all assemblies within the specified domain.</span></span>       |
| `dumpheap <arguments>`              | <span data-ttu-id="89db0-172">ガベージ コレクトされたヒープと、オブジェクトの収集統計に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-172">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="89db0-173">マネージド メソッドに関連付けられている Microsoft Intermediate Language (MSIL) を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-173">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="89db0-174">メモリ内ストレス ログの内容を、指定したファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="89db0-174">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="89db0-175">指定されたアドレスにある `MethodDesc` 構造体に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-175">Displays information about the `MethodDesc` structure at the specified address.</span></span>               |
| `dumpmodule <arguments>`            | <span data-ttu-id="89db0-176">指定されたアドレスにあるモジュールに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-176">Displays information about the module at the specified address.</span></span>                               |
| `dumpmt <arguments>`                | <span data-ttu-id="89db0-177">指定されたアドレスにある `MethodTable` に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-177">Displays information about the `MethodTable` at the specified address.</span></span>                        |
| `dumpobj <arguments>`               | <span data-ttu-id="89db0-178">指定したアドレスにあるオブジェクトに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-178">Displays info about the object at the specified address.</span></span>                                      |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="89db0-179">現在のスタックの範囲内で見つかったすべてのマネージド オブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-179">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="89db0-180">内部のランタイム データ構造体によって消費されたプロセス メモリに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-180">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="89db0-181">完了の目的で登録されているすべてのオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-181">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="89db0-182">指定されたアドレスにあるオブジェクトへの参照 (またはルート) に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-182">Displays info about references (or roots) to the object at the specified address.</span></span>             |
| `gcwhere <arguments>`               | <span data-ttu-id="89db0-183">渡された引数の GC ヒープ内の場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-183">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="89db0-184">指定したアドレスにある JIT コード内の `MethodDesc` 構造体に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-184">Displays the `MethodDesc` structure at the specified address in JIT code.</span></span>                     |
| `histclear <arguments>`             | <span data-ttu-id="89db0-185">`hist*` コマンドのファミリによって使用されているすべてのリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="89db0-185">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="89db0-186">デバッグ対象に保存されているストレス ログから SOS 構造体を初期化します。</span><span class="sxs-lookup"><span data-stu-id="89db0-186">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="89db0-187">`<arguments>` に関連するガベージ コレクションのストレス ログの再配置を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-187">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="89db0-188">指定されたアドレスにあるオブジェクトを参照するすべてのログ エントリを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-188">Displays all the log entries that reference the object at the specified address.</span></span>              |
| `histroot <arguments>`              | <span data-ttu-id="89db0-189">指定したルートの上位変換と再配置の両方に関係する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-189">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="89db0-190">プロセス内のネイティブ モジュールを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-190">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="89db0-191">`<argument>` の `MethodTable` 構造体と `EEClass` 構造体を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-191">Displays the `MethodTable` and `EEClass` structures for the `<argument>`.</span></span>                     |
| `pe|printexception <arguments>`     | <span data-ttu-id="89db0-192">`<argument>` の <xref:System.Exception> クラスから派生したオブジェクトを表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-192">Displays any object derived from the <xref:System.Exception> class for the `<argument>`.</span></span>      |
| `setsymbolserver <arguments>`       | <span data-ttu-id="89db0-193">シンボル サーバーのサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="89db0-193">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="89db0-194">SyncBlock の所有者の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-194">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="89db0-195">SOS コマンドの現在のスレッド ID を設定するか表示します。</span><span class="sxs-lookup"><span data-stu-id="89db0-195">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

> [!NOTE]
> <span data-ttu-id="89db0-196">その他の詳細は、「[.NET 用 SOS デバッガー拡張](sos-debugging-extension.md)」に記載されています。</span><span class="sxs-lookup"><span data-stu-id="89db0-196">Additional details can be found in [SOS Debugging Extension for .NET](sos-debugging-extension.md).</span></span>

## <a name="using-dotnet-dump"></a><span data-ttu-id="89db0-197">`dotnet-dump` を使用する</span><span class="sxs-lookup"><span data-stu-id="89db0-197">Using `dotnet-dump`</span></span>

<span data-ttu-id="89db0-198">まずはダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="89db0-198">The first step is to collect a dump.</span></span> <span data-ttu-id="89db0-199">コア ダンプを既に生成している場合、この手順をスキップできます。</span><span class="sxs-lookup"><span data-stu-id="89db0-199">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="89db0-200">コア ダンプは、オペレーティング システムまたは .NET Core ランタイムに組み込まれているそれぞれの[ダンプ生成機能](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md)で作成できます。</span><span class="sxs-lookup"><span data-stu-id="89db0-200">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="89db0-201">ここで、次のように `analyze` コマンドを使用して、コア ダンプを分析します。</span><span class="sxs-lookup"><span data-stu-id="89db0-201">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="89db0-202">この操作により、次のようなコマンドを受け取る対話型セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="89db0-202">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="89db0-203">アプリを強制終了させた未処理の例外を表示するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="89db0-203">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="89db0-204">Docker 用の特別な手順</span><span class="sxs-lookup"><span data-stu-id="89db0-204">Special instructions for Docker</span></span>

<span data-ttu-id="89db0-205">ダンプの収集を Docker で実行している場合、`SYS_PTRACE` 機能 (`--cap-add=SYS_PTRACE` または `--privileged`) が必要です。</span><span class="sxs-lookup"><span data-stu-id="89db0-205">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="89db0-206">Microsoft .NET Core SDK Linux Docker イメージでは、一部の `dotnet-dump` コマンドで次の例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="89db0-206">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="89db0-207">未処理の例外:System.DllNotFoundException:共有ライブラリ 'libdl.so' またはその依存関係の 1 つを読み込めませんでした。</span><span class="sxs-lookup"><span data-stu-id="89db0-207">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="89db0-208">"libc6-dev" パッケージをインストールすると、この問題を回避できます。</span><span class="sxs-lookup"><span data-stu-id="89db0-208">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="89db0-209">関連項目</span><span class="sxs-lookup"><span data-stu-id="89db0-209">See also</span></span>

- [<span data-ttu-id="89db0-210">メモリ ダンプの収集と分析に関するブログ</span><span class="sxs-lookup"><span data-stu-id="89db0-210">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="89db0-211">ヒープ分析ツール (dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="89db0-211">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
