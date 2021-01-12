---
title: openSUSE に .NET をインストールする - .NET
description: openSUSE に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 7a519f19f708e1f12af1e9715bad4f38a607f9c3
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970812"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-opensuse"></a><span data-ttu-id="0bac8-103">openSUSE に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="0bac8-103">Install the .NET SDK or the .NET Runtime on openSUSE</span></span>

<span data-ttu-id="0bac8-104">.NET は openSUSE でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0bac8-104">.NET is supported on openSUSE.</span></span> <span data-ttu-id="0bac8-105">この記事では、openSUSE に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0bac8-105">This article describes how to install .NET on openSUSE.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="0bac8-106">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="0bac8-106">Supported distributions</span></span>

<span data-ttu-id="0bac8-107">次の表は、openSUSE 15 で現在サポートされている .NET リリースの一覧です。</span><span class="sxs-lookup"><span data-stu-id="0bac8-107">The following table is a list of currently supported .NET releases on openSUSE 15.</span></span> <span data-ttu-id="0bac8-108">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、openSUSE のバージョンがサポート終了になるまでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="0bac8-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of openSUSE is no longer supported.</span></span>

- <span data-ttu-id="0bac8-109">✔️ は、openSUSE または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="0bac8-109">A ✔️ indicates that the version of openSUSE or .NET is still supported.</span></span>
- <span data-ttu-id="0bac8-110">❌ は、openSUSE または .NET のバージョンがその openSUSE のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="0bac8-110">A ❌ indicates that the version of openSUSE or .NET isn't supported on that openSUSE release.</span></span>
- <span data-ttu-id="0bac8-111">openSUSE のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0bac8-111">When both a version of openSUSE and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="0bac8-112">openSUSE</span><span class="sxs-lookup"><span data-stu-id="0bac8-112">openSUSE</span></span>                   | <span data-ttu-id="0bac8-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="0bac8-113">.NET Core 2.1</span></span> | <span data-ttu-id="0bac8-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="0bac8-114">.NET Core 3.1</span></span> | <span data-ttu-id="0bac8-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="0bac8-115">.NET 5.0</span></span> |
|----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="0bac8-116">✔️ [15](#opensuse-15-)</span><span class="sxs-lookup"><span data-stu-id="0bac8-116">✔️ [15](#opensuse-15-)</span></span>     | <span data-ttu-id="0bac8-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="0bac8-117">✔️ 2.1</span></span>        | <span data-ttu-id="0bac8-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="0bac8-118">✔️ 3.1</span></span>        | <span data-ttu-id="0bac8-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="0bac8-119">✔️ 5.0</span></span> |

<span data-ttu-id="0bac8-120">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="0bac8-120">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="0bac8-121">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="0bac8-121">The downloads for these still remain published:</span></span>

- <span data-ttu-id="0bac8-122">3.0</span><span class="sxs-lookup"><span data-stu-id="0bac8-122">3.0</span></span>
- <span data-ttu-id="0bac8-123">2.2</span><span class="sxs-lookup"><span data-stu-id="0bac8-123">2.2</span></span>
- <span data-ttu-id="0bac8-124">2.0</span><span class="sxs-lookup"><span data-stu-id="0bac8-124">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="0bac8-125">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="0bac8-125">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="opensuse-15-"></a><span data-ttu-id="0bac8-126">openSUSE 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="0bac8-126">openSUSE 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0bac8-127">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="0bac8-127">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="0bac8-128">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0bac8-128">Troubleshoot the package manager</span></span>

<span data-ttu-id="0bac8-129">このセクションでは、パッケージ マネージャーを使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0bac8-129">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="0bac8-130">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="0bac8-130">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="0bac8-131">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="0bac8-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="0bac8-132">依存関係</span><span class="sxs-lookup"><span data-stu-id="0bac8-132">Dependencies</span></span>

<span data-ttu-id="0bac8-133">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0bac8-133">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="0bac8-134">ただし、手動で .NET をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bac8-134">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="0bac8-135">krb5</span><span class="sxs-lookup"><span data-stu-id="0bac8-135">krb5</span></span>
- <span data-ttu-id="0bac8-136">libicu</span><span class="sxs-lookup"><span data-stu-id="0bac8-136">libicu</span></span>
- <span data-ttu-id="0bac8-137">libopenssl1_0_0</span><span class="sxs-lookup"><span data-stu-id="0bac8-137">libopenssl1_0_0</span></span>

<span data-ttu-id="0bac8-138">ターゲット ランタイム環境の OpenSSL バージョンが 1.1 以降である場合は、**compat-openssl10** をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0bac8-138">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="0bac8-139">依存関係の詳細については、「[Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」(自己完結型 Linux アプリケーション) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0bac8-139">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="0bac8-140">*System.Drawing.Common* アセンブリを使用する .NET アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="0bac8-140">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="0bac8-141">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="0bac8-141">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="0bac8-142">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="0bac8-142">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="0bac8-143">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0bac8-143">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0bac8-144">次の手順</span><span class="sxs-lookup"><span data-stu-id="0bac8-144">Next steps</span></span>

- [<span data-ttu-id="0bac8-145">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="0bac8-145">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="0bac8-146">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="0bac8-146">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
