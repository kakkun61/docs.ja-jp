---
title: 依存関係と .NET ライブラリ
description: .NET ライブラリの NuGet の依存関係を管理するためのベスト プラクティスの推奨事項。
ms.date: 10/02/2018
ms.openlocfilehash: d189a3364b501272e29de72b6018844877bf2128
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189304"
---
# <a name="dependencies"></a><span data-ttu-id="60731-103">依存関係</span><span class="sxs-lookup"><span data-stu-id="60731-103">Dependencies</span></span>

<span data-ttu-id="60731-104">.NET ライブラリに依存関係を追加する主な方法は、NuGet パッケージを参照することです。</span><span class="sxs-lookup"><span data-stu-id="60731-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="60731-105">NuGet パッケージ参照を使用すると、既に記述した機能をすぐに再利用して活用できますが、これは .NET 開発者にとってよくある衝突の原因となります。</span><span class="sxs-lookup"><span data-stu-id="60731-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="60731-106">依存関係を正しく管理することは、他の .NET ライブラリの変更によって自分の .NET ライブラリと互換性がなくなる問題、またはその逆の問題を防ぐために重要です。</span><span class="sxs-lookup"><span data-stu-id="60731-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="60731-107">ひし形の依存関係</span><span class="sxs-lookup"><span data-stu-id="60731-107">Diamond dependencies</span></span>

<span data-ttu-id="60731-108">.NET プロジェクトの依存関係ツリーに複数のバージョンのパッケージがあることは一般的です。</span><span class="sxs-lookup"><span data-stu-id="60731-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="60731-109">たとえば、アプリが 2 つの NuGet パッケージに依存し、各パッケージが同じパッケージの異なるバージョンに依存しているとします。</span><span class="sxs-lookup"><span data-stu-id="60731-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="60731-110">これで、ひし形の依存関係がアプリの依存関係グラフに存在することになります。</span><span class="sxs-lookup"><span data-stu-id="60731-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="60731-111">![ひし形の依存関係](./media/dependencies/diamond-dependency.png "ひし形の依存関係")</span><span class="sxs-lookup"><span data-stu-id="60731-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="60731-112">ビルド時に、NuGet では、依存関係の依存関係を含め、プロジェクトが依存するすべてのパッケージが分析されます。</span><span class="sxs-lookup"><span data-stu-id="60731-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="60731-113">複数バージョンのパッケージが検出されると、規則が評価され、1 つが選択されます。</span><span class="sxs-lookup"><span data-stu-id="60731-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="60731-114">同じアプリケーション内で複数バージョンのアセンブリを並列して実行すると .NET で問題が発生するため、パッケージを統一する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60731-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="60731-115">ほとんどのひし形の依存関係は簡単に解決できますが、状況によっては問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="60731-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

