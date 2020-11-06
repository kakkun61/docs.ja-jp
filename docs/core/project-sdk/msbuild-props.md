---
title: Microsoft.NET.Sdk の MSBuild プロパティ
description: .NET SDK によって認識される MSBuild のプロパティと項目のリファレンスです。
ms.date: 02/14/2020
ms.topic: reference
ms.custom: updateeachrelease
ms.openlocfilehash: 463e2a163e6a20f5631b0ab82462614834156ae3
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063229"
---
# <a name="msbuild-reference-for-net-sdk-projects"></a><span data-ttu-id="a1ff1-103">.NET SDK プロジェクトの MSBuild リファレンス</span><span class="sxs-lookup"><span data-stu-id="a1ff1-103">MSBuild reference for .NET SDK projects</span></span>

<span data-ttu-id="a1ff1-104">このページは、.NET プロジェクトの構成に使用できる、MSBuild のプロパティと項目のリファレンスです。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-104">This page is a reference for the MSBuild properties and items that you can use to configure .NET projects.</span></span>

> [!NOTE]
> <span data-ttu-id="a1ff1-105">このページの編集は進行中であり、.NET SDK の便利な MSBuild プロパティがすべて記載されている訳ではありません。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET SDK.</span></span> <span data-ttu-id="a1ff1-106">一般的な MSBuild プロパティの一覧については、「[MSBuild プロジェクトの共通プロパティ](/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="a1ff1-107">フレームワークのプロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-107">Framework properties</span></span>

- [<span data-ttu-id="a1ff1-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a1ff1-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="a1ff1-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="a1ff1-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="a1ff1-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="a1ff1-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="a1ff1-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="a1ff1-111">TargetFramework</span></span>

<span data-ttu-id="a1ff1-112">`TargetFramework` プロパティには、アプリのターゲット フレームワーク バージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-112">The `TargetFramework` property specifies the target framework version for the app.</span></span> <span data-ttu-id="a1ff1-113">有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-frameworks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="a1ff1-114">詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="a1ff1-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="a1ff1-115">TargetFrameworks</span></span>

<span data-ttu-id="a1ff1-116">アプリで複数のプラットフォームをターゲットにする場合は、`TargetFrameworks` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="a1ff1-117">有効なターゲット フレームワーク モニカーの一覧については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md#supported-target-frameworks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-frameworks).</span></span>

> [!NOTE]
> <span data-ttu-id="a1ff1-118">`TargetFramework` (単数形) が指定されている場合、このプロパティは無視されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="a1ff1-119">詳細については、「[SDK スタイルのプロジェクトでのターゲット フレームワーク](../../standard/frameworks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="a1ff1-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="a1ff1-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="a1ff1-121">このプロパティは、`netstandard1.x` を使用するプロジェクトにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="a1ff1-122">`netstandard2.x` を使用するプロジェクトには適用されません。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="a1ff1-123">メタパッケージ バージョンよりも低いフレームワーク バージョンを指定する場合は、`NetStandardImplicitPackageVersion` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the metapackage version.</span></span> <span data-ttu-id="a1ff1-124">次の例のプロジェクト ファイルは、`netstandard1.3` をターゲットにしていますが、`NETStandard.Library` の 1.6.0 バージョンを使用しています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="a1ff1-125">パッケージのプロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-125">Package properties</span></span>

<span data-ttu-id="a1ff1-126">`PackageId`、`PackageVersion`、`PackageIcon`、`Title`、`Description` などのプロパティを指定し、プロジェクトから作成されたパッケージについて説明できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-126">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="a1ff1-127">以上のプロパティとその他のプロパティの詳細については、「[pack ターゲット](/nuget/reference/msbuild-targets#pack-target)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-127">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties-and-items"></a><span data-ttu-id="a1ff1-128">プロパティと項目の発行</span><span class="sxs-lookup"><span data-stu-id="a1ff1-128">Publish properties and items</span></span>

- [<span data-ttu-id="a1ff1-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="a1ff1-129">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="a1ff1-130">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="a1ff1-130">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="a1ff1-131">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a1ff1-131">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="a1ff1-132">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a1ff1-132">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="a1ff1-133">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="a1ff1-133">RuntimeIdentifier</span></span>

<span data-ttu-id="a1ff1-134">`RuntimeIdentifier` プロパティを使用すると、プロジェクトに 1 つの[ランタイム識別子 (RID)](../rid-catalog.md) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-134">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a1ff1-135">RID により、自己完結型の展開を発行できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-135">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="a1ff1-136">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="a1ff1-136">RuntimeIdentifiers</span></span>

<span data-ttu-id="a1ff1-137">`RuntimeIdentifiers` プロパティには、プロジェクトの[ランタイム識別子 (RID)](../rid-catalog.md) のセミコロン区切りリストを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-137">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="a1ff1-138">複数のランタイムに発行する必要がある場合は、このプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-138">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="a1ff1-139">`RuntimeIdentifiers` は、復元時に適切な資産をグラフに確実に含めるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-139">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="a1ff1-140">`RuntimeIdentifier` (単数形) を使用すると、必要なランタイムが 1 つだけのとき、ビルドが速くなります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-140">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="a1ff1-141">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="a1ff1-141">TrimmerRootAssembly</span></span>

<span data-ttu-id="a1ff1-142">`TrimmerRootAssembly` 項目ではアセンブリを " [*トリミング*](../deploying/trim-self-contained.md)" から除外できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-142">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="a1ff1-143">トリミングとは、パッケージ化されたアプリケーションからランタイムの未使用部分を削除するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-143">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="a1ff1-144">必要な参照がトリミングによって間違って削除されることもあります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-144">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="a1ff1-145">次の XML では、トリミングから `System.Security` アセンブリが除外されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-145">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="a1ff1-146">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="a1ff1-146">UseAppHost</span></span>

<span data-ttu-id="a1ff1-147">`UseAppHost` プロパティは、.NET SDK の 2.1.400 バージョンで導入されました。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-147">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET SDK.</span></span> <span data-ttu-id="a1ff1-148">デプロイ用にネイティブ実行可能ファイルを作成するかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-148">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="a1ff1-149">自己完結型の配置にはネイティブの実行可能ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-149">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="a1ff1-150">.NET Core 3.0 以降のバージョンでは、既定でフレームワークに依存する実行可能ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-150">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="a1ff1-151">実行可能ファイルの生成を無効にするには、`UseAppHost` プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-151">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="a1ff1-152">配置の詳細については、[.NET アプリケーションの配置](../deploying/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-152">For more information about deployment, see [.NET application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="a1ff1-153">コンパイルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-153">Compile properties</span></span>

- [<span data-ttu-id="a1ff1-154">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="a1ff1-154">EmbeddedResourceUseDependentUponConvention</span></span>](#embeddedresourceusedependentuponconvention)
- [<span data-ttu-id="a1ff1-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a1ff1-155">LangVersion</span></span>](#langversion)

### <a name="embeddedresourceusedependentuponconvention"></a><span data-ttu-id="a1ff1-156">EmbeddedResourceUseDependentUponConvention</span><span class="sxs-lookup"><span data-stu-id="a1ff1-156">EmbeddedResourceUseDependentUponConvention</span></span>

<span data-ttu-id="a1ff1-157">`EmbeddedResourceUseDependentUponConvention` プロパティは、リソース マニフェスト ファイル名が、リソース ファイルと併置されているソース ファイルの型情報から生成されるかどうかを定義します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-157">The `EmbeddedResourceUseDependentUponConvention` property defines whether resource manifest file names are generated from type information in source files that are colocated with resource files.</span></span> <span data-ttu-id="a1ff1-158">たとえば、 *Form1.vb* が *Form1.cs* と同じフォルダーにあり、`EmbeddedResourceUseDependentUponConvention` が `true` に設定されている場合、生成された *.resources* ファイルは *Form1.cs* で定義されている最初の型から名前を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-158">For example, if *Form1.resx* is in the same folder as *Form1.cs* , and `EmbeddedResourceUseDependentUponConvention` is set to `true`, the generated *.resources* file takes its name from the first type that's defined in *Form1.cs*.</span></span> <span data-ttu-id="a1ff1-159">たとえば、`MyNamespace.Form1` が *Form1.cs* で定義されている最初の型である場合、生成されたファイル名は *MyNamespace.Form1.resources* になります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-159">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs* , the generated file name is *MyNamespace.Form1.resources*.</span></span>

> [!NOTE]
> <span data-ttu-id="a1ff1-160">`LogicalName`、`ManifestResourceName`、または `DependentUpon` メタデータが `EmbeddedResource` 項目に対して指定されている場合、そのリソース ファイルに対して生成されたマニフェスト ファイル名は、代わりにそのメタデータがベースになります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-160">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item, the generated manifest file name for that resource file is based on that metadata instead.</span></span>

<span data-ttu-id="a1ff1-161">既定では、新しい .NET プロジェクトでは、このプロパティは `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-161">By default, in a new .NET project, this property is set to `true`.</span></span> <span data-ttu-id="a1ff1-162">`false` に設定され、かつプロジェクト ファイルの `EmbeddedResource` 項目に `LogicalName`、`ManifestResourceName`、`DependentUpon` のメタデータがどれも指定されていない場合、リソース マニフェストのファイル名は、プロジェクトのルート名前空間と、 *.resx* ファイルへの相対ファイル パスがベースになります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-162">If set to `false`, and no `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for the `EmbeddedResource` item in the project file, the resource manifest file name is based off the root namespace for the project and the relative file path to the *.resx* file.</span></span> <span data-ttu-id="a1ff1-163">詳細については、「[リソース マニフェスト ファイルの名前付けの方法](../resources/manifest-file-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-163">For more information, see [How resource manifest files are named](../resources/manifest-file-names.md).</span></span>

```xml
<PropertyGroup>
  <EmbeddedResourceUseDependentUponConvention>true</EmbeddedResourceUseDependentUponConvention>
</PropertyGroup>
```

### <a name="langversion"></a><span data-ttu-id="a1ff1-164">LangVersion</span><span class="sxs-lookup"><span data-stu-id="a1ff1-164">LangVersion</span></span>

<span data-ttu-id="a1ff1-165">`LangVersion` プロパティを使用すると、特定のプログラミング言語バージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-165">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="a1ff1-166">たとえば、C# プレビュー機能にアクセスする場合は、`LangVersion` を `preview` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-166">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="a1ff1-167">詳細については、「[C# 言語のバージョン管理](../../csharp/language-reference/configure-language-version.md#override-a-default)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-167">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="code-analysis-properties"></a><span data-ttu-id="a1ff1-168">コード分析のプロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-168">Code analysis properties</span></span>

### <a name="analysislevel"></a><span data-ttu-id="a1ff1-169">AnalysisLevel</span><span class="sxs-lookup"><span data-stu-id="a1ff1-169">AnalysisLevel</span></span>

<span data-ttu-id="a1ff1-170">`AnalysisLevel` プロパティを使用すると、コード分析レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-170">The `AnalysisLevel` property lets you specify a code analysis level.</span></span> <span data-ttu-id="a1ff1-171">たとえば、プレビューのコード アナライザーにアクセスする場合は、`AnalysisLevel` を `preview` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-171">For example, if you want access to preview code analyzers, set `AnalysisLevel` to `preview`.</span></span> <span data-ttu-id="a1ff1-172">既定値は `latest` です。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-172">The default value is `latest`.</span></span>

```xml
<PropertyGroup>
  <AnalysisLevel>preview</AnalysisLevel>
</PropertyGroup>
```

<span data-ttu-id="a1ff1-173">次の表で利用可能なオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-173">The following table shows the available options.</span></span>

| <span data-ttu-id="a1ff1-174">値</span><span class="sxs-lookup"><span data-stu-id="a1ff1-174">Value</span></span> | <span data-ttu-id="a1ff1-175">説明</span><span class="sxs-lookup"><span data-stu-id="a1ff1-175">Meaning</span></span> |
|-|-|
| `latest` | <span data-ttu-id="a1ff1-176">リリースされている最新のコード アナライザーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-176">The latest code analyzers that have been released are used.</span></span> <span data-ttu-id="a1ff1-177">既定値です。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-177">This is the default.</span></span> |
| `preview` | <span data-ttu-id="a1ff1-178">最新のコード アナライザーが、プレビュー段階であっても使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-178">The latest code analyzers are used, even if they are in preview.</span></span> |
| `5.0` | <span data-ttu-id="a1ff1-179">新しいルールが使用可能な場合でも、.NET 5.0 リリースで有効になっていた一連のルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-179">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |
| `5` | <span data-ttu-id="a1ff1-180">新しいルールが使用可能な場合でも、.NET 5.0 リリースで有効になっていた一連のルールが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-180">The set of rules that was enabled for the .NET 5.0 release is used, even if newer rules are available.</span></span> |

### <a name="analysismode"></a><span data-ttu-id="a1ff1-181">AnalysisMode</span><span class="sxs-lookup"><span data-stu-id="a1ff1-181">AnalysisMode</span></span>

<span data-ttu-id="a1ff1-182">.NET 5.0 RC2 以降、.NET SDK には、すべての ["CA" コード品質ルール](../../fundamentals/code-analysis/quality-rules/index.md)が付属しています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-182">Starting with .NET 5.0 RC2, the .NET SDK ships with all of the ["CA" code quality rules](../../fundamentals/code-analysis/quality-rules/index.md).</span></span> <span data-ttu-id="a1ff1-183">既定では、ビルド警告として[一部のルールが有効](../../fundamentals/code-analysis/overview.md#enabled-rules)になっています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-183">By default, only [some rules are enabled](../../fundamentals/code-analysis/overview.md#enabled-rules) as build warnings.</span></span> <span data-ttu-id="a1ff1-184">`AnalysisMode` プロパティを使用すると、既定で有効になるルールのセットをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-184">The `AnalysisMode` property lets you customize the set of rules that are enabled by default.</span></span> <span data-ttu-id="a1ff1-185">より積極的な (オプトアウト) 分析モード、またはより保守的な (オプトイン) 分析モードに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-185">You can either switch to a more aggressive (opt-out) analysis mode or a more conservative (opt-in) analysis mode.</span></span> <span data-ttu-id="a1ff1-186">たとえば、既定ですべてのルールをビルド警告として有効にする場合は、値を `AllEnabledByDefault` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-186">For example, if you want to enable all rules by default as build warnings, set the value to `AllEnabledByDefault`.</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
</PropertyGroup>
```

<span data-ttu-id="a1ff1-187">次の表で利用可能なオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-187">The following table shows the available options.</span></span>

| <span data-ttu-id="a1ff1-188">値</span><span class="sxs-lookup"><span data-stu-id="a1ff1-188">Value</span></span> | <span data-ttu-id="a1ff1-189">説明</span><span class="sxs-lookup"><span data-stu-id="a1ff1-189">Meaning</span></span> |
|-|-|
| `Default` | <span data-ttu-id="a1ff1-190">既定のモードでは、特定のルールがビルド警告として有効になり、特定のルールが Visual Studio IDE の提案として有効になり、残りは無効になります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-190">Default mode, where certain rules are enabled as build warnings, certain rules are enabled as Visual Studio IDE suggestions, and the remainder are disabled.</span></span> |
| `AllEnabledByDefault` | <span data-ttu-id="a1ff1-191">積極的な (オプトアウト) モード。すべてのルールが既定でビルド警告として有効になっています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-191">Aggressive or opt-out mode, where all rules are enabled by default as build warnings.</span></span> <span data-ttu-id="a1ff1-192">個々のルールを選択的に[オプトアウト](../../fundamentals/code-analysis/configuration-options.md)して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-192">You can selectively [opt out](../../fundamentals/code-analysis/configuration-options.md) of individual rules to disable them.</span></span> |
| `AllDisabledByDefault` | <span data-ttu-id="a1ff1-193">保守的な (オプトイン) モード。すべてのルールが既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-193">Conservative or opt-in mode, where all rules are disabled by default.</span></span> <span data-ttu-id="a1ff1-194">個々のルールを選択的に[オプトイン](../../fundamentals/code-analysis/configuration-options.md)して有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-194">You can selectively [opt into](../../fundamentals/code-analysis/configuration-options.md) individual rules to enable them.</span></span> |

### <a name="codeanalysistreatwarningsaserrors"></a><span data-ttu-id="a1ff1-195">CodeAnalysisTreatWarningsAsErrors</span><span class="sxs-lookup"><span data-stu-id="a1ff1-195">CodeAnalysisTreatWarningsAsErrors</span></span>

<span data-ttu-id="a1ff1-196">`CodeAnalysisTreatWarningsAsErrors` プロパティを使用すると、コード品質分析の警告 (CAxxxx) を警告として扱い、ビルドを中断するかどうかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-196">The `CodeAnalysisTreatWarningsAsErrors` property lets you configure whether code quality analysis warnings (CAxxxx) should be treated as warnings and break the build.</span></span> <span data-ttu-id="a1ff1-197">プロジェクトをビルドするときに `-warnaserror` フラグを使用すると、[.NET コード品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)の警告もエラーとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-197">If you use the `-warnaserror` flag when you build your projects, [.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) warnings are also treated as errors.</span></span> <span data-ttu-id="a1ff1-198">コード品質分析の警告がエラーとして扱われないようにするには、プロジェクト ファイル内の `CodeAnalysisTreatWarningsAsErrors` MSBuild プロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-198">If you do not want code quality analysis warnings to be treated as errors, you can set the `CodeAnalysisTreatWarningsAsErrors` MSBuild property to `false` in your project file.</span></span>

```xml
<PropertyGroup>
  <CodeAnalysisTreatWarningsAsErrors>false</CodeAnalysisTreatWarningsAsErrors>
</PropertyGroup>
```

### <a name="enablenetanalyzers"></a><span data-ttu-id="a1ff1-199">EnableNETAnalyzers</span><span class="sxs-lookup"><span data-stu-id="a1ff1-199">EnableNETAnalyzers</span></span>

<span data-ttu-id="a1ff1-200">.NET 5.0 以降をターゲットとするプロジェクトでは、[.NET コード品質分析](../../fundamentals/code-analysis/overview.md#code-quality-analysis)が既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-200">[.NET code quality analysis](../../fundamentals/code-analysis/overview.md#code-quality-analysis) is enabled, by default, for projects that target .NET 5.0 or later.</span></span> <span data-ttu-id="a1ff1-201">以前のバージョンの .NET をターゲットとするプロジェクトで .NET コード分析を有効にするには、`EnableNETAnalyzers` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-201">You can enable .NET code analysis for projects that target earlier versions of .NET by setting the `EnableNETAnalyzers` property to `true`.</span></span> <span data-ttu-id="a1ff1-202">任意のプロジェクトでコード分析を無効にするには、このプロパティを `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-202">To disable code analysis in any project, set this property to `false`.</span></span>

```xml
<PropertyGroup>
  <EnableNETAnalyzers>true</EnableNETAnalyzers>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="a1ff1-203">.Net 5.0 より前の .NET バージョンを対象とするプロジェクトで .NET コード分析を有効にするもう 1 つの方法は、[AnalysisLevel](#analysislevel) プロパティを `latest` に設定することです。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-203">Another way to enable .NET code analysis on projects that target .NET versions prior to .NET 5.0 is to set the [AnalysisLevel](#analysislevel) property to `latest`.</span></span>

### <a name="enforcecodestyleinbuild"></a><span data-ttu-id="a1ff1-204">EnforceCodeStyleInBuild</span><span class="sxs-lookup"><span data-stu-id="a1ff1-204">EnforceCodeStyleInBuild</span></span>

> [!NOTE]
> <span data-ttu-id="a1ff1-205">この機能は現在試験段階にあり、.NET 5 リリースと .NET 6 リリースの間で変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-205">This feature is currently experimental and may change between the .NET 5 and .NET 6 releases.</span></span>

<span data-ttu-id="a1ff1-206">すべての .NET プロジェクトのビルドでは、[.NET コード スタイル分析](../../fundamentals/code-analysis/overview.md#code-style-analysis)は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-206">[.NET code style analysis](../../fundamentals/code-analysis/overview.md#code-style-analysis) is disabled, by default, on build for all .NET projects.</span></span> <span data-ttu-id="a1ff1-207">`EnforceCodeStyleInBuild` プロパティを `true` に設定して、.NET プロジェクトのコード スタイル分析を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-207">You can enable code style analysis for .NET projects by setting the `EnforceCodeStyleInBuild` property to `true`.</span></span>

```xml
<PropertyGroup>
  <EnforceCodeStyleInBuild>true</EnforceCodeStyleInBuild>
</PropertyGroup>
```

<span data-ttu-id="a1ff1-208">警告またはエラーになるように[構成](../../fundamentals/code-analysis/overview.md#code-style-analysis)されているすべてのコード スタイル ルールは、ビルド時に実行され、違反を報告します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-208">All code style rules that are [configured](../../fundamentals/code-analysis/overview.md#code-style-analysis) to be warnings or errors will execute on build and report violations.</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="a1ff1-209">ランタイム構成プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-209">Run-time configuration properties</span></span>

<span data-ttu-id="a1ff1-210">アプリのプロジェクト ファイルに MSBuild プロパティを指定することで一部のランタイム動作を構成できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-210">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="a1ff1-211">ランタイム動作のその他の構成方法については、[ランタイム構成設定](../run-time-config/index.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-211">For information about other ways of configuring run-time behavior, see [Run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="a1ff1-212">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1ff1-212">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="a1ff1-213">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="a1ff1-213">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="a1ff1-214">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1ff1-214">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="a1ff1-215">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1ff1-215">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="a1ff1-216">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a1ff1-216">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="a1ff1-217">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a1ff1-217">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="a1ff1-218">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a1ff1-218">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="a1ff1-219">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="a1ff1-219">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="a1ff1-220">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="a1ff1-220">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="a1ff1-221">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1ff1-221">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="a1ff1-222">`ConcurrentGarbageCollection` プロパティでは、[バックグラウンド (同時実行) ガベージ コレクション](../../standard/garbage-collection/background-gc.md)の有効または無効が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-222">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="a1ff1-223">この値を `false` に設定すると、バックグラウンド ガベージ コレクションが無効になります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-223">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="a1ff1-224">詳細については、「[バックグラウンド GC](../run-time-config/garbage-collector.md#background-gc)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-224">For more information, see [Background GC](../run-time-config/garbage-collector.md#background-gc).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="a1ff1-225">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="a1ff1-225">InvariantGlobalization</span></span>

<span data-ttu-id="a1ff1-226">`InvariantGlobalization` プロパティでは、アプリを *globalization-invariant* モードで実行するかどうかを設定します。このモードでは、カルチャ固有のデータにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-226">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="a1ff1-227">この値を `true` に設定すると、globalization-invariant モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-227">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="a1ff1-228">詳細については、「[インバリアント モード](../run-time-config/globalization.md#invariant-mode)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-228">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="a1ff1-229">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1ff1-229">RetainVMGarbageCollection</span></span>

<span data-ttu-id="a1ff1-230">`RetainVMGarbageCollection` プロパティでは、将来利用する目的で削除済みメモリ セグメントを待機一覧に載せるように、あるいは削除済みメモリ セグメントを解放するようにガベージ コレクターを設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-230">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="a1ff1-231">この値を `true` に設定すると、セグメントを待機一覧に載せるよう、ガベージ コレクターが命令されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-231">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="a1ff1-232">詳細については、「[VM の保持](../run-time-config/garbage-collector.md#retain-vm)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-232">For more information, see [Retain VM](../run-time-config/garbage-collector.md#retain-vm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="a1ff1-233">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="a1ff1-233">ServerGarbageCollection</span></span>

<span data-ttu-id="a1ff1-234">`ServerGarbageCollection` プロパティでは、アプリケーションで使用するガベージ コレクションとして[ワークステーション ガベージ コレクションまたはサーバー ガベージ コレクション](../../standard/garbage-collection/workstation-server-gc.md)を設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-234">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="a1ff1-235">この値を `true` に設定すると、サーバー ガベージ コレクションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-235">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="a1ff1-236">詳細については、「[ワークステーションとサーバー](../run-time-config/garbage-collector.md#workstation-vs-server)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-236">For more information, see [Workstation vs. server](../run-time-config/garbage-collector.md#workstation-vs-server).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="a1ff1-237">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="a1ff1-237">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="a1ff1-238">`ThreadPoolMaxThreads` プロパティでは、ワーカー スレッド プールの最大スレッド数を設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-238">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a1ff1-239">詳細については、「[最大スレッド数](../run-time-config/threading.md#maximum-threads)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-239">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="a1ff1-240">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="a1ff1-240">ThreadPoolMinThreads</span></span>

<span data-ttu-id="a1ff1-241">`ThreadPoolMinThreads` プロパティでは、ワーカー スレッド プールの最小スレッド数を設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-241">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="a1ff1-242">詳細については、「[最小スレッド数](../run-time-config/threading.md#minimum-threads)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-242">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="a1ff1-243">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="a1ff1-243">TieredCompilation</span></span>

<span data-ttu-id="a1ff1-244">`TieredCompilation` プロパティでは、Just-In-Time (JIT) コンパイラで[階層型コンパイル](../whats-new/dotnet-core-3-0.md#tiered-compilation)を使用するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-244">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="a1ff1-245">この値を `false` に設定すると、階層型コンパイルが無効になります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-245">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="a1ff1-246">詳細については、「[階層型コンパイル](../run-time-config/compilation.md#tiered-compilation)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-246">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="a1ff1-247">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="a1ff1-247">TieredCompilationQuickJit</span></span>

<span data-ttu-id="a1ff1-248">`TieredCompilationQuickJit` プロパティでは、JIT コンパイラでクイック JIT を使用するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-248">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="a1ff1-249">この値を `false` に設定すると、クイック JIT が無効になります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-249">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="a1ff1-250">詳細については、「[クイック JIT](../run-time-config/compilation.md#quick-jit)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-250">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="a1ff1-251">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="a1ff1-251">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="a1ff1-252">`TieredCompilationQuickJitForLoops` プロパティでは、ループを含むメソッドに対して JIT コンパイラでクリック JIT を使用するかどうかを設定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-252">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a1ff1-253">この値を `true` に設定すると、ループが含まれるメソッドでクイック JIT が有効になります。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-253">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="a1ff1-254">詳細については、「[ループに対するクイック JIT](../run-time-config/compilation.md#quick-jit-for-loops)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-254">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties-and-items"></a><span data-ttu-id="a1ff1-255">プロパティと項目の参照</span><span class="sxs-lookup"><span data-stu-id="a1ff1-255">Reference properties and items</span></span>

- [<span data-ttu-id="a1ff1-256">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a1ff1-256">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="a1ff1-257">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a1ff1-257">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="a1ff1-258">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="a1ff1-258">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="a1ff1-259">参照</span><span class="sxs-lookup"><span data-stu-id="a1ff1-259">Reference</span></span>](#reference)
- [<span data-ttu-id="a1ff1-260">Restore プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-260">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="a1ff1-261">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="a1ff1-261">AssetTargetFallback</span></span>

<span data-ttu-id="a1ff1-262">`AssetTargetFallback` プロパティを使用すると、プロジェクト参照と NuGet パッケージに対して、互換性のある追加のフレームワーク バージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-262">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="a1ff1-263">たとえば、`PackageReference` を使用してパッケージの依存関係を指定し、そのパッケージにプロジェクトの `TargetFramework` と互換性のある資産が含まれない場合は、`AssetTargetFallback` プロパティが機能します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-263">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="a1ff1-264">参照されたパッケージの互換性は、`AssetTargetFallback` で指定された各ターゲット フレームワークを使用して再確認されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-264">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="a1ff1-265">`AssetTargetFallback` プロパティを 1 つ以上の[ターゲット フレームワーク バージョン](../../standard/frameworks.md#supported-target-frameworks)に設定できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-265">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-frameworks).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="a1ff1-266">PackageReference</span><span class="sxs-lookup"><span data-stu-id="a1ff1-266">PackageReference</span></span>

<span data-ttu-id="a1ff1-267">`PackageReference` 項目では、NuGet パッケージへの参照が定義されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-267">The `PackageReference` item defines a reference to a NuGet package.</span></span>

<span data-ttu-id="a1ff1-268">`Include` 属性は、パッケージ ID を指定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-268">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="a1ff1-269">`Version` 属性では、バージョンまたはバージョン範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-269">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="a1ff1-270">最小バージョン、最大バージョン、範囲、厳密一致を指定する方法については、「[バージョン範囲](/nuget/concepts/package-versioning#version-ranges)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-270">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="a1ff1-271">また、メタデータ `IncludeAssets`、`ExcludeAssets`、`PrivateAssets` をプロジェクト参照に追加できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-271">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="a1ff1-272">次の例のプロジェクト ファイル スニペットでは、[System.Runtime](https://www.nuget.org/packages/System.Runtime/) パッケージを参照しています。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-272">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="a1ff1-273">詳細については、[プロジェクト ファイルのパッケージ参照](/nuget/consume-packages/package-references-in-project-files)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-273">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="a1ff1-274">ProjectReference</span><span class="sxs-lookup"><span data-stu-id="a1ff1-274">ProjectReference</span></span>

<span data-ttu-id="a1ff1-275">`ProjectReference` 項目では、別のプロジェクトへの参照を定義します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-275">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="a1ff1-276">参照されたプロジェクトは NuGet パッケージ依存関係として追加されます。つまり、`PackageReference` と同じように処理されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-276">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="a1ff1-277">`Include` 属性は、プロジェクトのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-277">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="a1ff1-278">また、メタデータ `IncludeAssets`、`ExcludeAssets`、`PrivateAssets` をプロジェクト参照に追加できます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-278">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="a1ff1-279">次の例のプロジェクト ファイル スニペットでは、`Project2` という名前のプロジェクトが参照されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-279">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="a1ff1-280">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1ff1-280">Reference</span></span>

<span data-ttu-id="a1ff1-281">`Reference` 項目では、アセンブリ ファイルへの参照を定義します。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-281">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="a1ff1-282">`Include` 属性によってファイルの名前が指定され、`HintPath` メタデータによってアセンブリへのパスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-282">The `Include` attribute specifies the name of the file, and the `HintPath` metadata specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="a1ff1-283">restore のプロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-283">Restore properties</span></span>

<span data-ttu-id="a1ff1-284">参照されたパッケージを復元すると、その直接的な依存関係と間接的な依存関係がすべてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-284">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="a1ff1-285">`RestorePackagesPath` や `RestoreIgnoreFailedSources` など、プロパティを指定することでパッケージ復元をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-285">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="a1ff1-286">以上のプロパティとその他のプロパティの詳細については、「[restore ターゲット](/nuget/reference/msbuild-targets#restore-target)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1ff1-286">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="a1ff1-287">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1ff1-287">See also</span></span>

- [<span data-ttu-id="a1ff1-288">MSBuild スキーマ リファレンス</span><span class="sxs-lookup"><span data-stu-id="a1ff1-288">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="a1ff1-289">MSBuild の共通プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-289">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="a1ff1-290">NuGet pack の MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-290">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="a1ff1-291">NuGet restore の MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-291">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="a1ff1-292">ビルドのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="a1ff1-292">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
