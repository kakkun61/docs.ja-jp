---
title: dotnet run コマンド
description: dotnet run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。
ms.date: 02/19/2020
ms.openlocfilehash: c80f290c75e3bac65ae73fe8edada53db4ce86f8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634417"
---
# <a name="dotnet-run"></a><span data-ttu-id="81b24-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="81b24-103">dotnet run</span></span>

<span data-ttu-id="81b24-104">**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="81b24-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="81b24-105">名前</span><span class="sxs-lookup"><span data-stu-id="81b24-105">Name</span></span>

<span data-ttu-id="81b24-106">`dotnet run` -- 明示的なコンパイルや起動コマンドなしで、ソース コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="81b24-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="81b24-107">構文</span><span class="sxs-lookup"><span data-stu-id="81b24-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="81b24-108">説明</span><span class="sxs-lookup"><span data-stu-id="81b24-108">Description</span></span>

<span data-ttu-id="81b24-109">`dotnet run` コマンドは、1 つのコマンドを使用して、ソース コードからアプリケーションを実行する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="81b24-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="81b24-110">コマンド ラインからの短期間の反復開発に便利です。</span><span class="sxs-lookup"><span data-stu-id="81b24-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="81b24-111">このコマンドは [`dotnet build`](dotnet-build.md) コマンドに依存し、コードをビルドします。</span><span class="sxs-lookup"><span data-stu-id="81b24-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="81b24-112">そのため、プロジェクトを最初に復元する必要があるなど、ビルドに要件があれば、それが `dotnet run` にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="81b24-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="81b24-113">出力ファイルは既定の場所である `bin/<configuration>/<target>` に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="81b24-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="81b24-114">たとえば、`netcoreapp2.1` というアプリケーションがあり、`dotnet run` を実行する場合、`bin/Debug/netcoreapp2.1` に出力されます。</span><span class="sxs-lookup"><span data-stu-id="81b24-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="81b24-115">必要に応じて、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="81b24-115">Files are overwritten as needed.</span></span> <span data-ttu-id="81b24-116">一時ファイルは `obj` ディレクトリに置かれます。</span><span class="sxs-lookup"><span data-stu-id="81b24-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="81b24-117">フレームワークを複数指定するプロジェクトの場合、`-f|--framework <FRAMEWORK>` オプションを使用してフレームワークを指定しない限り、`dotnet run` を実行するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="81b24-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="81b24-118">`dotnet run` コマンドは、ビルド済みのアセンブリではなく、プロジェクトのコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="81b24-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="81b24-119">代わりにフレームワークに依存するアプリケーション DLL の実行を試みる場合は、コマンドなしで [dotnet](dotnet.md) を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81b24-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="81b24-120">たとえば、`myapp.dll` を実行する場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="81b24-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="81b24-121">`dotnet` ドライバーの詳細については、[.NET コマンド ライン ツール (CLI)](index.md) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81b24-121">For more information on the `dotnet` driver, see the [.NET Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="81b24-122">アプリケーションを実行するため、`dotnet run` コマンドは、NuGet キャッシュから共有ランタイムの外にあるアプリケーションの依存関係を解決します。</span><span class="sxs-lookup"><span data-stu-id="81b24-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="81b24-123">このコマンドではキャッシュされた依存関係を使用するため、`dotnet run` を使用してアプリケーションを実稼働環境で実行することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="81b24-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="81b24-124">代わりに、[`dotnet publish`](dotnet-publish.md) コマンドを使用して[展開を作成](../deploying/index.md)し、発行された出力を展開します。</span><span class="sxs-lookup"><span data-stu-id="81b24-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="81b24-125">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="81b24-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="81b24-126">オプション</span><span class="sxs-lookup"><span data-stu-id="81b24-126">Options</span></span>

- **`--`**

  <span data-ttu-id="81b24-127">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="81b24-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="81b24-128">この区切り記号の後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="81b24-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="81b24-129">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="81b24-129">Defines the build configuration.</span></span> <span data-ttu-id="81b24-130">ほとんどのプロジェクトの既定値は `Debug` ですが、プロジェクトでビルド構成設定をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="81b24-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="81b24-131">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="81b24-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="81b24-132">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81b24-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="81b24-133">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="81b24-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="81b24-134">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="81b24-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="81b24-135">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="81b24-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="81b24-136">コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。</span><span class="sxs-lookup"><span data-stu-id="81b24-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="81b24-137">.NET Core 3.0 SDK 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="81b24-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="81b24-138">アプリケーションを起動する場合に使用する起動プロファイル (存在する場合) の名前です。</span><span class="sxs-lookup"><span data-stu-id="81b24-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="81b24-139">起動プロファイルは *launchSettings.json* ファイル内に定義されており、通常は、`Development`、`Staging`、`Production` と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="81b24-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="81b24-140">詳細については、[「Working with multiple environments」](/aspnet/core/fundamentals/environments) (複数の環境での使用) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="81b24-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="81b24-141">実行前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="81b24-141">Doesn't build the project before running.</span></span> <span data-ttu-id="81b24-142">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="81b24-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="81b24-143">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="81b24-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="81b24-144">アプリケーションを構成するための *launchSettings.json* の使用を試みません。</span><span class="sxs-lookup"><span data-stu-id="81b24-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="81b24-145">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="81b24-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="81b24-146">実行するプロジェクト ファイルのパスを指定します (フォルダー名または完全なパス)。</span><span class="sxs-lookup"><span data-stu-id="81b24-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="81b24-147">指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="81b24-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="81b24-148">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="81b24-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="81b24-149">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="81b24-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="81b24-150">.NET Core 3.0 SDK 以降、`-r` の短いオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="81b24-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="81b24-151">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="81b24-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="81b24-152">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="81b24-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="81b24-153">既定値は `m` です。</span><span class="sxs-lookup"><span data-stu-id="81b24-153">The default value is `m`.</span></span> <span data-ttu-id="81b24-154">.NET Core 2.1 SDK 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="81b24-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="81b24-155">使用例</span><span class="sxs-lookup"><span data-stu-id="81b24-155">Examples</span></span>

- <span data-ttu-id="81b24-156">現在のディレクトリのプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="81b24-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="81b24-157">指定されたプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="81b24-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="81b24-158">現在のディレクトリのプロジェクトを実行します (この例では、空の `--` オプションが使用されているため、`--help` 引数がアプリケーションに渡されます)。</span><span class="sxs-lookup"><span data-stu-id="81b24-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="81b24-159">最小限の出力のみを表示して、現在のディレクトリでプロジェクトの依存関係とツールを復元し、プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="81b24-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project:</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
