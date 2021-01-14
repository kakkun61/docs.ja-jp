---
title: Fedora に .NET をインストールする - .NET
description: Fedora に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 9dd8c6264831e2a9382960be505639f1eba95151
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970825"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="eed27-103">Fedora に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="eed27-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="eed27-104">.NET は Fedora でサポートされており、この記事では Fedora に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eed27-104">.NET is supported on Fedora and this article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="eed27-105">Fedora のバージョンがサポート対象外となった場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="eed27-105">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="install-net-50"></a><span data-ttu-id="eed27-106">.NET 5.0 をインストールする</span><span class="sxs-lookup"><span data-stu-id="eed27-106">Install .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="eed27-107">**Fedora 32**</span><span class="sxs-lookup"><span data-stu-id="eed27-107">**Fedora 32**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

<span data-ttu-id="eed27-108">**Fedora 33**</span><span class="sxs-lookup"><span data-stu-id="eed27-108">**Fedora 33**</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="install-net-core-31"></a><span data-ttu-id="eed27-109">.NET Core 3.1 をインストールする</span><span class="sxs-lookup"><span data-stu-id="eed27-109">Install .NET Core 3.1</span></span>

<span data-ttu-id="eed27-110">Fedora の既定のパッケージ リポジトリで利用可能な最新バージョンの .NET は、.NET Core 3.1 です。</span><span class="sxs-lookup"><span data-stu-id="eed27-110">The latest version of .NET available in the default package repositories for Fedora is .NET Core 3.1.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="supported-distributions"></a><span data-ttu-id="eed27-111">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="eed27-111">Supported distributions</span></span>

