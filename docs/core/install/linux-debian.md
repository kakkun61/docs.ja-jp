---
title: Debian に .NET をインストールする - .NET
description: Debian に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 6dad4e1779600b22b8301e03ffb8fb2c16786ead
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506999"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="a1e3b-103">Debian に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="a1e3b-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="a1e3b-104">この記事では、Debian に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="a1e3b-105">Debian のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="a1e3b-106">ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="a1e3b-107">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="a1e3b-107">Supported distributions</span></span>

<span data-ttu-id="a1e3b-108">次の表は、現在サポートされている .NET リリースと、それらがサポートされている Debian のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="a1e3b-109">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Debian のバージョンの有効期限が切れる](https://wiki.debian.org/DebianReleases)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="a1e3b-110">✔️ は、Debian または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="a1e3b-111">❌ は、Debian または .NET のバージョンがその Debian のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="a1e3b-112">Debian のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="a1e3b-113">Debian</span><span class="sxs-lookup"><span data-stu-id="a1e3b-113">Debian</span></span>                   | <span data-ttu-id="a1e3b-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-114">.NET Core 2.1</span></span> | <span data-ttu-id="a1e3b-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-115">.NET Core 3.1</span></span> | <span data-ttu-id="a1e3b-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a1e3b-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="a1e3b-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="a1e3b-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-118">✔️ 2.1</span></span>        | <span data-ttu-id="a1e3b-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-119">✔️ 3.1</span></span>        | <span data-ttu-id="a1e3b-120">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="a1e3b-120">✔️ 5.0</span></span> |
| <span data-ttu-id="a1e3b-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="a1e3b-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-122">✔️ 2.1</span></span>        | <span data-ttu-id="a1e3b-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-123">✔️ 3.1</span></span>        | <span data-ttu-id="a1e3b-124">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="a1e3b-124">✔️ 5.0</span></span> |
| <span data-ttu-id="a1e3b-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="a1e3b-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-126">✔️ 2.1</span></span>        | <span data-ttu-id="a1e3b-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-127">❌ 3.1</span></span>        | <span data-ttu-id="a1e3b-128">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="a1e3b-128">❌ 5.0</span></span> |

<span data-ttu-id="a1e3b-129">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="a1e3b-130">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="a1e3b-131">3.0</span><span class="sxs-lookup"><span data-stu-id="a1e3b-131">3.0</span></span>
- <span data-ttu-id="a1e3b-132">2.2</span><span class="sxs-lookup"><span data-stu-id="a1e3b-132">2.2</span></span>
- <span data-ttu-id="a1e3b-133">2.0</span><span class="sxs-lookup"><span data-stu-id="a1e3b-133">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a1e3b-134">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="a1e3b-134">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="a1e3b-135">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="a1e3b-135">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="a1e3b-136">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="a1e3b-136">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="a1e3b-137">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="a1e3b-137">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="a1e3b-138">APT での SDK またはランタイムの更新</span><span class="sxs-lookup"><span data-stu-id="a1e3b-138">APT update SDK or runtime</span></span>

<span data-ttu-id="a1e3b-139">.NET で新しい修正プログラムのリリースを利用できる場合は、次のコマンドを使用して、APT で簡単にアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-139">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="a1e3b-140">APT のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a1e3b-140">APT troubleshooting</span></span>

<span data-ttu-id="a1e3b-141">このセクションでは、APT を使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-141">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="a1e3b-142">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="a1e3b-142">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="a1e3b-143">見つからない \\ 一部のパッケージをインストールできませんでした</span><span class="sxs-lookup"><span data-stu-id="a1e3b-143">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="a1e3b-144">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="a1e3b-144">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="a1e3b-145">Snap</span><span class="sxs-lookup"><span data-stu-id="a1e3b-145">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="a1e3b-146">依存関係</span><span class="sxs-lookup"><span data-stu-id="a1e3b-146">Dependencies</span></span>

<span data-ttu-id="a1e3b-147">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-147">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="a1e3b-148">ただし、手動で .NET Core をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-148">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="a1e3b-149">libc6</span><span class="sxs-lookup"><span data-stu-id="a1e3b-149">libc6</span></span>
- <span data-ttu-id="a1e3b-150">libgcc1</span><span class="sxs-lookup"><span data-stu-id="a1e3b-150">libgcc1</span></span>
- <span data-ttu-id="a1e3b-151">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="a1e3b-151">libgssapi-krb5-2</span></span>
- <span data-ttu-id="a1e3b-152">libicu52 (8.x 用)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-152">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="a1e3b-153">libicu57 (9.x 用)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-153">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="a1e3b-154">libicu63 (10.x 用)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-154">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="a1e3b-155">libicu67 (11.x 用)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-155">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="a1e3b-156">libssl1.0.0 (8.x 用)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-156">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="a1e3b-157">libssl1.1 (9.x - 11.x 用)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-157">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="a1e3b-158">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="a1e3b-158">libstdc++6</span></span>
- <span data-ttu-id="a1e3b-159">zlib1g</span><span class="sxs-lookup"><span data-stu-id="a1e3b-159">zlib1g</span></span>

<span data-ttu-id="a1e3b-160">*System.Drawing.Common* アセンブリを使用する .NET Core アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-160">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="a1e3b-161">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="a1e3b-161">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="a1e3b-162">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-162">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="a1e3b-163">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e3b-163">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="a1e3b-164">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="a1e3b-164">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="a1e3b-165">手動インストール</span><span class="sxs-lookup"><span data-stu-id="a1e3b-165">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="a1e3b-166">次の手順</span><span class="sxs-lookup"><span data-stu-id="a1e3b-166">Next steps</span></span>

- [<span data-ttu-id="a1e3b-167">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="a1e3b-167">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
