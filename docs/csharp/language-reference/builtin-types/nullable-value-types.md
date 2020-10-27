---
title: null 許容値型 - C# リファレンス
description: C# の Null 許容値型とその使用方法について説明します
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 3ab2dff6b7399b0458a69d4498b2ebda24f6c5cc
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471836"
---
# <a name="nullable-value-types-c-reference"></a><span data-ttu-id="ad509-103">null 許容値型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ad509-103">Nullable value types (C# reference)</span></span>

<span data-ttu-id="ad509-104">" *null 許容値型* " `T?` は、基になる [値型](value-types.md) `T` のすべての値と、追加の [null](../keywords/null.md) 値を表します。</span><span class="sxs-lookup"><span data-stu-id="ad509-104">A *nullable value type* `T?` represents all values of its underlying [value type](value-types.md) `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="ad509-105">たとえば、`bool?` 変数には、`true`、`false`、`null` の 3 つの値のいずれかを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ad509-105">For example, you can assign any of the following three values to a `bool?` variable: `true`, `false`, or `null`.</span></span> <span data-ttu-id="ad509-106">基になる値型 `T` を null 許容値型にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ad509-106">An underlying value type `T` cannot be a nullable value type itself.</span></span>

> [!NOTE]
> <span data-ttu-id="ad509-107">C# 8.0 で、Null 許容参照型機能が導入されました。</span><span class="sxs-lookup"><span data-stu-id="ad509-107">C# 8.0 introduces the nullable reference types feature.</span></span> <span data-ttu-id="ad509-108">詳細については、「[null 許容参照型](nullable-reference-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad509-108">For more information, see [Nullable reference types](nullable-reference-types.md).</span></span> <span data-ttu-id="ad509-109">null 許容値型は、C# 2 から使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad509-109">The nullable value types are available beginning with C# 2.</span></span>

<span data-ttu-id="ad509-110">null 許容値型は、ジェネリック <xref:System.Nullable%601?displayProperty=nameWithType> 構造体のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="ad509-110">Any nullable value type is an instance of the generic <xref:System.Nullable%601?displayProperty=nameWithType> structure.</span></span> <span data-ttu-id="ad509-111">`Nullable<T>` または `T?` の代替可能な形式のいずれかで基になる型 `T` を持つ null 許容値型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="ad509-111">You can refer to a nullable value type with an underlying type `T` in any of the following interchangeable forms: `Nullable<T>` or `T?`.</span></span>

<span data-ttu-id="ad509-112">null 許容値型は通常、基になる値型の未定義の値を表す必要があるときに使用します。</span><span class="sxs-lookup"><span data-stu-id="ad509-112">You typically use a nullable value type when you need to represent the undefined value of an underlying value type.</span></span> <span data-ttu-id="ad509-113">たとえば、ブール型 (`bool`) 変数で可能なのは、`true` または `false` のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="ad509-113">For example, a Boolean, or `bool`, variable can only be either `true` or `false`.</span></span> <span data-ttu-id="ad509-114">ただし、一部のアプリケーションでは、変数の値が未定義または存在しない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad509-114">However, in some applications a variable value can be undefined or missing.</span></span> <span data-ttu-id="ad509-115">たとえば、データベース フィールドに、`true` または `false` が含まれている場合や、値がまったく含まれていない場合 (`NULL`) があります。</span><span class="sxs-lookup"><span data-stu-id="ad509-115">For example, a database field may contain `true` or `false`, or it may contain no value at all, that is, `NULL`.</span></span> <span data-ttu-id="ad509-116">このシナリオでは、`bool?` 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad509-116">You can use the `bool?` type in that scenario.</span></span>

## <a name="declaration-and-assignment"></a><span data-ttu-id="ad509-117">宣言と代入</span><span class="sxs-lookup"><span data-stu-id="ad509-117">Declaration and assignment</span></span>

<span data-ttu-id="ad509-118">値型は、対応する null 許容値型に暗黙的に変換できるため、基になる値型の場合と同様に、null 許容値型の変数に値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="ad509-118">As a value type is implicitly convertible to the corresponding nullable value type, you can assign a value to a variable of a nullable value type as you would do that for its underlying value type.</span></span> <span data-ttu-id="ad509-119">`null` 値を代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad509-119">You can also assign the `null` value.</span></span> <span data-ttu-id="ad509-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ad509-120">For example:</span></span>

[!code-csharp[declare and assign](snippets/shared/NullableValueTypes.cs#Declaration)]

<span data-ttu-id="ad509-121">null 許容値型の既定値は `null` を表します。つまり、<xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> プロパティが `false` を返すインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="ad509-121">The default value of a nullable value type represents `null`, that is, it's an instance whose <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> property returns `false`.</span></span>

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a><span data-ttu-id="ad509-122">null 許容値型のインスタンスの検査</span><span class="sxs-lookup"><span data-stu-id="ad509-122">Examination of an instance of a nullable value type</span></span>

<span data-ttu-id="ad509-123">C# 7.0 以降では、[型パターンで `is` 演算子](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching)を使用して、`null` の null 許容値型のインスタンスを調べ、基になる型の値を取得することができます。</span><span class="sxs-lookup"><span data-stu-id="ad509-123">Beginning with C# 7.0, you can use the [`is` operator with a type pattern](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) to both examine an instance of a nullable value type for `null` and retrieve a value of an underlying type:</span></span>

[!code-csharp-interactive[use pattern matching](snippets/shared/NullableValueTypes.cs#PatternMatching)]

<span data-ttu-id="ad509-124">null 許容値型の変数の値を確認して取得するには、常に次の読み取り専用プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad509-124">You always can use the following read-only properties to examine and get a value of a nullable value type variable:</span></span>

- <span data-ttu-id="ad509-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> は、null 許容値型のインスタンスに、基になる型の値が含まれるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ad509-125"><xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indicates whether an instance of a nullable value type has a value of its underlying type.</span></span>

- <span data-ttu-id="ad509-126"><xref:System.Nullable%601.HasValue%2A> が `true` の場合、<xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> は基になる型の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ad509-126"><xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> gets the value of an underlying type if <xref:System.Nullable%601.HasValue%2A> is `true`.</span></span> <span data-ttu-id="ad509-127"><xref:System.Nullable%601.HasValue%2A> が `false` の場合、<xref:System.Nullable%601.Value%2A> プロパティは <xref:System.InvalidOperationException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="ad509-127">If <xref:System.Nullable%601.HasValue%2A> is `false`, the <xref:System.Nullable%601.Value%2A> property throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="ad509-128">次の例では、`HasValue` プロパティを使用して、値を表示する前に変数に値が格納されているかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="ad509-128">The following example uses the `HasValue` property to test whether the variable contains a value before displaying it:</span></span>

[!code-csharp-interactive[use HasValue](snippets/shared/NullableValueTypes.cs#HasValue)]

<span data-ttu-id="ad509-129">次の例に示すように、`HasValue` プロパティを使用する代わりに、null 許容値型の変数を `null` と比較することもできます。</span><span class="sxs-lookup"><span data-stu-id="ad509-129">You can also compare a variable of a nullable value type with `null` instead of using the `HasValue` property, as the following example shows:</span></span>

[!code-csharp-interactive[use comparison with null](snippets/shared/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a><span data-ttu-id="ad509-130">null 許容値型から基になる型への変換</span><span class="sxs-lookup"><span data-stu-id="ad509-130">Conversion from a nullable value type to an underlying type</span></span>

<span data-ttu-id="ad509-131">null 許容値型の値を null 非許容値型の変数に割り当てる場合は、`null` の代わりに割り当てる値を指定する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad509-131">If you want to assign a value of a nullable value type to a non-nullable value type variable, you might need to specify the value to be assigned in place of `null`.</span></span> <span data-ttu-id="ad509-132">これを行うには、[null 合体演算子 `??`](../operators/null-coalescing-operator.md) を使用します (<xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> メソッドも同じ目的で使用することができます)。</span><span class="sxs-lookup"><span data-stu-id="ad509-132">Use the [null-coalescing operator `??`](../operators/null-coalescing-operator.md) to do that (you can also use the <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> method for the same purpose):</span></span>

[!code-csharp-interactive[?? operator](snippets/shared/NullableValueTypes.cs#NullCoalescing)]

<span data-ttu-id="ad509-133">`null` の代わりに基になる値の型の[既定](default-values.md)値を使用する場合は、<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad509-133">If you want to use the [default](default-values.md) value of the underlying value type in place of `null`, use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="ad509-134">次の例に示すように、null 許容値型を null 非許容型に明示的にキャストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ad509-134">You can also explicitly cast a nullable value type to a non-nullable type, as the following example shows:</span></span>

[!code-csharp[explicit cast](snippets/shared/NullableValueTypes.cs#Cast)]

<span data-ttu-id="ad509-135">実行時に null 許容値型の値が `null` の場合は、明示的なキャストによって <xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ad509-135">At run time, if the value of a nullable value type is `null`, the explicit cast throws an <xref:System.InvalidOperationException>.</span></span>

<span data-ttu-id="ad509-136">null 非許容値型 `T` は、対応する null 許容値型 `T?` に暗黙的に変換されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-136">A non-nullable value type `T` is implicitly convertible to the corresponding nullable value type `T?`.</span></span>

## <a name="lifted-operators"></a><span data-ttu-id="ad509-137">リフト演算子</span><span class="sxs-lookup"><span data-stu-id="ad509-137">Lifted operators</span></span>

<span data-ttu-id="ad509-138">定義済みの単項[演算子](../operators/index.md)および 2 項演算子、または値型 `T` によってサポートされるオーバーロードされた任意の演算子は、対応する null 許容値型 `T?` でもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ad509-138">The predefined unary and binary [operators](../operators/index.md) or any overloaded operators that are supported by a value type `T` are also supported by the corresponding nullable value type `T?`.</span></span> <span data-ttu-id="ad509-139">" *リフト演算子* " とも呼ばれるこれらの演算子では、一方または両方のオペランドが `null` の場合に `null` が生成されます。それ以外の場合は、そのオペランドに含まれている値を使用して結果が算出されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-139">These operators, also known as *lifted operators* , produce `null` if one or both operands are `null`; otherwise, the operator uses the contained values of its operands to calculate the result.</span></span> <span data-ttu-id="ad509-140">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ad509-140">For example:</span></span>

[!code-csharp[lifted operators](snippets/shared/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> <span data-ttu-id="ad509-141">`bool?` 型の場合、定義済みの `&` および `|` 演算子は、このセクションで説明されている規則に従わないことに注意してください。オペランドの 1 つが `null` の場合も、演算子の評価の結果は null 以外である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ad509-141">For the `bool?` type, the predefined `&` and `|` operators don't follow the rules described in this section: the result of an operator evaluation can be non-null even if one of the operands is `null`.</span></span> <span data-ttu-id="ad509-142">詳細については、「[Boolean logical operators (ブール論理演算子)](../operators/boolean-logical-operators.md)」記事の「[Nullable Boolean logical operators (null 許容論理演算子)](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad509-142">For more information, see the [Nullable Boolean logical operators](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](../operators/boolean-logical-operators.md) article.</span></span>

<span data-ttu-id="ad509-143">[比較演算子](../operators/comparison-operators.md) `<`、`>`、`<=`、`>=` では、一方または両方のオペランドが `null` の場合、結果は `false` になります。それ以外の場合は、オペランドに含まれる値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-143">For the [comparison operators](../operators/comparison-operators.md) `<`, `>`, `<=`, and `>=`, if one or both operands are `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span> <span data-ttu-id="ad509-144">ある比較 (たとえば、`<=`) から返される結果が `false` であっても、逆の比較 (`>`) から返される結果が `true` であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ad509-144">Do not assume that because a particular comparison (for example, `<=`) returns `false`, the opposite comparison (`>`) returns `true`.</span></span> <span data-ttu-id="ad509-145">次の例は、10 が</span><span class="sxs-lookup"><span data-stu-id="ad509-145">The following example shows that 10 is</span></span>

