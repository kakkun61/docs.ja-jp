---
title: タプル型 - C# リファレンス
description: 'C# のタプルについて学習する: 関連性の低いデータ要素をグループ化するために使用できる軽量データ構造'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: d996c7afecba1b58bfd8337fa444fd71790dd482
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471773"
---
# <a name="tuple-types-c-reference"></a><span data-ttu-id="80f57-103">タプル型 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="80f57-103">Tuple types (C# reference)</span></span>

<span data-ttu-id="80f57-104">C# 7.0 以降で利用できる " *タプル* " 機能により、軽量データ構造に複数のデータ要素をグループ化するための簡潔な構文が提供されています。</span><span class="sxs-lookup"><span data-stu-id="80f57-104">Available in C# 7.0 and later, the *tuples* feature provides concise syntax to group multiple data elements in a lightweight data structure.</span></span> <span data-ttu-id="80f57-105">次の例は、タプル変数を宣言して初期化し、そのデータ メンバーにアクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="80f57-105">The following example shows how you can declare a tuple variable, initialize it, and access its data members:</span></span>

[!code-csharp-interactive[tuple intro](snippets/shared/ValueTuples.cs#Introduction)]

<span data-ttu-id="80f57-106">前の例で示したように、タプル型を定義するには、すべてのデータ メンバーの型と、必要に応じて[フィールド名](#tuple-field-names)を指定します。</span><span class="sxs-lookup"><span data-stu-id="80f57-106">As the preceding example shows, to define a tuple type, you specify types of all its data members and, optionally, the [field names](#tuple-field-names).</span></span> <span data-ttu-id="80f57-107">タプル型でメソッドを定義することはできませんが、次の例に示すように、.NET によって提供されるメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="80f57-107">You cannot define methods in a tuple type, but you can use the methods provided by .NET, as the following example shows:</span></span>

[!code-csharp-interactive[tuple methods](snippets/shared/ValueTuples.cs#MethodOnTuples)]

<span data-ttu-id="80f57-108">C# 7.3 以降では、タプル型で[等値演算子](../operators/equality-operators.md) `==` と `!=` がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="80f57-108">Beginning with C# 7.3, tuple types support [equality operators](../operators/equality-operators.md) `==` and `!=`.</span></span> <span data-ttu-id="80f57-109">詳しくは、「[タプルの等値性](#tuple-equality)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80f57-109">For more information, see the [Tuple equality](#tuple-equality) section.</span></span>

<span data-ttu-id="80f57-110">タプル型は[値型](value-types.md)であり、タプル要素はパブリック フィールドです。</span><span class="sxs-lookup"><span data-stu-id="80f57-110">Tuple types are [value types](value-types.md); tuple elements are public fields.</span></span> <span data-ttu-id="80f57-111">そのため、タプルは " *変更可能な* " 値の型になります。</span><span class="sxs-lookup"><span data-stu-id="80f57-111">That makes tuples *mutable* value types.</span></span>

> [!NOTE]
> <span data-ttu-id="80f57-112">タプルの機能には、<xref:System.ValueTuple?displayProperty=nameWithType> 型と、.NET Core と .NET Framework 4.7 以降で使用できる、関連のジェネリック型 (たとえば、<xref:System.ValueTuple%602?displayProperty=nameWithType>) が必要です。</span><span class="sxs-lookup"><span data-stu-id="80f57-112">The tuples feature requires the <xref:System.ValueTuple?displayProperty=nameWithType> type and related generic types (for example, <xref:System.ValueTuple%602?displayProperty=nameWithType>), which are available in .NET Core and .NET Framework 4.7 and later.</span></span> <span data-ttu-id="80f57-113">4\.6.2 以前の .NET Framework を対象とするプロジェクトでタプルを使用するには、NuGet パッケージ [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) をプロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="80f57-113">To use tuples in a project that targets .NET Framework 4.6.2 or earlier, add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) to the project.</span></span>

<span data-ttu-id="80f57-114">任意の多数の要素を持つタプルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="80f57-114">You can define tuples with an arbitrary large number of elements:</span></span>

[!code-csharp-interactive[large tuple](snippets/shared/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a><span data-ttu-id="80f57-115">タプルのユース ケース</span><span class="sxs-lookup"><span data-stu-id="80f57-115">Use cases of tuples</span></span>

<span data-ttu-id="80f57-116">特に一般的なタプルのユース ケースの 1 つが、メソッドの戻り値の型です。</span><span class="sxs-lookup"><span data-stu-id="80f57-116">One of the most common use cases of tuples is as a method return type.</span></span> <span data-ttu-id="80f57-117">つまり、[`out` メソッド パラメーター](../keywords/out-parameter-modifier.md)を定義するのではなく、次の例のようにメソッドの結果をタプルの戻り値の型でグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="80f57-117">That is, instead of defining [`out` method parameters](../keywords/out-parameter-modifier.md), you can group method results in a tuple return type, as the following example shows:</span></span>

[!code-csharp-interactive[multiple method outputs](snippets/shared/ValueTuples.cs#MultipleReturns)]

<span data-ttu-id="80f57-118">前の例で示したように、返されたタプルのインスタンスを直接操作することも、別の変数に[分解する](#tuple-assignment-and-deconstruction)こともできます。</span><span class="sxs-lookup"><span data-stu-id="80f57-118">As the preceding example shows, you can work with the returned tuple instance directly or [deconstruct](#tuple-assignment-and-deconstruction) it in separate variables.</span></span>

<span data-ttu-id="80f57-119">タプル型は[匿名型](../../programming-guide/classes-and-structs/anonymous-types.md)の代わりに、たとえば LINQ クエリで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="80f57-119">You can also use tuple types instead of [anonymous types](../../programming-guide/classes-and-structs/anonymous-types.md); for example, in LINQ queries.</span></span> <span data-ttu-id="80f57-120">詳細については、「[匿名型またはタプル型の選択](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80f57-120">For more information, see [Choosing between anonymous and tuple types](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).</span></span>

<span data-ttu-id="80f57-121">通常、タプルは関連性の低いデータ要素をグループ化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="80f57-121">Typically, you use tuples to group loosely related data elements.</span></span> <span data-ttu-id="80f57-122">これは通常、非公開および内部のユーティリティ メソッド内で役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="80f57-122">That is usually useful within private and internal utility methods.</span></span> <span data-ttu-id="80f57-123">パブリック API の場合は、[クラス](../keywords/class.md)または[構造体](struct.md)型を定義することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="80f57-123">In the case of public API, consider defining a [class](../keywords/class.md) or a [structure](struct.md) type.</span></span>

## <a name="tuple-field-names"></a><span data-ttu-id="80f57-124">タプルのフィールド名</span><span class="sxs-lookup"><span data-stu-id="80f57-124">Tuple field names</span></span>

<span data-ttu-id="80f57-125">次の例に示すように、タプルの初期化式またはタプルの型の定義でタプル フィールドの名前を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="80f57-125">You can explicitly specify the names of tuple fields either in a tuple initialization expression or in the definition of a tuple type, as the following example shows:</span></span>

[!code-csharp-interactive[explicit field names](snippets/shared/ValueTuples.cs#ExplicitFieldNames)]

<span data-ttu-id="80f57-126">C# 7.1 以降では、フィールド名を指定しない場合、次の例に示すように、タプルの初期化式で対応する変数の名前からそれが推論される場合があります。</span><span class="sxs-lookup"><span data-stu-id="80f57-126">Beginning with C# 7.1, if you don't specify a field name, it may be inferred from the name of the corresponding variable in a tuple initialization expression, as the following example shows:</span></span>

[!code-csharp-interactive[inferred field names](snippets/shared/ValueTuples.cs#InferFieldNames)]

<span data-ttu-id="80f57-127">これはタプル プロジェクション初期化子と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="80f57-127">That's known as tuple projection initializers.</span></span> <span data-ttu-id="80f57-128">変数の名前は、次の場合、タプル フィールド名に投影されません。</span><span class="sxs-lookup"><span data-stu-id="80f57-128">The name of a variable isn't projected onto a tuple field name in the following cases:</span></span>

- <span data-ttu-id="80f57-129">候補名が `Item3`、`ToString`、`Rest` などのタプル型のメンバー名である。</span><span class="sxs-lookup"><span data-stu-id="80f57-129">The candidate name is a member name of a tuple type, for example, `Item3`, `ToString`, or `Rest`.</span></span>
- <span data-ttu-id="80f57-130">候補名が、別のタプル フィールド名 (明示的または暗黙的のいずれか) の複製である。</span><span class="sxs-lookup"><span data-stu-id="80f57-130">The candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="80f57-131">このような場合は、フィールドの名前を明示的に指定するか、既定の名前でフィールドにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="80f57-131">In those cases you either explicitly specify the name of a field or access a field by its default name.</span></span>

<span data-ttu-id="80f57-132">タプル フィールドの既定の名前は、`Item1`、`Item2`、`Item3` などです。</span><span class="sxs-lookup"><span data-stu-id="80f57-132">The default names of tuple fields are `Item1`, `Item2`, `Item3` and so on.</span></span> <span data-ttu-id="80f57-133">次の例に示すように、フィールド名が明示的に指定されていたり推論されていたりする場合でも、フィールドの既定の名前をいつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="80f57-133">You can always use the default name of a field, even when a field name is specified explicitly or inferred, as the following example shows:</span></span>

[!code-csharp-interactive[default field names](snippets/shared/ValueTuples.cs#DefaultFieldNames)]

<span data-ttu-id="80f57-134">[タプルの代入](#tuple-assignment-and-deconstruction)と[タプルの等価比較](#tuple-equality)では、フィールド名が考慮されません。</span><span class="sxs-lookup"><span data-stu-id="80f57-134">[Tuple assignment](#tuple-assignment-and-deconstruction) and [tuple equality comparisons](#tuple-equality) don't take field names into account.</span></span>

<span data-ttu-id="80f57-135">コンパイル時に、コンパイラは既定以外のフィールド名を、対応する既定の名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="80f57-135">At compile time, the compiler replaces non-default field names with the corresponding default names.</span></span> <span data-ttu-id="80f57-136">このため、明示的に指定された、または推論されたフィールド名は実行時に使用できません。</span><span class="sxs-lookup"><span data-stu-id="80f57-136">As a result, explicitly specified or inferred field names aren't available at run time.</span></span>

## <a name="tuple-assignment-and-deconstruction"></a><span data-ttu-id="80f57-137">タプルの代入と分解</span><span class="sxs-lookup"><span data-stu-id="80f57-137">Tuple assignment and deconstruction</span></span>

<span data-ttu-id="80f57-138">C# では、次の両方の条件を満たすタプル型間の代入がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="80f57-138">C# supports assignment between tuple types that satisfy both of the following conditions:</span></span>

- <span data-ttu-id="80f57-139">両方のタプル型に、同じ数の要素がある</span><span class="sxs-lookup"><span data-stu-id="80f57-139">both tuple types have the same number of elements</span></span>
- <span data-ttu-id="80f57-140">タプルのそれぞれの位置で、右側のタプル要素の型が対応する左側のタプル要素の型と同じか、暗黙的に変換可能である</span><span class="sxs-lookup"><span data-stu-id="80f57-140">for each tuple position, the type of the right-hand tuple element is the same as or implicitly convertible to the type of the corresponding left-hand tuple element</span></span>

<span data-ttu-id="80f57-141">タプル要素の値は、タプル要素の順序に従って代入されます。</span><span class="sxs-lookup"><span data-stu-id="80f57-141">Tuple element values are assigned following the order of tuple elements.</span></span> <span data-ttu-id="80f57-142">次の例に示すように、タプル フィールドの名前は無視され、代入されません。</span><span class="sxs-lookup"><span data-stu-id="80f57-142">The names of tuple fields are ignored and not assigned, as the following example shows:</span></span>

[!code-csharp-interactive[tuple assignment](snippets/shared/ValueTuples.cs#Assignment)]

<span data-ttu-id="80f57-143">また、代入演算子 `=` を使用して、別の変数でタプル インスタンスを " *分解する* " こともできます。</span><span class="sxs-lookup"><span data-stu-id="80f57-143">You can also use the assignment operator `=` to *deconstruct* a tuple instance in separate variables.</span></span> <span data-ttu-id="80f57-144">これは、次の方法のいずれかで実行できます。</span><span class="sxs-lookup"><span data-stu-id="80f57-144">You can do that in one of the following ways:</span></span>

- <span data-ttu-id="80f57-145">かっこ内の各変数の型を明示的に宣言する。</span><span class="sxs-lookup"><span data-stu-id="80f57-145">Explicitly declare the type of each variable inside parentheses:</span></span>

  [!code-csharp-interactive[specify types of variables](snippets/shared/ValueTuples.cs#DeconstructExplicit)]

- <span data-ttu-id="80f57-146">かっこの外にある `var` キーワードを使用して、暗黙的に型指定された変数を宣言し、コンパイラによってその型が推論されるようにする。</span><span class="sxs-lookup"><span data-stu-id="80f57-146">Use the `var` keyword outside the parentheses to declare implicitly typed variables and let the compiler infer their types:</span></span>

  [!code-csharp-interactive[implicitly typed variables](snippets/shared/ValueTuples.cs#DeconstructVar)]

- <span data-ttu-id="80f57-147">既存の変数を使用する。</span><span class="sxs-lookup"><span data-stu-id="80f57-147">Use existing variables:</span></span>

  [!code-csharp-interactive[existing variables](snippets/shared/ValueTuples.cs#DeconstructExisting)]

<span data-ttu-id="80f57-148">タプルとその他の型の分解の詳細については、「[タプルとその他の型の分解](../../deconstruct.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80f57-148">For more information about deconstruction of tuples and other types, see [Deconstructing tuples and other types](../../deconstruct.md).</span></span>

## <a name="tuple-equality"></a><span data-ttu-id="80f57-149">タプルの等値性</span><span class="sxs-lookup"><span data-stu-id="80f57-149">Tuple equality</span></span>

<span data-ttu-id="80f57-150">C# 7.3 以降では、タプル型で `==` および `!=` 演算子がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="80f57-150">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="80f57-151">これらの演算子により、左側のオペランドのメンバーが、タプル要素の順序に従って、右側のオペランドの対応するメンバーと比較されます。</span><span class="sxs-lookup"><span data-stu-id="80f57-151">These operators compare members of the left-hand operand with the corresponding members of the right-hand operand following the order of tuple elements.</span></span>

[!code-csharp-interactive[tuple equality](snippets/shared/ValueTuples.cs#TupleEquality)]

<span data-ttu-id="80f57-152">前の例で示したように、`==` と `!=` の演算では、タプルのフィールド名は考慮されません。</span><span class="sxs-lookup"><span data-stu-id="80f57-152">As the preceding example shows, the `==` and `!=` operations don't take into account tuple field names.</span></span>

<span data-ttu-id="80f57-153">2 つのタプルは、次の両方の条件が満たされている場合に比較できます。</span><span class="sxs-lookup"><span data-stu-id="80f57-153">Two tuples are comparable when both of the following conditions are satisfied:</span></span>

- <span data-ttu-id="80f57-154">両方のタプルが、同じ数の要素を保持している。</span><span class="sxs-lookup"><span data-stu-id="80f57-154">Both tuples have the same number of elements.</span></span> <span data-ttu-id="80f57-155">たとえば、`t1` と `t2` の要素数が異なる場合、`t1 != t2` はコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="80f57-155">For example, `t1 != t2` doesn't compile if `t1` and `t2` have different numbers of elements.</span></span>
- <span data-ttu-id="80f57-156">タプルの位置ごとに、左側と右側のタプルのオペランドの対応する要素が、`==` と `!=` の演算子と比較されます。</span><span class="sxs-lookup"><span data-stu-id="80f57-156">For each tuple position, the corresponding elements from the left-hand and right-hand tuple operands are comparable with the `==` and `!=` operators.</span></span> <span data-ttu-id="80f57-157">たとえば、`1` は `(1, 2)` と比較できないため、`(1, (2, 3)) == ((1, 2), 3)` はコンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="80f57-157">For example, `(1, (2, 3)) == ((1, 2), 3)` doesn't compile because `1` is not comparable with `(1, 2)`.</span></span>

<span data-ttu-id="80f57-158">`==` と `!=` の演算子によって、タプルがショートサーキット方式で比較されます。</span><span class="sxs-lookup"><span data-stu-id="80f57-158">The `==` and `!=` operators compare tuples in short-circuiting way.</span></span> <span data-ttu-id="80f57-159">つまり、等しくない要素のペアか、タプルの端に到達するとすぐに、演算が停止します。</span><span class="sxs-lookup"><span data-stu-id="80f57-159">That is, an operation stops as soon as it meets a pair of non equal elements or reaches the ends of tuples.</span></span> <span data-ttu-id="80f57-160">ただし、比較の前には必ず、次の例に示すように、" *すべての* " タプル要素が評価されます。</span><span class="sxs-lookup"><span data-stu-id="80f57-160">However, before any comparison, *all* tuple elements are evaluated, as the following example shows:</span></span>

[!code-csharp-interactive[tuple element evaluation](snippets/shared/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="80f57-161">out パラメーターとしてのタプル</span><span class="sxs-lookup"><span data-stu-id="80f57-161">Tuples as out parameters</span></span>

<span data-ttu-id="80f57-162">通常は、[`out` パラメーター](../keywords/out-parameter-modifier.md)を持つメソッドを、タプルを返すメソッドにリファクタリングします。</span><span class="sxs-lookup"><span data-stu-id="80f57-162">Typically, you refactor a method that has [`out` parameters](../keywords/out-parameter-modifier.md) into a method that returns a tuple.</span></span> <span data-ttu-id="80f57-163">ただし、`out` パラメーターがタプル型である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="80f57-163">However, there are cases in which an `out` parameter can be of a tuple type.</span></span> <span data-ttu-id="80f57-164">次の例に、`out` パラメーターとしてタプルを操作する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="80f57-164">The following example shows how to work with tuples as `out` parameters:</span></span>

[!code-csharp-interactive[tuple as out parameter](snippets/shared/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a><span data-ttu-id="80f57-165">タプルと `System.Tuple`</span><span class="sxs-lookup"><span data-stu-id="80f57-165">Tuples vs `System.Tuple`</span></span>

<span data-ttu-id="80f57-166"><xref:System.ValueTuple?displayProperty=nameWithType> 型によってサポートされる C# のタプルは、<xref:System.Tuple?displayProperty=nameWithType> タプルで表されるタプルとは異なります。</span><span class="sxs-lookup"><span data-stu-id="80f57-166">C# tuples, which are backed by <xref:System.ValueTuple?displayProperty=nameWithType> types, are different from tuples that are represented by <xref:System.Tuple?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="80f57-167">主な相違点は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="80f57-167">The main differences are as follows:</span></span>

- <span data-ttu-id="80f57-168">`ValueTuple` 型は[値の型](value-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="80f57-168">`ValueTuple` types are [value types](value-types.md).</span></span> <span data-ttu-id="80f57-169">`Tuple` 型は[参照型](../keywords/reference-types.md)です。</span><span class="sxs-lookup"><span data-stu-id="80f57-169">`Tuple` types are [reference types](../keywords/reference-types.md).</span></span>
- <span data-ttu-id="80f57-170">`ValueTuple` 型は変更可能です。</span><span class="sxs-lookup"><span data-stu-id="80f57-170">`ValueTuple` types are mutable.</span></span> <span data-ttu-id="80f57-171">`Tuple` 型は変更不可能です。</span><span class="sxs-lookup"><span data-stu-id="80f57-171">`Tuple` types are immutable.</span></span>
- <span data-ttu-id="80f57-172">`ValueTuple` 型のデータ メンバーはフィールドです。</span><span class="sxs-lookup"><span data-stu-id="80f57-172">Data members of `ValueTuple` types are fields.</span></span> <span data-ttu-id="80f57-173">`Tuple` 型のデータ メンバーはプロパティです。</span><span class="sxs-lookup"><span data-stu-id="80f57-173">Data members of `Tuple` types are properties.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="80f57-174">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="80f57-174">C# language specification</span></span>

<span data-ttu-id="80f57-175">詳しくは、次の機能提案メモをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="80f57-175">For more information, see the following feature proposal notes:</span></span>

- [<span data-ttu-id="80f57-176">タプル名 (別名タプル プロジェクション初期化子) を推測する</span><span class="sxs-lookup"><span data-stu-id="80f57-176">Infer tuple names (aka. tuple projection initializers)</span></span>](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [<span data-ttu-id="80f57-177">タプル型での `==` と `!=` のサポート</span><span class="sxs-lookup"><span data-stu-id="80f57-177">Support for `==` and `!=` on tuple types</span></span>](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a><span data-ttu-id="80f57-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="80f57-178">See also</span></span>

- [<span data-ttu-id="80f57-179">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="80f57-179">C# reference</span></span>](../index.md)
- [<span data-ttu-id="80f57-180">値型</span><span class="sxs-lookup"><span data-stu-id="80f57-180">Value types</span></span>](value-types.md)
- [<span data-ttu-id="80f57-181">匿名型またはタプル型の選択</span><span class="sxs-lookup"><span data-stu-id="80f57-181">Choosing between anonymous and tuple types</span></span>](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>
