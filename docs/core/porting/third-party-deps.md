---
title: コードを .NET Core に移植するために依存関係を分析する
description: .NET Framework から .NET Core にプロジェクトを移植するために、外部の依存関係を分析する方法を説明します。
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 430da45052e3953ab49f182b1773fc6d74bd2221
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223605"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a><span data-ttu-id="882d5-103">コードを .NET Core に移植するために依存関係を分析する</span><span class="sxs-lookup"><span data-stu-id="882d5-103">Analyze your dependencies to port code to .NET Core</span></span>

<span data-ttu-id="882d5-104">.NET Core または .NET Standard にコードを移植するには、依存関係を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="882d5-104">To port your code to .NET Core or .NET Standard, you must understand your dependencies.</span></span> <span data-ttu-id="882d5-105">外部の依存関係は、プロジェクトで参照する NuGet パッケージまたは `.dll` ファイルですが、これはユーザーが構築するものではありません。</span><span class="sxs-lookup"><span data-stu-id="882d5-105">External dependencies are the NuGet packages or `.dll` files you reference in your project, but that you don't build yourself.</span></span>

## <a name="migrate-your-nuget-packages-to-packagereference"></a><span data-ttu-id="882d5-106">NuGet パッケージを `PackageReference` に移行する</span><span class="sxs-lookup"><span data-stu-id="882d5-106">Migrate your NuGet packages to `PackageReference`</span></span>

<span data-ttu-id="882d5-107">.NET Core は [PackageReference](/nuget/consume-packages/package-references-in-project-files) を使用してパッケージの依存関係を指定します。</span><span class="sxs-lookup"><span data-stu-id="882d5-107">.NET Core uses [PackageReference](/nuget/consume-packages/package-references-in-project-files) to specify package dependencies.</span></span> <span data-ttu-id="882d5-108">[packages.config](/nuget/reference/packages-config) を使用してプロジェクトにパッケージを指定している場合は、`packages.config` は .NET Core ではサポートされていないため、`PackageReference` 形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="882d5-108">If you're using [packages.config](/nuget/reference/packages-config) to specify your packages in your project, convert it to the `PackageReference` format, because `packages.config` isn't supported in .NET Core.</span></span>

<span data-ttu-id="882d5-109">移行方法については、「[packages.config から PackageReference への移行](/nuget/reference/migrate-packages-config-to-package-reference)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="882d5-109">To learn how to migrate, see the [Migrate from packages.config to PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) article.</span></span>

## <a name="upgrade-your-nuget-packages"></a><span data-ttu-id="882d5-110">NuGet パッケージをアップグレードする</span><span class="sxs-lookup"><span data-stu-id="882d5-110">Upgrade your NuGet packages</span></span>

<span data-ttu-id="882d5-111">プロジェクトを `PackageReference` 形式に移行した後、お使いのパッケージが .NET Core と互換性があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="882d5-111">After you migrate your project to the `PackageReference` format, verify if your packages are compatible with .NET Core.</span></span>

<span data-ttu-id="882d5-112">まず、パッケージを使用可能な最新バージョンにアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="882d5-112">First, upgrade your packages to the latest version that you can.</span></span> <span data-ttu-id="882d5-113">これは、Visual Studio の NuGet パッケージマネージャーの UI で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="882d5-113">This can be done with the NuGet Package Manager UI in Visual Studio.</span></span> <span data-ttu-id="882d5-114">パッケージの新しいバージョンの依存関係は、既に .NET Core と互換性がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="882d5-114">It's likely that newer versions of your package dependencies are already compatible with .NET Core.</span></span>

## <a name="analyze-your-package-dependencies"></a><span data-ttu-id="882d5-115">パッケージの依存関係を分析する</span><span class="sxs-lookup"><span data-stu-id="882d5-115">Analyze your package dependencies</span></span>

