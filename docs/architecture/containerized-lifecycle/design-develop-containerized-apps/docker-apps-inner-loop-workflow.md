---
title: Docker アプリの内部ループ開発ワークフロー
description: Docker アプリケーションの "内部ループ" 開発ワークフローについて説明します。
ms.date: 01/06/2021
ms.openlocfilehash: 78c593890d56a6888d4c4ea6752497918222ebee
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970586"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="46ce3-103">Docker アプリの内部ループ開発ワークフロー</span><span class="sxs-lookup"><span data-stu-id="46ce3-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="46ce3-104">DevOps サイクル全体にまたがる外部ループ ワークフローをトリガーする前に、各内部ループが各開発者のコンピューターで開始され、アプリ自体をコード化し、希望する言語またはプラットフォームを使用し、ローカルでテストされます (図 4-21)。</span><span class="sxs-lookup"><span data-stu-id="46ce3-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="46ce3-105">ただし、すべての場合において、選択する言語、フレームワーク、プラットフォームに関係なく、共通する重要な点が 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="46ce3-106">この特定のワークフローでは、Docker コンテナーを開発し、テストしますが、常に他の環境ではなくローカルで行います。</span><span class="sxs-lookup"><span data-stu-id="46ce3-106">In this specific workflow, you're always developing and testing Docker containers in no other environments, but locally.</span></span>

