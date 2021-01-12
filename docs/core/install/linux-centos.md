---
title: CentOS に .NET をインストールする - .NET
description: CentOS に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7e73f90a1f1f7e11e592b1b074f243c9f5b32ced
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970864"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="fc5c7-103">CentOS に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="fc5c7-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="fc5c7-104">.NET は CentOS でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="fc5c7-105">この記事では、CentOS に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="fc5c7-106">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="fc5c7-106">Supported distributions</span></span>

<span data-ttu-id="fc5c7-107">CentOS 7 と CentOS 8 の両方で現在サポートされている .NET のリリースの一覧は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="fc5c7-108">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、CentOS のバージョンがサポート終了になるまでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="fc5c7-109">✔️ は、CentOS または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="fc5c7-110">❌ は、CentOS または .NET のバージョンがその CentOS のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="fc5c7-111">CentOS のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="fc5c7-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="fc5c7-112">CentOS</span></span>                   | <span data-ttu-id="fc5c7-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fc5c7-113">.NET Core 2.1</span></span> | <span data-ttu-id="fc5c7-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="fc5c7-114">.NET Core 3.1</span></span> | <span data-ttu-id="fc5c7-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="fc5c7-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="fc5c7-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="fc5c7-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="fc5c7-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="fc5c7-117">✔️ 2.1</span></span>        | <span data-ttu-id="fc5c7-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="fc5c7-118">✔️ 3.1</span></span>        | <span data-ttu-id="fc5c7-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="fc5c7-119">✔️ 5.0</span></span> |
| <span data-ttu-id="fc5c7-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="fc5c7-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="fc5c7-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="fc5c7-121">✔️ 2.1</span></span>        | <span data-ttu-id="fc5c7-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="fc5c7-122">✔️ 3.1</span></span>        | <span data-ttu-id="fc5c7-123">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="fc5c7-123">✔️ 5.0</span></span> |

<span data-ttu-id="fc5c7-124">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="fc5c7-125">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="fc5c7-126">3.0</span><span class="sxs-lookup"><span data-stu-id="fc5c7-126">3.0</span></span>
- <span data-ttu-id="fc5c7-127">2.2</span><span class="sxs-lookup"><span data-stu-id="fc5c7-127">2.2</span></span>
- <span data-ttu-id="fc5c7-128">2.0</span><span class="sxs-lookup"><span data-stu-id="fc5c7-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="remove-preview-versions"></a><span data-ttu-id="fc5c7-129">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="fc5c7-129">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="centos-8-"></a><span data-ttu-id="fc5c7-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="fc5c7-130">CentOS 8 ✔️</span></span>

<span data-ttu-id="fc5c7-131">.NET 5.0 は CentOS 8 の既定のパッケージ リポジトリで利用できます。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-131">.NET 5.0 is available in the default package repositories for CentOS 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="fc5c7-132">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="fc5c7-132">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fc5c7-133">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="fc5c7-133">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="fc5c7-134">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="fc5c7-134">Troubleshoot the package manager</span></span>

<span data-ttu-id="fc5c7-135">このセクションでは、パッケージ マネージャーを使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fc5c7-135">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="fc5c7-136">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="fc5c7-136">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="fc5c7-137">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="fc5c7-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="fc5c7-138">依存関係</span><span class="sxs-lookup"><span data-stu-id="fc5c7-138">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="next-steps"></a><span data-ttu-id="fc5c7-139">次のステップ</span><span class="sxs-lookup"><span data-stu-id="fc5c7-139">Next steps</span></span>

- [<span data-ttu-id="fc5c7-140">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="fc5c7-140">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="fc5c7-141">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="fc5c7-141">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
