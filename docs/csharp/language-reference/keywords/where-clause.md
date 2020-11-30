---
description: where 句 - C# リファレンス
title: where 句 - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 58a8dc226bb2720b6a8251f028712a80f74e893c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141687"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="9bb44-103">where 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="9bb44-103">where clause (C# Reference)</span></span>

<span data-ttu-id="9bb44-104">`where` 句をクエリ式で使用して、クエリ式で返されるデータ ソースの要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bb44-104">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="9bb44-105">ブール条件 (*述語*) を (範囲変数で参照される) 各ソース要素に適用し、指定した条件に該当するものを返します。</span><span class="sxs-lookup"><span data-stu-id="9bb44-105">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="9bb44-106">単一のクエリ式に複数の `where` 句を含めることができ、単一の句に複数の述語部分式を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9bb44-106">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="9bb44-107">例</span><span class="sxs-lookup"><span data-stu-id="9bb44-107">Example</span></span>

<span data-ttu-id="9bb44-108">次の例では、`where` 句で、5 未満の数値を除くすべての数値を除外します。</span><span class="sxs-lookup"><span data-stu-id="9bb44-108">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="9bb44-109">`where` 句を削除すると、データ ソースのすべての数値が返されます。</span><span class="sxs-lookup"><span data-stu-id="9bb44-109">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="9bb44-110">式 `num < 5` は、各要素に適用される述語です。</span><span class="sxs-lookup"><span data-stu-id="9bb44-110">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="9bb44-111">例</span><span class="sxs-lookup"><span data-stu-id="9bb44-111">Example</span></span>

<span data-ttu-id="9bb44-112">単一の `where` 句内には、[&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) および [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) 演算子を使用して、必要な数の述語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9bb44-112">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="9bb44-113">次の例のクエリでは、5 未満の偶数のみを選択するために 2 つの述語を指定します。</span><span class="sxs-lookup"><span data-stu-id="9bb44-113">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="9bb44-114">例</span><span class="sxs-lookup"><span data-stu-id="9bb44-114">Example</span></span>

<span data-ttu-id="9bb44-115">`where` 句には、ブール値を返す 1 つ以上のメソッドを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9bb44-115">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="9bb44-116">次の例の `where` 句では、範囲変数の現在の値が偶数であるか、奇数であるかを判断するためのメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9bb44-116">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="9bb44-117">注釈</span><span class="sxs-lookup"><span data-stu-id="9bb44-117">Remarks</span></span>

<span data-ttu-id="9bb44-118">`where` 句はフィルター メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="9bb44-118">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="9bb44-119">クエリ式のほぼどこにでも指定できますが、最初の句や最後の句にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9bb44-119">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="9bb44-120">`where` 句は、ソース要素のフィルター処理をグループ化の前に行うか後に行うかによって、[group](group-clause.md) 句の前または後に指定できます。</span><span class="sxs-lookup"><span data-stu-id="9bb44-120">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="9bb44-121">指定した述語がデータ ソース内の要素に対して有効でない場合は、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="9bb44-121">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="9bb44-122">これは、LINQ で提供される厳密な型チェックの 1 つの利点です。</span><span class="sxs-lookup"><span data-stu-id="9bb44-122">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="9bb44-123">コンパイル時に、`where` キーワードは <xref:System.Linq.Enumerable.Where%2A> 標準クエリ演算子メソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="9bb44-123">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="9bb44-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bb44-124">See also</span></span>

- [<span data-ttu-id="9bb44-125">クエリ キーワード (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9bb44-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="9bb44-126">from 句</span><span class="sxs-lookup"><span data-stu-id="9bb44-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="9bb44-127">select 句</span><span class="sxs-lookup"><span data-stu-id="9bb44-127">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="9bb44-128">データのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="9bb44-128">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="9bb44-129">C# での LINQ</span><span class="sxs-lookup"><span data-stu-id="9bb44-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="9bb44-130">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9bb44-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
