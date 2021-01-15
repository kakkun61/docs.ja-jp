---
title: Azure CLI のインストール
description: Azure 開発者は Azure CLI をインストールする必要があるため、この記事では、CLI が必要な理由と、そのダウンロードとインストールの場所について説明します。
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: aa2739cc6c11145887e64921398c72affeaec729
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025030"
---
# <a name="install-the-azure-cli"></a><span data-ttu-id="b8cee-103">Azure CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="b8cee-103">Install the Azure CLI</span></span>

<span data-ttu-id="b8cee-104">Azure では、Azure portal に加えて、Azure リソースを作成して管理するためのコマンドライン ツールとして [Azure CLI](/cli/azure/) も提供されています。</span><span class="sxs-lookup"><span data-stu-id="b8cee-104">In addition to the Azure Portal, Azure also offers the [Azure CLI](/cli/azure/) as a command-line tool to create and manage Azure resources.</span></span> <span data-ttu-id="b8cee-105">Azure CLI には、効率性、再現性、および繰り返し発生するタスクをスクリプト化できるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="b8cee-105">The Azure CLI offers the benefits of efficiency, repeatability, and the ability to script recurring tasks.</span></span>  

<span data-ttu-id="b8cee-106">実際には、ほとんどの開発者は、Azure portal と Azure CLI の両方を使用しています。</span><span class="sxs-lookup"><span data-stu-id="b8cee-106">In practice, most developers use both the Azure Portal and the Azure CLI.</span></span> <span data-ttu-id="b8cee-107">Azure portal は、新しいサービスを探索したり、Azure アカウント内のすべてのリソースの概要を取得したりするときに便利ですが、ほとんどの開発者は、Azure CLI の方がより高速で効率的であると感じています。</span><span class="sxs-lookup"><span data-stu-id="b8cee-107">Where as the Azure Portal is useful when exploring new services and getting an overview of all of the resources in your Azure account, most developers find the Azure CLI to be faster and more efficient.</span></span>  <span data-ttu-id="b8cee-108">Azure CLI を使用すると、Azure portal では複数の手順を実行する必要があることを 1 つのコマンドで実行できる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="b8cee-108">The Azure CLI can often accomplish in a single command what takes multiple steps in the Azure Portal.</span></span>  <span data-ttu-id="b8cee-109">さらに、Azure CLI コマンドはファイルに保存できるため、開発者は繰り返しタスクが毎回同じように実行されることを保証できます。</span><span class="sxs-lookup"><span data-stu-id="b8cee-109">In addition, since Azure CLI commands can be saved to a file, developers can assure that recurrent tasks are run the same way each time.</span></span>

<span data-ttu-id="b8cee-110">Azure CLI は、Windows、macOS、Linux で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8cee-110">The Azure CLI is available for Windows, macOS, and Linux.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8cee-111">Windows での Azure CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="b8cee-111">Install the Azure CLI for Windows</span></span>](/cli/azure/install-azure-cli-windows?tabs=azure-cli)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8cee-112">macOS での Azure CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="b8cee-112">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8cee-113">Linux での Azure CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="b8cee-113">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

### <a name="azure-cloud-shell"></a><span data-ttu-id="b8cee-114">Azure Cloud Shell</span><span class="sxs-lookup"><span data-stu-id="b8cee-114">Azure Cloud Shell</span></span>

<span data-ttu-id="b8cee-115">Azure Cloud Shell ([https://shell.azure.com](https://shell.azure.com)) でも Azure CLI を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b8cee-115">You can also use the Azure CLI in the Azure Cloud Shell at [https://shell.azure.com](https://shell.azure.com).</span></span>  <span data-ttu-id="b8cee-116">Azure Cloud Shell は、Azure リソースを管理するための、完全に機能するブラウザーベースのシェルです。</span><span class="sxs-lookup"><span data-stu-id="b8cee-116">The Azure Cloud Shell is a fully functional, browser-based shell for managing Azure resources.</span></span>  <span data-ttu-id="b8cee-117">Azure Cloud Shell は、コマンドライン環境が必要だが、Azure CLI をインストールできないデバイスで作業している場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b8cee-117">The Azure Cloud Shell is useful when you need a command line environment but are working on a device where you are unable to install the Azure CLI.</span></span>

![ブラウザーで実行されている Azure Cloud Shell のスクリーンショット](media/azure-cloud-shell.png)

### <a name="next-steps"></a><span data-ttu-id="b8cee-119">次のステップ</span><span class="sxs-lookup"><span data-stu-id="b8cee-119">Next steps</span></span>

<span data-ttu-id="b8cee-120">次に、Azure を使用して生産性を向上させるために、Azure Storage Explorer や Azure Data Studio などの[追加の Azure ツールをインストール](./azure-tools.md)します。</span><span class="sxs-lookup"><span data-stu-id="b8cee-120">Next, you will want to [install additional Azure tools](./azure-tools.md) like Azure Storage Explorer and Azure Data Studio to make you more productive with Azure.</span></span>
