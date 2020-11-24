---
title: '方法 : finally ブロックを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, try/catch blocks
- exceptions, finally blocks
- try/catch blocks
- finally blocks
- ArgumentOutOfRangeException class
ms.assetid: 4b9c0137-04af-4468-91d1-b9014df8ddd2
ms.openlocfilehash: 8bc36ce9a755762bb5159a27f9ef5699b2992f0e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828037"
---
# <a name="how-to-use-finally-blocks"></a><span data-ttu-id="fc825-102">finally ブロックを使用する方法</span><span class="sxs-lookup"><span data-stu-id="fc825-102">How to use finally blocks</span></span>

<span data-ttu-id="fc825-103">例外が発生すると、実行が停止され、コントロールが適切な例外ハンドラーに付与されます。</span><span class="sxs-lookup"><span data-stu-id="fc825-103">When an exception occurs, execution stops and control is given to the appropriate exception handler.</span></span> <span data-ttu-id="fc825-104">これは、多くの場合、実行されるはずのコード行がバイパスされることを意味します。</span><span class="sxs-lookup"><span data-stu-id="fc825-104">This often means that lines of code you expect to be executed are bypassed.</span></span> <span data-ttu-id="fc825-105">ファイルを閉じるなどのいくつかのリソースのクリーンアップは、例外がスローされた場合でも実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc825-105">Some resource cleanup, such as closing a file, needs to be done even if an exception is thrown.</span></span> <span data-ttu-id="fc825-106">これを行うために、`finally` ブロックを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="fc825-106">To do this, you can use a `finally` block.</span></span> <span data-ttu-id="fc825-107">`finally` ブロックは、例外がスローされるかどうかに関係なく、常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="fc825-107">A `finally` block always executes, regardless of whether an exception is thrown.</span></span>

<span data-ttu-id="fc825-108">次のコード例では、`try`/`catch` ブロックを使用して <xref:System.ArgumentOutOfRangeException> をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="fc825-108">The following code example uses a `try`/`catch` block to catch an <xref:System.ArgumentOutOfRangeException>.</span></span> <span data-ttu-id="fc825-109">`Main` メソッドは 2 つの配列を作成し、一方の配列をもう一方にコピーすることを試みます。</span><span class="sxs-lookup"><span data-stu-id="fc825-109">The `Main` method creates two arrays and attempts to copy one to the other.</span></span> <span data-ttu-id="fc825-110">アクションが、<xref:System.ArgumentOutOfRangeException> を生成し、エラーは、コンソールに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="fc825-110">The action generates an <xref:System.ArgumentOutOfRangeException> and the error is written to the console.</span></span> <span data-ttu-id="fc825-111">`finally` ブロックは、コピー操作の結果に関係なく実行されます。</span><span class="sxs-lookup"><span data-stu-id="fc825-111">The `finally` block executes regardless of the outcome of the copy action.</span></span>

[!code-cpp[CodeTryCatchFinallyExample#3](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CPP/source2.cpp#3)]
[!code-csharp[CodeTryCatchFinallyExample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeTryCatchFinallyExample/CS/source2.cs#3)]
[!code-vb[CodeTryCatchFinallyExample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeTryCatchFinallyExample/VB/source2.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="fc825-112">参照</span><span class="sxs-lookup"><span data-stu-id="fc825-112">See also</span></span>

- [<span data-ttu-id="fc825-113">例外</span><span class="sxs-lookup"><span data-stu-id="fc825-113">Exceptions</span></span>](index.md)
