---
title: 例外処理 - C# プログラミング ガイド
description: 例外処理について説明します。 try-catch、try-finally、および try-catch-finally ステートメントの例を確認してください。
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: fabf1413ba498232e67f45460195fe96e25fab0a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110196"
---
# <a name="exception-handling-c-programming-guide"></a><span data-ttu-id="bd88c-104">例外処理 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="bd88c-104">Exception Handling (C# Programming Guide)</span></span>

<span data-ttu-id="bd88c-105">[try](../../language-reference/keywords/try-catch.md) ブロックは、例外の影響を受ける可能性があるコードを区分化するために、 C# プログラマによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-105">A [try](../../language-reference/keywords/try-catch.md) block is used by C# programmers to partition code that might be affected by an exception.</span></span> <span data-ttu-id="bd88c-106">関連付けられた [catch](../../language-reference/keywords/try-catch.md) ブロックは、スローされた例外を処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-106">Associated [catch](../../language-reference/keywords/try-catch.md) blocks are used to handle any resulting exceptions.</span></span> <span data-ttu-id="bd88c-107">[finally](../../language-reference/keywords/try-finally.md) ブロックには、`try` ブロックで例外がスローされたかどうかにかかわらず実行されるコードが含まれます (`try` ブロックに割り当てられたリソースの解放など)。</span><span class="sxs-lookup"><span data-stu-id="bd88c-107">A [finally](../../language-reference/keywords/try-finally.md) block contains code that is run whether or not an exception is thrown in the `try` block, such as releasing resources that are allocated in the `try` block.</span></span> <span data-ttu-id="bd88c-108">`try` ブロックには、1 つ以上の `catch` ブロック、`finally` ブロック、またはその両方が関連付けられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd88c-108">A `try` block requires one or more associated `catch` blocks, or a `finally` block, or both.</span></span>

<span data-ttu-id="bd88c-109">次のコードは、`try-catch` ステートメント、`try-finally` ステートメント、および `try-catch-finally` ステートメントの例です。</span><span class="sxs-lookup"><span data-stu-id="bd88c-109">The following examples show a `try-catch` statement, a `try-finally` statement, and a `try-catch-finally` statement.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryFinallyStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchFinallyStructure":::

<span data-ttu-id="bd88c-110">`try` ブロックに `catch` または `finally` ブロックがない場合は、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="bd88c-110">A `try` block without a `catch` or `finally` block causes a compiler error.</span></span>

## <a name="catch-blocks"></a><span data-ttu-id="bd88c-111">catch ブロック</span><span class="sxs-lookup"><span data-stu-id="bd88c-111">Catch Blocks</span></span>

<span data-ttu-id="bd88c-112">`catch` ブロックでは、キャッチする例外の種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-112">A `catch` block can specify the type of exception to catch.</span></span> <span data-ttu-id="bd88c-113">この型指定は、*例外フィルター* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-113">The type specification is called an *exception filter*.</span></span> <span data-ttu-id="bd88c-114">例外の種類は、<xref:System.Exception> から派生している必要があります。</span><span class="sxs-lookup"><span data-stu-id="bd88c-114">The exception type should be derived from <xref:System.Exception>.</span></span> <span data-ttu-id="bd88c-115">一般に、`try` ブロックからスローされる可能性があるすべての例外の処理方法を把握している場合や、`catch` ブロックの末尾に [throw](../../language-reference/keywords/throw.md) ステートメントが含まれている場合を除いては、例外フィルターとして <xref:System.Exception> を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="bd88c-115">In general, don't specify <xref:System.Exception> as the exception filter unless either you know how to handle all exceptions that might be thrown in the `try` block, or you've included a [throw](../../language-reference/keywords/throw.md) statement at the end of your `catch` block.</span></span>

