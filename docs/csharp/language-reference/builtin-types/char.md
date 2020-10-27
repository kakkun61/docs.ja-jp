---
description: C# での組み込みの文字型について
title: char 型 - C# リファレンス
ms.date: 05/11/2020
f1_keywords:
- char
- char_CSharpKeyword
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
ms.openlocfilehash: 1cb40759b81a1fcedcf5962b57d79cf3a64df561
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471877"
---
# <a name="char-c-reference"></a><span data-ttu-id="80525-103">char (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="80525-103">char (C# reference)</span></span>

<span data-ttu-id="80525-104">`char` 型のキーワードは、Unicode UTF-16 文字を表す .NET <xref:System.Char?displayProperty=nameWithType> 構造体型のエイリアスです。</span><span class="sxs-lookup"><span data-stu-id="80525-104">The `char` type keyword is an alias for the .NET <xref:System.Char?displayProperty=nameWithType> structure type that represents a Unicode UTF-16 character.</span></span>

|<span data-ttu-id="80525-105">種類</span><span class="sxs-lookup"><span data-stu-id="80525-105">Type</span></span>|<span data-ttu-id="80525-106">範囲</span><span class="sxs-lookup"><span data-stu-id="80525-106">Range</span></span>|<span data-ttu-id="80525-107">サイズ</span><span class="sxs-lookup"><span data-stu-id="80525-107">Size</span></span>|<span data-ttu-id="80525-108">.NET 型</span><span class="sxs-lookup"><span data-stu-id="80525-108">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`char`|<span data-ttu-id="80525-109">U+0000 ～ U+FFFF</span><span class="sxs-lookup"><span data-stu-id="80525-109">U+0000 to U+FFFF</span></span>|<span data-ttu-id="80525-110">16 ビット</span><span class="sxs-lookup"><span data-stu-id="80525-110">16 bit</span></span>|<xref:System.Char?displayProperty=nameWithType>|

<span data-ttu-id="80525-111">`char` 型の既定値は `\0` (つまり U+0000) です。</span><span class="sxs-lookup"><span data-stu-id="80525-111">The default value of the `char` type is `\0`, that is, U+0000.</span></span>

