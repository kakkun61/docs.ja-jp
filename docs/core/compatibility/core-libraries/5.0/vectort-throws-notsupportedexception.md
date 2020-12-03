---
title: 破壊的変更:Vector<T> が NotSupportedException をスローする
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。Vector<T> によって、サポートされていない型パラメーターに対して常に例外がスローされます。
ms.date: 11/01/2020
ms.openlocfilehash: 63db7c6b720735b180ed11098227b31a14008f74
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759770"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a><span data-ttu-id="d9995-103">Vector\<T> で、サポートされていない型に対して常に NotSupportedException がスローされる</span><span class="sxs-lookup"><span data-stu-id="d9995-103">Vector\<T> always throws NotSupportedException for unsupported types</span></span>

<span data-ttu-id="d9995-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> では、サポートされていない型パラメーターに対して常に <xref:System.NotSupportedException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d9995-104"><xref:System.Numerics.Vector%601?displayProperty=nameWithType> now always throws a <xref:System.NotSupportedException> for unsupported type parameters.</span></span>

## <a name="change-description"></a><span data-ttu-id="d9995-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="d9995-105">Change description</span></span>

<span data-ttu-id="d9995-106">以前の <xref:System.Numerics.Vector%601> のメンバーでは、`T` が [サポートされていない型](#unsupported-types)だった場合に、常に <xref:System.NotSupportedException> がスローされるとは限りませんでした。</span><span class="sxs-lookup"><span data-stu-id="d9995-106">Previously, members of <xref:System.Numerics.Vector%601> would not always throw a <xref:System.NotSupportedException> when `T` was an [unsupported type](#unsupported-types).</span></span> <span data-ttu-id="d9995-107">例外が常にスローされなかったのは、ハードウェアの高速化をサポートしていたコード パスが原因でした。</span><span class="sxs-lookup"><span data-stu-id="d9995-107">The exception wasn't always thrown because of code paths that supported hardware acceleration.</span></span> <span data-ttu-id="d9995-108">たとえば、ハードウェアの高速化がないプラットフォーム (ARM32 など) で `Vector<bool> + Vector<bool>` を使用すると、例外をスローするのではなく `default` が返されました。</span><span class="sxs-lookup"><span data-stu-id="d9995-108">For example, `Vector<bool> + Vector<bool>` returned `default` instead of throwing an exception on platforms that have no hardware acceleration, such as ARM32.</span></span> <span data-ttu-id="d9995-109">サポートされていない型について、<xref:System.Numerics.Vector%601> のメンバーが示す動作には、異なるプラットフォームやハードウェア構成にわたる一貫性がありませんでした。</span><span class="sxs-lookup"><span data-stu-id="d9995-109">For unsupported types, <xref:System.Numerics.Vector%601> members exhibited inconsistent behavior across different platforms and hardware configurations.</span></span>

<span data-ttu-id="d9995-110">.NET 5.0 以降、<xref:System.Numerics.Vector%601> のメンバーでは、`T` がサポートされていない型である場合に、すべてのハードウェア構成で常に <xref:System.NotSupportedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d9995-110">Starting in .NET 5.0, <xref:System.Numerics.Vector%601> members always throw a <xref:System.NotSupportedException> on all hardware configurations when `T` is not a supported type.</span></span>

### <a name="unsupported-types"></a><span data-ttu-id="d9995-111">サポートされていない型</span><span class="sxs-lookup"><span data-stu-id="d9995-111">Unsupported types</span></span>

<span data-ttu-id="d9995-112"><xref:System.Numerics.Vector%601> の型パラメーターでサポートされている型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d9995-112">The supported types for the type parameter of <xref:System.Numerics.Vector%601> are:</span></span>

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

<span data-ttu-id="d9995-113">サポートされている型は変更されていませんが、将来変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d9995-113">The supported types have not changed, however, they may change in the future.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d9995-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="d9995-114">Version introduced</span></span>

<span data-ttu-id="d9995-115">5.0</span><span class="sxs-lookup"><span data-stu-id="d9995-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d9995-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="d9995-116">Recommended action</span></span>

<span data-ttu-id="d9995-117"><xref:System.Numerics.Vector%601> の型パラメーターにサポートされていない型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="d9995-117">Don't use an unsupported type for the type parameter of <xref:System.Numerics.Vector%601>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d9995-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="d9995-118">Affected APIs</span></span>

- <span data-ttu-id="d9995-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> およびそのすべてのメンバー</span><span class="sxs-lookup"><span data-stu-id="d9995-119"><xref:System.Numerics.Vector%601?displayProperty=fullName> and all its members</span></span>

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
