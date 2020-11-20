---
title: 'チュートリアル: .NET グローバル ツールをインストールして使用する'
description: .NET ツールをグローバル ツールとしてインストールして使用する方法について説明します。
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 01b773516da92fb16fb0f67fc6617e0c70d17c9d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633896"
---
# <a name="tutorial-install-and-use-a-net-global-tool-using-the-net-cli"></a><span data-ttu-id="d1ec4-103">チュートリアル: .NET CLI を使って .NET グローバル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="d1ec4-103">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>

<span data-ttu-id="d1ec4-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="d1ec4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="d1ec4-105">このチュートリアルでは、グローバル ツールをインストールして使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="d1ec4-106">[このシリーズの最初のチュートリアル](global-tools-how-to-create.md)で作成されるツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1ec4-107">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d1ec4-107">Prerequisites</span></span>

* <span data-ttu-id="d1ec4-108">[このシリーズの最初のチュートリアル](global-tools-how-to-create.md)を完了します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="d1ec4-109">グローバル ツールとしてツールを使用する</span><span class="sxs-lookup"><span data-stu-id="d1ec4-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="d1ec4-110">*microsoft.botsay* プロジェクト フォルダーに [dotnet tool install](dotnet-tool-install.md) コマンドを実行して、パッケージからツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="d1ec4-111">`--global` パラメーターは、PATH 環境変数に自動的に追加される既定の場所にツール バイナリをインストールするように、.NET CLI に指示します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-111">The `--global` parameter tells the .NET CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="d1ec4-112">`--add-source` パラメーターは、NuGet パッケージへの追加のソース フィードとして *./nupkg* ディレクトリを一時的に使用するように、.NET CLI に指示します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-112">The `--add-source` parameter tells the .NET CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="d1ec4-113">Nuget.org サイト上ではなく、必ず *./nupkg* ディレクトリ内だけで見つかるように、パッケージには一意の名前を付けました。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="d1ec4-114">出力には、ツールの呼び出しに使用されたコマンドと、インストールされているバージョンが示されます。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="d1ec4-115">ツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="d1ec4-116">このコマンドが失敗すると、新しいターミナルを開いて PATH を更新することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="d1ec4-117">[dotnet tool uninstall](dotnet-tool-uninstall.md) コマンドを実行して、ツールを削除します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="d1ec4-118">カスタムの場所にインストールされているグローバル ツールとしてツールを使用する</span><span class="sxs-lookup"><span data-stu-id="d1ec4-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="d1ec4-119">パッケージからツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-119">Install the tool from the package.</span></span>

   <span data-ttu-id="d1ec4-120">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="d1ec4-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="d1ec4-121">Linux または macOS の場合:</span><span class="sxs-lookup"><span data-stu-id="d1ec4-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="d1ec4-122">`--tool-path` パラメーターは、指定された場所にツール バイナリをインストールするように、.NET CLI に指示します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-122">The `--tool-path` parameter tells the .NET CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="d1ec4-123">ディレクトリが存在しなければ、作成されます。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="d1ec4-124">このディレクトリは、PATH 環境変数に自動的に追加されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="d1ec4-125">出力には、ツールの呼び出しに使用されたコマンドと、インストールされているバージョンが示されます。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="d1ec4-126">ツールを起動します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-126">Invoke the tool:</span></span>

   <span data-ttu-id="d1ec4-127">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="d1ec4-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="d1ec4-128">Linux または macOS の場合:</span><span class="sxs-lookup"><span data-stu-id="d1ec4-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="d1ec4-129">[dotnet tool uninstall](dotnet-tool-uninstall.md) コマンドを実行して、ツールを削除します。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="d1ec4-130">Windows の場合:</span><span class="sxs-lookup"><span data-stu-id="d1ec4-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="d1ec4-131">Linux または macOS の場合:</span><span class="sxs-lookup"><span data-stu-id="d1ec4-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="d1ec4-132">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d1ec4-132">Troubleshoot</span></span>

<span data-ttu-id="d1ec4-133">チュートリアルの実行中にエラー メッセージが表示された場合は、「[.NET ツールの使用に関する問題のトラブルシューティング](troubleshoot-usage-issues.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-133">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d1ec4-134">次の手順</span><span class="sxs-lookup"><span data-stu-id="d1ec4-134">Next steps</span></span>

<span data-ttu-id="d1ec4-135">このチュートリアルでは、ツールをグローバル ツールとしてインストールして使用しました。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="d1ec4-136">ローカル ツールと同じツールをインストールして使用するには、次のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="d1ec4-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1ec4-137">ローカル ツールをインストールして使用する</span><span class="sxs-lookup"><span data-stu-id="d1ec4-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