- <span data-ttu-id="60731-116">**競合する NuGet パッケージ参照** があると、パッケージの復元中にバージョンが解決されません。</span><span class="sxs-lookup"><span data-stu-id="60731-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
- <span data-ttu-id="60731-117">**バージョン間で破壊的変更** があると、実行時にバグと例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="60731-117">**Breaking changes between the versions** cause bugs and exceptions at run time.</span></span>
- <span data-ttu-id="60731-118">**パッケージ アセンブリが厳密な名前** で、アセンブリ バージョンが変わり、アプリが .NET Framework 上で実行されている場合。</span><span class="sxs-lookup"><span data-stu-id="60731-118">**The package assembly is strong named** , the assembly version changed, and the app is running on .NET Framework.</span></span> <span data-ttu-id="60731-119">アセンブリのバインド リダイレクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="60731-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="60731-120">自分のパッケージと共に使用されるパッケージを知ることはできません。</span><span class="sxs-lookup"><span data-stu-id="60731-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="60731-121">ライブラリが中断するひし形の依存関係の可能性を減らすには、依存しているパッケージの数を最小限に抑えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60731-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="60731-122">✔️ .NET ライブラリに不要な依存関係がないか確認してください。</span><span class="sxs-lookup"><span data-stu-id="60731-122">✔️ DO review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="60731-123">NuGet の依存関係バージョンの範囲</span><span class="sxs-lookup"><span data-stu-id="60731-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="60731-124">パッケージ参照では、適用できる有効なパッケージの範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="60731-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="60731-125">通常、プロジェクト ファイルのパッケージ参照バージョンは最低バージョンであり、最高バージョンはありません。</span><span class="sxs-lookup"><span data-stu-id="60731-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="60731-126">依存関係を解決するときに NuGet で使用される規則は[複合](/nuget/consume-packages/dependency-resolution)ですが、NuGet の[既定では](/nuget/consume-packages/install-use-packages-visual-studio#install-and-update-options)適用可能な最低バージョンが検索されます。</span><span class="sxs-lookup"><span data-stu-id="60731-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet [by default](/nuget/consume-packages/install-use-packages-visual-studio#install-and-update-options) looks for the lowest applicable version.</span></span> <span data-ttu-id="60731-127">互換性の問題が最も少ないのは最低バージョンなので、NuGet では、適用できる最高バージョンよりも適用できる最低バージョンが優先されます。</span><span class="sxs-lookup"><span data-stu-id="60731-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="60731-128">NuGet の適用できる最低バージョン規則があるので、最新のバージョンを取得しないようにパッケージ参照に上限のバージョンまたは正確な範囲を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="60731-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="60731-129">NuGet は、最低の最も互換性の高いバージョンを自動的に検索しようとします。</span><span class="sxs-lookup"><span data-stu-id="60731-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="60731-130">上限のバージョンを指定すると、競合がある場合に NuGet が失敗します。</span><span class="sxs-lookup"><span data-stu-id="60731-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="60731-131">たとえば、あるライブラリが 1.0 のみを受け入れ、別のライブラリが 2.0 以降を必要としているとします。</span><span class="sxs-lookup"><span data-stu-id="60731-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="60731-132">バージョン 2.0 に互換性に影響する変更が組み込まれた可能性はありますが、厳密なバージョンやバージョンの上限が指定されていると、確実にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="60731-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="60731-133">![ひし形の依存関係の競合](./media/dependencies/diamond-dependency-conflict.png "ひし形の依存関係の競合")</span><span class="sxs-lookup"><span data-stu-id="60731-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="60731-134">❌ 最小バージョンを指定していない NuGet パッケージ参照を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="60731-134">❌ DO NOT have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="60731-135">❌ 正確なバージョンを要求する NuGet パッケージ参照は回避してください。</span><span class="sxs-lookup"><span data-stu-id="60731-135">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="60731-136">❌ バージョンの上限がある NuGet パッケージ参照を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="60731-136">❌ AVOID NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="60731-137">NuGet 共有ソース パッケージ</span><span class="sxs-lookup"><span data-stu-id="60731-137">NuGet shared source packages</span></span>

<span data-ttu-id="60731-138">外部 NuGet パッケージの依存関係を減らす方法の 1 つは、共有ソース パッケージを参照することです。</span><span class="sxs-lookup"><span data-stu-id="60731-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="60731-139">共有ソース パッケージには、参照時にプロジェクトに含まれる[ソース コード ファイル](/nuget/reference/nuspec#including-content-files)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="60731-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="60731-140">プロジェクトの他の部分と共にコンパイルされたソース コード ファイルのみを含めているので、外部の依存関係がなく、競合が発生する可能性がありません。</span><span class="sxs-lookup"><span data-stu-id="60731-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="60731-141">共有ソース パッケージは、小規模な機能を組み込む場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="60731-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="60731-142">たとえば、HTTP 呼び出しを行うヘルパー メソッドの共有ソース パッケージです。</span><span class="sxs-lookup"><span data-stu-id="60731-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="60731-143">![共有ソース パッケージ](./media/dependencies/shared-source-package.png "共有ソース パッケージ")</span><span class="sxs-lookup"><span data-stu-id="60731-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="60731-144">![共有ソース プロジェクト](./media/dependencies/shared-source-project.png "共有ソース プロジェクト")</span><span class="sxs-lookup"><span data-stu-id="60731-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="60731-145">共有ソース パッケージにはいくつの制限があります。</span><span class="sxs-lookup"><span data-stu-id="60731-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="60731-146">参照できるのは `PackageReference` からのみなので、以前の `packages.config` プロジェクトは除外されます。</span><span class="sxs-lookup"><span data-stu-id="60731-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="60731-147">また、共有ソース パッケージは、言語の種類が同じプロジェクトからのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="60731-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="60731-148">これらの制限があるため、共有ソース パッケージは、オープン ソース プロジェクト内で機能を共有する場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="60731-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="60731-149">✔️ 小規模な内部の機能の場合には、共有ソース パッケージを参照することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="60731-149">✔️ CONSIDER referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="60731-150">✔️ パッケージで小規模な内部の機能を提供する場合には、それを共有ソース パッケージにすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="60731-150">✔️ CONSIDER making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="60731-151">✔️ 共有ソース パッケージは `PrivateAssets="All"` を使用して参照してください。</span><span class="sxs-lookup"><span data-stu-id="60731-151">✔️ DO reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="60731-152">この設定で、これが開発時にのみ使用されるパッケージであり、パブリックな依存関係として公開されないように NuGet に指示します。</span><span class="sxs-lookup"><span data-stu-id="60731-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="60731-153">❌ パブリック API に共有ソース パッケージの種類を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="60731-153">❌ DO NOT have shared source package types in your public API.</span></span>

> <span data-ttu-id="60731-154">共有ソースの種類は参照アセンブリにコンパイルされ、アセンブリ境界を越えて交換することはできません。</span><span class="sxs-lookup"><span data-stu-id="60731-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="60731-155">たとえば、あるプロジェクトの共有ソースの種類 `IRepository` は別のプロジェクトの同じ共有ソース `IRepository` とは別の種類です。</span><span class="sxs-lookup"><span data-stu-id="60731-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="60731-156">共有ソース パッケージの種類には `internal` の可視性が必要です。</span><span class="sxs-lookup"><span data-stu-id="60731-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="60731-157">❌ 共有ソース パッケージを NuGet.org に公開しないでください。</span><span class="sxs-lookup"><span data-stu-id="60731-157">❌ DO NOT publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="60731-158">共有ソース パッケージにはソース コードが含まれており、言語の種類が同じプロジェクトでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="60731-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="60731-159">たとえば、C# 共有ソース パッケージを F# アプリケーションで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="60731-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="60731-160">共有ソース パッケージは、プロジェクト内で内部的に使用するように、[ローカル フィードまたは MyGet](./publish-nuget-package.md) に公開します。</span><span class="sxs-lookup"><span data-stu-id="60731-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="60731-161">[前へ](nuget.md)
>[次へ](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="60731-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
