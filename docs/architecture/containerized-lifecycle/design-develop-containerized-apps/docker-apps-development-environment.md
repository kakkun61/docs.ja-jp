---
title: Docker アプリの開発環境
description: Docker 開発ライフサイクルをサポートする最も重要な開発ツールのオプションについて説明します。
ms.date: 01/06/2021
ms.openlocfilehash: c6c4a1fda41131c00ba87808ed408f1d3250cabf
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970526"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="53c95-103">Docker アプリの開発環境</span><span class="sxs-lookup"><span data-stu-id="53c95-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="53c95-104">開発ツールの選択:IDE またはエディター</span><span class="sxs-lookup"><span data-stu-id="53c95-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="53c95-105">完全で強力な IDE または軽量でアジャイルなエディターのどちらを選んでも、Microsoft は Docker アプリケーションの開発時に対応できます。</span><span class="sxs-lookup"><span data-stu-id="53c95-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="53c95-106">Visual Studio Code と Docker CLI (Mac、Linux および Windows 用のクロスプラットフォーム ツール)</span><span class="sxs-lookup"><span data-stu-id="53c95-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="53c95-107">任意の開発言語をサポートする軽量なクロスプラットフォーム エディターを選択すると、Visual Studio Code と Docker CLI を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="53c95-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="53c95-108">これらの製品は、シンプルかつ堅牢性の高いエクスペリエンスを提供しますが、このことは開発者のワークフローを効率化するために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="53c95-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="53c95-109">Docker 開発者は、"Docker for Mac" または "Docker for Windows" (開発環境) をインストールすることで、1 つの Docker CLI を使用して Windows と Linux (実行時環境) 用の両方のアプリを構築することができます。</span><span class="sxs-lookup"><span data-stu-id="53c95-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="53c95-110">さらに、Visual Studio Code は、Dockerfile 用の IntelliSense を含む Docker の拡張機能や、エディターから Docker コマンドを実行するショートカット タスクをサポートします。</span><span class="sxs-lookup"><span data-stu-id="53c95-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="53c95-111">Visual Studio Code をダウンロードするには <https://code.visualstudio.com/download> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53c95-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>
>
> <span data-ttu-id="53c95-112">Mac および Windows 用 Docker をダウンロードするには <https://www.docker.com/products/docker> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53c95-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a><span data-ttu-id="53c95-113">Docker ツールを備えた Visual Studio (Windows の開発用コンピューター)</span><span class="sxs-lookup"><span data-stu-id="53c95-113">Visual Studio with Docker Tools (Windows development machine)</span></span>

<span data-ttu-id="53c95-114">組み込みの Docker ツールが有効にされた Visual Studio 2019 を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="53c95-114">It's recommend that you use Visual Studio 2019 with the built-in Docker Tools enabled.</span></span> <span data-ttu-id="53c95-115">Visual Studio により、選択した Docker 環境で、直接アプリケーションの開発、実行、および検証ができます。</span><span class="sxs-lookup"><span data-stu-id="53c95-115">With Visual Studio, you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="53c95-116">F5 キーを押すと、Docker ホスト内で直接アプリケーション (1 つのコンテナー、または複数のコンテナー) をデバッグできます。または、Ctrl キーを押しながら F5 キーを押すと、コンテナーを再構築しなくても、アプリケーションを編集して更新できます。</span><span class="sxs-lookup"><span data-stu-id="53c95-116">Press F5 to debug your application (single container or multiple containers) directly in a Docker host, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="53c95-117">これは、Linux または Windows の Docker コンテナーを作成する Windows 開発者にとって最も簡単で最も強力な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="53c95-117">It's the simplest and most powerful choice for Windows developers to create Docker containers for Linux or Windows.</span></span>

### <a name="visual-studio-for-mac-mac-development-machine"></a><span data-ttu-id="53c95-118">Visual Studio for Mac (Mac の開発用コンピューター)</span><span class="sxs-lookup"><span data-stu-id="53c95-118">Visual Studio for Mac (Mac development machine)</span></span>

<span data-ttu-id="53c95-119">Docker ベースのアプリケーションを開発するときに、[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="53c95-119">You can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) when developing Docker-based applications.</span></span> <span data-ttu-id="53c95-120">Visual Studio for Mac は、Visual Studio Code for Mac と比較した場合、より豊富な IDE を備えています。</span><span class="sxs-lookup"><span data-stu-id="53c95-120">Visual Studio for Mac offers a richer IDE when compared to Visual Studio Code for Mac.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="53c95-121">言語とフレームワークの選択肢</span><span class="sxs-lookup"><span data-stu-id="53c95-121">Language and framework choices</span></span>

<span data-ttu-id="53c95-122">最新の言語で Microsoft のツールを使用して Docker アプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="53c95-122">You can develop Docker applications using Microsoft tools with most modern languages.</span></span> <span data-ttu-id="53c95-123">次が初期一覧ですが、これに限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="53c95-123">The following is an initial list, but you're not limited to it:</span></span>

- <span data-ttu-id="53c95-124">.NET と ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="53c95-124">.NET and ASP.NET Core</span></span>
- <span data-ttu-id="53c95-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="53c95-125">Node.js</span></span>
- <span data-ttu-id="53c95-126">移動</span><span class="sxs-lookup"><span data-stu-id="53c95-126">Go</span></span>
- <span data-ttu-id="53c95-127">Java</span><span class="sxs-lookup"><span data-stu-id="53c95-127">Java</span></span>
- <span data-ttu-id="53c95-128">Ruby</span><span class="sxs-lookup"><span data-stu-id="53c95-128">Ruby</span></span>
- <span data-ttu-id="53c95-129">Python</span><span class="sxs-lookup"><span data-stu-id="53c95-129">Python</span></span>

<span data-ttu-id="53c95-130">基本的に、Linux または Windows で Docker によってサポートされている任意の最新の言語を使用できます。</span><span class="sxs-lookup"><span data-stu-id="53c95-130">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="53c95-131">[前へ](deploy-azure-kubernetes-service.md)
>[次へ](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="53c95-131">[Previous](deploy-azure-kubernetes-service.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>
