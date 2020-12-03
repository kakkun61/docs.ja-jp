---
title: '破壊的変更: WinForms プロパティによる ArgumentOutOfRangeException のスロー'
description: .NET 5.0 での破壊的変更について学習します。この変更により、一部の Windows フォームのプロパティは、無効な引数の ArgumentOutOfRangeException をスローするようになりました。
ms.date: 06/18/2020
ms.openlocfilehash: 94593047d16304ce401b23993ad4ca173c10812b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759873"
---
# <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="225b7-103">WinForms プロパティによる ArgumentOutOfRangeException のスロー</span><span class="sxs-lookup"><span data-stu-id="225b7-103">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="225b7-104">一部の Windows フォーム プロパティで、無効な引数に対して <xref:System.ArgumentOutOfRangeException> がスローされるようになりました。以前はスローされませんでした。</span><span class="sxs-lookup"><span data-stu-id="225b7-104">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

## <a name="change-description"></a><span data-ttu-id="225b7-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="225b7-105">Change description</span></span>

<span data-ttu-id="225b7-106">以前は、これらのプロパティでは、範囲外の引数が渡されたときに <xref:System.NullReferenceException>、<xref:System.IndexOutOfRangeException>、<xref:System.ArgumentException> などのさまざまな例外がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="225b7-106">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="225b7-107">.NET 5.0 以降、これらのプロパティでは、範囲外の引数が渡されたときに <xref:System.ArgumentOutOfRangeException> がスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="225b7-107">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="225b7-108"><xref:System.ArgumentOutOfRangeException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="225b7-108">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="225b7-109">また、どの引数が無効であるのかが明確に伝えられることで、デバッグ エクスペリエンスも向上します。</span><span class="sxs-lookup"><span data-stu-id="225b7-109">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="225b7-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="225b7-110">Version introduced</span></span>

<span data-ttu-id="225b7-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="225b7-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="225b7-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="225b7-112">Recommended action</span></span>

- <span data-ttu-id="225b7-113">無効な引数を渡さないようにコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="225b7-113">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="225b7-114">必要に応じて、プロパティを設定するときに <xref:System.ArgumentOutOfRangeException> を処理します。</span><span class="sxs-lookup"><span data-stu-id="225b7-114">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="225b7-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="225b7-115">Affected APIs</span></span>

<span data-ttu-id="225b7-116">次の表に、影響を受けるプロパティとパラメーターの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="225b7-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="225b7-117">プロパティ</span><span class="sxs-lookup"><span data-stu-id="225b7-117">Property</span></span> | <span data-ttu-id="225b7-118">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="225b7-118">Parameter name</span></span> | <span data-ttu-id="225b7-119">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="225b7-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="225b7-120">5.0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="225b7-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="225b7-121">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="225b7-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="225b7-122">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="225b7-122">5.0 Preview 6</span></span> |

<!--

### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

### Category

Windows Forms

-->
