---
title: スレッドの破棄
description: 協調的なキャンセルまたは Thread.Abort メソッドなど、.NET でスレッドを破棄する必要がある場合のオプションについて確認します。 ThreadAbortException を処理する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: be31b0232889227fa5d4990c9481305eea343f11
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826483"
---
# <a name="destroying-threads"></a><span data-ttu-id="95a57-104">スレッドの破棄</span><span class="sxs-lookup"><span data-stu-id="95a57-104">Destroying threads</span></span>

<span data-ttu-id="95a57-105">スレッドの実行を終了するには、通常、[協調的なキャンセル モデル](cancellation-in-managed-threads.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="95a57-105">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="95a57-106">協調的なキャンセルを行うように設計されていないサード パーティのコードがスレッドで実行されているために、スレッドを協調的に停止できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="95a57-106">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="95a57-107">.NET Framework の <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> メソッドを使用すると、マネージド スレッドを強制的に終了できます。</span><span class="sxs-lookup"><span data-stu-id="95a57-107">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="95a57-108"><xref:System.Threading.Thread.Abort%2A> を呼び出すと、共通言語ランタイムにより対象スレッド内で <xref:System.Threading.ThreadAbortException> がスローされます。対象スレッドはこれをキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="95a57-108">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="95a57-109">詳細については、「<xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95a57-109">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95a57-110"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> メソッドは .NET 5 (.NET Core を含む) 以降のバージョンではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="95a57-110">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET 5 (including .NET Core) and later versions.</span></span> <span data-ttu-id="95a57-111">.NET 5+ でサード パーティのコードの実行を強制的に終了する必要がある場合は、それを別のプロセスで実行し、<xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="95a57-111">If you need to terminate the execution of third-party code forcibly in .NET 5+, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="95a57-112">スレッドが <xref:System.Threading.Thread.Abort%2A> メソッドの呼び出し時にアンマネージ コードを実行する場合、ランタイムはそれを <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType> としてマークします。</span><span class="sxs-lookup"><span data-stu-id="95a57-112">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="95a57-113">スレッドがマネージド コードに戻ると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="95a57-113">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="95a57-114">スレッドが中止されると、再起動することはできません。</span><span class="sxs-lookup"><span data-stu-id="95a57-114">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="95a57-115">対象スレッドが <xref:System.Threading.ThreadAbortException> をキャッチし、`finally` ブロック内の任意の量のコードを実行できるため、<xref:System.Threading.Thread.Abort%2A> メソッドにより、スレッドがすぐに中止されることはありません。</span><span class="sxs-lookup"><span data-stu-id="95a57-115">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="95a57-116">スレッドが終了するまで待機する必要がある場合は、<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="95a57-116">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="95a57-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> は、スレッドが実際に実行を停止するか、オプションのタイムアウト間隔が経過するまで返されないブロック呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="95a57-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="95a57-118">中止されたスレッドは <xref:System.Threading.Thread.ResetAbort%2A> メソッドを呼び出したり、`finally` ブロックで無制限処理を実行したりすることができるため、タイムアウトを指定しない場合、終了するまで待機するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="95a57-118">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="95a57-119"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> メソッドへの呼び出しを待機しているスレッドは、<xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> を呼び出す他のスレッドで中断することができます。</span><span class="sxs-lookup"><span data-stu-id="95a57-119">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="95a57-120">ThreadAbortException の処理</span><span class="sxs-lookup"><span data-stu-id="95a57-120">Handling ThreadAbortException</span></span>  
 <span data-ttu-id="95a57-121">独自のコードからの <xref:System.Threading.Thread.Abort%2A> の呼び出しの結果、またはスレッドが実行中のアプリケーション ドメインのアンロード (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> が <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を使用してスレッドを終了する) の結果として、スレッドが中止されることが予想される場合、スレッドは <xref:System.Threading.ThreadAbortException> を処理し、以下のコードに示すように、`finally` 句で最終処理を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95a57-121">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try
{  
    // Code that is executing when the thread is aborted.  
}
catch (ThreadAbortException ex)
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.
}  
// Do not put clean-up code here, because the exception
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="95a57-122">クリーンアップ コードは `catch` 句または `finally` 句にある必要があります。これは、<xref:System.Threading.ThreadAbortException> が `finally` 句の最後、または `catch` 句の最後 (`finally` 句がない場合) にシステムによって再スローされるためです。</span><span class="sxs-lookup"><span data-stu-id="95a57-122">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="95a57-123"><xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> メソッドを呼び出して、システムが例外を再スローしないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="95a57-123">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="95a57-124">ただし、この操作は独自のコードにより <xref:System.Threading.ThreadAbortException> が発生した場合にのみ行ってください。</span><span class="sxs-lookup"><span data-stu-id="95a57-124">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a57-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="95a57-125">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="95a57-126">スレッドの使用とスレッド処理</span><span class="sxs-lookup"><span data-stu-id="95a57-126">Using Threads and Threading</span></span>](using-threads-and-threading.md)
