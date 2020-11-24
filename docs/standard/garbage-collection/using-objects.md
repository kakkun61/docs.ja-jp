---
title: IDisposable を実装するオブジェクトの使用
description: .NET で IDisposable インターフェイスを実装するオブジェクトを使用する方法について学習します。 アンマネージ リソースを使用する型は、リソースを再利用できるように IDisposable を実装します。
ms.date: 05/13/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 50769bdf684f6eb3a51dc2bd00c6a774a02976b7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827452"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="f6ca3-104">IDisposable を実装するオブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="f6ca3-104">Using objects that implement IDisposable</span></span>

<span data-ttu-id="f6ca3-105">共通言語ランタイムのガベージ コレクターは、アンマネージド オブジェクトによって使用されているメモリを解放しますが、アンマネージ リソースを使用する型は、これらのアンマネージ リソースで必要なリソースが再利用されるように <xref:System.IDisposable> インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-105">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the resources needed by these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="f6ca3-106"><xref:System.IDisposable> を実装するオブジェクトを使い終わったら、オブジェクトの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-106">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="f6ca3-107">2 つの方法のいずれかでこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-107">You can do this in one of two ways:</span></span>

- <span data-ttu-id="f6ca3-108">C# の `using` ステートメント (Visual Basic の `Using`)。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-108">With the C# `using` statement (`Using` in Visual Basic).</span></span>
- <span data-ttu-id="f6ca3-109">`try/finally` ブロックを実装し、`finally` で <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-109">By implementing a `try/finally` block, and calling the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> in the `finally`.</span></span>

## <a name="the-using-statement"></a><span data-ttu-id="f6ca3-110">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="f6ca3-110">The using statement</span></span>

<span data-ttu-id="f6ca3-111">C# の [`using` ステートメント](../../csharp/language-reference/keywords/using-statement.md)および Visual Basic の [`Using` ステートメント](../../visual-basic/language-reference/statements/using-statement.md)を使用すると、オブジェクトのクリーンアップ時に記述する必要のあるコードが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-111">The [`using` statement](../../csharp/language-reference/keywords/using-statement.md) in C# and the [`Using` statement](../../visual-basic/language-reference/statements/using-statement.md) in Visual Basic simplify the code that you must write to cleanup an object.</span></span> <span data-ttu-id="f6ca3-112">`using` ステートメントは、1 つ以上のリソースを取得し、指定されたステートメントを実行し、オブジェクトを自動的に破棄します。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-112">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="f6ca3-113">ただし、`using` ステートメントは、オブジェクトが構築されるメソッドのスコープ内で使用されるオブジェクトに対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-113">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>

<span data-ttu-id="f6ca3-114">次の例では、`using` ステートメントを使用して <xref:System.IO.StreamReader?displayProperty=nameWithType> オブジェクトを作成し解放します。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-114">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

<span data-ttu-id="f6ca3-115"><xref:System.IO.StreamReader> クラスは <xref:System.IDisposable> インターフェイスを実装し、これはアンマネージ リソースを使用することを示していますが、例では <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> メソッドを明示的に呼び出していません。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-115">Although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f6ca3-116">C# または Visual Basic コンパイラが `using` ステートメントを見つけると、明示的に `try/finally` ブロックを含む次のコードと同等の中間言語 (IL) を生成します。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-116">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

<span data-ttu-id="f6ca3-117">また、C# の `using` ステートメントでは、単一のステートメントで複数のリソースを取得できます。そのようなステートメントは、内部的には複数の `using` ステートメントを入れ子にした場合と同等です。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-117">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="f6ca3-118">次の例では、2 つの異なるファイルの内容を読み取るために、<xref:System.IO.StreamReader> の 2 つのオブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-118">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="f6ca3-119">Try/Finally ブロック</span><span class="sxs-lookup"><span data-stu-id="f6ca3-119">Try/finally block</span></span>

<span data-ttu-id="f6ca3-120">`using` ステートメントで `try/finally` ブロックをラップする代わりに、`try/finally` ブロックを直接実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-120">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="f6ca3-121">これは、個人のコーディング スタイルであることも、次のいずれかの理由からそうすることもあります。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-121">It may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>

- <span data-ttu-id="f6ca3-122">`catch` ブロックでスローされた例外を処理する `try` ブロックを含めるため。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-122">To include a `catch` block to handle exceptions thrown in the `try` block.</span></span> <span data-ttu-id="f6ca3-123">それ以外の場合、`using` ステートメント内でスローされた例外は処理されません。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-123">Otherwise, any exceptions thrown within the `using` statement are unhandled.</span></span>

- <span data-ttu-id="f6ca3-124">宣言されたブロックに対してスコープがローカルでない <xref:System.IDisposable> を実装するオブジェクトをインスタンス化するため。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-124">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>

<span data-ttu-id="f6ca3-125">次の例は前の例に似ていますが、`try/catch/finally` ブロックを使用して、<xref:System.IO.StreamReader> オブジェクトのインスタンス化、使用、破棄を実行し、<xref:System.IO.StreamReader> コンストラクターと <xref:System.IO.StreamReader.ReadToEnd%2A> メソッドによってスローされた例外を処理しています。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-125">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="f6ca3-126">`finally` メソッドを呼び出す前に <xref:System.IDisposable> を実装するオブジェクトが `null` でないことを <xref:System.IDisposable.Dispose%2A> ブロックのコードがチェックします。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-126">The code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="f6ca3-127">これを行わない場合、実行時に <xref:System.NullReferenceException> 例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-127">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

<span data-ttu-id="f6ca3-128">この基本パターンを利用できるのは、プログラミング言語で `using` ステートメントがサポートされていないが、<xref:System.IDisposable.Dispose%2A> メソッドを直接呼び出すことはできるため、`try/finally` ブロックの実装を選択した場合、または実装する必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-128">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>

## <a name="idisposable-instance-members"></a><span data-ttu-id="f6ca3-129">IDisposable インスタンス メンバー</span><span class="sxs-lookup"><span data-stu-id="f6ca3-129">IDisposable instance members</span></span>

<span data-ttu-id="f6ca3-130">クラスがインスタンス メンバーとして <xref:System.IDisposable> の実装 (フィールドまたはプロパティ) を保持している場合、クラスも <xref:System.IDisposable> を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-130">If a class holds an <xref:System.IDisposable> implementation as an instance member, either a field or a property, the class should also implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="f6ca3-131">詳細については、[カスケード破棄の実装に関する記事](implementing-dispose.md#cascade-dispose-calls)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f6ca3-131">For more information, see [implement a cascade dispose](implementing-dispose.md#cascade-dispose-calls).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6ca3-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="f6ca3-132">See also</span></span>

- [<span data-ttu-id="f6ca3-133">アンマネージ リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="f6ca3-133">Cleaning up unmanaged resources</span></span>](unmanaged.md)
- [<span data-ttu-id="f6ca3-134">using ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f6ca3-134">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="f6ca3-135">Using ステートメント (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6ca3-135">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
