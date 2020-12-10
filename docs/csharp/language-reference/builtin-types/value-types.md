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
ms.openlocfilehash: 64c9e9eba2495531cfef8a603d53fb21c95c87a4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599396"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="649a2-103">値型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="649a2-103">Value types (C# reference)</span></span>

<span data-ttu-id="649a2-104">C# 型の 2 つの主なカテゴリは、*値型* と [参照型](../keywords/reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="649a2-104">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="649a2-105">値型の変数には、その型のインスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="649a2-105">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="649a2-106">これは、その型のインスタンスへの参照を含む参照型の変数とは異なります。</span><span class="sxs-lookup"><span data-stu-id="649a2-106">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="649a2-107">既定では、[代入](../operators/assignment-operator.md)時、引数がメソッドに渡され、メソッドの結果が返され、変数値がコピーされます。</span><span class="sxs-lookup"><span data-stu-id="649a2-107">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="649a2-108">値型の変数の場合、対応する型のインスタンスがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="649a2-108">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="649a2-109">次の例は、その動作を示します。</span><span class="sxs-lookup"><span data-stu-id="649a2-109">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/shared/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="649a2-110">前の例のとおり、値型変数に対する操作は、その変数に格納されている値型のインスタンスのみに影響します。</span><span class="sxs-lookup"><span data-stu-id="649a2-110">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="649a2-111">値型に参照型のデータ メンバーが含まれている場合は、値型のインスタンスがコピーされるとき、その参照型のインスタンスへの参照のみがコピーされます。</span><span class="sxs-lookup"><span data-stu-id="649a2-111">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="649a2-112">コピーと元の値型のインスタンスの両方が、同じ参照型のインスタンスにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="649a2-112">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="649a2-113">次の例は、その動作を示します。</span><span class="sxs-lookup"><span data-stu-id="649a2-113">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/shared/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="649a2-114">ご自分のコードをエラーがより発生しにくく、より堅牢にするには、変更できない値型を定義して使用します。</span><span class="sxs-lookup"><span data-stu-id="649a2-114">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="649a2-115">この記事では、デモンストレーションの目的でのみ、変更可能な値型を使用します。</span><span class="sxs-lookup"><span data-stu-id="649a2-115">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types-and-type-constraints"></a><span data-ttu-id="649a2-116">値型と型制約の種類</span><span class="sxs-lookup"><span data-stu-id="649a2-116">Kinds of value types and type constraints</span></span>

<span data-ttu-id="649a2-117">値型には、次の 2 種類のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="649a2-117">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="649a2-118">データと関連機能をカプセル化する[構造体の型](struct.md)</span><span class="sxs-lookup"><span data-stu-id="649a2-118">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="649a2-119">名前付き定数のセットによって定義され、選択肢または選択肢の組み合わせを表す、[列挙型](enum.md)</span><span class="sxs-lookup"><span data-stu-id="649a2-119">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="649a2-120">[null 許容値型](nullable-value-types.md) `T?` は、基になる値型のすべての値 `T` と、追加の [null](../keywords/null.md) 値を表します。</span><span class="sxs-lookup"><span data-stu-id="649a2-120">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="649a2-121">値型の変数には、Null 許容値型でない限り `null` を割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="649a2-121">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

<span data-ttu-id="649a2-122">[`struct` 制約](../../programming-guide/generics/constraints-on-type-parameters.md)を使用して、型パラメーターが null 非許容値型であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="649a2-122">You can use the [`struct` constraint](../../programming-guide/generics/constraints-on-type-parameters.md) to specify that a type parameter is a non-nullable value type.</span></span> <span data-ttu-id="649a2-123">構造体と列挙型の型は、どちらも `struct` 制約を満たしています。</span><span class="sxs-lookup"><span data-stu-id="649a2-123">Both structure and enumeration types satisfy the `struct` constraint.</span></span> <span data-ttu-id="649a2-124">C# 7.3 以降、基底クラス制約 ([列挙の制約](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)と呼ばれます) で `System.Enum` を使用して、型パラメーターが列挙型であることを指定できます。</span><span class="sxs-lookup"><span data-stu-id="649a2-124">Beginning with C# 7.3, you can use `System.Enum` in a base class constraint (that is known as the [enum constraint](../../programming-guide/generics/constraints-on-type-parameters.md#enum-constraints)) to specify that a type parameter is an enumeration type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="649a2-125">組み込みの値型</span><span class="sxs-lookup"><span data-stu-id="649a2-125">Built-in value types</span></span>

<span data-ttu-id="649a2-126">C# には、*単純型* とも呼ばれる次の組み込み値型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="649a2-126">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="649a2-127">整数数値型</span><span class="sxs-lookup"><span data-stu-id="649a2-127">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="649a2-128">浮動小数点数値型</span><span class="sxs-lookup"><span data-stu-id="649a2-128">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="649a2-129">ブール値を表す [bool](bool.md)</span><span class="sxs-lookup"><span data-stu-id="649a2-129">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="649a2-130">Unicode UTF-16 文字を表す [char](char.md)</span><span class="sxs-lookup"><span data-stu-id="649a2-130">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="649a2-131">すべての単純型は構造体型で、それらには他の構造体型とは異なる特定の追加操作があります。</span><span class="sxs-lookup"><span data-stu-id="649a2-131">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="649a2-132">単純型の値の指定には、リテラルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="649a2-132">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="649a2-133">たとえば、`'A'` は `char` 型のリテラルで、`2001` は `int` 型のリテラルです。</span><span class="sxs-lookup"><span data-stu-id="649a2-133">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="649a2-134">単純型の定数は、[const](../keywords/const.md) キーワードを使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="649a2-134">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="649a2-135">他の構造体型の定数は使用できません。</span><span class="sxs-lookup"><span data-stu-id="649a2-135">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="649a2-136">オペランドがすべて単純型の定数の定数式は、コンパイル時に評価されます。</span><span class="sxs-lookup"><span data-stu-id="649a2-136">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="649a2-137">C# は C# 7.0 以降で、[値のタプル](value-tuples.md)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="649a2-137">Beginning with C# 7.0, C# supports [value tuples](value-tuples.md).</span></span> <span data-ttu-id="649a2-138">値のタプルは単純型ではない値型です。</span><span class="sxs-lookup"><span data-stu-id="649a2-138">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="649a2-139">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="649a2-139">C# language specification</span></span>

<span data-ttu-id="649a2-140">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="649a2-140">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="649a2-141">値型</span><span class="sxs-lookup"><span data-stu-id="649a2-141">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="649a2-142">単純型</span><span class="sxs-lookup"><span data-stu-id="649a2-142">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="649a2-143">変数</span><span class="sxs-lookup"><span data-stu-id="649a2-143">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="649a2-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="649a2-144">See also</span></span>

- [<span data-ttu-id="649a2-145">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="649a2-145">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="649a2-146">参照型</span><span class="sxs-lookup"><span data-stu-id="649a2-146">Reference types</span></span>](../keywords/reference-types.md)
