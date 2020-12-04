---
title: Raspberry Pi への .NET アプリのデプロイ
description: .NET アプリを Raspberry Pi にデプロイする方法について説明します。
author: camsoper
ms.author: casoper
ms.date: 11/13/2020
ms.topic: how-to
ms.prod: dotnet
ms.openlocfilehash: 4da558e2cdfc283d21f2a5497cb71dc746109614
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96594127"
---
# <a name="deploy-net-apps-to-raspberry-pi"></a><span data-ttu-id="fe390-103">Raspberry Pi への .NET アプリのデプロイ</span><span class="sxs-lookup"><span data-stu-id="fe390-103">Deploy .NET apps to Raspberry Pi</span></span>

<span data-ttu-id="fe390-104">Raspberry Pi への .NET アプリのデプロイは、他のプラットフォームと同じです。</span><span class="sxs-lookup"><span data-stu-id="fe390-104">Deployment of .NET apps to Raspberry Pi is identical to that of any other platform.</span></span> <span data-ttu-id="fe390-105">アプリは、 *自己完結* 型または *フレームワーク依存の* 配置モードとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="fe390-105">Your app can run as *self-contained* or *framework-dependent* deployment modes.</span></span> <span data-ttu-id="fe390-106">各方法には利点があります。</span><span class="sxs-lookup"><span data-stu-id="fe390-106">There are advantages to each strategy.</span></span> <span data-ttu-id="fe390-107">詳細については、「 [.net アプリケーションの公開の概要](../core/deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe390-107">For more information, see [.NET application publishing overview](../core/deploying/index.md).</span></span>

## <a name="deploying-a-framework-dependent-app"></a><span data-ttu-id="fe390-108">フレームワークに依存するアプリの配置</span><span class="sxs-lookup"><span data-stu-id="fe390-108">Deploying a framework-dependent app</span></span>

<span data-ttu-id="fe390-109">アプリをフレームワークに依存するアプリとしてデプロイするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-109">To deploy your app as a framework-dependent app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="fe390-110">[Dotnet スクリプト](../core/tools/dotnet-install-script.md)を使用して、Raspberry Pi に .net をインストールします。</span><span class="sxs-lookup"><span data-stu-id="fe390-110">Install .NET on the Raspberry Pi using the [dotnet-install scripts](../core/tools/dotnet-install-script.md).</span></span> <span data-ttu-id="fe390-111">Raspberry Pi (ローカルまたは SSH) で Bash プロンプトから次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-111">Complete the following steps from a Bash prompt on the Raspberry Pi (local or SSH):</span></span>
    1. <span data-ttu-id="fe390-112">次のコマンドを実行して .NET をインストールします。</span><span class="sxs-lookup"><span data-stu-id="fe390-112">Run the following command to install .NET:</span></span>

        ```bash
        curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin
        ```

        > [!NOTE]
        > <span data-ttu-id="fe390-113">これにより、最新バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fe390-113">This installs the latest version.</span></span> <span data-ttu-id="fe390-114">特定のバージョンが必要な場合は、を `--version <VERSION>` 末尾に追加します。ここで、 `<VERSION>` は特定のビルドバージョンです。</span><span class="sxs-lookup"><span data-stu-id="fe390-114">If you need a specific version, add `--version <VERSION>` to the end, where `<VERSION>` is the specific build version.</span></span>

    1. <span data-ttu-id="fe390-115">パスの解決を簡単にするには、 `DOTNET_ROOT` 次のコマンドを使用して、環境変数を追加し、 *dotnet* ディレクトリをに追加します。 `$PATH`</span><span class="sxs-lookup"><span data-stu-id="fe390-115">To simplify path resolution, add a `DOTNET_ROOT` environment variable and add the *.dotnet* directory to `$PATH` with the following commands:</span></span>

        ```bash
        echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
        echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
        source ~/.bashrc
        ```

    1. <span data-ttu-id="fe390-116">次のコマンドを使用して、.NET インストールを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe390-116">Verify the .NET installation with the following command:</span></span>

        ```dotnetcli
        dotnet --version
        ```

        <span data-ttu-id="fe390-117">表示されているバージョンが、インストールしたバージョンと一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe390-117">Verify the displayed version matches the version you installed.</span></span>

1. <span data-ttu-id="fe390-118">開発環境に応じて、次のようにして、開発用コンピューターにアプリを発行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-118">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="fe390-119">**Visual Studio** を使用している場合は、[アプリケーションをローカルフォルダーに配置](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)します。</span><span class="sxs-lookup"><span data-stu-id="fe390-119">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="fe390-120">発行する前に、発行プロファイルの概要で [ **編集** ] を選択し、[ **設定** ] タブを選択します。 **配置モード** が *フレームワークに依存* し、 **ターゲットランタイム** が *ポータブル* に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe390-120">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Framework-dependent* and **Target runtime** is set to *Portable*.</span></span>
    - <span data-ttu-id="fe390-121">**.NET CLI** を使用している場合は、 [dotnet publish](../core/tools/dotnet-publish.md)コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fe390-121">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="fe390-122">追加の引数は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="fe390-122">No additional arguments are required.</span></span>

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="fe390-123">Raspberry Pi (ローカルまたは SSH) の Bash プロンプトから、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-123">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="fe390-124">これを行うには、配置フォルダーを現在のディレクトリとして設定し、次のコマンドを実行します ( *HelloWorld.dll* はアプリのエントリポイントです)。</span><span class="sxs-lookup"><span data-stu-id="fe390-124">To do this, set the deployment folder as the current directory and execute the following command (where *HelloWorld.dll* is the entry point of the app):</span></span>

    ```dotnetcli
    dotnet HelloWorld.dll
    ```

## <a name="deploying-a-self-contained-app"></a><span data-ttu-id="fe390-125">自己完結型アプリの展開</span><span class="sxs-lookup"><span data-stu-id="fe390-125">Deploying a self-contained app</span></span>

<span data-ttu-id="fe390-126">自己完結型アプリとしてアプリをデプロイするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-126">To deploy your app as a self-contained app, complete the following steps:</span></span>

1. [!INCLUDE [ensure-ssh](includes/ensure-ssh.md)]

1. <span data-ttu-id="fe390-127">開発環境に応じて、次のようにして、開発用コンピューターにアプリを発行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-127">Publish the app on the development computer as follows, depending on development environment.</span></span>
    - <span data-ttu-id="fe390-128">**Visual Studio** を使用している場合は、[アプリケーションをローカルフォルダーに配置](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019)します。</span><span class="sxs-lookup"><span data-stu-id="fe390-128">If using **Visual Studio**, [deploy the app to a local folder](/visualstudio/deployment/quickstart-deploy-to-local-folder?view=vs-2019).</span></span> <span data-ttu-id="fe390-129">発行する前に、発行プロファイルの概要で [ **編集** ] を選択し、[ **設定** ] タブを選択します。 **配置モード** が " *自己完結型* " に設定されており、 **ターゲットランタイム** が " *linux-arm*" に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fe390-129">Before publishing, select **Edit** in the publish profile summary and select the **Settings** tab. Ensure that **Deployment mode** is set to *Self-contained* and **Target runtime** is set to *linux-arm*.</span></span>
    - <span data-ttu-id="fe390-130">**.NET CLI** を使用している場合は、次の引数を指定して [dotnet publish](../core/tools/dotnet-publish.md)コマンドを使用し `-r linux-arm` ます。</span><span class="sxs-lookup"><span data-stu-id="fe390-130">If using the **.NET CLI**, use the [dotnet publish](../core/tools/dotnet-publish.md) command with the `-r linux-arm` argument:</span></span>

        ```dotnetcli
        dotnet publish -r linux-arm
        ```

1. [!INCLUDE [sftp-client](includes/sftp-client.md)]

1. <span data-ttu-id="fe390-131">Raspberry Pi (ローカルまたは SSH) の Bash プロンプトから、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-131">From a Bash prompt on the Raspberry Pi (local or SSH), run the app.</span></span> <span data-ttu-id="fe390-132">これを行うには、現在のディレクトリを配置場所に設定し、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-132">To do this, set the current directory to the deployment location and complete the following steps:</span></span>
    1. <span data-ttu-id="fe390-133">実行可能ファイルの *実行* アクセス許可を指定し `HelloWorld` ます (は実行可能ファイルの名前です)。</span><span class="sxs-lookup"><span data-stu-id="fe390-133">Give the executable *execute* permission (where `HelloWorld` is the executable file name).</span></span>

        ```bash
        chmod +x HelloWorld
        ```

    1. <span data-ttu-id="fe390-134">実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="fe390-134">Run the executable.</span></span>

        ```bash
        ./HelloWorld
        ```
