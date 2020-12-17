---
title: RHEL に .NET をインストールする - .NET
description: RHEL に .NET SDK と .NET ランタイムをインストールするさまざまな方法を示します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 0b6138185bfd3e2f50c1b31e82779165715a5b6e
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851641"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="ed27d-103">RHEL に .NET SDK または .NET ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="ed27d-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="ed27d-104">.NET は RHEL でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ed27d-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="ed27d-105">この記事では、RHEL に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="ed27d-106">ご利用の Red Hat サブスクリプションを登録する</span><span class="sxs-lookup"><span data-stu-id="ed27d-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="ed27d-107">Red Hat から RHEL に .NET をインストールするには、まず、Red Hat Subscription Manager を使用して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed27d-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="ed27d-108">ご利用のシステムでまだこれを行っていない場合、または不明な場合は、[.NET 向けの Red Hat の製品ドキュメント](https://access.redhat.com/documentation/net/5.0/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed27d-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="ed27d-109">サポートされているディストリビューション</span><span class="sxs-lookup"><span data-stu-id="ed27d-109">Supported distributions</span></span>

<span data-ttu-id="ed27d-110">RHEL 7 と RHEL 8 の両方で現在サポートされている .NET のリリースの一覧は、次の表のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ed27d-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="ed27d-111">これらのバージョンは、[.NET のバージョンがサポート終了になる](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)か、RHEL のバージョンがサポート終了になるまでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="ed27d-112">✔️ は、RHEL または .NET のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="ed27d-113">❌ は、RHEL または .NET のバージョンがその RHEL のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="ed27d-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="ed27d-114">RHEL のバージョンと .NET のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="ed27d-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="ed27d-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="ed27d-115">RHEL</span></span>                     | <span data-ttu-id="ed27d-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ed27d-116">.NET Core 2.1</span></span> | <span data-ttu-id="ed27d-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ed27d-117">.NET Core 3.1</span></span> | <span data-ttu-id="ed27d-118">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="ed27d-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="ed27d-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="ed27d-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="ed27d-120">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ed27d-120">✔️ 2.1</span></span>        | <span data-ttu-id="ed27d-121">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="ed27d-121">✔️ 3.1</span></span>        | <span data-ttu-id="ed27d-122">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="ed27d-122">✔️ 5.0</span></span> |
| <span data-ttu-id="ed27d-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="ed27d-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="ed27d-124">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="ed27d-124">✔️ 2.1</span></span>        | <span data-ttu-id="ed27d-125">✔️ [3.1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="ed27d-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="ed27d-126">✔️ [5.0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="ed27d-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="ed27d-127">次のバージョンの .NET は、サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="ed27d-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="ed27d-128">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="ed27d-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ed27d-129">3.0</span><span class="sxs-lookup"><span data-stu-id="ed27d-129">3.0</span></span>
- <span data-ttu-id="ed27d-130">2.2</span><span class="sxs-lookup"><span data-stu-id="ed27d-130">2.2</span></span>
- <span data-ttu-id="ed27d-131">2.0</span><span class="sxs-lookup"><span data-stu-id="ed27d-131">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="ed27d-132">プレビュー バージョンの削除</span><span class="sxs-lookup"><span data-stu-id="ed27d-132">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ed27d-133">その他のバージョンをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="ed27d-133">How to install other versions</span></span>

<span data-ttu-id="ed27d-134">.NET の他のリリースをインストールするために必要な手順については、[.NET 向けの Red Hat のドキュメント](https://access.redhat.com/documentation/net/5.0/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed27d-134">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="ed27d-135">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="ed27d-135">RHEL 8 ✔️</span></span>

<span data-ttu-id="ed27d-136">.NET は、RHEL 8 用の AppStream リポジトリに含まれています。</span><span class="sxs-lookup"><span data-stu-id="ed27d-136">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="ed27d-137">RHEL 7 ✔️ .NET 5.0</span><span class="sxs-lookup"><span data-stu-id="ed27d-137">RHEL 7 ✔️ .NET 5.0</span></span>

<span data-ttu-id="ed27d-138">次のコマンドでは、`scl-utils` パッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-138">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="ed27d-139">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="ed27d-139">Install the SDK</span></span>

<span data-ttu-id="ed27d-140">.NET SDK を使用すると、.NET を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-140">The .NET SDK allows you to develop apps with .NET .</span></span> <span data-ttu-id="ed27d-141">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ed27d-141">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="ed27d-142">.NET SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-142">To install .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="ed27d-143">Red Hat では、`rh-dotnet50` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="ed27d-143">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="ed27d-144">`rh-dotnet` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-144">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="ed27d-145">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="ed27d-145">Install the runtime</span></span>

<span data-ttu-id="ed27d-146">.NET ランタイムを使用すると、ランタイムを含まない .NET を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-146">The .NET Runtime allows you to run apps that were made with .NET that didn't include the runtime.</span></span> <span data-ttu-id="ed27d-147">次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-147">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="ed27d-148">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-148">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="ed27d-149">Red Hat では、`rh-dotnet50` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="ed27d-149">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="ed27d-150">`rh-dotnet50` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-150">If you want to enable `rh-dotnet50` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

<span data-ttu-id="ed27d-151">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET ランタイムをインストールできます。それには、前述のコマンドの `rh-dotnet50-aspnetcore-runtime-5.0` を `rh-dotnet50-dotnet-runtime-5.0` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-151">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the commands above with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="ed27d-152">RHEL 7 ✔️ .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ed27d-152">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="ed27d-153">次のコマンドでは、`scl-utils` パッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-153">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="ed27d-154">SDK のインストール</span><span class="sxs-lookup"><span data-stu-id="ed27d-154">Install the SDK</span></span>

<span data-ttu-id="ed27d-155">.NET Core SDK を使用すると、.NET Core を使用してアプリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-155">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="ed27d-156">.NET Core SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ed27d-156">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="ed27d-157">.NET Core SDK をインストールするには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-157">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="ed27d-158">Red Hat では、`rh-dotnet31` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="ed27d-158">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="ed27d-159">たとえば、`rh-dotnet31` には、ベースとなる RHEL のバージョンとは異なるバージョンの `libcurl` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ed27d-159">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="ed27d-160">これにより、異なるバージョンの `libcurl` を想定していないプログラムで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed27d-160">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="ed27d-161">`rh-dotnet` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-161">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="ed27d-162">ランタイムをインストールする</span><span class="sxs-lookup"><span data-stu-id="ed27d-162">Install the runtime</span></span>

<span data-ttu-id="ed27d-163">.NET Core ランタイムを使用すると、ランタイムを含まない .NET Core を使用して作成されたアプリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-163">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="ed27d-164">次のコマンドを実行すると、.NET Core の最も互換性の高いランタイムである ASP.NET Core ランタイムがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-164">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="ed27d-165">ご利用のターミナルで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-165">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="ed27d-166">Red Hat では、`rh-dotnet31` を永続的に有効にすることは推奨されません。他のプログラムに影響を与える可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="ed27d-166">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="ed27d-167">たとえば、`rh-dotnet31` には、ベースとなる RHEL のバージョンとは異なるバージョンの `libcurl` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ed27d-167">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="ed27d-168">これにより、異なるバージョンの `libcurl` を想定していないプログラムで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ed27d-168">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="ed27d-169">`rh-dotnet31` を永続的に有効にする場合は、 _~/.bashrc_ ファイルに次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="ed27d-169">If you want to enable `rh-dotnet31` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

<span data-ttu-id="ed27d-170">ASP.NET Core ランタイムの代替手段として、ASP.NET Core サポートを含まない .NET Core ランタイムをインストールできます。それには、前述のコマンドの `rh-dotnet31-aspnetcore-runtime-3.1` を `rh-dotnet31-dotnet-runtime-3.1` で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ed27d-170">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="ed27d-171">Snap</span><span class="sxs-lookup"><span data-stu-id="ed27d-171">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="ed27d-172">依存関係</span><span class="sxs-lookup"><span data-stu-id="ed27d-172">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="ed27d-173">スクリプトでのインストール</span><span class="sxs-lookup"><span data-stu-id="ed27d-173">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="ed27d-174">手動インストール</span><span class="sxs-lookup"><span data-stu-id="ed27d-174">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="ed27d-175">次の手順</span><span class="sxs-lookup"><span data-stu-id="ed27d-175">Next steps</span></span>

- [<span data-ttu-id="ed27d-176">チュートリアル: Visual Studio Code を使用して .NET SDK でコンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="ed27d-176">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
