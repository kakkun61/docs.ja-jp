---
title: macOS に .NET をインストールする
description: .NET をインストールできる macOS のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 983c5d2c04b87759b898f449bc092161b03c8ace
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594457"
---
# <a name="install-net-on-macos"></a><span data-ttu-id="4e140-103">macOS に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="4e140-103">Install .NET on macOS</span></span>

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

<span data-ttu-id="4e140-107">この記事では、macOS に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4e140-107">In this article, you'll learn how to install .NET on macOS.</span></span> <span data-ttu-id="4e140-108">.NET は、ランタイムと SDK で構成されています。</span><span class="sxs-lookup"><span data-stu-id="4e140-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="4e140-109">ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4e140-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="4e140-110">SDK は、.NET アプリとライブラリの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="4e140-111">.NET ランタイムは、常に SDK と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4e140-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="4e140-112">.NET の最新バージョンは 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="4e140-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="4e140-113">.NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="4e140-113">Download .NET Core</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="4e140-114">サポートされているリリース</span><span class="sxs-lookup"><span data-stu-id="4e140-114">Supported releases</span></span>

<span data-ttu-id="4e140-115">次の表に、現在サポートされている .NET リリースと、それらがサポートされている macOS のバージョンの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="4e140-115">The following table is a list of currently supported .NET releases and the versions of macOS they're supported on.</span></span> <span data-ttu-id="4e140-116">これらのバージョンは、いずれかのバージョンの [.NET がサポート終了に達する](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)まで、サポートされています。</span><span class="sxs-lookup"><span data-stu-id="4e140-116">These versions remain supported either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

- <span data-ttu-id="4e140-117">✔️ は、.NET Core のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="4e140-117">A ✔️ indicates that the version of .NET Core is still supported.</span></span>
- <span data-ttu-id="4e140-118">❌ は、.NET Core のバージョンがサポートされていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="4e140-118">A ❌ indicates that the version of .NET Core isn't supported.</span></span>

| <span data-ttu-id="4e140-119">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="4e140-119">Operating System</span></span>          | <span data-ttu-id="4e140-120">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4e140-120">.NET Core 2.1</span></span> | <span data-ttu-id="4e140-121">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="4e140-121">.NET Core 3.1</span></span> | <span data-ttu-id="4e140-122">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="4e140-122">.NET 5.0</span></span> |
|---------------------------|---------------|---------------|----------------|
| <span data-ttu-id="4e140-123">macOS 10.15 "Catalina"</span><span class="sxs-lookup"><span data-stu-id="4e140-123">macOS 10.15 "Catalina"</span></span>    | <span data-ttu-id="4e140-124">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4e140-124">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4e140-125">✔️ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4e140-125">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4e140-126">✔️ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4e140-126">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4e140-127">macOS 10.14 "Mojave"</span><span class="sxs-lookup"><span data-stu-id="4e140-127">macOS 10.14 "Mojave"</span></span>      | <span data-ttu-id="4e140-128">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4e140-128">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4e140-129">✔️ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4e140-129">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4e140-130">✔️ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4e140-130">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4e140-131">macOS 10.13 "High Sierra"</span><span class="sxs-lookup"><span data-stu-id="4e140-131">macOS 10.13 "High Sierra"</span></span> | <span data-ttu-id="4e140-132">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4e140-132">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4e140-133">✔️ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4e140-133">✔️ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4e140-134">✔️ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4e140-134">✔️ 5.0 ([Release notes][release-notes-50])</span></span> |
| <span data-ttu-id="4e140-135">macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="4e140-135">macOS 10.12 "Sierra"</span></span>      | <span data-ttu-id="4e140-136">✔️ 2.1 ([リリース ノート][release-notes-21])</span><span class="sxs-lookup"><span data-stu-id="4e140-136">✔️ 2.1 ([Release notes][release-notes-21])</span></span> | <span data-ttu-id="4e140-137">❌ 3.1 ([リリース ノート][release-notes-31])</span><span class="sxs-lookup"><span data-stu-id="4e140-137">❌ 3.1 ([Release notes][release-notes-31])</span></span> | <span data-ttu-id="4e140-138">❌ 5.0 ([リリース ノート][release-notes-50])</span><span class="sxs-lookup"><span data-stu-id="4e140-138">❌ 5.0 ([Release notes][release-notes-50])</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="4e140-139">サポートされていないリリース</span><span class="sxs-lookup"><span data-stu-id="4e140-139">Unsupported releases</span></span>