![内部ループ開発環境の概念を示す図。](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="46ce3-108">**図 4-21**</span><span class="sxs-lookup"><span data-stu-id="46ce3-108">**Figure 4-21**.</span></span> <span data-ttu-id="46ce3-109">内部ループの開発コンテキスト</span><span class="sxs-lookup"><span data-stu-id="46ce3-109">Inner-loop development context</span></span>

<span data-ttu-id="46ce3-110">Docker イメージのコンテナーまたはインスタンスには、以下のコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="46ce3-111">選択したオペレーティング システム (Linux ディストリビューションや Windows など)</span><span class="sxs-lookup"><span data-stu-id="46ce3-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="46ce3-112">開発者が追加したファイル (アプリのバイナリなど)</span><span class="sxs-lookup"><span data-stu-id="46ce3-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="46ce3-113">構成 (環境の設定や依存関係など)</span><span class="sxs-lookup"><span data-stu-id="46ce3-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="46ce3-114">Docker でどのプロセスを実行するかに関する指示</span><span class="sxs-lookup"><span data-stu-id="46ce3-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="46ce3-115">Docker をプロセスとして活用する内部ループ開発ワークフローを設定できます (詳細は次のセクションにあります)。</span><span class="sxs-lookup"><span data-stu-id="46ce3-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="46ce3-116">環境設定の初回手順は含まれていません。それは一度だけ実行すれば良いからです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="46ce3-117">Visual Studio Code と Docker CLI を使用し、Docker コンテナー内で 1 つのアプリをビルドする</span><span class="sxs-lookup"><span data-stu-id="46ce3-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="46ce3-118">アプリは自分のサービスと追加のライブラリ (依存関係) から構成されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="46ce3-119">図 4-22 では、Docker アプリをビルドするときに通常行う基本手順と各手順の詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![コンテナー化されたアプリを作成するために必要な 7 つの手順を示す図。](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="46ce3-121">**図 4-22**</span><span class="sxs-lookup"><span data-stu-id="46ce3-121">**Figure 4-22**.</span></span> <span data-ttu-id="46ce3-122">Docker CLI を利用し、Docker でコンテナー化されたアプリケーションのワークフローの概要</span><span class="sxs-lookup"><span data-stu-id="46ce3-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="46ce3-123">手順 1: Visual Studio Code でコーディングを開始し、初回アプリ/サービス ベースラインを作成する</span><span class="sxs-lookup"><span data-stu-id="46ce3-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="46ce3-124">アプリケーションの開発方法は、Docker を使用しない場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="46ce3-125">違いは、開発中、ローカル環境 (Linux VM や Windows など) に配置されている Docker コンテナー内で実行されているアプリケーションやサービスを展開し、テストするということです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="46ce3-126">**ローカル環境を設定する**</span><span class="sxs-lookup"><span data-stu-id="46ce3-126">**Setting up your local environment**</span></span>

<span data-ttu-id="46ce3-127">Mac または Windows 向けの最新版 Docker Desktop を使用すると、Docker アプリケーションをもっと簡単に開発できます。設定も簡単です。</span><span class="sxs-lookup"><span data-stu-id="46ce3-127">With the latest versions of Docker Desktop for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="46ce3-128">Docker Desktop for Windows の設定方法については、<https://docs.docker.com/docker-for-windows/> にお進みください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-128">For instructions on setting up Docker Desktop for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
> <span data-ttu-id="46ce3-129">Docker Desktop for Mac の設定方法については、<https://docs.docker.com/docker-for-mac/> にお進みください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-129">For instructions on setting up Docker Desktop for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="46ce3-130">また、Docker CLI の使用時、実際にアプリケーションを開発できるよう、コード エディターが必要です。</span><span class="sxs-lookup"><span data-stu-id="46ce3-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="46ce3-131">Microsoft からは Visual Studio Code が提供されます。これは Windows、Linux、macOS でサポートされている軽量のコード エディターであり、IntelliSense、[さまざまな言語のサポート](https://code.visualstudio.com/docs/languages/overview) (JavaScript、.NET、Go、Java、Ruby、Python、ほとんどの新しい言語)、[デバッグ](https://code.visualstudio.com/Docs/editor/debugging)、[Git との統合](https://code.visualstudio.com/Docs/editor/versioncontrol)、[拡張機能サポート](https://code.visualstudio.com/docs/extensions/overview)を提供します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="46ce3-132">このエディターは、macOS および Linux の開発者に最適です。</span><span class="sxs-lookup"><span data-stu-id="46ce3-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="46ce3-133">Windows では、Visual Studio を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="46ce3-134">Windows、Linux、または macOS 用の Visual Studio Code をインストールする手順については、「<https://code.visualstudio.com/docs/setup/setup-overview/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="46ce3-135">Docker for Mac の設定方法については、<https://docs.docker.com/docker-for-mac/> にお進みください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="46ce3-136">Docker CLI を使用して、あらゆるコード エディターでコードを記述できますが、Docker 拡張機能と共に Visual Studio Code を使用すると、ワークスペースで `Dockerfile` ファイルや `docker-compose.yml` ファイルを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="46ce3-137">Visual Studio Code IDE からタスクやスクリプトを実行し、下部の Docker CLI を使用して Docker コマンドを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="46ce3-138">VS Code 用 Docker 拡張機能からは次の機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="46ce3-139">`Dockerfile` および `docker-compose.yml` ファイルの自動生成</span><span class="sxs-lookup"><span data-stu-id="46ce3-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="46ce3-140">`docker-compose.yml` および `Dockerfile` ファイルの構文強調表示とツールチップ</span><span class="sxs-lookup"><span data-stu-id="46ce3-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="46ce3-141">`Dockerfile` および `docker-compose.yml` ファイルの IntelliSense (入力候補)</span><span class="sxs-lookup"><span data-stu-id="46ce3-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="46ce3-142">`Dockerfile` ファイルの Lint 処理 (エラーと警告)</span><span class="sxs-lookup"><span data-stu-id="46ce3-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="46ce3-143">最も一般的な Docker コマンドのコマンド パレット (F1) 統合</span><span class="sxs-lookup"><span data-stu-id="46ce3-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="46ce3-144">イメージとコンテナーを管理するためのエクスプローラー統合</span><span class="sxs-lookup"><span data-stu-id="46ce3-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="46ce3-145">DockerHub と Azure Container Registry から Azure App Service へのイメージのデプロイ</span><span class="sxs-lookup"><span data-stu-id="46ce3-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="46ce3-146">Docker 拡張機能をインストールするには、Ctrl + Shift + P キーを押しながら、「`ext install`」と入力し、Install Extension コマンドを実行して Marketplace 拡張機能一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="46ce3-147">次に、図 4-23 のように、「**docker**」と入力して結果にフィルターを適用し、Docker Support 拡張機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![VS Code 用 Docker 拡張機能の表示。](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="46ce3-149">**図 4-23**. </span><span class="sxs-lookup"><span data-stu-id="46ce3-149">**Figure 4-23**.</span></span> <span data-ttu-id="46ce3-150">Visual Studio Code で Docker 拡張機能をインストールする</span><span class="sxs-lookup"><span data-stu-id="46ce3-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-nodejs-and-ruby"></a><span data-ttu-id="46ce3-151">手順 2: 既存のイメージ (プレーンな OS か、.NET、Node.js、Ruby などの開発環境) に関連する DockerFile を作成する</span><span class="sxs-lookup"><span data-stu-id="46ce3-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET, Node.js, and Ruby)</span></span>

<span data-ttu-id="46ce3-152">ビルドするカスタム イメージごとと、展開するコンテナーごとに `DockerFile` が必要になります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="46ce3-153">アプリが 1 つのカスタム サービスで構成される場合、`DockerFile` が 1 つ必要になります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-153">If your app is made up of single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="46ce3-154">ただし、(マイクロサービス アーキテクチャの場合のように) アプリが複数のサービスで構成される場合、サービスごとに `Dockerfile` が 1 つ必要になります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="46ce3-155">`DockerFile` は通常、アプリまたはサービスのルート フォルダーに配置され、そのアプリまたはサービスを設定し、実行する方法を Docker に認識させるための必須のコマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="46ce3-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="46ce3-156">`DockerFile` を作成し、コード (node.js や .NET など) とともにプロジェクトに追加できます。この環境が初めての場合、次のヒントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="46ce3-157">Docker コンテナーに関連する `Dockerfile` および `docker-compose.yml` ファイルを使用するとき、Docker 拡張機能を利用してガイドを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="46ce3-158">最終的には、このツールなしでこの種類のファイルを記述することになるでしょうが、Docker 拡張機能の使用は学習曲線を加速するので、開始点として推奨されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="46ce3-159">図 4-24 で、VS Code 用の Docker 拡張機能を使用して Docker ファイルをプロジェクトに追加する手順を確認できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-159">In Figure 4-24, you can see the steps to add the docker files to a project by using the Docker Extension for VS Code:</span></span>

1. <span data-ttu-id="46ce3-160">コマンド パレットを開き、「**docker**」と入力してから、"**Add Docker Files to Workspace**" を選択します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-160">Open the command palette, type "**docker**" and select "**Add Docker Files to Workspace**".</span></span>
2. <span data-ttu-id="46ce3-161">アプリケーション プラットフォーム (ASP.NET Core) の選択</span><span class="sxs-lookup"><span data-stu-id="46ce3-161">Select Application Platform (ASP.NET Core)</span></span>
3. <span data-ttu-id="46ce3-162">オペレーティング システム (Linux) の選択</span><span class="sxs-lookup"><span data-stu-id="46ce3-162">Select Operating System (Linux)</span></span>
4. <span data-ttu-id="46ce3-163">オプションの Docker Compose ファイルを含める</span><span class="sxs-lookup"><span data-stu-id="46ce3-163">Include optional Docker Compose files</span></span>
5. <span data-ttu-id="46ce3-164">公開するポート (80、443) を入力</span><span class="sxs-lookup"><span data-stu-id="46ce3-164">Enter ports to publish (80, 443)</span></span>
6. <span data-ttu-id="46ce3-165">プロジェクトを選択する</span><span class="sxs-lookup"><span data-stu-id="46ce3-165">Select the project</span></span>

![Docker 拡張機能を使用して Docker ファイルを追加する手順](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="46ce3-167">**図 4-24**</span><span class="sxs-lookup"><span data-stu-id="46ce3-167">**Figure 4-24**.</span></span> <span data-ttu-id="46ce3-168">**Add Docker files to Workspace** コマンドで追加された Docker ファイル</span><span class="sxs-lookup"><span data-stu-id="46ce3-168">Docker files added using the **Add Docker files to Workspace** command</span></span>

<span data-ttu-id="46ce3-169">DockerFile を追加するとき、(`FROM mcr.microsoft.com/dotnet/aspnet` を使用するなどして) 使用する基本の Docker イメージを指定します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-169">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/aspnet`).</span></span> <span data-ttu-id="46ce3-170">通常、[Docker Hub レジストリ](https://hub.docker.com/)にある公式リポジトリから得られる基本イメージ ([.NET 用のイメージ](https://hub.docker.com/_/microsoft-dotnet/)や [Node.js 用のイメージ](https://hub.docker.com/_/node/)など) を基礎にしてカスタム イメージをビルドします。</span><span class="sxs-lookup"><span data-stu-id="46ce3-170">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET](https://hub.docker.com/_/microsoft-dotnet/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

> [!TIP]
> <span data-ttu-id="46ce3-171">アプリケーション内のすべてのプロジェクトに対してこの手順を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-171">You'll have to repeat this procedure for every project in your application.</span></span> <span data-ttu-id="46ce3-172">ただし、拡張機能によって、2 回目以降は生成された docker-compose ファイルを上書きするように求められます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-172">However, the extension will ask to overwrite the generated docker-compose file after the first time.</span></span> <span data-ttu-id="46ce3-173">それを上書きしないように応答する必要があります。そうすると拡張機能によって個別の docker-compose ファイルが作成され、docker-compose を実行する前に手動でマージできます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-173">You should reply to not overwrite it, so the extension creates separate docker-compose files, that you can then merge by hand, prior to running docker-compose.</span></span>

<span data-ttu-id="46ce3-174">**_既存の公式 Docker イメージを使用する_**</span><span class="sxs-lookup"><span data-stu-id="46ce3-174">**_Use an existing official Docker image_**</span></span>

<span data-ttu-id="46ce3-175">バージョン番号を持つ言語スタックの公式イメージ リポジトリを使うと、同じ言語機能が (開発、テスト、運用環境など) すべてのコンピューターで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-175">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="46ce3-176">次は .NET コンテナー向けサンプル DockerFile です。</span><span class="sxs-lookup"><span data-stu-id="46ce3-176">The following is a sample DockerFile for a .NET container:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

<span data-ttu-id="46ce3-177">この場合、イメージは、`FROM mcr.microsoft.com/dotnet/aspnet:5.0` の行から、公式の ASP.NET Core Docker イメージ (Linux および Windows 用マルチアーキテクチャ) のバージョン 5.0 に基づいています</span><span class="sxs-lookup"><span data-stu-id="46ce3-177">In this case, the image is based on version 5.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/aspnet:5.0`.</span></span> <span data-ttu-id="46ce3-178">(このトピックの詳細については、[ASP.NET Core Docker イメージ](https://hub.docker.com/_/microsoft-dotnet-aspnet/)に関するページと [.NET Docker イメージ](https://hub.docker.com/_/microsoft-dotnet/)に関するページを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="46ce3-178">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-aspnet/) page and the [.NET Docker Image](https://hub.docker.com/_/microsoft-dotnet/) page).</span></span>

<span data-ttu-id="46ce3-179">DockerFile では、実行時に使用する TCP ポートをリッスンするように Docker に指示することもできます (ポート 80 や 443 など)。</span><span class="sxs-lookup"><span data-stu-id="46ce3-179">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80 or 443).</span></span>

<span data-ttu-id="46ce3-180">使用している言語とフレームワークによっては、Dockerfile に別の構成設定を指定できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="46ce3-181">たとえば、`["dotnet", "WebMvcApplication.dll"]` を含む `ENTRYPOINT` 行では、.NET アプリケーションを実行するように Docker に指示します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-181">For instance, the `ENTRYPOINT` line with `["dotnet", "WebMvcApplication.dll"]` tells Docker to run a .NET application.</span></span> <span data-ttu-id="46ce3-182">SDK と .NET CLI (`dotnet CLI`) を使用して .NET アプリケーションをビルドし、実行する場合、この設定は異なるものになります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-182">If you're using the SDK and the .NET CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="46ce3-183">ここで重要なことは、ENTRYPOINT 行とその他の設定はアプリケーションに選択した言語とプラットフォームに依存するということです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-183">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="46ce3-184">.NET アプリケーション向け Docker イメージのビルド方法については、<https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images> にお進みください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-184">For more information about building Docker images for .NET applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="46ce3-185">独自のイメージをビルドする方法については、<https://docs.docker.com/engine/tutorials/dockerimages/> にお進みください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-185">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="46ce3-186">**マルチアーキテクチャ イメージ リポジトリを使用する**</span><span class="sxs-lookup"><span data-stu-id="46ce3-186">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="46ce3-187">リポジトリの単一のイメージ名には、Linux イメージや Windows イメージなどのプラットフォーム バリアントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-187">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="46ce3-188">この機能では、Microsoft (基本イメージの作成者) などのベンダーが、複数のプラットフォーム (つまり、Linux および Windows) に対応できるリポジトリを 1 つ作成できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-188">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="46ce3-189">たとえば、Docker Hub レジストリにある [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) リポジトリでは、同じイメージ名を使用して Linux および Windows Nano Server をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="46ce3-189">For example, the [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="46ce3-190">Windows ホストから [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) イメージをプルした場合、Windows バリアントがプルされ、同じイメージ名が Linux ホストからプルされた場合、Linux バリアントがプルされます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-190">Pulling the [dotnet/aspnet](https://hub.docker.com/_/microsoft-dotnet-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="46ce3-191">**_基本イメージを一から作成する_**</span><span class="sxs-lookup"><span data-stu-id="46ce3-191">**_Create your base image from scratch_**</span></span>

<span data-ttu-id="46ce3-192">Docker の[この記事](https://docs.docker.com/engine/userguide/eng-image/baseimages/)で説明されているように、独自の Docker 基本イメージを一から作成できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-192">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="46ce3-193">Docker を初めて使用するユーザーにはおそらく推奨されませんが、独自の基本イメージを設定するならそれは可能です。</span><span class="sxs-lookup"><span data-stu-id="46ce3-193">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="46ce3-194">手順 3: カスタム Docker イメージを作成し、それにサービスを埋め込む</span><span class="sxs-lookup"><span data-stu-id="46ce3-194">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="46ce3-195">アプリを構成するカスタム サービスごとに、関連イメージを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-195">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="46ce3-196">アプリが 1 つのサービスまたは Web アプリで構成されている場合、イメージは 1 つのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="46ce3-196">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="46ce3-197">"外部ループ DevOps ワークフロー" を考慮すると、イメージがソース コードからそのグローバル環境で作成されるよう、ソース コードを Git リポジトリにプッシュするたびに (継続的インテグレーション)、自動化されたビルド プロセスによってイメージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-197">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="46ce3-198">ただし、その外部ループ ルートへの移行を検討する前に、Docker アプリケーションが実際に適切に動作していることを確保して、ソース管理システム (Git など) に、適切に機能しない可能性のあるコードがプッシュされないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-198">But before you consider going to that outer-loop route, you need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="46ce3-199">そのため、各開発者はまず、内部ループ プロセス全体を行ってローカル テストし、それから、完全な機能または変更をソース コントロール システムにプッシュするまで開発を続けます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-199">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="46ce3-200">ローカル環境で DockerFile を使用してイメージを作成するには、図 4-25 に示すように、docker build コマンドを使用します。あらかじめイメージにタグが付けられていて、簡単なコマンドでアプリケーション内のすべてのサービスのイメージをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-200">To create an image in your local environment and using the DockerFile, you can use the docker build command, as shown in Figure 4-25, because it already tags the image for you and builds the images for all services in the application with a simple command.</span></span>

![docker-compose build コマンドのコンソール出力を示すスクリーンショット。](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="46ce3-202">**図 4-25**</span><span class="sxs-lookup"><span data-stu-id="46ce3-202">**Figure 4-25**.</span></span> <span data-ttu-id="46ce3-203">docker build の実行</span><span class="sxs-lookup"><span data-stu-id="46ce3-203">Running docker build</span></span>

<span data-ttu-id="46ce3-204">任意で、プロジェクト フォルダーから `docker build` を直接実行する代わりに、`dotnet publish` 実行コマンドを使用し、それから `docker build` を実行することで、まず、必要な .NET ライブラリで展開可能なフォルダーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-204">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="46ce3-205">この例では、`webapi:latest` という名前で Docker イメージが作成されます (`:latest` は特定のバージョンのようなタグです)。</span><span class="sxs-lookup"><span data-stu-id="46ce3-205">This example creates a Docker image with the name `webapi:latest` (`:latest` is a tag, like a specific version).</span></span> <span data-ttu-id="46ce3-206">いくつかのコンテナーで作成した Docker アプリケーション用に作成する必要のあるカスタム イメージごとにこの手順を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-206">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span> <span data-ttu-id="46ce3-207">一方で、次のセクションでは、`docker-compose` を使用してこれをもっと簡単に行う方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-207">However, we'll see in the next section that it's easier to do this using `docker-compose`.</span></span>

<span data-ttu-id="46ce3-208">図 4-26 に示すように、`docker images` コマンドを使用して、ローカル リポジトリ (開発コンピューター) の既存のイメージを検索できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-208">You can find the existing images in your local repository (your development machine) by using the `docker images` command, as illustrated in Figure 4-26.</span></span>

![コマンド docker イメージからのコンソール出力。既存のイメージを確認できます。](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="46ce3-210">**図 4-26**</span><span class="sxs-lookup"><span data-stu-id="46ce3-210">**Figure 4-26**.</span></span> <span data-ttu-id="46ce3-211">docker images を使用した既存のイメージの表示</span><span class="sxs-lookup"><span data-stu-id="46ce3-211">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="46ce3-212">手順 4: 複数のサービスで Docker アプリケーションを構築するときに docker-compose.yml でサービスを定義する</span><span class="sxs-lookup"><span data-stu-id="46ce3-212">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="46ce3-213">`docker-compose.yml` ファイルを利用すると、次のセクションで説明するように、展開コマンドで構成済みアプリケーションとして展開する一連の関連サービスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-213">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="46ce3-214">メインまたはルート ソリューション フォルダーでそのファイルを作成します。この `docker-compose.yml` ファイルで確認できるものと同様のコンテンツが含まれているはずです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-214">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

<span data-ttu-id="46ce3-215">この特定のケースでは、このファイルにより、Web API サービス (カスタム サービス)、Web アプリケーション、Redis サービス (人気のキャッシュ サービス) という 3 つのサービスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-215">In this particular case, this file defines three services: the web API service (your custom service), a web application, and the Redis service (a popular cache service).</span></span> <span data-ttu-id="46ce3-216">各サービスはコンテナーとして配置されます。そのため、それぞれに具体的な Docker イメージを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-216">Each service will be deployed as a container, so you need to use a concrete Docker image for each.</span></span> <span data-ttu-id="46ce3-217">この特定のアプリケーションの場合、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-217">For this particular application:</span></span>

- <span data-ttu-id="46ce3-218">Web API サービスは、`src/WebApi/Dockerfile` ディレクトリの DockerFile から構築されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-218">The web API service is built from the DockerFile in the `src/WebApi/Dockerfile` directory.</span></span>

- <span data-ttu-id="46ce3-219">ホスト ポート 51080 は、`webapi` コンテナーの公開されているポート 80 に転送されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-219">The host port 51080 is forwarded to the exposed port 80 on the `webapi` container.</span></span>

- <span data-ttu-id="46ce3-220">Web API サービスは Redis サービスに依存しています。</span><span class="sxs-lookup"><span data-stu-id="46ce3-220">The web API service depends on the Redis service</span></span>

- <span data-ttu-id="46ce3-221">Web アプリケーションから内部アドレス `http://webapi` を使用して Web API サービスにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="46ce3-221">The web application accesses the web API service using the internal address: `http://webapi`.</span></span>

- <span data-ttu-id="46ce3-222">Redis サービスによって、Docker Hub レジストリからプルされた[最新のパブリック redis イメージ](https://hub.docker.com/_/redis/)が使用されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-222">The Redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="46ce3-223">[Redis](https://redis.io/) はサーバー側アプリケーション用として人気があるキャッシュ システムです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-223">[Redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="46ce3-224">手順 5: Docker アプリをビルドし、実行する</span><span class="sxs-lookup"><span data-stu-id="46ce3-224">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="46ce3-225">アプリにコンテナーが 1 つしかない場合、必要な作業は Docker ホスト (VM または物理サーバー) にそれを展開して実行することだけになります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-225">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="46ce3-226">ただし、アプリが複数のサービスで構成されている場合、_それを作成する_ 必要もあります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-226">However, if your app is made up of multiple services, you need to _compose it_, too.</span></span> <span data-ttu-id="46ce3-227">別のオプションを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="46ce3-227">Let's see the different options.</span></span>

<span data-ttu-id="46ce3-228">**_オプション A:1 つのコンテナーまたはサービスを実行する_**</span><span class="sxs-lookup"><span data-stu-id="46ce3-228">**_Option A: Run a single container or service_**</span></span>

<span data-ttu-id="46ce3-229">次に示すように docker run コマンドを使用し、Docker イメージを実行できます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-229">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 50080:80 webapp:latest
```

<span data-ttu-id="46ce3-230">この特定の配置の場合、ホストのポート 50080 に送信された要求を内部ポート 80 にリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="46ce3-230">For this particular deployment, we'll be redirecting requests sent to port 50080 on the host to the internal port 80.</span></span>

<span data-ttu-id="46ce3-231">**_オプション B:複数コンテナー アプリケーションを作成し、実行する_**</span><span class="sxs-lookup"><span data-stu-id="46ce3-231">**_Option B: Compose and run a multiple-container application_**</span></span>

<span data-ttu-id="46ce3-232">ほとんどの企業のシナリオでは、Docker アプリケーションは複数のサービスから構成されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-232">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="46ce3-233">それらのケースでは、`docker-compose up` コマンド (図 4-27) を実行でき、先ほど作成した docker-compose.yml ファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-233">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you created previously.</span></span> <span data-ttu-id="46ce3-234">このコマンドを実行すると、すべてのカスタム イメージがビルドされ、作成されたアプリケーションがそのすべての関連コンテナーと共に配置されます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-234">Running this command builds all custom images and deploys the composed application with all of its related containers.</span></span>

![docker-compose up コマンドからのコンソール出力。](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="46ce3-236">**図 4-27**</span><span class="sxs-lookup"><span data-stu-id="46ce3-236">**Figure 4-27**.</span></span> <span data-ttu-id="46ce3-237">"docker-compose up" コマンドの実行結果</span><span class="sxs-lookup"><span data-stu-id="46ce3-237">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="46ce3-238">VM を表現する図 4-28 で示すように、`docker-compose up` の実行後、Docker ホストにアプリケーションとその関連コンテナーを展開します。</span><span class="sxs-lookup"><span data-stu-id="46ce3-238">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![マルチコンテナー アプリケーションを実行する VM](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="46ce3-240">**図 4-28**</span><span class="sxs-lookup"><span data-stu-id="46ce3-240">**Figure 4-28**.</span></span> <span data-ttu-id="46ce3-241">Docker コンテナーが展開された VM</span><span class="sxs-lookup"><span data-stu-id="46ce3-241">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="46ce3-242">手順 6: Docker アプリケーションをローカル テストする (ローカル、CD VM で)</span><span class="sxs-lookup"><span data-stu-id="46ce3-242">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="46ce3-243">この手順は、アプリで何が実行されているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="46ce3-243">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="46ce3-244">1 つのコンテナーまたはサービスとして展開される単純な .NET Web API "Hello World" の場合、DockerFile に指定されている TCP ポートを指定し、サービスにアクセスするだけです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-244">In a simple .NET Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="46ce3-245">Docker ホストでブラウザーを開き、そのサイトに移動します。図 4-29 に示すように、アプリ/サービスが実行中であることを確認できるはずです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-245">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![ブラウザーに表示される localhost/API/values からの応答](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="46ce3-247">**図 4-29**</span><span class="sxs-lookup"><span data-stu-id="46ce3-247">**Figure 4-29**.</span></span> <span data-ttu-id="46ce3-248">ブラウザーを使用して Docker アプリケーションをローカルでテストする</span><span class="sxs-lookup"><span data-stu-id="46ce3-248">Testing your Docker application locally by using the browser</span></span>

<span data-ttu-id="46ce3-249">ポート 50080 を使用していますが、内部ではポート 80 にリダイレクトされていることにご注意ください。これは、前に説明したように、`docker compose` でこのように配置されたためです。</span><span class="sxs-lookup"><span data-stu-id="46ce3-249">Note that it's using port 50080, but internally it's being redirected to port 80, because that's how it was deployed with `docker compose`, as explained earlier.</span></span>

<span data-ttu-id="46ce3-250">このテストは、図 4-30 に示すように、ターミナルから CURL を使用してブラウザーを使って行うことができます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-250">You can test this by using the browser using CURL from the terminal, as depicted in Figure 4-30.</span></span>

![http://localhost:51080/WeatherForecast から取得された CURL の結果](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="46ce3-252">**図 4-30**</span><span class="sxs-lookup"><span data-stu-id="46ce3-252">**Figure 4-30**.</span></span> <span data-ttu-id="46ce3-253">CURL を使用した Docker アプリケーションのローカル テスト</span><span class="sxs-lookup"><span data-stu-id="46ce3-253">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="46ce3-254">**Docker で実行されているコンテナーをデバッグする**</span><span class="sxs-lookup"><span data-stu-id="46ce3-254">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="46ce3-255">Visual Studio Code では、Node.js かその他のプラットフォーム (.NET コンテナーなど) を使用している場合、Docker をデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-255">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET containers.</span></span>

<span data-ttu-id="46ce3-256">次のセクションで説明するように、Windows または Mac 向けの Visual Studio の使用時、Docker で .NET または .NET Framework コンテナーをデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="46ce3-256">You also can debug .NET or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="46ce3-257">Node.js Docker コンテナーのデバッグの詳細については、<https://blog.docker.com/2016/07/live-debugging-docker/> と <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46ce3-257">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="46ce3-258">[前へ](docker-apps-development-environment.md)
> [次へ](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="46ce3-258">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
