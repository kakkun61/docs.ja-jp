---
title: 列挙型形式文字列
description: .NET で Enum.ToString メソッドを使用して、列挙型形式文字列を作成します。 列挙型メンバーの数値、16 進数、または文字列値の書式を設定します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
ms.openlocfilehash: e4d8ca27d99c211653269b2477be8f5632b78229
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888660"
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="7058a-104">列挙型形式文字列</span><span class="sxs-lookup"><span data-stu-id="7058a-104">Enumeration format strings</span></span>

<span data-ttu-id="7058a-105"><xref:System.Enum.ToString%2A?displayProperty=nameWithType> メソッドを使用すると、列挙型メンバーの数値、16 進数、または文字列値を表す新しい文字列オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7058a-105">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="7058a-106">このメソッドは、列挙型書式指定文字列のいずれかを使って、返される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="7058a-106">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>

<span data-ttu-id="7058a-107">次のセクションでは、列挙型書式指定文字列とそれが返す値を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7058a-107">The following sections list the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="7058a-108">これらの書式指定子では大文字と小文字は区別されません。</span><span class="sxs-lookup"><span data-stu-id="7058a-108">These format specifiers are not case-sensitive.</span></span>

## <a name="g-or-g"></a><span data-ttu-id="7058a-109">G または g</span><span class="sxs-lookup"><span data-stu-id="7058a-109">G or g</span></span>

<span data-ttu-id="7058a-110">可能な場合には列挙エントリを文字列値として表示し、それ以外の場合は、現在のインスタンスの整数値を表示します。</span><span class="sxs-lookup"><span data-stu-id="7058a-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="7058a-111">列挙型が **Flags** 属性セットで定義されている場合、有効な各エントリの文字列値はコンマで区切られて連結されます。</span><span class="sxs-lookup"><span data-stu-id="7058a-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="7058a-112">**Flags** 属性が設定されていない場合、無効な値が数値エントリとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="7058a-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="7058a-113">次の例は、G 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="7058a-113">The following example illustrates the G format specifier.</span></span>

[!code-csharp[Formatting.Enum#1](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)]
[!code-vb[Formatting.Enum#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]

## <a name="f-or-f"></a><span data-ttu-id="7058a-114">F または f</span><span class="sxs-lookup"><span data-stu-id="7058a-114">F or f</span></span>

<span data-ttu-id="7058a-115">可能な場合には列挙エントリを文字列値として表示します。</span><span class="sxs-lookup"><span data-stu-id="7058a-115">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="7058a-116">( **Flags** 属性が存在しない場合でも) 値が列挙内のエントリの総和として完全に表示できる場合、有効な各エントリの文字列値はコンマで区切られて連結されます。</span><span class="sxs-lookup"><span data-stu-id="7058a-116">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="7058a-117">値が列挙エントリによって完全に特定できない場合、その値は整数値として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="7058a-117">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="7058a-118">次の例は、F 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="7058a-118">The following example illustrates the F format specifier.</span></span>

[!code-csharp[Formatting.Enum#2](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)]
[!code-vb[Formatting.Enum#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]

## <a name="d-or-d"></a><span data-ttu-id="7058a-119">D または d</span><span class="sxs-lookup"><span data-stu-id="7058a-119">D or d</span></span>

<span data-ttu-id="7058a-120">列挙エントリを整数値として可能な限り短い表現で表示します。</span><span class="sxs-lookup"><span data-stu-id="7058a-120">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="7058a-121">次の例は、D 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="7058a-121">The following example illustrates the D format specifier.</span></span>

[!code-csharp[Formatting.Enum#3](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)]
[!code-vb[Formatting.Enum#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]

## <a name="x-or-x"></a><span data-ttu-id="7058a-122">X または x</span><span class="sxs-lookup"><span data-stu-id="7058a-122">X or x</span></span>

<span data-ttu-id="7058a-123">列挙エントリを 16 進値として表示します。</span><span class="sxs-lookup"><span data-stu-id="7058a-123">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="7058a-124">列挙型の[基になる数値型](xref:System.Enum.GetUnderlyingType%2A)で結果文字列にバイトあたり文字が 2 つ与えられるように、必要に応じてこの値の先頭にゼロが付きます。</span><span class="sxs-lookup"><span data-stu-id="7058a-124">The value is represented with leading zeros as necessary, to ensure that the result string has two characters for each byte in the enumeration type's [underlying numeric type](xref:System.Enum.GetUnderlyingType%2A).</span></span> <span data-ttu-id="7058a-125">次の例は、X 書式指定子を示しています。</span><span class="sxs-lookup"><span data-stu-id="7058a-125">The following example illustrates the X format specifier.</span></span> <span data-ttu-id="7058a-126">例では、<xref:System.ConsoleColor> と <xref:System.IO.FileAttributes> は両方、基になる型が <xref:System.Int32> か 32 ビット (4 バイト) の整数になり、8 文字からなる結果文字列が生成されます。</span><span class="sxs-lookup"><span data-stu-id="7058a-126">In the example, the underlying type of both <xref:System.ConsoleColor> and <xref:System.IO.FileAttributes> is <xref:System.Int32>, or a 32-bit (or 4-byte) integer, which produces an 8-character result string.</span></span>

[!code-csharp[Formatting.Enum#4](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)]
[!code-vb[Formatting.Enum#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]

## <a name="example"></a><span data-ttu-id="7058a-127">例</span><span class="sxs-lookup"><span data-stu-id="7058a-127">Example</span></span>

<span data-ttu-id="7058a-128">次の例では、`Red`、`Blue`、`Green` の 3 つのエントリから構成される、`Colors` と呼ばれる列挙型を定義します。</span><span class="sxs-lookup"><span data-stu-id="7058a-128">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>

[!code-csharp[Formatting.Enum#5](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
[!code-vb[Formatting.Enum#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]

<span data-ttu-id="7058a-129">列挙型を定義すると、次のようにインスタンスを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="7058a-129">After the enumeration is defined, an instance can be declared in the following manner.</span></span>

[!code-csharp[Formatting.Enum#6](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
[!code-vb[Formatting.Enum#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]

<span data-ttu-id="7058a-130">これで `Color.ToString(System.String)` メソッドを使用して、渡された書式指定子に応じて、列挙値をさまざまな方法で表示することができます。</span><span class="sxs-lookup"><span data-stu-id="7058a-130">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>

[!code-csharp[Formatting.Enum#7](~/samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
[!code-vb[Formatting.Enum#7](~/samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]

## <a name="see-also"></a><span data-ttu-id="7058a-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="7058a-131">See also</span></span>

- [<span data-ttu-id="7058a-132">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="7058a-132">Formatting Types</span></span>](formatting-types.md)