<span data-ttu-id="4e140-140">次のバージョンの .NET は、❌ サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="4e140-140">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="4e140-141">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="4e140-141">The downloads for these still remain published:</span></span>

- <span data-ttu-id="4e140-142">3.0 ([リリース ノート][release-notes-30])</span><span class="sxs-lookup"><span data-stu-id="4e140-142">3.0 ([Release notes][release-notes-30])</span></span>
- <span data-ttu-id="4e140-143">2.2 ([リリース ノート][release-notes-22])</span><span class="sxs-lookup"><span data-stu-id="4e140-143">2.2 ([Release notes][release-notes-22])</span></span>
- <span data-ttu-id="4e140-144">2.0 ([リリース ノート][release-notes-20])</span><span class="sxs-lookup"><span data-stu-id="4e140-144">2.0 ([Release notes][release-notes-20])</span></span>

## <a name="runtime-information"></a><span data-ttu-id="4e140-145">ランタイムに関する情報</span><span class="sxs-lookup"><span data-stu-id="4e140-145">Runtime information</span></span>

<span data-ttu-id="4e140-146">ランタイムは、.NET で作成されたアプリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-146">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="4e140-147">アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="4e140-147">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="4e140-148">ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e140-148">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="4e140-149">macOS には、3 つの異なるランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="4e140-149">There are three different runtimes you can install on macOS:</span></span>

<span data-ttu-id="4e140-150">*ASP.NET Core ランタイム*</span><span class="sxs-lookup"><span data-stu-id="4e140-150">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="4e140-151">ASP.NET Core アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="4e140-151">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="4e140-152">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4e140-152">Includes the .NET runtime.</span></span>

<span data-ttu-id="4e140-153">*.NET ランタイム*</span><span class="sxs-lookup"><span data-stu-id="4e140-153">*.NET runtime*</span></span>\
<span data-ttu-id="4e140-154">このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="4e140-154">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="4e140-155">.NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4e140-155">It's highly recommended that you install *ASP.NET Core runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="4e140-156">.NET ランタイムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="4e140-156">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="4e140-157">SDK に関する情報</span><span class="sxs-lookup"><span data-stu-id="4e140-157">SDK information</span></span>

<span data-ttu-id="4e140-158">SDK は、.NET アプリとライブラリを作成して公開するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-158">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="4e140-159">SDK のインストールには、次の両方の[ランタイム](#runtime-information)が含まれます: ASP.NET Core と .NET。</span><span class="sxs-lookup"><span data-stu-id="4e140-159">Installing the SDK includes both [runtimes](#runtime-information): ASP.NET Core and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="4e140-160">依存関係</span><span class="sxs-lookup"><span data-stu-id="4e140-160">Dependencies</span></span>

<span data-ttu-id="4e140-161">.NET は、次の macOS のリリースでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="4e140-161">.NET is supported on the following macOS releases:</span></span>

