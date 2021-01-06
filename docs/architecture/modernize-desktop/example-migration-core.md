---
title: .NET Core 3.1 への移行の例
description: .NET Framework を対象とするサンプルアプリケーションを .NET Core 3.1 に移行する方法を示します。
ms.date: 05/12/2020
ms.openlocfilehash: 6a0311e9aaeb25ac39f3394d3a62e17046fe03d8
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2020
ms.locfileid: "97866656"
---
# <a name="example-of-migrating-to-net-core-31"></a><span data-ttu-id="14ffb-103">.NET Core 3.1 への移行の例</span><span class="sxs-lookup"><span data-stu-id="14ffb-103">Example of migrating to .NET Core 3.1</span></span>

<span data-ttu-id="14ffb-104">この章では、.NET Framework から .NET Core への既存のアプリケーションの移行を実行する際に役立つ実用的なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-104">In this chapter, we present practical guidelines to help you perform a migration of your existing application from .NET Framework to .NET Core.</span></span>

<span data-ttu-id="14ffb-105">ここでは、適切に構成されたプロセスを紹介し、各ステップで考慮する必要がある最も重要なプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-105">We present a well-structured process you can follow and the most important things to consider on each step.</span></span>

<span data-ttu-id="14ffb-106">次に、WinForms と WPF の両方のバージョンから、サンプルデスクトップアプリケーションのステップバイステップ移行プロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-106">We then document a step-by-step migration process for a sample desktop application, both from WinForms and WPF versions.</span></span>

## <a name="migration-process-overview"></a><span data-ttu-id="14ffb-107">移行プロセスの概要</span><span class="sxs-lookup"><span data-stu-id="14ffb-107">Migration process overview</span></span>

<span data-ttu-id="14ffb-108">移行プロセスは、次の4つの手順で構成されています。</span><span class="sxs-lookup"><span data-stu-id="14ffb-108">The migration process consists of four sequential steps:</span></span>

1. <span data-ttu-id="14ffb-109">**準備**: プロジェクトにおける依存関係について理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-109">**Preparation**: Understand the dependencies the project has to have an idea of what's ahead.</span></span> <span data-ttu-id="14ffb-110">このステップでは、現在のプロジェクトを、移行の開始点を簡略化する状態にします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-110">In this step, you take the current project into a state that simplifies the startup point for the migration.</span></span>

2. <span data-ttu-id="14ffb-111">**プロジェクトファイルの移行:** .net Core プロジェクトでは、新しい SDK スタイルのプロジェクト形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-111">**Migrate Project File:** .NET Core projects use the new SDK-style project format.</span></span> <span data-ttu-id="14ffb-112">この形式で新しいプロジェクトファイルを作成するか、SDK スタイルを使用する必要があるものを更新します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-112">Create a new project file with this format or update the one you have to use the SDK style.</span></span>

3. <span data-ttu-id="14ffb-113">**コードを修正してビルドする:** .NET Core で、.NET Framework と .NET Core の間の API レベルの違いに対処するコードをビルドします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-113">**Fix code and build:** Build the code in .NET Core addressing API-level differences between .NET Framework and .NET Core.</span></span> <span data-ttu-id="14ffb-114">必要に応じて、サードパーティのパッケージを .NET Core をサポートするパッケージに更新します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-114">If needed, update third-party packages to the ones that support .NET Core.</span></span>

4. <span data-ttu-id="14ffb-115">**実行とテスト:** 実行時まで表示されない相違がある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-115">**Run and test:** There might be differences that don't show up until run time.</span></span> <span data-ttu-id="14ffb-116">そのため、必ずアプリケーションを実行し、すべてが期待どおりに動作することをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="14ffb-116">So, don't forget to run the application and test that everything works as expected.</span></span>

### <a name="preparation"></a><span data-ttu-id="14ffb-117">準備</span><span class="sxs-lookup"><span data-stu-id="14ffb-117">Preparation</span></span>

#### <a name="migrate-packagesconfig-file"></a><span data-ttu-id="14ffb-118">packages.config ファイルの移行</span><span class="sxs-lookup"><span data-stu-id="14ffb-118">Migrate packages.config file</span></span>

