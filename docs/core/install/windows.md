---
title: Windows に .NET をインストールする
description: .NET をインストールできる Windows のバージョンについて説明します。
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 786814549724948fa69b18a05cee966e0940aaf4
ms.sourcegitcommit: c6de55556add9f92af17e0f8d1da8f356a19a03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2020
ms.locfileid: "96549346"
---
# <a name="install-net-on-windows"></a><span data-ttu-id="ca337-103">Windows に .NET をインストールする</span><span class="sxs-lookup"><span data-stu-id="ca337-103">Install .NET on Windows</span></span>

> [!div class="op_single_selector"]
>
> - [Windows へのインストール](windows.md)
> - [macOS へのインストール](macos.md)
> - [Linux にインストールする](linux.md)

<span data-ttu-id="ca337-107">この記事では、Windows に .NET をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca337-107">In this article, you'll learn how to install .NET on Windows.</span></span> <span data-ttu-id="ca337-108">.NET は、ランタイムと SDK で構成されています。</span><span class="sxs-lookup"><span data-stu-id="ca337-108">.NET is made up of the runtime and the SDK.</span></span> <span data-ttu-id="ca337-109">ランタイムは .NET アプリを実行するために使用され、アプリに含まれている場合と含まれていない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca337-109">The runtime is used to run a .NET app and may or may not be included with the app.</span></span> <span data-ttu-id="ca337-110">SDK は、.NET アプリとライブラリの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca337-110">The SDK is used to create .NET apps and libraries.</span></span> <span data-ttu-id="ca337-111">.NET ランタイムは、常に SDK と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-111">The .NET runtime is always installed with the SDK.</span></span>

<span data-ttu-id="ca337-112">.NET の最新バージョンは 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="ca337-112">The latest version of .NET is 5.0.</span></span>

