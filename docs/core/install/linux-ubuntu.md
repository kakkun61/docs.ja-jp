---
title: Ubuntu に .NET をインストールする - .NET
description: Ubuntu に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 22ce3379e028f065528e1f507a2d8c1ae598f0e8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031848"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="88547-103">Ubuntu に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="88547-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="88547-104">.NET は Ubuntu でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="88547-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="88547-105">この記事では、Ubuntu に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="88547-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="88547-106">Ubuntu のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="88547-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="88547-107">ただし、サポート対象外の場合でも、これらの手順がそれらのバージョンで .NET を実行するのに役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="88547-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="88547-108">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="88547-108">Supported distributions</span></span>

<span data-ttu-id="88547-109">次の表は、現在サポートされている .NET リリースと、それらがサポートされている Ubuntu のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="88547-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="88547-110">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Ubuntu のバージョンが期限切れになる](https://wiki.ubuntu.com/Releases)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="88547-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="88547-111">✔️ は、Ubuntu または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="88547-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="88547-112">❌ は、Ubuntu または .NET のバージョンがその Ubuntu のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="88547-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="88547-113">Ubuntu のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="88547-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="88547-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="88547-114">Ubuntu</span></span>                   | <span data-ttu-id="88547-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-115">.NET Core 2.1</span></span> | <span data-ttu-id="88547-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-116">.NET Core 3.1</span></span> | <span data-ttu-id="88547-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="88547-118">✔️ [20.10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="88547-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="88547-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-119">✔️ 2.1</span></span>        | <span data-ttu-id="88547-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-120">✔️ 3.1</span></span>        | <span data-ttu-id="88547-121">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-121">✔️ 5.0</span></span> |
| <span data-ttu-id="88547-122">✔️ [20.04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="88547-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="88547-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-123">✔️ 2.1</span></span>        | <span data-ttu-id="88547-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-124">✔️ 3.1</span></span>        | <span data-ttu-id="88547-125">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-125">✔️ 5.0</span></span> |
| <span data-ttu-id="88547-126">❌ [19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="88547-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="88547-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-127">✔️ 2.1</span></span>        | <span data-ttu-id="88547-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-128">✔️ 3.1</span></span>        | <span data-ttu-id="88547-129">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-129">✔️ 5.0</span></span> |
| <span data-ttu-id="88547-130">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="88547-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="88547-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-131">✔️ 2.1</span></span>        | <span data-ttu-id="88547-132">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-132">✔️ 3.1</span></span>        | <span data-ttu-id="88547-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-133">❌ 5.0</span></span> |
| <span data-ttu-id="88547-134">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="88547-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="88547-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-135">✔️ 2.1</span></span>        | <span data-ttu-id="88547-136">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-136">❌ 3.1</span></span>        | <span data-ttu-id="88547-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-137">❌ 5.0</span></span> |
| <span data-ttu-id="88547-138">✔️ [18.04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="88547-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="88547-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-139">✔️ 2.1</span></span>        | <span data-ttu-id="88547-140">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-140">✔️ 3.1</span></span>        | <span data-ttu-id="88547-141">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-141">✔️ 5.0</span></span> |
| <span data-ttu-id="88547-142">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="88547-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="88547-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-143">✔️ 2.1</span></span>        | <span data-ttu-id="88547-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-144">❌ 3.1</span></span>        | <span data-ttu-id="88547-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-145">❌ 5.0</span></span> |
| <span data-ttu-id="88547-146">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="88547-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="88547-147">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-147">✔️ 2.1</span></span>        | <span data-ttu-id="88547-148">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-148">❌ 3.1</span></span>        | <span data-ttu-id="88547-149">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-149">❌ 5.0</span></span> |
| <span data-ttu-id="88547-150">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="88547-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="88547-151">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-151">❌ 2.1</span></span>        | <span data-ttu-id="88547-152">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-152">❌ 3.1</span></span>        | <span data-ttu-id="88547-153">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-153">❌ 5.0</span></span> |
| <span data-ttu-id="88547-154">✔️ [16.04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="88547-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="88547-155">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="88547-155">✔️ 2.1</span></span>        | <span data-ttu-id="88547-156">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="88547-156">✔️ 3.1</span></span>        | <span data-ttu-id="88547-157">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="88547-157">✔️ 5.0</span></span> |

<span data-ttu-id="88547-158">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="88547-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="88547-159">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="88547-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="88547-160">3.0</span><span class="sxs-lookup"><span data-stu-id="88547-160">3.0</span></span>
- <span data-ttu-id="88547-161">2.2</span><span class="sxs-lookup"><span data-stu-id="88547-161">2.2</span></span>
- <span data-ttu-id="88547-162">2.0</span><span class="sxs-lookup"><span data-stu-id="88547-162">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="88547-163">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="88547-163">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="88547-164">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="88547-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="88547-165">20.10 ✔️</span><span class="sxs-lookup"><span data-stu-id="88547-165">20.10 ✔️</span></span>

> [!IMPORTANT]
> <span data-ttu-id="88547-166">.NET Core 2.1 はパッケージ フィードではまだ利用できません。</span><span class="sxs-lookup"><span data-stu-id="88547-166">.NET Core 2.1 isn't yet available in the package feed.</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="88547-167">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="88547-167">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="88547-168">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="88547-168">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="88547-169">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="88547-169">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="88547-170">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="88547-170">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="88547-171">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="88547-171">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="88547-172">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="88547-172">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="88547-173">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="88547-173">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="88547-174">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="88547-174">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="88547-175">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="88547-175">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="88547-176">APT での SDK またはランタイムの更新</span><span class="sxs-lookup"><span data-stu-id="88547-176">APT update SDK or runtime</span></span>

<span data-ttu-id="88547-177">.NET で新しい修正プログラムのリリースを利用できる場合は、次のコマンドを使用して、APT で簡単にアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="88547-177">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="88547-178">APT のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="88547-178">APT troubleshooting</span></span>

<span data-ttu-id="88547-179">このセクションでは、APT を使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="88547-179">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="88547-180">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="88547-180">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="88547-181">見つからない \\ 一部のパッケージをインストールできませんでした</span><span class="sxs-lookup"><span data-stu-id="88547-181">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="88547-182">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="88547-182">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="88547-183">Snap</span><span class="sxs-lookup"><span data-stu-id="88547-183">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="88547-184">依存関係</span><span class="sxs-lookup"><span data-stu-id="88547-184">Dependencies</span></span>

<span data-ttu-id="88547-185">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="88547-185">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="88547-186">ただし、手動で .NET をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88547-186">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="88547-187">libc6</span><span class="sxs-lookup"><span data-stu-id="88547-187">libc6</span></span>
- <span data-ttu-id="88547-188">libgcc1</span><span class="sxs-lookup"><span data-stu-id="88547-188">libgcc1</span></span>
- <span data-ttu-id="88547-189">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="88547-189">libgssapi-krb5-2</span></span>
- <span data-ttu-id="88547-190">libicu52 (14.x 用)</span><span class="sxs-lookup"><span data-stu-id="88547-190">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="88547-191">libicu55 (16.x 用)</span><span class="sxs-lookup"><span data-stu-id="88547-191">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="88547-192">libicu60 (18.x 用)</span><span class="sxs-lookup"><span data-stu-id="88547-192">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="88547-193">libicu66 (20.x 用)</span><span class="sxs-lookup"><span data-stu-id="88547-193">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="88547-194">libssl1.0.0 (14.x、16.x 用)</span><span class="sxs-lookup"><span data-stu-id="88547-194">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="88547-195">libssl1.1 (18.x、20.x 用)</span><span class="sxs-lookup"><span data-stu-id="88547-195">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="88547-196">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="88547-196">libstdc++6</span></span>
- <span data-ttu-id="88547-197">zlib1g</span><span class="sxs-lookup"><span data-stu-id="88547-197">zlib1g</span></span>

<span data-ttu-id="88547-198">*System.Drawing.Common* アセンブリを使用する .NET アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="88547-198">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="88547-199">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="88547-199">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="88547-200">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="88547-200">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="88547-201">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88547-201">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="88547-202">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="88547-202">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="88547-203">手動インストール</span><span class="sxs-lookup"><span data-stu-id="88547-203">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="88547-204">次の手順</span><span class="sxs-lookup"><span data-stu-id="88547-204">Next steps</span></span>

- [<span data-ttu-id="88547-205">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="88547-205">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
