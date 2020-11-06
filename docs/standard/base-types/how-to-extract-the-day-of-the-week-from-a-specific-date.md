---
title: '方法: 特定の日付から曜日を抽出する'
description: .NET で特定の日付が週の何日目であるかを確認する方法について説明します。 特定の日付のローカライズされた曜日名を表示する方法について説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [.NET], dates
- DateTime.DayOfWeek property
- DateTime.ToString method
- dates [.NET], retrieving week information
- DateTimeOffset.DayOfWeek property
- dates [.NET], day of week
- Weekday function
- day of week [.NET]
- extracting day of week
- weekday names
- WeekdayName function
- numbers [.NET], day of week
- formatting [.NET], time
- DateTimeOffset.ToString method
- full weekday names
ms.assetid: 1c9bef76-5634-46cf-b91c-9b9eb72091d7
ms.openlocfilehash: f7a18a3ab414a07fa4908c67c5ec9334ce63953f
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888522"
---
# <a name="how-to-extract-the-day-of-the-week-from-a-specific-date"></a><span data-ttu-id="16cbb-104">方法: 特定の日付から曜日を抽出する</span><span class="sxs-lookup"><span data-stu-id="16cbb-104">How to: Extract the Day of the Week from a Specific Date</span></span>

<span data-ttu-id="16cbb-105">.NET では、特定の日付が週の何日目であるかを容易に判別でき、また特定の日付のローカライズされた曜日名を表示できます。</span><span class="sxs-lookup"><span data-stu-id="16cbb-105">.NET makes it easy to determine the ordinal day of the week for a particular date, and to display the localized weekday name for a particular date.</span></span> <span data-ttu-id="16cbb-106">特定の日付に対応する曜日を示す列挙値は、<xref:System.DateTime.DayOfWeek%2A> または <xref:System.DateTimeOffset.DayOfWeek%2A> プロパティから取得できます。</span><span class="sxs-lookup"><span data-stu-id="16cbb-106">An enumerated value that indicates the day of the week corresponding to a particular date is available from the <xref:System.DateTime.DayOfWeek%2A> or <xref:System.DateTimeOffset.DayOfWeek%2A> property.</span></span> <span data-ttu-id="16cbb-107">対照的に、曜日名の取得は、書式指定メソッド （日付と時刻の値の `ToString` メソッドや <xref:System.String.Format%2A?displayProperty=nameWithType> メソッドなど） を呼び出して実行できる書式指定操作です。</span><span class="sxs-lookup"><span data-stu-id="16cbb-107">In contrast, retrieving the weekday name is a formatting operation that can be performed by calling a formatting method, such as a date and time value's `ToString` method or the <xref:System.String.Format%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="16cbb-108">このトピックでは、このような書式指定操作を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-108">This topic shows how to perform these formatting operations.</span></span>  
  
## <a name="extract-a-number-indicating-the-day-of-the-week"></a><span data-ttu-id="16cbb-109">曜日を表す数値を抽出する</span><span class="sxs-lookup"><span data-stu-id="16cbb-109">Extract a number indicating the day of the week</span></span>
  
1. <span data-ttu-id="16cbb-110">文字列形式の日付を処理している場合には、静的 <xref:System.DateTime> または <xref:System.DateTimeOffset> メソッドを使用して、その日付を<xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 値または <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-110">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="16cbb-111"><xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> プロパティまたは <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> プロパティを使用して、曜日を示す <xref:System.DayOfWeek> 値を取得します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-111">Use the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve a <xref:System.DayOfWeek> value that indicates the day of the week.</span></span>  
  