<span data-ttu-id="882d5-116">変換およびアップグレードしたパッケージの依存関係が .NET Core で動作することをまだ確認していない場合は、次のいくつかの方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="882d5-116">If you haven't already verified that your converted and upgraded package dependencies work on .NET Core, there are a few ways that you can achieve that:</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="882d5-117">nuget.org を使用して NuGet パッケージを分析する</span><span class="sxs-lookup"><span data-stu-id="882d5-117">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="882d5-118">[nuget.org](https://www.nuget.org/) のパッケージのページの **[Dependencies]\(依存関係\)** のセクションで、各パッケージでサポートされる TFM (ターゲット フレームワーク モニカー) を確認できます。</span><span class="sxs-lookup"><span data-stu-id="882d5-118">You can see the Target Framework Monikers (TFMs) that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="882d5-119">互換性はこのサイトを使用して確認するのが簡単ですが、 **依存関係** の情報はすべてのパッケージのサイトにはありません。</span><span class="sxs-lookup"><span data-stu-id="882d5-119">Although using the site is an easier method to verify the compatibility, **Dependencies** information isn't available on the site for all packages.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="882d5-120">NuGet パッケージ エクスプローラーを使用して NuGet パッケージを分析する</span><span class="sxs-lookup"><span data-stu-id="882d5-120">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="882d5-121">NuGet パッケージ自体はフォルダーのセットであり、プラットフォーム固有のアセンブリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="882d5-121">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="882d5-122">パッケージ内に互換性のあるアセンブリを含むフォルダーがあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="882d5-122">Check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="882d5-123">NuGet パッケージ フォルダーを調べる最も簡単な方法は、[NuGet パッケージ エクスプローラー](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) ツールを使用することです。</span><span class="sxs-lookup"><span data-stu-id="882d5-123">The easiest way to inspect NuGet package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="882d5-124">これをインストールした後、次の手順を使用してフォルダー名を確認します。</span><span class="sxs-lookup"><span data-stu-id="882d5-124">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="882d5-125">NuGet パッケージ エクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="882d5-125">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="882d5-126">**[Open package from online feed]\(オンライン フィードからパッケージを開く\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="882d5-126">Click **Open package from online feed** .</span></span>
3. <span data-ttu-id="882d5-127">パッケージの名前を検索します。</span><span class="sxs-lookup"><span data-stu-id="882d5-127">Search for the name of the package.</span></span>
4. <span data-ttu-id="882d5-128">検索結果からパッケージ名を選択し、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="882d5-128">Select the package name from the search results and click **open** .</span></span>
5. <span data-ttu-id="882d5-129">右側にある *lib* フォルダーを展開し、フォルダー名を確認します。</span><span class="sxs-lookup"><span data-stu-id="882d5-129">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="882d5-130">`netstandardX.Y` または `netcoreappX.Y` のパターンのいずれかを使用するフォルダー名を検索します。</span><span class="sxs-lookup"><span data-stu-id="882d5-130">Look for a folder with names using one the following patterns: `netstandardX.Y` or `netcoreappX.Y`.</span></span>

<span data-ttu-id="882d5-131">これらの値は[ターゲット フレームワーク モニカー (TFM)](../../standard/frameworks.md) であり、[.NET Standard](../../standard/net-standard.md)、.NET Core、および .NET Core と互換性がある従来のポータブル クラス ライブラリ (PCL) プロファイルのバージョンにマップされます。</span><span class="sxs-lookup"><span data-stu-id="882d5-131">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="882d5-132">パッケージでサポートされる TFM を見ると、`netcoreapp*` に互換性はあるものの、.NET Core プロジェクトのみを対象としており、.NET Standard プロジェクトを対象としていないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="882d5-132">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="882d5-133">他の .NET Core アプリで使用できるのは、`netstandard*` ではなく、`netcoreapp*` のみをターゲットとするライブラリだけです。</span><span class="sxs-lookup"><span data-stu-id="882d5-133">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

## <a name="net-framework-compatibility-mode"></a><span data-ttu-id="882d5-134">.NET Framework 互換モード</span><span class="sxs-lookup"><span data-stu-id="882d5-134">.NET Framework compatibility mode</span></span>

<span data-ttu-id="882d5-135">NuGet パッケージの分析後、.NET Framework のみをターゲットとしていることがわかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="882d5-135">After analyzing the NuGet packages, you might find that they only target the .NET Framework.</span></span>

<span data-ttu-id="882d5-136">.NET Standard 2.0 以降、.NET Framework 互換モードが導入されました。</span><span class="sxs-lookup"><span data-stu-id="882d5-136">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="882d5-137">この互換モードにより、.NET Standard および .NET Core プロジェクトは .NET Framework ライブラリを参照できます。</span><span class="sxs-lookup"><span data-stu-id="882d5-137">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="882d5-138">.NET Framework ライブラリの参照はすべてのプロジェクトで機能するわけではありません (例えばライブラリで Windows Presentation Foundation (WPF) API を使用していても、多くの移植シナリオがブロック解除される場合など)。</span><span class="sxs-lookup"><span data-stu-id="882d5-138">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="882d5-139">[Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections) など、プロジェクトで .NET Framework をターゲットとする NuGet パッケージを参照すると、次の例のようなパッケージ フォールバック警告 ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="882d5-139">When you reference NuGet packages that target .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="882d5-140">この警告は、パッケージを追加したとき、およびプロジェクトでそのパッケージを確実にテストするためにビルドするたびに表示されます。</span><span class="sxs-lookup"><span data-stu-id="882d5-140">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="882d5-141">プロジェクトが予期したとおりに動作している場合は、Visual Studio でパッケージ プロパティを編集するか、任意のコード エディターでプロジェクト ファイルを手動で編集して、この警告を非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="882d5-141">If your project works as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="882d5-142">プロジェクト ファイルを編集して警告を非表示にするには、警告を非表示にするパッケージの `PackageReference` エントリを見つけて、`NoWarn` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="882d5-142">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="882d5-143">`NoWarn` 属性では、すべての警告 ID のコンマ区切りリストを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="882d5-143">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="882d5-144">次の例は、プロジェクト ファイルを手動で編集して、`Huitian.PowerCollections` パッケージの `NU1701` 警告を非表示にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="882d5-144">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="882d5-145">Visual Studio でコンパイラ警告を非表示にする方法の詳細については、「[NuGet パッケージの警告を非表示にする](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="882d5-145">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).</span></span>

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="882d5-146">NuGet パッケージの依存関係が .NET Core で動作しない場合の対処方法</span><span class="sxs-lookup"><span data-stu-id="882d5-146">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="882d5-147">依存している NuGet パッケージが .NET Core で動作しない場合の対処方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="882d5-147">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

- <span data-ttu-id="882d5-148">プロジェクトがオープン ソースで、GitHub のような場所にホストされている場合、直接開発者に連絡することができます。</span><span class="sxs-lookup"><span data-stu-id="882d5-148">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
- <span data-ttu-id="882d5-149">[nuget.org](https://www.nuget.org/) で直接作成者に連絡することができます。パッケージを検索し、パッケージのページの左側にある **[Contact Owners]\(所有者に問い合わせる\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="882d5-149">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
- <span data-ttu-id="882d5-150">使用していたパッケージと同じタスクを実行する、.NET Core で実行される別のパッケージを検索することができます。</span><span class="sxs-lookup"><span data-stu-id="882d5-150">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
- <span data-ttu-id="882d5-151">パッケージが行っていたコードを自分で記述できます。</span><span class="sxs-lookup"><span data-stu-id="882d5-151">You can attempt to write the code the package was doing yourself.</span></span>
- <span data-ttu-id="882d5-152">少なくともパッケージの互換バージョンが利用可能になるまでは、アプリの機能を変更することで、パッケージの依存関係を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="882d5-152">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="882d5-153">オープン ソース プロジェクトの保守管理者および NuGet パッケージの発行者の多くは、ボランティアであることを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="882d5-153">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="882d5-154">彼らは、その分野に関心があるために無償で作業を行っており、多くの場合、日中に別の仕事を抱えています。</span><span class="sxs-lookup"><span data-stu-id="882d5-154">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="882d5-155">.NET Core のサポートを求めるために連絡する際には、この点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="882d5-155">Be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="882d5-156">これらの方法のいずれでも問題を解決できない場合、後日 .NET Core に移植しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="882d5-156">If you can't resolve your issue with any of these options, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="882d5-157">.NET チームは .NET Core のサポートでどのライブラリが最も重要かを知りたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="882d5-157">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="882d5-158">使用したいライブラリについて、dotnet@microsoft.com にメールを送ることができます。</span><span class="sxs-lookup"><span data-stu-id="882d5-158">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="882d5-159">NuGet パッケージではない依存関係を分析する</span><span class="sxs-lookup"><span data-stu-id="882d5-159">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="882d5-160">ファイル システム内の DLL など、NuGet パッケージではない依存関係がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="882d5-160">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="882d5-161">その依存関係の移植性を調べる唯一の方法が、[.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) ツールを実行することです。</span><span class="sxs-lookup"><span data-stu-id="882d5-161">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="882d5-162">このツールでは、.NET Framework をターゲットとするアセンブリを分析し、.NET Core などの他の .NET プラットフォームに移植できない API を特定します。</span><span class="sxs-lookup"><span data-stu-id="882d5-162">The tool analyzes assemblies that target the .NET Framework and identifies APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="882d5-163">このツールはコンソール アプリケーションまたは [Visual Studio 拡張機能](../../standard/analyzers/portability-analyzer.md)として実行できます。</span><span class="sxs-lookup"><span data-stu-id="882d5-163">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="882d5-164">次の手順</span><span class="sxs-lookup"><span data-stu-id="882d5-164">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="882d5-165">ライブラリを移植する</span><span class="sxs-lookup"><span data-stu-id="882d5-165">Port libraries</span></span>](libraries.md)
