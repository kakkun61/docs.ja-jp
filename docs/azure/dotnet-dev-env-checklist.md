---
title: Azure での .NET 開発の構成チェックリスト
description: Azure を使用して .net 開発を行うためにインストールしておく必要があるすべてのツールについて簡単にまとめます
ms.date: 1/1/2021
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: a2ff9bbf1e6a8790ddc161a1a1c8d14e8fab6e41
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98027242"
---
# <a name="net-on-azure-development-environment-checklist"></a><span data-ttu-id="a35e4-103">Azure での .NET 開発環境のチェックリスト</span><span class="sxs-lookup"><span data-stu-id="a35e4-103">.NET on Azure development environment checklist</span></span>

<span data-ttu-id="a35e4-104">このチェックリストは、Azure を使用する .NET 開発用に開発環境が正しく構成されていることを確認するのに役立つように提供されています</span><span class="sxs-lookup"><span data-stu-id="a35e4-104">This checklist is provided to help you make sure you have your development environment correctly configured for .NET development with Azure</span></span>

## <a name="create-an-azure-account"></a><span data-ttu-id="a35e4-105">Azure アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="a35e4-105">Create an Azure account</span></span>

<span data-ttu-id="a35e4-106">Azure サービスにアクセスしたり、Azure でアプリケーションを実行したりするには、Azure アカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="a35e4-106">To access Azure services or run applications in Azure, you need an Azure account.</span></span>

