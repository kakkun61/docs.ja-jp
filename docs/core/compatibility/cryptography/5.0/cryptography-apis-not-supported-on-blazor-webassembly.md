---
title: 破壊的変更:Blazor WebAssembly で System.Security.Cryptography API がサポートされない
description: .NET 5.0 の破壊的変更について学習します。この変更後、暗号化 API は、ブラウザーで実行されると例外をスローするようになりました。
ms.date: 09/16/2020
ms.openlocfilehash: ec10fa777e91f641b5582378830536a0cfa8dd72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759355"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a><span data-ttu-id="a505a-103">Blazor WebAssembly で System.Security.Cryptography API がサポートされない</span><span class="sxs-lookup"><span data-stu-id="a505a-103">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>

<span data-ttu-id="a505a-104"><xref:System.Security.Cryptography> API は、ブラウザーで実行されると、実行時に <xref:System.PlatformNotSupportedException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="a505a-104"><xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> at run time when run on a browser.</span></span>

## <a name="change-description"></a><span data-ttu-id="a505a-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="a505a-105">Change description</span></span>

<span data-ttu-id="a505a-106">以前のバージョンの .NET では、ほとんどの <xref:System.Security.Cryptography> API が Blazor WebAssembly で使用できません。</span><span class="sxs-lookup"><span data-stu-id="a505a-106">In previous .NET versions, most of the <xref:System.Security.Cryptography> APIs aren't available to Blazor WebAssembly apps.</span></span> <span data-ttu-id="a505a-107">.NET 5.0 以降、Blazor WebAssembly アプリでは .NET 5 API の全アクセス領域が対象になりますが、ブラウザー サンドボックスの制約によりすべての .NET 5 API がサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a505a-107">Starting in .NET 5.0, Blazor WebAssembly apps target the full .NET 5 API surface area, however, not all .NET 5 APIs are supported due to browser sandbox constraints.</span></span> <span data-ttu-id="a505a-108">.NET 5.0 以降のバージョンでは、サポートされていない <xref:System.Security.Cryptography> API を WebAssembly で実行すると <xref:System.PlatformNotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a505a-108">In .NET 5.0 and later versions, the unsupported <xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> when running on WebAssembly.</span></span>

> [!TIP]
> <span data-ttu-id="a505a-109">ブラウザー プラットフォームをサポートするプロジェクトをビルドすると、[プラットフォーム互換性アナライザー](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md)によって、影響を受ける API の呼び出しにフラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="a505a-109">The [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) will flag any calls to the affected APIs when you build a project that supports the browser platform.</span></span> <span data-ttu-id="a505a-110">このアナライザーは、.NET 5.0 以降のアプリでは既定で実行されます。</span><span class="sxs-lookup"><span data-stu-id="a505a-110">This analyzer runs by default in .NET 5.0 and later apps.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a505a-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="a505a-111">Reason for change</span></span>

<span data-ttu-id="a505a-112">Microsoft では、Blazor WebAssembly 構成の依存関係として OpenSSL を公開することができません。</span><span class="sxs-lookup"><span data-stu-id="a505a-112">Microsoft is unable to ship OpenSSL as a dependency in the Blazor WebAssembly configuration.</span></span> <span data-ttu-id="a505a-113">私たちは、ブラウザーの `SubtleCrypto` API と統合することでこれを回避しようとしました。</span><span class="sxs-lookup"><span data-stu-id="a505a-113">We attempted to work around this by trying to integrate with the browser's `SubtleCrypto` API.</span></span> <span data-ttu-id="a505a-114">残念ながら、それには大幅な API の変更が必要であり、統合は困難でした。</span><span class="sxs-lookup"><span data-stu-id="a505a-114">Unfortunately, it required significant API changes that made it too hard to integrate.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a505a-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a505a-115">Version introduced</span></span>

<span data-ttu-id="a505a-116">5.0</span><span class="sxs-lookup"><span data-stu-id="a505a-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a505a-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a505a-117">Recommended action</span></span>

<span data-ttu-id="a505a-118">現時点では、推奨される回避策はありません。</span><span class="sxs-lookup"><span data-stu-id="a505a-118">There are no good workarounds to suggest at this time.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a505a-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a505a-119">Affected APIs</span></span>

<span data-ttu-id="a505a-120">次を除くすべての <xref:System.Security.Cryptography?displayProperty=fullName> API:</span><span class="sxs-lookup"><span data-stu-id="a505a-120">All <xref:System.Security.Cryptography?displayProperty=fullName> APIs except the following:</span></span>

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->
