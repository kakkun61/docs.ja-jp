---
title: Fedora に .NET をインストールする - .NET
description: Fedora に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: f7422941af7e39d69d286a0f79920b025c1bf9c0
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031905"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="a05c6-103">Fedora に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="a05c6-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="a05c6-104">.NET は Fedora でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a05c6-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="a05c6-105">この記事では、Fedora に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a05c6-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="a05c6-106">Fedora のバージョンがサポート対象外となった場合、.NET もそのバージョンでサポート対象外となります。</span><span class="sxs-lookup"><span data-stu-id="a05c6-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="a05c6-107">ただし、サポート対象外となった場合でも、ここで説明する手順がそれらのバージョンの .NET の実行に役立つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="a05c6-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="a05c6-108">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="a05c6-108">Supported distributions</span></span>

<span data-ttu-id="a05c6-109">現在サポートされている .NET リリースと、それらがサポートされている Fedora のバージョンの一覧は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a05c6-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="a05c6-110">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、[Fedora のバージョンがサポート終了になる](https://fedoraproject.org/wiki/End_of_life)までサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a05c6-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="a05c6-111">✔️ は、Fedora または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="a05c6-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="a05c6-112">❌ は、Fedora または .NET のバージョンがその Fedora のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="a05c6-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="a05c6-113">Fedora のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a05c6-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="a05c6-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="a05c6-114">Fedora</span></span>               | <span data-ttu-id="a05c6-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-115">.NET Core 2.1</span></span> | <span data-ttu-id="a05c6-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-116">.NET Core 3.1</span></span> | <span data-ttu-id="a05c6-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="a05c6-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="a05c6-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="a05c6-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-119">✔️ 2.1</span></span>        | <span data-ttu-id="a05c6-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-120">✔️ 3.1</span></span>        | <span data-ttu-id="a05c6-121">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-121">✔️ 5.0</span></span> |
| <span data-ttu-id="a05c6-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="a05c6-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="a05c6-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-123">✔️ 2.1</span></span>        | <span data-ttu-id="a05c6-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-124">✔️ 3.1</span></span>        | <span data-ttu-id="a05c6-125">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-125">✔️ 5.0</span></span> |
| <span data-ttu-id="a05c6-126">❌ [31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="a05c6-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="a05c6-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-127">✔️ 2.1</span></span>        | <span data-ttu-id="a05c6-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-128">✔️ 3.1</span></span>        | <span data-ttu-id="a05c6-129">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-129">❌ 5.0</span></span> |
| <span data-ttu-id="a05c6-130">❌ [30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="a05c6-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="a05c6-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-131">✔️ 2.1</span></span>        | <span data-ttu-id="a05c6-132">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-132">✔️ 3.1</span></span>        | <span data-ttu-id="a05c6-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-133">❌ 5.0</span></span> |
| <span data-ttu-id="a05c6-134">❌ [29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="a05c6-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="a05c6-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-135">✔️ 2.1</span></span>        | <span data-ttu-id="a05c6-136">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-136">✔️ 3.1</span></span>        | <span data-ttu-id="a05c6-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-137">❌ 5.0</span></span> |
| <span data-ttu-id="a05c6-138">❌ [28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="a05c6-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="a05c6-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-139">✔️ 2.1</span></span>        | <span data-ttu-id="a05c6-140">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-140">❌ 3.1</span></span>        | <span data-ttu-id="a05c6-141">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-141">❌ 5.0</span></span> |
| <span data-ttu-id="a05c6-142">❌ [27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="a05c6-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="a05c6-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-143">✔️ 2.1</span></span>        | <span data-ttu-id="a05c6-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="a05c6-144">❌ 3.1</span></span>        | <span data-ttu-id="a05c6-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-145">❌ 5.0</span></span> |

<span data-ttu-id="a05c6-146">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="a05c6-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="a05c6-147">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="a05c6-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="a05c6-148">3.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-148">3.0</span></span>
- <span data-ttu-id="a05c6-149">2.2</span><span class="sxs-lookup"><span data-stu-id="a05c6-149">2.2</span></span>
- <span data-ttu-id="a05c6-150">2.0</span><span class="sxs-lookup"><span data-stu-id="a05c6-150">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="a05c6-151">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="a05c6-151">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a05c6-152">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="a05c6-152">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="a05c6-153">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="a05c6-153">Fedora 33 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="a05c6-154">.NET Core 3.1 は Fedora 33 の既定のパッケージ リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="a05c6-154">.NET Core 3.1 is available in the default package repositories for Fedora 33.</span></span> <span data-ttu-id="a05c6-155">.NET Core 3.1 をインストールするには、`aspnetcore-runtime-3.1` や `dotnet-sdk-3.1` などの適切なパッケージで `dnf install` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a05c6-155">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="a05c6-156">.NET 5.0 は、既定のパッケージ リポジトリにはまだありません。</span><span class="sxs-lookup"><span data-stu-id="a05c6-156">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="a05c6-157">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="a05c6-157">Fedora 32 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="a05c6-158">.NET Core 3.1 は Fedora 32 の既定のパッケージ リポジトリで利用できます。</span><span class="sxs-lookup"><span data-stu-id="a05c6-158">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span> <span data-ttu-id="a05c6-159">.NET Core 3.1 をインストールするには、`aspnetcore-runtime-3.1` や `dotnet-sdk-3.1` などの適切なパッケージで `dnf install` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a05c6-159">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="a05c6-160">.NET 5.0 は、既定のパッケージ リポジトリにはまだありません。</span><span class="sxs-lookup"><span data-stu-id="a05c6-160">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="a05c6-161">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="a05c6-161">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="a05c6-162">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="a05c6-162">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="a05c6-163">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="a05c6-163">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="a05c6-164">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="a05c6-164">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="a05c6-165">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="a05c6-165">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a05c6-166">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="a05c6-166">Troubleshoot the package manager</span></span>

<span data-ttu-id="a05c6-167">このセクションでは、パッケージ マネージャーを使用して .NET Core をインストールするときに発生する可能性のある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a05c6-167">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="a05c6-168">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="a05c6-168">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="a05c6-169">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="a05c6-169">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="a05c6-170">Snap</span><span class="sxs-lookup"><span data-stu-id="a05c6-170">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="a05c6-171">依存関係</span><span class="sxs-lookup"><span data-stu-id="a05c6-171">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="a05c6-172">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="a05c6-172">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="a05c6-173">手動インストール</span><span class="sxs-lookup"><span data-stu-id="a05c6-173">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="a05c6-174">次の手順</span><span class="sxs-lookup"><span data-stu-id="a05c6-174">Next steps</span></span>

- [<span data-ttu-id="a05c6-175">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="a05c6-175">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
