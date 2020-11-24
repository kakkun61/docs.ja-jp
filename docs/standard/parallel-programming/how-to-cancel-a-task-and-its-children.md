---
title: '方法: タスクとその子を取り消す'
description: .NET でタスクとその子を取り消す方法の例を参照します。 この例では、取り消し可能なタスクの作成から、タスクが取り消されたことを知らせる通知までの手順を説明しています。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 578544a910127f41dfdfd577316b23d6d5a60bc4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817264"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="3054e-104">方法: タスクとその子を取り消す</span><span class="sxs-lookup"><span data-stu-id="3054e-104">How to: Cancel a Task and Its Children</span></span>
<span data-ttu-id="3054e-105">以下の例では、次のタスクを実行する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3054e-105">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="3054e-106">取り消すことができるタスクを作成し、開始します。</span><span class="sxs-lookup"><span data-stu-id="3054e-106">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="3054e-107">キャンセル トークンをユーザー デリゲートに渡し、必要に応じてタスク インスタンスにも渡します。</span><span class="sxs-lookup"><span data-stu-id="3054e-107">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="3054e-108">ユーザー デリゲート内のキャンセル要求を確認し、これに応答します。</span><span class="sxs-lookup"><span data-stu-id="3054e-108">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="3054e-109">必要に応じて、タスクが取り消された呼び出し元のスレッドを確認します。</span><span class="sxs-lookup"><span data-stu-id="3054e-109">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="3054e-110">呼び出し元のスレッドは、タスクを強制終了せず、キャンセルが要求されたことを通知するだけです。</span><span class="sxs-lookup"><span data-stu-id="3054e-110">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="3054e-111">タスクが既に実行中である場合、ユーザー デリゲートが要求を確認して適切に応答します。</span><span class="sxs-lookup"><span data-stu-id="3054e-111">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="3054e-112">タスクを実行する前にキャンセルが要求された場合、ユーザー デリゲートは実行されず、タスク オブジェクトは Canceled 状態に遷移します。</span><span class="sxs-lookup"><span data-stu-id="3054e-112">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3054e-113">例</span><span class="sxs-lookup"><span data-stu-id="3054e-113">Example</span></span>  
 <span data-ttu-id="3054e-114">次の例は、キャンセル要求に応答して <xref:System.Threading.Tasks.Task> およびその子を終了する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3054e-114">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="3054e-115">また、ユーザー デリゲートが <xref:System.Threading.Tasks.TaskCanceledException> をスローして終了した場合、タスクの終了を待つために、呼び出し元スレッドが必要に応じて <xref:System.Threading.Tasks.Task.Wait%2A> メソッドまたは <xref:System.Threading.Tasks.Task.WaitAll%2A> メソッドを使用できることも示しています。</span><span class="sxs-lookup"><span data-stu-id="3054e-115">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="3054e-116">この例では `try/catch` ブロックを使用して、呼び出し元スレッドで例外を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3054e-116">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="3054e-117"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラスは、<xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> の型および <xref:System.Threading.CancellationToken?displayProperty=nameWithType> の型に基づくキャンセル モデルに完全に統合されています。</span><span class="sxs-lookup"><span data-stu-id="3054e-117">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="3054e-118">詳細については、「[マネージド スレッドのキャンセル](../threading/cancellation-in-managed-threads.md)」と「[タスクのキャンセル](task-cancellation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3054e-118">For more information, see [Cancellation in Managed Threads](../threading/cancellation-in-managed-threads.md) and [Task Cancellation](task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3054e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3054e-119">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="3054e-120">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="3054e-120">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="3054e-121">アタッチされた子タスクとデタッチされた子タスク</span><span class="sxs-lookup"><span data-stu-id="3054e-121">Attached and Detached Child Tasks</span></span>](attached-and-detached-child-tasks.md)
- [<span data-ttu-id="3054e-122">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="3054e-122">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
