---
title: 文字列を数値に変換する方法 - C# プログラミング ガイド
description: C# で Parse、TryParse、または Convert クラスのメソッドを呼び出すことによって、文字列を数値に変換する方法について説明します。
ms.date: 11/20/2020
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 0a9585d05a817d09308e06558352f78a5347a8f1
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099173"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="c8912-103">文字列を数値に変換する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c8912-103">How to convert a string to a number (C# Programming Guide)</span></span>

<span data-ttu-id="c8912-104">さまざまな数値型 (`int`、`long`、`double` など) にある `Parse` または `TryParse` メソッドを呼び出すか <xref:System.Convert?displayProperty=nameWithType> クラスにあるメソッドを使用して、[文字列](../../language-reference/builtin-types/reference-types.md)を数値に変換できます。</span><span class="sxs-lookup"><span data-stu-id="c8912-104">You can convert a [string](../../language-reference/builtin-types/reference-types.md) to a number by calling the `Parse` or `TryParse` method found on the various numeric types (`int`, `long`, `double`, and so on), or by using methods in the <xref:System.Convert?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="c8912-105">`TryParse` メソッド (たとえば [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) または `Parse` メソッド (たとえば [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)) を呼び出す方がいくらか効率的で簡単です。</span><span class="sxs-lookup"><span data-stu-id="c8912-105">It's slightly more efficient and straightforward to call a `TryParse` method (for example, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) or `Parse` method (for example, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).</span></span>  <span data-ttu-id="c8912-106"><xref:System.IConvertible> を実装している一般的なオブジェクトでは、<xref:System.Convert> メソッドを使用するのがより便利です。</span><span class="sxs-lookup"><span data-stu-id="c8912-106">Using a <xref:System.Convert> method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="c8912-107">文字列に含まれていると思われる数値型 (<xref:System.Int32?displayProperty=nameWithType> 型など) の `Parse` または `TryParse` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8912-107">You use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="c8912-108"><xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> メソッドは、<xref:System.Int32.Parse%2A> を内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="c8912-108">The <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="c8912-109">`Parse` メソッドは、変換された数値を返します。`TryParse` メソッドは、変換に成功したかどうかを示す <xref:System.Boolean> 値を返し、変換された数値を [`out` パラメーター](../../language-reference/keywords/out.md)内で返します。</span><span class="sxs-lookup"><span data-stu-id="c8912-109">The `Parse` method returns the converted number; the `TryParse` method returns a <xref:System.Boolean> value that indicates whether the conversion succeeded, and returns the converted number in an [`out` parameter](../../language-reference/keywords/out.md).</span></span> <span data-ttu-id="c8912-110">文字列の形式が無効である場合、`Parse` では例外がスローされますが、`TryParse` では `false` が返されます。</span><span class="sxs-lookup"><span data-stu-id="c8912-110">If the string isn't in a valid format, `Parse` throws an exception, but `TryParse` returns `false`.</span></span> <span data-ttu-id="c8912-111">`Parse` メソッドを呼び出すときに、常に例外処理を使用して、解析操作が失敗した場合に <xref:System.FormatException> をキャッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8912-111">When calling a `Parse` method, you should always use exception handling to catch a <xref:System.FormatException> in the event that the parse operation fails.</span></span>  
  
## <a name="calling-the-parse-and-tryparse-methods"></a><span data-ttu-id="c8912-112">Parse メソッドと TryParse メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="c8912-112">Calling the Parse and TryParse methods</span></span>

<span data-ttu-id="c8912-113">文字列の先頭と末尾の空白文字は、`Parse` および `TryParse` メソッドによって無視されますが、その他のすべての文字は、適切な数値型 (`int`、`long`、`ulong`、`float`、`decimal` など) を形成する文字である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8912-113">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (`int`, `long`, `ulong`, `float`, `decimal`, and so on).</span></span>  <span data-ttu-id="c8912-114">数値を形成する文字列内に空白文字があると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="c8912-114">Any white space within the string that forms the number causes an error.</span></span>  <span data-ttu-id="c8912-115">たとえば、"10"、"10.3"、または "  10  " を解析するために `decimal.TryParse` を使用することはできますが、"10X"、"1 0" (埋め込みスペースに注意)、"10 .3" (埋め込みスペースに注意)、"10e1" (この場合は `float.TryParse` を使用) などからこのメソッドを使用して 10 を解析することはできません。</span><span class="sxs-lookup"><span data-stu-id="c8912-115">For example, you can use `decimal.TryParse` to parse "10", "10.3", or "  10  ", but you can't use this method to parse 10 from "10X", "1 0" (note the embedded space), "10 .3" (note the embedded space), "10e1" (`float.TryParse` works here), and so on.</span></span> <span data-ttu-id="c8912-116">値が `null` または <xref:System.String.Empty?displayProperty=nameWithType> の文字列は正常に解析できません。</span><span class="sxs-lookup"><span data-stu-id="c8912-116">A string whose value is `null` or <xref:System.String.Empty?displayProperty=nameWithType> fails to parse successfully.</span></span> <span data-ttu-id="c8912-117"><xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> メソッドを呼び出すことで、解析を試みる前に null または空の文字列を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c8912-117">You can check for a null or empty string before attempting to parse it by calling the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c8912-118">次の例は、`Parse` および `TryParse` の呼び出しの成功例と失敗例の両方を示しています。</span><span class="sxs-lookup"><span data-stu-id="c8912-118">The following example demonstrates both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

<span data-ttu-id="c8912-119">次の例は、先頭に数字 (16 進数文字を含む)、末尾に数字以外の文字を含むと予想される文字列を解析する 1 つのアプローチを示しています。</span><span class="sxs-lookup"><span data-stu-id="c8912-119">The following example illustrates one approach to parsing a string expected to include leading numeric characters (including hexadecimal characters) and trailing non-numeric characters.</span></span> <span data-ttu-id="c8912-120"><xref:System.Int32.TryParse%2A> メソッドを呼び出す前に、文字列の先頭から新しい文字列に有効な文字を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c8912-120">It assigns valid characters from the beginning of a string to a new string before calling the <xref:System.Int32.TryParse%2A> method.</span></span> <span data-ttu-id="c8912-121">解析する文字列には少数の文字が含まれるので、例では <xref:System.String.Concat%2A?displayProperty=nameWithType> メソッドを呼び出して新しい文字列に有効な文字を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c8912-121">Because the strings to be parsed contain a small number of characters, the example calls the <xref:System.String.Concat%2A?displayProperty=nameWithType> method to assign valid characters to a new string.</span></span> <span data-ttu-id="c8912-122">より大きな文字列の場合は、代わりに <xref:System.Text.StringBuilder> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8912-122">For a larger string, the <xref:System.Text.StringBuilder> class can be used instead.</span></span>
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a><span data-ttu-id="c8912-123">変換メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="c8912-123">Calling the Convert methods</span></span>

<span data-ttu-id="c8912-124">文字列を数値に変換するために使用できる <xref:System.Convert> クラスのメソッドの一部を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="c8912-124">The following table lists some of the methods from the <xref:System.Convert> class that you can use to convert a string to a number.</span></span>  
  
|<span data-ttu-id="c8912-125">数値型</span><span class="sxs-lookup"><span data-stu-id="c8912-125">Numeric Type</span></span>|<span data-ttu-id="c8912-126">メソッド</span><span class="sxs-lookup"><span data-stu-id="c8912-126">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="c8912-127">次の例では、<xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> メソッドを呼び出して、入力文字列を [int](../../language-reference/builtin-types/integral-numeric-types.md) に変換します。例では、このメソッドからスローされる可能性のある最も一般的な 2 種類の例外 (<xref:System.FormatException> と <xref:System.OverflowException>) をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="c8912-127">The following example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input string to an [int](../../language-reference/builtin-types/integral-numeric-types.md). The example catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="c8912-128"><xref:System.Int32.MaxValue?displayProperty=nameWithType> を超えずに結果の数値を増やすことができる場合、例では結果に 1 を加算し、出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="c8912-128">If the resulting number can be incremented without exceeding <xref:System.Int32.MaxValue?displayProperty=nameWithType>, the example adds 1 to the result and displays the output.</span></span>  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c8912-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8912-129">See also</span></span>

- [<span data-ttu-id="c8912-130">型</span><span class="sxs-lookup"><span data-stu-id="c8912-130">Types</span></span>](./index.md)
- [<span data-ttu-id="c8912-131">文字列が数値を表しているかどうかを確認する方法</span><span class="sxs-lookup"><span data-stu-id="c8912-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- [<span data-ttu-id="c8912-132">サンプル: .NET Core WinForms 書式設定ユーティリティ (C#)</span><span class="sxs-lookup"><span data-stu-id="c8912-132">Sample: .NET Core WinForms Formatting Utility (C#)</span></span>](/samples/dotnet/samples/windowsforms-formatting-utility-cs)
