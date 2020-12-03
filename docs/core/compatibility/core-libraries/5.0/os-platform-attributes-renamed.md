---
title: 破壊的変更:OSPlatform 属性の名前変更または削除
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。プレビュー バージョンで実装された OS プラットフォームの属性が削除または名前変更されました。
ms.date: 11/01/2020
ms.openlocfilehash: 7e709b84005a7b807e390e12d9f36d8b4f73a9df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759416"
---
# <a name="osplatform-attributes-renamed-or-removed"></a><span data-ttu-id="30440-103">OSPlatform 属性の名前変更または削除</span><span class="sxs-lookup"><span data-stu-id="30440-103">OSPlatform attributes renamed or removed</span></span>

<span data-ttu-id="30440-104">.NET 5.0 Preview 8 で実装された、`MinimumOSPlatformAttribute`、`RemovedInOSPlatformAttribute`、および `ObsoletedInOSPlatformAttribute` 属性が、削除または名前変更されました。</span><span class="sxs-lookup"><span data-stu-id="30440-104">The following attributes that were introduced in .NET 5.0 Preview 8 have been removed or renamed: `MinimumOSPlatformAttribute`, `RemovedInOSPlatformAttribute`, and `ObsoletedInOSPlatformAttribute`.</span></span>

## <a name="change-description"></a><span data-ttu-id="30440-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="30440-105">Change description</span></span>

<span data-ttu-id="30440-106">.NET 5.0 Preview 8 で <xref:System.Runtime.Versioning> 名前空間に次の属性が実装されました。</span><span class="sxs-lookup"><span data-stu-id="30440-106">.NET 5.0 Preview 8 introduced the following attributes in the <xref:System.Runtime.Versioning> namespace:</span></span>

- `MinimumOSPlatformAttribute`
- `RemovedInOSPlatformAttribute`
- `ObsoletedInOSPlatformAttribute`

<span data-ttu-id="30440-107">.NET 5.0 Preview 8 のプロジェクトで、`net5.0-windows` などの[ターゲット フレームワーク モニカー](../../../../standard/frameworks.md)を使用し、.NET 5 の OS 固有のフレーバーをターゲットとしている場合、ビルドでは、アセンブリレベルの `System.Runtime.Versioning.MinimumOSPlatformAttribute` 属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="30440-107">In .NET 5.0 Preview 8, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level `System.Runtime.Versioning.MinimumOSPlatformAttribute` attribute.</span></span>

<span data-ttu-id="30440-108">.NET 5.0 RC1 では、`ObsoletedInOSPlatformAttribute` が削除され、`MinimumOSPlatformAttribute` と `RemovedInOSPlatformAttribute` が次のように名前変更されています。</span><span class="sxs-lookup"><span data-stu-id="30440-108">In .NET 5.0 RC1, the `ObsoletedInOSPlatformAttribute` has been removed, and `MinimumOSPlatformAttribute` and `RemovedInOSPlatformAttribute` have been renamed as follows:</span></span>

| <span data-ttu-id="30440-109">Preview 8 での名前</span><span class="sxs-lookup"><span data-stu-id="30440-109">Preview 8 name</span></span> | <span data-ttu-id="30440-110">RC1 以降での名前</span><span class="sxs-lookup"><span data-stu-id="30440-110">RC1 and later name</span></span> |
| - | - |
| `MinimumOSPlatformAttribute` | <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> |
| `RemovedInOSPlatformAttribute` | <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> |

<span data-ttu-id="30440-111">.NET 5.0 RC1 以降のプロジェクトで、`net5.0-windows` などの[ターゲット フレームワーク モニカー](../../../../standard/frameworks.md)を使用し、.NET 5 の OS 固有のフレーバーをターゲットとしている場合、ビルドでは、アセンブリレベルの <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> 属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="30440-111">In .NET 5.0 RC1 and later, when a project targets an OS-specific flavor of .NET 5 by using a [target framework moniker](../../../../standard/frameworks.md) such as `net5.0-windows`, the build adds an assembly-level <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> attribute.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="30440-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="30440-112">Reason for change</span></span>

