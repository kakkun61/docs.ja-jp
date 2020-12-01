---
ms.openlocfilehash: d598d8d3203e804e5e935c3564b0053f9fc2e9a6
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032655"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="f778d-101">共有フレームワーク: Microsoft.AspNetCore.App から削除されたアセンブリ</span><span class="sxs-lookup"><span data-stu-id="f778d-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="f778d-102">ASP.NET Core 3.0 以降、ASP.NET Core 共有フレームワーク (`Microsoft.AspNetCore.App`) には、Microsoft が完全に開発、サポートし、処理可能なファースト パーティのアセンブリだけが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f778d-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f778d-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="f778d-103">Change description</span></span>

<span data-ttu-id="f778d-104">この変更は、ASP.NET Core "プラットフォーム" の境界の再定義と考えてください。</span><span class="sxs-lookup"><span data-stu-id="f778d-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="f778d-105">共有フレームワークは、[GitHub を介して誰でもソース ビルドが可能](https://github.com/dotnet/source-build)になり、.NET Core 共有フレームワークの既存の利点をアプリに引き続き提供します。</span><span class="sxs-lookup"><span data-stu-id="f778d-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="f778d-106">利点として、デプロイのサイズの縮小、修正プログラムの適用の一元化、起動時間の短縮などがあります。</span><span class="sxs-lookup"><span data-stu-id="f778d-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="f778d-107">変更の一貫として、いくつかの注目すべき破壊的変更が `Microsoft.AspNetCore.App` に導入されました。</span><span class="sxs-lookup"><span data-stu-id="f778d-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f778d-108">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f778d-108">Version introduced</span></span>

<span data-ttu-id="f778d-109">3.0</span><span class="sxs-lookup"><span data-stu-id="f778d-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f778d-110">以前の動作</span><span class="sxs-lookup"><span data-stu-id="f778d-110">Old behavior</span></span>

<span data-ttu-id="f778d-111">プロジェクトでは、プロジェクト ファイル内の `<PackageReference>` 要素を介して `Microsoft.AspNetCore.App` を参照していました。</span><span class="sxs-lookup"><span data-stu-id="f778d-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="f778d-112">さらに、`Microsoft.AspNetCore.App` に次のサブコンポーネントが含まれていました。</span><span class="sxs-lookup"><span data-stu-id="f778d-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="f778d-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="f778d-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="f778d-114">Entity Framework Core (`Microsoft.EntityFrameworkCore.` がプレフィックスとして付加されたアセンブリ)</span><span class="sxs-lookup"><span data-stu-id="f778d-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="f778d-115">Roslyn (`Microsoft.CodeAnalysis`)</span><span class="sxs-lookup"><span data-stu-id="f778d-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f778d-116">新しい動作</span><span class="sxs-lookup"><span data-stu-id="f778d-116">New behavior</span></span>

