---
title: Ubuntu に .NET をインストールする - .NET
description: Ubuntu に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 14e5e9548d4aa09a586e2038f3e35a489ee65cd2
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970768"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="ba50c-103">Ubuntu に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="ba50c-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="ba50c-104">.NET は Ubuntu でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ba50c-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="ba50c-105">この記事では、Ubuntu に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ba50c-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="ba50c-106">Ubuntu のバージョンがサポート対象外である場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="ba50c-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="ba50c-107">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="ba50c-107">Supported distributions</span></span>

<span data-ttu-id="ba50c-108">次の表は、現在サポートされている .NET リリースと、それらがサポートされている Ubuntu のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ba50c-108">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="ba50c-109">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Ubuntu のバージョンが期限切れになる](https://wiki.ubuntu.com/Releases)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ba50c-109">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="ba50c-110">✔️ は、Ubuntu または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="ba50c-110">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="ba50c-111">❌ は、Ubuntu または .NET のバージョンがその Ubuntu のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="ba50c-111">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="ba50c-112">Ubuntu のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ba50c-112">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="ba50c-113">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="ba50c-113">Ubuntu</span></span>                   | <span data-ttu-id="ba50c-114">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-114">.NET Core 2.1</span></span> | <span data-ttu-id="ba50c-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-115">.NET Core 3.1</span></span> | <span data-ttu-id="ba50c-116">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-116">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="ba50c-117">✔️ [20.10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-117">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="ba50c-118">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-118">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-119">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-119">✔️ 3.1</span></span>        | <span data-ttu-id="ba50c-120">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-120">✔️ 5.0</span></span> |
| <span data-ttu-id="ba50c-121">✔️ [20.04 (LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-121">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="ba50c-122">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-122">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-123">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-123">✔️ 3.1</span></span>        | <span data-ttu-id="ba50c-124">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-124">✔️ 5.0</span></span> |
| <span data-ttu-id="ba50c-125">❌ [19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-125">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="ba50c-126">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-126">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-127">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-127">✔️ 3.1</span></span>        | <span data-ttu-id="ba50c-128">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-128">✔️ 5.0</span></span> |
| <span data-ttu-id="ba50c-129">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-129">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="ba50c-130">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-130">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-131">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-131">✔️ 3.1</span></span>        | <span data-ttu-id="ba50c-132">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-132">❌ 5.0</span></span> |
| <span data-ttu-id="ba50c-133">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-133">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="ba50c-134">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-134">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-135">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-135">❌ 3.1</span></span>        | <span data-ttu-id="ba50c-136">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-136">❌ 5.0</span></span> |
| <span data-ttu-id="ba50c-137">✔️ [18.04 (LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-137">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="ba50c-138">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-138">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-139">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-139">✔️ 3.1</span></span>        | <span data-ttu-id="ba50c-140">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-140">✔️ 5.0</span></span> |
| <span data-ttu-id="ba50c-141">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-141">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="ba50c-142">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-142">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-143">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-143">❌ 3.1</span></span>        | <span data-ttu-id="ba50c-144">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-144">❌ 5.0</span></span> |
| <span data-ttu-id="ba50c-145">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-145">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="ba50c-146">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-146">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-147">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-147">❌ 3.1</span></span>        | <span data-ttu-id="ba50c-148">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-148">❌ 5.0</span></span> |
| <span data-ttu-id="ba50c-149">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-149">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="ba50c-150">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-150">❌ 2.1</span></span>        | <span data-ttu-id="ba50c-151">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-151">❌ 3.1</span></span>        | <span data-ttu-id="ba50c-152">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-152">❌ 5.0</span></span> |
| <span data-ttu-id="ba50c-153">✔️ [16.04 (LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="ba50c-153">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="ba50c-154">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-154">✔️ 2.1</span></span>        | <span data-ttu-id="ba50c-155">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="ba50c-155">✔️ 3.1</span></span>        | <span data-ttu-id="ba50c-156">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-156">✔️ 5.0</span></span> |

<span data-ttu-id="ba50c-157">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="ba50c-157">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="ba50c-158">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="ba50c-158">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ba50c-159">3.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-159">3.0</span></span>
- <span data-ttu-id="ba50c-160">2.2</span><span class="sxs-lookup"><span data-stu-id="ba50c-160">2.2</span></span>
- <span data-ttu-id="ba50c-161">2.0</span><span class="sxs-lookup"><span data-stu-id="ba50c-161">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="ba50c-162">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="ba50c-162">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="2010-"></a><span data-ttu-id="ba50c-163">20.10 ✔️</span><span class="sxs-lookup"><span data-stu-id="ba50c-163">20.10 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="ba50c-164">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="ba50c-164">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="ba50c-165">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ba50c-165">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="ba50c-166">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="ba50c-166">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="ba50c-167">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ba50c-167">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="ba50c-168">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="ba50c-168">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="ba50c-169">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ba50c-169">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="ba50c-170">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="ba50c-170">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="ba50c-171">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="ba50c-171">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="ba50c-172">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="ba50c-172">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ba50c-173">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="ba50c-173">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="use-apt-to-update-net"></a><span data-ttu-id="ba50c-174">APT を使用して .NET を更新する</span><span class="sxs-lookup"><span data-stu-id="ba50c-174">Use APT to update .NET</span></span>

<span data-ttu-id="ba50c-175">.NET で新しい修正プログラムのリリースを利用できる場合は、次のコマンドを使用して、APT で簡単にアップグレードすることができます。</span><span class="sxs-lookup"><span data-stu-id="ba50c-175">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="ba50c-176">APT のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ba50c-176">APT troubleshooting</span></span>

<span data-ttu-id="ba50c-177">このセクションでは、APT を使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ba50c-177">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="ba50c-178">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="ba50c-178">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="ba50c-179">見つからない \\ 一部のパッケージをインストールできませんでした</span><span class="sxs-lookup"><span data-stu-id="ba50c-179">Unable to locate \\ Some packages could not be installed</span></span>

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

### <a name="failed-to-fetch"></a><span data-ttu-id="ba50c-180">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="ba50c-180">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="dependencies"></a><span data-ttu-id="ba50c-181">依存関係</span><span class="sxs-lookup"><span data-stu-id="ba50c-181">Dependencies</span></span>

<span data-ttu-id="ba50c-182">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ba50c-182">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="ba50c-183">ただし、手動で .NET をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba50c-183">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="ba50c-184">libc6</span><span class="sxs-lookup"><span data-stu-id="ba50c-184">libc6</span></span>
- <span data-ttu-id="ba50c-185">libgcc1</span><span class="sxs-lookup"><span data-stu-id="ba50c-185">libgcc1</span></span>
- <span data-ttu-id="ba50c-186">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="ba50c-186">libgssapi-krb5-2</span></span>
- <span data-ttu-id="ba50c-187">libicu52 (14.x 用)</span><span class="sxs-lookup"><span data-stu-id="ba50c-187">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="ba50c-188">libicu55 (16.x 用)</span><span class="sxs-lookup"><span data-stu-id="ba50c-188">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="ba50c-189">libicu60 (18.x 用)</span><span class="sxs-lookup"><span data-stu-id="ba50c-189">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="ba50c-190">libicu66 (20.x 用)</span><span class="sxs-lookup"><span data-stu-id="ba50c-190">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="ba50c-191">libssl1.0.0 (14.x、16.x 用)</span><span class="sxs-lookup"><span data-stu-id="ba50c-191">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="ba50c-192">libssl1.1 (18.x、20.x 用)</span><span class="sxs-lookup"><span data-stu-id="ba50c-192">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="ba50c-193">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="ba50c-193">libstdc++6</span></span>
- <span data-ttu-id="ba50c-194">zlib1g</span><span class="sxs-lookup"><span data-stu-id="ba50c-194">zlib1g</span></span>

<span data-ttu-id="ba50c-195">*System.Drawing.Common* アセンブリを使用する .NET アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="ba50c-195">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="ba50c-196">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="ba50c-196">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="ba50c-197">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="ba50c-197">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="ba50c-198">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba50c-198">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ba50c-199">次の手順</span><span class="sxs-lookup"><span data-stu-id="ba50c-199">Next steps</span></span>

- [<span data-ttu-id="ba50c-200">.NET CLI のタブ補完を有効にする方法</span><span class="sxs-lookup"><span data-stu-id="ba50c-200">How to enable TAB completion for the .NET CLI</span></span>](../tools/enable-tab-autocomplete.md)
- [<span data-ttu-id="ba50c-201">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="ba50c-201">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