> [!div class="button"]
> [<span data-ttu-id="ca337-113">.NET をダウンロードする</span><span class="sxs-lookup"><span data-stu-id="ca337-113">Download .NET</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="supported-releases"></a><span data-ttu-id="ca337-114">サポートされているリリース</span><span class="sxs-lookup"><span data-stu-id="ca337-114">Supported releases</span></span>

<span data-ttu-id="ca337-115">以下の表は、現在サポートされている .NET リリースと、それらがサポートされている Windows のバージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="ca337-115">The following table is a list of currently supported .NET releases and the versions of Windows they're supported on.</span></span> <span data-ttu-id="ca337-116">これらのバージョンは、[.NET のバージョンがサポート終了](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)するか、[Windows のバージョンの有効期限が切れるまで](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)サポートされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-116">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Windows reaches end-of-life](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet).</span></span>

<span data-ttu-id="ca337-117">Windows 10 のバージョンのサービス終了日は、エディションごとに分かれています。</span><span class="sxs-lookup"><span data-stu-id="ca337-117">Windows 10 versions end-of-service dates are segmented by edition.</span></span> <span data-ttu-id="ca337-118">次の表では、**Home**、**Pro**、**Pro Education**、**Pro for Workstations** の各エディションだけが考慮されています。</span><span class="sxs-lookup"><span data-stu-id="ca337-118">Only **Home**, **Pro**, **Pro Education**, and **Pro for Workstations** editions are considered in the following table.</span></span> <span data-ttu-id="ca337-119">具体的な詳細については、「[Windows ライフサイクルのファクト シート](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)」を確認してください。</span><span class="sxs-lookup"><span data-stu-id="ca337-119">Check the [Windows lifecycle fact sheet](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) for specific details.</span></span>

> [!TIP]
> <span data-ttu-id="ca337-120">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="ca337-120">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ca337-121">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="ca337-121">Operating System</span></span>            | <span data-ttu-id="ca337-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ca337-122">.NET Core 2.1</span></span> | <span data-ttu-id="ca337-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ca337-123">.NET Core 3.1</span></span> | <span data-ttu-id="ca337-124">.NET 5</span><span class="sxs-lookup"><span data-stu-id="ca337-124">.NET 5</span></span> |
|-----------------------------|---------------|---------------|--------|
| <span data-ttu-id="ca337-125">Windows 10 バージョン 2004</span><span class="sxs-lookup"><span data-stu-id="ca337-125">Windows 10, Version 2004</span></span>    | <span data-ttu-id="ca337-126">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-126">✔️</span></span>           | <span data-ttu-id="ca337-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-127">✔️</span></span>            | <span data-ttu-id="ca337-128">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-128">✔️</span></span>    |
| <span data-ttu-id="ca337-129">Windows 10 バージョン 1909</span><span class="sxs-lookup"><span data-stu-id="ca337-129">Windows 10, Version 1909</span></span>    | <span data-ttu-id="ca337-130">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-130">✔️</span></span>           | <span data-ttu-id="ca337-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-131">✔️</span></span>            | <span data-ttu-id="ca337-132">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-132">✔️</span></span>    |
| <span data-ttu-id="ca337-133">Windows 10 バージョン 1903</span><span class="sxs-lookup"><span data-stu-id="ca337-133">Windows 10, Version 1903</span></span>    | <span data-ttu-id="ca337-134">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-134">✔️</span></span>           | <span data-ttu-id="ca337-135">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-135">✔️</span></span>            | <span data-ttu-id="ca337-136">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-136">✔️</span></span>    |
| <span data-ttu-id="ca337-137">Windows 10 バージョン 1809</span><span class="sxs-lookup"><span data-stu-id="ca337-137">Windows 10, Version 1809</span></span>    | <span data-ttu-id="ca337-138">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-138">✔️</span></span>           | <span data-ttu-id="ca337-139">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-139">✔️</span></span>            | <span data-ttu-id="ca337-140">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-140">✔️</span></span>    |
| <span data-ttu-id="ca337-141"> Windows 10 バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="ca337-141">Windows 10, Version 1803</span></span>    | <span data-ttu-id="ca337-142">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-142">✔️</span></span>           | <span data-ttu-id="ca337-143">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-143">✔️</span></span>            | <span data-ttu-id="ca337-144">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-144">✔️</span></span>    |
| <span data-ttu-id="ca337-145">Windows 10 バージョン 1709</span><span class="sxs-lookup"><span data-stu-id="ca337-145">Windows 10, Version 1709</span></span>    | <span data-ttu-id="ca337-146">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-146">✔️</span></span>           | <span data-ttu-id="ca337-147">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-147">✔️</span></span>            | <span data-ttu-id="ca337-148">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-148">✔️</span></span>    |
| <span data-ttu-id="ca337-149">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="ca337-149">Windows 10, Version 1607</span></span>    | <span data-ttu-id="ca337-150">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-150">✔️</span></span>           | <span data-ttu-id="ca337-151">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-151">✔️</span></span>            | <span data-ttu-id="ca337-152">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-152">✔️</span></span>    |
| <span data-ttu-id="ca337-153">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ca337-153">Windows 8.1</span></span>                 | <span data-ttu-id="ca337-154">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-154">✔️</span></span>           | <span data-ttu-id="ca337-155">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-155">✔️</span></span>            | <span data-ttu-id="ca337-156">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-156">✔️</span></span>    |
| <span data-ttu-id="ca337-157">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="ca337-157">Windows 7 SP1 [ESU][esu]</span></span>    | <span data-ttu-id="ca337-158">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-158">✔️</span></span>           | <span data-ttu-id="ca337-159">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-159">✔️</span></span>            | <span data-ttu-id="ca337-160">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-160">✔️</span></span>    |
| <span data-ttu-id="ca337-161">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="ca337-161">Windows 10, Version 1607</span></span>    | <span data-ttu-id="ca337-162">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-162">✔️</span></span>           | <span data-ttu-id="ca337-163">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-163">✔️</span></span>            | <span data-ttu-id="ca337-164">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-164">✔️</span></span>    |
| <span data-ttu-id="ca337-165">Windows 10 バージョン 1607</span><span class="sxs-lookup"><span data-stu-id="ca337-165">Windows 10, Version 1607</span></span>    | <span data-ttu-id="ca337-166">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-166">✔️</span></span>           | <span data-ttu-id="ca337-167">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-167">✔️</span></span>            | <span data-ttu-id="ca337-168">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-168">✔️</span></span>    |
| <span data-ttu-id="ca337-169">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ca337-169">Windows Server 2012 R2</span></span>      | <span data-ttu-id="ca337-170">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-170">✔️</span></span>           | <span data-ttu-id="ca337-171">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-171">✔️</span></span>            | <span data-ttu-id="ca337-172">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-172">✔️</span></span>    |
| <span data-ttu-id="ca337-173">Windows Server Core 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ca337-173">Windows Server Core 2012 R2</span></span> | <span data-ttu-id="ca337-174">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-174">✔️</span></span>           | <span data-ttu-id="ca337-175">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-175">✔️</span></span>            | <span data-ttu-id="ca337-176">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-176">✔️</span></span>    |
| <span data-ttu-id="ca337-177">Nano Server バージョン 1809 以上</span><span class="sxs-lookup"><span data-stu-id="ca337-177">Nano Server, Version 1809+</span></span>  | <span data-ttu-id="ca337-178">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-178">✔️</span></span>           | <span data-ttu-id="ca337-179">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-179">✔️</span></span>            | <span data-ttu-id="ca337-180">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-180">✔️</span></span>    |
| <span data-ttu-id="ca337-181">Nano Server バージョン 1803</span><span class="sxs-lookup"><span data-stu-id="ca337-181">Nano Server, Version 1803</span></span>   | <span data-ttu-id="ca337-182">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-182">✔️</span></span>           | <span data-ttu-id="ca337-183">✔️</span><span class="sxs-lookup"><span data-stu-id="ca337-183">✔️</span></span>            | ❌    |

## <a name="unsupported-releases"></a><span data-ttu-id="ca337-184">サポートされていないリリース</span><span class="sxs-lookup"><span data-stu-id="ca337-184">Unsupported releases</span></span>

<span data-ttu-id="ca337-185">次のバージョンの .NET は、❌ サポート対象外となりました。</span><span class="sxs-lookup"><span data-stu-id="ca337-185">The following versions of .NET are ❌ no longer supported.</span></span> <span data-ttu-id="ca337-186">これらのダウンロードは、まだ公開されています。</span><span class="sxs-lookup"><span data-stu-id="ca337-186">The downloads for these still remain published:</span></span>

- <span data-ttu-id="ca337-187">3.0</span><span class="sxs-lookup"><span data-stu-id="ca337-187">3.0</span></span>
- <span data-ttu-id="ca337-188">2.2</span><span class="sxs-lookup"><span data-stu-id="ca337-188">2.2</span></span>
- <span data-ttu-id="ca337-189">2.0</span><span class="sxs-lookup"><span data-stu-id="ca337-189">2.0</span></span>

## <a name="runtime-information"></a><span data-ttu-id="ca337-190">ランタイムに関する情報</span><span class="sxs-lookup"><span data-stu-id="ca337-190">Runtime information</span></span>

<span data-ttu-id="ca337-191">ランタイムは、.NET で作成されたアプリを実行するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca337-191">The runtime is used to run apps created with .NET.</span></span> <span data-ttu-id="ca337-192">アプリの作成者は、アプリを公開するとき、アプリにランタイムを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ca337-192">When an app author publishes an app, they can include the runtime with their app.</span></span> <span data-ttu-id="ca337-193">ランタイムが含まれていない場合は、ユーザーがランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca337-193">If they don't include the runtime, it's up to the user to install the runtime.</span></span>

<span data-ttu-id="ca337-194">Windows には、3 つの異なるランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ca337-194">There are three different runtimes you can install on Windows:</span></span>

<span data-ttu-id="ca337-195">*ASP.NET Core ランタイム*</span><span class="sxs-lookup"><span data-stu-id="ca337-195">*ASP.NET Core runtime*</span></span>\
<span data-ttu-id="ca337-196">ASP.NET Core アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ca337-196">Runs ASP.NET Core apps.</span></span> <span data-ttu-id="ca337-197">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ca337-197">Includes the .NET runtime.</span></span>

<span data-ttu-id="ca337-198">*Desktop ランタイム*</span><span class="sxs-lookup"><span data-stu-id="ca337-198">*Desktop runtime*</span></span>\
<span data-ttu-id="ca337-199">Windows 用の .NET WPF と Windows フォームのデスクトップ アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="ca337-199">Runs .NET WPF and Windows Forms desktop apps for Windows.</span></span> <span data-ttu-id="ca337-200">.NET ランタイムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ca337-200">Includes the .NET runtime.</span></span>

<span data-ttu-id="ca337-201">*.NET ランタイム*</span><span class="sxs-lookup"><span data-stu-id="ca337-201">*.NET runtime*</span></span>\
<span data-ttu-id="ca337-202">このランタイムは最も単純なランタイムであり、他のランタイムは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="ca337-202">This runtime is the simplest runtime and doesn't include any other runtime.</span></span> <span data-ttu-id="ca337-203">.NET アプリとの互換性を最善にするには、"*ASP.NET Core ランタイム*" と "*Desktop ランタイム*" の両方をインストールすることを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ca337-203">It's highly recommended that you install both *ASP.NET Core runtime* and *Desktop runtime* for the best compatibility with .NET apps.</span></span>

> [!div class="button"]
> [<span data-ttu-id="ca337-204">.NET ランタイムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="ca337-204">Download .NET Runtime</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

## <a name="sdk-information"></a><span data-ttu-id="ca337-205">SDK に関する情報</span><span class="sxs-lookup"><span data-stu-id="ca337-205">SDK information</span></span>

<span data-ttu-id="ca337-206">SDK は、.NET アプリとライブラリを作成して公開するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca337-206">The SDK is used to build and publish .NET apps and libraries.</span></span> <span data-ttu-id="ca337-207">SDK のインストールには、次の 3 つの[ランタイム](#runtime-information)が含まれます: ASP.NET Core、Desktop、.NET。</span><span class="sxs-lookup"><span data-stu-id="ca337-207">Installing the SDK includes all three [runtimes](#runtime-information): ASP.NET Core, Desktop, and .NET.</span></span>

## <a name="dependencies"></a><span data-ttu-id="ca337-208">依存関係</span><span class="sxs-lookup"><span data-stu-id="ca337-208">Dependencies</span></span>

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-50"></a>[<span data-ttu-id="ca337-209">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="ca337-209">.NET 5.0</span></span>](#tab/net50)

<span data-ttu-id="ca337-210">.NET 5.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-210">The following Windows versions are supported with .NET 5.0:</span></span>

> [!NOTE]
> <span data-ttu-id="ca337-211">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="ca337-211">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ca337-212">OS</span><span class="sxs-lookup"><span data-stu-id="ca337-212">OS</span></span>                  | <span data-ttu-id="ca337-213">バージョン</span><span class="sxs-lookup"><span data-stu-id="ca337-213">Version</span></span>       | <span data-ttu-id="ca337-214">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ca337-214">Architectures</span></span>   |
|---------------------|---------------|-----------------|
| <span data-ttu-id="ca337-215">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-215">Windows 10 Client</span></span>   | <span data-ttu-id="ca337-216">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="ca337-216">Version 1607+</span></span> | <span data-ttu-id="ca337-217">x64、x86、ARM64</span><span class="sxs-lookup"><span data-stu-id="ca337-217">x64, x86, ARM64</span></span> |
| <span data-ttu-id="ca337-218">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-218">Windows Client</span></span>      | <span data-ttu-id="ca337-219">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="ca337-219">7 SP1+, 8.1</span></span>   | <span data-ttu-id="ca337-220">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-220">x64, x86</span></span>        |
| <span data-ttu-id="ca337-221">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ca337-221">Windows Server</span></span>      | <span data-ttu-id="ca337-222">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="ca337-222">2012 R2+</span></span>      | <span data-ttu-id="ca337-223">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-223">x64, x86</span></span>        |
| <span data-ttu-id="ca337-224">Windows サーバー コア</span><span class="sxs-lookup"><span data-stu-id="ca337-224">Windows Server Core</span></span> | <span data-ttu-id="ca337-225">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="ca337-225">2012 R2+</span></span>      | <span data-ttu-id="ca337-226">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-226">x64, x86</span></span>        |
| <span data-ttu-id="ca337-227">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ca337-227">Nano Server</span></span>         | <span data-ttu-id="ca337-228">バージョン 1809+</span><span class="sxs-lookup"><span data-stu-id="ca337-228">Version 1809+</span></span> | <span data-ttu-id="ca337-229">X64</span><span class="sxs-lookup"><span data-stu-id="ca337-229">x64</span></span>             |

<span data-ttu-id="ca337-230">.NET 5.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md)」 (.NET 5.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca337-230">For more information about .NET 5.0 supported operating systems, distributions, and lifecycle policy, see [.NET 5.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/5.0/5.0-supported-os.md).</span></span>

# <a name="net-core-31"></a>[<span data-ttu-id="ca337-231">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ca337-231">.NET Core 3.1</span></span>](#tab/netcore31)

<span data-ttu-id="ca337-232">.NET Core 3.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-232">The following Windows versions are supported with .NET Core 3.1:</span></span>

> [!NOTE]
> <span data-ttu-id="ca337-233">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="ca337-233">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ca337-234">OS</span><span class="sxs-lookup"><span data-stu-id="ca337-234">OS</span></span>                            | <span data-ttu-id="ca337-235">バージョン</span><span class="sxs-lookup"><span data-stu-id="ca337-235">Version</span></span>                        | <span data-ttu-id="ca337-236">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ca337-236">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ca337-237">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-237">Windows Client</span></span>                | <span data-ttu-id="ca337-238">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="ca337-238">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ca337-239">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-239">x64, x86</span></span>        |
| <span data-ttu-id="ca337-240">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-240">Windows 10 Client</span></span>             | <span data-ttu-id="ca337-241">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="ca337-241">Version 1607+</span></span>                  | <span data-ttu-id="ca337-242">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-242">x64, x86</span></span>        |
| <span data-ttu-id="ca337-243">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ca337-243">Windows Server</span></span>                | <span data-ttu-id="ca337-244">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="ca337-244">2012 R2+</span></span>                       | <span data-ttu-id="ca337-245">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-245">x64, x86</span></span>        |
| <span data-ttu-id="ca337-246">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ca337-246">Nano Server</span></span>                   | <span data-ttu-id="ca337-247">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="ca337-247">Version 1803+</span></span>                  | <span data-ttu-id="ca337-248">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="ca337-248">x64, ARM32</span></span>      |

<span data-ttu-id="ca337-249">.NET Core 3.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)」(.NET Core 3.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca337-249">For more information about .NET Core 3.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).</span></span>

# <a name="net-core-30"></a>[<span data-ttu-id="ca337-250">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ca337-250">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="ca337-251">" *.NET Core 3.0 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="ca337-251">*.NET Core 3.0 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="ca337-252">.NET Core 3.0 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-252">The following Windows versions are supported with .NET Core 3.0:</span></span>

> [!NOTE]
> <span data-ttu-id="ca337-253">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="ca337-253">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ca337-254">OS</span><span class="sxs-lookup"><span data-stu-id="ca337-254">OS</span></span>                            | <span data-ttu-id="ca337-255">バージョン</span><span class="sxs-lookup"><span data-stu-id="ca337-255">Version</span></span>                        | <span data-ttu-id="ca337-256">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ca337-256">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ca337-257">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-257">Windows Client</span></span>                | <span data-ttu-id="ca337-258">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="ca337-258">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ca337-259">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-259">x64, x86</span></span>        |
| <span data-ttu-id="ca337-260">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-260">Windows 10 Client</span></span>             | <span data-ttu-id="ca337-261">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="ca337-261">Version 1607+</span></span>                  | <span data-ttu-id="ca337-262">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-262">x64, x86</span></span>        |
| <span data-ttu-id="ca337-263">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ca337-263">Windows Server</span></span>                | <span data-ttu-id="ca337-264">2012 R2+</span><span class="sxs-lookup"><span data-stu-id="ca337-264">2012 R2+</span></span>                       | <span data-ttu-id="ca337-265">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-265">x64, x86</span></span>        |
| <span data-ttu-id="ca337-266">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ca337-266">Nano Server</span></span>                   | <span data-ttu-id="ca337-267">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="ca337-267">Version 1803+</span></span>                  | <span data-ttu-id="ca337-268">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="ca337-268">x64, ARM32</span></span>      |

<span data-ttu-id="ca337-269">.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)」(.NET Core 3.0 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca337-269">For more information about .NET Core 3.0 supported operating systems, distributions, and lifecycle policy, see [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).</span></span>

# <a name="net-core-22"></a>[<span data-ttu-id="ca337-270">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="ca337-270">.NET Core 2.2</span></span>](#tab/netcore22)

<span data-ttu-id="ca337-271">" *.NET Core 2.2 は現在 ❌ サポートされていません。詳細については、「[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)」をご覧ください。* "</span><span class="sxs-lookup"><span data-stu-id="ca337-271">*.NET Core 2.2 is currently ❌ out of support. For more information, see the [.NET Core Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*</span></span>

<span data-ttu-id="ca337-272">.NET Core 2.2 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-272">The following Windows versions are supported with .NET Core 2.2:</span></span>

> [!NOTE]
> <span data-ttu-id="ca337-273">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="ca337-273">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ca337-274">OS</span><span class="sxs-lookup"><span data-stu-id="ca337-274">OS</span></span>                            | <span data-ttu-id="ca337-275">バージョン</span><span class="sxs-lookup"><span data-stu-id="ca337-275">Version</span></span>                        | <span data-ttu-id="ca337-276">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ca337-276">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ca337-277">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-277">Windows Client</span></span>                | <span data-ttu-id="ca337-278">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="ca337-278">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ca337-279">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-279">x64, x86</span></span>        |
| <span data-ttu-id="ca337-280">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-280">Windows 10 Client</span></span>             | <span data-ttu-id="ca337-281">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="ca337-281">Version 1607+</span></span>                  | <span data-ttu-id="ca337-282">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-282">x64, x86</span></span>        |
| <span data-ttu-id="ca337-283">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ca337-283">Windows Server</span></span>                | <span data-ttu-id="ca337-284">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="ca337-284">2008 R2 SP1+</span></span>                   | <span data-ttu-id="ca337-285">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-285">x64, x86</span></span>        |
| <span data-ttu-id="ca337-286">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ca337-286">Nano Server</span></span>                   | <span data-ttu-id="ca337-287">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="ca337-287">Version 1803+</span></span>                   | <span data-ttu-id="ca337-288">x64、ARM32</span><span class="sxs-lookup"><span data-stu-id="ca337-288">x64, ARM32</span></span>      |

<span data-ttu-id="ca337-289">.NET Core 2.2 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)」(.NET Core 2.2 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca337-289">For more information about .NET Core 2.2 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="ca337-290">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ca337-290">.NET Core 2.1</span></span>](#tab/netcore21)

<span data-ttu-id="ca337-291">.NET Core 2.1 では以下の Windows のバージョンがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-291">The following Windows versions are supported with .NET Core 2.1:</span></span>

> [!NOTE]
> <span data-ttu-id="ca337-292">`+` 記号は、最小バージョンを表します。</span><span class="sxs-lookup"><span data-stu-id="ca337-292">A `+` symbol represents the minimum version.</span></span>

| <span data-ttu-id="ca337-293">OS</span><span class="sxs-lookup"><span data-stu-id="ca337-293">OS</span></span>                            | <span data-ttu-id="ca337-294">バージョン</span><span class="sxs-lookup"><span data-stu-id="ca337-294">Version</span></span>                        | <span data-ttu-id="ca337-295">アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="ca337-295">Architectures</span></span>   |
| ----------------------------- | ------------------------------ | --------------- |
| <span data-ttu-id="ca337-296">Windows クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-296">Windows Client</span></span>                | <span data-ttu-id="ca337-297">7 SP1+、8.1</span><span class="sxs-lookup"><span data-stu-id="ca337-297">7 SP1+, 8.1</span></span>                    | <span data-ttu-id="ca337-298">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-298">x64, x86</span></span>        |
| <span data-ttu-id="ca337-299">Windows 10 クライアント</span><span class="sxs-lookup"><span data-stu-id="ca337-299">Windows 10 Client</span></span>             | <span data-ttu-id="ca337-300">バージョン 1607+</span><span class="sxs-lookup"><span data-stu-id="ca337-300">Version 1607+</span></span>                  | <span data-ttu-id="ca337-301">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-301">x64, x86</span></span>        |
| <span data-ttu-id="ca337-302">Windows Server</span><span class="sxs-lookup"><span data-stu-id="ca337-302">Windows Server</span></span>                | <span data-ttu-id="ca337-303">2008 R2 SP1+</span><span class="sxs-lookup"><span data-stu-id="ca337-303">2008 R2 SP1+</span></span>                   | <span data-ttu-id="ca337-304">x64、x86</span><span class="sxs-lookup"><span data-stu-id="ca337-304">x64, x86</span></span>        |
| <span data-ttu-id="ca337-305">Nano Server</span><span class="sxs-lookup"><span data-stu-id="ca337-305">Nano Server</span></span>                   | <span data-ttu-id="ca337-306">バージョン 1803+</span><span class="sxs-lookup"><span data-stu-id="ca337-306">Version 1803+</span></span>                  | <span data-ttu-id="ca337-307">x64、</span><span class="sxs-lookup"><span data-stu-id="ca337-307">x64,</span></span>            |

<span data-ttu-id="ca337-308">.NET Core 2.1 でサポートされているオペレーティング システム、ディストリビューション、ライフサイクル ポリシーの詳細については、「[.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)」(.NET Core 2.1 でサポートされている OS バージョン) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca337-308">For more information about .NET Core 2.1 supported operating systems, distributions, and lifecycle policy, see [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).</span></span>

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a> <span data-ttu-id="ca337-309">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ca337-309">Windows 7 / Vista / 8.1 / Server 2008 R2 / Server 2012 R2</span></span>

<span data-ttu-id="ca337-310">次の Windows のバージョンに .NET SDK またはランタイムをインストールする場合は、追加の依存関係が必要です。</span><span class="sxs-lookup"><span data-stu-id="ca337-310">Additional dependencies are required if you're installing the .NET SDK or runtime on the following Windows versions:</span></span>

- <span data-ttu-id="ca337-311">Windows 7 SP1 [ESU][esu]</span><span class="sxs-lookup"><span data-stu-id="ca337-311">Windows 7 SP1 [ESU][esu]</span></span>
- <span data-ttu-id="ca337-312">Windows Vista SP 2</span><span class="sxs-lookup"><span data-stu-id="ca337-312">Windows Vista SP 2</span></span>
- <span data-ttu-id="ca337-313">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="ca337-313">Windows 8.1</span></span>
- <span data-ttu-id="ca337-314">Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="ca337-314">Windows Server 2008 R2</span></span>
- <span data-ttu-id="ca337-315">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="ca337-315">Windows Server 2012 R2</span></span>

<span data-ttu-id="ca337-316">以下をインストールします。</span><span class="sxs-lookup"><span data-stu-id="ca337-316">Install the following:</span></span>

- <span data-ttu-id="ca337-317">[Microsoft Visual C++ 2015 再頒布可能パッケージ Update 3](https://www.microsoft.com/download/details.aspx?id=52685)。</span><span class="sxs-lookup"><span data-stu-id="ca337-317">[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685).</span></span>
- [<span data-ttu-id="ca337-318">KB2533623</span><span class="sxs-lookup"><span data-stu-id="ca337-318">KB2533623</span></span>](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

<span data-ttu-id="ca337-319">上記の要件は、次のいずれかのエラーが発生した場合にも必要です。</span><span class="sxs-lookup"><span data-stu-id="ca337-319">The previous requirements are also required if you come across one of the following errors:</span></span>

> <span data-ttu-id="ca337-320">お使いのコンピューターに *api-ms-win-crt-runtime-l1-1-0.dll* が見つからず、プログラムを開始できない。</span><span class="sxs-lookup"><span data-stu-id="ca337-320">The program can't start because *api-ms-win-crt-runtime-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="ca337-321">この問題を解決するには、プログラムを再インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="ca337-321">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="ca337-322">\- または</span><span class="sxs-lookup"><span data-stu-id="ca337-322">\- or -</span></span>
>
> <span data-ttu-id="ca337-323">お使いのコンピューターに *api-ms-win-cor-timezone-l1-1-0.dll* が見つからず、プログラムを開始できない。</span><span class="sxs-lookup"><span data-stu-id="ca337-323">The program can't start because *api-ms-win-cor-timezone-l1-1-0.dll* is missing from your computer.</span></span> <span data-ttu-id="ca337-324">この問題を解決するには、プログラムを再インストールしてください。</span><span class="sxs-lookup"><span data-stu-id="ca337-324">Try reinstalling the program to fix this problem.</span></span>
>
> <span data-ttu-id="ca337-325">\- または</span><span class="sxs-lookup"><span data-stu-id="ca337-325">\- or -</span></span>
>
> <span data-ttu-id="ca337-326">ライブラリ *hostfxr.dll* は見つかったが、その *C:\\\<path_to_app>\\hostfxr.dll* からの読み込みに失敗した。</span><span class="sxs-lookup"><span data-stu-id="ca337-326">The library *hostfxr.dll* was found, but loading it from *C:\\\<path_to_app>\\hostfxr.dll* failed.</span></span>

## <a name="install-with-powershell-automation"></a><span data-ttu-id="ca337-327">PowerShell オートメーションを使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="ca337-327">Install with PowerShell automation</span></span>

<span data-ttu-id="ca337-328">[dotnet-install スクリプト](../tools/dotnet-install-script.md)は、ランタイムの CI 自動化および管理者以外によるインストールに使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca337-328">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for CI automation and non-admin installs of the runtime.</span></span> <span data-ttu-id="ca337-329">スクリプトは、[dotnet-install スクリプト参照ページ](../tools/dotnet-install-script.md)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ca337-329">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="ca337-330">スクリプトでは、既定で最新の [長期サポート (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) バージョン (.NET Core 3.1) がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-330">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 3.1.</span></span> <span data-ttu-id="ca337-331">`Channel` スイッチを指定することで、特定のリリースを選択できます。</span><span class="sxs-lookup"><span data-stu-id="ca337-331">You can choose a specific release by specifying the `Channel` switch.</span></span> <span data-ttu-id="ca337-332">ランタイムをインストールするには、`Runtime` スイッチを含めます。</span><span class="sxs-lookup"><span data-stu-id="ca337-332">Include the `Runtime` switch to install a runtime.</span></span> <span data-ttu-id="ca337-333">それ以外の場合は、スクリプトによって SDK がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-333">Otherwise, the script installs the SDK.</span></span>

```powershell
dotnet-install.ps1 -Channel 5.0 -Runtime aspnetcore
```

<span data-ttu-id="ca337-334">`-Runtime` スイッチを省略して SDK をインストールします。</span><span class="sxs-lookup"><span data-stu-id="ca337-334">Install the SDK by omitting the `-Runtime` switch.</span></span> <span data-ttu-id="ca337-335">この例では、`-Channel` スイッチが `Current` に設定されているため、サポートされている最新バージョンがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-335">The `-Channel` switch is set in this example to `Current`, which installs the latest supported version.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

## <a name="install-with-visual-studio"></a><span data-ttu-id="ca337-336">Visual Studio を使用してインストールする</span><span class="sxs-lookup"><span data-stu-id="ca337-336">Install with Visual Studio</span></span>

<span data-ttu-id="ca337-337">次の表で、Visual Studio を使用して .NET アプリを開発している場合に、ターゲットの .NET SDK バージョンに基づいて最低限必要な Visual Studio のバージョンを説明しています。</span><span class="sxs-lookup"><span data-stu-id="ca337-337">If you're using Visual Studio to develop .NET apps, the following table describes the minimum required version of Visual Studio based on the target .NET SDK version.</span></span>

| <span data-ttu-id="ca337-338">.NET SDK バージョン</span><span class="sxs-lookup"><span data-stu-id="ca337-338">.NET SDK version</span></span>      | <span data-ttu-id="ca337-339">Visual Studio のバージョン</span><span class="sxs-lookup"><span data-stu-id="ca337-339">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="ca337-340">5.0</span><span class="sxs-lookup"><span data-stu-id="ca337-340">5.0</span></span>                   | <span data-ttu-id="ca337-341">Visual Studio 2019 バージョン 16.8 以降。</span><span class="sxs-lookup"><span data-stu-id="ca337-341">Visual Studio 2019 version 16.8 or higher.</span></span> |
| <span data-ttu-id="ca337-342">3.1</span><span class="sxs-lookup"><span data-stu-id="ca337-342">3.1</span></span>                   | <span data-ttu-id="ca337-343">Visual Studio 2019 バージョン 16.4 以降。</span><span class="sxs-lookup"><span data-stu-id="ca337-343">Visual Studio 2019 version 16.4 or higher.</span></span> |
| <span data-ttu-id="ca337-344">3.0</span><span class="sxs-lookup"><span data-stu-id="ca337-344">3.0</span></span>                   | <span data-ttu-id="ca337-345">Visual Studio 2019 バージョン 16.3 以降。</span><span class="sxs-lookup"><span data-stu-id="ca337-345">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="ca337-346">2.2</span><span class="sxs-lookup"><span data-stu-id="ca337-346">2.2</span></span>                   | <span data-ttu-id="ca337-347">Visual Studio 2017 バージョン 15.9 以降。</span><span class="sxs-lookup"><span data-stu-id="ca337-347">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="ca337-348">2.1</span><span class="sxs-lookup"><span data-stu-id="ca337-348">2.1</span></span>                   | <span data-ttu-id="ca337-349">Visual Studio 2017 バージョン 15.7 以降。</span><span class="sxs-lookup"><span data-stu-id="ca337-349">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="ca337-350">Visual Studio を既にインストールしてある場合は、次の手順でバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="ca337-350">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="ca337-351">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="ca337-351">Open Visual Studio.</span></span>
01. <span data-ttu-id="ca337-352">**[ヘルプ]**  >  **[Microsoft Visual Studio のバージョン情報]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ca337-352">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="ca337-353">**[バージョン情報]** ダイアログで、バージョン番号を確認します。</span><span class="sxs-lookup"><span data-stu-id="ca337-353">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="ca337-354">Visual Studio には、最新の .NET SDK とランタイムをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ca337-354">Visual Studio can install the latest .NET SDK and runtime.</span></span>

> [!div class="button"]
> <span data-ttu-id="ca337-355">[Visual Studio をダウンロードします](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="ca337-355">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="ca337-356">ワークロードを選択する</span><span class="sxs-lookup"><span data-stu-id="ca337-356">Select a workload</span></span>

<span data-ttu-id="ca337-357">Visual Studio をインストールまたは変更するときは、ビルドするアプリケーションの種類に応じて、次の 1 つ以上のワークロードを選択します。</span><span class="sxs-lookup"><span data-stu-id="ca337-357">When installing or modifying Visual Studio, select one or more of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="ca337-358">**[他のツールセット]** セクションの **[.NET Core クロスプラットフォームの開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="ca337-358">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="ca337-359">**[Web クラウド]** セクションの **[ASP.NET と Web 開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="ca337-359">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="ca337-360">**[Web クラウド]** セクションの **[Azure の開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="ca337-360">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="ca337-361">**[デスクトップとモバイル]** セクションの **[.NET デスクトップ開発]** ワークロード。</span><span class="sxs-lookup"><span data-stu-id="ca337-361">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="ca337-362">[![Windows Visual Studio 2019 と .NET Core ワークロード](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="ca337-362">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

## <a name="install-alongside-visual-studio-code"></a><span data-ttu-id="ca337-363">Visual Studio Code と共にインストールする</span><span class="sxs-lookup"><span data-stu-id="ca337-363">Install alongside Visual Studio Code</span></span>

<span data-ttu-id="ca337-364">Visual Studio Code は、デスクトップ上で動作する強力で軽量なソース コード エディターです。</span><span class="sxs-lookup"><span data-stu-id="ca337-364">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="ca337-365">Visual Studio Code は、Windows、macOS、Linux で利用できます。</span><span class="sxs-lookup"><span data-stu-id="ca337-365">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="ca337-366">Visual Studio Code には、Visual Studio のような自動化された .NET Core インストーラーは付属していませんが、.NET Core のサポートを簡単に追加できます。</span><span class="sxs-lookup"><span data-stu-id="ca337-366">While Visual Studio Code doesn't come with an automated .NET Core installer like Visual Studio does, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="ca337-367">[Visual Studio Code をダウンロードしてインストールします](https://code.visualstudio.com/Download)。</span><span class="sxs-lookup"><span data-stu-id="ca337-367">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="ca337-368">[.NET Core SDK をダウンロードしてインストールします](https://dotnet.microsoft.com/download/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="ca337-368">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).</span></span>
01. <span data-ttu-id="ca337-369">[Visual Studio Code マーケットプレースから C# 拡張機能をインストールします](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)。</span><span class="sxs-lookup"><span data-stu-id="ca337-369">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="ca337-370">Windows インストーラー</span><span class="sxs-lookup"><span data-stu-id="ca337-370">Windows Installer</span></span>

<span data-ttu-id="ca337-371">.NET の[ダウンロード ページ](https://dotnet.microsoft.com/download/dotnet-core)には、Windows インストーラーの実行可能ファイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ca337-371">The [download page](https://dotnet.microsoft.com/download/dotnet-core) for .NET provides Windows Installer executables.</span></span>

<span data-ttu-id="ca337-372">MSI ファイルを使用して .NET をインストールする場合、`DOTNETHOME_X64` と `DOTNETHOME_X86` パラメーターを設定することによってインストール パスをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="ca337-372">When you use the MSI files to install .NET< you can customize the installation path by setting the `DOTNETHOME_X64` and `DOTNETHOME_X86` parameters:</span></span>

```console
dotnet-sdk-3.1.301-win-x64.exe DOTNETHOME_X64="F:\dotnet\x64" DOTNETHOME_X86="F:\dotnet\x86"
```

## <a name="download-and-manually-install"></a><span data-ttu-id="ca337-373">手動でダウンロードしてインストールする</span><span class="sxs-lookup"><span data-stu-id="ca337-373">Download and manually install</span></span>

<span data-ttu-id="ca337-374">.NET 用 Windows インストーラーの代わりに、SDK またはランタイムをダウンロードして手動でインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ca337-374">As an alternative to the Windows installers for .NET, you can download and manually install the SDK or runtime.</span></span> <span data-ttu-id="ca337-375">手動インストールは、通常、継続的インテグレーション テストの一環として実行されます。</span><span class="sxs-lookup"><span data-stu-id="ca337-375">Manual install is usually performed as part of continuous integration testing.</span></span> <span data-ttu-id="ca337-376">開発者またはユーザーの場合、通常は[インストーラー](https://dotnet.microsoft.com/download/dotnet-core)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ca337-376">For a developer or user, it's generally better to use an [installer](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

<span data-ttu-id="ca337-377">.NET SDK と .NET ランタイムはどちらも、ダウンロード後に手動でインストールできます。</span><span class="sxs-lookup"><span data-stu-id="ca337-377">Both .NET SDK and .NET Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="ca337-378">.NET SDK をインストールする場合、対応するランタイムをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ca337-378">If you install .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="ca337-379">まず、次のいずれかのサイトから SDK またはランタイムのバイナリ リリースをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ca337-379">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- [<span data-ttu-id="ca337-380">.NET 5.0 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="ca337-380">.NET 5.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- [<span data-ttu-id="ca337-381">.NET Core 3.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="ca337-381">.NET Core 3.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="ca337-382">.NET Core 2.1 のダウンロード</span><span class="sxs-lookup"><span data-stu-id="ca337-382">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [<span data-ttu-id="ca337-383">すべての .NET Core のダウンロード</span><span class="sxs-lookup"><span data-stu-id="ca337-383">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="ca337-384">.NET を抽出するためのディレクトリを作成します (`%USERPROFILE%\dotnet` など)。</span><span class="sxs-lookup"><span data-stu-id="ca337-384">Create a directory to extract .NET to, for example `%USERPROFILE%\dotnet`.</span></span> <span data-ttu-id="ca337-385">次に、ダウンロードした zip ファイルをそのディレクトリに抽出します。</span><span class="sxs-lookup"><span data-stu-id="ca337-385">Then, extract the downloaded zip file into that directory.</span></span>

<span data-ttu-id="ca337-386">既定では、この方法でインストールされた .NET は、.NET CLI コマンドおよびアプリから使用されないため、使用することを明示的に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca337-386">By default, .NET CLI commands and apps won't use .NET installed in this way and you must explicitly choose to use it.</span></span> <span data-ttu-id="ca337-387">これを行うには、アプリケーションの起動に使用する環境変数を変更します。</span><span class="sxs-lookup"><span data-stu-id="ca337-387">To do so, change the environment variables with which an application is started:</span></span>

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
set DOTNET_MULTILEVEL_LOOKUP=0
```

<span data-ttu-id="ca337-388">この方法では、複数のバージョンを別々の場所にインストールして、その場所を参照する環境変数を使ってアプリケーションを実行することで、アプリケーションによって使用されるインストール場所を明示的に選択できます。</span><span class="sxs-lookup"><span data-stu-id="ca337-388">This approach lets you install multiple versions into separate locations, then explicitly choose which install location an application should use by running the application with environment variables pointing at that location.</span></span>

<span data-ttu-id="ca337-389">`DOTNET_MULTILEVEL_LOOKUP` が `0` に設定されている場合、.NET により、グローバルにインストールされている .NET のバージョンはすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="ca337-389">When `DOTNET_MULTILEVEL_LOOKUP` is set to `0`, .NET ignores any globally installed .NET version.</span></span> <span data-ttu-id="ca337-390">アプリケーションを実行するための最適なフレームワークを選択するときに、.NET によりグローバル インストールの既定の場所が考慮されるようにするには、その環境設定を削除します。</span><span class="sxs-lookup"><span data-stu-id="ca337-390">Remove that environment setting to let .NET consider the default global install location when selecting the best framework for running the application.</span></span> <span data-ttu-id="ca337-391">通常、既定値は `C:\Program Files\dotnet` です。インストーラーによってここに .NET がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="ca337-391">The default is typically `C:\Program Files\dotnet`, which is where the installers install .NET.</span></span>

## <a name="docker"></a><span data-ttu-id="ca337-392">Docker</span><span class="sxs-lookup"><span data-stu-id="ca337-392">Docker</span></span>

<span data-ttu-id="ca337-393">コンテナーを使用すると、アプリケーションをホスト システムの他の部分から簡単に分離できます。</span><span class="sxs-lookup"><span data-stu-id="ca337-393">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="ca337-394">同じコンピューター上のコンテナーでは、カーネルだけが共有され、アプリケーションに提供されたリソースが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ca337-394">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="ca337-395">.NET は Docker コンテナー内で実行できます。</span><span class="sxs-lookup"><span data-stu-id="ca337-395">.NET can run in a Docker container.</span></span> <span data-ttu-id="ca337-396">公式の .NET Docker イメージは Microsoft Container Registry (MCR) に公開され、[Microsoft .NET の Docker Hub リポジトリ](https://hub.docker.com/_/microsoft-dotnet)で見つけられます。</span><span class="sxs-lookup"><span data-stu-id="ca337-396">Official .NET Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet).</span></span> <span data-ttu-id="ca337-397">各リポジトリには、.NET (SDK またはランタイム) と自分が使用できる OS のさまざまな組み合わせのイメージが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ca337-397">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="ca337-398">Microsoft は、特定のシナリオに対応したイメージを用意しています。</span><span class="sxs-lookup"><span data-stu-id="ca337-398">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="ca337-399">たとえば、[ASP.NET Core リポジトリ](https://hub.docker.com/_/microsoft-dotnet-aspnet)には、運用環境での ASP.NET Core アプリの実行用にビルドされたイメージが用意されています。</span><span class="sxs-lookup"><span data-stu-id="ca337-399">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-aspnet) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="ca337-400">Docker コンテナー内で .NET を使用する方法の詳細については、「[.NET および Docker の概要](../docker/introduction.md)」と[サンプル](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md)ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca337-400">For more information about using .NET in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ca337-401">次のステップ</span><span class="sxs-lookup"><span data-stu-id="ca337-401">Next steps</span></span>

- <span data-ttu-id="ca337-402">[.NET が既にインストールされているかどうかを確認する方法](how-to-detect-installed-versions.md?pivots=os-windows)。</span><span class="sxs-lookup"><span data-stu-id="ca337-402">[How to check if .NET is already installed](how-to-detect-installed-versions.md?pivots=os-windows).</span></span>
- <span data-ttu-id="ca337-403">[チュートリアル: Hello World チュートリアル](../tutorials/with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="ca337-403">[Tutorial: Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="ca337-404">[チュートリアル: Visual Studio Code を使用して新しいアプリを作成する](../tutorials/with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="ca337-404">[Tutorial: Create a new app with Visual Studio Code](../tutorials/with-visual-studio-code.md).</span></span>
- <span data-ttu-id="ca337-405">[チュートリアル: NET Core アプリをコンテナー化する](../docker/build-container.md)。</span><span class="sxs-lookup"><span data-stu-id="ca337-405">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

[esu]: /troubleshoot/windows-client/windows-7-eos-faq/windows-7-extended-security-updates-faq