- <span data-ttu-id="ad509-146">`null` 以上ではなく</span><span class="sxs-lookup"><span data-stu-id="ad509-146">neither greater than or equal to `null`</span></span>
- <span data-ttu-id="ad509-147">`null` 未満でもないことを示します</span><span class="sxs-lookup"><span data-stu-id="ad509-147">nor less than `null`</span></span>

[!code-csharp-interactive[relational and equality operators](snippets/shared/NullableValueTypes.cs#ComparisonOperators)]

<span data-ttu-id="ad509-148">[等値演算子](../operators/equality-operators.md#equality-operator-) `==` では、両方のオペランドが `null` の場合、結果は `true` になります。一方のオペランドだけが `null` の場合、結果は `false` です。それ以外の場合は、オペランドに含まれる値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-148">For the [equality operator](../operators/equality-operators.md#equality-operator-) `==`, if both operands are `null`, the result is `true`, if only one of the operands is `null`, the result is `false`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="ad509-149">[非等値演算子](../operators/equality-operators.md#inequality-operator-) `!=` では、両方のオペランドが `null` の場合、結果は `false` になります。一方のオペランドだけが `null` の場合、結果は `true` です。それ以外の場合は、オペランドに含まれる値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-149">For the [inequality operator](../operators/equality-operators.md#inequality-operator-) `!=`, if both operands are `null`, the result is `false`, if only one of the operands is `null`, the result is `true`; otherwise, the contained values of operands are compared.</span></span>

<span data-ttu-id="ad509-150">2 つの値型の間に[ユーザー定義の変換](../operators/user-defined-conversion-operators.md)が存在する場合は、それに対応する null 許容値型間でも同じ変換を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ad509-150">If there exists a [user-defined conversion](../operators/user-defined-conversion-operators.md) between two value types, the same conversion can also be used between the corresponding nullable value types.</span></span>

## <a name="boxing-and-unboxing"></a><span data-ttu-id="ad509-151">ボックス化とボックス化解除</span><span class="sxs-lookup"><span data-stu-id="ad509-151">Boxing and unboxing</span></span>

<span data-ttu-id="ad509-152">null 許容値型のインスタンス `T?` は、次のように[ボックス化](../../programming-guide/types/boxing-and-unboxing.md)されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-152">An instance of a nullable value type `T?` is [boxed](../../programming-guide/types/boxing-and-unboxing.md) as follows:</span></span>

- <span data-ttu-id="ad509-153"><xref:System.Nullable%601.HasValue%2A> が `false` を返した場合は、null 参照が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-153">If <xref:System.Nullable%601.HasValue%2A> returns `false`, the null reference is produced.</span></span>
- <span data-ttu-id="ad509-154"><xref:System.Nullable%601.HasValue%2A> が `true`を返した場合は、<xref:System.Nullable%601> のインスタンスではなく、基になる値型 `T` の対応する値がボックス化されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-154">If <xref:System.Nullable%601.HasValue%2A> returns `true`, the corresponding value of the underlying value type `T` is boxed, not the instance of <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="ad509-155">次の例に示すように、値型 `T` のボックス化された値を、対応する null 許容値型 `T?` にボックス化解除できます。</span><span class="sxs-lookup"><span data-stu-id="ad509-155">You can unbox a boxed value of a value type `T` to the corresponding nullable value type `T?`, as the following example shows:</span></span>

[!code-csharp-interactive[boxing and unboxing](snippets/shared/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a><span data-ttu-id="ad509-156">方法: null 許容値型を識別する</span><span class="sxs-lookup"><span data-stu-id="ad509-156">How to identify a nullable value type</span></span>

<span data-ttu-id="ad509-157">次の例は、<xref:System.Type?displayProperty=nameWithType> インスタンスが構築された null 許容値型 (つまり、指定された型パラメーター `T` を使用する <xref:System.Nullable%601?displayProperty=nameWithType> 型) を表すかどうかを判断する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="ad509-157">The following example shows how to determine whether a <xref:System.Type?displayProperty=nameWithType> instance represents a constructed nullable value type, that is, the <xref:System.Nullable%601?displayProperty=nameWithType> type with a specified type parameter `T`:</span></span>

[!code-csharp-interactive[whether Type is nullable](snippets/shared/NullableValueTypes.cs#IsTypeNullable)]

<span data-ttu-id="ad509-158">例で示されているとおり、<xref:System.Type?displayProperty=nameWithType> インスタンスの作成には、[typeof](../operators/type-testing-and-cast.md#typeof-operator) 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="ad509-158">As the example shows, you use the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator to create a <xref:System.Type?displayProperty=nameWithType> instance.</span></span>

<span data-ttu-id="ad509-159">インスタンスが null 許容値型かどうかを判断したい場合は、<xref:System.Type> インスタンスが前述のコードでテストされるように、<xref:System.Object.GetType%2A?displayProperty=nameWithType> メソッドは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ad509-159">If you want to determine whether an instance is of a nullable value type, don't use the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method to get a <xref:System.Type> instance to be tested with the preceding code.</span></span> <span data-ttu-id="ad509-160">null 許容値型のインスタンスで <xref:System.Object.GetType%2A?displayProperty=nameWithType> メソッドを呼び出した場合、そのインスタンスは <xref:System.Object> に[ボクシング](#boxing-and-unboxing)されます。</span><span class="sxs-lookup"><span data-stu-id="ad509-160">When you call the <xref:System.Object.GetType%2A?displayProperty=nameWithType> method on an instance of a nullable value type, the instance is [boxed](#boxing-and-unboxing) to <xref:System.Object>.</span></span> <span data-ttu-id="ad509-161">null 許容値型の null 以外のインスタンスのボックス化は、基になる型の値のボックス化と等しいので、<xref:System.Object.GetType%2A> は、null 許容値型の基になる型を表す <xref:System.Type> インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="ad509-161">As boxing of a non-null instance of a nullable value type is equivalent to boxing of a value of the underlying type, <xref:System.Object.GetType%2A> returns a <xref:System.Type> instance that represents the underlying type of a nullable value type:</span></span>

[!code-csharp-interactive[GetType example](snippets/shared/NullableValueTypes.cs#GetType)]

<span data-ttu-id="ad509-162">また、インスタンスが null 許容値型であるかどうかを判断するために、[is](../operators/type-testing-and-cast.md#is-operator) 演算子を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ad509-162">Also, don't use the [is](../operators/type-testing-and-cast.md#is-operator) operator to determine whether an instance is of a nullable value type.</span></span> <span data-ttu-id="ad509-163">次の例に示すように、`is` 演算子を使用して null 許容値型のインスタンスとその基になる型のインスタンスの型を区別することはできません。</span><span class="sxs-lookup"><span data-stu-id="ad509-163">As the following example shows, you cannot distinguish types of a nullable value type instance and its underlying type instance with the `is` operator:</span></span>

[!code-csharp-interactive[is operator example](snippets/shared/NullableValueTypes.cs#IsOperator)]

<span data-ttu-id="ad509-164">次の例のコードを使用すると、インスタンスが null 許容値型であるかどうかを判別することができます。</span><span class="sxs-lookup"><span data-stu-id="ad509-164">You can use the code presented in the following example to determine whether an instance is of a nullable value type:</span></span>

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/shared/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> <span data-ttu-id="ad509-165">このセクションで説明されているメソッドは、[null 許容参照型](nullable-reference-types.md)の場合には適用されません。</span><span class="sxs-lookup"><span data-stu-id="ad509-165">The methods described in this section are not applicable in the case of [nullable reference types](nullable-reference-types.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ad509-166">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ad509-166">C# language specification</span></span>

<span data-ttu-id="ad509-167">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad509-167">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="ad509-168">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="ad509-168">Nullable types</span></span>](~/_csharplang/spec/types.md#nullable-types)
- [<span data-ttu-id="ad509-169">リフト演算子</span><span class="sxs-lookup"><span data-stu-id="ad509-169">Lifted operators</span></span>](~/_csharplang/spec/expressions.md#lifted-operators)
- [<span data-ttu-id="ad509-170">暗黙の null 許容変換</span><span class="sxs-lookup"><span data-stu-id="ad509-170">Implicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [<span data-ttu-id="ad509-171">明示的な null 許容変換</span><span class="sxs-lookup"><span data-stu-id="ad509-171">Explicit nullable conversions</span></span>](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [<span data-ttu-id="ad509-172">リフト変換演算子</span><span class="sxs-lookup"><span data-stu-id="ad509-172">Lifted conversion operators</span></span>](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a><span data-ttu-id="ad509-173">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad509-173">See also</span></span>

- [<span data-ttu-id="ad509-174">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ad509-174">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ad509-175">What Exactly Does 'Lifted' mean? ('Lifted' の正確な意味)</span><span class="sxs-lookup"><span data-stu-id="ad509-175">What exactly does 'lifted' mean?</span></span>](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ad509-176">Null 許容参照型</span><span class="sxs-lookup"><span data-stu-id="ad509-176">Nullable reference types</span></span>](nullable-reference-types.md)
