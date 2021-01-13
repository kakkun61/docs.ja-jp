---
title: .NET を使用して Azure 開発用に Visual Studio Code を構成する
description: この記事は、VS Code で適切なプラグインをインストールして構成するなど、Azure 開発用に Visual Studio Code を構成するのに役立ちます
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700988"
---
# <a name="configure-visual-studio-code-for-azure-development"></a><span data-ttu-id="dc722-103">Azure 開発用に Visual Studio Code を構成する</span><span class="sxs-lookup"><span data-stu-id="dc722-103">Configure Visual Studio Code for Azure development</span></span>

<span data-ttu-id="dc722-104">.NET 開発のため、Angular、React、Vue などのフレームワークを使用したシングル ページ アプリケーションをビルドするため、または Python などの別の言語でのアプリケーションを作成するためかどうかに関係なく、Visual Studio Code を使用している場合は、Azure 開発用に Visual Studio Code を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc722-104">If you are using Visual Studio Code, whether for .NET development, for building single page applications using frameworks like Angular, React or Vue, or for writing applications in another language like Python, you will want to configure Visual Studio Code for Azure development.</span></span>

### <a name="download-visual-studio-code"></a><span data-ttu-id="dc722-105">Visual Studio Code をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="dc722-105">Download Visual Studio Code</span></span>

<span data-ttu-id="dc722-106">既に Visual Studio Code をインストールしている場合、この手順は省略できます</span><span class="sxs-lookup"><span data-stu-id="dc722-106">If you already have Visual Studio Code installed, you can skip this step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc722-107">Visual Studio Code をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="dc722-107">Download Visual Studio Code</span></span>](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a><span data-ttu-id="dc722-108">Azure Tools 拡張機能パックをインストールする</span><span class="sxs-lookup"><span data-stu-id="dc722-108">Install the Azure Tools Extension Pack</span></span>

<span data-ttu-id="dc722-109">[Azure Tools 拡張機能パック](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)は、Azure App Service、Azure Functions、Azure Storage、Cosmos DB、Azure Virtual Machines を使用するためのすべての拡張機能を 1 つの便利なパッケージに収めたものです。</span><span class="sxs-lookup"><span data-stu-id="dc722-109">The [Azure Tools Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) contains extensions for working with Azure App Service, Azure Functions, Azure Storage, Cosmos DB, and Azure Virtual Machines all in one convenient package.</span></span>

<span data-ttu-id="dc722-110">Visual Studio Code から拡張機能をインストールするには:</span><span class="sxs-lookup"><span data-stu-id="dc722-110">To install the extension from Visual Studio Code:</span></span>

1. <span data-ttu-id="dc722-111"><kbd>Ctrl + Shift + X</kbd> キーを押して、 **[拡張機能]** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="dc722-111">Press <kbd>Ctrl+Shift+X</kbd> to open the **Extensions** window.</span></span>
1. <span data-ttu-id="dc722-112">*Azure Tools* 拡張機能を検索します。</span><span class="sxs-lookup"><span data-stu-id="dc722-112">Search for the *Azure Tools* extension.</span></span>
1. <span data-ttu-id="dc722-113">**[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="dc722-113">Select the **Install** button.</span></span>

![Azure Tools 拡張機能パックを検索している拡張機能パネルを示している Visual Studio Code のスクリーンショット](./media/visual-studio-code-azure-tools.png)

<span data-ttu-id="dc722-115">Visual Studio Code に拡張機能をインストールする方法の詳細については、Visual Studio Code Web サイトの「[Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)」のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc722-115">To learn more about installing extensions in Visual Studio Code, refer to the [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) document on the Visual Studio Code website.</span></span>

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a><span data-ttu-id="dc722-116">Azure Tools を使用して Azure アカウントにサインインする</span><span class="sxs-lookup"><span data-stu-id="dc722-116">Sign in to your Azure account with Azure Tools</span></span>

<span data-ttu-id="dc722-117">左側のパネルに、Azure アイコンが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc722-117">On the left hand panel, you'll see an Azure icon.</span></span> <span data-ttu-id="dc722-118">このアイコンを選択すると、Azure サービスのコントロール パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dc722-118">Select this icon, and a control panel for Azure services will appear.</span></span> <span data-ttu-id="dc722-119">任意のサービスの下で **[Azure にサインイン]** を選択して、Visual Studio Code で Azure Tools の認証プロセスを完了します。</span><span class="sxs-lookup"><span data-stu-id="dc722-119">Choose **Sign in to Azure...** under any service to complete the authentication process for the Azure tools in Visual Studio Code.</span></span>

![Azure Tools を Azure にログインする方法を示している Visual Studio Code のスクリーンショット](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a><span data-ttu-id="dc722-121">次のステップ</span><span class="sxs-lookup"><span data-stu-id="dc722-121">Next steps</span></span>

<span data-ttu-id="dc722-122">次は、Azure CLI をワークステーションにインストールします。</span><span class="sxs-lookup"><span data-stu-id="dc722-122">Next, you will want to install the Azure CLI on your workstation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc722-123">Azure CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="dc722-123">Install the Azure CLI</span></span>](./install-azure-cli.md)
