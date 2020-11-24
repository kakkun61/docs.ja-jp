---
title: '方法: 例外を明示的にスローする'
description: C# の Throw ステートメントまたは Visual Basic の Throw ステートメントを使用して、.NET で明示的に例外をスローする方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- FileNotFoundException class
- try/catch blocks
- exceptions, throwing
- implicitly throwing exceptions
ms.assetid: 72bdd157-caa9-4478-9ee3-cb4500b84528
ms.openlocfilehash: 37ba5f952d621ff2e209a3bac375b62894c944a7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828050"
---
# <a name="how-to-explicitly-throw-exceptions"></a><span data-ttu-id="ccbf0-103">例外を明示的にスローする方法</span><span class="sxs-lookup"><span data-stu-id="ccbf0-103">How to explicitly throw exceptions</span></span>

<span data-ttu-id="ccbf0-104">明示的に例外をスローするには、C# の [`throw`](../../csharp/language-reference/keywords/throw.md) または Visual Basic の [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="ccbf0-104">You can explicitly throw an exception using the C# [`throw`](../../csharp/language-reference/keywords/throw.md) or the Visual Basic [`Throw`](../../visual-basic/language-reference/statements/throw-statement.md) statement.</span></span> <span data-ttu-id="ccbf0-105">`throw` ステートメントを使って、キャッチした例外をもう一度スローすることもできます。</span><span class="sxs-lookup"><span data-stu-id="ccbf0-105">You can also throw a caught exception again using the `throw` statement.</span></span> <span data-ttu-id="ccbf0-106">再スローされる例外に情報を追加して、デバッグ時により多くの情報を提供するコーディング手法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ccbf0-106">It is good coding practice to add information to an exception that is re-thrown to provide more information when debugging.</span></span>

<span data-ttu-id="ccbf0-107">次のコード例では、`try`/`catch` ブロックを使用して可能性のある <xref:System.IO.FileNotFoundException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="ccbf0-107">The following code example uses a `try`/`catch` block to catch a possible <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="ccbf0-108">次の `try` ブロックは、<xref:System.IO.FileNotFoundException> をキャッチし、データ ファイルが見つからない場合に、メッセージをコンソールに出力する `catch` ブロックです。</span><span class="sxs-lookup"><span data-stu-id="ccbf0-108">Following the `try` block is a `catch` block that catches the <xref:System.IO.FileNotFoundException> and writes a message to the console if the data file is not found.</span></span> <span data-ttu-id="ccbf0-109">次のステートメントは、新しい <xref:System.IO.FileNotFoundException> をスローして、テキスト情報を例外に追加する `throw` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ccbf0-109">The next statement is the `throw` statement that throws a new <xref:System.IO.FileNotFoundException> and adds text information to the exception.</span></span>

[!code-csharp[Exception.Throwing#1](~/samples/snippets/csharp/VS_Snippets_CLR/Exception.Throwing/CS/throw.cs#1)]
[!code-vb[Exception.Throwing#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/Exception.Throwing/VB/throw.vb#1)]  

## <a name="see-also"></a><span data-ttu-id="ccbf0-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccbf0-110">See also</span></span>

- [<span data-ttu-id="ccbf0-111">例外</span><span class="sxs-lookup"><span data-stu-id="ccbf0-111">Exceptions</span></span>](index.md)