3. <span data-ttu-id="16cbb-112">必要に応じて、<xref:System.DayOfWeek> 値を整数にキャスト （C#） または変換 （Visual Basic） します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-112">If necessary, cast (in C#) or convert (in Visual Basic) the <xref:System.DayOfWeek> value to an integer.</span></span>  
  
 <span data-ttu-id="16cbb-113">次の例は、特定の日付の曜日を表す整数を表示します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-113">The following example displays an integer that represents the day of the week of a specific date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/weekdaynumber7.cs#7)]
 [!code-vb[Formatting.Howto.WeekdayName#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/weekdaynumber7.vb#7)]  
  
## <a name="extract-the-abbreviated-weekday-name"></a><span data-ttu-id="16cbb-114">曜日の省略名を抽出する</span><span class="sxs-lookup"><span data-stu-id="16cbb-114">Extract the abbreviated weekday name</span></span>
  
1. <span data-ttu-id="16cbb-115">文字列形式の日付を処理している場合には、静的 <xref:System.DateTime> または <xref:System.DateTimeOffset> メソッドを使用して、その日付を<xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 値または <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-115">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="16cbb-116">次の手順で現在のカルチャまたは特定のカルチャの曜日の省略名を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="16cbb-116">You can extract the abbreviated weekday name of the current culture or of a specific culture:</span></span>  
  
    1. <span data-ttu-id="16cbb-117">現在のカルチャの曜日の省略名を抽出するには、日付と時刻の値の <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> インスタンス メソッドまたは <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> インスタンス メソッドを呼び出し、`format` パラメーターとして文字列 "ddd" を渡します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-117">To extract the abbreviated weekday name for the current culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="16cbb-118">次の例に、<xref:System.DateTime.ToString%28System.String%29> メソッドの呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-118">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname1.cs#1)]
         [!code-vb[Formatting.Howto.WeekdayName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname1.vb#1)]  
  
    2. <span data-ttu-id="16cbb-119">特定のカルチャの曜日の省略名を抽出するには、日付と時刻の値の <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> インスタンス メソッドまたは <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> インスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-119">To extract the abbreviated weekday name for a specific culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="16cbb-120">`format` パラメーターとして文字列 "ddd" を渡します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-120">Pass the string "ddd" as the `format` parameter.</span></span> <span data-ttu-id="16cbb-121">曜日名を取得するカルチャを表す <xref:System.Globalization.CultureInfo> または <xref:System.Globalization.DateTimeFormatInfo> オブジェクトのいずれかを`provider` パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-121">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="16cbb-122">次のコードは、fr-FR カルチャを表す <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> オブジェクトを使用した <xref:System.Globalization.CultureInfo> メソッドの呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-122">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the fr-FR culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/abbrname2.cs#2)]
         [!code-vb[Formatting.Howto.WeekdayName#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/abbrname2.vb#2)]  
  
## <a name="extract-the-full-weekday-name"></a><span data-ttu-id="16cbb-123">曜日の完全な名前を抽出する</span><span class="sxs-lookup"><span data-stu-id="16cbb-123">Extract the full weekday name</span></span>
  
1. <span data-ttu-id="16cbb-124">文字列形式の日付を処理している場合には、静的 <xref:System.DateTime> または <xref:System.DateTimeOffset> メソッドを使用して、その日付を<xref:System.DateTime.Parse%2A?displayProperty=nameWithType> 値または <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-124">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
2. <span data-ttu-id="16cbb-125">現在のカルチャまたは特定のカルチャでの曜日の正式な名前を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="16cbb-125">You can extract the full weekday name of the current culture or of a specific culture:</span></span>  
  
    1. <span data-ttu-id="16cbb-126">現在のカルチャの曜日名を抽出するには、日付と時刻の値の <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> インスタンス メソッドまたは <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> インスタンス メソッドを呼び出し、`format` パラメーターとして文字列 "dddd" を渡します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-126">To extract the weekday name for the current culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> instance method, and pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="16cbb-127">次の例に、<xref:System.DateTime.ToString%28System.String%29> メソッドの呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-127">The following example illustrates the call to the <xref:System.DateTime.ToString%28System.String%29> method.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname4.cs#4)]
         [!code-vb[Formatting.Howto.WeekdayName#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname4.vb#4)]  
  
    2. <span data-ttu-id="16cbb-128">特定のカルチャの曜日名を抽出するには、日付と時刻の値の <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> インスタンス メソッドまたは <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> インスタンス メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-128">To extract the weekday name for a specific culture, call the date and time value's <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> instance method.</span></span> <span data-ttu-id="16cbb-129">`format` パラメーターとして文字列 "dddd" を渡します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-129">Pass the string "dddd" as the `format` parameter.</span></span> <span data-ttu-id="16cbb-130">曜日名を取得するカルチャを表す <xref:System.Globalization.CultureInfo> または <xref:System.Globalization.DateTimeFormatInfo> オブジェクトのいずれかを`provider` パラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-130">Pass either a <xref:System.Globalization.CultureInfo> or a <xref:System.Globalization.DateTimeFormatInfo> object that represents the culture whose weekday name you want to retrieve as the `provider` parameter.</span></span> <span data-ttu-id="16cbb-131">次のコードは、es-ES カルチャを表す <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> オブジェクトを使用した <xref:System.Globalization.CultureInfo> メソッドの呼び出しを示します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-131">The following code illustrates a call to the <xref:System.DateTime.ToString%28System.String%2CSystem.IFormatProvider%29> method using a <xref:System.Globalization.CultureInfo> object that represents the es-ES culture.</span></span>  
  
         [!code-csharp[Formatting.Howto.WeekdayName#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/fullname5.cs#5)]
         [!code-vb[Formatting.Howto.WeekdayName#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/fullname5.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="16cbb-132">例</span><span class="sxs-lookup"><span data-stu-id="16cbb-132">Example</span></span>  
 <span data-ttu-id="16cbb-133">この例は、<xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> プロパティと<xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> プロパティ、および<xref:System.DateTime.ToString%2A?displayProperty=nameWithType> メソッドと <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> メソッドを呼び出し、特定の日付の曜日を表す番号、曜日の省略名、および正式な名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-133">The example illustrates calls to the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.DayOfWeek%2A?displayProperty=nameWithType> properties and the <xref:System.DateTime.ToString%2A?displayProperty=nameWithType> and <xref:System.DateTimeOffset.ToString%2A?displayProperty=nameWithType> methods to retrieve the number that represents the day of the week, the abbreviated weekday name, and the full weekday name for a particular date.</span></span>  
  
 [!code-csharp[Formatting.Howto.WeekdayName#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/example6.cs#6)]
 [!code-vb[Formatting.Howto.WeekdayName#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example6.vb#6)]  
  
 <span data-ttu-id="16cbb-134">それぞれの言語には、.NET の機能と重複する機能または補足する機能が存在していることがあります。</span><span class="sxs-lookup"><span data-stu-id="16cbb-134">Individual languages may provide functionality that duplicates or supplements the functionality provided by .NET.</span></span> <span data-ttu-id="16cbb-135">たとえば Visual Basic には次の 2 つの関数があります。</span><span class="sxs-lookup"><span data-stu-id="16cbb-135">For example, Visual Basic includes two such functions:</span></span>  
  
- <span data-ttu-id="16cbb-136">`Weekday`: 特定の日付の曜日を示す番号を返します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-136">`Weekday`, which returns a number that indicates the day of the week of a particular date.</span></span> <span data-ttu-id="16cbb-137">この関数では週の初日の序数値が 1 ですが、<xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> プロパティでは週の初日の序数値はゼロです。</span><span class="sxs-lookup"><span data-stu-id="16cbb-137">It considers the ordinal value of the first day of the week to be one, whereas the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property considers it to be zero.</span></span>  
  
- <span data-ttu-id="16cbb-138">`WeekdayName`: 現在のカルチャで、特定の曜日番号に対応する曜日名を返します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-138">`WeekdayName`, which returns the name of the week in the current culture that corresponds to a particular weekday number.</span></span>  
  
 <span data-ttu-id="16cbb-139">次の例は、Visual Basic の `Weekday` 関数と `WeekdayName` 関数の使い方を示します。</span><span class="sxs-lookup"><span data-stu-id="16cbb-139">The following example illustrates the use of the Visual Basic `Weekday` and `WeekdayName` functions.</span></span>  
  
 [!code-vb[Formatting.HowTo.WeekdayName#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/example9.vb#9)]  
  
 <span data-ttu-id="16cbb-140">また、特定の日付の曜日名を取得するには <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> プロパティから返される値も使用できます。</span><span class="sxs-lookup"><span data-stu-id="16cbb-140">You can also use the value returned by the <xref:System.DateTime.DayOfWeek%2A?displayProperty=nameWithType> property to retrieve the weekday name of a particular date.</span></span> <span data-ttu-id="16cbb-141">このためには、プロパティから返された <xref:System.Enum.ToString%2A> 値に対して <xref:System.DayOfWeek> メソッドを呼び出す操作だけが必要です。</span><span class="sxs-lookup"><span data-stu-id="16cbb-141">This requires only a call to the <xref:System.Enum.ToString%2A> method on the <xref:System.DayOfWeek> value returned by the property.</span></span> <span data-ttu-id="16cbb-142">ただしこの手法では、次の例に示すように、現在のカルチャでのローカライズされた曜日名は作成されません。</span><span class="sxs-lookup"><span data-stu-id="16cbb-142">However, this technique does not produce a localized weekday name for the current culture, as the following example illustrates.</span></span>  
  
 [!code-csharp[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/cs/Howto1.cs#8)]
 [!code-vb[Formatting.HowTo.WeekdayName#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.WeekdayName/vb/Howto1.vb#8)]

## <a name="see-also"></a><span data-ttu-id="16cbb-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="16cbb-143">See also</span></span>

- [<span data-ttu-id="16cbb-144">標準の日時形式文字列</span><span class="sxs-lookup"><span data-stu-id="16cbb-144">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)
- [<span data-ttu-id="16cbb-145">カスタム日時形式文字列</span><span class="sxs-lookup"><span data-stu-id="16cbb-145">Custom Date and Time Format Strings</span></span>](custom-date-and-time-format-strings.md)
