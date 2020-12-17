---
title: Windows に .NET をインストールする
description: .NET をインストールできる Windows のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: b5c0949bbd591906536094a33d8583a265d8a4c8
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110235"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="eba45-103">Windows に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="eba45-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

<span data-ttu-id="eba45-107">この記事では、Windows に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="eba45-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="eba45-108">.NET は、ランタイムと SDK で構成されています。</span><span class="sxs-lookup"><span data-stu-id="eba45-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="eba45-109">ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="eba45-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="eba45-110">SDK は、.NET アプリとライブラリの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="eba45-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="eba45-111">.NET ランタイムは、常に SDK と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="eba45-112">.NET の最新バージョンは 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="eba45-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="eba45-113">.NET をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="eba45-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="eba45-114">サポートされているリリース</span><span class="sxs-lookup"><span data-stu-id="eba45-114">Supported releases</span></span>

<span data-ttu-id="eba45-115">以下の表は、現在サポートされている .NET リリースと、それらがサポートされている Windows のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="eba45-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="eba45-116">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Windows のバージョンの有効期限が切れるまで](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="eba45-117">Windows 10 のバージョンのサービス終了日は、エディションごとに分かれています。</span><span class="sxs-lookup"><span data-stu-id="eba45-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="eba45-118">次の表では、**Home**、**Pro**、**Pro Education**、**Pro for Workstations** の各エディションだけが考慮されています。</span><span class="sxs-lookup"><span data-stu-id="eba45-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="eba45-119">具体的な詳細については、「[Windows ライフサイクルのファクト シート](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)」を確認してください。</span><span class="sxs-lookup"><span data-stu-id="eba45-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="eba45-120">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="eba45-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="eba45-121">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="eba45-121">Operating System</span></span>            | <span data-ttu-id="eba45-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eba45-122">.NET Core 2.1</span></span> | <span data-ttu-id="eba45-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="eba45-123">.NET Core 3.1</span></span> | <span data-ttu-id="eba45-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="eba45-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="eba45-125">Windows 10 バージョン 20H2</span><span class="sxs-lookup"><span data-stu-id="eba45-125">Windows 10, Version 20H2</span></span>    | <span data-ttu-id="eba45-126">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-126">✔️</span></span>           | <span data-ttu-id="eba45-127">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-127">✔️</span></span>            | <span data-ttu-id="eba45-128">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-128">✔️</span></span>    |
| <span data-ttu-id="eba45-129">Windows 10 バージョン 2004</span><span class="sxs-lookup"><span data-stu-id="eba45-129">Windows 10, Version 2004</span></span>    | <span data-ttu-id="eba45-130">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-130">✔️</span></span>           | <span data-ttu-id="eba45-131">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-131">✔️</span></span>            | <span data-ttu-id="eba45-132">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-132">✔️</span></span>    |
| <span data-ttu-id="eba45-133">Windows 10 バージョン 1909</span><span class="sxs-lookup"><span data-stu-id="eba45-133">Windows 10, Version 1909</span></span>    | <span data-ttu-id="eba45-134">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-134">✔️</span></span>           | <span data-ttu-id="eba45-135">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-135">✔️</span></span>            | <span data-ttu-id="eba45-136">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-136">✔️</span></span>    |
| <span data-ttu-id="eba45-137">Windows 10 バージョン 1903</span><span class="sxs-lookup"><span data-stu-id="eba45-137">Windows 10, Version 1903</span></span>    | <span data-ttu-id="eba45-138">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-138">✔️</span></span>           | <span data-ttu-id="eba45-139">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-139">✔️</span></span>            | <span data-ttu-id="eba45-140">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-140">✔️</span></span>    |
| <span data-ttu-id="eba45-141">Windows 10 バージョン 1809</span><span class="sxs-lookup"><span data-stu-id="eba45-141">Windows 10, Version 1809</span></span>    | <span data-ttu-id="eba45-142">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-142">✔️</span></span>           | <span data-ttu-id="eba45-143">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-143">✔️</span></span>            | <span data-ttu-id="eba45-144">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-144">✔️</span></span>    |
| <span data-ttu-id="eba45-145"> Windows 10 バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="eba45-145">Windows 10, Version 1803</span></span>    | <span data-ttu-id="eba45-146">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-146">✔️</span></span>           | <span data-ttu-id="eba45-147">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-147">✔️</span></span>            | <span data-ttu-id="eba45-148">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-148">✔️</span></span>    |
| <span data-ttu-id="eba45-149">Windows 10 バージョン 1709</span><span class="sxs-lookup"><span data-stu-id="eba45-149">Windows 10, Version 1709</span></span>    | <span data-ttu-id="eba45-150">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-150">✔️</span></span>           | <span data-ttu-id="eba45-151">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-151">✔️</span></span>            | <span data-ttu-id="eba45-152">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-152">✔️</span></span>    |
| <span data-ttu-id="eba45-153">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="eba45-153">Windows 10, Version 1607</span></span>    | <span data-ttu-id="eba45-154">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-154">✔️</span></span>           | <span data-ttu-id="eba45-155">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-155">✔️</span></span>            | <span data-ttu-id="eba45-156">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-156">✔️</span></span>    |
| <span data-ttu-id="eba45-157">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="eba45-157">Windows 8.1</span></span>                 | <span data-ttu-id="eba45-158">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-158">✔️</span></span>           | <span data-ttu-id="eba45-159">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-159">✔️</span></span>            | <span data-ttu-id="eba45-160">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-160">✔️</span></span>    |
| <span data-ttu-id="eba45-161">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="eba45-161">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="eba45-162">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-162">✔️</span></span>           | <span data-ttu-id="eba45-163">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-163">✔️</span></span>            | <span data-ttu-id="eba45-164">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-164">✔️</span></span>    |
| <span data-ttu-id="eba45-165">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="eba45-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="eba45-166">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-166">✔️</span></span>           | <span data-ttu-id="eba45-167">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-167">✔️</span></span>            | <span data-ttu-id="eba45-168">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-168">✔️</span></span>    |
| <span data-ttu-id="eba45-169">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="eba45-169">Windows 10, Version 1607</span></span>    | <span data-ttu-id="eba45-170">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-170">✔️</span></span>           | <span data-ttu-id="eba45-171">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-171">✔️</span></span>            | <span data-ttu-id="eba45-172">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-172">✔️</span></span>    |
| <span data-ttu-id="eba45-173">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eba45-173">Windows Server 2012 R2</span></span>      | <span data-ttu-id="eba45-174">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-174">✔️</span></span>           | <span data-ttu-id="eba45-175">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-175">✔️</span></span>            | <span data-ttu-id="eba45-176">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-176">✔️</span></span>    |
| <span data-ttu-id="eba45-177">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eba45-177">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="eba45-178">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-178">✔️</span></span>           | <span data-ttu-id="eba45-179">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-179">✔️</span></span>            | <span data-ttu-id="eba45-180">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-180">✔️</span></span>    |
| <span data-ttu-id="eba45-181">Nano Server バージョン 1809 以上</span><span class="sxs-lookup"><span data-stu-id="eba45-181">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="eba45-182">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-182">✔️</span></span>           | <span data-ttu-id="eba45-183">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-183">✔️</span></span>            | <span data-ttu-id="eba45-184">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-184">✔️</span></span>    |
| <span data-ttu-id="eba45-185">Nano Server バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="eba45-185">Nano Server, Version 1803</span></span>   | <span data-ttu-id="eba45-186">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-186">✔️</span></span>           | <span data-ttu-id="eba45-187">✔️</span><span class="sxs-lookup"><span data-stu-id="eba45-187">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="eba45-188">サポートされていないリリース</span><span class="sxs-lookup"><span data-stu-id="eba45-188">Unsupported releases</span></span>