<span data-ttu-id="eed27-112">現在サポートされている .NET リリースと、それらがサポートされている Fedora のバージョンの一覧は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="eed27-112">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="eed27-113">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Fedora のバージョンがサポート終了になる](https://fedoraproject.org/wiki/End_of_life)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="eed27-113">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="eed27-114">✔️ は、Fedora または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="eed27-114">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="eed27-115">❌ は、Fedora または .NET のバージョンがその Fedora のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="eed27-115">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="eed27-116">Fedora のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="eed27-116">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="eed27-117">.NET のバージョン</span><span class="sxs-lookup"><span data-stu-id="eed27-117">.NET Version</span></span>  | <span data-ttu-id="eed27-118">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-118">Fedora 33 ✔️</span></span> | <span data-ttu-id="eed27-119">32 ✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-119">32 ✔️</span></span> | <span data-ttu-id="eed27-120">31 ❌</span><span class="sxs-lookup"><span data-stu-id="eed27-120">31 ❌</span></span> | <span data-ttu-id="eed27-121">30 ❌</span><span class="sxs-lookup"><span data-stu-id="eed27-121">30 ❌</span></span> | <span data-ttu-id="eed27-122">29 ❌</span><span class="sxs-lookup"><span data-stu-id="eed27-122">29 ❌</span></span> | <span data-ttu-id="eed27-123">28 ❌</span><span class="sxs-lookup"><span data-stu-id="eed27-123">28 ❌</span></span> | <span data-ttu-id="eed27-124">27 ❌</span><span class="sxs-lookup"><span data-stu-id="eed27-124">27 ❌</span></span> |
| ------------  | ---------: | --: | --: | --: | --: | --: | --: |
| <span data-ttu-id="eed27-125">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="eed27-125">.NET 5.0</span></span>      | <span data-ttu-id="eed27-126">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-126">✔️</span></span>        | <span data-ttu-id="eed27-127">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-127">✔️</span></span> | ❌|❌ |❌ |❌  |❌ |
| <span data-ttu-id="eed27-128">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="eed27-128">.NET Core 3.1</span></span> | <span data-ttu-id="eed27-129">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-129">✔️</span></span>        | <span data-ttu-id="eed27-130">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-130">✔️</span></span> | <span data-ttu-id="eed27-131">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-131">✔️</span></span>|<span data-ttu-id="eed27-132">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-132">✔️</span></span> |<span data-ttu-id="eed27-133">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-133">✔️</span></span> |❌  |❌ |
| <span data-ttu-id="eed27-134">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eed27-134">.NET Core 2.1</span></span> | <span data-ttu-id="eed27-135">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-135">✔️</span></span>        | <span data-ttu-id="eed27-136">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-136">✔️</span></span> | <span data-ttu-id="eed27-137">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-137">✔️</span></span>|<span data-ttu-id="eed27-138">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-138">✔️</span></span> |<span data-ttu-id="eed27-139">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-139">✔️</span></span> |<span data-ttu-id="eed27-140">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-140">✔️</span></span>  |<span data-ttu-id="eed27-141">✔️</span><span class="sxs-lookup"><span data-stu-id="eed27-141">✔️</span></span> |

<span data-ttu-id="eed27-142">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="eed27-142">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="eed27-143">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="eed27-143">The downloads for these still remain published:</span></span>

- <span data-ttu-id="eed27-144">3.0</span><span class="sxs-lookup"><span data-stu-id="eed27-144">3.0</span></span>
- <span data-ttu-id="eed27-145">2.2</span><span class="sxs-lookup"><span data-stu-id="eed27-145">2.2</span></span>
- <span data-ttu-id="eed27-146">2.0</span><span class="sxs-lookup"><span data-stu-id="eed27-146">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="eed27-147">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="eed27-147">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="dependencies"></a><span data-ttu-id="eed27-148">依存関係</span><span class="sxs-lookup"><span data-stu-id="eed27-148">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="install-on-older-distributions"></a><span data-ttu-id="eed27-149">古いディストリビューションにインストールする</span><span class="sxs-lookup"><span data-stu-id="eed27-149">Install on older distributions</span></span>

<span data-ttu-id="eed27-150">古いバージョンの Fedora の既定のパッケージ リポジトリには、.NET Core が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="eed27-150">Older versions of Fedora don't contain .NET Core in the default package repositories.</span></span> <span data-ttu-id="eed27-151">[snap](linux-snap.md)、[_dotnet-install.sh_ スクリプト](linux-scripted-manual.md#scripted-install)、または Microsoft のリポジトリを使用して、.NET をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="eed27-151">You can install .NET with [snap](linux-snap.md), through the [_dotnet-install.sh_ script](linux-scripted-manual.md#scripted-install), or use Microsoft's repository to install .NET:</span></span>

01. <span data-ttu-id="eed27-152">最初に、Microsoft 署名キーを信頼されたキーのリストに追加します。</span><span class="sxs-lookup"><span data-stu-id="eed27-152">First, add the Microsoft signing key to your list of trusted keys.</span></span>

    ```bash
    sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
    ```

02. <span data-ttu-id="eed27-153">次に、Microsoft パッケージ リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="eed27-153">Next, add the Microsoft package repository.</span></span> <span data-ttu-id="eed27-154">リポジトリのソースは、お使いの Fedora のバージョンに基づいています。</span><span class="sxs-lookup"><span data-stu-id="eed27-154">The source of the repository is based on your version of Fedora.</span></span>

    | <span data-ttu-id="eed27-155">Fedora のバージョン</span><span class="sxs-lookup"><span data-stu-id="eed27-155">Fedora Version</span></span> | <span data-ttu-id="eed27-156">パッケージ リポジトリ</span><span class="sxs-lookup"><span data-stu-id="eed27-156">Package repository</span></span> |
    | -------------- | ------- |
    | <span data-ttu-id="eed27-157">31</span><span class="sxs-lookup"><span data-stu-id="eed27-157">31</span></span>             | `https://packages.microsoft.com/config/fedora/31/prod.repo` |
    | <span data-ttu-id="eed27-158">30</span><span class="sxs-lookup"><span data-stu-id="eed27-158">30</span></span>             | `https://packages.microsoft.com/config/fedora/30/prod.repo` |
    | <span data-ttu-id="eed27-159">29</span><span class="sxs-lookup"><span data-stu-id="eed27-159">29</span></span>             | `https://packages.microsoft.com/config/fedora/29/prod.repo` |
    | <span data-ttu-id="eed27-160">28</span><span class="sxs-lookup"><span data-stu-id="eed27-160">28</span></span>             | `https://packages.microsoft.com/config/fedora/28/prod.repo` |
    | <span data-ttu-id="eed27-161">27</span><span class="sxs-lookup"><span data-stu-id="eed27-161">27</span></span>             | `https://packages.microsoft.com/config/fedora/27/prod.repo` |

    ```bash
    sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
    ```

[!INCLUDE [linux-dnf-install-31](./includes/linux-install-31-dnf.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="eed27-162">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="eed27-162">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="eed27-163">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="eed27-163">Troubleshoot the package manager</span></span>

<span data-ttu-id="eed27-164">このセクションでは、パッケージ マネージャーを使用して .NET または .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="eed27-164">This section provides information on common errors you may get while using the package manager to install .NET or .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="eed27-165">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="eed27-165">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="eed27-166">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="eed27-166">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="next-steps"></a><span data-ttu-id="eed27-167">次のステップ</span><span class="sxs-lookup"><span data-stu-id="eed27-167">Next steps</span></span>

- [<span data-ttu-id="eed27-168">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="eed27-168">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="eed27-169">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="eed27-169">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
