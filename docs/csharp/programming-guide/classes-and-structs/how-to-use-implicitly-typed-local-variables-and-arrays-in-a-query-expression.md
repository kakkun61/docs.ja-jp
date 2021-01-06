---
title: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する方法 - C# プログラミング ガイド
description: コンパイラでローカル変数の型を決定できるようにするには、C# で暗黙的に型指定されたローカル変数を使用します。 匿名型を格納するには、これらを使用する必要があります。
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: bd68c913c6f0d410d97973fb28789218f88903b5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512386"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a><span data-ttu-id="88b63-104">クエリ式で暗黙的に型指定されるローカル変数および配列を使用する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="88b63-104">How to use implicitly typed local variables and arrays in a query expression (C# Programming Guide)</span></span>

<span data-ttu-id="88b63-105">コンパイラによってローカル変数の型が決定されるようにする場合は、暗黙的に型指定されたローカル変数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="88b63-105">You can use implicitly typed local variables whenever you want the compiler to determine the type of a local variable.</span></span> <span data-ttu-id="88b63-106">クエリ式でよく使用する匿名型を格納するには、暗黙的に型指定されたローカル変数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88b63-106">You must use implicitly typed local variables to store anonymous types, which are often used in query expressions.</span></span> <span data-ttu-id="88b63-107">以下の例では、クエリで暗黙的に型指定されたローカル変数を省略できる場合と、使用しなければならない場合の両方を示します。</span><span class="sxs-lookup"><span data-stu-id="88b63-107">The following examples illustrate both optional and required uses of implicitly typed local variables in queries.</span></span>  
  
 <span data-ttu-id="88b63-108">暗黙的に型指定されたローカル変数は、[var](../../language-reference/keywords/var.md) コンテキスト キーワードを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="88b63-108">Implicitly typed local variables are declared by using the [var](../../language-reference/keywords/var.md) contextual keyword.</span></span> <span data-ttu-id="88b63-109">詳細については、「[暗黙的に型指定されるローカル変数](./implicitly-typed-local-variables.md)」と「[暗黙的に型指定される配列](../arrays/implicitly-typed-arrays.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88b63-109">For more information, see [Implicitly Typed Local Variables](./implicitly-typed-local-variables.md) and [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b63-110">例</span><span class="sxs-lookup"><span data-stu-id="88b63-110">Example</span></span>  

 <span data-ttu-id="88b63-111">次の例は、`var` キーワードが必須である一般的なシナリオ (匿名型のシーケンスを生成するクエリ) を示しています。</span><span class="sxs-lookup"><span data-stu-id="88b63-111">The following example shows a common scenario in which the `var` keyword is required: a query expression that produces a sequence of anonymous types.</span></span> <span data-ttu-id="88b63-112">このシナリオでは、匿名型の型名にアクセスできないため、`var`を使用して `foreach` ステートメントのクエリ変数と反復変数の両方を暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="88b63-112">In this scenario, both the query variable and the iteration variable in the `foreach` statement must be implicitly typed by using `var` because you do not have access to a type name for the anonymous type.</span></span> <span data-ttu-id="88b63-113">匿名型の詳細については、「[匿名型](./anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88b63-113">For more information about anonymous types, see [Anonymous Types](./anonymous-types.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="88b63-114">例</span><span class="sxs-lookup"><span data-stu-id="88b63-114">Example</span></span>  

 <span data-ttu-id="88b63-115">次の例では、同様の状況で `var` キーワードを使用しています。ただし、この場合、`var` の使用はオプションです。</span><span class="sxs-lookup"><span data-stu-id="88b63-115">The following example uses the `var` keyword in a situation that is similar, but in which the use of `var` is optional.</span></span> <span data-ttu-id="88b63-116">`student.LastName` は文字列であるため、クエリを実行すると文字列のシーケンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="88b63-116">Because `student.LastName` is a string, execution of the query returns a sequence of strings.</span></span> <span data-ttu-id="88b63-117">したがって、`queryID` の型は、`var` ではなく `System.Collections.Generic.IEnumerable<string>` として宣言できます。</span><span class="sxs-lookup"><span data-stu-id="88b63-117">Therefore, the type of `queryID` could be declared as `System.Collections.Generic.IEnumerable<string>` instead of `var`.</span></span> <span data-ttu-id="88b63-118">`var` キーワードは利便性のために使用されます。</span><span class="sxs-lookup"><span data-stu-id="88b63-118">Keyword `var` is used for convenience.</span></span> <span data-ttu-id="88b63-119">この例では、`foreach` ステートメントの反復変数は文字列として明示的に型指定されていますが、代わりに `var` を使用して宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="88b63-119">In the example, the iteration variable in the `foreach` statement is explicitly typed as a string, but it could instead be declared by using `var`.</span></span> <span data-ttu-id="88b63-120">反復変数の型は匿名型ではないため、`var` の使用はオプションであり、必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="88b63-120">Because the type of the iteration variable is not an anonymous type, the use of `var` is an option, not a requirement.</span></span> <span data-ttu-id="88b63-121">`var` 自体は型ではなく、型を推論して割り当てるようコンパイラに指示する命令です。</span><span class="sxs-lookup"><span data-stu-id="88b63-121">Remember, `var` itself is not a type, but an instruction to the compiler to infer and assign the type.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a><span data-ttu-id="88b63-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="88b63-122">See also</span></span>

- [<span data-ttu-id="88b63-123">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="88b63-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88b63-124">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="88b63-124">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="88b63-125">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="88b63-125">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="88b63-126">var</span><span class="sxs-lookup"><span data-stu-id="88b63-126">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="88b63-127">C# での LINQ</span><span class="sxs-lookup"><span data-stu-id="88b63-127">LINQ in C#</span></span>](../../linq/index.md)