<span data-ttu-id="eba45-189">次のバージョンの .NET は、❌ サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="eba45-189">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="eba45-190">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="eba45-190">The downloads for these still remain published:</span></span>

- <span data-ttu-id="eba45-191">3.0</span><span class="sxs-lookup"><span data-stu-id="eba45-191">3.0</span></span>
- <span data-ttu-id="eba45-192">2.2</span><span class="sxs-lookup"><span data-stu-id="eba45-192">2.2</span></span>
- <span data-ttu-id="eba45-193">2.0</span><span class="sxs-lookup"><span data-stu-id="eba45-193">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="eba45-194">ランタイムに関する情報</span><span class="sxs-lookup"><span data-stu-id="eba45-194">Runtime information</span></span>

<span data-ttu-id="eba45-195">ランタイムは、.NET で作成されたアプリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eba45-195">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="eba45-196">アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="eba45-196">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="eba45-197">ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="eba45-197">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="eba45-198">Windows には、3 つの異なるランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="eba45-198">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="eba45-199">*ASP.NET Core ランタイム*</span><span class="sxs-lookup"><span data-stu-id="eba45-199">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="eba45-200">ASP.NET Core アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="eba45-200">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="eba45-201">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="eba45-201">Includes the .NET runtime.</span></span>

