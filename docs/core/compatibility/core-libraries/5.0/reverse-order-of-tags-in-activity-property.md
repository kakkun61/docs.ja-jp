---
title: 破壊的変更:Activity.Tags 内のタグの順序が逆になっている
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。Activity.Tags では、追加された順に項目がリストに格納されるようになりました。
ms.date: 11/01/2020
ms.openlocfilehash: 1ff14dc1a4f7a0bf8cf9e79f3750b819f4d4a5ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759444"
---
# <a name="order-of-tags-in-activitytags-is-reversed"></a><span data-ttu-id="b0d5c-103">Activity.Tags 内のタグの順序が逆になっている</span><span class="sxs-lookup"><span data-stu-id="b0d5c-103">Order of tags in Activity.Tags is reversed</span></span>

<span data-ttu-id="b0d5c-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> では、追加された順に項目がリストに格納されるようになりました。つまり、最初に追加された項目がリストの先頭になります。</span><span class="sxs-lookup"><span data-stu-id="b0d5c-104"><xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> now stores items in the list according to the order they are added, that is, the first item that's added is first in the list.</span></span> <span data-ttu-id="b0d5c-105">この変更は、[OpenTelemetry Attributes 仕様](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes)と一致させるために行われました。</span><span class="sxs-lookup"><span data-stu-id="b0d5c-105">This change was made to match the [OpenTelemetry Attributes specification](https://github.com/open-telemetry/opentelemetry-specification/blob/master/specification/common/common.md#attributes).</span></span>

## <a name="change-description"></a><span data-ttu-id="b0d5c-106">変更内容</span><span class="sxs-lookup"><span data-stu-id="b0d5c-106">Change description</span></span>

<span data-ttu-id="b0d5c-107">以前のバージョンの .NET では、<xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> により追加されたのと逆の順序で項目が格納されます。</span><span class="sxs-lookup"><span data-stu-id="b0d5c-107">In previous .NET versions, <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> stores items in the reverse order from which they're added.</span></span> <span data-ttu-id="b0d5c-108">つまり、最初に追加された項目がリストの末尾になります。</span><span class="sxs-lookup"><span data-stu-id="b0d5c-108">That is, the first item added is last in the list.</span></span> <span data-ttu-id="b0d5c-109">.NET 5.0 以降では、項目の順序は逆になり、最初に追加された項目が常にリストの先頭になります。</span><span class="sxs-lookup"><span data-stu-id="b0d5c-109">Starting in .NET 5.0, the order of the items is reversed, and the first item added is always first in the list.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b0d5c-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="b0d5c-110">Version introduced</span></span>

<span data-ttu-id="b0d5c-111">5.0</span><span class="sxs-lookup"><span data-stu-id="b0d5c-111">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b0d5c-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="b0d5c-112">Recommended action</span></span>

<span data-ttu-id="b0d5c-113">ご使用のアプリが <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> リストの順序に依存していて、.NET 5.0 以降にアップグレードする場合は、コードのこの部分を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0d5c-113">If your app has a dependency on the <xref:System.Diagnostics.Activity.Tags?displayProperty=nameWithType> list order and you're upgrading to .NET 5.0 or later, you'll need to change this part of your code.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="b0d5c-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b0d5c-114">Affected APIs</span></span>

- <xref:System.Diagnostics.Activity.Tags?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `P:System.Diagnostics.Activity.Tags`

-->