* <span data-ttu-id="a35e4-107">Visual Studio サブスクライバーである場合は、月単位の[無料の Azure クレジット](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/)を毎月ご利用いただけます</span><span class="sxs-lookup"><span data-stu-id="a35e4-107">If you are a Visual Studio subscriber, you have monthly [free Azure credits](https://azure.microsoft.com/pricing/member-offers/credit-for-visual-studio-subscribers/) available to you every month</span></span>
* <span data-ttu-id="a35e4-108">[無料の Azure アカウントを作成](https://azure.microsoft.com/free/dotnet/)し、$200 をクレジットで受け取り、12 か月間無料のサービスを選択します</span><span class="sxs-lookup"><span data-stu-id="a35e4-108">[Create a free Azure account](https://azure.microsoft.com/free/dotnet/) and receive $200 in credits and select services free for 12 months</span></span>
* <span data-ttu-id="a35e4-109">会社の Azure 管理者によって割り当てられたアカウントを使用します</span><span class="sxs-lookup"><span data-stu-id="a35e4-109">Use an account assigned to you by your company's Azure administrator</span></span>

## <a name="configure-your-ide"></a><span data-ttu-id="a35e4-110">IDE を構成する</span><span class="sxs-lookup"><span data-stu-id="a35e4-110">Configure your IDE</span></span>

<span data-ttu-id="a35e4-111">Visual Studio や Visual Studio Code などの一般的なツールには、IDE から直接 Azure を操作できる拡張機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a35e4-111">Popular tools like Visual Studio and Visual Studio Code have extensions available to let you work with Azure right from your IDE.</span></span>

* <span data-ttu-id="a35e4-112">Azure を使用する .NET 開発用に [Visual Studio を構成する](./configure-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="a35e4-112">[Configure Visual Studio](./configure-visual-studio.md) for .NET development using Azure</span></span>
* <span data-ttu-id="a35e4-113">Azure を使用する .NET 開発用に [Visual Studio Code を構成する](./configure-vs-code.md)</span><span class="sxs-lookup"><span data-stu-id="a35e4-113">[Configure Visual Studio Code](./configure-vs-code.md) for .NET Development using Azure</span></span>

## <a name="install-the-azure-cli"></a><span data-ttu-id="a35e4-114">Azure CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="a35e4-114">Install the Azure CLI</span></span>

<span data-ttu-id="a35e4-115">Azure portal を使用するだけでなく、Azure CLI をインストールして Azure リソースを作成および管理することもできます。</span><span class="sxs-lookup"><span data-stu-id="a35e4-115">In addition to using the Azure portal, you will want to install the Azure CLI to create and manage Azure resources.</span></span>

* <span data-ttu-id="a35e4-116">[Windows 用の Azure CLI をインストールする](/cli/azure/install-azure-cli-windows?tabs=azure-cli)</span><span class="sxs-lookup"><span data-stu-id="a35e4-116">[Install the Azure CLI for Windows](/cli/azure/install-azure-cli-windows?tabs=azure-cli))</span></span>
* [<span data-ttu-id="a35e4-117">macOS での Azure CLI のインストール</span><span class="sxs-lookup"><span data-stu-id="a35e4-117">Install the Azure CLI for macOS</span></span>](/cli/azure/install-azure-cli-macos)
* [<span data-ttu-id="a35e4-118">Linux 用の Azure CLI をインストールする</span><span class="sxs-lookup"><span data-stu-id="a35e4-118">Install the Azure CLI for Linux</span></span>](/cli/azure/install-azure-cli-linux)

## <a name="install-additional-tools-and-utilities"></a><span data-ttu-id="a35e4-119">その他のツールとユーティリティをインストールする</span><span class="sxs-lookup"><span data-stu-id="a35e4-119">Install additional tools and utilities</span></span>

<span data-ttu-id="a35e4-120">これらのその他のツールは、Azure を操作するときの生産性を高めるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a35e4-120">These additional tools are designed to make you more productive when working with Azure.</span></span>

* <span data-ttu-id="a35e4-121">PowerShell スクリプトを使用して Azure リソースを作成および管理する予定の場合は、[Azure PowerShell をインストールします](/powershell/azure/install-az-ps)</span><span class="sxs-lookup"><span data-stu-id="a35e4-121">[Install Azure PowerShell](/powershell/azure/install-az-ps) if you plan on using PowerShell scripts to create and manage Azure resources</span></span>
* <span data-ttu-id="a35e4-122">BLOB、キュー、テーブル、CosmosDB を含む Azure ストレージ リソースのデータをアップロード、ダウンロード、および管理するには、[Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a35e4-122">[Install Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) to upload, download, and manage data in Azure storage resources including blobs, queues, tables, and CosmosDB.</span></span>
* <span data-ttu-id="a35e4-123">Azure SQL を操作する場合は、[Azure Data Studio をインストールします](/sql/azure-data-studio/download-azure-data-studio)</span><span class="sxs-lookup"><span data-stu-id="a35e4-123">[Install Azure Data Studio](/sql/azure-data-studio/download-azure-data-studio) if you are working with Azure SQL</span></span>

## <a name="bookmark-the-following-sites"></a><span data-ttu-id="a35e4-124">フォロー中のサイトをブックマークする</span><span class="sxs-lookup"><span data-stu-id="a35e4-124">Bookmark the following sites</span></span>

<span data-ttu-id="a35e4-125">これらのサイトは、Azure の開発を行うときに頻繁に使用します。</span><span class="sxs-lookup"><span data-stu-id="a35e4-125">You will use these sites frequently when doing Azure development.</span></span>  <span data-ttu-id="a35e4-126">クイック リファレンス用にブックマークします。</span><span class="sxs-lookup"><span data-stu-id="a35e4-126">Bookmark them for quick reference.</span></span>

* <span data-ttu-id="a35e4-127">Azure Portal - [https://portal.azure.com/](https://portal.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="a35e4-127">Azure Portal - [https://portal.azure.com/](https://portal.azure.com/)</span></span>
* <span data-ttu-id="a35e4-128">Azure Cloud Shell - [https://shell.azure.com/](https://shell.azure.com/)</span><span class="sxs-lookup"><span data-stu-id="a35e4-128">Azure Cloud Shell - [https://shell.azure.com/](https://shell.azure.com/)</span></span>
