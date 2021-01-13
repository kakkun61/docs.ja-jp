---
title: 破壊的変更:TextInfo.ListSeparator 値の変更
description: .NET 5.0 の破壊的変更について説明します。これにより、バージョン 5.0 と 5.0.1 間で TextInfo.ListSeparator の既定値が変更されました。
ms.date: 12/10/2020
ms.openlocfilehash: 720d46c1908bcd70812f575a90f580470dbc7f32
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596393"
---
# <a name="textinfolistseparator-values-changed"></a><span data-ttu-id="f6e39-103">TextInfo.ListSeparator 値の変更</span><span class="sxs-lookup"><span data-stu-id="f6e39-103">TextInfo.ListSeparator values changed</span></span>

<span data-ttu-id="f6e39-104">すべてのオペレーティング システムで、さまざまなカルチャの既定の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値が変更されています。</span><span class="sxs-lookup"><span data-stu-id="f6e39-104">The default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures have changed on all operating systems.</span></span>

## <a name="change-description"></a><span data-ttu-id="f6e39-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="f6e39-105">Change description</span></span>

<span data-ttu-id="f6e39-106">.NET 5.0.0 では、[NLS から ICU ライブラリへの切り替え](icu-globalization-api.md)の一環として、Windows 上のさまざまなカルチャの既定の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値が変更されました。</span><span class="sxs-lookup"><span data-stu-id="f6e39-106">In .NET 5.0.0, as part of the [switch from NLS to ICU libraries](icu-globalization-api.md), the default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures changed on Windows.</span></span> <span data-ttu-id="f6e39-107">International Components for Unicode (ICU) から取得された小数点区切りの値は、<xref:System.Globalization.TextInfo.ListSeparator> 値として使用されていました。</span><span class="sxs-lookup"><span data-stu-id="f6e39-107">Decimal separator values, obtained from International Components for Unicode (ICU), were used as the <xref:System.Globalization.TextInfo.ListSeparator> values.</span></span> <span data-ttu-id="f6e39-108">Linux と macOS 上では、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値に変更はありませんでした。つまり、小数点区切りの値は引き続き使用されました。</span><span class="sxs-lookup"><span data-stu-id="f6e39-108">On Linux and macOS, there was no change in <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values; that is, they continued to use decimal separator values.</span></span>

<span data-ttu-id="f6e39-109">.NET 5.0.1 以降のバージョンのすべてのオペレーティング システムでは、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> の値は NLS から取得される値と同じです。</span><span class="sxs-lookup"><span data-stu-id="f6e39-109">For all operating systems in .NET 5.0.1 and later versions, the values for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> are equivalent to the values that would be obtained from NLS.</span></span> <span data-ttu-id="f6e39-110">Windows の場合、これは、値が .NET Framework および .NET Core 1.0 から 3.1 の値と同じであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f6e39-110">For Windows, this means the values are equivalent to what they were in .NET Framework and .NET Core 1.0 - 3.1.</span></span> <span data-ttu-id="f6e39-111">Linux と macOS の場合、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値は Windows の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値と一致するようになりました。</span><span class="sxs-lookup"><span data-stu-id="f6e39-111">For Linux and macOS, the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values now match the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for Windows.</span></span>

<span data-ttu-id="f6e39-112">次の表は、<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値の変更をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="f6e39-112">The following table summarizes the changes for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

| | <span data-ttu-id="f6e39-113">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6e39-113">.NET Framework</span></span><br/><span data-ttu-id="f6e39-114">.NET Core 1.0 から 3.1</span><span class="sxs-lookup"><span data-stu-id="f6e39-114">.NET Core 1.0 - 3.1</span></span> | <span data-ttu-id="f6e39-115">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f6e39-115">.NET 5.0</span></span> | <span data-ttu-id="f6e39-116">.NET 5.0.1</span><span class="sxs-lookup"><span data-stu-id="f6e39-116">.NET 5.0.1</span></span> |
-|-|-|-
| <span data-ttu-id="f6e39-117">**Windows**</span><span class="sxs-lookup"><span data-stu-id="f6e39-117">**Windows**</span></span> | <span data-ttu-id="f6e39-118">NLS から取得されます</span><span class="sxs-lookup"><span data-stu-id="f6e39-118">Obtain from NLS</span></span> | <span data-ttu-id="f6e39-119">ICU の小数点区切り。</span><span class="sxs-lookup"><span data-stu-id="f6e39-119">Decimal separator from ICU.</span></span><br/><span data-ttu-id="f6e39-120">NLS に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="f6e39-120">Can switch back to NLS.</span></span> | <span data-ttu-id="f6e39-121">NLS と同じです</span><span class="sxs-lookup"><span data-stu-id="f6e39-121">Equivalent to NLS</span></span> |
| <span data-ttu-id="f6e39-122">**Linux と macOS**</span><span class="sxs-lookup"><span data-stu-id="f6e39-122">**Linux and macOS**</span></span> | <span data-ttu-id="f6e39-123">ICU の小数点区切り</span><span class="sxs-lookup"><span data-stu-id="f6e39-123">Decimal separator from ICU</span></span> | <span data-ttu-id="f6e39-124">ICU の小数点区切り</span><span class="sxs-lookup"><span data-stu-id="f6e39-124">Decimal separator from ICU</span></span> | <span data-ttu-id="f6e39-125">NLS と同じです</span><span class="sxs-lookup"><span data-stu-id="f6e39-125">Equivalent to NLS</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="f6e39-126">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f6e39-126">Version introduced</span></span>

<span data-ttu-id="f6e39-127">5.0.1</span><span class="sxs-lookup"><span data-stu-id="f6e39-127">5.0.1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f6e39-128">変更理由</span><span class="sxs-lookup"><span data-stu-id="f6e39-128">Reason for change</span></span>

<span data-ttu-id="f6e39-129">コンマ区切り値 (CSV) ファイルを解析するときに <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> プロパティを使用していて、新しい <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値によってその解析が中断された、と開発者から報告されました。</span><span class="sxs-lookup"><span data-stu-id="f6e39-129">Developers reported that they use the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> property when parsing comma-separated value (CSV) files, and the new <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values broke that parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f6e39-130">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f6e39-130">Recommended action</span></span>

<span data-ttu-id="f6e39-131">コードが以前の小数点区切り値に依存している場合は、目的の <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> 値をハードコーディングすることができます。</span><span class="sxs-lookup"><span data-stu-id="f6e39-131">If your code relies on the previous decimal separator values, you can hardcode the desired <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f6e39-132">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f6e39-132">Affected APIs</span></span>

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