<span data-ttu-id="30440-113">.NET 5.0 Preview 8 で API をサポートするプラットフォームの指定に、<xref:System.Runtime.Versioning> に属性が実装されました。</span><span class="sxs-lookup"><span data-stu-id="30440-113">.NET 5.0 Preview 8 introduced attributes in <xref:System.Runtime.Versioning> to specify supported platforms for APIs.</span></span> <span data-ttu-id="30440-114">これらの属性は、プラットフォーム固有の API がそれらの API をサポートしないプラットフォームで使用された場合に、ビルド警告を生成する、[プラットフォーム互換性アナライザー](../../../../core/compatibility/code-analysis.md#ca1416-platform-compatibility)によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="30440-114">The attributes are consumed by the [Platform compatibility analyzer](../../../../core/compatibility/code-analysis.md#ca1416-platform-compatibility) to produce build warnings when platform-specific APIs are consumed on platforms that don't supported those APIs.</span></span>

<span data-ttu-id="30440-115">.NET 5.0 RC1 では、プラットフォーム互換性アナライザーにプラットフォームを除外する機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="30440-115">For .NET 5.0 RC1, an additional feature was added to the platform compatibility analyzer for platform exclusion.</span></span> <span data-ttu-id="30440-116">この機能を使用すると、API を OS プラットフォームで完全にサポートされていないものとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="30440-116">The feature allows APIs to be marked as entirely unsupported on OS platforms.</span></span> <span data-ttu-id="30440-117">この機能では、より適切な名前を使用するなど、属性への変更が求められています。</span><span class="sxs-lookup"><span data-stu-id="30440-117">That feature prompted changes to the attributes, including using more suitable names.</span></span> <span data-ttu-id="30440-118">不要になった `ObsoletedInOSPlatformAttribute` は、削除されています。</span><span class="sxs-lookup"><span data-stu-id="30440-118">The `ObsoletedInOSPlatformAttribute` was removed because it was no longer needed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="30440-119">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="30440-119">Version introduced</span></span>

<span data-ttu-id="30440-120">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="30440-120">5.0 RC1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="30440-121">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="30440-121">Recommended action</span></span>

<span data-ttu-id="30440-122">プロジェクトのターゲットを .NET 5.0 Preview 8 から .NET 5.0 RC1 に変更した場合、これらの変更によりビルド エラーまたは実行時エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="30440-122">When you retarget your project from .NET 5.0 Preview 8 to .NET 5.0 RC1, you might encounter build or run-time errors due to these changes.</span></span> <span data-ttu-id="30440-123">たとえば、`MinimumOSPlatformAttribute` を名前変更すると、エラーが発生する可能性があります。これは、この属性がビルド時にプラットフォーム固有のアセンブリに適用されますが、古い成果物では古い API 名を参照したままであるためです。</span><span class="sxs-lookup"><span data-stu-id="30440-123">For example, the renaming of `MinimumOSPlatformAttribute` is likely to produce errors, because the attribute is applied to platform-specific assemblies at build time, and old build artifacts will still reference the old API name.</span></span>

<span data-ttu-id="30440-124">ビルド時のエラーの例:</span><span class="sxs-lookup"><span data-stu-id="30440-124">Example build-time errors:</span></span>

- <span data-ttu-id="30440-125">**エラー CS0246:型または名前空間の名前 'MinimumOSPlatformAttribute' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が指定されていることを確認してください)**</span><span class="sxs-lookup"><span data-stu-id="30440-125">**error CS0246: The type or namespace name 'MinimumOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="30440-126">**エラー CS0246:型または名前空間の名前 'RemovedInOSPlatformAttribute' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が指定されていることを確認してください)**</span><span class="sxs-lookup"><span data-stu-id="30440-126">**error CS0246: The type or namespace name 'RemovedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>
- <span data-ttu-id="30440-127">**エラー CS0246:型または名前空間の名前 'ObsoletedInOSPlatformAttribute' が見つかりませんでした (using ディレクティブまたはアセンブリ参照が指定されていることを確認してください)**</span><span class="sxs-lookup"><span data-stu-id="30440-127">**error CS0246: The type or namespace name 'ObsoletedInOSPlatformAttribute' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="30440-128">ランタイム エラーの例:</span><span class="sxs-lookup"><span data-stu-id="30440-128">Example run-time error:</span></span>

<span data-ttu-id="30440-129">**未処理の例外。System.TypeLoadException:アセンブリから型 'System.Runtime.Versioning.MinimumOSPlatformAttribute' を読み込むことができませんでした 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span><span class="sxs-lookup"><span data-stu-id="30440-129">**Unhandled exception. System.TypeLoadException: Could not load type 'System.Runtime.Versioning.MinimumOSPlatformAttribute' from assembly 'System.Runtime, Version=5.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'.**</span></span>

<span data-ttu-id="30440-130">これらのエラーを解決するには:</span><span class="sxs-lookup"><span data-stu-id="30440-130">To resolve these errors:</span></span>

- <span data-ttu-id="30440-131">`MinimumOSPlatformAttribute` に対する参照を <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute> に更新します。</span><span class="sxs-lookup"><span data-stu-id="30440-131">Update any references of `MinimumOSPlatformAttribute` to <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="30440-132">`RemovedInOSPlatformAttribute` に対する参照を <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute> に更新します。</span><span class="sxs-lookup"><span data-stu-id="30440-132">Update any references of `RemovedInOSPlatformAttribute` to <xref:System.Runtime.Versioning.UnsupportedOSPlatformAttribute>.</span></span>
- <span data-ttu-id="30440-133">`ObsoletedInOSPlatformAttribute` に対する参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="30440-133">Remove any references to `ObsoletedInOSPlatformAttribute`.</span></span>
- <span data-ttu-id="30440-134">古いビルド成果物を削除して、自分のプロジェクトをリビルドします (またはクリーンおよびビルドを実行します)。</span><span class="sxs-lookup"><span data-stu-id="30440-134">Rebuild your project (or perform clean + build) to delete old build artifacts.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="30440-135">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="30440-135">Affected APIs</span></span>

- `System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `System.Runtime.Versioning.RemovedInOSPlatformAttribute`

<!--

### Category

Core .NET libraries

### Affected APIs

- `T:System.Runtime.Versioning.MinimumOSPlatformAttribute`
- `T:System.Runtime.Versioning.ObsoletedInOSPlatformAttribute`
- `T:System.Runtime.Versioning.RemovedInOSPlatformAttribute`

-->
