---
title: CentOS に .NET をインストールする - .NET
description: CentOS に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b2ed62d024c6f0d78a4ec64693f1dafeabd8f47b
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594633"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-centos"></a><span data-ttu-id="f8c4f-103">CentOS に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="f8c4f-103">Install the .NET SDK or the .NET Runtime on CentOS</span></span>

<span data-ttu-id="f8c4f-104">.NET は CentOS でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-104">.NET is supported on CentOS.</span></span> <span data-ttu-id="f8c4f-105">この記事では、CentOS に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-105">This article describes how to install .NET on CentOS.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="f8c4f-106">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="f8c4f-106">Supported distributions</span></span>

<span data-ttu-id="f8c4f-107">CentOS 7 と CentOS 8 の両方で現在サポートされている .NET のリリースの一覧は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-107">The following table is a list of currently supported .NET releases on both CentOS 7 and CentOS 8.</span></span> <span data-ttu-id="f8c4f-108">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、CentOS のバージョンがサポート終了になるまでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of CentOS is no longer supported.</span></span>

- <span data-ttu-id="f8c4f-109">✔️ は、CentOS または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-109">A ✔️ indicates that the version of CentOS or .NET is still supported.</span></span>
- <span data-ttu-id="f8c4f-110">❌ は、CentOS または .NET のバージョンがその CentOS のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-110">A ❌ indicates that the version of CentOS or .NET isn't supported on that CentOS release.</span></span>
- <span data-ttu-id="f8c4f-111">CentOS のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-111">When both a version of CentOS and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="f8c4f-112">CentOS</span><span class="sxs-lookup"><span data-stu-id="f8c4f-112">CentOS</span></span>                   | <span data-ttu-id="f8c4f-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="f8c4f-113">.NET Core 2.1</span></span> | <span data-ttu-id="f8c4f-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="f8c4f-114">.NET Core 3.1</span></span> | <span data-ttu-id="f8c4f-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f8c4f-115">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="f8c4f-116">✔️ [8](#centos-8-)</span><span class="sxs-lookup"><span data-stu-id="f8c4f-116">✔️ [8](#centos-8-)</span></span> | <span data-ttu-id="f8c4f-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f8c4f-117">✔️ 2.1</span></span>        | <span data-ttu-id="f8c4f-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f8c4f-118">✔️ 3.1</span></span>        | <span data-ttu-id="f8c4f-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="f8c4f-119">✔️ 5.0</span></span> |
| <span data-ttu-id="f8c4f-120">✔️ [7](#centos-7-)</span><span class="sxs-lookup"><span data-stu-id="f8c4f-120">✔️ [7](#centos-7-)</span></span> | <span data-ttu-id="f8c4f-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="f8c4f-121">✔️ 2.1</span></span>        | <span data-ttu-id="f8c4f-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="f8c4f-122">✔️ 3.1</span></span>        | <span data-ttu-id="f8c4f-123">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="f8c4f-123">✔️ 5.0</span></span> |

<span data-ttu-id="f8c4f-124">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-124">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="f8c4f-125">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="f8c4f-126">3.0</span><span class="sxs-lookup"><span data-stu-id="f8c4f-126">3.0</span></span>
- <span data-ttu-id="f8c4f-127">2.2</span><span class="sxs-lookup"><span data-stu-id="f8c4f-127">2.2</span></span>
- <span data-ttu-id="f8c4f-128">2.0</span><span class="sxs-lookup"><span data-stu-id="f8c4f-128">2.0</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="f8c4f-129">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="f8c4f-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="centos-8-"></a><span data-ttu-id="f8c4f-130">CentOS 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="f8c4f-130">CentOS 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="f8c4f-131">.NET 5.0 は、既定のパッケージ リポジトリにはまだありませんが、.NET Core 3.1 はあります。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-131">.NET 5.0 isn't yet available in the default package repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="f8c4f-132">.NET Core 3.1 をインストールするには、`aspnetcore-runtime-3.1` や `dotnet-sdk-3.1` などの適切なパッケージで `dnf install` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-132">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="f8c4f-133">以下の手順は .NET 5.0 の場合です。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-133">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/8/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="centos-7-"></a><span data-ttu-id="f8c4f-134">CentOS 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="f8c4f-134">CentOS 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-yum-install-50](includes/linux-install-50-yum.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="f8c4f-135">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="f8c4f-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="f8c4f-136">このセクションでは、パッケージ マネージャーを使用して .NET をインストールするときに発生する可能性のある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f8c4f-136">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="f8c4f-137">パッケージが見つからない</span><span class="sxs-lookup"><span data-stu-id="f8c4f-137">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="f8c4f-138">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="f8c4f-138">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="f8c4f-139">Snap</span><span class="sxs-lookup"><span data-stu-id="f8c4f-139">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="f8c4f-140">依存関係</span><span class="sxs-lookup"><span data-stu-id="f8c4f-140">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="f8c4f-141">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="f8c4f-141">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="f8c4f-142">手動インストール</span><span class="sxs-lookup"><span data-stu-id="f8c4f-142">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="f8c4f-143">次の手順</span><span class="sxs-lookup"><span data-stu-id="f8c4f-143">Next steps</span></span>

- [<span data-ttu-id="f8c4f-144">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="f8c4f-144">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