<span data-ttu-id="14ffb-119">.NET Framework アプリケーションでは、外部パッケージへのすべての参照が *packages.config* ファイルで宣言されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-119">In a .NET Framework application, all references to external packages are declared in the *packages.config* file.</span></span> <span data-ttu-id="14ffb-120">.NET Core では、 *packages.config* ファイルを使用する必要がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="14ffb-120">In .NET Core, there's no longer the need to use the *packages.config* file.</span></span> <span data-ttu-id="14ffb-121">代わりに、プロジェクトファイル内の [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) プロパティを使用して、アプリの NuGet パッケージを指定します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-121">Instead, use the [PackageReference](../../core/project-sdk/msbuild-props.md#packagereference) property inside the project file to specify the NuGet packages for your app.</span></span>

<span data-ttu-id="14ffb-122">そのため、1つの形式から別の形式に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-122">So, you need to transition from one format to another.</span></span> <span data-ttu-id="14ffb-123">更新を手動で実行するには、 *packages.config* ファイルに含まれている依存関係を取得し、という形式でプロジェクトファイルに移行し `PackageReference` ます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-123">You can do the update manually, taking the dependencies contained in the *packages.config* file and migrating them to the project file with the `PackageReference` format.</span></span> <span data-ttu-id="14ffb-124">または、Visual Studio で作業を実行できるようにするには、 *packages.config* ファイルを右クリックし、[ **packages.config を PackageReference に移行する** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-124">Or, you can let Visual Studio do the work for you: right-click on the *packages.config* file and select the **Migrate packages.config to PackageReference** option.</span></span>

#### <a name="verify-every-dependency-compatibility-in-net-core"></a><span data-ttu-id="14ffb-125">.NET Core ですべての依存関係の互換性を確認する</span><span class="sxs-lookup"><span data-stu-id="14ffb-125">Verify every dependency compatibility in .NET Core</span></span>

<span data-ttu-id="14ffb-126">パッケージ参照を移行したら、各参照に互換性があるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-126">Once you've migrated the package references, you must check each reference for compatibility.</span></span> <span data-ttu-id="14ffb-127">アプリケーションが [nuget.org](https://www.nuget.org/)で使用している各 NuGet パッケージの依存関係を調べることができます。パッケージに .NET Standard 依存関係がある場合は、.net Core 3.1 がすべてのバージョンの .NET Standard を [サポート](../../standard/net-standard.md#net-implementation-support) しているため、.net core で動作します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-127">You can explore the dependencies of each NuGet package your application is using on [nuget.org](https://www.nuget.org/). If the package has .NET Standard dependencies, then it's going to work on .NET Core because .NET Core 3.1 [supports](../../standard/net-standard.md#net-implementation-support) all versions of .NET Standard.</span></span> <span data-ttu-id="14ffb-128">次の図は、パッケージの依存関係を示してい `Castle.Windsor` ます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-128">The following image shows the dependencies for the `Castle.Windsor` package:</span></span>

![Windsor パッケージの NuGet 依存関係のスクリーンショット](./media/example-migration-core/nuget-dependencies.png)

<span data-ttu-id="14ffb-130">パッケージの互換性を確認するには、 <https://fuget.org> バージョンと依存関係に関するより詳細な情報を提供するツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-130">To check the package compatibility, you can use the tool <https://fuget.org> that offers a more detailed information about versions and dependencies.</span></span>

<span data-ttu-id="14ffb-131">.NET Core をサポートしていない古いバージョンのパッケージがプロジェクトで参照されている可能性がありますが、それをサポートしている新しいバージョンが見つかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-131">Maybe the project is referencing older package versions that don't support .NET Core, but you might find newer versions that do support it.</span></span> <span data-ttu-id="14ffb-132">そのため、通常は、パッケージを新しいバージョンに更新することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-132">So, updating packages to newer versions is generally a good recommendation.</span></span> <span data-ttu-id="14ffb-133">ただし、パッケージバージョンを更新すると、コードの更新を必要とする重大な変更が発生する場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="14ffb-133">However, you should consider that updating the package version can introduce some breaking changes that would force you to update your code.</span></span>

<span data-ttu-id="14ffb-134">互換性のあるバージョンが見つからない場合はどうなりますか。</span><span class="sxs-lookup"><span data-stu-id="14ffb-134">What happens if you don't find a compatible version?</span></span> <span data-ttu-id="14ffb-135">これらの重大な変更のためにパッケージのバージョンを更新したくない場合はどうすればよいですか。</span><span class="sxs-lookup"><span data-stu-id="14ffb-135">What if you just don't want to update the version of a package because of these breaking changes?</span></span> <span data-ttu-id="14ffb-136">.NET Core アプリケーションの .NET Framework パッケージに依存する可能性があるため、心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="14ffb-136">Don't worry because it's possible to depend on .NET Framework packages from a .NET Core application.</span></span> <span data-ttu-id="14ffb-137">外部パッケージが .NET Core で使用できない API を呼び出す場合は、実行時エラーが発生する可能性があるため、必ずテストしてください。</span><span class="sxs-lookup"><span data-stu-id="14ffb-137">Don't forget to test it extensively because it can cause run-time errors if the external package calls an API that isn't available on .NET Core.</span></span> <span data-ttu-id="14ffb-138">これは、更新される予定のない古いパッケージを使用している場合に適しています。また、.NET Core での作業に再ターゲットすることもできます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-138">This is great for when you're using an old package that isn't going to be updated and you can just retarget to work on the .NET Core.</span></span>

#### <a name="check-for-api-compatibility"></a><span data-ttu-id="14ffb-139">API の互換性を確認する</span><span class="sxs-lookup"><span data-stu-id="14ffb-139">Check for API compatibility</span></span>

<span data-ttu-id="14ffb-140">.NET Framework と .NET Core の API サーフェイスは似ていますが、同一ではありません。 .NET Core で使用できる Api を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-140">Since the API surface in .NET Framework and .NET Core is similar but not identical, you must check which APIs are available on .NET Core and which aren't.</span></span> <span data-ttu-id="14ffb-141">.Net 移植性アナライザーツールを使用すると、.NET Core に存在しない Api を表示できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-141">You can use the .NET Portability Analyzer tool to surface APIs used that aren't present on .NET Core.</span></span> <span data-ttu-id="14ffb-142">アプリのバイナリレベルを確認し、呼び出されたすべての Api を抽出して、ターゲットフレームワークで使用できない Api (この場合は .NET Core 3.1) を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-142">It looks at the binary level of your app, extracts all the APIs that are called, and then lists which APIs aren't available on your target framework (.NET Core 3.1 in this case).</span></span>

<span data-ttu-id="14ffb-143">このツールの詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14ffb-143">You can find more information about this tool at:</span></span>

<https://docs.microsoft.com/dotnet/standard/analyzers/portability-analyzer>

<span data-ttu-id="14ffb-144">このツールの興味深い点は、外部パッケージからのコードではなく、独自のコードの違いだけを表示し、変更できないことです。</span><span class="sxs-lookup"><span data-stu-id="14ffb-144">An interesting aspect of this tool is that it only surfaces the differences from your own code and not code from external packages, which you can't change.</span></span> <span data-ttu-id="14ffb-145">.NET Core で動作するように、これらのパッケージのほとんどを更新しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-145">Remember you should have updated most of these packages to make them work with .NET Core.</span></span>

### <a name="migrate-project-file"></a><span data-ttu-id="14ffb-146">プロジェクトファイルの移行</span><span class="sxs-lookup"><span data-stu-id="14ffb-146">Migrate project file</span></span>

#### <a name="create-the-new-net-core-project"></a><span data-ttu-id="14ffb-147">新しい .NET Core プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="14ffb-147">Create the new .NET Core project</span></span>

<span data-ttu-id="14ffb-148">ほとんどの場合、既存のプロジェクトを新しい .NET Core 形式に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-148">In most of the cases, you'll want to update your existing project to the new .NET Core format.</span></span> <span data-ttu-id="14ffb-149">ただし、古いプロジェクトを維持しながら新しいプロジェクトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-149">However, you can also create a new project while maintaining the old one.</span></span> <span data-ttu-id="14ffb-150">古いプロジェクトを更新することによる主な欠点は、デザイナーのサポートが失われることです。これは、お客様にとって重要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-150">The main drawback from updating the old project is that you lose designer support, which may be important for you.</span></span> <span data-ttu-id="14ffb-151">デザイナーを引き続き使用する場合は、新しい .NET Core プロジェクトを古いものと並行して作成し、アセットを共有する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-151">If you want to keep using the designer, you must create a new .NET Core project in parallel with the old one and share assets.</span></span> <span data-ttu-id="14ffb-152">デザイナーで UI 要素を変更する必要がある場合は、古いプロジェクトに切り替えてそれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-152">If you need to modify UI elements in the designer, you can switch to the old project to do that.</span></span> <span data-ttu-id="14ffb-153">また、資産はリンクされているため、.NET Core プロジェクトでも更新されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-153">And since assets are linked, they'll be updated in the .NET Core project as well.</span></span>

<span data-ttu-id="14ffb-154">.NET Core 用の [SDK スタイルのプロジェクト](../../core/project-sdk/msbuild-props.md) は、.NET Framework のプロジェクト形式よりもはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="14ffb-154">The [SDK-style project](../../core/project-sdk/msbuild-props.md) for .NET Core is a lot simpler than .NET Framework's project format.</span></span> <span data-ttu-id="14ffb-155">前述のエントリとは別 `PackageReference` に、さらに多くのことを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="14ffb-155">And apart from the previously mentioned `PackageReference` entries, you won't need to do much more.</span></span> <span data-ttu-id="14ffb-156">新しいプロジェクト形式には、ファイルやファイルなど、 [既定で](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects)特定のファイル拡張子が含まれていますが、 `.cs` `.xaml` プロジェクトファイルに明示的に含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="14ffb-156">The new project format includes certain file extensions [by default](../../core/tools/csproj.md#default-compilation-includes-in-net-core-projects), such as `.cs` and `.xaml` files, without the need to explicitly include them in the project file.</span></span>

#### <a name="assemblyinfo-considerations"></a><span data-ttu-id="14ffb-157">Assembly.info に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="14ffb-157">Assembly.info considerations</span></span>

<span data-ttu-id="14ffb-158">属性は .NET Core プロジェクトで自動生成されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-158">Attributes are autogenerated on .NET Core projects.</span></span> <span data-ttu-id="14ffb-159">プロジェクトに *AssemblyInfo.cs* ファイルが含まれている場合は、定義が重複するため、コンパイルの競合が発生します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-159">If the project contains an *AssemblyInfo.cs* file, the definitions will be duplicated, which will cause compilation conflicts.</span></span> <span data-ttu-id="14ffb-160">.Net Core プロジェクトファイルに次のエントリを追加することで、古い *AssemblyInfo.cs* ファイルを削除するか、自動生成を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-160">You can delete the older *AssemblyInfo.cs* file or disable autogeneration by adding the following entry to the .NET Core project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
  </PropertyGroup>
</Project>
```

#### <a name="resources"></a><span data-ttu-id="14ffb-161">リソース</span><span class="sxs-lookup"><span data-stu-id="14ffb-161">Resources</span></span>

<span data-ttu-id="14ffb-162">埋め込みリソースは自動的にインクルードされますが、リソースは含まれないため、リソースを新しいプロジェクトファイルに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-162">Embedded resources are included automatically but resources aren't, so you need to migrate the resources to the new project file.</span></span>

#### <a name="package-references"></a><span data-ttu-id="14ffb-163">パッケージ参照</span><span class="sxs-lookup"><span data-stu-id="14ffb-163">Package references</span></span>

<span data-ttu-id="14ffb-164">**PackageReference への packages.config 移行** オプションを使用すると、前に説明したように、外部パッケージの参照を新しい形式に簡単に移動できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-164">With the **Migrate packages.config to PackageReference** option, you can easily move your external package references to the new format as previously mentioned.</span></span>

#### <a name="update-package-references"></a><span data-ttu-id="14ffb-165">パッケージ参照の更新</span><span class="sxs-lookup"><span data-stu-id="14ffb-165">Update package references</span></span>

<span data-ttu-id="14ffb-166">前のセクションで示したように、互換性のあるものとして見つかったパッケージのバージョンを更新します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-166">Update the versions of the packages you've found to be compatible, as shown in the previous section.</span></span>

### <a name="fix-the-code-and-build"></a><span data-ttu-id="14ffb-167">コードを修正してビルドする</span><span class="sxs-lookup"><span data-stu-id="14ffb-167">Fix the code and build</span></span>

#### <a name="microsoftwindowscompatibility"></a><span data-ttu-id="14ffb-168">Microsoft. Windows. 互換性</span><span class="sxs-lookup"><span data-stu-id="14ffb-168">Microsoft.Windows.Compatibility</span></span>

<span data-ttu-id="14ffb-169">アプリケーションが .NET Core で使用できない Api (レジストリ、Acl、WCF など) に依存している場合、これらの Windows 固有の Api を追加するには、パッケージへの参照を含める必要があり `Microsoft.Windows.Compatibility` ます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-169">If your application depends on APIs that aren't available on .NET Core, such as Registry, ACLs, or WCF, you have to include a reference to the `Microsoft.Windows.Compatibility` package to add these Windows-specific APIs.</span></span> <span data-ttu-id="14ffb-170">.NET Core で動作しますが、クロスプラットフォームではないため、含まれていません。</span><span class="sxs-lookup"><span data-stu-id="14ffb-170">They work on .NET Core but aren't included as they aren't cross-platform.</span></span>

<span data-ttu-id="14ffb-171">API Analyzer () というツールを使用すると、 <https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer> コードと互換性のない api を識別できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-171">There's a tool called API Analyzer (<https://docs.microsoft.com/dotnet/standard/analyzers/api-analyzer>) that helps you identify APIs that aren't compatible with your code.</span></span>

#### <a name="use-if-directives"></a><span data-ttu-id="14ffb-172">If ディレクティブを使用する \#</span><span class="sxs-lookup"><span data-stu-id="14ffb-172">Use \#if directives</span></span>

<span data-ttu-id="14ffb-173">.NET Framework と .NET Core を対象とする場合に異なる実行パスが必要な場合は、コンパイル定数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-173">If you need different execution paths when targeting .NET Framework and .NET Core, you should use compilation constants.</span></span> <span data-ttu-id="14ffb-174">\#同じコードベースを両方のターゲットに保持するために、いくつかの if ディレクティブをコードに追加します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-174">Add some \#if directives to your code to keep the same code base for both targets.</span></span>

#### <a name="technologies-not-available-on-net-core"></a><span data-ttu-id="14ffb-175">.NET Core で使用できないテクノロジ</span><span class="sxs-lookup"><span data-stu-id="14ffb-175">Technologies not available on .NET Core</span></span>

<span data-ttu-id="14ffb-176">次のような一部のテクノロジは .NET Core では使用できません。</span><span class="sxs-lookup"><span data-stu-id="14ffb-176">Some technologies aren't available on .NET Core, such as:</span></span>

* <span data-ttu-id="14ffb-177">AppDomain</span><span class="sxs-lookup"><span data-stu-id="14ffb-177">AppDomains</span></span>
* <span data-ttu-id="14ffb-178">リモート処理</span><span class="sxs-lookup"><span data-stu-id="14ffb-178">Remoting</span></span>
* <span data-ttu-id="14ffb-179">コード アクセス セキュリティ</span><span class="sxs-lookup"><span data-stu-id="14ffb-179">Code Access Security</span></span>
* <span data-ttu-id="14ffb-180">WCF サーバー</span><span class="sxs-lookup"><span data-stu-id="14ffb-180">WCF Server</span></span>
* <span data-ttu-id="14ffb-181">Windows Workflow</span><span class="sxs-lookup"><span data-stu-id="14ffb-181">Windows Workflow</span></span>

<span data-ttu-id="14ffb-182">そのため、これらのテクノロジをアプリケーションで使用している場合は、それらのテクノロジに代わるものを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-182">That's why you need to find a replacement for these technologies if you're using them in your application.</span></span> <span data-ttu-id="14ffb-183">詳細については、 [.Net Core で使用できない .NET Framework テクノロジ](../../core/porting/net-framework-tech-unavailable.md) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14ffb-183">For more information, see the [.NET Framework technologies unavailable on .NET Core](../../core/porting/net-framework-tech-unavailable.md) article.</span></span>

#### <a name="regenerate-autogenerated-clients"></a><span data-ttu-id="14ffb-184">自動生成したクライアントの再生成</span><span class="sxs-lookup"><span data-stu-id="14ffb-184">Regenerate autogenerated clients</span></span>

<span data-ttu-id="14ffb-185">アプリケーションが自動生成されたコード (WCF クライアントなど) を使用する場合は、.NET Core を対象とするようにこのコードを再生成する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-185">If your application uses autogenerated code, such as a WCF client, you may need to regenerate this code to target .NET Core.</span></span> <span data-ttu-id="14ffb-186">既定の .NET Core アセンブリセットの一部として含まれていない可能性があるため、不足している参照がいくつか見つかることがあります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-186">Sometimes, you can find some missing references since they may not be included as part of the default .NET Core assemblies set.</span></span> <span data-ttu-id="14ffb-187">などのツールを使用 <https://apisof.net/> すると、不足している参照が存在するアセンブリを簡単に見つけて、NuGet から追加することができます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-187">Using a tool like <https://apisof.net/>, you can easily locate the assembly the missing reference lives in and add it from NuGet.</span></span>

#### <a name="rolling-back-package-versions"></a><span data-ttu-id="14ffb-188">パッケージバージョンのロールバック</span><span class="sxs-lookup"><span data-stu-id="14ffb-188">Rolling back package versions</span></span>

<span data-ttu-id="14ffb-189">一般的な規則として、1つのパッケージバージョンを .NET Core と互換性があるように更新することをお勧めしました。</span><span class="sxs-lookup"><span data-stu-id="14ffb-189">As a general rule, we've previously stated that you better update every single package version to be compatible with .NET Core.</span></span> <span data-ttu-id="14ffb-190">ただし、アセンブリの更新バージョンと互換性のあるバージョンをターゲットにすると、支払いが行われないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-190">However, you can find that targeting an updated and compatible version of an assembly just doesn't pay off.</span></span> <span data-ttu-id="14ffb-191">変更のコストが許容できない場合は、.NET Framework で使用しているパッケージのバージョンをロールバックすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="14ffb-191">If the cost of change isn't acceptable, you can consider rolling back package versions keeping the ones you use on .NET Framework.</span></span> <span data-ttu-id="14ffb-192">.NET Core を対象としていない場合もありますが、サポートされていない Api を呼び出す場合を除き、適切に機能します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-192">Although they may not be targeting .NET Core, they should work well unless they call some unsupported APIs.</span></span>

### <a name="run-and-test"></a><span data-ttu-id="14ffb-193">実行してテストする</span><span class="sxs-lookup"><span data-stu-id="14ffb-193">Run and test</span></span>

<span data-ttu-id="14ffb-194">エラーを発生させずにアプリケーションを構築した後は、すべての機能をテストすることで、移行の最後の手順を開始できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-194">Once you have your application building with no errors, you can start the last step of the migration by testing every functionality.</span></span>

<span data-ttu-id="14ffb-195">この最後の手順では、アプリケーションの複雑さと使用している依存関係と Api に応じて、いくつかの異なる問題を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-195">In this final step, you can find several different issues depending on the complexity of your application and the dependencies and APIs you're using.</span></span>

<span data-ttu-id="14ffb-196">たとえば、構成ファイル (*app.config*) を使用する場合、構成セクションが存在しないなど、実行時にエラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-196">For example, if you use configuration files (*app.config*), you may find some errors at run time like Configuration Sections not present.</span></span> <span data-ttu-id="14ffb-197">NuGet パッケージを使用する `Microsoft.Extensions.Configuration` と、そのエラーを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-197">Using the `Microsoft.Extensions.Configuration` NuGet package should fix that error.</span></span>

<span data-ttu-id="14ffb-198">エラーのもう1つの理由は、 `BeginInvoke` メソッドとメソッドを使用する `EndInvoke` ことです。これらは .net Core ではサポートされていないためです。</span><span class="sxs-lookup"><span data-stu-id="14ffb-198">Another reason for errors is the use of the `BeginInvoke` and `EndInvoke` methods because they aren't supported on .NET Core.</span></span> <span data-ttu-id="14ffb-199">.Net core ではサポートされていません。これは、.NET Core には存在しないリモート処理に依存しているためです。</span><span class="sxs-lookup"><span data-stu-id="14ffb-199">They aren't supported on .NET Core because they have a dependency on Remoting, which doesn't exist on .NET Core.</span></span> <span data-ttu-id="14ffb-200">この問題を解決するに `await` は、キーワード (使用可能な場合) またはメソッドを使用してください <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="14ffb-200">To solve this issue, try to use the `await` keyword (when available) or the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="14ffb-201">互換性アナライザーを使用すると、.NET Core で実行時に問題を引き起こす可能性がある Api とコードパターンをコード内で識別できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-201">You can use compatibility analyzers to let you identify APIs and code patterns in your code that can potentially cause problems at run time with .NET Core.</span></span> <span data-ttu-id="14ffb-202">にアクセス <https://github.com/dotnet/platform-compat> し、プロジェクトで .NET API analyzer を使用します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-202">Go to <https://github.com/dotnet/platform-compat> and use the .NET API analyzer on your project.</span></span>

## <a name="migrating-a-windows-forms-application"></a><span data-ttu-id="14ffb-203">Windows フォームアプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="14ffb-203">Migrating a Windows Forms application</span></span>

<span data-ttu-id="14ffb-204">Windows フォームアプリケーションの移行プロセスを完了するには、で入手できる eShop サンプルアプリケーションを移行することを選択しました <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms> 。</span><span class="sxs-lookup"><span data-stu-id="14ffb-204">To showcase a complete migration process of a Windows Forms application, we've chosen to migrate the eShop sample application available at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopLegacyNTier/src/eShopWinForms>.</span></span> <span data-ttu-id="14ffb-205">移行の完全な結果については、「」を参照 <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms> してください。</span><span class="sxs-lookup"><span data-stu-id="14ffb-205">You can find the complete result of the migration at <https://github.com/dotnet-architecture/eShopModernizing/tree/master/eShopModernizedNTier/src/eShopWinForms>.</span></span>

<span data-ttu-id="14ffb-206">このアプリケーションは、製品カタログを表示し、ユーザーが製品の移動、フィルター処理、および検索を行えるようにします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-206">This application shows a product catalog and allows the user to navigate, filter, and search for products.</span></span> <span data-ttu-id="14ffb-207">アーキテクチャの観点から見ると、アプリは、ファサードとして機能する外部の WCF サービスをバックエンドデータベースに依存しています。</span><span class="sxs-lookup"><span data-stu-id="14ffb-207">From an architecture point of view, the app relies on an external WCF service that serves as a façade to a back-end database.</span></span>

<span data-ttu-id="14ffb-208">メインアプリケーションウィンドウは、次の図のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-208">You can see the main application window in the following picture:</span></span>

![メインアプリケーションウィンドウ](./media/example-migration-core/main-application-window.png)

<span data-ttu-id="14ffb-210">.Csproj プロジェクトファイルを開くと、次のような内容が表示さ *れ* ます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-210">If you open the *.csproj* project file, you can see something like this:</span></span>

![.Csproj ファイルの内容のスクリーンショット](./media/example-migration-core/csproj-file.png)

<span data-ttu-id="14ffb-212">前述のように、.NET Core プロジェクトにはよりコンパクトなスタイルがあり、プロジェクトの構造を新しい .NET Core SDK スタイルに移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-212">As previously mentioned, .NET Core project has a more compact style and you need to migrate the project structure to the new .NET Core SDK style.</span></span>

<span data-ttu-id="14ffb-213">ソリューションエクスプローラーで Windows フォームプロジェクトを右クリックし、[プロジェクトの **アンロード**] [編集] の順に選択し  >  ます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-213">In the Solution Explorer, right click on the Windows Forms project and select **Unload Project** > **Edit**.</span></span>

<span data-ttu-id="14ffb-214">.Csproj ファイルを更新できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="14ffb-214">Now you can update the .csproj file.</span></span> <span data-ttu-id="14ffb-215">コンテンツ全体を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-215">You'll delete the entire content and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWindowsForms>true</UseWindowsForms>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="14ffb-216">プロジェクトを保存して再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-216">Save and reload the project.</span></span> <span data-ttu-id="14ffb-217">これでプロジェクトファイルの更新が完了し、プロジェクトは .NET Core を対象としています。</span><span class="sxs-lookup"><span data-stu-id="14ffb-217">You're now done updating the project file and the project is targeting the .NET Core.</span></span>

<span data-ttu-id="14ffb-218">この時点でプロジェクトをコンパイルすると、WCF クライアントリファレンスに関連するエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-218">If you compile the project at this point, you'll find some errors related to the WCF client reference.</span></span> <span data-ttu-id="14ffb-219">このコードは自動生成されるため、.NET Core を対象とするように再生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-219">Since this code is autogenerated, you must regenerate it to target .NET Core.</span></span>

![Visual Studio でのコンパイルエラーのスクリーンショット](./media/example-migration-core/winforms-compilation-errors.png)

<span data-ttu-id="14ffb-221">*Reference.cs* ファイルを削除し、新しいサービスクライアントを生成します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-221">Delete the *Reference.cs* file and generate a new Service Client.</span></span>

<span data-ttu-id="14ffb-222">**接続済みサービス** を右クリックし、[**接続済みサービスの追加**] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-222">Right-click on **Connected Services** and select the **Add Connected Service** option.</span></span>

![[接続済みサービスの追加] オプションが選択されている接続済みサービスメニューのスクリーンショット](./media/example-migration-core/add-connected-service.png)

<span data-ttu-id="14ffb-224">[接続済みサービス] ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-224">The Connected Services window opens.</span></span> <span data-ttu-id="14ffb-225">[ **MICROSOFT WCF Web サービス** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-225">Select the **Microsoft WCF Web Service** option.</span></span>

![[接続済みサービス] ウィンドウのスクリーンショット](./media/example-migration-core/connected-services-window.png)

<span data-ttu-id="14ffb-227">この例と同じソリューションに WCF サービスがある場合は、サービス URL を指定する代わりに、 **Discover** オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-227">If you have the WCF Service in the same solution as we have in this example, you can select the **Discover** option instead of specifying a service URL.</span></span>

![[WCF Web サービス参照の構成] ウィンドウのスクリーンショット](./media/example-migration-core/configure-wcf-reference.png)

<span data-ttu-id="14ffb-229">サービスが配置されると、このツールはサービスによって実装されている API コントラクトを反映します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-229">Once the service is located, the tool reflects the API contract implemented by the service.</span></span> <span data-ttu-id="14ffb-230">次の図に示すように、名前空間の名前をに変更し `eShopServiceReference` ます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-230">Change the name of the namespace to be `eShopServiceReference` as shown in the following image:</span></span>

![API コントラクトと名前空間が変更されたことを示すスクリーンショット](./media/example-migration-core/api-contract-namespace.png)

<span data-ttu-id="14ffb-232">[ **完了** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-232">Select the **Finish** button.</span></span> <span data-ttu-id="14ffb-233">しばらくすると、生成されたコードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-233">After a while, you'll see the generated code.</span></span>

<span data-ttu-id="14ffb-234">次の3つの自動生成ファイルが表示できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-234">You should see three autogenerated files:</span></span>

1. <span data-ttu-id="14ffb-235">*はじめに*: WCF に関する情報を提供する GitHub へのリンク。</span><span class="sxs-lookup"><span data-stu-id="14ffb-235">*Getting Started*: a link to GitHub to provide some information on WCF.</span></span>
2. <span data-ttu-id="14ffb-236">*ConnectedService.js*: サービスに接続するための構成パラメーター。</span><span class="sxs-lookup"><span data-stu-id="14ffb-236">*ConnectedService.json*: configuration parameters to connect to the service.</span></span>
3. <span data-ttu-id="14ffb-237">*Reference.cs*: 実際の WCF クライアントコード。</span><span class="sxs-lookup"><span data-stu-id="14ffb-237">*Reference.cs*: the actual WCF client code.</span></span>

![自動生成された3つのファイルがある [ソリューションエクスプローラー] ウィンドウのスクリーンショット](./media/example-migration-core/autogenerated-files.png)

<span data-ttu-id="14ffb-239">もう一度コンパイルすると、*ヘルパー* フォルダー内の *.cs* ファイルから発生する多くのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-239">If you compile again, you'll see many errors coming from *.cs* files inside the *Helper* folder.</span></span> <span data-ttu-id="14ffb-240">このフォルダーは .NET Framework バージョンに存在しましたが、古い *.csproj* には含まれていません。</span><span class="sxs-lookup"><span data-stu-id="14ffb-240">This folder was present in the .NET Framework version but not included in the old *.csproj*.</span></span> <span data-ttu-id="14ffb-241">ただし、新しい SDK スタイルのプロジェクトでは、プロジェクトファイルの場所の下にあるすべてのコードファイルが既定で含まれています。</span><span class="sxs-lookup"><span data-stu-id="14ffb-241">But with the new SDK-style project, every code file present underneath the project file location is included by default.</span></span> <span data-ttu-id="14ffb-242">つまり、新しい .NET Core プロジェクトでは、 *ヘルパー* フォルダー内のファイルのコンパイルが試行されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-242">That is, the new .NET Core project tries to compile the files inside the *Helper* folder.</span></span> <span data-ttu-id="14ffb-243">このフォルダーは必須ではないため、安全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-243">Since that folder isn't needed, you can safely delete it.</span></span>

<span data-ttu-id="14ffb-244">プロジェクトを再度コンパイルして実行すると、製品イメージは表示されません。</span><span class="sxs-lookup"><span data-stu-id="14ffb-244">If you compile the project again and execute it, you won't see the product images.</span></span> <span data-ttu-id="14ffb-245">問題は、ファイルへのパスが少し変更されたことです。</span><span class="sxs-lookup"><span data-stu-id="14ffb-245">The problem is that now the path to the files has slightly changed.</span></span> <span data-ttu-id="14ffb-246">この問題を解決するには、パスに別の深さレベルを追加し、ファイル内で次の行を更新する必要があり `CatalogView.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-246">To fix this issue, you need to add another level of depth in the path, updating in the file `CatalogView.cs` the line:</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="14ffb-247">から</span><span class="sxs-lookup"><span data-stu-id="14ffb-247">to</span></span>

```csharp
string image_name = Environment.CurrentDirectory + "\\..\\..\\..\\Assets\\Images\\Catalog\\" + catalogItems.Picturefilename;
```

<span data-ttu-id="14ffb-248">この変更を行った後、アプリケーションが起動され、.NET Core で想定どおりに実行されることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-248">After this change, you can check that the application launches and runs as expected on .NET Core.</span></span>

## <a name="migrating-a-wpf-application"></a><span data-ttu-id="14ffb-249">WPF アプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="14ffb-249">Migrating a WPF application</span></span>

<span data-ttu-id="14ffb-250">サンプルアプリケーションを使用して `Shop.ClassicWPF` 移行を実行します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-250">We'll use the `Shop.ClassicWPF` sample application to perform the migration.</span></span> <span data-ttu-id="14ffb-251">次の図は、移行前のアプリのスクリーンショットを示しています。</span><span class="sxs-lookup"><span data-stu-id="14ffb-251">The following image shows a screenshot of the app before migration:</span></span>

![移行前のサンプルアプリ](./media/example-migration-core/app-before-migration.png)

<span data-ttu-id="14ffb-253">このアプリケーションでは、ローカルの SQL Server Express データベースを使用して、製品カタログ情報を保持します。</span><span class="sxs-lookup"><span data-stu-id="14ffb-253">This application uses a local SQL Server Express database to hold the product catalog information.</span></span> <span data-ttu-id="14ffb-254">このデータベースには、WPF アプリケーションから直接アクセスします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-254">This database is accessed directly from the WPF application.</span></span>

<span data-ttu-id="14ffb-255">最初に、 *.csproj* ファイルを .net Core アプリケーションで使用される新しい SDK スタイルに更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-255">First, you must update the *.csproj* file to the new SDK style used by .NET Core applications.</span></span> <span data-ttu-id="14ffb-256">「Windows フォームの移行」で説明されているのと同じ手順に従います。プロジェクトをアンロードし、 *.csproj* ファイルを開き、内容を更新して、プロジェクトを再読み込みします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-256">You'll follow the same steps described in the Windows Forms migration: you'll unload the project, open the *.csproj* file, update its contents, and reload the project.</span></span>

<span data-ttu-id="14ffb-257">この場合は、 *.csproj* ファイルのすべての内容を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-257">In this case, delete all the content of the *.csproj* file and replace it with the following code:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
    <PropertyGroup>
        <OutputType>WinExe</OutputType>
        <TargetFramework>netcoreapp3.1</TargetFramework>
        <UseWpf>true</UseWpf>
        <GenerateAssemblyInfo>false</GenerateAssemblyInfo>
    </PropertyGroup>
</Project>
```

<span data-ttu-id="14ffb-258">プロジェクトを再読み込みしてコンパイルすると、次のエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-258">If you reload the project and compile it, you'll get the following error:</span></span>

![Visual Studio でのコンパイルエラーのスクリーンショット](./media/example-migration-core/wpf-compilation-error.png)

<span data-ttu-id="14ffb-260">*.Csproj* の内容をすべて削除したため、古いプロジェクトに存在するプロジェクト参照の仕様が失われています。</span><span class="sxs-lookup"><span data-stu-id="14ffb-260">Since you've deleted all the *.csproj* contents, you've lost a project reference specification present in the old project.</span></span> <span data-ttu-id="14ffb-261">次の行を *.csproj* ファイルに追加して、プロジェクト参照を戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="14ffb-261">You just need to add this line to the *.csproj* file to include the project reference back:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\\eShop.SqlProvider\\eShop.SqlProvider.csproj" />
<ItemGroup>
```

<span data-ttu-id="14ffb-262">また、[ **依存関係** ] ノードを右クリックし、[ **プロジェクト参照の追加**] を選択して、Visual Studio が役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-262">You can also let Visual Studio help you by right-clicking on the **Dependencies** node and selecting **Add Project Reference**.</span></span> <span data-ttu-id="14ffb-263">ソリューションからプロジェクトを選択し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="14ffb-263">Select the project from the solution and click **OK**:</span></span>

![[参照マネージャー] ダイアログのスクリーンショット (eShop. SqlProvider プロジェクトが選択されている場合)](./media/example-migration-core/reference-manager.png)

<span data-ttu-id="14ffb-265">見つからないプロジェクト参照を追加すると、アプリケーションは .NET Core で予想どおりにコンパイルおよび実行されます。</span><span class="sxs-lookup"><span data-stu-id="14ffb-265">Once you add the missing project reference, the application compiles and runs as expected on .NET Core.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="14ffb-266">[前へ](windows-migration.md)
>[次へ](deploy-modern-applications.md)</span><span class="sxs-lookup"><span data-stu-id="14ffb-266">[Previous](windows-migration.md)
[Next](deploy-modern-applications.md)</span></span>
