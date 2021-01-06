---
title: 16 進文字列と数値型の間で変換する方法 - C# プログラミング ガイド
description: 16 進文字列と数値型の間で変換を行う方法について説明します。 コード例を参照し、使用可能なその他のリソースを確認してください。
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 18021156af879f324993beca04531c8a822725db
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513238"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="20e7b-104">16 進文字列と数値型の間で変換する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="20e7b-104">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>

<span data-ttu-id="20e7b-105">以下の例では、次のタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-105">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="20e7b-106">[string](../../language-reference/builtin-types/reference-types.md) の各文字の 16 進値を取得する。</span><span class="sxs-lookup"><span data-stu-id="20e7b-106">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="20e7b-107">16 進文字列の各値に対応する [char](../../language-reference/builtin-types/char.md) を取得する。</span><span class="sxs-lookup"><span data-stu-id="20e7b-107">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="20e7b-108">16 進 `string` を [int](../../language-reference/builtin-types/integral-numeric-types.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="20e7b-108">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="20e7b-109">16 進 `string` を [float](../../language-reference/builtin-types/floating-point-numeric-types.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="20e7b-109">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="20e7b-110">[バイト](../../language-reference/builtin-types/integral-numeric-types.md)配列を 16 進 `string` に変換する。</span><span class="sxs-lookup"><span data-stu-id="20e7b-110">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20e7b-111">例</span><span class="sxs-lookup"><span data-stu-id="20e7b-111">Example</span></span>  

 <span data-ttu-id="20e7b-112">この例では、`string` の各文字の 16 進値を出力しています。</span><span class="sxs-lookup"><span data-stu-id="20e7b-112">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="20e7b-113">まず `string` を解析し、文字配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-113">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="20e7b-114">次いで、その数値を取得するために、各文字で <xref:System.Convert.ToInt32%28System.Char%29> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-114">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="20e7b-115">最後に、その数を 16 進表現で `string` に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-115">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="20e7b-116">例</span><span class="sxs-lookup"><span data-stu-id="20e7b-116">Example</span></span>  

 <span data-ttu-id="20e7b-117">この例は、16 進値の `string` を解析し、各 16 進値に対応する文字を出力しています。</span><span class="sxs-lookup"><span data-stu-id="20e7b-117">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="20e7b-118">まず、[Split(Char\[\])](xref:System.String.Split(System.Char[])) メソッドを呼び出して、各 16 進値を配列内の個別の `string` として取得します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-118">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="20e7b-119">次いで <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> を呼び出し、16 進数値を [int](../../language-reference/builtin-types/integral-numeric-types.md) の 10 進数値に変換します。ここでは、その文字コードに対応する文字を取得するための 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="20e7b-119">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="20e7b-120">1 つは、<xref:System.Char.ConvertFromUtf32%28System.Int32%29> を使用する方法です。これは、整数引数に対応する文字を `string` として返します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="20e7b-121">もう 1 つは、`int` を明示的に [char](../../language-reference/builtin-types/char.md) にキャストする方法です。</span><span class="sxs-lookup"><span data-stu-id="20e7b-121">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="20e7b-122">例</span><span class="sxs-lookup"><span data-stu-id="20e7b-122">Example</span></span>  

 <span data-ttu-id="20e7b-123">この例では、<xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> メソッドを呼び出し、16 進数 `string` を整数に変換する、別の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-123">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="20e7b-124">例</span><span class="sxs-lookup"><span data-stu-id="20e7b-124">Example</span></span>  

 <span data-ttu-id="20e7b-125">次の例では、<xref:System.BitConverter?displayProperty=nameWithType> クラスおよび <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> メソッドを使用して、16 進数の `string` を [float](../../language-reference/builtin-types/floating-point-numeric-types.md) に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-125">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="20e7b-126">例</span><span class="sxs-lookup"><span data-stu-id="20e7b-126">Example</span></span>  

 <span data-ttu-id="20e7b-127">次の例は、<xref:System.BitConverter?displayProperty=nameWithType> クラスを使用して [byte](../../language-reference/builtin-types/integral-numeric-types.md) 配列を 16 進文字列に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="20e7b-127">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="20e7b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="20e7b-128">See also</span></span>

- [<span data-ttu-id="20e7b-129">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="20e7b-129">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="20e7b-130">型</span><span class="sxs-lookup"><span data-stu-id="20e7b-130">Types</span></span>](./index.md)
- [<span data-ttu-id="20e7b-131">文字列が数値を表しているかどうかを確認する方法</span><span class="sxs-lookup"><span data-stu-id="20e7b-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
