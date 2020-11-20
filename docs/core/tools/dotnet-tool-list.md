---
title: dotnet tool list コマンド
description: dotnet tool list コマンドを実行すると、お使いのコンピューターにインストールされている .NET ツールが一覧表示されます。
ms.date: 02/14/2020
ms.openlocfilehash: d884f2c41834dd9704de3a8ca15417ba368fde4b
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634286"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="ee7e2-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="ee7e2-103">dotnet tool list</span></span>

<span data-ttu-id="ee7e2-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="ee7e2-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ee7e2-105">名前</span><span class="sxs-lookup"><span data-stu-id="ee7e2-105">Name</span></span>

<span data-ttu-id="ee7e2-106">`dotnet tool list` - お使いのコンピューターに現在インストールされている指定した種類の [.NET ツール](global-tools.md)を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-106">`dotnet tool list` - Lists all [.NET tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ee7e2-107">構文</span><span class="sxs-lookup"><span data-stu-id="ee7e2-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="ee7e2-108">説明</span><span class="sxs-lookup"><span data-stu-id="ee7e2-108">Description</span></span>

<span data-ttu-id="ee7e2-109">`dotnet tool list` コマンドを実行すると、お使いのコンピューターにインストールされている .NET グローバル ツール、ツールパス、またはローカル ツールが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-109">The `dotnet tool list` command provides a way for you to list all .NET global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="ee7e2-110">コマンドでは、パッケージ名、インストールされているバージョン、およびツール コマンドを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="ee7e2-111">コマンドを使用するには、次のいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="ee7e2-112">既定の場所にインストールされているグローバル ツールを一覧表示するには、`--global` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="ee7e2-113">ユーザー指定の場所にインストールされているグローバル ツールを一覧表示するには、`--tool-path` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="ee7e2-114">ローカル ツールを一覧表示するには、`--local` オプションを使用するか、`--global` オプション、`--tool-path` オプション、および `--local` オプションを省略します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-114">To list local tools, use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="ee7e2-115">**ローカル ツールは .NET Core SDK 3.0 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="ee7e2-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="ee7e2-116">オプション</span><span class="sxs-lookup"><span data-stu-id="ee7e2-116">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="ee7e2-117">ユーザー全体のグローバル ツールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-117">Lists user-wide global tools.</span></span> <span data-ttu-id="ee7e2-118">`--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-118">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="ee7e2-119">`--global` と `--tool-path` の両方を省略すると、ローカル ツールが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-119">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ee7e2-120">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-120">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="ee7e2-121">現在のディレクトリのローカル ツールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-121">Lists local tools for the current directory.</span></span> <span data-ttu-id="ee7e2-122">`--global` または `--tool-path` オプションとは組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-122">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="ee7e2-123">`--global` と `--tool-path` の両方を省略すると、`--local` が指定されていない場合でも、ローカル ツールが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-123">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="ee7e2-124">グローバル ツールを検索するカスタムの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="ee7e2-125">PATH は絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="ee7e2-126">`--global` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="ee7e2-127">`--global` と `--tool-path` の両方を省略すると、ローカル ツールが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="ee7e2-128">使用例</span><span class="sxs-lookup"><span data-stu-id="ee7e2-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="ee7e2-129">お使いのコンピューター (現在のユーザー プロファイル) 上でユーザー全体にインストールされているすべてのグローバル ツールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="ee7e2-130">特定の Windows ディレクトリからグローバル ツールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="ee7e2-131">特定の Linux/macOS ディレクトリからグローバル ツールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="ee7e2-132">**`dotnet tool list`** または **`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="ee7e2-132">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="ee7e2-133">現在のディレクトリで使用可能なすべてのローカル ツールを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="ee7e2-133">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee7e2-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee7e2-134">See also</span></span>

- [<span data-ttu-id="ee7e2-135">.NET ツール</span><span class="sxs-lookup"><span data-stu-id="ee7e2-135">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="ee7e2-136">チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="ee7e2-136">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="ee7e2-137">チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="ee7e2-137">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
