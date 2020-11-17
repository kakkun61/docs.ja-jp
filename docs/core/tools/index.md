---
title: .NET CLI
titleSuffix: ''
description: .NET CLI とその機能に関する概要です。
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 6a12e2d16afe36092c10e14a7465fa3bdbb23f32
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633857"
---
# <a name="net-cli-overview"></a><span data-ttu-id="c91db-103">.NET CLI の概要</span><span class="sxs-lookup"><span data-stu-id="c91db-103">.NET CLI overview</span></span>

<span data-ttu-id="c91db-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="c91db-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="c91db-105">.NET コマンド ライン インターフェイス (CLI) は、.NET アプリケーションを開発、ビルド、実行、発行するためのクロスプラットフォーム ツールチェーンです。</span><span class="sxs-lookup"><span data-stu-id="c91db-105">The .NET command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span>

<span data-ttu-id="c91db-106">.NET CLI は、[.NET SDK](../sdk.md) に含まれています。</span><span class="sxs-lookup"><span data-stu-id="c91db-106">The .NET CLI is included with the [.NET SDK](../sdk.md).</span></span> <span data-ttu-id="c91db-107">.NET SDK をインストールする方法については、[.NET のインストール](../install/windows.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c91db-107">To learn how to install the .NET SDK, see [Install .NET Core](../install/windows.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="c91db-108">CLI コマンド</span><span class="sxs-lookup"><span data-stu-id="c91db-108">CLI commands</span></span>

<span data-ttu-id="c91db-109">既定では、次のコマンドがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c91db-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="c91db-110">基本的なコマンド</span><span class="sxs-lookup"><span data-stu-id="c91db-110">Basic commands</span></span>

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="c91db-111">プロジェクトの変更コマンド</span><span class="sxs-lookup"><span data-stu-id="c91db-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="c91db-112">高度なコマンド</span><span class="sxs-lookup"><span data-stu-id="c91db-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="c91db-113">ツール管理コマンド</span><span class="sxs-lookup"><span data-stu-id="c91db-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="c91db-114">[`tool restore`](global-tools.md#install-a-local-tool) .NET Core SDK 3.0 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="c91db-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="c91db-115">[`tool run`](global-tools.md#invoke-a-local-tool) .NET Core SDK 3.0 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="c91db-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="c91db-116">ツールは、NuGet パッケージからインストールされ、コマンド プロンプトから呼び出されるコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="c91db-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="c91db-117">ツールは自分で作成することも、サードパーティによって作成されたツールをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="c91db-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="c91db-118">ツールは、グローバル ツール、ツールパス ツール、およびローカル ツールとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c91db-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="c91db-119">詳細については、[.NET ツールの概要](global-tools.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c91db-119">For more information, see [.NET tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="c91db-120">コマンド構造</span><span class="sxs-lookup"><span data-stu-id="c91db-120">Command structure</span></span>

<span data-ttu-id="c91db-121">CLI コマンド構造は、[ドライバー ("dotnet")](#driver) と[コマンド](#command)、また場合によってはコマンドの[引数](#arguments)と[オプション](#options)で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c91db-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="c91db-122">*my_app* という名前のディレクトリから実行する場合、次のコマンドで示されているように、新しいコンソール アプリの作成やコマンド ラインからの実行など、ほとんどの CLI 操作でこのパターンが見られます。</span><span class="sxs-lookup"><span data-stu-id="c91db-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="c91db-123">ドライバー</span><span class="sxs-lookup"><span data-stu-id="c91db-123">Driver</span></span>

<span data-ttu-id="c91db-124">ドライバーは [dotnet](dotnet.md) という名前で、2 つの役割 ([フレームワークに依存するアプリ](../deploying/index.md)の実行と、コマンドの実行) があります。</span><span class="sxs-lookup"><span data-stu-id="c91db-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="c91db-125">フレームワークに依存するアプリを実行するには、`dotnet /path/to/my_app.dll` など、ドライバーの後にアプリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c91db-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="c91db-126">アプリの DLL が存在するフォルダーからコマンドを実行する場合は、`dotnet my_app.dll` を実行するだけです。</span><span class="sxs-lookup"><span data-stu-id="c91db-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="c91db-127">.NET ランタイムの特定のバージョンを使用する場合は、`--fx-version <VERSION>` オプションを使用してください (「[dotnet コマンド](dotnet.md)」リファレンスを参照)。</span><span class="sxs-lookup"><span data-stu-id="c91db-127">If you want to use a specific version of the .NET Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="c91db-128">ドライバーにコマンドを指定すると、`dotnet.exe` は CLI コマンドの実行プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="c91db-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="c91db-129">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c91db-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="c91db-130">最初に、ドライバーは使用する SDK のバージョンを決定します。</span><span class="sxs-lookup"><span data-stu-id="c91db-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="c91db-131">[global.json](global-json.md) ファイルがない場合は、利用可能な SDK の最新バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="c91db-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="c91db-132">コンピューターで最新のプレビューまたは安定したバージョンになります。</span><span class="sxs-lookup"><span data-stu-id="c91db-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="c91db-133">SDK バージョンが決定されたら、コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c91db-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="c91db-134">コマンド</span><span class="sxs-lookup"><span data-stu-id="c91db-134">Command</span></span>

<span data-ttu-id="c91db-135">コマンドは、アクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="c91db-135">The command performs an action.</span></span> <span data-ttu-id="c91db-136">たとえば、`dotnet build` はコードをビルドします。</span><span class="sxs-lookup"><span data-stu-id="c91db-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="c91db-137">`dotnet publish` はコードを発行します。</span><span class="sxs-lookup"><span data-stu-id="c91db-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="c91db-138">コマンドは、`dotnet {command}` 規則を使用してコンソール アプリケーションとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="c91db-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="c91db-139">引数</span><span class="sxs-lookup"><span data-stu-id="c91db-139">Arguments</span></span>

<span data-ttu-id="c91db-140">コマンド ラインで渡す引数は、呼び出されたコマンドへの引数です。</span><span class="sxs-lookup"><span data-stu-id="c91db-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="c91db-141">たとえば、`dotnet publish my_app.csproj` を実行した場合、`my_app.csproj` 引数は、発行するプロジェクトを示し、`publish` コマンドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="c91db-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="c91db-142">オプション</span><span class="sxs-lookup"><span data-stu-id="c91db-142">Options</span></span>

<span data-ttu-id="c91db-143">コマンド ラインで渡すオプションは、呼び出されたコマンドへのオプションです。</span><span class="sxs-lookup"><span data-stu-id="c91db-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="c91db-144">たとえば、`dotnet publish --output /build_output` を実行した場合、`--output` オプションとその値は `publish` コマンドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="c91db-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="c91db-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="c91db-145">See also</span></span>

- [<span data-ttu-id="c91db-146">dotnet/sdk GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="c91db-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="c91db-147">.NET インストール ガイド</span><span class="sxs-lookup"><span data-stu-id="c91db-147">.NET installation guide</span></span>](../install/windows.md)
