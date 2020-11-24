---
title: '方法: 日付および時刻の値のミリ秒部分を表示する'
description: この記事では、.NET で、書式設定された日付と時刻の文字列に、日付と時刻のミリ秒部分を含める方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DateTime.ToString method
- displaying date and time data
- time [.NET], milliseconds
- dates [.NET], milliseconds
- milliseconds [.NET]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
ms.openlocfilehash: 333b41fe3d4fa68ce26ab5dbd7d5938dda220b9a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822114"
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a><span data-ttu-id="e622d-103">方法: 日付および時刻の値のミリ秒部分を表示する</span><span class="sxs-lookup"><span data-stu-id="e622d-103">How to: Display Milliseconds in Date and Time Values</span></span>
<span data-ttu-id="e622d-104"><xref:System.DateTime.ToString?displayProperty=nameWithType> などの既定の日付および時刻書式指定メソッドは時刻値の時間、分、秒を含めますが、ミリ秒の部分は含めません。</span><span class="sxs-lookup"><span data-stu-id="e622d-104">The default date and time formatting methods, such as <xref:System.DateTime.ToString?displayProperty=nameWithType>, include the hours, minutes, and seconds of a time value but exclude its milliseconds component.</span></span> <span data-ttu-id="e622d-105">ここでは、書式設定された日付および時刻文字列の中にミリ秒部分を含める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e622d-105">This topic shows how to include a date and time's millisecond component in formatted date and time strings.</span></span>  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a><span data-ttu-id="e622d-106">DateTime 値のミリ秒部分を表示するには</span><span class="sxs-lookup"><span data-stu-id="e622d-106">To display the millisecond component of a DateTime value</span></span>  
  