<span data-ttu-id="80525-112">`char` 型では、[比較](../operators/comparison-operators.md)演算子、[等値](../operators/equality-operators.md)演算子、[インクリメント](../operators/arithmetic-operators.md#increment-operator-)演算子、および[デクリメント](../operators/arithmetic-operators.md#decrement-operator---)演算子がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="80525-112">The `char` type supports [comparison](../operators/comparison-operators.md), [equality](../operators/equality-operators.md), [increment](../operators/arithmetic-operators.md#increment-operator-), and [decrement](../operators/arithmetic-operators.md#decrement-operator---) operators.</span></span> <span data-ttu-id="80525-113">さらに、`char` オペランドの場合、[算術](../operators/arithmetic-operators.md)演算子および[ビット論理](../operators/bitwise-and-shift-operators.md)演算子によって、対応する文字コードに対する演算が実行され、`int` 型の結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="80525-113">Moreover, for `char` operands, [arithmetic](../operators/arithmetic-operators.md) and [bitwise logical](../operators/bitwise-and-shift-operators.md) operators perform an operation on the corresponding character codes and produce the result of the `int` type.</span></span>

<span data-ttu-id="80525-114">[string](reference-types.md#the-string-type) 型では、`char` 値のシーケンスとしてテキストを表わします。</span><span class="sxs-lookup"><span data-stu-id="80525-114">The [string](reference-types.md#the-string-type) type represents text as a sequence of `char` values.</span></span>

## <a name="literals"></a><span data-ttu-id="80525-115">リテラル</span><span class="sxs-lookup"><span data-stu-id="80525-115">Literals</span></span>

<span data-ttu-id="80525-116">`char` 値は以下で指定できます。</span><span class="sxs-lookup"><span data-stu-id="80525-116">You can specify a `char` value with:</span></span>

- <span data-ttu-id="80525-117">文字リテラル。</span><span class="sxs-lookup"><span data-stu-id="80525-117">a character literal.</span></span>
- <span data-ttu-id="80525-118">Unicode エスケープシーケンス。これは `\u` の後に文字コードの 16 進数表現 (4 つの記号) を続けたものになります。</span><span class="sxs-lookup"><span data-stu-id="80525-118">a Unicode escape sequence, which is `\u` followed by the four-symbol hexadecimal representation of a character code.</span></span>
- <span data-ttu-id="80525-119">16 進数エスケープシーケンス。これは `\x` の後に文字コードの 16 進数表現を続けたものになります。</span><span class="sxs-lookup"><span data-stu-id="80525-119">a hexadecimal escape sequence, which is `\x` followed by the hexadecimal representation of a character code.</span></span>

[!code-csharp-interactive[char literals](snippets/shared/CharType.cs#Literals)]

<span data-ttu-id="80525-120">前の例に示したように、文字コードの値をそれに対応する `char` 値に型変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="80525-120">As the preceding example shows, you can also cast the value of a character code into the corresponding `char` value.</span></span>

> [!NOTE]
> <span data-ttu-id="80525-121">Unicode エスケープ シーケンスの場合、4 つの 16 進数をすべて指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80525-121">In the case of a Unicode escape sequence, you must specify all four hexadecimal digits.</span></span> <span data-ttu-id="80525-122">つまり、`\u006A` は有効なエスケープ シーケンスであり、`\u06A` と `\u6A` は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="80525-122">That is, `\u006A` is a valid escape sequence, while `\u06A` and `\u6A` are not valid.</span></span>
>
> <span data-ttu-id="80525-123">16 進数エスケープ シーケンスの場合、先頭のゼロを省略できます。</span><span class="sxs-lookup"><span data-stu-id="80525-123">In the case of a hexadecimal escape sequence, you can omit the leading zeros.</span></span> <span data-ttu-id="80525-124">つまり、エスケープ シーケンスの `\x006A`、`\x06A`、`\x6A` は有効であり、同じ文字に対応します。</span><span class="sxs-lookup"><span data-stu-id="80525-124">That is, the `\x006A`, `\x06A`, and `\x6A` escape sequences are valid and correspond to the same character.</span></span>

## <a name="conversions"></a><span data-ttu-id="80525-125">変換</span><span class="sxs-lookup"><span data-stu-id="80525-125">Conversions</span></span>

<span data-ttu-id="80525-126">`char` 型は、[整数](integral-numeric-types.md)型 (`ushort`、`int`、`uint`、`long`、`ulong`) に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="80525-126">The `char` type is implicitly convertible to the following [integral](integral-numeric-types.md) types: `ushort`, `int`, `uint`, `long`, and `ulong`.</span></span> <span data-ttu-id="80525-127">また、組み込みの[浮動小数点](floating-point-numeric-types.md)数値型 (`float`、`double`、`decimal`) に暗黙的に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="80525-127">It's also implicitly convertible to the built-in [floating-point](floating-point-numeric-types.md) numeric types: `float`, `double`, and `decimal`.</span></span> <span data-ttu-id="80525-128">`sbyte`、`byte`、`short` 整数型に明示的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="80525-128">It's explicitly convertible to `sbyte`, `byte`, and `short` integral types.</span></span>

<span data-ttu-id="80525-129">他の型から `char` 型へと暗黙的に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="80525-129">There are no implicit conversions from other types to the `char` type.</span></span> <span data-ttu-id="80525-130">しかし、[整数](integral-numeric-types.md)または[浮動小数点](floating-point-numeric-types.md)の数値型は、`char` に明示的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="80525-130">However, any [integral](integral-numeric-types.md) or [floating-point](floating-point-numeric-types.md) numeric type is explicitly convertible to `char`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="80525-131">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="80525-131">C# language specification</span></span>

<span data-ttu-id="80525-132">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の[整数型](~/_csharplang/spec/types.md#integral-types)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="80525-132">For more information, see the [Integral types](~/_csharplang/spec/types.md#integral-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="80525-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="80525-133">See also</span></span>

- [<span data-ttu-id="80525-134">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="80525-134">C# reference</span></span>](../index.md)
- [<span data-ttu-id="80525-135">値型</span><span class="sxs-lookup"><span data-stu-id="80525-135">Value types</span></span>](value-types.md)
- [<span data-ttu-id="80525-136">文字列</span><span class="sxs-lookup"><span data-stu-id="80525-136">Strings</span></span>](../../programming-guide/strings/index.md)
- <xref:System.Text.Rune?displayProperty=nameWithType>
- [<span data-ttu-id="80525-137">.NET での文字エンコード</span><span class="sxs-lookup"><span data-stu-id="80525-137">Character encoding in .NET</span></span>](../../../standard/base-types/character-encoding-introduction.md)
