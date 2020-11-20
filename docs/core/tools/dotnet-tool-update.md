---
title: dotnet tool update コマンド
description: dotnet tool update コマンドは、お使いのコンピューター上の指定された .NET ツールを更新します。
ms.date: 07/08/2020
ms.openlocfilehash: 18b153e53a6dbcb32e50ae4a7d06a1c2f53d1eb5
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634078"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="2cb95-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="2cb95-103">dotnet tool update</span></span>

<span data-ttu-id="2cb95-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="2cb95-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2cb95-105">名前</span><span class="sxs-lookup"><span data-stu-id="2cb95-105">Name</span></span>

<span data-ttu-id="2cb95-106">`dotnet tool update` - お使いのコンピューター上の指定された [.NET ツール](global-tools.md)を更新します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-106">`dotnet tool update` - Updates the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2cb95-107">構文</span><span class="sxs-lookup"><span data-stu-id="2cb95-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="2cb95-108">説明</span><span class="sxs-lookup"><span data-stu-id="2cb95-108">Description</span></span>

<span data-ttu-id="2cb95-109">`dotnet tool update` コマンドを使用すると、お使いのコンピューター上の .NET ツールをパッケージの最新の安定バージョンに更新することができます。</span><span class="sxs-lookup"><span data-stu-id="2cb95-109">The `dotnet tool update` command provides a way for you to update .NET tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="2cb95-110">このコマンドは、ツールをアンインストールして再インストールして、効果的に更新します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="2cb95-111">コマンドを使用するには、次のいずれかのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="2cb95-112">既定の場所にインストールされたグローバル ツールを更新するには、`--global` オプションを使用します</span><span class="sxs-lookup"><span data-stu-id="2cb95-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="2cb95-113">カスタムの場所にインストールされたグローバル ツールを更新するには、`--tool-path` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="2cb95-114">ローカル ツールを更新するには、`--local` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-114">To update a local tool, use the `--local` option.</span></span>

<span data-ttu-id="2cb95-115">**ローカル ツールは .NET Core SDK 3.0 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="2cb95-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="2cb95-116">引数</span><span class="sxs-lookup"><span data-stu-id="2cb95-116">Arguments</span></span>

- **`PACKAGE_ID`**

  <span data-ttu-id="2cb95-117">更新する .NET グローバル ツールが格納されている NuGet パッケージの名前または ID。</span><span class="sxs-lookup"><span data-stu-id="2cb95-117">Name/ID of the NuGet package that contains the .NET global tool to update.</span></span> <span data-ttu-id="2cb95-118">パッケージを見つけるには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2cb95-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="2cb95-119">オプション</span><span class="sxs-lookup"><span data-stu-id="2cb95-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="2cb95-120">インストール時に使用するために追加の NuGet パッケージ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2cb95-121">使用する NuGet 構成 (*nuget.config*) ファイル。</span><span class="sxs-lookup"><span data-stu-id="2cb95-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="2cb95-122">複数のプロジェクトを並行して復元できないようにします。</span><span class="sxs-lookup"><span data-stu-id="2cb95-122">Prevent restoring multiple projects in parallel.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="2cb95-123">ツールを更新する[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-123">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="2cb95-124">パッケージ ソース エラーを警告として処理します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-124">Treat package source failures as warnings.</span></span>

- **`--interactive`**

  <span data-ttu-id="2cb95-125">コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。</span><span class="sxs-lookup"><span data-stu-id="2cb95-125">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`--local`**

  <span data-ttu-id="2cb95-126">ツールとローカル ツール マニフェストを更新します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-126">Update the tool and the local tool manifest.</span></span> <span data-ttu-id="2cb95-127">`--global` オプションまたは `--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="2cb95-127">Can't be combined with the `--global` option or the `--tool-path` option.</span></span>

- **`--no-cache`**

  <span data-ttu-id="2cb95-128">パッケージと HTTP 要求はキャッシュしないでください。</span><span class="sxs-lookup"><span data-stu-id="2cb95-128">Do not cache packages and HTTP requests.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="2cb95-129">マニフェスト ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="2cb95-129">Path to the manifest file.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="2cb95-130">グローバル ツールがインストールされている場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-130">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="2cb95-131">PATH は絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="2cb95-131">PATH can be absolute or relative.</span></span> <span data-ttu-id="2cb95-132">`--global` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="2cb95-132">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="2cb95-133">`--global` と `--tool-path` の両方を省略すると、更新されるツールはローカル ツールであると指定されます。</span><span class="sxs-lookup"><span data-stu-id="2cb95-133">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`--version <VERSION>`**

  <span data-ttu-id="2cb95-134">更新対象のツール パッケージのバージョン範囲。</span><span class="sxs-lookup"><span data-stu-id="2cb95-134">The version range of the tool package to update to.</span></span> <span data-ttu-id="2cb95-135">これはバージョンのダウングレードに使用できません。その前に新しいバージョンを `uninstall` する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2cb95-135">This cannot be used to downgrade versions, you must `uninstall` newer versions first.</span></span>

- **`-g|--global`**

  <span data-ttu-id="2cb95-136">更新プログラムがユーザー全体のツール用であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-136">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="2cb95-137">`--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="2cb95-137">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="2cb95-138">`--global` と `--tool-path` の両方を省略すると、更新されるツールはローカル ツールであると指定されます。</span><span class="sxs-lookup"><span data-stu-id="2cb95-138">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2cb95-139">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-139">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2cb95-140">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2cb95-141">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="2cb95-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="2cb95-142">使用例</span><span class="sxs-lookup"><span data-stu-id="2cb95-142">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="2cb95-143">[dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-143">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="2cb95-144">特定の Windows ディレクトリに配置されている [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-144">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="2cb95-145">特定の Linux/macOS ディレクトリに配置されている [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-145">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="2cb95-146">現在のディレクトリに対してインストールされている [dotnetsay](https://www.nuget.org/packages/dotnetsay/) ローカル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="2cb95-146">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  <span data-ttu-id="2cb95-147">[dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを最新パッチ バージョンに更新します。メジャー バージョンが `2` で、マイナー バージョンが `0` です。</span><span class="sxs-lookup"><span data-stu-id="2cb95-147">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the latest patch version, with a major version of `2`, and a minor version of `0`.</span></span>

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  <span data-ttu-id="2cb95-148">指定の範囲 `(> 2.0.0 && < 2.1.4)` 内で [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを一番下のバージョンに更新します。バージョン `2.1.0` がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="2cb95-148">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the lowest version within the specified range `(> 2.0.0 && < 2.1.4)`, version `2.1.0` would be installed.</span></span> <span data-ttu-id="2cb95-149">セマンティック バージョン管理の範囲に関する詳細については、[NuGet パッケージのバージョン管理範囲](/nuget/concepts/package-versioning#version-ranges)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cb95-149">For more information on semantic versioning ranges, see [NuGet packaging version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

## <a name="see-also"></a><span data-ttu-id="2cb95-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="2cb95-150">See also</span></span>

- [<span data-ttu-id="2cb95-151">.NET ツール</span><span class="sxs-lookup"><span data-stu-id="2cb95-151">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="2cb95-152">セマンティック バージョン管理</span><span class="sxs-lookup"><span data-stu-id="2cb95-152">Semantic versioning</span></span>](https://semver.org)
- [<span data-ttu-id="2cb95-153">チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="2cb95-153">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="2cb95-154">チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="2cb95-154">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
