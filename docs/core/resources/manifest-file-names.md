---
title: MSBuild によるマニフェスト ファイル名の生成方法
description: MSBuild によってコンパイル時に生成されるリソース マニフェスト ファイル名の名前に影響する要因について説明します。
ms.date: 05/08/2020
ms.topic: conceptual
ms.openlocfilehash: 2e0461e34bbd7f8da35bea1db1913a32915c7117
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970682"
---
# <a name="how-resource-manifest-files-are-named"></a><span data-ttu-id="08a31-103">リソース マニフェスト ファイルの名前付け方法</span><span class="sxs-lookup"><span data-stu-id="08a31-103">How resource manifest files are named</span></span>

<span data-ttu-id="08a31-104">MSBuild により .NET Core プロジェクトがコンパイルされると、 *.resx* ファイル拡張子を持つ XML リソース ファイルがバイナリ *.resources* ファイルに変換されます。</span><span class="sxs-lookup"><span data-stu-id="08a31-104">When MSBuild compiles a .NET Core project, XML resource files, which have the *.resx* file extension, are converted into binary *.resources* files.</span></span> <span data-ttu-id="08a31-105">バイナリ ファイルは、コンパイラの出力に埋め込まれ、<xref:System.Resources.ResourceManager> で読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="08a31-105">The binary files are embedded into the output of the compiler and can be read by the <xref:System.Resources.ResourceManager>.</span></span> <span data-ttu-id="08a31-106">この記事では、MSBuild によって各 *.resources* ファイルの名前がどのように選択されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08a31-106">This article describes how MSBuild chooses a name for each *.resources* file.</span></span>

