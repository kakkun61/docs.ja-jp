---
title: dotnet tool restore コマンド
description: dotnet tool restore コマンドを実行すると、現在のディレクトリのスコープ内にある .NET ローカル ツールがお使いのコンピューターにインストールされます。
ms.date: 02/14/2020
ms.openlocfilehash: 3425bc6b78fd53f578c209013f83b006305dbb81
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242930"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="825cd-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="825cd-103">dotnet tool restore</span></span>

<span data-ttu-id="825cd-104">**この記事の対象:** ✔️ .NET Core 3.0 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="825cd-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="825cd-105">名前</span><span class="sxs-lookup"><span data-stu-id="825cd-105">Name</span></span>

<span data-ttu-id="825cd-106">`dotnet tool restore` - 現在のディレクトリのスコープ内にある .NET ローカル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="825cd-106">`dotnet tool restore` - Installs the .NET local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="825cd-107">構文</span><span class="sxs-lookup"><span data-stu-id="825cd-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore
    [--configfile <FILE>] [--add-source <SOURCE>]
    [tool-manifest <PATH_TO_MANIFEST_FILE>] [--disable-parallel]
    [--ignore-failed-sources] [--no-cache] [--interactive]
    [-v|--verbosity <LEVEL>]

dotnet tool restore -h|--help
```

## <a name="description"></a><span data-ttu-id="825cd-108">説明</span><span class="sxs-lookup"><span data-stu-id="825cd-108">Description</span></span>

<span data-ttu-id="825cd-109">`dotnet tool restore` コマンドでは、現在のディレクトリのスコープ内にあるツール マニフェスト ファイルを検索し、そこに一覧表示されたツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="825cd-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="825cd-110">マニフェスト ファイルの詳細については、「[ローカル ツールのインストール](global-tools.md#install-a-local-tool)」および「[ローカル ツールの起動](global-tools.md#invoke-a-local-tool)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="825cd-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="options"></a><span data-ttu-id="825cd-111">オプション</span><span class="sxs-lookup"><span data-stu-id="825cd-111">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="825cd-112">使用する NuGet 構成 (*nuget.config*) ファイル。</span><span class="sxs-lookup"><span data-stu-id="825cd-112">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="825cd-113">インストール時に使用するために追加の NuGet パッケージ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="825cd-113">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="825cd-114">マニフェスト ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="825cd-114">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="825cd-115">複数のプロジェクトを並行して復元できないようにします。</span><span class="sxs-lookup"><span data-stu-id="825cd-115">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="825cd-116">パッケージ ソース エラーを警告として処理します。</span><span class="sxs-lookup"><span data-stu-id="825cd-116">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="825cd-117">パッケージと HTTP 要求をキャッシュしません。</span><span class="sxs-lookup"><span data-stu-id="825cd-117">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="825cd-118">コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。</span><span class="sxs-lookup"><span data-stu-id="825cd-118">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="825cd-119">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="825cd-119">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="825cd-120">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="825cd-120">Sets the verbosity level of the command.</span></span> <span data-ttu-id="825cd-121">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="825cd-121">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="825cd-122">例</span><span class="sxs-lookup"><span data-stu-id="825cd-122">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="825cd-123">現在のディレクトリのローカル ツールを復元します。</span><span class="sxs-lookup"><span data-stu-id="825cd-123">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="825cd-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="825cd-124">See also</span></span>

- [<span data-ttu-id="825cd-125">.NET ツール</span><span class="sxs-lookup"><span data-stu-id="825cd-125">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="825cd-126">チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="825cd-126">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