<span data-ttu-id="f778d-117">`Microsoft.AspNetCore.App` への参照に、プロジェクト ファイル内の `<PackageReference>` 要素は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="f778d-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="f778d-118">.NET Core SDK では、`<FrameworkReference>` と呼ばれる新しい要素がサポートされています。これは、`<PackageReference>` に代わって使用されます。</span><span class="sxs-lookup"><span data-stu-id="f778d-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="f778d-119">詳細については、[dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f778d-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="f778d-120">Entity Framework Core は NuGet パッケージとして配布されます。</span><span class="sxs-lookup"><span data-stu-id="f778d-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="f778d-121">この変更により、.NET 上の他のすべてのデータ アクセス ライブラリに合わせて配布モデルが調整されます。</span><span class="sxs-lookup"><span data-stu-id="f778d-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="f778d-122">さまざまな .NET プラットフォームをサポートしながらイノベーションを継続するための最も簡単なパスが Entity Framework Core に提供されます。</span><span class="sxs-lookup"><span data-stu-id="f778d-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="f778d-123">共有フレームワークからの Entity Framework Core の移動は、Microsoft が開発、サポートし、処理可能なライブラリとしての状態には影響しません。</span><span class="sxs-lookup"><span data-stu-id="f778d-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="f778d-124">[.NET Core のサポート ポリシー](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)は、引き続きこれに対応しています。</span><span class="sxs-lookup"><span data-stu-id="f778d-124">The [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continues to cover it.</span></span>

<span data-ttu-id="f778d-125">Json.NET と Entity Framework Core は、ASP.NET Core と引き続き連携します。</span><span class="sxs-lookup"><span data-stu-id="f778d-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="f778d-126">ただし、これらは共有フレームワークには含まれません。</span><span class="sxs-lookup"><span data-stu-id="f778d-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="f778d-127">詳細については、「[The future of JSON in .NET Core 3.0 (.NET Core 3.0 での JSON の未来)](https://github.com/dotnet/announcements/issues/90)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f778d-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="f778d-128">また、共有フレームワークから削除された[バイナリの一覧](https://github.com/dotnet/aspnetcore/issues/3755)もご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f778d-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f778d-129">変更理由</span><span class="sxs-lookup"><span data-stu-id="f778d-129">Reason for change</span></span>

<span data-ttu-id="f778d-130">この変更により、`Microsoft.AspNetCore.App` の使用が簡素化され、NuGet パッケージと共有フレームワーク間の重複が削減されます。</span><span class="sxs-lookup"><span data-stu-id="f778d-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="f778d-131">この変更の目的の詳細については、[こちらのブログ記事](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f778d-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f778d-132">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f778d-132">Recommended action</span></span>

<span data-ttu-id="f778d-133">プロジェクトでは、`Microsoft.AspNetCore.App` のアセンブリを NuGet パッケージとして使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f778d-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="f778d-134">ASP.NET Core 共有フレームワークのターゲット設定と使用を簡素化するために、ASP.NET Core 1.0 以降に配布された多くの NuGet パッケージが生成されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="f778d-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="f778d-135">これらのパッケージで提供される API は、`Microsoft.AspNetCore.App` への `<FrameworkReference>` を使用することで引き続きアプリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f778d-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="f778d-136">一般的な API の例として、Kestrel、MVC、Razor などがあります。</span><span class="sxs-lookup"><span data-stu-id="f778d-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="f778d-137">この変更は、ASP.NET Core 2.x の `Microsoft.AspNetCore.App` を介して参照されるすべてのバイナリに適用されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="f778d-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="f778d-138">重要な例外は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f778d-138">Notable exceptions include:</span></span>

- <span data-ttu-id="f778d-139">.NET Standard を引き続きターゲットとする `Microsoft.Extensions` ライブラリは、NuGet パッケージとして利用できます (<https://github.com/dotnet/extensions> を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="f778d-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see <https://github.com/dotnet/extensions>).</span></span>
- <span data-ttu-id="f778d-140">ASP.NET Core チームによって生成され、`Microsoft.AspNetCore.App` に含まれていない API。</span><span class="sxs-lookup"><span data-stu-id="f778d-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="f778d-141">たとえば、次のコンポーネントは NuGet パッケージとして利用できます。</span><span class="sxs-lookup"><span data-stu-id="f778d-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="f778d-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="f778d-142">Entity Framework Core</span></span>
  - <span data-ttu-id="f778d-143">サード パーティの統合を提供するAPI</span><span class="sxs-lookup"><span data-stu-id="f778d-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="f778d-144">試験的な機能</span><span class="sxs-lookup"><span data-stu-id="f778d-144">Experimental features</span></span>
  - <span data-ttu-id="f778d-145">[共有フレームワークに含めるための要件](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)を満たすことができなかった依存関係を持つ API</span><span class="sxs-lookup"><span data-stu-id="f778d-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="f778d-146">Json.NET のサポートを維持する MVC の拡張機能。</span><span class="sxs-lookup"><span data-stu-id="f778d-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="f778d-147">API は、Json.NET と MVC の使用をサポートする NuGet パッケージとして提供されます。</span><span class="sxs-lookup"><span data-stu-id="f778d-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="f778d-148">SignalR .NET クライアントは、.NET Standard を引き続きサポートし、NuGet パッケージとして配布されます。</span><span class="sxs-lookup"><span data-stu-id="f778d-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="f778d-149">これは、Xamarin や UWP など、多くの .NET ランタイムでの使用を目的としています。</span><span class="sxs-lookup"><span data-stu-id="f778d-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="f778d-150">詳細については、「[Stop producing packages for shared framework assemblies in 3.0 (3.0 における共有フレームワークのアセンブリのパッケージ生成の停止)](https://github.com/dotnet/aspnetcore/issues/3756)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f778d-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="f778d-151">ディスカッションについては、[dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f778d-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="f778d-152">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="f778d-152">Category</span></span>

<span data-ttu-id="f778d-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f778d-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f778d-154">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f778d-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
