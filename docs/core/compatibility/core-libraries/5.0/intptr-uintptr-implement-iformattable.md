---
title: 破壊的変更:IntPtr と UIntPtr の IFormattable 実装
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。IntPtr と UIntPtr で IFormattable が実装されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 0684652cdc2b8cf1d237074263bf0809082b0dcd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759956"
---
# <a name="intptr-and-uintptr-implement-iformattable"></a><span data-ttu-id="44be7-103">IntPtr と UIntPtr の IFormattable 実装</span><span class="sxs-lookup"><span data-stu-id="44be7-103">IntPtr and UIntPtr implement IFormattable</span></span>

<span data-ttu-id="44be7-104"><xref:System.IntPtr> と <xref:System.UIntPtr> で <xref:System.IFormattable> が実装されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="44be7-104"><xref:System.IntPtr> and <xref:System.UIntPtr> now implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="44be7-105">現在、<xref:System.IFormattable> サポートを確認する関数からは、これらの型に対して異なる結果が返されることがあります。書式指定子とカルチャで渡されることがあるためです。</span><span class="sxs-lookup"><span data-stu-id="44be7-105">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

## <a name="change-description"></a><span data-ttu-id="44be7-106">変更の説明</span><span class="sxs-lookup"><span data-stu-id="44be7-106">Change description</span></span>

<span data-ttu-id="44be7-107">以前のバージョンの .NET では、<xref:System.IntPtr> と <xref:System.UIntPtr> では <xref:System.IFormattable> が実装されません。</span><span class="sxs-lookup"><span data-stu-id="44be7-107">In previous versions of .NET, <xref:System.IntPtr> and <xref:System.UIntPtr> do not implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="44be7-108"><xref:System.IFormattable> を確認する関数はフォールバックし、<xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> または <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType> を呼び出すことがあります。つまり、書式指定子とカルチャは無視されます。</span><span class="sxs-lookup"><span data-stu-id="44be7-108">Functions that check for <xref:System.IFormattable> may fall back to just calling <xref:System.IntPtr.ToString%2A?displayProperty=nameWithType> or <xref:System.UIntPtr.ToString%2A?displayProperty=nameWithType>, which means that format specifiers and cultures are not respected.</span></span>

<span data-ttu-id="44be7-109">.NET 5.0 以降のバージョンでは、<xref:System.IntPtr> と <xref:System.UIntPtr> で <xref:System.IFormattable> が実装されます。</span><span class="sxs-lookup"><span data-stu-id="44be7-109">In .NET 5.0 and later versions, <xref:System.IntPtr> and <xref:System.UIntPtr> implement <xref:System.IFormattable>.</span></span> <span data-ttu-id="44be7-110">現在、<xref:System.IFormattable> サポートを確認する関数からは、これらの型に対して異なる結果が返されることがあります。書式指定子とカルチャで渡されることがあるためです。</span><span class="sxs-lookup"><span data-stu-id="44be7-110">Functions that check for <xref:System.IFormattable> support may now return different results for these types, because they may pass in a format specifier and a culture.</span></span>

<span data-ttu-id="44be7-111">この変更は、補間された文字列や <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> などのシナリオに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="44be7-111">This change impacts scenarios like interpolated strings and <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, among others.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="44be7-112">変更理由</span><span class="sxs-lookup"><span data-stu-id="44be7-112">Reason for change</span></span>

<span data-ttu-id="44be7-113"><xref:System.IntPtr> と <xref:System.UIntPtr> は、キーワードの `nint` と `nuint` を介して C# で言語サポートされます。</span><span class="sxs-lookup"><span data-stu-id="44be7-113"><xref:System.IntPtr> and <xref:System.UIntPtr> now have language support in C# through the `nint` and `nuint` keywords.</span></span> <span data-ttu-id="44be7-114">バッキング型は、<xref:System.Int32?displayProperty=nameWithType> など、他のプリミティブ型によって公開される機能により (可能であれば) ほぼ等しくなるように更新されました。</span><span class="sxs-lookup"><span data-stu-id="44be7-114">The backing types were updated to provide near parity (where possible) with functionality exposed by other primitive types, such as <xref:System.Int32?displayProperty=nameWithType>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="44be7-115">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="44be7-115">Version introduced</span></span>

<span data-ttu-id="44be7-116">5.0</span><span class="sxs-lookup"><span data-stu-id="44be7-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="44be7-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="44be7-117">Recommended action</span></span>

<span data-ttu-id="44be7-118">これらの型の値を表示するとき、書式指定子またはカルチャを使用しない場合、`ToString()` のオーバーロードの <xref:System.IntPtr.ToString?displayProperty=nameWithType> と <xref:System.UIntPtr.ToString?displayProperty=nameWithType> を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="44be7-118">If you don't want a format specifier or custom culture to be used when displaying values of these types, you can call the <xref:System.IntPtr.ToString?displayProperty=nameWithType> and <xref:System.UIntPtr.ToString?displayProperty=nameWithType> overloads of `ToString()`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="44be7-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="44be7-119">Affected APIs</span></span>

<span data-ttu-id="44be7-120">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="44be7-120">Not detectable via API analysis.</span></span>

<!--

### Category

Core .NET libraries

### Affected APIs

Not detectable via API analysis.

-->
