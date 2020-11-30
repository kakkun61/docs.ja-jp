---
title: Windows に .NET をインストールする
description: .NET をインストールできる Windows のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 4d3abde965d9a2ab0f86477feeb7c10f274a4b9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715122"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="7a81e-103">Windows に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="7a81e-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

<span data-ttu-id="7a81e-107">この記事では、Windows に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="7a81e-108">.NET は、ランタイムと SDK で構成されています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="7a81e-109">ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7a81e-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="7a81e-110">SDK は、.NET アプリとライブラリの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="7a81e-111">.NET ランタイムは、常に SDK と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="7a81e-112">.NET の最新バージョンは 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="7a81e-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7a81e-113">.NET をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7a81e-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="7a81e-114">サポートされているリリース</span><span class="sxs-lookup"><span data-stu-id="7a81e-114">Supported releases</span></span>

<span data-ttu-id="7a81e-115">以下の表は、現在サポートされている .NET リリースと、それらがサポートされている Windows のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="7a81e-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="7a81e-116">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Windows のバージョンの有効期限が切れるまで](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="7a81e-117">Windows 10 のバージョンのサービス終了日は、エディションごとに分かれています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="7a81e-118">次の表では、**Home**、**Pro**、**Pro Education**、**Pro for Workstations** の各エディションだけが考慮されています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="7a81e-119">具体的な詳細については、「[Windows ライフサイクルのファクト シート](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)」を確認してください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