<span data-ttu-id="bd88c-116">複数の `catch` ブロックに異なる例外クラスが含まれている場合は、それらを連結することができます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-116">Multiple `catch` blocks with different exception classes can be chained together.</span></span> <span data-ttu-id="bd88c-117">`catch` ブロックはコード内で上から下に評価されますが、スローされた各例外に対して実行される `catch` ブロックは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="bd88c-117">The `catch` blocks are evaluated from top to bottom in your code, but only one `catch` block is executed for each exception that is thrown.</span></span> <span data-ttu-id="bd88c-118">スローされた例外の厳密な型か、その基底クラスを指定する最初の `catch` ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-118">The first `catch` block that specifies the exact type or a base class of the thrown exception is executed.</span></span> <span data-ttu-id="bd88c-119">一致する例外クラスを指定した `catch` ブロックがない場合は、種類のない `catch` ブロックが選択されます (それがステートメント内に存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="bd88c-119">If no `catch` block specifies a matching exception class, a `catch` block that doesn't have any type is selected, if one is present in the statement.</span></span> <span data-ttu-id="bd88c-120">最初に配置する `catch` ブロックでは、最も具体的な (つまり、最も派生した) 例外クラスを指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="bd88c-120">It's important to position `catch` blocks with the most specific (that is, the most derived) exception classes first.</span></span>

<span data-ttu-id="bd88c-121">次の条件に該当する場合は、例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="bd88c-121">Catch exceptions when the following conditions are true:</span></span>

- <span data-ttu-id="bd88c-122">例外がスローされる理由を十分に理解していて、かつ特定の回復手段を実装できる (<xref:System.IO.FileNotFoundException> オブジェクトをキャッチした場合に、ユーザーに新しいファイル名を入力するよう求めるなど)。</span><span class="sxs-lookup"><span data-stu-id="bd88c-122">You have a good understanding of why the exception might be thrown, and you can implement a specific recovery, such as prompting the user to enter a new file name when you catch a <xref:System.IO.FileNotFoundException> object.</span></span>
- <span data-ttu-id="bd88c-123">より具体的な例外を新規に作成し、スローできる。</span><span class="sxs-lookup"><span data-stu-id="bd88c-123">You can create and throw a new, more specific exception.</span></span>
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowMoreSpecificException":::
- <span data-ttu-id="bd88c-124">例外を追加処理に渡す前に、その例外を部分的に処理する必要がある。</span><span class="sxs-lookup"><span data-stu-id="bd88c-124">You want to partially handle an exception before passing it on for additional handling.</span></span> <span data-ttu-id="bd88c-125">次の例では、例外を再スローする前に、エラー ログにエントリを追加する目的で `catch` ブロックが使用されています。</span><span class="sxs-lookup"><span data-stu-id="bd88c-125">In the following example, a `catch` block is used to add an entry to an error log before rethrowing the exception.</span></span>
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="RethrowError":::

<span data-ttu-id="bd88c-126">"*例外フィルター*" を指定して、catch 句にブール式を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-126">You can also specify *exception filters* to add a boolean expression to a catch clause.</span></span> <span data-ttu-id="bd88c-127">これは、特定の catch 句が、その条件が true の場合にのみ一致することを示します。</span><span class="sxs-lookup"><span data-stu-id="bd88c-127">These indicate that a specific catch clause matches only when that condition is true.</span></span> <span data-ttu-id="bd88c-128">次の例では、両方の catch 句で同じ例外クラスが使用されますが、追加の条件が確認され、別のエラー メッセージが作成されます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-128">In the following example, both catch clauses use the same exception class, but an additional condition is checked to create a different error message:</span></span>

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="DemonstrateExceptionFilter":::

<span data-ttu-id="bd88c-129">常に `false` を返す例外フィルターを使用すると、すべての例外を検証できますが、処理は行われません。</span><span class="sxs-lookup"><span data-stu-id="bd88c-129">An exception filter that always returns `false` can be used to examine all exceptions but not process them.</span></span> <span data-ttu-id="bd88c-130">通常は、例外をログに記録するために使用します。</span><span class="sxs-lookup"><span data-stu-id="bd88c-130">A typical use is to log exceptions:</span></span>

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="ShowExceptionFilter":::

<span data-ttu-id="bd88c-131">`LogException` メソッドにより常に `false` が返され、この例外フィルターを使用する `catch` 句は一致しません。</span><span class="sxs-lookup"><span data-stu-id="bd88c-131">The `LogException` method always returns `false`, no `catch` clause using this exception filter matches.</span></span> <span data-ttu-id="bd88c-132">catch 句は一般的なもので (<xref:System.Exception?displayProperty=nameWithType> を使用)、後の句によってより具体的な例外クラスを処理することができます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-132">The catch clause can be general, using <xref:System.Exception?displayProperty=nameWithType>, and later clauses can process more specific exception classes.</span></span>

## <a name="finally-blocks"></a><span data-ttu-id="bd88c-133">Finally ブロック</span><span class="sxs-lookup"><span data-stu-id="bd88c-133">Finally Blocks</span></span>

<span data-ttu-id="bd88c-134">`finally` ブロックでは、`try` ブロックで実行されるアクションをクリーンアップすることができます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-134">A `finally` block enables you to clean up actions that are performed in a `try` block.</span></span> <span data-ttu-id="bd88c-135">`finally` ブロック (存在する場合) は、最後 (`try` ブロックおよび一致する `catch` ブロックの後) に実行されます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-135">If present, the `finally` block executes last, after the `try` block and any matched `catch` block.</span></span> <span data-ttu-id="bd88c-136">`finally` ブロックは、例外がスローされたかどうか、または例外の種類に一致する `catch` ブロックが見つかったかどうかにかかわらず、常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-136">A `finally` block always runs, whether an exception is thrown or a `catch` block matching the exception type is found.</span></span>

<span data-ttu-id="bd88c-137">`finally` ブロックは、ランタイム内のガベージ コレクターによってオブジェクトがファイナライズされるのを待つことなく、ファイル ストリーム、データベース接続、グラフィックス ハンドルなどのリソースを解放するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-137">The `finally` block can be used to release resources such as file streams, database connections, and graphics handles without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="bd88c-138">詳細については、[using ステートメント](../../language-reference/keywords/using-statement.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd88c-138">For more information See the [using Statement](../../language-reference/keywords/using-statement.md).</span></span>

<span data-ttu-id="bd88c-139">次の例では、`try` ブロックで開かれたファイルを閉じるために `finally` ブロックが使用されています。</span><span class="sxs-lookup"><span data-stu-id="bd88c-139">In the following example, the `finally` block is used to close a file that is opened in the `try` block.</span></span> <span data-ttu-id="bd88c-140">ファイルを閉じる前に、ファイル ハンドルの状態が確認されています。</span><span class="sxs-lookup"><span data-stu-id="bd88c-140">Notice that the state of the file handle is checked before the file is closed.</span></span> <span data-ttu-id="bd88c-141">`try` ブロックからファイルを開けなかった場合は、ファイル ハンドルの値が `null` のままになり、`finally` ブロックでファイルが閉じられることはありません。</span><span class="sxs-lookup"><span data-stu-id="bd88c-141">If the `try` block can't open the file, the file handle still has the value `null` and the `finally` block doesn't try to close it.</span></span> <span data-ttu-id="bd88c-142">代わりに、`try` ブロックでファイルが正常に開かれた場合は、`finally` ブロックによって開かれたファイルが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="bd88c-142">Instead, if the file is opened successfully in the `try` block, the `finally` block closes the open file.</span></span>

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CleanupIfNotNull":::

## <a name="c-language-specification"></a><span data-ttu-id="bd88c-143">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="bd88c-143">C# Language Specification</span></span>

<span data-ttu-id="bd88c-144">詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[例外](~/_csharplang/spec/exceptions.md)と [try ステートメント](~/_csharplang/spec/statements.md#the-try-statement)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="bd88c-144">For more information, see [Exceptions](~/_csharplang/spec/exceptions.md) and [The try statement](~/_csharplang/spec/statements.md#the-try-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="bd88c-145">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="bd88c-145">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bd88c-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd88c-146">See also</span></span>

- [<span data-ttu-id="bd88c-147">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="bd88c-147">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="bd88c-148">try-catch</span><span class="sxs-lookup"><span data-stu-id="bd88c-148">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="bd88c-149">try-finally</span><span class="sxs-lookup"><span data-stu-id="bd88c-149">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="bd88c-150">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="bd88c-150">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
- [<span data-ttu-id="bd88c-151">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="bd88c-151">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