1. <span data-ttu-id="e622d-107">文字列形式の日付を処理している場合には、静的 <xref:System.DateTime> または <xref:System.DateTimeOffset> メソッドを使用して、その日付を<xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> 値または <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="e622d-107">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="e622d-108">時刻のミリ秒部分の文字列表現を抽出するには、日付および時刻の値の <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> メソッドまたは <xref:System.DateTimeOffset.ToString%2A> メソッドを呼び出して、カスタム書式パターン `fff` または `FFF` を単独で、あるいは他のカスタム書式指定子と共に `format` パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="e622d-108">To extract the string representation of a time's millisecond component, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%2A> method, and pass the `fff` or `FFF` custom format pattern either alone or with other custom format specifiers as the `format` parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e622d-109">例</span><span class="sxs-lookup"><span data-stu-id="e622d-109">Example</span></span>  
 <span data-ttu-id="e622d-110">この例では、<xref:System.DateTime> および <xref:System.DateTimeOffset> 値のミリ秒の部分をコンソールに表示します。単独で表示する場合と、より長い日付および時刻文字列に含める場合の両方を示します。</span><span class="sxs-lookup"><span data-stu-id="e622d-110">The example displays the millisecond component of a <xref:System.DateTime> and a <xref:System.DateTimeOffset> value to the console, both alone and included in a longer date and time string.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 <span data-ttu-id="e622d-111">`fff` 書式パターンを使うと、ミリ秒値に後続のゼロがあればこれは含められます。</span><span class="sxs-lookup"><span data-stu-id="e622d-111">The `fff` format pattern includes any trailing zeros in the millisecond value.</span></span> <span data-ttu-id="e622d-112">`FFF` 書式パターンでは、これが除外されます。</span><span class="sxs-lookup"><span data-stu-id="e622d-112">The `FFF` format pattern suppresses them.</span></span> <span data-ttu-id="e622d-113">この違いを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="e622d-113">The difference is illustrated in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 <span data-ttu-id="e622d-114">日付および時刻のミリ秒部分を含む完全なカスタム書式指定子を定義する場合、アプリケーションの現在のカルチャの時間要素の取り決めに対応しない可能性のあるハードコーディングされた書式を定義するという問題が生じます。</span><span class="sxs-lookup"><span data-stu-id="e622d-114">A problem with defining a complete custom format specifier that includes the millisecond component of a date and time is that it defines a hard-coded format that may not correspond to the arrangement of time elements in the application's current culture.</span></span> <span data-ttu-id="e622d-115">これに代わるより良い方法は、現在のカルチャの <xref:System.Globalization.DateTimeFormatInfo> オブジェクトで定義されているいずれかの日付および時刻表示パターンを取得して、ミリ秒を含むようにそれを修正することです。</span><span class="sxs-lookup"><span data-stu-id="e622d-115">A better alternative is to retrieve one of the date and time display patterns defined by the current culture's <xref:System.Globalization.DateTimeFormatInfo> object and modify it to include milliseconds.</span></span> <span data-ttu-id="e622d-116">この例では、この方法も示されています。</span><span class="sxs-lookup"><span data-stu-id="e622d-116">The example also illustrates this approach.</span></span> <span data-ttu-id="e622d-117">現在のカルチャの完全な日付および時刻パターンを <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> プロパティから取得した後、その秒パターンの後にカスタム パターン `.ffff` を挿入します。</span><span class="sxs-lookup"><span data-stu-id="e622d-117">It retrieves the current culture's full date and time pattern from the <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> property, and then inserts the custom pattern `.ffff` after its seconds pattern.</span></span> <span data-ttu-id="e622d-118">この例では、1 つのメソッド呼び出しでこの操作を実行するために正規表現が使われていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e622d-118">Note that the example uses a regular expression to perform this operation in a single method call.</span></span>  
  
 <span data-ttu-id="e622d-119">また、カスタム書式指定子を使用して、ミリ秒以外の秒の端数を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="e622d-119">You can also use a custom format specifier to display a fractional part of seconds other than milliseconds.</span></span> <span data-ttu-id="e622d-120">たとえば、カスタム書式指定子 `f` または `F` は 1/10 秒を表示し、カスタム書式指定子 `ff` または `FF` は 1/100 秒、カスタム書式指定子 `ffff` または `FFFF` は 1/10000 秒をそれぞれ表示します。</span><span class="sxs-lookup"><span data-stu-id="e622d-120">For example, the `f` or `F` custom format specifier displays tenths of a second, the `ff` or `FF` custom format specifier displays hundredths of a second, and the `ffff` or `FFFF` custom format specifier displays ten thousandths of a second.</span></span> <span data-ttu-id="e622d-121">返される文字列内では、ミリ秒の端数は丸められるのではなく、切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="e622d-121">Fractional parts of a millisecond are truncated instead of rounded in the returned string.</span></span> <span data-ttu-id="e622d-122">次の例では、これらの書式指定子が使用されています。</span><span class="sxs-lookup"><span data-stu-id="e622d-122">These format specifiers are used in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
> <span data-ttu-id="e622d-123">1/10000 秒、1/100000 秒などの非常に小さな端数単位を表示することが可能です。</span><span class="sxs-lookup"><span data-stu-id="e622d-123">It is possible to display very small fractional units of a second, such as ten thousandths of a second or hundred-thousandths of a second.</span></span> <span data-ttu-id="e622d-124">ただし、このような値を表示してもあまり意味がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e622d-124">However, these values may not be meaningful.</span></span> <span data-ttu-id="e622d-125">日付および時刻の値の精度は、システム クロックの分解能に依存します。</span><span class="sxs-lookup"><span data-stu-id="e622d-125">The precision of date and time values depends on the resolution of the system clock.</span></span> <span data-ttu-id="e622d-126">Windows NT 3.5 以降および Windows Vista オペレーティング システムでは、クロックの解像力は約 10-15 ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="e622d-126">On Windows NT 3.5 and later, and Windows Vista operating systems, the clock's resolution is approximately 10-15 milliseconds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e622d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e622d-127">See also</span></span>

- <xref:System.Globalization.DateTimeFormatInfo>
- [<span data-ttu-id="e622d-128">カスタム日時形式文字列</span><span class="sxs-lookup"><span data-stu-id="e622d-128">Custom Date and Time Format Strings</span></span>](custom-date-and-time-format-strings.md)
