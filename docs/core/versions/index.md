---
title: .NET ランタイムおよび SDK のバージョン管理の方法
description: この記事では、.NET SDK とランタイムがどのようにバージョン管理されているかについて説明します (セマンティック バージョニングと似ています)。
ms.date: 12/07/2020
ms.openlocfilehash: 2fe0b162b52f1e4500ec87f7d5d92054cd569552
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009307"
---
# <a name="overview-of-how-net-is-versioned"></a><span data-ttu-id="ee994-103">.NET のバージョン管理の方法の概要</span><span class="sxs-lookup"><span data-stu-id="ee994-103">Overview of how .NET is versioned</span></span>

<span data-ttu-id="ee994-104">[.NET ランタイムと .NET SDK](../introduction.md#sdk-and-runtimes) では、新しい機能が追加される頻度が異なります。</span><span class="sxs-lookup"><span data-stu-id="ee994-104">The [.NET Runtime and the .NET SDK](../introduction.md#sdk-and-runtimes) add new features at different frequencies.</span></span> <span data-ttu-id="ee994-105">一般には、ランタイムよりも SDK の方がより頻繁に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-105">In general, the SDK is updated more frequently than the Runtime.</span></span> <span data-ttu-id="ee994-106">この記事では、ランタイムと SDK のバージョン番号について説明します。</span><span class="sxs-lookup"><span data-stu-id="ee994-106">This article explains the runtime and the SDK version numbers.</span></span>

## <a name="versioning-details"></a><span data-ttu-id="ee994-107">バージョン管理の詳細</span><span class="sxs-lookup"><span data-stu-id="ee994-107">Versioning details</span></span>

<span data-ttu-id="ee994-108">.NET ランタイムでは、[セマンティック バージョニング](#semantic-versioning)に従い、メジャー、マイナーおよびパッチを使用してバージョン管理を行っています。</span><span class="sxs-lookup"><span data-stu-id="ee994-108">The .NET Runtime has a major/minor/patch approach to versioning that follows [semantic versioning](#semantic-versioning).</span></span>

<span data-ttu-id="ee994-109">.NET SDK は、セマンティックバージョニングには従っていません。</span><span class="sxs-lookup"><span data-stu-id="ee994-109">The .NET SDK doesn't follow semantic versioning.</span></span> <span data-ttu-id="ee994-110">.NET SDK の方が速くリリースされ、そのバージョン番号では、それと連携しているランタイムとその SDK 自体のマイナーおよびパッチ リリースの両方が示されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ee994-110">The .NET SDK releases faster and its version numbers must communicate both the aligned runtime and the SDK's own minor and patch releases.</span></span>

<span data-ttu-id="ee994-111">.NET SDK のバージョン番号の 1 番目と 2 番目の位置は、一緒にリリースされる .NET ランタイムと固定されています。</span><span class="sxs-lookup"><span data-stu-id="ee994-111">The first two positions of the .NET SDK version number are locked to the .NET Runtime it released with.</span></span> <span data-ttu-id="ee994-112">SDK の各バージョンでは、このランタイムまたはより低いバージョンに対するアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ee994-112">Each version of the SDK can create applications for this runtime or any lower version.</span></span>

<span data-ttu-id="ee994-113">SDK バージョン番号の 3 番目の位置には、マイナー番号とパッチ番号の両方が示されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-113">The third position of the SDK version number communicates both the minor and patch number.</span></span> <span data-ttu-id="ee994-114">マイナー バージョンには 100 が乗算されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-114">The minor version is multiplied by 100.</span></span> <span data-ttu-id="ee994-115">マイナー バージョン 1、パッチ バージョン 2 の場合は、102 と表現されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-115">Minor version 1, patch version 2 would be represented as 102.</span></span> <span data-ttu-id="ee994-116">最後の 2 桁はパッチの番号を示しています。</span><span class="sxs-lookup"><span data-stu-id="ee994-116">The final two digits represent the patch number.</span></span> <span data-ttu-id="ee994-117">たとえば、ランタイムと SDK のバージョン番号の順番としては、次が可能です。</span><span class="sxs-lookup"><span data-stu-id="ee994-117">For example, here's a possible sequence of runtime and SDK version numbers:</span></span>

| <span data-ttu-id="ee994-118">Change</span><span class="sxs-lookup"><span data-stu-id="ee994-118">Change</span></span>                | <span data-ttu-id="ee994-119">.NET ランタイム</span><span class="sxs-lookup"><span data-stu-id="ee994-119">.NET Runtime</span></span>      | <span data-ttu-id="ee994-120">.NET SDK (\*)</span><span class="sxs-lookup"><span data-stu-id="ee994-120">.NET SDK (\*)</span></span>     |
|-----------------------|-------------------|-------------------|
| <span data-ttu-id="ee994-121">初期リリース</span><span class="sxs-lookup"><span data-stu-id="ee994-121">Initial release</span></span>       | <span data-ttu-id="ee994-122">2.2.0</span><span class="sxs-lookup"><span data-stu-id="ee994-122">2.2.0</span></span>             | <span data-ttu-id="ee994-123">2.2.100</span><span class="sxs-lookup"><span data-stu-id="ee994-123">2.2.100</span></span>           |
| <span data-ttu-id="ee994-124">SDK パッチ</span><span class="sxs-lookup"><span data-stu-id="ee994-124">SDK Patch</span></span>             | <span data-ttu-id="ee994-125">2.2.0</span><span class="sxs-lookup"><span data-stu-id="ee994-125">2.2.0</span></span>             | <span data-ttu-id="ee994-126">2.2.101</span><span class="sxs-lookup"><span data-stu-id="ee994-126">2.2.101</span></span>           |
| <span data-ttu-id="ee994-127">ランタイムおよび SDK パッチ</span><span class="sxs-lookup"><span data-stu-id="ee994-127">Runtime and SDK Patch</span></span> | <span data-ttu-id="ee994-128">2.2.1</span><span class="sxs-lookup"><span data-stu-id="ee994-128">2.2.1</span></span>             | <span data-ttu-id="ee994-129">2.2.102</span><span class="sxs-lookup"><span data-stu-id="ee994-129">2.2.102</span></span>           |
| <span data-ttu-id="ee994-130">SDK 機能変更</span><span class="sxs-lookup"><span data-stu-id="ee994-130">SDK Feature change</span></span>    | <span data-ttu-id="ee994-131">2.2.1</span><span class="sxs-lookup"><span data-stu-id="ee994-131">2.2.1</span></span>             | <span data-ttu-id="ee994-132">2.2.200</span><span class="sxs-lookup"><span data-stu-id="ee994-132">2.2.200</span></span>           |

<span data-ttu-id="ee994-133">注:</span><span class="sxs-lookup"><span data-stu-id="ee994-133">NOTES:</span></span>

- <span data-ttu-id="ee994-134">SDK において、ランタイムの機能更新プログラムの前に 10 の機能更新プログラムがある場合、バージョン番号は 1000 シリーズに展開され、番号は 2.2.1000 のようになります。これは 2.2.900 に続く機能リリースを示しています。</span><span class="sxs-lookup"><span data-stu-id="ee994-134">If the SDK has 10 feature updates before a runtime feature update, version numbers roll into the 1000 series with numbers like 2.2.1000 as the feature release following 2.2.900.</span></span> <span data-ttu-id="ee994-135">このような状況が発生することは想定されていません。</span><span class="sxs-lookup"><span data-stu-id="ee994-135">This situation isn't expected to occur.</span></span>
- <span data-ttu-id="ee994-136">機能リリースなしで 99 のパッチ リリースは、発生しません。</span><span class="sxs-lookup"><span data-stu-id="ee994-136">99 patch releases without a feature release won't occur.</span></span> <span data-ttu-id="ee994-137">リリースがこの数に近づくと、機能リリースが強制的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-137">If a release approaches this number, it forces a feature release.</span></span>

<span data-ttu-id="ee994-138">詳細については、[dotnet/designs](https://github.com/dotnet/designs/pull/29) リポジトリにある初期の提案を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee994-138">You can see more details in the initial proposal at the [dotnet/designs](https://github.com/dotnet/designs/pull/29) repository.</span></span>

## <a name="semantic-versioning"></a><span data-ttu-id="ee994-139">セマンティック バージョン管理</span><span class="sxs-lookup"><span data-stu-id="ee994-139">Semantic versioning</span></span>

<span data-ttu-id="ee994-140">.NET *ランタイム* は、[セマンティック バージョニング (SemVer)](https://semver.org/) にほぼ準拠しています。`MAJOR.MINOR.PATCH` バージョン管理の使用が採用され、バージョン番号のさまざまな部分を使用してどの程度のどのような種類の変更があったかが示されています。</span><span class="sxs-lookup"><span data-stu-id="ee994-140">The .NET *Runtime* roughly adheres to [Semantic Versioning (SemVer)](https://semver.org/), adopting the use of `MAJOR.MINOR.PATCH` versioning, using the various parts of the version number to describe the degree and type of change.</span></span>

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

<span data-ttu-id="ee994-141">省略可能な `PRERELEASE` と `BUILDNUMBER` の部分はサポートされるリリースに含まれることはなく、ソース ターゲットからローカルでビルドされた夜間のビルドおよびサポートされていないプレビュー リリースにのみ存在します。</span><span class="sxs-lookup"><span data-stu-id="ee994-141">The optional `PRERELEASE` and `BUILDNUMBER` parts are never part of supported releases and only exist on nightly builds, local builds from source targets, and unsupported preview releases.</span></span>

### <a name="understand-runtime-version-number-changes"></a><span data-ttu-id="ee994-142">ランタイム バージョン番号の変更を理解する</span><span class="sxs-lookup"><span data-stu-id="ee994-142">Understand runtime version number changes</span></span>

<span data-ttu-id="ee994-143">`MAJOR` は次のときに増分されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-143">`MAJOR` is incremented when:</span></span>

- <span data-ttu-id="ee994-144">製品に重大な変更が加えられた。または製品の方向性が新しくなった。</span><span class="sxs-lookup"><span data-stu-id="ee994-144">Significant changes occur to the product, or a new product direction.</span></span>
- <span data-ttu-id="ee994-145">互換性に影響する変更が行われた。</span><span class="sxs-lookup"><span data-stu-id="ee994-145">Breaking changes were taken.</span></span> <span data-ttu-id="ee994-146">互換性に影響する変更の受け入れには大きな制約があります。</span><span class="sxs-lookup"><span data-stu-id="ee994-146">There's a high bar to accepting breaking changes.</span></span>
- <span data-ttu-id="ee994-147">古いバージョンがサポート対象から除外された。</span><span class="sxs-lookup"><span data-stu-id="ee994-147">An old version is no longer supported.</span></span>
- <span data-ttu-id="ee994-148">既存の依存関係の新しい `MAJOR` バージョンが採用された。</span><span class="sxs-lookup"><span data-stu-id="ee994-148">A newer `MAJOR` version of an existing dependency is adopted.</span></span>

<span data-ttu-id="ee994-149">`MINOR` は次のときに増分されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-149">`MINOR` is incremented when:</span></span>

- <span data-ttu-id="ee994-150">パブリック API アクセス領域が追加された。</span><span class="sxs-lookup"><span data-stu-id="ee994-150">Public API surface area is added.</span></span>
- <span data-ttu-id="ee994-151">新しい動作が追加された。</span><span class="sxs-lookup"><span data-stu-id="ee994-151">A new behavior is added.</span></span>
- <span data-ttu-id="ee994-152">既存の依存関係の新しい `MINOR` バージョンが採用された。</span><span class="sxs-lookup"><span data-stu-id="ee994-152">A newer `MINOR` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="ee994-153">新しい依存関係が導入された。</span><span class="sxs-lookup"><span data-stu-id="ee994-153">A new dependency is introduced.</span></span>

<span data-ttu-id="ee994-154">`PATCH` は次のときに増分されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-154">`PATCH` is incremented when:</span></span>

- <span data-ttu-id="ee994-155">バグの修正が行われた。</span><span class="sxs-lookup"><span data-stu-id="ee994-155">Bug fixes are made.</span></span>
- <span data-ttu-id="ee994-156">より新しいプラットフォームのサポートが追加された。</span><span class="sxs-lookup"><span data-stu-id="ee994-156">Support for a newer platform is added.</span></span>
- <span data-ttu-id="ee994-157">既存の依存関係の新しい `PATCH` バージョンが採用された。</span><span class="sxs-lookup"><span data-stu-id="ee994-157">A newer `PATCH` version of an existing dependency is adopted.</span></span>
- <span data-ttu-id="ee994-158">前のケースのいずれかに一致しない他の変更。</span><span class="sxs-lookup"><span data-stu-id="ee994-158">Any other change doesn't fit one of the previous cases.</span></span>

<span data-ttu-id="ee994-159">複数の変更が存在する場合、個々の変更によって影響を受ける最高位置の要素が増分され、それに続く要素はゼロにリセットされます。</span><span class="sxs-lookup"><span data-stu-id="ee994-159">When there are multiple changes, the highest element affected by individual changes is incremented, and the following ones are reset to zero.</span></span> <span data-ttu-id="ee994-160">たとえば、`MAJOR` が増分され、`MINOR` と `PATCH` はゼロにリセットされます。</span><span class="sxs-lookup"><span data-stu-id="ee994-160">For example, when `MAJOR` is incremented, `MINOR` and `PATCH` are reset to zero.</span></span> <span data-ttu-id="ee994-161">`MINOR` が増分されるときには、`PATCH` はゼロにリセットされますが、`MAJOR` は変更されません。</span><span class="sxs-lookup"><span data-stu-id="ee994-161">When `MINOR` is incremented, `PATCH` is reset to zero while `MAJOR` is left untouched.</span></span>

## <a name="version-numbers-in-file-names"></a><span data-ttu-id="ee994-162">ファイル名に含まれるバージョン番号</span><span class="sxs-lookup"><span data-stu-id="ee994-162">Version numbers in file names</span></span>

<span data-ttu-id="ee994-163">.NET 用にダウンロードされるファイルは、たとえば、`dotnet-sdk-2.1.300-win10-x64.exe` のようにバージョンを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="ee994-163">The files downloaded for .NET carry the version, for example, `dotnet-sdk-2.1.300-win10-x64.exe`.</span></span>

### <a name="preview-versions"></a><span data-ttu-id="ee994-164">プレビュー バージョン</span><span class="sxs-lookup"><span data-stu-id="ee994-164">Preview versions</span></span>

<span data-ttu-id="ee994-165">プレビュー バージョンには、`-preview[number]-([build]|"final")` がバージョン番号に追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-165">Preview versions have a `-preview[number]-([build]|"final")` appended to the version number.</span></span> <span data-ttu-id="ee994-166">たとえば、`2.0.0-preview1-final` のようにします。</span><span class="sxs-lookup"><span data-stu-id="ee994-166">For example, `2.0.0-preview1-final`.</span></span>

### <a name="servicing-versions"></a><span data-ttu-id="ee994-167">サービスのバージョン</span><span class="sxs-lookup"><span data-stu-id="ee994-167">Servicing versions</span></span>

<span data-ttu-id="ee994-168">リリースされると、通常はリリース ブランチが毎日のビルドの生成を停止し、代わりにサービスのビルドの生成を開始します。</span><span class="sxs-lookup"><span data-stu-id="ee994-168">After a release goes out, the release branches generally stop producing daily builds and instead start producing servicing builds.</span></span> <span data-ttu-id="ee994-169">サービスのバージョンには、`-servicing-[number]` がバージョンに追加されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-169">Servicing versions have a `-servicing-[number]` appended to the version.</span></span> <span data-ttu-id="ee994-170">たとえば、`2.0.1-servicing-006924` のようにします。</span><span class="sxs-lookup"><span data-stu-id="ee994-170">For example, `2.0.1-servicing-006924`.</span></span>

## <a name="relationship-to-net-standard-versions"></a><span data-ttu-id="ee994-171">.NET Standard との関係</span><span class="sxs-lookup"><span data-stu-id="ee994-171">Relationship to .NET Standard versions</span></span>

<span data-ttu-id="ee994-172">.NET Standard は、.NET 参照アセンブリで構成されています。</span><span class="sxs-lookup"><span data-stu-id="ee994-172">.NET Standard consists of a .NET reference assembly.</span></span> <span data-ttu-id="ee994-173">各プラットフォームに固有の複数の実装があります。</span><span class="sxs-lookup"><span data-stu-id="ee994-173">There are multiple implementations specific to each platform.</span></span> <span data-ttu-id="ee994-174">参照アセンブリには、指定された .NET Standard バージョンの一部である .NET API の定義が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ee994-174">The reference assembly contains the definition of .NET APIs which are part of a given .NET Standard version.</span></span> <span data-ttu-id="ee994-175">各実装では、特定のプラットフォームに対する .NET Standard コントラクトが満たされます。</span><span class="sxs-lookup"><span data-stu-id="ee994-175">Each implementation fulfills the .NET Standard contract on the specific platform.</span></span>

<span data-ttu-id="ee994-176">.NET Standard 参照アセンブリでは、`MAJOR.MINOR` バージョン管理スキームが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ee994-176">The .NET Standard reference assembly uses a `MAJOR.MINOR` versioning scheme.</span></span> <span data-ttu-id="ee994-177">.NET Standard の場合、`PATCH` レベルは有用ではありません。 .NET Standard では、API 仕様しか公開されず (実装は対象外)、定義上、API に対する変更はいずれも機能セット内の変更を示すものであり、`MINOR` バージョンとなるためです。</span><span class="sxs-lookup"><span data-stu-id="ee994-177">`PATCH` level isn't useful for .NET Standard because it exposes only an API specification (no implementation) and by definition any change to the API would represent a change in the feature set, and thus a new `MINOR` version.</span></span>

<span data-ttu-id="ee994-178">各プラットフォーム上の実装の場合は、通常、プラットフォーム リリースの一部として更新されるので、そのプラットフォーム上で .NET Standard を使用しているプログラマには明らかにされません。</span><span class="sxs-lookup"><span data-stu-id="ee994-178">The implementations on each platform may be updated, typically as part of the platform release, and thus not evident to the programmers using .NET Standard on that platform.</span></span>

<span data-ttu-id="ee994-179">詳細については、「[.NET Standard](../../standard/net-standard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ee994-179">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee994-180">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee994-180">See also</span></span>

- [<span data-ttu-id="ee994-181">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="ee994-181">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ee994-182">.NET の配布パッケージ</span><span class="sxs-lookup"><span data-stu-id="ee994-182">.NET distribution packaging</span></span>](../distribution-packaging.md)
- [<span data-ttu-id="ee994-183">.NET サポート ライフサイクルのファクト シート</span><span class="sxs-lookup"><span data-stu-id="ee994-183">.NET Support Lifecycle Fact Sheet</span></span>](https://dotnet.microsoft.com/platform/support/policy)
- [<span data-ttu-id="ee994-184">.NET の Docker イメージ</span><span class="sxs-lookup"><span data-stu-id="ee994-184">Docker images for .NET</span></span>](https://hub.docker.com/_/microsoft-dotnet/)