> [!TIP]
> <span data-ttu-id="08a31-107">リソース項目をプロジェクト ファイルに明示的に追加するときに、それが [.NET Core の既定の include glob にも含まれる](../project-sdk/overview.md#default-includes-and-excludes)場合、ビルド エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="08a31-107">If you explicitly add a resource item to your project file, and it's also [included with the default include globs for .NET Core](../project-sdk/overview.md#default-includes-and-excludes), you will get a build error.</span></span> <span data-ttu-id="08a31-108">リソース ファイルを `EmbeddedResource` 項目として手動で含めるには、`EnableDefaultEmbeddedResourceItems` プロパティを false に設定します。</span><span class="sxs-lookup"><span data-stu-id="08a31-108">To manually include resource files as `EmbeddedResource` items, set the `EnableDefaultEmbeddedResourceItems` property to false.</span></span>

## <a name="default-name"></a><span data-ttu-id="08a31-109">既定名</span><span class="sxs-lookup"><span data-stu-id="08a31-109">Default name</span></span>

<span data-ttu-id="08a31-110">.NET Core 3.0 以降では、次の両方の条件が満たされる場合に、リソース マニフェストの既定名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="08a31-110">In .NET Core 3.0 and later, the default name for a resource manifest is used when both of the following conditions are met:</span></span>

- <span data-ttu-id="08a31-111">リソース ファイルが、`LogicalName`、`ManifestResourceName`、または `DependentUpon` メタデータを持つ `EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれていない。</span><span class="sxs-lookup"><span data-stu-id="08a31-111">The resource file is not explicitly included in the project file as an `EmbeddedResource` item with `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata.</span></span>
- <span data-ttu-id="08a31-112">`EmbeddedResourceUseDependentUponConvention` プロパティがプロジェクト ファイルで `false` に設定されていない。</span><span class="sxs-lookup"><span data-stu-id="08a31-112">The `EmbeddedResourceUseDependentUponConvention` property is not set to `false` in the project file.</span></span> <span data-ttu-id="08a31-113">既定では、このプロパティは `true`に設定されています。</span><span class="sxs-lookup"><span data-stu-id="08a31-113">By default, this property is set to `true`.</span></span> <span data-ttu-id="08a31-114">詳細については、「[EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08a31-114">For more information, see [EmbeddedResourceUseDependentUponConvention](../project-sdk/msbuild-props.md#embeddedresourceusedependentuponconvention).</span></span>

<span data-ttu-id="08a31-115">リソース ファイルが、同じルート ファイル名のソース ファイル ( *.cs* または *.vb*) と併置されている場合、ソース ファイルで定義されている最初の型の完全な名前がマニフェスト ファイル名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="08a31-115">If the resource file is colocated with a source file (*.cs* or *.vb*) of the same root file name, the full name of the first type that's defined in the source file is used for the manifest file name.</span></span> <span data-ttu-id="08a31-116">たとえば、`MyNamespace.Form1` が *Form1.cs* で定義されている最初の型であり、*Form1.cs* が *Form1.resx* と併置されている場合、そのリソース ファイルに対して生成されたマニフェスト名は *MyNamespace.Form1.resources* となります。</span><span class="sxs-lookup"><span data-stu-id="08a31-116">For example, if `MyNamespace.Form1` is the first type defined in *Form1.cs*, and *Form1.cs* is colocated with *Form1.resx*, the generated manifest name for that resource file is *MyNamespace.Form1.resources*.</span></span>

## <a name="logicalname-metadata"></a><span data-ttu-id="08a31-117">LogicalName メタデータ</span><span class="sxs-lookup"><span data-stu-id="08a31-117">LogicalName metadata</span></span>

<span data-ttu-id="08a31-118">リソース ファイルが `LogicalName` メタデータを持つ `EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれている場合、`LogicalName` 値がマニフェスト名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="08a31-118">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `LogicalName` metadata, the `LogicalName` value is used as the manifest name.</span></span> <span data-ttu-id="08a31-119">`LogicalName` は、他のメタデータや設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="08a31-119">`LogicalName` takes precedence over any other metadata or setting.</span></span>

<span data-ttu-id="08a31-120">たとえば、次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*SomeName.resources* となります。</span><span class="sxs-lookup"><span data-stu-id="08a31-120">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" LogicalName="SomeName.resources" />
```

<span data-ttu-id="08a31-121">- または -</span><span class="sxs-lookup"><span data-stu-id="08a31-121">-or-</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" LogicalName="SomeName.resources" />
```

## <a name="manifestresourcename-metadata"></a><span data-ttu-id="08a31-122">ManifestResourceName メタデータ</span><span class="sxs-lookup"><span data-stu-id="08a31-122">ManifestResourceName metadata</span></span>

<span data-ttu-id="08a31-123">リソース ファイルが `ManifestResourceName` メタデータを持つ (`LogicalName` は存在しない)`EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれている場合、`ManifestResourceName` 値は、ファイル拡張子 *.resources* と組み合わされ、マニフェスト ファイル名として使用されます。</span><span class="sxs-lookup"><span data-stu-id="08a31-123">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `ManifestResourceName` metadata (and `LogicalName` is absent), the `ManifestResourceName` value, combined with the file extension *.resources*, is used as the manifest file name.</span></span>

<span data-ttu-id="08a31-124">たとえば、次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*SomeName.resources* となります。</span><span class="sxs-lookup"><span data-stu-id="08a31-124">For example, the manifest name for the resource file that's defined in the following project file snippet is *SomeName.resources*.</span></span>

```xml
<EmbeddedResource Include="X.resx" ManifestResourceName="SomeName" />
```

<span data-ttu-id="08a31-125">次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*SomeName.fr-FR.resources* となります。</span><span class="sxs-lookup"><span data-stu-id="08a31-125">The manifest name for the resource file that's defined in the following project file snippet is *SomeName.fr-FR.resources*.</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" ManifestResourceName="SomeName.fr-FR" />
```

## <a name="dependentupon-metadata"></a><span data-ttu-id="08a31-126">DependentUpon メタデータ</span><span class="sxs-lookup"><span data-stu-id="08a31-126">DependentUpon metadata</span></span>

<span data-ttu-id="08a31-127">リソース ファイルが `DependentUpon` メタデータを持つ (`LogicalName` と `ManifestResourceName` は存在しない) `EmbeddedResource` 項目としてプロジェクト ファイルに明示的に含まれている場合、`DependentUpon` で定義されているソース ファイルからの情報がリソース マニフェストのファイル名に使用されます。</span><span class="sxs-lookup"><span data-stu-id="08a31-127">If a resource file is explicitly included in the project file as an `EmbeddedResource` item with `DependentUpon` metadata (and `LogicalName` and `ManifestResourceName` are absent), information from the source file defined by `DependentUpon` is used for the resource manifest file name.</span></span> <span data-ttu-id="08a31-128">具体的には、ソース ファイルで定義されている最初の型の名前がマニフェスト名で次のように使用されます: *Namespace.Classname\[.Culture].resources*。</span><span class="sxs-lookup"><span data-stu-id="08a31-128">Specifically, the name of the first type that's defined in the source file is used in the manifest name as follows: *Namespace.Classname\[.Culture].resources*.</span></span>

<span data-ttu-id="08a31-129">たとえば、次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は、*Namespace.Classname.resources* となります (ここで、`Namespace.Classname` は *MyTypes.cs* で定義されている最初のクラスです)。</span><span class="sxs-lookup"><span data-stu-id="08a31-129">For example, the manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.resx" DependentUpon="MyTypes.cs">
```

<span data-ttu-id="08a31-130">次のプロジェクト ファイル スニペットで定義されているリソース ファイルのマニフェスト名は *Namespace.Classname.fr-FR.resources* となります (ここで、`Namespace.Classname` は *MyTypes.cs* で定義されている最初のクラスです)。</span><span class="sxs-lookup"><span data-stu-id="08a31-130">The manifest name for the resource file that's defined in the following project file snippet is *Namespace.Classname.fr-FR.resources* (where `Namespace.Classname` is the first class that's defined in *MyTypes.cs*).</span></span>

```xml
<EmbeddedResource Include="X.fr-FR.resx" DependentUpon="MyTypes.cs">
```

## <a name="embeddedresourceusedependentuponconvention-property"></a><span data-ttu-id="08a31-131">EmbeddedResourceUseDependentUponConvention プロパティ</span><span class="sxs-lookup"><span data-stu-id="08a31-131">EmbeddedResourceUseDependentUponConvention property</span></span>

<span data-ttu-id="08a31-132">プロジェクト ファイルで `EmbeddedResourceUseDependentUponConvention` が `false` に設定されている場合、各リソース マニフェストのファイル名は、プロジェクトのルート名前空間と、プロジェクト ルートから *.resx* ファイルへの相対パスに基づきます。</span><span class="sxs-lookup"><span data-stu-id="08a31-132">If `EmbeddedResourceUseDependentUponConvention` is set to `false` in the project file, each resource manifest file name is based off the root namespace for the project and the relative path from the project root to the *.resx* file.</span></span> <span data-ttu-id="08a31-133">さらに具体的に言うと、生成されるリソース マニフェストのファイル名は *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources* となります。</span><span class="sxs-lookup"><span data-stu-id="08a31-133">More specifically, the generated resource manifest file name is *RootNamespace.RelativePathWithDotsForSlashes.\[Culture.]resources*.</span></span> <span data-ttu-id="08a31-134">これは、3.0 より前の .NET Core バージョンでマニフェスト名を生成するために使用されるロジックでもあります。</span><span class="sxs-lookup"><span data-stu-id="08a31-134">This is also the logic used to generate manifest names in .NET Core versions prior to 3.0.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="08a31-135">`RootNamespace` が定義されていない場合は、既定でそのプロジェクト名になります。</span><span class="sxs-lookup"><span data-stu-id="08a31-135">If `RootNamespace` is not defined, it defaults to the project name.</span></span>
> - <span data-ttu-id="08a31-136">`LogicalName`、`ManifestResourceName`、または `DependentUpon` メタデータがプロジェクト ファイルで `EmbeddedResource` 項目に対して指定されている場合、この名前付けルールはそのリソース ファイルには適用されません。</span><span class="sxs-lookup"><span data-stu-id="08a31-136">If `LogicalName`, `ManifestResourceName`, or `DependentUpon` metadata is specified for an `EmbeddedResource` item in the project file, this naming rule does not apply to that resource file.</span></span>

## <a name="see-also"></a><span data-ttu-id="08a31-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="08a31-137">See also</span></span>

- [<span data-ttu-id="08a31-138">マニフェスト リソースの名前付けのしくみ</span><span class="sxs-lookup"><span data-stu-id="08a31-138">How Manifest Resource Naming Works</span></span>](https://gist.github.com/BenVillalobos/041673b9a73bec60fdc3bf0f86fae62a)
- [<span data-ttu-id="08a31-139">.NET Core SDK プロジェクトの MSBuild プロパティ</span><span class="sxs-lookup"><span data-stu-id="08a31-139">MSBuild properties for .NET Core SDK projects</span></span>](../project-sdk/msbuild-props.md)
- [<span data-ttu-id="08a31-140">MSBuild に関する破壊的変更</span><span class="sxs-lookup"><span data-stu-id="08a31-140">MSBuild breaking changes</span></span>](../compatibility/msbuild.md)