<span data-ttu-id="eba45-202">*Desktop ランタイム*</span><span class="sxs-lookup"><span data-stu-id="eba45-202">*Desktop runtime*</span></span>\
<span data-ttu-id="eba45-203">Windows 用の .NET WPF と Windows フォームのデスクトップ アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="eba45-203">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="eba45-204">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="eba45-204">Includes the .NET runtime.</span></span>

<span data-ttu-id="eba45-205">*.NET ランタイム*</span><span class="sxs-lookup"><span data-stu-id="eba45-205">*.NET runtime*</span></span>\
<span data-ttu-id="eba45-206">このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="eba45-206">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="eba45-207">.NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" と "*Desktop ランタイム*" の両方をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="eba45-207">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="eba45-208">.NET ランタイムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="eba45-208">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="eba45-209">SDK に関する情報</span><span class="sxs-lookup"><span data-stu-id="eba45-209">SDK information</span></span>

<span data-ttu-id="eba45-210">SDK は、.NET アプリとライブラリを作成して公開するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="eba45-210">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="eba45-211">SDK のインストールには、次の 3 つの[ランタイム](#runtime-information)が含まれます: ASP.NET Core、Desktop、.NET。</span><span class="sxs-lookup"><span data-stu-id="eba45-211">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="eba45-212">依存関係</span><span class="sxs-lookup"><span data-stu-id="eba45-212">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="eba45-213">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="eba45-213">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="eba45-214">.NET 5.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-214">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="eba45-215">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="eba45-215">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="eba45-216">OS</span><span class="sxs-lookup"><span data-stu-id="eba45-216">OS</span></span>                  | <span data-ttu-id="eba45-217">バージョン</span><span class="sxs-lookup"><span data-stu-id="eba45-217">Version</span></span>       | <span data-ttu-id="eba45-218">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="eba45-218">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="eba45-219">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-219">Windows 10 Client</span></span>   | <span data-ttu-id="eba45-220">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="eba45-220">Version 1607+</span></span> | <span data-ttu-id="eba45-221">x64、x86、ARM64</span><span class="sxs-lookup"><span data-stu-id="eba45-221">x64, x86, ARM64</span></span> |
| <span data-ttu-id="eba45-222">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-222">Windows Client</span></span>      | <span data-ttu-id="eba45-223">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="eba45-223">7 SP1+, 8.1</span></span>   | <span data-ttu-id="eba45-224">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-224">x64, x86</span></span>        |
| <span data-ttu-id="eba45-225">Windows Server</span><span class="sxs-lookup"><span data-stu-id="eba45-225">Windows Server</span></span>      | <span data-ttu-id="eba45-226">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="eba45-226">2012 R2+</span></span>      | <span data-ttu-id="eba45-227">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-227">x64, x86</span></span>        |
| <span data-ttu-id="eba45-228">Windows サーバー コア</span><span class="sxs-lookup"><span data-stu-id="eba45-228">Windows Server Core</span></span> | <span data-ttu-id="eba45-229">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="eba45-229">2012 R2+</span></span>      | <span data-ttu-id="eba45-230">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-230">x64, x86</span></span>        |
| <span data-ttu-id="eba45-231">Nano Server</span><span class="sxs-lookup"><span data-stu-id="eba45-231">Nano Server</span></span>         | <span data-ttu-id="eba45-232">バージョン 1809+</span><span class="sxs-lookup"><span data-stu-id="eba45-232">Version 1809+</span></span> | <span data-ttu-id="eba45-233">X64</span><span class="sxs-lookup"><span data-stu-id="eba45-233">x64</span></span>             |

<span data-ttu-id="eba45-234">.NET 5.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)」 (.NET 5.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba45-234">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="eba45-235">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="eba45-235">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="eba45-236">.NET Core 3.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-236">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="eba45-237">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="eba45-237">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="eba45-238">OS</span><span class="sxs-lookup"><span data-stu-id="eba45-238">OS</span></span>                            | <span data-ttu-id="eba45-239">バージョン</span><span class="sxs-lookup"><span data-stu-id="eba45-239">Version</span></span>                        | <span data-ttu-id="eba45-240">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="eba45-240">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="eba45-241">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-241">Windows Client</span></span>                | <span data-ttu-id="eba45-242">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="eba45-242">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="eba45-243">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-243">x64, x86</span></span>        |
| <span data-ttu-id="eba45-244">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-244">Windows 10 Client</span></span>             | <span data-ttu-id="eba45-245">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="eba45-245">Version 1607+</span></span>                  | <span data-ttu-id="eba45-246">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-246">x64, x86</span></span>        |
| <span data-ttu-id="eba45-247">Windows Server</span><span class="sxs-lookup"><span data-stu-id="eba45-247">Windows Server</span></span>                | <span data-ttu-id="eba45-248">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="eba45-248">2012 R2+</span></span>                       | <span data-ttu-id="eba45-249">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-249">x64, x86</span></span>        |
| <span data-ttu-id="eba45-250">Nano Server</span><span class="sxs-lookup"><span data-stu-id="eba45-250">Nano Server</span></span>                   | <span data-ttu-id="eba45-251">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="eba45-251">Version 1803+</span></span>                  | <span data-ttu-id="eba45-252">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="eba45-252">x64, ARM32</span></span>      |

<span data-ttu-id="eba45-253">.NET Core 3.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)」(.NET Core 3.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba45-253">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="eba45-254">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="eba45-254">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="eba45-255">" *.NET Core 3.0 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="eba45-255">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="eba45-256">.NET Core 3.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-256">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="eba45-257">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="eba45-257">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="eba45-258">OS</span><span class="sxs-lookup"><span data-stu-id="eba45-258">OS</span></span>                            | <span data-ttu-id="eba45-259">バージョン</span><span class="sxs-lookup"><span data-stu-id="eba45-259">Version</span></span>                        | <span data-ttu-id="eba45-260">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="eba45-260">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="eba45-261">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-261">Windows Client</span></span>                | <span data-ttu-id="eba45-262">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="eba45-262">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="eba45-263">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-263">x64, x86</span></span>        |
| <span data-ttu-id="eba45-264">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-264">Windows 10 Client</span></span>             | <span data-ttu-id="eba45-265">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="eba45-265">Version 1607+</span></span>                  | <span data-ttu-id="eba45-266">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-266">x64, x86</span></span>        |
| <span data-ttu-id="eba45-267">Windows Server</span><span class="sxs-lookup"><span data-stu-id="eba45-267">Windows Server</span></span>                | <span data-ttu-id="eba45-268">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="eba45-268">2012 R2+</span></span>                       | <span data-ttu-id="eba45-269">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-269">x64, x86</span></span>        |
| <span data-ttu-id="eba45-270">Nano Server</span><span class="sxs-lookup"><span data-stu-id="eba45-270">Nano Server</span></span>                   | <span data-ttu-id="eba45-271">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="eba45-271">Version 1803+</span></span>                  | <span data-ttu-id="eba45-272">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="eba45-272">x64, ARM32</span></span>      |

<span data-ttu-id="eba45-273">.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)」(.NET Core 3.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba45-273">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="eba45-274">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="eba45-274">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="eba45-275">" *.NET Core 2.2 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="eba45-275">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="eba45-276">.NET Core 2.2 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-276">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="eba45-277">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="eba45-277">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="eba45-278">OS</span><span class="sxs-lookup"><span data-stu-id="eba45-278">OS</span></span>                            | <span data-ttu-id="eba45-279">バージョン</span><span class="sxs-lookup"><span data-stu-id="eba45-279">Version</span></span>                        | <span data-ttu-id="eba45-280">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="eba45-280">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="eba45-281">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-281">Windows Client</span></span>                | <span data-ttu-id="eba45-282">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="eba45-282">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="eba45-283">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-283">x64, x86</span></span>        |
| <span data-ttu-id="eba45-284">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-284">Windows 10 Client</span></span>             | <span data-ttu-id="eba45-285">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="eba45-285">Version 1607+</span></span>                  | <span data-ttu-id="eba45-286">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-286">x64, x86</span></span>        |
| <span data-ttu-id="eba45-287">Windows Server</span><span class="sxs-lookup"><span data-stu-id="eba45-287">Windows Server</span></span>                | <span data-ttu-id="eba45-288">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="eba45-288">2008 R2 SP1+</span></span>                   | <span data-ttu-id="eba45-289">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-289">x64, x86</span></span>        |
| <span data-ttu-id="eba45-290">Nano Server</span><span class="sxs-lookup"><span data-stu-id="eba45-290">Nano Server</span></span>                   | <span data-ttu-id="eba45-291">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="eba45-291">Version 1803+</span></span>                   | <span data-ttu-id="eba45-292">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="eba45-292">x64, ARM32</span></span>      |

<span data-ttu-id="eba45-293">.NET Core 2.2 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)」(.NET Core 2.2 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba45-293">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="eba45-294">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="eba45-294">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="eba45-295">.NET Core 2.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-295">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="eba45-296">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="eba45-296">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="eba45-297">OS</span><span class="sxs-lookup"><span data-stu-id="eba45-297">OS</span></span>                            | <span data-ttu-id="eba45-298">バージョン</span><span class="sxs-lookup"><span data-stu-id="eba45-298">Version</span></span>                        | <span data-ttu-id="eba45-299">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="eba45-299">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="eba45-300">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-300">Windows Client</span></span>                | <span data-ttu-id="eba45-301">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="eba45-301">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="eba45-302">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-302">x64, x86</span></span>        |
| <span data-ttu-id="eba45-303">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="eba45-303">Windows 10 Client</span></span>             | <span data-ttu-id="eba45-304">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="eba45-304">Version 1607+</span></span>                  | <span data-ttu-id="eba45-305">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-305">x64, x86</span></span>        |
| <span data-ttu-id="eba45-306">Windows Server</span><span class="sxs-lookup"><span data-stu-id="eba45-306">Windows Server</span></span>                | <span data-ttu-id="eba45-307">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="eba45-307">2008 R2 SP1+</span></span>                   | <span data-ttu-id="eba45-308">x64、x86</span><span class="sxs-lookup"><span data-stu-id="eba45-308">x64, x86</span></span>        |
| <span data-ttu-id="eba45-309">Nano Server</span><span class="sxs-lookup"><span data-stu-id="eba45-309">Nano Server</span></span>                   | <span data-ttu-id="eba45-310">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="eba45-310">Version 1803+</span></span>                  | <span data-ttu-id="eba45-311">x64、</span><span class="sxs-lookup"><span data-stu-id="eba45-311">x64,</span></span>            |

<span data-ttu-id="eba45-312">.NET Core 2.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)」(.NET Core 2.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba45-312">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="eba45-313">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eba45-313">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="eba45-314">次の Windows のバージョンに .NET SDK またはランタイムをインストールする場合は、追加の依存関係が必要です。</span><span class="sxs-lookup"><span data-stu-id="eba45-314">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="eba45-315">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="eba45-315">Windows 7 SP1 [ESU][esu]</span></span>
- <span data-ttu-id="eba45-316">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="eba45-316">Windows Vista SP 2</span></span>
- <span data-ttu-id="eba45-317">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="eba45-317">Windows 8.1</span></span>
- <span data-ttu-id="eba45-318">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="eba45-318">Windows Server 2008 R2</span></span>
- <span data-ttu-id="eba45-319">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="eba45-319">Windows Server 2012 R2</span></span>

<span data-ttu-id="eba45-320">以下をインストールします。</span><span class="sxs-lookup"><span data-stu-id="eba45-320">Install the following:</span></span>

- <span data-ttu-id="eba45-321">[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685)。</span><span class="sxs-lookup"><span data-stu-id="eba45-321">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="eba45-322">KB2533623</span><span class="sxs-lookup"><span data-stu-id="eba45-322">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="eba45-323">上記の要件は、次のいずれかのエラーが発生した場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="eba45-323">The previous requirements are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="eba45-324">お使いのコンピューターに *api-ms-win-crt-runtime-l1-1-0.dll* が見つからず、プログラムを開始できない。</span><span class="sxs-lookup"><span data-stu-id="eba45-324">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="eba45-325">この問題を解決するには、プログラムを再インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="eba45-325">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="eba45-326">\- または</span><span class="sxs-lookup"><span data-stu-id="eba45-326">\- or -</span></span>
>
> <span data-ttu-id="eba45-327">お使いのコンピューターに *api-ms-win-cor-timezone-l1-1-0.dll* が見つからず、プログラムを開始できない。</span><span class="sxs-lookup"><span data-stu-id="eba45-327">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="eba45-328">この問題を解決するには、プログラムを再インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="eba45-328">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="eba45-329">\- または</span><span class="sxs-lookup"><span data-stu-id="eba45-329">\- or -</span></span>
>
> <span data-ttu-id="eba45-330">ライブラリ *hostfxr.dll* は見つかったが、その *C:\\\<path_to_app>\\hostfxr.dll* からの読み込みに失敗した。</span><span class="sxs-lookup"><span data-stu-id="eba45-330">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="eba45-331">PowerShell オートメーションを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="eba45-331">Install with PowerShell automation</span></span>

<span data-ttu-id="eba45-332">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの CI 自動化および管理者以外によるインストールに使用されます。</span><span class="sxs-lookup"><span data-stu-id="eba45-332">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="eba45-333">スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="eba45-333">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="eba45-334">スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-334">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="eba45-335">`Channel` スイッチを指定することで、特定のリリースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="eba45-335">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="eba45-336">ランタイムをインストールするには、`Runtime` スイッチを含めます。</span><span class="sxs-lookup"><span data-stu-id="eba45-336">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="eba45-337">それ以外の場合は、スクリプトによって SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-337">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="eba45-338">`-Runtime` スイッチを省略して SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="eba45-338">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="eba45-339">この例では、`-Channel` スイッチが `Current` に設定されているため、サポートされている最新バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-339">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="eba45-340">Visual Studio を使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="eba45-340">Install with Visual Studio</span></span>

<span data-ttu-id="eba45-341">次の表で、Visual Studio を使用して .NET アプリを開発している場合に、ターゲットの .NET SDK バージョンに基づいて最低限必要な Visual Studio のバージョンを説明しています。</span><span class="sxs-lookup"><span data-stu-id="eba45-341">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="eba45-342">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="eba45-342">.NET SDK version</span></span>      | <span data-ttu-id="eba45-343">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="eba45-343">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="eba45-344">5.0</span><span class="sxs-lookup"><span data-stu-id="eba45-344">5.0</span></span>                   | <span data-ttu-id="eba45-345">Visual Studio 2019 バージョン 16.8 以降。</span><span class="sxs-lookup"><span data-stu-id="eba45-345">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="eba45-346">3.1</span><span class="sxs-lookup"><span data-stu-id="eba45-346">3.1</span></span>                   | <span data-ttu-id="eba45-347">Visual Studio 2019 バージョン 16.4 以降。</span><span class="sxs-lookup"><span data-stu-id="eba45-347">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="eba45-348">3.0</span><span class="sxs-lookup"><span data-stu-id="eba45-348">3.0</span></span>                   | <span data-ttu-id="eba45-349">Visual Studio 2019 バージョン 16.3 以降。</span><span class="sxs-lookup"><span data-stu-id="eba45-349">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="eba45-350">2.2</span><span class="sxs-lookup"><span data-stu-id="eba45-350">2.2</span></span>                   | <span data-ttu-id="eba45-351">Visual Studio 2017 バージョン 15.9 以降。</span><span class="sxs-lookup"><span data-stu-id="eba45-351">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="eba45-352">2.1</span><span class="sxs-lookup"><span data-stu-id="eba45-352">2.1</span></span>                   | <span data-ttu-id="eba45-353">Visual Studio 2017 バージョン 15.7 以降。</span><span class="sxs-lookup"><span data-stu-id="eba45-353">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="eba45-354">Visual Studio を既にインストールしてある場合は、次の手順でバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="eba45-354">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="eba45-355">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="eba45-355">Open Visual Studio.</span></span>
01. <span data-ttu-id="eba45-356">**[ヘルプ]**  >  **[Microsoft Visual Studio のバージョン情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="eba45-356">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="eba45-357">**[バージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="eba45-357">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="eba45-358">Visual Studio には、最新の .NET SDK とランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="eba45-358">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="eba45-359">[Visual Studio をダウンロードします](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="eba45-359">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="eba45-360">ワークロードを選択する</span><span class="sxs-lookup"><span data-stu-id="eba45-360">Select a workload</span></span>

<span data-ttu-id="eba45-361">Visual Studio をインストールまたは変更するときは、ビルドするアプリケーションの種類に応じて、次の 1 つ以上のワークロードを選択します。</span><span class="sxs-lookup"><span data-stu-id="eba45-361">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="eba45-362">**[他のツールセット]** セクションの **[.NET Core クロスプラットフォームの開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="eba45-362">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="eba45-363">**[Web クラウド]** セクションの **[ASP.NET と Web 開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="eba45-363">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="eba45-364">**[Web クラウド]** セクションの **[Azure の開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="eba45-364">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="eba45-365">**[デスクトップとモバイル]** セクションの **[.NET デスクトップ開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="eba45-365">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="eba45-366">[![Windows Visual Studio 2019 と .NET Core ワークロード](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="eba45-366">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="eba45-367">Visual Studio Code と共にインストールする</span><span class="sxs-lookup"><span data-stu-id="eba45-367">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="eba45-368">Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="eba45-368">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="eba45-369">Visual Studio Code は、Windows、macOS、Linux で利用できます。</span><span class="sxs-lookup"><span data-stu-id="eba45-369">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="eba45-370">Visual Studio Code には、Visual Studio のような自動化された .NET Core インストーラーは付属していませんが、.NET Core のサポートを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="eba45-370">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="eba45-371">[Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="eba45-371">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="eba45-372">[.NET Core SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="eba45-372">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="eba45-373">[Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="eba45-373">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="eba45-374">Windows インストーラー</span><span class="sxs-lookup"><span data-stu-id="eba45-374">Windows Installer</span></span>

<span data-ttu-id="eba45-375">.NET の[ダウンロード ページ](https://dotnet.microsoft.com/download/dotnet-core)には、Windows インストーラーの実行可能ファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eba45-375">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="eba45-376">MSI ファイルを使用して .NET をインストールする場合、`DOTNETHOME_X64` と `DOTNETHOME_X86` パラメーターを設定することによってインストール パスをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="eba45-376">When you use the MSI files to install .NET< you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

## <a name="download-and-manually-install"></a><span data-ttu-id="eba45-377">手動でダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="eba45-377">Download and manually install</span></span>

<span data-ttu-id="eba45-378">.NET 用 Windows インストーラーの代わりに、SDK またはランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="eba45-378">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="eba45-379">手動インストールは、通常、継続的インテグレーション テストの一環として実行されます。</span><span class="sxs-lookup"><span data-stu-id="eba45-379">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="eba45-380">開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet-core)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="eba45-380">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="eba45-381">.NET SDK と .NET ランタイムはどちらも、ダウンロード後に手動でインストールできます。</span><span class="sxs-lookup"><span data-stu-id="eba45-381">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="eba45-382">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="eba45-382">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="eba45-383">まず、次のいずれかのサイトから SDK またはランタイムのバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="eba45-383">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="eba45-384">.NET 5.0 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="eba45-384">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="eba45-385">.NET Core 3.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="eba45-385">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="eba45-386">.NET Core 2.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="eba45-386">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="eba45-387">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="eba45-387">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="eba45-388">.NET を抽出するためのディレクトリを作成します (`%USERPROFILE%\dotnet` など)。</span><span class="sxs-lookup"><span data-stu-id="eba45-388">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="eba45-389">次に、ダウンロードした zip ファイルをそのディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="eba45-389">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="eba45-390">既定では、この方法でインストールされた .NET は、.NET CLI コマンドおよびアプリから使用されないため、使用することを明示的に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eba45-390">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="eba45-391">これを行うには、アプリケーションの起動に使用する環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="eba45-391">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="eba45-392">この方法では、複数のバージョンを別々の場所にインストールして、その場所を参照する環境変数を使ってアプリケーションを実行することで、アプリケーションによって使用されるインストール場所を明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="eba45-392">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="eba45-393">`DOTNET_MULTILEVEL_LOOKUP` が `0` に設定されている場合、.NET により、グローバルにインストールされている .NET のバージョンはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="eba45-393">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="eba45-394">アプリケーションを実行するための最適なフレームワークを選択するときに、.NET によりグローバル インストールの既定の場所が考慮されるようにするには、その環境設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="eba45-394">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="eba45-395">通常、既定値は `C:\Program Files\dotnet` です。インストーラーによってここに .NET がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="eba45-395">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="eba45-396">Docker</span><span class="sxs-lookup"><span data-stu-id="eba45-396">Docker</span></span>

<span data-ttu-id="eba45-397">コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。</span><span class="sxs-lookup"><span data-stu-id="eba45-397">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="eba45-398">同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="eba45-398">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="eba45-399">.NET は Docker コンテナー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="eba45-399">.NET can run in a Docker container.</span></span> <span data-ttu-id="eba45-400">公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet)で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="eba45-400">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="eba45-401">各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eba45-401">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="eba45-402">Microsoft は、特定のシナリオに対応したイメージを用意しています。</span><span class="sxs-lookup"><span data-stu-id="eba45-402">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="eba45-403">たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="eba45-403">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="eba45-404">Docker コンテナー内で .NET を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="eba45-404">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="eba45-405">次のステップ</span><span class="sxs-lookup"><span data-stu-id="eba45-405">Next steps</span></span>

- <span data-ttu-id="eba45-406">[.NET が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="eba45-406">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="eba45-407">[チュートリアル: Hello World チュートリアル](../tutorials/with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="eba45-407">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="eba45-408">[チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="eba45-408">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="eba45-409">[チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="eba45-409">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
