---
title: Debian に .NET をインストールする - .NET
description: Debian に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 913d8bffdd6c0b5e88a70dae0ec4c8d732e80cc0
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970838"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="e6195-103">Debian に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="e6195-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="e6195-104">この記事では、Debian に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e6195-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="e6195-105">Debian のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="e6195-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="e6195-106">ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="e6195-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="e6195-107">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="e6195-107">Supported distributions</span></span>

<span data-ttu-id="e6195-108">次の表は、現在サポートされている .NET リリースと、それらがサポートされている Debian のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="e6195-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="e6195-109">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Debian のバージョンの有効期限が切れる](https://wiki.debian.org/DebianReleases)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e6195-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="e6195-110">✔️ は、Debian または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="e6195-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="e6195-111">❌ は、Debian または .NET のバージョンがその Debian のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="e6195-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="e6195-112">Debian のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e6195-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="e6195-113">Debian</span><span class="sxs-lookup"><span data-stu-id="e6195-113">Debian</span></span>                   | <span data-ttu-id="e6195-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e6195-114">.NET Core 2.1</span></span> | <span data-ttu-id="e6195-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="e6195-115">.NET Core 3.1</span></span> | <span data-ttu-id="e6195-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="e6195-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="e6195-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="e6195-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="e6195-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="e6195-118">✔️ 2.1</span></span>        | <span data-ttu-id="e6195-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="e6195-119">✔️ 3.1</span></span>        | <span data-ttu-id="e6195-120">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="e6195-120">✔️ 5.0</span></span> |
| <span data-ttu-id="e6195-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="e6195-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="e6195-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="e6195-122">✔️ 2.1</span></span>        | <span data-ttu-id="e6195-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="e6195-123">✔️ 3.1</span></span>        | <span data-ttu-id="e6195-124">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="e6195-124">✔️ 5.0</span></span> |
| <span data-ttu-id="e6195-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="e6195-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="e6195-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="e6195-126">✔️ 2.1</span></span>        | <span data-ttu-id="e6195-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="e6195-127">❌ 3.1</span></span>        | <span data-ttu-id="e6195-128">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="e6195-128">❌ 5.0</span></span> |

<span data-ttu-id="e6195-129">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="e6195-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="e6195-130">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="e6195-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="e6195-131">3.0</span><span class="sxs-lookup"><span data-stu-id="e6195-131">3.0</span></span>
- <span data-ttu-id="e6195-132">2.2</span><span class="sxs-lookup"><span data-stu-id="e6195-132">2.2</span></span>
- <span data-ttu-id="e6195-133">2.0</span><span class="sxs-lookup"><span data-stu-id="e6195-133">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="e6195-134">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="e6195-134">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="debian-10-"></a><span data-ttu-id="e6195-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="e6195-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="e6195-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="e6195-136">Debian 9 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-8-"></a><span data-ttu-id="e6195-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="e6195-137">Debian 8 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-debian.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/8/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e6195-138">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="e6195-138">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="e6195-139">APT を使用して .NET を更新する</span><span class="sxs-lookup"><span data-stu-id="e6195-139">Use APT to update .NET</span></span>

<span data-ttu-id="e6195-140">.NET で新しい修正プログラムのリリースを利用できる場合は、次のコマンドを使用して、APT で簡単にアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="e6195-140">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="e6195-141">APT のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e6195-141">APT troubleshooting</span></span>

<span data-ttu-id="e6195-142">このセクションでは、APT を使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e6195-142">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="e6195-143">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="e6195-143">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="e6195-144">見つからない \\ 一部のパッケージをインストールできませんでした</span><span class="sxs-lookup"><span data-stu-id="e6195-144">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="e6195-145">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="e6195-145">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="e6195-146">依存関係</span><span class="sxs-lookup"><span data-stu-id="e6195-146">Dependencies</span></span>

<span data-ttu-id="e6195-147">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e6195-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="e6195-148">ただし、手動で .NET Core をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e6195-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="e6195-149">libc6</span><span class="sxs-lookup"><span data-stu-id="e6195-149">libc6</span></span>
- <span data-ttu-id="e6195-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="e6195-150">libgcc1</span></span>
- <span data-ttu-id="e6195-151">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="e6195-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="e6195-152">libicu52 (8.x 用)</span><span class="sxs-lookup"><span data-stu-id="e6195-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="e6195-153">libicu57 (9.x 用)</span><span class="sxs-lookup"><span data-stu-id="e6195-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="e6195-154">libicu63 (10.x 用)</span><span class="sxs-lookup"><span data-stu-id="e6195-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="e6195-155">libicu67 (11.x 用)</span><span class="sxs-lookup"><span data-stu-id="e6195-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="e6195-156">libssl1.0.0 (8.x 用)</span><span class="sxs-lookup"><span data-stu-id="e6195-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="e6195-157">libssl1.1 (9.x - 11.x 用)</span><span class="sxs-lookup"><span data-stu-id="e6195-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="e6195-158">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="e6195-158">libstdc++6</span></span>
- <span data-ttu-id="e6195-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="e6195-159">zlib1g</span></span>

<span data-ttu-id="e6195-160">*System.Drawing.Common* アセンブリを使用する .NET Core アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="e6195-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="e6195-161">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="e6195-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="e6195-162">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="e6195-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="e6195-163">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e6195-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e6195-164">次の手順</span><span class="sxs-lookup"><span data-stu-id="e6195-164">Next steps</span></span>

- [<span data-ttu-id="e6195-165">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="e6195-165">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="e6195-166">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="e6195-166">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
