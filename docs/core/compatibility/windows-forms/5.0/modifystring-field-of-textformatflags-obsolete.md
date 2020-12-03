---
title: 破壊的変更:TextFormatFlags.ModifyString は古くなっています
description: .NET 5.0 の破壊的変更について学習します。この変更により、TextFormatFlags.ModifyString は警告として古いものとなります。
ms.date: 11/05/2020
ms.openlocfilehash: 83dca65a770ccdcd5ce48bb669f5122dc2d5ad77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759376"
---
# <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="29c01-103">TextFormatFlags.ModifyString は古くなっています</span><span class="sxs-lookup"><span data-stu-id="29c01-103">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="29c01-104"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> フィールドには警告として非推奨マークが付いています。今後の .NET バージョンで削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="29c01-104">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

## <a name="change-description"></a><span data-ttu-id="29c01-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="29c01-105">Change description</span></span>

<span data-ttu-id="29c01-106">以前のバージョンの .NET では、<xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> 列挙フィールドは非推奨になっていません。</span><span class="sxs-lookup"><span data-stu-id="29c01-106">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="29c01-107">.NET 5.0 以降のバージョンでは、警告として非推奨マークが付いています。</span><span class="sxs-lookup"><span data-stu-id="29c01-107">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="29c01-108">このフィールドは今後の .NET バージョンで削除される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="29c01-108">This field may be removed in a future .NET version.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="29c01-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="29c01-109">Reason for change</span></span>

<span data-ttu-id="29c01-110"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> で <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> に文字列を渡すと、その文字列が変化することがあります。</span><span class="sxs-lookup"><span data-stu-id="29c01-110">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="29c01-111">この動作は文字列の不変性という約束事を破るものであり、.NET ランタイムが致命的に破損するおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="29c01-111">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="29c01-112">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="29c01-112">Version introduced</span></span>

<span data-ttu-id="29c01-113">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="29c01-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="29c01-114">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="29c01-114">Recommended action</span></span>

<span data-ttu-id="29c01-115"><xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> に依存するコードがあれば、それを更新します。</span><span class="sxs-lookup"><span data-stu-id="29c01-115">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="29c01-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="29c01-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

### Category

Windows Forms

-->