> [!NOTE]
> <span data-ttu-id="4e140-162">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="4e140-162">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="4e140-163">.NET Core のバージョン</span><span class="sxs-lookup"><span data-stu-id="4e140-163">.NET Core Version</span></span> | <span data-ttu-id="4e140-164">macOS</span><span class="sxs-lookup"><span data-stu-id="4e140-164">macOS</span></span>                 | <span data-ttu-id="4e140-165">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="4e140-165">Architectures</span></span> | <span data-ttu-id="4e140-166">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4e140-166">More information</span></span>    |
| ----------------- | --------------------- | --------------| --- |
| <span data-ttu-id="4e140-167">5.0</span><span class="sxs-lookup"><span data-stu-id="4e140-167">5.0</span></span>               | <span data-ttu-id="4e140-168">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="4e140-168">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4e140-169">X64</span><span class="sxs-lookup"><span data-stu-id="4e140-169">x64</span></span> | [<span data-ttu-id="4e140-170">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4e140-170">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md) |
| <span data-ttu-id="4e140-171">3.1</span><span class="sxs-lookup"><span data-stu-id="4e140-171">3.1</span></span>               | <span data-ttu-id="4e140-172">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="4e140-172">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4e140-173">X64</span><span class="sxs-lookup"><span data-stu-id="4e140-173">x64</span></span> | [<span data-ttu-id="4e140-174">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4e140-174">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| <span data-ttu-id="4e140-175">3.0</span><span class="sxs-lookup"><span data-stu-id="4e140-175">3.0</span></span>               | <span data-ttu-id="4e140-176">High Sierra (10.13+)</span><span class="sxs-lookup"><span data-stu-id="4e140-176">High Sierra (10.13+)</span></span>  | <span data-ttu-id="4e140-177">X64</span><span class="sxs-lookup"><span data-stu-id="4e140-177">x64</span></span> | [<span data-ttu-id="4e140-178">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4e140-178">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| <span data-ttu-id="4e140-179">2.2</span><span class="sxs-lookup"><span data-stu-id="4e140-179">2.2</span></span>               | <span data-ttu-id="4e140-180">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="4e140-180">Sierra (10.12+)</span></span>       | <span data-ttu-id="4e140-181">X64</span><span class="sxs-lookup"><span data-stu-id="4e140-181">x64</span></span> | [<span data-ttu-id="4e140-182">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4e140-182">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| <span data-ttu-id="4e140-183">2.1</span><span class="sxs-lookup"><span data-stu-id="4e140-183">2.1</span></span>               | <span data-ttu-id="4e140-184">Sierra (10.12+)</span><span class="sxs-lookup"><span data-stu-id="4e140-184">Sierra (10.12+)</span></span>       | <span data-ttu-id="4e140-185">X64</span><span class="sxs-lookup"><span data-stu-id="4e140-185">x64</span></span> | [<span data-ttu-id="4e140-186">詳細情報</span><span class="sxs-lookup"><span data-stu-id="4e140-186">More information</span></span>](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

<span data-ttu-id="4e140-187">macOS Catalina (バージョン 10.15) 以降では、2019 年 6 月 1 日より後に作成され、Developer ID と共に配布されたすべてのソフトウェアは公証される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e140-187">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019 that is distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="4e140-188">この要件は、.NET ランタイム、.NET SDK、および .NET を使用して作成されたソフトウェアに適用されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-188">This requirement applies to the .NET runtime, .NET SDK, and software created with .NET.</span></span>

<span data-ttu-id="4e140-189">.NET 5.0 と .NET Core 3.1、3.0、2.1 のランタイムおよび SDK のインストーラーは、2020 年 2 月 18 日から公証されています。</span><span class="sxs-lookup"><span data-stu-id="4e140-189">The runtime and SDK installers for .NET 5.0 and .NET Core 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="4e140-190">それより前にリリースされたバージョンは、公証されていません。</span><span class="sxs-lookup"><span data-stu-id="4e140-190">Prior released versions aren't notarized.</span></span> <span data-ttu-id="4e140-191">公証されていないアプリを実行すると、次のイメージのようなエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-191">If you run a non-notarized app, you'll see an error similar to the following image:</span></span>

![macOS Catalina の公証に関するアラート](media/dependencies/macos-notarized-pkg-warning.png)

<span data-ttu-id="4e140-193">公証の強制が .NET (および .NET アプリ) に与える影響の詳細については、[macOS Catalina の公証への対応](macos-notarization-issues.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e140-193">For more information about how enforced-notarization affects .NET (and your .NET apps), see [Working with macOS Catalina Notarization](macos-notarization-issues.md).</span></span>

## <a name="libgdiplus"></a><span data-ttu-id="4e140-194">libgdiplus</span><span class="sxs-lookup"><span data-stu-id="4e140-194">libgdiplus</span></span>

<span data-ttu-id="4e140-195">*System.Drawing.Common* アセンブリを使用する .NET アプリケーションの場合は、libgdiplus をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4e140-195">.NET applications that use the *System.Drawing.Common* assembly require libgdiplus to be installed.</span></span>

<span data-ttu-id="4e140-196">libgdiplus を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。</span><span class="sxs-lookup"><span data-stu-id="4e140-196">An easy way to obtain libgdiplus is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="4e140-197">*brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して libgdiplus をインストールします。</span><span class="sxs-lookup"><span data-stu-id="4e140-197">After installing *brew*, install libgdiplus by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install mono-libgdiplus
```

## <a name="install-with-an-installer"></a><span data-ttu-id="4e140-198">インストーラーを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="4e140-198">Install with an installer</span></span>

<span data-ttu-id="4e140-199">macOS には、.NET 5.0 SDK のインストールに使用できるスタンドアロン インストーラーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4e140-199">macOS has standalone installers that can be used to install the .NET 5.0 SDK:</span></span>

- [<span data-ttu-id="4e140-200">x64 (64 ビット) CPU</span><span class="sxs-lookup"><span data-stu-id="4e140-200">x64 (64-bit) CPUs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/5.0)

## <a name="download-and-manually-install"></a><span data-ttu-id="4e140-201">手動でダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="4e140-201">Download and manually install</span></span>

<!-- Note, this content is taken from includes/linux-install-manual.md but changed for macOS. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="4e140-202">.NET 用 macOS インストーラーの代わりに、SDK とランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4e140-202">As an alternative to the macOS installers for .NET, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="4e140-203">手動インストールは、通常、継続的インテグレーション テストの一環として実行されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-203">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="4e140-204">開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet-core)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4e140-204">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="4e140-205">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4e140-205">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="4e140-206">まず、次のいずれかのサイトから SDK またはランタイムの **バイナリ** リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4e140-206">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="4e140-207">✔️ [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="4e140-207">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="4e140-208">✔️ [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="4e140-208">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="4e140-209">✔️ [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="4e140-209">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="4e140-210">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="4e140-210">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="4e140-211">次に、ダウンロードしたファイルを抽出し、`export` コマンドを使用して .NET で使用される変数を設定してから、.NET が PATH に含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4e140-211">Next, extract the downloaded file and use the `export` command to set variables used by .NET and then ensure .NET is in PATH.</span></span>

<span data-ttu-id="4e140-212">ランタイムを抽出し、.NET CLI コマンドをターミナルで使用できるようにするには、最初に .NET のバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="4e140-212">To extract the runtime and make the .NET CLI commands available at the terminal, first download a .NET binary release.</span></span> <span data-ttu-id="4e140-213">次に、ターミナルを開き、ファイルが保存されているディレクトリから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="4e140-213">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="4e140-214">アーカイブ ファイル名は、ダウンロードした内容によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4e140-214">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="4e140-215">**次のコマンドを使用して、ランタイムを抽出します**。</span><span class="sxs-lookup"><span data-stu-id="4e140-215">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="4e140-216">**次のコマンドを使用して、SDK を抽出します**。</span><span class="sxs-lookup"><span data-stu-id="4e140-216">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-osx-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="4e140-217">上記の `export` コマンドを使用すると、それを実行したターミナル セッションでのみ .NET CLI コマンドを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4e140-217">The preceding `export` commands only make the .NET CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="4e140-218">シェル プロファイルを編集して、コマンドを永続的に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="4e140-218">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="4e140-219">Linux ではさまざまなシェルを使用でき、それぞれに異なるプロファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="4e140-219">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="4e140-220">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4e140-220">For example:</span></span>
>
> - <span data-ttu-id="4e140-221">**Bash シェル**: *~/.bash_profile*、 *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="4e140-221">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="4e140-222">**Korn シェル**: *~/.kshrc* または *.profile*</span><span class="sxs-lookup"><span data-stu-id="4e140-222">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="4e140-223">**Z シェル**: *~/.zshrc* または *.zprofile*</span><span class="sxs-lookup"><span data-stu-id="4e140-223">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="4e140-224">シェルの適切なソース ファイルを編集し、既存の `PATH` ステートメントの末尾に `:$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="4e140-224">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="4e140-225">`PATH` ステートメントが含まれていない場合は、`export PATH=$PATH:$HOME/dotnet` を含む新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="4e140-225">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="4e140-226">また、ファイルの末尾に `export DOTNET_ROOT=$HOME/dotnet` を追加します。</span><span class="sxs-lookup"><span data-stu-id="4e140-226">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="4e140-227">この方法では、別々の場所に異なるバージョンをインストールして、どのアプリケーションにどれを使用するかを明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="4e140-227">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="4e140-228">Visual Studio for Mac を使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="4e140-228">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="4e140-229">Visual Studio for Mac を使用し、 **.NET** ワークロードを選択すると、.NET SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4e140-229">Visual Studio for Mac installs the .NET SDK when the **.NET** workload is selected.</span></span> <span data-ttu-id="4e140-230">macOS で .NET の開発を始めるには、「[Visual Studio 2019 for Mac をインストールする](/visualstudio/mac/installation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e140-230">To get started with .NET development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

| <span data-ttu-id="4e140-231">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="4e140-231">.NET SDK version</span></span>      | <span data-ttu-id="4e140-232">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="4e140-232">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="4e140-233">5.0</span><span class="sxs-lookup"><span data-stu-id="4e140-233">5.0</span></span>                   | <span data-ttu-id="4e140-234">Visual Studio 2019 for Mac バージョン 8.8 以降。</span><span class="sxs-lookup"><span data-stu-id="4e140-234">Visual Studio 2019 for Mac version 8.8 or higher.</span></span> |
| <span data-ttu-id="4e140-235">3.1</span><span class="sxs-lookup"><span data-stu-id="4e140-235">3.1</span></span>                   | <span data-ttu-id="4e140-236">Visual Studio 2019 for Mac バージョン 8.4 以降。</span><span class="sxs-lookup"><span data-stu-id="4e140-236">Visual Studio 2019 for Mac version 8.4 or higher.</span></span> |
| <span data-ttu-id="4e140-237">2.1</span><span class="sxs-lookup"><span data-stu-id="4e140-237">2.1</span></span>                   | <span data-ttu-id="4e140-238">Visual Studio 2019 for Mac バージョン 8.0 以降。</span><span class="sxs-lookup"><span data-stu-id="4e140-238">Visual Studio 2019 for Mac version 8.0 or higher.</span></span> |

<span data-ttu-id="4e140-239">[![macOS Visual Studio 2019 for Mac と .NET ワークロード機能](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="4e140-239">[![macOS Visual Studio 2019 for Mac with .NET workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="4e140-240">Visual Studio Code と共にインストールする</span><span class="sxs-lookup"><span data-stu-id="4e140-240">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="4e140-241">Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="4e140-241">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="4e140-242">Visual Studio Code は、Windows、macOS、Linux で利用できます。</span><span class="sxs-lookup"><span data-stu-id="4e140-242">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="4e140-243">Visual Studio Code には、Visual Studio のような自動化された .NET インストーラーは付属していませんが、.NET のサポートを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="4e140-243">While Visual Studio Code doesn't come with an automated .NET installer like Visual Studio does, adding .NET support is simple.</span></span>

01. <span data-ttu-id="4e140-244">[Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="4e140-244">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="4e140-245">[.NET SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="4e140-245">[Download and install the .NET SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="4e140-246">[Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="4e140-246">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="install-with-bash-automation"></a><span data-ttu-id="4e140-247">bash オートメーションを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="4e140-247">Install with bash automation</span></span>

<span data-ttu-id="4e140-248">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの自動化および管理者以外によるインストールに使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-248">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="4e140-249">スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="4e140-249">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="4e140-250">このスクリプトを使用すると、最新の[長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET 3.1) が既定でインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4e140-250">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET 3.1.</span></span> <span data-ttu-id="4e140-251">`current` スイッチを指定することで、特定のリリースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4e140-251">You can choose a specific release by specifying the `current` switch.</span></span> <span data-ttu-id="4e140-252">ランタイムをインストールするには、`runtime` スイッチを含めます。</span><span class="sxs-lookup"><span data-stu-id="4e140-252">Include the `runtime` switch to install a runtime.</span></span> <span data-ttu-id="4e140-253">それ以外の場合は、スクリプトによって [SDK](./windows.md) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="4e140-253">Otherwise, the script installs the [SDK](./windows.md).</span></span>

```bash
./dotnet-install.sh --channel 5.0 --runtime aspnetcore
```

> [!NOTE]
> <span data-ttu-id="4e140-254">前述のコマンドにより、互換性を最大限に高めるために ASP.NET Core ランタイムをインストールします。</span><span class="sxs-lookup"><span data-stu-id="4e140-254">The previous command installs the ASP.NET Core runtime for maximum compatability.</span></span> <span data-ttu-id="4e140-255">ASP.NET Core ランタイムには、標準の .NET ランタイムも含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e140-255">The ASP.NET Core runtime also includes the standard .NET runtime.</span></span>

## <a name="docker"></a><span data-ttu-id="4e140-256">Docker</span><span class="sxs-lookup"><span data-stu-id="4e140-256">Docker</span></span>

<span data-ttu-id="4e140-257">コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。</span><span class="sxs-lookup"><span data-stu-id="4e140-257">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="4e140-258">同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4e140-258">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="4e140-259">.NET は Docker コンテナー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="4e140-259">.NET can run in a Docker container.</span></span> <span data-ttu-id="4e140-260">公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET Core の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet/)で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="4e140-260">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet/).</span></span> <span data-ttu-id="4e140-261">各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e140-261">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="4e140-262">Microsoft は、特定のシナリオに対応したイメージを用意しています。</span><span class="sxs-lookup"><span data-stu-id="4e140-262">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="4e140-263">たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4e140-263">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="4e140-264">Docker コンテナー内で .NET Core を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e140-264">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="4e140-265">次の手順</span><span class="sxs-lookup"><span data-stu-id="4e140-265">Next steps</span></span>

- <span data-ttu-id="4e140-266">[.NET Core が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="4e140-266">[How to check if .NET Core is already installed](how-to-detect-installed-versions.md?pivots=os-macos).</span></span>
- <span data-ttu-id="4e140-267">[macOS Catalina の公証に対応する](macos-notarization-issues.md)。</span><span class="sxs-lookup"><span data-stu-id="4e140-267">[Working with macOS Catalina notarization](macos-notarization-issues.md).</span></span>
- <span data-ttu-id="4e140-268">[チュートリアル: macOS での作業を始める](../tutorials/with-visual-studio-mac.md).</span><span class="sxs-lookup"><span data-stu-id="4e140-268">[Tutorial: Get started on macOS](../tutorials/with-visual-studio-mac.md).</span></span>
- <span data-ttu-id="4e140-269">[チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="4e140-269">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="4e140-270">[チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="4e140-270">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[release-notes-21]: https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md
[release-notes-31]: https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md
[release-notes-50]: https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md
[release-notes-20]: https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md
[release-notes-22]: https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md
[release-notes-30]: https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md