- <span data-ttu-id="7a81e-120">✔️ は、Windows または .NET Core のバージョンがまだサポートされていることを示します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-120">A ✔️ indicates that the version of Windows or .NET Core is still supported.</span></span>
- <span data-ttu-id="7a81e-121">❌ は、Windows または .NET Core のバージョンがその Windows のリリースではサポートされていないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-121">A ❌ indicates that the version of Windows or .NET Core isn't supported on that Windows release.</span></span>
- <span data-ttu-id="7a81e-122">Windows のバージョンと .NET Core のバージョンの両方に ✔️ が付いている場合、その OS と .NET の組み合わせはサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-122">When both a version of Windows and a version of .NET Core have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="7a81e-123">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="7a81e-123">Operating System</span></span>                      | <span data-ttu-id="7a81e-124">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-124">.NET Core 2.1</span></span> | <span data-ttu-id="7a81e-125">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-125">.NET Core 3.1</span></span> | <span data-ttu-id="7a81e-126">.NET 5</span><span class="sxs-lookup"><span data-stu-id="7a81e-126">.NET 5</span></span> |
|-----------------------------|---------------|---------------|----------------|
| <span data-ttu-id="7a81e-127">✔️ Windows 10 バージョン 2004</span><span class="sxs-lookup"><span data-stu-id="7a81e-127">✔️ Windows 10, Version 2004</span></span> | <span data-ttu-id="7a81e-128">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-128">✔️ 2.1</span></span>        | <span data-ttu-id="7a81e-129">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-129">✔️ 3.1</span></span>        | <span data-ttu-id="7a81e-130">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-130">✔️ 5.0</span></span> |
| <span data-ttu-id="7a81e-131">✔️ Windows 10 バージョン 1909</span><span class="sxs-lookup"><span data-stu-id="7a81e-131">✔️ Windows 10, Version 1909</span></span> | <span data-ttu-id="7a81e-132">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-132">✔️ 2.1</span></span>        | <span data-ttu-id="7a81e-133">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-133">✔️ 3.1</span></span>        | <span data-ttu-id="7a81e-134">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-134">✔️ 5.0</span></span> |
| <span data-ttu-id="7a81e-135">✔️ Windows 10 バージョン 1903</span><span class="sxs-lookup"><span data-stu-id="7a81e-135">✔️ Windows 10, Version 1903</span></span> | <span data-ttu-id="7a81e-136">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-136">✔️ 2.1</span></span>        | <span data-ttu-id="7a81e-137">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-137">✔️ 3.1</span></span>        | <span data-ttu-id="7a81e-138">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-138">✔️ 5.0</span></span> |
| <span data-ttu-id="7a81e-139">✔️ Windows 10 バージョン 1809</span><span class="sxs-lookup"><span data-stu-id="7a81e-139">✔️ Windows 10, Version 1809</span></span> | <span data-ttu-id="7a81e-140">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-140">✔️ 2.1</span></span>        | <span data-ttu-id="7a81e-141">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-141">✔️ 3.1</span></span>        | <span data-ttu-id="7a81e-142">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-142">✔️ 5.0</span></span> |
| <span data-ttu-id="7a81e-143">❌ Windows 10 バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="7a81e-143">❌ Windows 10, Version 1803</span></span> | <span data-ttu-id="7a81e-144">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-144">✔️ 2.1</span></span>        | <span data-ttu-id="7a81e-145">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-145">✔️ 3.1</span></span>        | <span data-ttu-id="7a81e-146">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-146">✔️ 5.0</span></span> |
| <span data-ttu-id="7a81e-147">❌ Windows 10 バージョン 1709</span><span class="sxs-lookup"><span data-stu-id="7a81e-147">❌ Windows 10, Version 1709</span></span> | <span data-ttu-id="7a81e-148">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-148">✔️ 2.1</span></span>        | <span data-ttu-id="7a81e-149">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-149">✔️ 3.1</span></span>        | <span data-ttu-id="7a81e-150">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-150">✔️ 5.0</span></span> |
| <span data-ttu-id="7a81e-151">❌ Windows 10 バージョン 1703</span><span class="sxs-lookup"><span data-stu-id="7a81e-151">❌ Windows 10, Version 1703</span></span> | <span data-ttu-id="7a81e-152">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-152">❌ 2.1</span></span>        | <span data-ttu-id="7a81e-153">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-153">❌ 3.1</span></span>        | <span data-ttu-id="7a81e-154">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-154">❌ 5.0</span></span> |
| <span data-ttu-id="7a81e-155">❌ Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="7a81e-155">❌ Windows 10, Version 1607</span></span> | <span data-ttu-id="7a81e-156">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-156">✔️ 2.1</span></span>        | <span data-ttu-id="7a81e-157">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-157">✔️ 3.1</span></span>        | <span data-ttu-id="7a81e-158">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-158">✔️ 5.0</span></span> |
| <span data-ttu-id="7a81e-159">❌ Windows 10 バージョン 1511</span><span class="sxs-lookup"><span data-stu-id="7a81e-159">❌ Windows 10, Version 1511</span></span> | <span data-ttu-id="7a81e-160">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-160">❌ 2.1</span></span>        | <span data-ttu-id="7a81e-161">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-161">❌ 3.1</span></span>        | <span data-ttu-id="7a81e-162">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-162">❌ 5.0</span></span> |
| <span data-ttu-id="7a81e-163">❌ Windows 10 バージョン 1507</span><span class="sxs-lookup"><span data-stu-id="7a81e-163">❌ Windows 10, Version 1507</span></span> | <span data-ttu-id="7a81e-164">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-164">❌ 2.1</span></span>        | <span data-ttu-id="7a81e-165">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-165">❌ 3.1</span></span>        | <span data-ttu-id="7a81e-166">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-166">❌ 5.0</span></span> |

## <a name="unsupported-releases"></a><span data-ttu-id="7a81e-167">サポートされていないリリース</span><span class="sxs-lookup"><span data-stu-id="7a81e-167">Unsupported releases</span></span>

<span data-ttu-id="7a81e-168">次のバージョンの .NET は、❌ サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="7a81e-168">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="7a81e-169">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-169">The downloads for these still remain published:</span></span>

- <span data-ttu-id="7a81e-170">3.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-170">3.0</span></span>
- <span data-ttu-id="7a81e-171">2.2</span><span class="sxs-lookup"><span data-stu-id="7a81e-171">2.2</span></span>
- <span data-ttu-id="7a81e-172">2.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-172">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="7a81e-173">ランタイムに関する情報</span><span class="sxs-lookup"><span data-stu-id="7a81e-173">Runtime information</span></span>

