---
title: 破壊的変更:WinForms メソッドで ArgumentNullException がスローされるようになった
description: .NET 5.0 での破壊的変更について学習します。一部の Windows フォーム メソッドで、null 引数に対して ArgumentNullException がスローされるようになりました。
ms.date: 09/18/2020
ms.openlocfilehash: 77280827d44b0e58533339a09357d518a0bfe508
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759914"
---
# <a name="winforms-methods-now-throw-argumentnullexception"></a><span data-ttu-id="f5c5c-103">WinForms メソッドで ArgumentNullException がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="f5c5c-103">WinForms methods now throw ArgumentNullException</span></span>

<span data-ttu-id="f5c5c-104">一部の Windows フォーム メソッドで、null 引数について <xref:System.ArgumentNullException> がスローされるようになりました。以前は <xref:System.NullReferenceException> がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-104">Some Windows Forms methods now throw an <xref:System.ArgumentNullException> for null arguments, where previously they threw a <xref:System.NullReferenceException>.</span></span>

## <a name="change-description"></a><span data-ttu-id="f5c5c-105">変更の説明</span><span class="sxs-lookup"><span data-stu-id="f5c5c-105">Change description</span></span>

<span data-ttu-id="f5c5c-106">以前は、null の引数が渡された場合、特定の Windows フォーム メソッドでは <xref:System.NullReferenceException> がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-106">Previously, certain Windows Forms methods threw a <xref:System.NullReferenceException> if passed an argument that was null.</span></span> <span data-ttu-id="f5c5c-107">.NET 5.0 以降、これらのメソッドでは、null 引数に対して <xref:System.ArgumentNullException> が代わりにスローされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-107">Starting in .NET 5.0, these methods now throw an <xref:System.ArgumentNullException> for null arguments, instead.</span></span>

<span data-ttu-id="f5c5c-108"><xref:System.ArgumentNullException> をスローすることは、.NET ランタイムの動作に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-108">Throwing an <xref:System.ArgumentNullException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="f5c5c-109">また、引数が null であることと、どの引数がそうであるのかが明確に伝えられることで、デバッグ エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-109">It also improves the debugging experience by clearly communicating that an argument is null and which argument it is.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="f5c5c-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f5c5c-110">Version introduced</span></span>

<span data-ttu-id="f5c5c-111">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="f5c5c-111">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f5c5c-112">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="f5c5c-112">Recommended action</span></span>

<span data-ttu-id="f5c5c-113">これらのメソッドのいずれかを呼び出す場合、コードでは現在 null 引数について <xref:System.NullReferenceException> をキャッチする場合は、代わりに <xref:System.ArgumentNullException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-113">If you call any of these methods and your code currently catches a <xref:System.NullReferenceException> for null arguments, catch an <xref:System.ArgumentNullException> instead.</span></span> <span data-ttu-id="f5c5c-114">さらに、リストされているメソッドに null 引数が渡されないようにコードを更新することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-114">In addition, consider updating the code to prevent passing null arguments to the listed methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f5c5c-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="f5c5c-115">Affected APIs</span></span>

