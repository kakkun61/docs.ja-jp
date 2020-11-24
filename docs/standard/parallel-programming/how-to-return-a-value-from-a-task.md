---
title: '方法: タスクから値を返す'
description: .NET で System.Threading.Tasks.Task<TResult> 型を使用して Result プロパティから値を返す方法について参照します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: c7a4a683545c9ef0448d9cdce769aae79215aecf
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825612"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="54a03-103">方法: タスクから値を返す</span><span class="sxs-lookup"><span data-stu-id="54a03-103">How to: Return a Value from a Task</span></span>
<span data-ttu-id="54a03-104">この例では、<xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> の型を使用して <xref:System.Threading.Tasks.Task%601.Result%2A> プロパティから値を返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="54a03-104">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="54a03-105">C:\Users\Public\Pictures\Sample Pictures\ ディレクトリが存在している必要があり、それがファイルを含んでいる必要があります。</span><span class="sxs-lookup"><span data-stu-id="54a03-105">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54a03-106">例</span><span class="sxs-lookup"><span data-stu-id="54a03-106">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="54a03-107"><xref:System.Threading.Tasks.Task%601.Result%2A> プロパティは、タスクが終了するまで呼び出し元のスレッドをブロックします。</span><span class="sxs-lookup"><span data-stu-id="54a03-107">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="54a03-108">1 つの <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> の結果を継続タスクに渡す方法を確認するには、「[継続タスクを使用したタスクの連結](chaining-tasks-by-using-continuation-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54a03-108">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54a03-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="54a03-109">See also</span></span>

- [<span data-ttu-id="54a03-110">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="54a03-110">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="54a03-111">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="54a03-111">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
