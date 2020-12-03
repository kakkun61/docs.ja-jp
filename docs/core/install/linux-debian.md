---
title: Debian に .NET をインストールする - .NET
description: Debian に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 683d0a9c47edf3cf9c47426d659e778eeb6f84df
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031892"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-debian"></a><span data-ttu-id="8954e-103">Debian に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="8954e-103">Install the .NET SDK or the .NET Runtime on Debian</span></span>

<span data-ttu-id="8954e-104">この記事では、Debian に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8954e-104">This article describes how to install .NET on Debian.</span></span> <span data-ttu-id="8954e-105">Debian のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="8954e-105">When a Debian version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="8954e-106">ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="8954e-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="8954e-107">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="8954e-107">Supported distributions</span></span>

<span data-ttu-id="8954e-108">次の表は、現在サポートされている .NET リリースと、それらがサポートされている Debian のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="8954e-108">The following table is a list of currently supported .NET releases and the versions of Debian they're supported on.</span></span> <span data-ttu-id="8954e-109">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Debian のバージョンの有効期限が切れる](https://wiki.debian.org/DebianReleases)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8954e-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Debian reaches end-of-life](https://wiki.debian.org/DebianReleases).</span></span>

- <span data-ttu-id="8954e-110">✔️ は、Debian または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="8954e-110">A ✔️ indicates that the version of Debian or .NET is still supported.</span></span>
- <span data-ttu-id="8954e-111">❌ は、Debian または .NET のバージョンがその Debian のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="8954e-111">A ❌ indicates that the version of Debian or .NET isn't supported on that Debian release.</span></span>
- <span data-ttu-id="8954e-112">Debian のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8954e-112">When both a version of Debian and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="8954e-113">Debian</span><span class="sxs-lookup"><span data-stu-id="8954e-113">Debian</span></span>                   | <span data-ttu-id="8954e-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8954e-114">.NET Core 2.1</span></span> | <span data-ttu-id="8954e-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="8954e-115">.NET Core 3.1</span></span> | <span data-ttu-id="8954e-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="8954e-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="8954e-117">✔️ [10](#debian-10-)</span><span class="sxs-lookup"><span data-stu-id="8954e-117">✔️ [10](#debian-10-)</span></span>     | <span data-ttu-id="8954e-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="8954e-118">✔️ 2.1</span></span>        | <span data-ttu-id="8954e-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="8954e-119">✔️ 3.1</span></span>        | <span data-ttu-id="8954e-120">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="8954e-120">✔️ 5.0</span></span> |
| <span data-ttu-id="8954e-121">✔️ [9](#debian-9-)</span><span class="sxs-lookup"><span data-stu-id="8954e-121">✔️ [9](#debian-9-)</span></span>       | <span data-ttu-id="8954e-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="8954e-122">✔️ 2.1</span></span>        | <span data-ttu-id="8954e-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="8954e-123">✔️ 3.1</span></span>        | <span data-ttu-id="8954e-124">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="8954e-124">✔️ 5.0</span></span> |
| <span data-ttu-id="8954e-125">❌ [8](#debian-8-)</span><span class="sxs-lookup"><span data-stu-id="8954e-125">❌ [8](#debian-8-)</span></span>       | <span data-ttu-id="8954e-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="8954e-126">✔️ 2.1</span></span>        | <span data-ttu-id="8954e-127">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="8954e-127">❌ 3.1</span></span>        | <span data-ttu-id="8954e-128">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="8954e-128">❌ 5.0</span></span> |

<span data-ttu-id="8954e-129">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="8954e-129">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="8954e-130">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="8954e-130">The downloads for these still remain published:</span></span>

- <span data-ttu-id="8954e-131">3.0</span><span class="sxs-lookup"><span data-stu-id="8954e-131">3.0</span></span>
- <span data-ttu-id="8954e-132">2.2</span><span class="sxs-lookup"><span data-stu-id="8954e-132">2.2</span></span>
- <span data-ttu-id="8954e-133">2.0</span><span class="sxs-lookup"><span data-stu-id="8954e-133">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="8954e-134">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="8954e-134">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="8954e-135">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="8954e-135">How to install other versions</span></span>

[!INCLUDE [hack-pkgname](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="debian-10-"></a><span data-ttu-id="8954e-136">Debian 10 ✔️</span><span class="sxs-lookup"><span data-stu-id="8954e-136">Debian 10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/debian/10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="debian-9-"></a><span data-ttu-id="8954e-137">Debian 9 ✔️</span><span class="sxs-lookup"><span data-stu-id="8954e-137">Debian 9 ✔️</span></span>

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

## <a name="debian-8-"></a><span data-ttu-id="8954e-138">Debian 8 ❌</span><span class="sxs-lookup"><span data-stu-id="8954e-138">Debian 8 ❌</span></span>

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

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="8954e-139">APT での SDK またはランタイムの更新</span><span class="sxs-lookup"><span data-stu-id="8954e-139">APT update SDK or runtime</span></span>

<span data-ttu-id="8954e-140">.NET で新しい修正プログラムのリリースを利用できる場合は、次のコマンドを使用して、APT で簡単にアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="8954e-140">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="8954e-141">APT のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8954e-141">APT troubleshooting</span></span>

<span data-ttu-id="8954e-142">このセクションでは、APT を使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8954e-142">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="8954e-143">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="8954e-143">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="8954e-144">見つからない \\ 一部のパッケージをインストールできませんでした</span><span class="sxs-lookup"><span data-stu-id="8954e-144">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="8954e-145">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="8954e-145">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="8954e-146">Snap</span><span class="sxs-lookup"><span data-stu-id="8954e-146">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="8954e-147">依存関係</span><span class="sxs-lookup"><span data-stu-id="8954e-147">Dependencies</span></span>

<span data-ttu-id="8954e-148">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="8954e-148">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="8954e-149">ただし、手動で .NET Core をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8954e-149">But, if you manually install .NET Core or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="8954e-150">libc6</span><span class="sxs-lookup"><span data-stu-id="8954e-150">libc6</span></span>
- <span data-ttu-id="8954e-151">libgcc1</span><span class="sxs-lookup"><span data-stu-id="8954e-151">libgcc1</span></span>
- <span data-ttu-id="8954e-152">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="8954e-152">libgssapi-krb5-2</span></span>
- <span data-ttu-id="8954e-153">libicu52 (8.x 用)</span><span class="sxs-lookup"><span data-stu-id="8954e-153">libicu52 (for 8.x)</span></span>
- <span data-ttu-id="8954e-154">libicu57 (9.x 用)</span><span class="sxs-lookup"><span data-stu-id="8954e-154">libicu57 (for 9.x)</span></span>
- <span data-ttu-id="8954e-155">libicu63 (10.x 用)</span><span class="sxs-lookup"><span data-stu-id="8954e-155">libicu63 (for 10.x)</span></span>
- <span data-ttu-id="8954e-156">libicu67 (11.x 用)</span><span class="sxs-lookup"><span data-stu-id="8954e-156">libicu67 (for 11.x)</span></span>
- <span data-ttu-id="8954e-157">libssl1.0.0 (8.x 用)</span><span class="sxs-lookup"><span data-stu-id="8954e-157">libssl1.0.0 (for 8.x)</span></span>
- <span data-ttu-id="8954e-158">libssl1.1 (9.x - 11.x 用)</span><span class="sxs-lookup"><span data-stu-id="8954e-158">libssl1.1 (for 9.x-11.x)</span></span>
- <span data-ttu-id="8954e-159">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="8954e-159">libstdc++6</span></span>
- <span data-ttu-id="8954e-160">zlib1g</span><span class="sxs-lookup"><span data-stu-id="8954e-160">zlib1g</span></span>

<span data-ttu-id="8954e-161">*System.Drawing.Common* アセンブリを使用する .NET Core アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="8954e-161">For .NET Core apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="8954e-162">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="8954e-162">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="8954e-163">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="8954e-163">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="8954e-164">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8954e-164">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="8954e-165">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="8954e-165">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="8954e-166">手動インストール</span><span class="sxs-lookup"><span data-stu-id="8954e-166">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="8954e-167">次の手順</span><span class="sxs-lookup"><span data-stu-id="8954e-167">Next steps</span></span>

- [<span data-ttu-id="8954e-168">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="8954e-168">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