<span data-ttu-id="f5c5c-116">次の表では、影響を受けるメソッドとパラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="f5c5c-116">The following table lists the affected methods and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="f5c5c-117">メソッド</span><span class="sxs-lookup"><span data-stu-id="f5c5c-117">Method</span></span> | <span data-ttu-id="f5c5c-118">パラメーター名</span><span class="sxs-lookup"><span data-stu-id="f5c5c-118">Parameter name</span></span> | <span data-ttu-id="f5c5c-119">追加されたバージョン</span><span class="sxs-lookup"><span data-stu-id="f5c5c-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.Control.ControlCollection.%23ctor(System.Windows.Forms.Control)> | `owner` | <span data-ttu-id="f5c5c-120">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-120">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=nameWithType> | `item` | <span data-ttu-id="f5c5c-121">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-121">Preview 1</span></span> |
> | <xref:System.Windows.Forms.TableLayoutControlCollection.%23ctor(System.Windows.Forms.TableLayoutPanel)> | `container` | <span data-ttu-id="f5c5c-122">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-122">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="f5c5c-123">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-123">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="f5c5c-124">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-124">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="f5c5c-125">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-125">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="f5c5c-126">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-126">Preview 1</span></span> |
> | <xref:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)?displayProperty=nameWithType> > | `e` | <span data-ttu-id="f5c5c-127">Preview 1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-127">Preview 1</span></span> |
> | <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)?displayProperty=nameWithType> | `dataGridViewCellStyle` | <span data-ttu-id="f5c5c-128">Preview 2</span><span class="sxs-lookup"><span data-stu-id="f5c5c-128">Preview 2</span></span> |
> | <xref:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)?displayProperty=nameWithType> | `data` | <span data-ttu-id="f5c5c-129">Preview 2</span><span class="sxs-lookup"><span data-stu-id="f5c5c-129">Preview 2</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="f5c5c-130">Preview 5</span><span class="sxs-lookup"><span data-stu-id="f5c5c-130">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="f5c5c-131">Preview 5</span><span class="sxs-lookup"><span data-stu-id="f5c5c-131">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListViewGroup.System%23Runtime%23Serialization%23ISerializable%23GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | `info` | <span data-ttu-id="f5c5c-132">Preview 5</span><span class="sxs-lookup"><span data-stu-id="f5c5c-132">Preview 5</span></span> |
> | <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor(System.String,System.Int32,System.Int32)> | `className` | <span data-ttu-id="f5c5c-133">Preview 5</span><span class="sxs-lookup"><span data-stu-id="f5c5c-133">Preview 5</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox)> | `owner` | <span data-ttu-id="f5c5c-134">Preview 6</span><span class="sxs-lookup"><span data-stu-id="f5c5c-134">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Object[])> | <span data-ttu-id="f5c5c-135">`owner`、`value`</span><span class="sxs-lookup"><span data-stu-id="f5c5c-135">`owner`, `value`</span></span> | <span data-ttu-id="f5c5c-136">Preview 6</span><span class="sxs-lookup"><span data-stu-id="f5c5c-136">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.%23ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)> | <span data-ttu-id="f5c5c-137">`owner`、`value`</span><span class="sxs-lookup"><span data-stu-id="f5c5c-137">`owner`, `value`</span></span> | <span data-ttu-id="f5c5c-138">Preview 6</span><span class="sxs-lookup"><span data-stu-id="f5c5c-138">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])?displayProperty=nameWithType> | `items` | <span data-ttu-id="f5c5c-139">Preview 6</span><span class="sxs-lookup"><span data-stu-id="f5c5c-139">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)?displayProperty=nameWithType> | `value` | <span data-ttu-id="f5c5c-140">Preview 6</span><span class="sxs-lookup"><span data-stu-id="f5c5c-140">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="f5c5c-141">Preview 6</span><span class="sxs-lookup"><span data-stu-id="f5c5c-141">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListBox.ObjectCollection.System%23Collections%23ICollection%23CopyTo(System.Array,System.Int32)?displayProperty=nameWithType> | `destination` | <span data-ttu-id="f5c5c-142">Preview 6</span><span class="sxs-lookup"><span data-stu-id="f5c5c-142">Preview 6</span></span> |
> | <xref:System.Windows.Forms.ListView.SelectedIndexCollection.%23ctor(System.Windows.Forms.ListView)> | `owner` | <span data-ttu-id="f5c5c-143">Preview 7</span><span class="sxs-lookup"><span data-stu-id="f5c5c-143">Preview 7</span></span> |
> | <xref:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="f5c5c-144">`key` が `null` または空です</span><span class="sxs-lookup"><span data-stu-id="f5c5c-144">`key` is `null` or empty</span></span> | <span data-ttu-id="f5c5c-145">Preview 8</span><span class="sxs-lookup"><span data-stu-id="f5c5c-145">Preview 8</span></span> |
> | <xref:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="f5c5c-146">`key` が `null` または空です</span><span class="sxs-lookup"><span data-stu-id="f5c5c-146">`key` is `null` or empty</span></span> | <span data-ttu-id="f5c5c-147">RC1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-147">RC1</span></span> |
> | <xref:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)?displayProperty=nameWithType> | `e` | <span data-ttu-id="f5c5c-148">RC1</span><span class="sxs-lookup"><span data-stu-id="f5c5c-148">RC1</span></span> |

<!--

### Affected APIs

- `M:System.Windows.Forms.Control.ControlCollection.#ctor(System.Windows.Forms.Control)`
- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.TableLayoutControlCollection.#ctor(System.Windows.Forms.TableLayoutPanel)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderArrow(System.Windows.Forms.ToolStripArrowRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemImage(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemCheck(System.Windows.Forms.ToolStripItemImageRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderItemText(System.Windows.Forms.ToolStripItemTextRenderEventArgs)`
- `M:System.Windows.Forms.ToolStripRenderer.OnRenderStatusStripSizingGrip(System.Windows.Forms.ToolStripRenderEventArgs)`
- `M:System.Windows.Forms.DataGridViewComboBoxEditingControl.ApplyCellStyleToEditingControl(System.Windows.Forms.DataGridViewCellStyle)`
- `M:System.Windows.Forms.RichTextBox.LoadFile(System.IO.Stream,System.Windows.Forms.RichTextBoxStreamType)`
- `M:System.Windows.Forms.ListViewGroup.System#Runtime#Serialization#ISerializable#GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)`
- `M:System.Windows.Forms.VisualStyles.VisualStyleRenderer.#ctor(System.String,System.Int32,System.Int32)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.IntegerCollection.CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.#ctor(System.Windows.Forms.ListBox,System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Object[])`
- `M:System.Windows.Forms.ListBox.ObjectCollection.AddRange(System.Windows.Forms.ListBox.ObjectCollection)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.CopyTo(System.Object[],System.Int32)`
- `M:System.Windows.Forms.ListBox.ObjectCollection.System#Collections#ICollection#CopyTo(System.Array,System.Int32)`
- `M:System.Windows.Forms.ListView.SelectedIndexCollection.#ctor(System.Windows.Forms.ListView)`
- `M:System.Windows.Forms.TreeNodeCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ListView.ListViewItemCollection.Find(System.String,System.Boolean)`
- `M:System.Windows.Forms.ScrollableControl.OnPaintBackground(System.Windows.Forms.PaintEventArgs)`

### Category

Windows Forms

-->
