---
title: dotnet test コマンド
description: dotnet test コマンドは、指定されたプロジェクトで単体テストを実行する場合に使用されます。
ms.date: 04/29/2020
ms.openlocfilehash: a5666cfe4c09b2b88d77b256fac922154c7d6bd7
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634384"
---
# <a name="dotnet-test"></a><span data-ttu-id="eccee-103">dotnet test</span><span class="sxs-lookup"><span data-stu-id="eccee-103">dotnet test</span></span>

<span data-ttu-id="eccee-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="eccee-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="eccee-105">名前</span><span class="sxs-lookup"><span data-stu-id="eccee-105">Name</span></span>

<span data-ttu-id="eccee-106">`dotnet test` - 単体テストを実行するために使用される .NET テスト ドライバー。</span><span class="sxs-lookup"><span data-stu-id="eccee-106">`dotnet test` - .NET test driver used to execute unit tests.</span></span>

## <a name="synopsis"></a><span data-ttu-id="eccee-107">構文</span><span class="sxs-lookup"><span data-stu-id="eccee-107">Synopsis</span></span>

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <ADAPTER_PATH>] [--blame] [--blame-crash]
    [--blame-crash-dump-type <DUMP_TYPE>] [--blame-crash-collect-always]
    [--blame-hang] [--blame-hang-dump-type <DUMP_TYPE>]
    [--blame-hang-timeout <TIMESPAN>]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_NAME>]
    [-d|--diag <LOG_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <RESULTS_DIR>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a><span data-ttu-id="eccee-108">説明</span><span class="sxs-lookup"><span data-stu-id="eccee-108">Description</span></span>

<span data-ttu-id="eccee-109">`dotnet test` コマンドは、指定されたソリューションで単体テストを実行する場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-109">The `dotnet test` command is used to execute unit tests in a given solution.</span></span> <span data-ttu-id="eccee-110">`dotnet test` コマンドを実行すると、ソリューションがビルドされ、ソリューション内の各テスト プロジェクトのテスト ホスト アプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-110">The `dotnet test` command builds the solution and runs a test host application for each test project in the solution.</span></span> <span data-ttu-id="eccee-111">テスト ホストは、指定されたプロジェクトで、テスト フレームワークを使用してテストを実行します。たとえば、MSTest、NUnit、xUnit などです。そして、各テストの成功または失敗を報告します。</span><span class="sxs-lookup"><span data-stu-id="eccee-111">The test host executes tests in the given project using a test framework, for example: MSTest, NUnit, or xUnit, and reports the success or failure of each test.</span></span> <span data-ttu-id="eccee-112">すべてのテストが成功した場合、テスト ランナーは 0 の終了コードを返します。それ以外の、いずれかのテストに失敗した場合は、1 を返します。</span><span class="sxs-lookup"><span data-stu-id="eccee-112">If all tests are successful, the test runner returns 0 as an exit code; otherwise if any test fails, it returns 1.</span></span>

<span data-ttu-id="eccee-113">複数の対象を持つプロジェクトでは、対象となる各フレームワークに対してテストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-113">For multi-targeted projects, tests are run for each targeted framework.</span></span> <span data-ttu-id="eccee-114">テスト ホストと単体テスト フレームワークは、NuGet パッケージとしてパッケージ化され、プロジェクトの通常の依存関係として復元されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-114">The test host and the unit test framework are packaged as NuGet packages and are restored as ordinary dependencies for the project.</span></span>

<span data-ttu-id="eccee-115">テスト プロジェクトでは、通常の `<PackageReference>` 要素を使用してテスト ランナーを指定します。次のサンプル プロジェクト ファイルのようになります。</span><span class="sxs-lookup"><span data-stu-id="eccee-115">Test projects specify the test runner using an ordinary `<PackageReference>` element, as seen in the following sample project file:</span></span>

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

<span data-ttu-id="eccee-116">`Microsoft.NET.Test.Sdk` がテスト ホストの場合、`xunit` はテスト フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="eccee-116">Where `Microsoft.NET.Test.Sdk` is the test host, `xunit` is the test framework.</span></span> <span data-ttu-id="eccee-117">また、`xunit.runner.visualstudio` はテスト アダプターであり、xUnit フレームワークはテスト ホストと連携できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-117">And `xunit.runner.visualstudio` is a test adapter, which allows the xUnit framework to work with the test host.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="eccee-118">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="eccee-118">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="eccee-119">引数</span><span class="sxs-lookup"><span data-stu-id="eccee-119">Arguments</span></span>

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - <span data-ttu-id="eccee-120">テスト プロジェクトへのパス。</span><span class="sxs-lookup"><span data-stu-id="eccee-120">Path to the test project.</span></span>
  - <span data-ttu-id="eccee-121">ソリューションへのパス。</span><span class="sxs-lookup"><span data-stu-id="eccee-121">Path to the solution.</span></span>
  - <span data-ttu-id="eccee-122">プロジェクトまたはソリューションを含むディレクトリへのパス。</span><span class="sxs-lookup"><span data-stu-id="eccee-122">Path to a directory that contains a project or a solution.</span></span>
  - <span data-ttu-id="eccee-123">テスト プロジェクト " *.dll*" ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="eccee-123">Path to a test project *.dll* file.</span></span>

  <span data-ttu-id="eccee-124">指定されていない場合、プロジェクトまたはソリューションが現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-124">If not specified, it searches for a project or a solution in the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="eccee-125">オプション</span><span class="sxs-lookup"><span data-stu-id="eccee-125">Options</span></span>

- **`-a|--test-adapter-path <ADAPTER_PATH>`**

  <span data-ttu-id="eccee-126">追加のテスト アダプターを検索するディレクトリへのパス。</span><span class="sxs-lookup"><span data-stu-id="eccee-126">Path to a directory to be searched for additional test adapters.</span></span> <span data-ttu-id="eccee-127">サフィックス `.TestAdapter.dll` を持つ " *.dll*" ファイルのみが検査されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-127">Only *.dll* files with suffix `.TestAdapter.dll` are inspected.</span></span> <span data-ttu-id="eccee-128">指定しない場合、テスト " *.dll*" のディレクトリが検索されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-128">If not specified, the directory of the test *.dll* is searched.</span></span>

- **`--blame`**

  <span data-ttu-id="eccee-129">変更履歴モードでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="eccee-129">Runs the tests in blame mode.</span></span> <span data-ttu-id="eccee-130">このオプションは、テスト ホストがクラッシュする原因となる問題のあるテストを分離するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="eccee-130">This option is helpful in isolating problematic tests that cause the test host to crash.</span></span> <span data-ttu-id="eccee-131">クラッシュが検出されると、クラッシュ前に実行されたテストの順序をキャプチャするシーケンス ファイルが `TestResults/<Guid>/<Guid>_Sequence.xml` に作成されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-131">When a crash is detected, it creates a sequence file in `TestResults/<Guid>/<Guid>_Sequence.xml` that captures the order of tests that were run before the crash.</span></span>

- <span data-ttu-id="eccee-132">**`--blame-crash`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="eccee-132">**`--blame-crash`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="eccee-133">テスト ホストが予期せずに終了した場合に、変更履歴モードでテストを実行して、クラッシュ ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="eccee-133">Runs the tests in blame mode and collects a crash dump when the test host exits unexpectedly.</span></span> <span data-ttu-id="eccee-134">このオプションは、使用されている .NET のバージョン、エラーの種類、およびオペレーティング システムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="eccee-134">This option depends on the version of .NET used, the type of error, and the operating system.</span></span>
  
  <span data-ttu-id="eccee-135">マネージド コードでの例外の場合、ダンプは .NET 5.0 以降のバージョンで自動的に収集されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-135">For exceptions in managed code, a dump will be automatically collected on .NET 5.0 and later versions.</span></span> <span data-ttu-id="eccee-136">testhost や、やはり .NET 5.0 で実行されてクラッシュした子プロセスのダンプが生成されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-136">It will generate a dump for testhost or any child process that also ran on .NET 5.0 and crashed.</span></span> <span data-ttu-id="eccee-137">ネイティブ コードでのクラッシュの場合、ダンプは生成されません。</span><span class="sxs-lookup"><span data-stu-id="eccee-137">Crashes in native code will not generate a dump.</span></span> <span data-ttu-id="eccee-138">このオプションは、Windows、macOS、Linux で動作します。</span><span class="sxs-lookup"><span data-stu-id="eccee-138">This option works on Windows, macOS, and Linux.</span></span>
  
  <span data-ttu-id="eccee-139">ネイティブ コードでのクラッシュ ダンプ、または .NET Core 3.1 以前のバージョンを使用しているときのクラッシュ ダンプは、Windows 上でのみ、Procdump を使用して収集できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-139">Crash dumps in native code, or when using .NET Core 3.1 or earlier versions, can only be collected on Windows, by using Procdump.</span></span> <span data-ttu-id="eccee-140">*procdump.exe* および *procdump64.exe* を含むディレクトリが、PATH または PROCDUMP_PATH 環境変数に指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="eccee-140">A directory that contains *procdump.exe* and *procdump64.exe* must be in the PATH or PROCDUMP_PATH environment variable.</span></span> <span data-ttu-id="eccee-141">[ツールをダウンロード](/sysinternals/downloads/procdump)します。</span><span class="sxs-lookup"><span data-stu-id="eccee-141">[Download the tools](/sysinternals/downloads/procdump).</span></span> <span data-ttu-id="eccee-142">`--blame` を意味します。</span><span class="sxs-lookup"><span data-stu-id="eccee-142">Implies `--blame`.</span></span>
  
  <span data-ttu-id="eccee-143">.NET 5.0 以降で実行されているネイティブ アプリケーションからクラッシュ ダンプを収集するには、`VSTEST_DUMP_FORCEPROCDUMP` 環境変数を `1` に設定することで、Procdump を強制的に使用できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-143">To collect a crash dump from a native application running on .NET 5.0 or later, the usage of Procdump can be forced by setting the `VSTEST_DUMP_FORCEPROCDUMP` environment variable to `1`.</span></span>

- <span data-ttu-id="eccee-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="eccee-144">**`--blame-crash-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="eccee-145">収集されるクラッシュ ダンプの種類。</span><span class="sxs-lookup"><span data-stu-id="eccee-145">The type of crash dump to be collected.</span></span> <span data-ttu-id="eccee-146">`--blame-crash` を意味します。</span><span class="sxs-lookup"><span data-stu-id="eccee-146">Implies `--blame-crash`.</span></span>

- <span data-ttu-id="eccee-147">**`--blame-crash-collect-always`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="eccee-147">**`--blame-crash-collect-always`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="eccee-148">予期しないテスト ホストの終了だけでなく、予期されていたものに対しても、クラッシュ ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="eccee-148">Collects a crash dump on expected as well as unexpected test host exit.</span></span>

- <span data-ttu-id="eccee-149">**`--blame-hang`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="eccee-149">**`--blame-hang`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="eccee-150">変更履歴モードでテストを実行し、テストが指定のタイムアウトを超えたときにハング ダンプを収集します。</span><span class="sxs-lookup"><span data-stu-id="eccee-150">Run the tests in blame mode and collects a hang dump when a test exceeds the given timeout.</span></span>

- <span data-ttu-id="eccee-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="eccee-151">**`--blame-hang-dump-type <DUMP_TYPE>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="eccee-152">収集されるクラッシュ ダンプの種類。</span><span class="sxs-lookup"><span data-stu-id="eccee-152">The type of crash dump to be collected.</span></span> <span data-ttu-id="eccee-153">必ず、`full`、`mini`、または `none` になります。</span><span class="sxs-lookup"><span data-stu-id="eccee-153">It should be `full`, `mini`, or `none`.</span></span> <span data-ttu-id="eccee-154">`none` が指定されている場合、タイムアウト時にテスト ホストが終了されますが、ダンプは収集されません。</span><span class="sxs-lookup"><span data-stu-id="eccee-154">When `none` is specified, test host is terminated on timeout, but no dump is collected.</span></span> <span data-ttu-id="eccee-155">`--blame-hang` を意味します。</span><span class="sxs-lookup"><span data-stu-id="eccee-155">Implies `--blame-hang`.</span></span>

- <span data-ttu-id="eccee-156">**`--blame-hang-timeout <TIMESPAN>`** (.NET 5.0 プレビュー SDK 以降で利用可能)</span><span class="sxs-lookup"><span data-stu-id="eccee-156">**`--blame-hang-timeout <TIMESPAN>`** (Available since .NET 5.0 preview SDK)</span></span>

  <span data-ttu-id="eccee-157">テストごとのタイムアウト。それが過ぎると、ハング ダンプがトリガーされ、テスト ホスト プロセスとそのすべての子プロセスは、ダンプされて終了されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-157">Per-test timeout, after which a hang dump is triggered and the test host process and all of its child processes are dumped and terminated.</span></span> <span data-ttu-id="eccee-158">タイムアウト値は、次のいずれかの形式で指定されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-158">The timeout value is specified in one of the following formats:</span></span>
  
  - <span data-ttu-id="eccee-159">1.5h、1.5hour、1.5hours</span><span class="sxs-lookup"><span data-stu-id="eccee-159">1.5h, 1.5hour, 1.5hours</span></span>
  - <span data-ttu-id="eccee-160">90m、90min、90minute、90minutes</span><span class="sxs-lookup"><span data-stu-id="eccee-160">90m, 90min, 90minute, 90minutes</span></span>
  - <span data-ttu-id="eccee-161">5400s、5400sec、5400second、5400seconds</span><span class="sxs-lookup"><span data-stu-id="eccee-161">5400s, 5400sec, 5400second, 5400seconds</span></span>
  - <span data-ttu-id="eccee-162">5400000ms、5400000mil、5400000millisecond、5400000milliseconds</span><span class="sxs-lookup"><span data-stu-id="eccee-162">5400000ms, 5400000mil, 5400000millisecond, 5400000milliseconds</span></span>

  <span data-ttu-id="eccee-163">単位が使用されていない場合 (例: 5400000)、値はミリ秒単位であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="eccee-163">When no unit is used (for example, 5400000), the value is assumed to be in milliseconds.</span></span> <span data-ttu-id="eccee-164">データ ドリブン テストと共に使用すると、タイムアウトの動作は、利用するテスト アダプターに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="eccee-164">When used together with data driven tests, the timeout behavior depends on the test adapter used.</span></span> <span data-ttu-id="eccee-165">xUnit および NUnit の場合、タイムアウトはテスト ケースの後に毎回更新されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-165">For xUnit and NUnit the timeout is renewed after every test case.</span></span> <span data-ttu-id="eccee-166">MSTest の場合、すべてのテスト ケースにこのタイムアウトが使用されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-166">For MSTest, the timeout is used for all test cases.</span></span> <span data-ttu-id="eccee-167">このオプションは、netcoreapp 2.1 以降がインストールされている Windows、netcoreapp 3.1 以降がインストールされている Linux、net5.0 以降がインストールされている macOS でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="eccee-167">This option is supported on Windows with netcoreapp2.1 and later, on Linux with netcoreapp3.1 and later, and on macOS with net5.0 or later.</span></span> <span data-ttu-id="eccee-168">`--blame` と `--blame-hang` を意味します。</span><span class="sxs-lookup"><span data-stu-id="eccee-168">Implies `--blame` and `--blame-hang`.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="eccee-169">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="eccee-169">Defines the build configuration.</span></span> <span data-ttu-id="eccee-170">既定値は `Debug` ですが、プロジェクトの構成がこの既定の SDK 設定をオーバーライドする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="eccee-170">The default value is `Debug`, but your project's configuration could override this default SDK setting.</span></span>

- **`--collect <DATA_COLLECTOR_NAME>`**

  <span data-ttu-id="eccee-171">テストの実行のためのデータ コレクターを有効にします。</span><span class="sxs-lookup"><span data-stu-id="eccee-171">Enables data collector for the test run.</span></span> <span data-ttu-id="eccee-172">詳細については、[「Monitor and analyze test run」](https://aka.ms/vstest-collect) (テストの実行のモニターと分析) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccee-172">For more information, see [Monitor and analyze test run](https://aka.ms/vstest-collect).</span></span>
  
  <span data-ttu-id="eccee-173">.NET Core でサポートされている任意のプラットフォーム上のコード カバレッジを収集するには、[Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) をインストールし、`--collect:"XPlat Code Coverage"` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="eccee-173">To collect code coverage on any platform that is supported by .NET Core, install [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) and use the `--collect:"XPlat Code Coverage"` option.</span></span>

  <span data-ttu-id="eccee-174">Windows では、`--collect "Code Coverage"` オプションを使用してコード カバレッジを収集できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-174">On Windows, you can collect code coverage by using the `--collect "Code Coverage"` option.</span></span> <span data-ttu-id="eccee-175">このオプションを選択すると、 *.coverage* ファイルが生成されます。このファイルは、Visual Studio 2019 Enterprise で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="eccee-175">This option generates a *.coverage* file, which can be opened in Visual Studio 2019 Enterprise.</span></span> <span data-ttu-id="eccee-176">詳細については、[コード カバレッジの使用](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested)に関するページと「[コード カバレッジ分析のカスタマイズ](/visualstudio/test/customizing-code-coverage-analysis)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccee-176">For more information, see [Use code coverage](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) and [Customize code coverage analysis](/visualstudio/test/customizing-code-coverage-analysis).</span></span>

- **`-d|--diag <LOG_FILE>`**

  <span data-ttu-id="eccee-177">テスト プラットフォームの診断モードを有効にし、指定したファイルとそれ以降のファイルに診断メッセージを出力します。</span><span class="sxs-lookup"><span data-stu-id="eccee-177">Enables diagnostic mode for the test platform and writes diagnostic messages to the specified file and to files next to it.</span></span> <span data-ttu-id="eccee-178">メッセージをログに記録するプロセスによって、テスト ホスト ログの `*.host_<date>.txt` やデータ コレクター ログの `*.datacollector_<date>.txt` などの、作成されるファイルが決まります。</span><span class="sxs-lookup"><span data-stu-id="eccee-178">The process that is logging the messages determines which files are created, such as `*.host_<date>.txt` for test host log, and `*.datacollector_<date>.txt` for data collector log.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="eccee-179">テスト バイナリに `dotnet` または .NET Framework テスト ホストを強制的に使用します。</span><span class="sxs-lookup"><span data-stu-id="eccee-179">Forces the use of `dotnet` or .NET Framework test host for the test binaries.</span></span> <span data-ttu-id="eccee-180">このオプションでは、使用するホストの種類のみが決定されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-180">This option only determines which type of host to use.</span></span> <span data-ttu-id="eccee-181">実際に使用されるフレームワークのバージョンは、テスト プロジェクトの "*runtimeconfig. json*" によって決まります。</span><span class="sxs-lookup"><span data-stu-id="eccee-181">The actual framework version to be used is determined by the *runtimeconfig.json* of the test project.</span></span> <span data-ttu-id="eccee-182">指定しない場合、[TargetFramework アセンブリ属性](/dotnet/api/system.runtime.versioning.targetframeworkattribute) を使用してホストの種類が決定されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-182">When not specified, the [TargetFramework assembly attribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute) is used to determine the type of host.</span></span> <span data-ttu-id="eccee-183">その属性が " *.dll*" から削除されると、.NET Framework ホストが使用されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-183">When that attribute is stripped from the *.dll*, the .NET Framework host is used.</span></span>

- **`--filter <EXPRESSION>`**

  <span data-ttu-id="eccee-184">指定された式を使用して、現在のプロジェクト内のテストを除外します。</span><span class="sxs-lookup"><span data-stu-id="eccee-184">Filters out tests in the current project using the given expression.</span></span> <span data-ttu-id="eccee-185">詳細については、「[フィルター オプションの詳細](#filter-option-details)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eccee-185">For more information, see the [Filter option details](#filter-option-details) section.</span></span> <span data-ttu-id="eccee-186">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[選択的単体テストの実行](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eccee-186">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="eccee-187">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="eccee-187">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="eccee-188">コマンドを停止して、ユーザーの入力または操作のために待機させることができます。</span><span class="sxs-lookup"><span data-stu-id="eccee-188">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="eccee-189">たとえば、認証を完了する場合があります。</span><span class="sxs-lookup"><span data-stu-id="eccee-189">For example, to complete authentication.</span></span> <span data-ttu-id="eccee-190">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-190">Available since .NET Core 3.0 SDK.</span></span>

- **`-l|--logger <LOGGER>`**

  <span data-ttu-id="eccee-191">テスト結果のロガーを指定します。</span><span class="sxs-lookup"><span data-stu-id="eccee-191">Specifies a logger for test results.</span></span> <span data-ttu-id="eccee-192">MSBuild とは異なり、dotnet テストでは省略形は受け入れられません。`-l "console;v=d"` ではなく `-l "console;verbosity=detailed"` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="eccee-192">Unlike MSBuild, dotnet test doesn't accept abbreviations: instead of `-l "console;v=d"` use `-l "console;verbosity=detailed"`.</span></span>

- **`--no-build`**

  <span data-ttu-id="eccee-193">実行前にテスト プロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="eccee-193">Doesn't build the test project before running it.</span></span> <span data-ttu-id="eccee-194">また、- `--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-194">It also implicitly sets the - `--no-restore` flag.</span></span>

- **`--nologo`**

  <span data-ttu-id="eccee-195">Microsoft TestPlatform バナーを表示せずにテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="eccee-195">Run tests without displaying the Microsoft TestPlatform banner.</span></span> <span data-ttu-id="eccee-196">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-196">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="eccee-197">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="eccee-197">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="eccee-198">実行するバイナリを検索するディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="eccee-198">Directory in which to find the binaries to run.</span></span> <span data-ttu-id="eccee-199">指定しない場合、既定のパスは `./bin/<configuration>/<framework>/` になります。</span><span class="sxs-lookup"><span data-stu-id="eccee-199">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="eccee-200">(`TargetFrameworks` プロパティを使用した) ターゲット フレームワークが複数あるプロジェクトの場合は、このオプションを指定するときに `--framework` も定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eccee-200">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="eccee-201">`dotnet test` では常に、出力ディレクトリからテストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-201">`dotnet test` always runs tests from the output directory.</span></span> <span data-ttu-id="eccee-202"><xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> を使用して、出力ディレクトリ内のテスト資産を使用できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-202">You can use <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> to consume test assets in the output directory.</span></span>

- **`-r|--results-directory <RESULTS_DIR>`**

  <span data-ttu-id="eccee-203">テスト結果が配置されるディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="eccee-203">The directory where the test results are going to be placed.</span></span> <span data-ttu-id="eccee-204">指定されたディレクトリが存在しない場合は、作成されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-204">If the specified directory doesn't exist, it's created.</span></span> <span data-ttu-id="eccee-205">既定値は、プロジェクト ファイルが含まれるディレクトリの `TestResults` です。</span><span class="sxs-lookup"><span data-stu-id="eccee-205">The default is `TestResults` in the directory that contains the project file.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="eccee-206">テスト対象のターゲット ランタイム。</span><span class="sxs-lookup"><span data-stu-id="eccee-206">The target runtime to test for.</span></span>

- **`-s|--settings <SETTINGS_FILE>`**

  <span data-ttu-id="eccee-207">テストの実行に使用する `.runsettings` ファイルです。</span><span class="sxs-lookup"><span data-stu-id="eccee-207">The `.runsettings` file to use for running the tests.</span></span> <span data-ttu-id="eccee-208">`TargetPlatform` 要素 (x86|x64) は `dotnet test` には影響しません。</span><span class="sxs-lookup"><span data-stu-id="eccee-208">The `TargetPlatform` element (x86|x64) has no effect for `dotnet test`.</span></span> <span data-ttu-id="eccee-209">x86 を対象とするテストを実行するには、x86 バージョンの .NET Core をインストールします。</span><span class="sxs-lookup"><span data-stu-id="eccee-209">To run tests that target x86, install the x86 version of .NET Core.</span></span> <span data-ttu-id="eccee-210">パスにある *dotnet.exe* のビットは、テストを実行するために使用されるものです。</span><span class="sxs-lookup"><span data-stu-id="eccee-210">The bitness of the *dotnet.exe* that is on the path is what will be used for running tests.</span></span> <span data-ttu-id="eccee-211">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccee-211">For more information, see the following resources:</span></span>

  - [<span data-ttu-id="eccee-212">`.runsettings` ファイルを使用して単体テストを構成します。</span><span class="sxs-lookup"><span data-stu-id="eccee-212">Configure unit tests by using a `.runsettings` file.</span></span>](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [<span data-ttu-id="eccee-213">テスト実行を構成する</span><span class="sxs-lookup"><span data-stu-id="eccee-213">Configure a test run</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  <span data-ttu-id="eccee-214">テストを実行する代わりに、検出されたテストを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="eccee-214">List the discovered tests instead of running the tests.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="eccee-215">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="eccee-215">Sets the verbosity level of the command.</span></span> <span data-ttu-id="eccee-216">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="eccee-216">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="eccee-217">既定値は、`minimal` です。</span><span class="sxs-lookup"><span data-stu-id="eccee-217">The default is `minimal`.</span></span> <span data-ttu-id="eccee-218">詳細については、「<xref:Microsoft.Build.Framework.LoggerVerbosity>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eccee-218">For more information, see <xref:Microsoft.Build.Framework.LoggerVerbosity>.</span></span>

- <span data-ttu-id="eccee-219">**`RunSettings`** 引数</span><span class="sxs-lookup"><span data-stu-id="eccee-219">**`RunSettings`** arguments</span></span>

 <span data-ttu-id="eccee-220">インラインの `RunSettings` は、コマンド ラインの最後の引数として "-- " の後に渡されます (-- の後のスペースに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="eccee-220">Inline `RunSettings` are passed as the last arguments on the command line after "-- " (note the space after --).</span></span> <span data-ttu-id="eccee-221">インラインの `RunSettings` は `[name]=[value]` のペアとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-221">Inline `RunSettings` are specified as `[name]=[value]` pairs.</span></span> <span data-ttu-id="eccee-222">複数の `[name]=[value]` のペアを区切るにはスペースを使用します。</span><span class="sxs-lookup"><span data-stu-id="eccee-222">A space is used to separate multiple `[name]=[value]` pairs.</span></span>

  <span data-ttu-id="eccee-223">例 : `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span><span class="sxs-lookup"><span data-stu-id="eccee-223">Example: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`</span></span>

  <span data-ttu-id="eccee-224">詳しくは、「[コマンド ラインで RunSettings 引数を渡す](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eccee-224">For more information, see [Passing RunSettings arguments through command line](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).</span></span>

## <a name="examples"></a><span data-ttu-id="eccee-225">使用例</span><span class="sxs-lookup"><span data-stu-id="eccee-225">Examples</span></span>

- <span data-ttu-id="eccee-226">現在のディレクトリのプロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="eccee-226">Run the tests in the project in the current directory:</span></span>

  ```dotnetcli
  dotnet test
  ```

- <span data-ttu-id="eccee-227">`test1` プロジェクトでテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="eccee-227">Run the tests in the `test1` project:</span></span>

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- <span data-ttu-id="eccee-228">現在のディレクトリでプロジェクトのテストを実行し、trx 形式でテスト結果ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="eccee-228">Run the tests in the project in the current directory, and generate a test results file in the trx format:</span></span>

  ```dotnetcli
  dotnet test --logger trx
  ```

- <span data-ttu-id="eccee-229">現在のディレクトリでプロジェクトのテストを実行し、([Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) コレクター統合をインストールした後) コード カバレッジ ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="eccee-229">Run the tests in the project in the current directory, and generate a code coverage file (after installing [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/Documentation/VSTestIntegration.md) collectors integration):</span></span>

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- <span data-ttu-id="eccee-230">現在のディレクトリでプロジェクトのテストを実行し、コード カバレッジ ファイルを生成します (Windows のみ)。</span><span class="sxs-lookup"><span data-stu-id="eccee-230">Run the tests in the project in the current directory, and generate a code coverage file (Windows only):</span></span>

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- <span data-ttu-id="eccee-231">現在のディレクトリでプロジェクトのテストを実行し、詳細をコンソールに記録します。</span><span class="sxs-lookup"><span data-stu-id="eccee-231">Run the tests in the project in the current directory, and log with detailed verbosity to the console:</span></span>

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```

- <span data-ttu-id="eccee-232">現在のディレクトリのプロジェクトでテストを実行し、テスト ホストがクラッシュしたときに実行されていたテストを報告します。</span><span class="sxs-lookup"><span data-stu-id="eccee-232">Run the tests in the project in the current directory, and report tests that were in progress when the test host crashed:</span></span>

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a><span data-ttu-id="eccee-233">フィルター オプションの詳細</span><span class="sxs-lookup"><span data-stu-id="eccee-233">Filter option details</span></span>

`--filter <EXPRESSION>`

<span data-ttu-id="eccee-234">`<Expression>` の形式は `<property><operator><value>[|&<Expression>]` です。</span><span class="sxs-lookup"><span data-stu-id="eccee-234">`<Expression>` has the format `<property><operator><value>[|&<Expression>]`.</span></span>

<span data-ttu-id="eccee-235">`<property>` は `Test Case` の属性です。</span><span class="sxs-lookup"><span data-stu-id="eccee-235">`<property>` is an attribute of the `Test Case`.</span></span> <span data-ttu-id="eccee-236">よく利用される単体テスト フレームワークでサポートされるプロパティは以下の通りです。</span><span class="sxs-lookup"><span data-stu-id="eccee-236">The following are the properties supported by popular unit test frameworks:</span></span>

| <span data-ttu-id="eccee-237">テスト フレームワーク</span><span class="sxs-lookup"><span data-stu-id="eccee-237">Test Framework</span></span> | <span data-ttu-id="eccee-238">サポートされるプロパティ</span><span class="sxs-lookup"><span data-stu-id="eccee-238">Supported properties</span></span>                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="eccee-239">MSTest</span><span class="sxs-lookup"><span data-stu-id="eccee-239">MSTest</span></span>         | <ul><li><span data-ttu-id="eccee-240">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="eccee-240">FullyQualifiedName</span></span></li><li><span data-ttu-id="eccee-241">名前</span><span class="sxs-lookup"><span data-stu-id="eccee-241">Name</span></span></li><li><span data-ttu-id="eccee-242">ClassName</span><span class="sxs-lookup"><span data-stu-id="eccee-242">ClassName</span></span></li><li><span data-ttu-id="eccee-243">優先度</span><span class="sxs-lookup"><span data-stu-id="eccee-243">Priority</span></span></li><li><span data-ttu-id="eccee-244">TestCategory</span><span class="sxs-lookup"><span data-stu-id="eccee-244">TestCategory</span></span></li></ul> |
| <span data-ttu-id="eccee-245">xUnit</span><span class="sxs-lookup"><span data-stu-id="eccee-245">xUnit</span></span>          | <ul><li><span data-ttu-id="eccee-246">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="eccee-246">FullyQualifiedName</span></span></li><li><span data-ttu-id="eccee-247">DisplayName</span><span class="sxs-lookup"><span data-stu-id="eccee-247">DisplayName</span></span></li><li><span data-ttu-id="eccee-248">Traits</span><span class="sxs-lookup"><span data-stu-id="eccee-248">Traits</span></span></li></ul>                                   |
| <span data-ttu-id="eccee-249">NUnit</span><span class="sxs-lookup"><span data-stu-id="eccee-249">NUnit</span></span>          | <ul><li><span data-ttu-id="eccee-250">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="eccee-250">FullyQualifiedName</span></span></li><li><span data-ttu-id="eccee-251">名前</span><span class="sxs-lookup"><span data-stu-id="eccee-251">Name</span></span></li><li><span data-ttu-id="eccee-252">TestCategory</span><span class="sxs-lookup"><span data-stu-id="eccee-252">TestCategory</span></span></li><li><span data-ttu-id="eccee-253">優先度</span><span class="sxs-lookup"><span data-stu-id="eccee-253">Priority</span></span></li></ul>                                   |

<span data-ttu-id="eccee-254">`<operator>` は、プロパティと値の関係を示します。</span><span class="sxs-lookup"><span data-stu-id="eccee-254">The `<operator>` describes the relationship between the property and the value:</span></span>

| <span data-ttu-id="eccee-255">演算子</span><span class="sxs-lookup"><span data-stu-id="eccee-255">Operator</span></span> | <span data-ttu-id="eccee-256">関数</span><span class="sxs-lookup"><span data-stu-id="eccee-256">Function</span></span>        |
| :------: | --------------- |
| `=`      | <span data-ttu-id="eccee-257">完全一致</span><span class="sxs-lookup"><span data-stu-id="eccee-257">Exact match</span></span>     |
| `!=`     | <span data-ttu-id="eccee-258">完全一致ではない</span><span class="sxs-lookup"><span data-stu-id="eccee-258">Not exact match</span></span> |
| `~`      | <span data-ttu-id="eccee-259">内容</span><span class="sxs-lookup"><span data-stu-id="eccee-259">Contains</span></span>        |
| `!~`     | <span data-ttu-id="eccee-260">含まない</span><span class="sxs-lookup"><span data-stu-id="eccee-260">Not contains</span></span>    |

<span data-ttu-id="eccee-261">`<value>` は文字列です。</span><span class="sxs-lookup"><span data-stu-id="eccee-261">`<value>` is a string.</span></span> <span data-ttu-id="eccee-262">すべての参照で大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="eccee-262">All the lookups are case insensitive.</span></span>

<span data-ttu-id="eccee-263">`<operator>` を含まない式は、自動的に `FullyQualifiedName` プロパティの `contains` とみなされます (たとえば、`dotnet test --filter xyz` は `dotnet test --filter FullyQualifiedName~xyz` と同じです)。</span><span class="sxs-lookup"><span data-stu-id="eccee-263">An expression without an `<operator>` is automatically considered as a `contains` on `FullyQualifiedName` property (for example, `dotnet test --filter xyz` is same as `dotnet test --filter FullyQualifiedName~xyz`).</span></span>

<span data-ttu-id="eccee-264">式は条件演算子を使用して結合できます。</span><span class="sxs-lookup"><span data-stu-id="eccee-264">Expressions can be joined with conditional operators:</span></span>

| <span data-ttu-id="eccee-265">演算子</span><span class="sxs-lookup"><span data-stu-id="eccee-265">Operator</span></span>            | <span data-ttu-id="eccee-266">関数</span><span class="sxs-lookup"><span data-stu-id="eccee-266">Function</span></span> |
| ------------------- | -------- |
| <code>&#124;</code> | <span data-ttu-id="eccee-267">OR</span><span class="sxs-lookup"><span data-stu-id="eccee-267">OR</span></span>       |
| `&`                 | <span data-ttu-id="eccee-268">AND</span><span class="sxs-lookup"><span data-stu-id="eccee-268">AND</span></span>      |

<span data-ttu-id="eccee-269">条件演算子を使用する場合は、式をかっこで囲みます (例: `(Name~TestMethod1) | (Name~TestMethod2)`)。</span><span class="sxs-lookup"><span data-stu-id="eccee-269">You can enclose expressions in parenthesis when using conditional operators (for example, `(Name~TestMethod1) | (Name~TestMethod2)`).</span></span>

<span data-ttu-id="eccee-270">選択的単体テストのフィルター処理の使用方法に関する詳細と例については、「[選択的単体テストの実行](../testing/selective-unit-tests.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="eccee-270">For more information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eccee-271">関連項目</span><span class="sxs-lookup"><span data-stu-id="eccee-271">See also</span></span>

- [<span data-ttu-id="eccee-272">フレームワークとターゲット</span><span class="sxs-lookup"><span data-stu-id="eccee-272">Frameworks and Targets</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="eccee-273">.NET Runtime Identifier (RID) カタログ</span><span class="sxs-lookup"><span data-stu-id="eccee-273">.NET Runtime Identifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="eccee-274">コマンドラインを使用して runsettings 引数を渡す</span><span class="sxs-lookup"><span data-stu-id="eccee-274">Passing runsettings arguments through commandline</span></span>](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
