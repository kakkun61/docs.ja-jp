---
description: C# での値の型、その種類、組み込みのものについて
title: 値型 - C# リファレンス
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 6fb33ad2eb3f6a5e8f6506527f3807f31bf33fdc
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471652"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="588d7-103">値型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="588d7-103">Value types (C# reference)</span></span>

<span data-ttu-id="588d7-104">C# 型の 2 つの主なカテゴリは、 *値型* と [参照型](../keywords/reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="588d7-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="588d7-105">値型の変数には、その型のインスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="588d7-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="588d7-106">これは、その型のインスタンスへの参照を含む参照型の変数とは異なります。</span><span class="sxs-lookup"><span data-stu-id="588d7-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="588d7-107">既定では、[代入](../operators/assignment-operator.md)時、引数がメソッドに渡され、メソッドの結果が返され、変数値がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="588d7-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="588d7-108">値型の変数の場合、対応する型のインスタンスがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="588d7-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="588d7-109">次の例は、その動作を示します。</span><span class="sxs-lookup"><span data-stu-id="588d7-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="588d7-110">前の例のとおり、値型変数に対する操作は、その変数に格納されている値型のインスタンスのみに影響します。</span><span class="sxs-lookup"><span data-stu-id="588d7-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="588d7-111">値型に参照型のデータ メンバーが含まれている場合は、値型のインスタンスがコピーされるとき、その参照型のインスタンスへの参照のみがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="588d7-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="588d7-112">コピーと元の値型のインスタンスの両方が、同じ参照型のインスタンスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="588d7-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="588d7-113">次の例は、その動作を示します。</span><span class="sxs-lookup"><span data-stu-id="588d7-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="588d7-114">ご自分のコードをエラーがより発生しにくく、より堅牢にするには、変更できない値型を定義して使用します。</span><span class="sxs-lookup"><span data-stu-id="588d7-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="588d7-115">この記事では、デモンストレーションの目的でのみ、変更可能な値型を使用します。</span><span class="sxs-lookup"><span data-stu-id="588d7-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="588d7-116">値型の種類</span><span class="sxs-lookup"><span data-stu-id="588d7-116">Kinds of value types</span></span>

<span data-ttu-id="588d7-117">値型には、次の 2 種類のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="588d7-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="588d7-118">データと関連機能をカプセル化する[構造体の型](struct.md)</span><span class="sxs-lookup"><span data-stu-id="588d7-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="588d7-119">名前付き定数のセットによって定義され、選択肢または選択肢の組み合わせを表す、[列挙型](enum.md)</span><span class="sxs-lookup"><span data-stu-id="588d7-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="588d7-120">[null 許容値型](nullable-value-types.md) `T?` は、基になる値型のすべての値 `T` と、追加の [null](../keywords/null.md) 値を表します。</span><span class="sxs-lookup"><span data-stu-id="588d7-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="588d7-121">値型の変数には、Null 許容値型でない限り `null` を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="588d7-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="588d7-122">組み込みの値型</span><span class="sxs-lookup"><span data-stu-id="588d7-122">Built-in value types</span></span>

<span data-ttu-id="588d7-123">C# には、 *単純型* とも呼ばれる次の組み込み値型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="588d7-123">C# provides the following built-in value types, also known as *simple types* :</span></span>

- [<span data-ttu-id="588d7-124">整数数値型</span><span class="sxs-lookup"><span data-stu-id="588d7-124">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="588d7-125">浮動小数点数値型</span><span class="sxs-lookup"><span data-stu-id="588d7-125">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="588d7-126">ブール値を表す [bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="588d7-126">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="588d7-127">Unicode UTF-16 文字を表す [char](char.md)</span><span class="sxs-lookup"><span data-stu-id="588d7-127">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="588d7-128">すべての単純型は構造体型で、それらには他の構造体型とは異なる特定の追加操作があります。</span><span class="sxs-lookup"><span data-stu-id="588d7-128">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="588d7-129">単純型の値の指定には、リテラルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="588d7-129">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="588d7-130">たとえば、`'A'` は `char` 型のリテラルで、`2001` は `int` 型のリテラルです。</span><span class="sxs-lookup"><span data-stu-id="588d7-130">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="588d7-131">単純型の定数は、[const](../keywords/const.md) キーワードを使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="588d7-131">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="588d7-132">他の構造体型の定数は使用できません。</span><span class="sxs-lookup"><span data-stu-id="588d7-132">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="588d7-133">オペランドがすべて単純型の定数の定数式は、コンパイル時に評価されます。</span><span class="sxs-lookup"><span data-stu-id="588d7-133">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="588d7-134">C# は C# 7.0 以降で、[値のタプル](value-tuples.md)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="588d7-134">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="588d7-135">値のタプルは単純型ではない値型です。</span><span class="sxs-lookup"><span data-stu-id="588d7-135">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="588d7-136">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="588d7-136">C# language specification</span></span>

<span data-ttu-id="588d7-137">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="588d7-137">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="588d7-138">値型</span><span class="sxs-lookup"><span data-stu-id="588d7-138">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="588d7-139">単純型</span><span class="sxs-lookup"><span data-stu-id="588d7-139">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="588d7-140">変数</span><span class="sxs-lookup"><span data-stu-id="588d7-140">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="588d7-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="588d7-141">See also</span></span>

- [<span data-ttu-id="588d7-142">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="588d7-142">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="588d7-143">参照型</span><span class="sxs-lookup"><span data-stu-id="588d7-143">Reference types</span></span>](../keywords/reference-types.md)
