---
title: dotnet tool uninstall コマンド
description: dotnet tool uninstall コマンドでは、お使いのコンピューター上から指定された .NET ツールをアンインストールします。
ms.date: 02/14/2020
ms.openlocfilehash: 34dffde8f9c930327c6b42d1d89bb4f511959fb2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634091"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="d92c1-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="d92c1-103">dotnet tool uninstall</span></span>

<span data-ttu-id="d92c1-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="d92c1-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d92c1-105">名前</span><span class="sxs-lookup"><span data-stu-id="d92c1-105">Name</span></span>

<span data-ttu-id="d92c1-106">`dotnet tool uninstall` - お使いのコンピューター上から指定された [.NET ツール](global-tools.md)をアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="d92c1-106">`dotnet tool uninstall` - Uninstalls the specified [.NET tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d92c1-107">構文</span><span class="sxs-lookup"><span data-stu-id="d92c1-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="d92c1-108">説明</span><span class="sxs-lookup"><span data-stu-id="d92c1-108">Description</span></span>

<span data-ttu-id="d92c1-109">`dotnet tool uninstall` コマンドを使用すると、お使いのコンピューター上から .NET ツールをアンインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="d92c1-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET tools from your machine.</span></span> <span data-ttu-id="d92c1-110">コマンドを使用するには、次のいずれかのオプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d92c1-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="d92c1-111">既定の場所にインストールされたグローバル ツールをアンインストールするには、`--global` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="d92c1-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="d92c1-112">カスタムの場所にインストールされたグローバル ツールをアンインストールするには、`--tool-path` オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="d92c1-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="d92c1-113">ローカル ツールをアンインストールするには、`--global` および `--tool-path` オプションを省略します。</span><span class="sxs-lookup"><span data-stu-id="d92c1-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="d92c1-114">**ローカル ツールは .NET Core SDK 3.0 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="d92c1-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="d92c1-115">引数</span><span class="sxs-lookup"><span data-stu-id="d92c1-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="d92c1-116">アンインストールする .NET ツールが格納されている NuGet パッケージの名前または ID。</span><span class="sxs-lookup"><span data-stu-id="d92c1-116">Name/ID of the NuGet package that contains the .NET tool to uninstall.</span></span> <span data-ttu-id="d92c1-117">パッケージを見つけるには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d92c1-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="d92c1-118">オプション</span><span class="sxs-lookup"><span data-stu-id="d92c1-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="d92c1-119">ツールがユーザー全体のインストールから削除されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d92c1-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="d92c1-120">`--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="d92c1-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="d92c1-121">`--global` と `--tool-path` の両方を省略すると、削除されるツールはローカル ツールであると指定されます。</span><span class="sxs-lookup"><span data-stu-id="d92c1-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d92c1-122">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="d92c1-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="d92c1-123">ツールをアンインストールする場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="d92c1-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="d92c1-124">PATH は絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="d92c1-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="d92c1-125">`--global` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="d92c1-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="d92c1-126">`--global` と `--tool-path` の両方を省略すると、削除されるツールはローカル ツールであると指定されます。</span><span class="sxs-lookup"><span data-stu-id="d92c1-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="d92c1-127">使用例</span><span class="sxs-lookup"><span data-stu-id="d92c1-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="d92c1-128">[dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="d92c1-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="d92c1-129">特定の Windows ディレクトリから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="d92c1-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="d92c1-130">特定の Linux/macOS ディレクトリから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="d92c1-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="d92c1-131">現在のディレクトリから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) ローカル ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="d92c1-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="d92c1-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="d92c1-132">See also</span></span>

- [<span data-ttu-id="d92c1-133">.NET ツール</span><span class="sxs-lookup"><span data-stu-id="d92c1-133">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="d92c1-134">チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="d92c1-134">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="d92c1-135">チュートリアル: .NET CLI を使って .NET ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="d92c1-135">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
