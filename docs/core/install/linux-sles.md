---
title: SLES 上に .NET をインストールする - .NET
description: SLES に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 558574116aac2a3c755481069641e81a435a2a43
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506865"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-sles"></a><span data-ttu-id="32189-103">SLES に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="32189-103">Install the .NET SDK or the .NET Runtime on SLES</span></span>

<span data-ttu-id="32189-104">.NET は SLES 上でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="32189-104">.NET is supported on SLES.</span></span> <span data-ttu-id="32189-105">この記事では、SLES 上に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="32189-105">This article describes how to install .NET on SLES.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a><span data-ttu-id="32189-106">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="32189-106">Supported distributions</span></span>

<span data-ttu-id="32189-107">次の表は、SLES 12 SP2 と SLES 15 の両方で現在サポートされている .NET リリースの一覧です。</span><span class="sxs-lookup"><span data-stu-id="32189-107">The following table is a list of currently supported .NET releases on both SLES 12 SP2 and SLES 15.</span></span> <span data-ttu-id="32189-108">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、SLES のバージョンがサポート終了になるまでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="32189-108">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of SLES is no longer supported.</span></span>

- <span data-ttu-id="32189-109">✔️ は、SLES または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="32189-109">A ✔️ indicates that the version of SLES or .NET is still supported.</span></span>
- <span data-ttu-id="32189-110">❌ は、SLES または .NET のバージョンがその SLES のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="32189-110">A ❌ indicates that the version of SLES or .NET isn't supported on that SLES release.</span></span>
- <span data-ttu-id="32189-111">SLES のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="32189-111">When both a version of SLES and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="32189-112">SLES</span><span class="sxs-lookup"><span data-stu-id="32189-112">SLES</span></span>                   | <span data-ttu-id="32189-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="32189-113">.NET Core 2.1</span></span> | <span data-ttu-id="32189-114">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="32189-114">.NET Core 3.1</span></span> | <span data-ttu-id="32189-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="32189-115">.NET 5.0</span></span> |
|------------------------|---------------|---------------|----------------|
| <span data-ttu-id="32189-116">✔️ [15](#sles-15-)</span><span class="sxs-lookup"><span data-stu-id="32189-116">✔️ [15](#sles-15-)</span></span>     | <span data-ttu-id="32189-117">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="32189-117">✔️ 2.1</span></span>        | <span data-ttu-id="32189-118">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="32189-118">✔️ 3.1</span></span>        | <span data-ttu-id="32189-119">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="32189-119">✔️ 5.0</span></span> |
| <span data-ttu-id="32189-120">✔️ [12 SP2](#sles-12-)</span><span class="sxs-lookup"><span data-stu-id="32189-120">✔️ [12 SP2](#sles-12-)</span></span> | <span data-ttu-id="32189-121">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="32189-121">✔️ 2.1</span></span>        | <span data-ttu-id="32189-122">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="32189-122">✔️ 3.1</span></span>        | <span data-ttu-id="32189-123">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="32189-123">✔️ 5.0</span></span> |

<span data-ttu-id="32189-124">次のバージョンの .NET Core は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="32189-124">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="32189-125">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="32189-125">The downloads for these still remain published:</span></span>

- <span data-ttu-id="32189-126">3.0</span><span class="sxs-lookup"><span data-stu-id="32189-126">3.0</span></span>
- <span data-ttu-id="32189-127">2.2</span><span class="sxs-lookup"><span data-stu-id="32189-127">2.2</span></span>
- <span data-ttu-id="32189-128">2.0</span><span class="sxs-lookup"><span data-stu-id="32189-128">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="32189-129">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="32189-129">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a><span data-ttu-id="32189-130">SLES 15 ✔️</span><span class="sxs-lookup"><span data-stu-id="32189-130">SLES 15 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="32189-131">現時点では、SLES 15 Microsoft リポジトリ セットアップ パッケージによって "*microsoft-prod.repo*" ファイルが間違ったディレクトリにインストールされるため、zypper が .NET パッケージを見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="32189-131">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET packages.</span></span> <span data-ttu-id="32189-132">この問題を解決するには、正しいディレクトリにシンボリックリンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="32189-132">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="sles-12-"></a><span data-ttu-id="32189-133">SLES 12 ✔️</span><span class="sxs-lookup"><span data-stu-id="32189-133">SLES 12 ✔️</span></span>

<span data-ttu-id="32189-134">.NET では、SLES 12 ファミリの最小要件として SP2 が必要です。</span><span class="sxs-lookup"><span data-stu-id="32189-134">.NET requires SP2 as a minimum for the SLES 12 family.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-50](includes/linux-install-50-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="32189-135">パッケージ マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="32189-135">Troubleshoot the package manager</span></span>

<span data-ttu-id="32189-136">このセクションでは、パッケージ マネージャーを使用して .NET をインストールするときに発生するおそれがある一般的なエラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="32189-136">This section provides information on common errors you may get while using the package manager to install .NET.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="32189-137">フェッチできない</span><span class="sxs-lookup"><span data-stu-id="32189-137">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a><span data-ttu-id="32189-138">依存関係</span><span class="sxs-lookup"><span data-stu-id="32189-138">Dependencies</span></span>

<span data-ttu-id="32189-139">パッケージ マネージャーを使用してインストールする場合、次のライブラリが自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="32189-139">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="32189-140">ただし、手動で .NET をインストールする場合、または自己完結型アプリを公開する場合は、次のライブラリがインストールされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32189-140">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="32189-141">krb5</span><span class="sxs-lookup"><span data-stu-id="32189-141">krb5</span></span>
- <span data-ttu-id="32189-142">libicu</span><span class="sxs-lookup"><span data-stu-id="32189-142">libicu</span></span>
- <span data-ttu-id="32189-143">libopenssl1_1</span><span class="sxs-lookup"><span data-stu-id="32189-143">libopenssl1_1</span></span>

<span data-ttu-id="32189-144">ターゲット ランタイム環境の OpenSSL バージョンが 1.1 以降である場合は、**compat-openssl10** をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="32189-144">If the target runtime environment's OpenSSL version is 1.1 or newer, you'll need to install **compat-openssl10**.</span></span>

<span data-ttu-id="32189-145">依存関係の詳細については、「[Self-contained Linux applications](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)」(自己完結型 Linux アプリケーション) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32189-145">For more information about the dependencies, see [Self-contained Linux apps](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).</span></span>

<span data-ttu-id="32189-146">*System.Drawing.Common* アセンブリを使用する .NET アプリの場合は、次の依存関係も必要です。</span><span class="sxs-lookup"><span data-stu-id="32189-146">For .NET apps that use the *System.Drawing.Common* assembly, you'll also need the following dependency:</span></span>

- [<span data-ttu-id="32189-147">libgdiplus (バージョン 6.0.1 以降)</span><span class="sxs-lookup"><span data-stu-id="32189-147">libgdiplus (version 6.0.1 or later)</span></span>](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > <span data-ttu-id="32189-148">最新バージョンの *libgdiplus* をインストールするには、システムに Mono リポジトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="32189-148">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="32189-149">詳細については、「<https://www.mono-project.com/download/stable/>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32189-149">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="32189-150">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="32189-150">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="32189-151">手動インストール</span><span class="sxs-lookup"><span data-stu-id="32189-151">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="32189-152">次の手順</span><span class="sxs-lookup"><span data-stu-id="32189-152">Next steps</span></span>

- [<span data-ttu-id="32189-153">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="32189-153">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