<span data-ttu-id="7a81e-174">ランタイムは、.NET で作成されたアプリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-174">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="7a81e-175">アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-175">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="7a81e-176">ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a81e-176">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="7a81e-177">Windows には、3 つの異なるランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-177">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="7a81e-178">*ASP.NET Core ランタイム*</span><span class="sxs-lookup"><span data-stu-id="7a81e-178">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="7a81e-179">ASP.NET Core アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-179">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="7a81e-180">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-180">Includes the .NET runtime.</span></span>

<span data-ttu-id="7a81e-181">*Desktop ランタイム*</span><span class="sxs-lookup"><span data-stu-id="7a81e-181">*Desktop runtime*</span></span>\
<span data-ttu-id="7a81e-182">Windows 用の .NET WPF と Windows フォームのデスクトップ アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-182">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="7a81e-183">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-183">Includes the .NET runtime.</span></span>

<span data-ttu-id="7a81e-184">*.NET ランタイム*</span><span class="sxs-lookup"><span data-stu-id="7a81e-184">*.NET runtime*</span></span>\
<span data-ttu-id="7a81e-185">このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="7a81e-185">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="7a81e-186">.NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" と "*Desktop ランタイム*" の両方をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a81e-186">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="7a81e-187">.NET ランタイムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="7a81e-187">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="7a81e-188">SDK に関する情報</span><span class="sxs-lookup"><span data-stu-id="7a81e-188">SDK information</span></span>

<span data-ttu-id="7a81e-189">SDK は、.NET アプリとライブラリを作成して公開するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-189">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="7a81e-190">SDK のインストールには、次の 3 つの[ランタイム](#runtime-information)が含まれます: ASP.NET Core、Desktop、.NET。</span><span class="sxs-lookup"><span data-stu-id="7a81e-190">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="7a81e-191">依存関係</span><span class="sxs-lookup"><span data-stu-id="7a81e-191">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="7a81e-192">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-192">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="7a81e-193">.NET 5.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-193">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="7a81e-194">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-194">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7a81e-195">OS</span><span class="sxs-lookup"><span data-stu-id="7a81e-195">OS</span></span>                  | <span data-ttu-id="7a81e-196">バージョン</span><span class="sxs-lookup"><span data-stu-id="7a81e-196">Version</span></span>       | <span data-ttu-id="7a81e-197">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7a81e-197">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="7a81e-198">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-198">Windows 10 Client</span></span>   | <span data-ttu-id="7a81e-199">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="7a81e-199">Version 1607+</span></span> | <span data-ttu-id="7a81e-200">x64、x86、ARM64</span><span class="sxs-lookup"><span data-stu-id="7a81e-200">x64, x86, ARM64</span></span> |
| <span data-ttu-id="7a81e-201">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-201">Windows Client</span></span>      | <span data-ttu-id="7a81e-202">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-202">7 SP1+, 8.1</span></span>   | <span data-ttu-id="7a81e-203">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-203">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-204">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-204">Windows Server</span></span>      | <span data-ttu-id="7a81e-205">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="7a81e-205">2012 R2+</span></span>      | <span data-ttu-id="7a81e-206">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-206">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-207">Windows サーバー コア</span><span class="sxs-lookup"><span data-stu-id="7a81e-207">Windows Server Core</span></span> | <span data-ttu-id="7a81e-208">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="7a81e-208">2012 R2+</span></span>      | <span data-ttu-id="7a81e-209">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-209">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-210">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-210">Nano Server</span></span>         | <span data-ttu-id="7a81e-211">バージョン 1809+</span><span class="sxs-lookup"><span data-stu-id="7a81e-211">Version 1809+</span></span> | <span data-ttu-id="7a81e-212">X64</span><span class="sxs-lookup"><span data-stu-id="7a81e-212">x64</span></span>             |

