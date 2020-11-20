---
title: RHEL に .NET をインストールする - .NET
description: RHEL に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: cb03f84cf84557d467f0a067b8d5629a843ec7e3
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594585"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="75e09-103">RHEL に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="75e09-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="75e09-104">.NET は RHEL でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="75e09-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="75e09-105">この記事では、RHEL に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="75e09-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="75e09-106">ご利用の Red Hat サブスクリプションを登録する</span><span class="sxs-lookup"><span data-stu-id="75e09-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="75e09-107">Red Hat から RHEL に .NET をインストールするには、まず、Red Hat Subscription Manager を使用して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="75e09-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="75e09-108">ご利用のシステムでまだこれを行っていない場合、または不明な場合は、[.NET 向けの Red Hat の製品ドキュメント](https://access.redhat.com/documentation/net/5.0/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75e09-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="75e09-109">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="75e09-109">Supported distributions</span></span>

<span data-ttu-id="75e09-110">RHEL 7 と RHEL 8 の両方で現在サポートされている .NET のリリースの一覧は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="75e09-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="75e09-111">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、RHEL のバージョンがサポート終了になるまでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="75e09-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="75e09-112">✔️ は、RHEL または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="75e09-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="75e09-113">❌ は、RHEL または .NET のバージョンがその RHEL のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="75e09-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="75e09-114">RHEL のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="75e09-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="75e09-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="75e09-115">RHEL</span></span>                     | <span data-ttu-id="75e09-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="75e09-116">.NET Core 2.1</span></span> | <span data-ttu-id="75e09-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="75e09-117">.NET Core 3.1</span></span> | <span data-ttu-id="75e09-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="75e09-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="75e09-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="75e09-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="75e09-120">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="75e09-120">✔️ 2.1</span></span>        | <span data-ttu-id="75e09-121">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="75e09-121">✔️ 3.1</span></span>        | <span data-ttu-id="75e09-122">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="75e09-122">✔️ 5.0</span></span> |
| <span data-ttu-id="75e09-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="75e09-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="75e09-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="75e09-124">✔️ 2.1</span></span>        | <span data-ttu-id="75e09-125">✔️ [3.1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="75e09-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="75e09-126">✔️ [5.0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="75e09-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="75e09-127">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="75e09-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="75e09-128">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="75e09-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="75e09-129">3.0</span><span class="sxs-lookup"><span data-stu-id="75e09-129">3.0</span></span>
- <span data-ttu-id="75e09-130">2.2</span><span class="sxs-lookup"><span data-stu-id="75e09-130">2.2</span></span>
- <span data-ttu-id="75e09-131">2.0</span><span class="sxs-lookup"><span data-stu-id="75e09-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="75e09-132">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="75e09-132">How to install other versions</span></span>

<span data-ttu-id="75e09-133">.NET の他のリリースをインストールするために必要な手順については、[.NET 向けの Red Hat のドキュメント](https://access.redhat.com/documentation/net/5.0/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="75e09-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="75e09-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="75e09-134">RHEL 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="75e09-135">.NET 5.0 は、AppStream のリポジトリにはまだありませんが、.NET Core 3.1 はあります。</span><span class="sxs-lookup"><span data-stu-id="75e09-135">.NET 5.0 isn't yet available in the AppStream repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="75e09-136">.NET Core 3.1 をインストールするには、`aspnetcore-runtime-3.1` や `dotnet-sdk-3.1` などの適切なパッケージで `dnf install` コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="75e09-136">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="75e09-137">以下の手順は .NET 5.0 の場合です。</span><span class="sxs-lookup"><span data-stu-id="75e09-137">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/8/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="75e09-138">RHEL 7 ✔️ .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="75e09-138">RHEL 7 ✔️ .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-yum.md)]

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="75e09-139">RHEL 7 ✔️ .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="75e09-139">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="75e09-140">次のコマンドでは、`scl-utils` パッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="75e09-140">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="75e09-141">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="75e09-141">Install the SDK</span></span>

<span data-ttu-id="75e09-142">.NET Core SDK を使用すると、.NET Core を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="75e09-142">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="75e09-143">.NET Core SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="75e09-143">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="75e09-144">.NET Core SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="75e09-144">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="75e09-145">Red Hat では、`rh-dotnet31` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="75e09-145">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="75e09-146">たとえば、`rh-dotnet31` には、ベースとなる RHEL のバージョンとは異なるバージョンの `libcurl` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="75e09-146">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="75e09-147">これにより、異なるバージョンの `libcurl` を想定していないプログラムで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75e09-147">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="75e09-148">`rh-dotnet` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="75e09-148">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="75e09-149">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="75e09-149">Install the runtime</span></span>

<span data-ttu-id="75e09-150">.NET Core ランタイムを使用すると、ランタイムを含まない .NET Core を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="75e09-150">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="75e09-151">次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="75e09-151">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="75e09-152">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="75e09-152">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="75e09-153">Red Hat では、`rh-dotnet31-aspnetcore-runtime-3.1` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="75e09-153">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="75e09-154">たとえば、`rh-dotnet31-aspnetcore-runtime-3.1` には、ベースとなる RHEL のバージョンとは異なるバージョンの `libcurl` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="75e09-154">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="75e09-155">これにより、異なるバージョンの `libcurl` を想定していないプログラムで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="75e09-155">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="75e09-156">`rh-dotnet31-aspnetcore-runtime-3.1` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="75e09-156">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="75e09-157">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET Core ランタイムをインストールできます。それには、前述のコマンドの `rh-dotnet31-aspnetcore-runtime-3.1` を `rh-dotnet31-dotnet-runtime-3.1` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="75e09-157">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="75e09-158">Snap</span><span class="sxs-lookup"><span data-stu-id="75e09-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="75e09-159">依存関係</span><span class="sxs-lookup"><span data-stu-id="75e09-159">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="75e09-160">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="75e09-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="75e09-161">手動インストール</span><span class="sxs-lookup"><span data-stu-id="75e09-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="75e09-162">次の手順</span><span class="sxs-lookup"><span data-stu-id="75e09-162">Next steps</span></span>

- [<span data-ttu-id="75e09-163">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="75e09-163">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
