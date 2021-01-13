---
title: .NET を使用して Azure 開発用に Visual Studio を構成する
description: この記事は、Azure 開発用に Visual Studio を構成するのに役立ちます。これには、適切なワークロードのインストールや、Visual Studio の Azure アカウントへの接続が含まれます
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2020
ms.locfileid: "97700995"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a><span data-ttu-id="a7181-103">.NET を使用して Azure 開発用に Visual Studio を構成する</span><span class="sxs-lookup"><span data-stu-id="a7181-103">Configure Visual Studio for Azure development with .NET</span></span>

<span data-ttu-id="a7181-104">Visual Studio には、Azure でのアプリケーションの開発とデプロイに役立つツールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a7181-104">Visual Studio includes tooling to help with the development and deployment of applications on Azure.</span></span>  <span data-ttu-id="a7181-105">このガイドは、Azure 開発用に Visual Studio が適切に構成されていることを確認するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a7181-105">This guide will help you make sure that you have Visual Studio properly configured for Azure development.</span></span>

### <a name="download-visual-studio-2019"></a><span data-ttu-id="a7181-106">Visual Studio 2019 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="a7181-106">Download Visual Studio 2019</span></span>

<span data-ttu-id="a7181-107">既に Visual Studio 2019 がインストールされている場合、この手順は省略できます。</span><span class="sxs-lookup"><span data-stu-id="a7181-107">If you already have Visual Studio 2019 installed, you can skip this step.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a7181-108">Visual Studio 2019 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="a7181-108">Download Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a><span data-ttu-id="a7181-109">Azure ワークロードのインストール</span><span class="sxs-lookup"><span data-stu-id="a7181-109">Install Azure workloads</span></span>

<span data-ttu-id="a7181-110">**Visual Studio インストーラー** を起動し、ワークロード **Azure 開発** および **ASP.NET と Web 開発** がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a7181-110">Launch the **Visual Studio Installer** and validate that you have the workloads **Azure development** and **ASP.NET and web development** are installed.</span></span>  <span data-ttu-id="a7181-111">これらのワークロードのいずれかがインストールされていない場合は、これらのワークロードを選択してインストールします。</span><span class="sxs-lookup"><span data-stu-id="a7181-111">If either of these workloads is not installed, select these workloads to install them.</span></span>

![選択された Azure 開発および ASP.NET と Web 開発のワークロードが選択されている Visual Studio インストーラーのスクリーンショット](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a><span data-ttu-id="a7181-113">Azure を使用して Visual Studio を認証する</span><span class="sxs-lookup"><span data-stu-id="a7181-113">Authenticate Visual Studio with Azure</span></span>

<span data-ttu-id="a7181-114">Visual Studio を使用してアプリをデバッグすると、Visual Studio では Azure アカウントを使用して Azure リソースの認証とアクセスが行われます。</span><span class="sxs-lookup"><span data-stu-id="a7181-114">When debugging apps through Visual Studio, Visual Studio can use your Azure account to authenticate and access Azure Resources with.</span></span>  <span data-ttu-id="a7181-115">このアカウントは、Visual Studio から Azure にアプリを直接発行する場合にも使用されます。</span><span class="sxs-lookup"><span data-stu-id="a7181-115">This account is also used when you publish apps directly from Visual Studio to Azure.</span></span>

<span data-ttu-id="a7181-116">Visual Studio から Azure アカウントを認証するには、 **[ツール]**  >  **[オプション]** メニューを選択し、 **[オプション]** ダイアログを起動します。</span><span class="sxs-lookup"><span data-stu-id="a7181-116">To authenticate your Azure account from Visual Studio, select the **Tools** > **Options** menu to launch the **Options** dialog.</span></span> <span data-ttu-id="a7181-117">`Azure Service Authentication` オプションに移動し、Azure アカウントを使用してサインインします。</span><span class="sxs-lookup"><span data-stu-id="a7181-117">Navigate to the `Azure Service Authentication` options and sign in using your Azure account.</span></span>

![Azure ログインを示している Visual Studio の [オプション] ダイアログのスクリーンショット](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a><span data-ttu-id="a7181-119">次のステップ</span><span class="sxs-lookup"><span data-stu-id="a7181-119">Next steps</span></span>

<span data-ttu-id="a7181-120">.NET またはその他の言語での開発にも [Visual Studio Code](https://code.visualstudio.com/) を使用する場合は、[Azure 開発用に Visual Studio Code を構成](./configure-vs-code.md)する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="a7181-120">If you also use [Visual Studio Code](https://code.visualstudio.com/) for development in .NET or any other language, you should also [configure Visual Studio Code for Azure development](./configure-vs-code.md).</span></span> <span data-ttu-id="a7181-121">それ以外の場合は、[Azure CLI のインストール](./install-azure-cli.md)に進みます。</span><span class="sxs-lookup"><span data-stu-id="a7181-121">Otherwise, proceed to [Installing the Azure CLI](./install-azure-cli.md).</span></span>