<span data-ttu-id="7a81e-213">.NET 5.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)」 (.NET 5.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-213">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="7a81e-214">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-214">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="7a81e-215">.NET Core 3.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-215">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7a81e-216">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-216">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7a81e-217">OS</span><span class="sxs-lookup"><span data-stu-id="7a81e-217">OS</span></span>                            | <span data-ttu-id="7a81e-218">バージョン</span><span class="sxs-lookup"><span data-stu-id="7a81e-218">Version</span></span>                        | <span data-ttu-id="7a81e-219">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7a81e-219">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7a81e-220">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-220">Windows Client</span></span>                | <span data-ttu-id="7a81e-221">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-221">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7a81e-222">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-222">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-223">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-223">Windows 10 Client</span></span>             | <span data-ttu-id="7a81e-224">バージョン 1609+</span><span class="sxs-lookup"><span data-stu-id="7a81e-224">Version 1609+</span></span>                  | <span data-ttu-id="7a81e-225">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-225">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-226">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-226">Windows Server</span></span>                | <span data-ttu-id="7a81e-227">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="7a81e-227">2012 R2+</span></span>                       | <span data-ttu-id="7a81e-228">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-228">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-229">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-229">Nano Server</span></span>                   | <span data-ttu-id="7a81e-230">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="7a81e-230">Version 1803+</span></span>                  | <span data-ttu-id="7a81e-231">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7a81e-231">x64, ARM32</span></span>      |

<span data-ttu-id="7a81e-232">.NET Core 3.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)」(.NET Core 3.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-232">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="7a81e-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-233">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="7a81e-234">" *.NET Core 3.0 は現在サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="7a81e-234">*.NET Core 3.0 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7a81e-235">.NET Core 3.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-235">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="7a81e-236">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-236">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7a81e-237">OS</span><span class="sxs-lookup"><span data-stu-id="7a81e-237">OS</span></span>                            | <span data-ttu-id="7a81e-238">バージョン</span><span class="sxs-lookup"><span data-stu-id="7a81e-238">Version</span></span>                        | <span data-ttu-id="7a81e-239">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7a81e-239">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7a81e-240">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-240">Windows Client</span></span>                | <span data-ttu-id="7a81e-241">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-241">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7a81e-242">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-242">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-243">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-243">Windows 10 Client</span></span>             | <span data-ttu-id="7a81e-244">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="7a81e-244">Version 1607+</span></span>                  | <span data-ttu-id="7a81e-245">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-245">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-246">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-246">Windows Server</span></span>                | <span data-ttu-id="7a81e-247">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="7a81e-247">2012 R2+</span></span>                       | <span data-ttu-id="7a81e-248">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-248">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-249">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-249">Nano Server</span></span>                   | <span data-ttu-id="7a81e-250">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="7a81e-250">Version 1803+</span></span>                  | <span data-ttu-id="7a81e-251">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7a81e-251">x64, ARM32</span></span>      |

<span data-ttu-id="7a81e-252">.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)」(.NET Core 3.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-252">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="7a81e-253">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7a81e-253">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="7a81e-254">" *.NET Core 2.2 は現在サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="7a81e-254">*.NET Core 2.2 is currently out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="7a81e-255">.NET Core 2.2 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-255">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="7a81e-256">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-256">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7a81e-257">OS</span><span class="sxs-lookup"><span data-stu-id="7a81e-257">OS</span></span>                            | <span data-ttu-id="7a81e-258">バージョン</span><span class="sxs-lookup"><span data-stu-id="7a81e-258">Version</span></span>                        | <span data-ttu-id="7a81e-259">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7a81e-259">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7a81e-260">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-260">Windows Client</span></span>                | <span data-ttu-id="7a81e-261">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-261">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7a81e-262">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-262">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-263">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-263">Windows 10 Client</span></span>             | <span data-ttu-id="7a81e-264">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="7a81e-264">Version 1607+</span></span>                  | <span data-ttu-id="7a81e-265">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-265">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-266">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-266">Windows Server</span></span>                | <span data-ttu-id="7a81e-267">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="7a81e-267">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7a81e-268">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-268">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-269">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-269">Nano Server</span></span>                   | <span data-ttu-id="7a81e-270">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="7a81e-270">Version 1803+</span></span>                   | <span data-ttu-id="7a81e-271">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="7a81e-271">x64, ARM32</span></span>      |

<span data-ttu-id="7a81e-272">.NET Core 2.2 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)」(.NET Core 2.2 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-272">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="7a81e-273">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-273">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="7a81e-274">.NET Core 2.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-274">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="7a81e-275">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-275">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="7a81e-276">OS</span><span class="sxs-lookup"><span data-stu-id="7a81e-276">OS</span></span>                            | <span data-ttu-id="7a81e-277">バージョン</span><span class="sxs-lookup"><span data-stu-id="7a81e-277">Version</span></span>                        | <span data-ttu-id="7a81e-278">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7a81e-278">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="7a81e-279">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-279">Windows Client</span></span>                | <span data-ttu-id="7a81e-280">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-280">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="7a81e-281">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-281">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-282">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="7a81e-282">Windows 10 Client</span></span>             | <span data-ttu-id="7a81e-283">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="7a81e-283">Version 1607+</span></span>                  | <span data-ttu-id="7a81e-284">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-284">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-285">Windows Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-285">Windows Server</span></span>                | <span data-ttu-id="7a81e-286">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="7a81e-286">2008 R2 SP1+</span></span>                   | <span data-ttu-id="7a81e-287">x64、x86</span><span class="sxs-lookup"><span data-stu-id="7a81e-287">x64, x86</span></span>        |
| <span data-ttu-id="7a81e-288">Nano Server</span><span class="sxs-lookup"><span data-stu-id="7a81e-288">Nano Server</span></span>                   | <span data-ttu-id="7a81e-289">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="7a81e-289">Version 1803+</span></span>                  | <span data-ttu-id="7a81e-290">x64、</span><span class="sxs-lookup"><span data-stu-id="7a81e-290">x64,</span></span>            |

<span data-ttu-id="7a81e-291">.NET Core 2.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)」(.NET Core 2.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-291">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="7a81e-292">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7a81e-292">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="7a81e-293">次の Windows のバージョンに .NET SDK またはランタイムをインストールする場合は、追加の依存関係が必要です。</span><span class="sxs-lookup"><span data-stu-id="7a81e-293">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="7a81e-294">❌ Windows 7 SP1</span><span class="sxs-lookup"><span data-stu-id="7a81e-294">❌ Windows 7 SP1</span></span>
- <span data-ttu-id="7a81e-295">❌ Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="7a81e-295">❌ Windows Vista SP 2</span></span>
- <span data-ttu-id="7a81e-296">✔️ Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-296">✔️ Windows 8.1</span></span>
- <span data-ttu-id="7a81e-297">✔️ Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="7a81e-297">✔️ Windows Server 2008 R2</span></span>
- <span data-ttu-id="7a81e-298">✔️ Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="7a81e-298">✔️ Windows Server 2012 R2</span></span>

<span data-ttu-id="7a81e-299">以下をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7a81e-299">Install the following:</span></span>

- <span data-ttu-id="7a81e-300">[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-300">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="7a81e-301">KB2533623</span><span class="sxs-lookup"><span data-stu-id="7a81e-301">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="7a81e-302">上記の要件は、次のいずれかのエラーが発生した場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="7a81e-302">The previous requirements are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="7a81e-303">お使いのコンピューターに *api-ms-win-crt-runtime-l1-1-0.dll* が見つからず、プログラムを開始できない。</span><span class="sxs-lookup"><span data-stu-id="7a81e-303">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7a81e-304">この問題を解決するには、プログラムを再インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-304">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7a81e-305">\- または</span><span class="sxs-lookup"><span data-stu-id="7a81e-305">\- or -</span></span>
>
> <span data-ttu-id="7a81e-306">お使いのコンピューターに *api-ms-win-cor-timezone-l1-1-0.dll* が見つからず、プログラムを開始できない。</span><span class="sxs-lookup"><span data-stu-id="7a81e-306">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="7a81e-307">この問題を解決するには、プログラムを再インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-307">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="7a81e-308">\- または</span><span class="sxs-lookup"><span data-stu-id="7a81e-308">\- or -</span></span>
>
> <span data-ttu-id="7a81e-309">ライブラリ *hostfxr.dll* は見つかったが、その *C:\\\<path_to_app>\\hostfxr.dll* からの読み込みに失敗した。</span><span class="sxs-lookup"><span data-stu-id="7a81e-309">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="7a81e-310">PowerShell オートメーションを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="7a81e-310">Install with PowerShell automation</span></span>

<span data-ttu-id="7a81e-311">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの CI 自動化および管理者以外によるインストールに使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-311">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="7a81e-312">スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-312">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="7a81e-313">スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-313">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="7a81e-314">`Channel` スイッチを指定することで、特定のリリースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-314">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="7a81e-315">ランタイムをインストールするには、`Runtime` スイッチを含めます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-315">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="7a81e-316">それ以外の場合は、スクリプトによって SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-316">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="7a81e-317">`-Runtime` スイッチを省略して SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7a81e-317">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="7a81e-318">この例では、`-Channel` スイッチが `Current` に設定されているため、サポートされている最新バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-318">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="7a81e-319">Visual Studio を使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="7a81e-319">Install with Visual Studio</span></span>

<span data-ttu-id="7a81e-320">次の表で、Visual Studio を使用して .NET アプリを開発している場合に、ターゲットの .NET SDK バージョンに基づいて最低限必要な Visual Studio のバージョンを説明しています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-320">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="7a81e-321">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="7a81e-321">.NET SDK version</span></span>      | <span data-ttu-id="7a81e-322">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="7a81e-322">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="7a81e-323">5.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-323">5.0</span></span>                   | <span data-ttu-id="7a81e-324">Visual Studio 2019 バージョン 16.8 以降。</span><span class="sxs-lookup"><span data-stu-id="7a81e-324">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="7a81e-325">3.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-325">3.1</span></span>                   | <span data-ttu-id="7a81e-326">Visual Studio 2019 バージョン 16.4 以降。</span><span class="sxs-lookup"><span data-stu-id="7a81e-326">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="7a81e-327">3.0</span><span class="sxs-lookup"><span data-stu-id="7a81e-327">3.0</span></span>                   | <span data-ttu-id="7a81e-328">Visual Studio 2019 バージョン 16.3 以降。</span><span class="sxs-lookup"><span data-stu-id="7a81e-328">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="7a81e-329">2.2</span><span class="sxs-lookup"><span data-stu-id="7a81e-329">2.2</span></span>                   | <span data-ttu-id="7a81e-330">Visual Studio 2017 バージョン 15.9 以降。</span><span class="sxs-lookup"><span data-stu-id="7a81e-330">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="7a81e-331">2.1</span><span class="sxs-lookup"><span data-stu-id="7a81e-331">2.1</span></span>                   | <span data-ttu-id="7a81e-332">Visual Studio 2017 バージョン 15.7 以降。</span><span class="sxs-lookup"><span data-stu-id="7a81e-332">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="7a81e-333">Visual Studio を既にインストールしてある場合は、次の手順でバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-333">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="7a81e-334">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-334">Open Visual Studio.</span></span>
01. <span data-ttu-id="7a81e-335">**[ヘルプ]**  >  **[Microsoft Visual Studio のバージョン情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-335">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="7a81e-336">**[バージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-336">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="7a81e-337">Visual Studio には、最新の .NET SDK とランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-337">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="7a81e-338">[Visual Studio をダウンロードします](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-338">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="7a81e-339">ワークロードを選択する</span><span class="sxs-lookup"><span data-stu-id="7a81e-339">Select a workload</span></span>

<span data-ttu-id="7a81e-340">Visual Studio をインストールまたは変更するときは、ビルドするアプリケーションの種類に応じて、次の 1 つ以上のワークロードを選択します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-340">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="7a81e-341">**[他のツールセット]** セクションの **[.NET Core クロスプラットフォームの開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="7a81e-341">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="7a81e-342">**[Web クラウド]** セクションの **[ASP.NET と Web 開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="7a81e-342">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7a81e-343">**[Web クラウド]** セクションの **[Azure の開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="7a81e-343">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="7a81e-344">**[デスクトップとモバイル]** セクションの **[.NET デスクトップ開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="7a81e-344">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="7a81e-345">[![Windows Visual Studio 2019 と .NET Core ワークロード](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="7a81e-345">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="7a81e-346">Visual Studio Code と共にインストールする</span><span class="sxs-lookup"><span data-stu-id="7a81e-346">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="7a81e-347">Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="7a81e-347">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="7a81e-348">Visual Studio Code は、Windows、macOS、Linux で利用できます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-348">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="7a81e-349">Visual Studio Code には、Visual Studio のような自動化された .NET Core インストーラーは付属していませんが、.NET Core のサポートを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-349">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="7a81e-350">[Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-350">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="7a81e-351">[.NET Core SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-351">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="7a81e-352">[Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-352">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="download-and-manually-install"></a><span data-ttu-id="7a81e-353">手動でダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="7a81e-353">Download and manually install</span></span>

<span data-ttu-id="7a81e-354">.NET 用 Windows インストーラーの代わりに、SDK またはランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-354">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="7a81e-355">手動インストールは、通常、継続的インテグレーション テストの一環として実行されます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-355">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="7a81e-356">開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet-core)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7a81e-356">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="7a81e-357">.NET SDK と .NET ランタイムはどちらも、ダウンロード後に手動でインストールできます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-357">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="7a81e-358">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7a81e-358">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="7a81e-359">まず、次のいずれかのサイトから SDK またはランタイムのバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7a81e-359">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="7a81e-360">✔️ [.NET 5.0 のダウンロード](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="7a81e-360">✔️ [.NET 5.0 downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="7a81e-361">✔️ [.NET Core 3.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="7a81e-361">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="7a81e-362">✔️ [.NET Core 2.1 のダウンロード](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="7a81e-362">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="7a81e-363">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="7a81e-363">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="7a81e-364">.NET を抽出するためのディレクトリを作成します (`%USERPROFILE%\dotnet` など)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-364">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="7a81e-365">次に、ダウンロードした zip ファイルをそのディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-365">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="7a81e-366">既定では、この方法でインストールされた .NET は、.NET CLI コマンドおよびアプリから使用されないため、使用することを明示的に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7a81e-366">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="7a81e-367">これを行うには、アプリケーションの起動に使用する環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-367">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="7a81e-368">この方法では、複数のバージョンを別々の場所にインストールして、その場所を参照する環境変数を使ってアプリケーションを実行することで、アプリケーションによって使用されるインストール場所を明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-368">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="7a81e-369">`DOTNET_MULTILEVEL_LOOKUP` が `0` に設定されている場合、.NET により、グローバルにインストールされている .NET のバージョンはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-369">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="7a81e-370">アプリケーションを実行するための最適なフレームワークを選択するときに、.NET によりグローバル インストールの既定の場所が考慮されるようにするには、その環境設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="7a81e-370">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="7a81e-371">通常、既定値は `C:\Program Files\dotnet` です。インストーラーによってここに .NET がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-371">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="7a81e-372">Docker</span><span class="sxs-lookup"><span data-stu-id="7a81e-372">Docker</span></span>

<span data-ttu-id="7a81e-373">コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-373">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="7a81e-374">同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-374">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="7a81e-375">.NET は Docker コンテナー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-375">.NET can run in a Docker container.</span></span> <span data-ttu-id="7a81e-376">公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet)で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="7a81e-376">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="7a81e-377">各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-377">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="7a81e-378">Microsoft は、特定のシナリオに対応したイメージを用意しています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-378">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="7a81e-379">たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7a81e-379">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="7a81e-380">Docker コンテナー内で .NET を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7a81e-380">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="7a81e-381">次のステップ</span><span class="sxs-lookup"><span data-stu-id="7a81e-381">Next steps</span></span>

- <span data-ttu-id="7a81e-382">[.NET が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-382">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="7a81e-383">[チュートリアル: Hello World チュートリアル](../tutorials/with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-383">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="7a81e-384">[チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-384">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="7a81e-385">[チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="7a81e-385">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>
