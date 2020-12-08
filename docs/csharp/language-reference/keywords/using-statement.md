---
description: using ステートメント - C# リファレンス
title: using ステートメント - C# リファレンス
ms.date: 05/29/2020
f1_keywords:
- using-statement_CSharpKeyword
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 451235d9d41565c35369700eeec75cfd2f5bfc06
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599331"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="58189-103">using ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="58189-103">using statement (C# Reference)</span></span>

<span data-ttu-id="58189-104"><xref:System.IDisposable> オブジェクトの正しい使用を保証する簡易構文を提供します。</span><span class="sxs-lookup"><span data-stu-id="58189-104">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="58189-105">C# 8.0 以降は、`using` ステートメントによって <xref:System.IAsyncDisposable> オブジェクトが適切に使用されるようになります。</span><span class="sxs-lookup"><span data-stu-id="58189-105">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="58189-106">例</span><span class="sxs-lookup"><span data-stu-id="58189-106">Example</span></span>

<span data-ttu-id="58189-107">`using` ステートメントを使用する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="58189-107">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="58189-108">C# 8.0 以降では、中かっこを必要としない `using` ステートメントに次の代替構文を使用できます。</span><span class="sxs-lookup"><span data-stu-id="58189-108">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="58189-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="58189-109">Remarks</span></span>

<span data-ttu-id="58189-110"><xref:System.IO.File> と <xref:System.Drawing.Font> は、アンマネージド リソース (この場合はファイル ハンドルとデバイス コンテキスト) にアクセスするマネージド型の例です。</span><span class="sxs-lookup"><span data-stu-id="58189-110"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="58189-111">アンマネージ リソースや、それをカプセル化するクラス ライブラリ型は他にもたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="58189-111">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="58189-112">このようなすべての型は、<xref:System.IDisposable> インターフェイスまたは <xref:System.IAsyncDisposable> インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58189-112">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="58189-113">`IDisposable` オブジェクトの有効期間が 1 つのメソッドに限定されているとき、それを `using` ステートメントで宣言し、インスタンス化してください。</span><span class="sxs-lookup"><span data-stu-id="58189-113">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="58189-114">`using` ステートメントは、オブジェクトで正しく <xref:System.IDisposable.Dispose%2A> メソッドを呼び出します。(前述のようにこのステートメントを使用する場合) <xref:System.IDisposable.Dispose%2A> が呼び出されるとすぐに、オブジェクト自体がスコープの外側に出されます。</span><span class="sxs-lookup"><span data-stu-id="58189-114">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="58189-115">オブジェクトは、`using` ブロック内では読み取り専用です。変更したり再割り当てしたりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="58189-115">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="58189-116">オブジェクトに `IDisposable` ではなく `IAsyncDisposable` が実装されている場合、`using` ステートメントからは <xref:System.IAsyncDisposable.DisposeAsync%2A> が呼び出され、返される <xref:System.Threading.Tasks.ValueTask> の `awaits` を行います。</span><span class="sxs-lookup"><span data-stu-id="58189-116">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.ValueTask>.</span></span> <span data-ttu-id="58189-117"><xref:System.IAsyncDisposable> の詳細については、「[DisposeAsync メソッドの実装](../../../standard/garbage-collection/implementing-disposeasync.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58189-117">For more information on <xref:System.IAsyncDisposable>, see [Implement a DisposeAsync method](../../../standard/garbage-collection/implementing-disposeasync.md).</span></span>

<span data-ttu-id="58189-118">`using` ステートメントにより、`using` ブロック内で例外が発生した場合でも必ず <xref:System.IDisposable.Dispose%2A> (または <xref:System.IAsyncDisposable.DisposeAsync%2A>) が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="58189-118">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="58189-119">オブジェクトを `try` ブロックに配置し、`finally` ブロック内で <xref:System.IDisposable.Dispose%2A> (または <xref:System.IAsyncDisposable.DisposeAsync%2A>) を呼び出しても、同じ結果が得られます。実際には、コンパイラによって `using` ステートメントがこのように変換されます。</span><span class="sxs-lookup"><span data-stu-id="58189-119">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="58189-120">前のコード例は、コンパイル時に次のコードに展開されます (オブジェクトのスコープ制限を定義する中かっこが加えられていることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="58189-120">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="58189-121">新しい `using` ステートメントの構文は似たコードに変換されます。</span><span class="sxs-lookup"><span data-stu-id="58189-121">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="58189-122">変数が宣言されている場所で `try` ブロックが開きます。</span><span class="sxs-lookup"><span data-stu-id="58189-122">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="58189-123">`finally` ブロックは、囲んでいるブロックの終わり、通常はメソッドの最後に追加されます。</span><span class="sxs-lookup"><span data-stu-id="58189-123">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="58189-124">`try`-`finally` ステートメントの詳細については、「[try-finally](try-finally.md)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58189-124">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="58189-125">次の例のように、1 つの `using` ステートメントで型の複数のインスタンスを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="58189-125">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="58189-126">1 つのステートメントで複数の変数を宣言する場合、暗黙的に型指定された変数 (`var`) を使用できないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="58189-126">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="58189-127">次の例に示すように、C# 8 で導入された新しい構文を使用して、同じ型の複数の宣言を組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="58189-127">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="58189-128">リソース オブジェクトをインスタンス化してから、変数を `using` ステートメントに渡すことはできますが、これはベスト プラクティスではありません。</span><span class="sxs-lookup"><span data-stu-id="58189-128">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="58189-129">この場合、アンマネージド リソースへのアクセスがなくなっている可能性が高いのにもかかわらず、制御が `using` ブロックを離れた後もオブジェクトはスコープ内に残ります。</span><span class="sxs-lookup"><span data-stu-id="58189-129">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="58189-130">つまり、完全に初期化されることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="58189-130">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="58189-131">`using` ブロックの外側でオブジェクトを使用しようとすると、例外がスローされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="58189-131">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="58189-132">このため、オブジェクトを `using` ステートメントでインスタンス化して、そのスコープを `using` ブロックに制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="58189-132">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="58189-133">`IDisposable` オブジェクトの破棄に関する詳細については、「[IDisposable を実装するオブジェクトの使用](../../../standard/garbage-collection/using-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58189-133">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="58189-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="58189-134">C# language specification</span></span>

<span data-ttu-id="58189-135">詳細については、[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)に関するページの [using ステートメント](~/_csharplang/spec/statements.md#the-using-statement)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="58189-135">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="58189-136">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="58189-136">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="58189-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="58189-137">See also</span></span>

- [<span data-ttu-id="58189-138">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="58189-138">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="58189-139">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="58189-139">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="58189-140">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="58189-140">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="58189-141">using ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="58189-141">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="58189-142">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="58189-142">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="58189-143">IDisposable を実装するオブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="58189-143">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="58189-144">IDisposable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="58189-144">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="58189-145">C# 8.0 の using ステートメント</span><span class="sxs-lookup"><span data-stu-id="58189-145">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
