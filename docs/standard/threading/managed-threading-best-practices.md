---
title: マネージド スレッド処理のベスト プラクティス
description: .NET でのマネージド スレッド処理のベスト プラクティスについて説明します。 多数のスレッドの調整やブロッキング スレッドの処理など、困難な状況に対応します。
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET], design guidelines
- threading [.NET], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: 88e1f34388cd58fef59bc4005bcaf630c59a661e
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189005"
---
# <a name="managed-threading-best-practices"></a><span data-ttu-id="fc853-104">マネージド スレッド処理のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="fc853-104">Managed threading best practices</span></span>

<span data-ttu-id="fc853-105">マルチスレッドには慎重なプログラミングが必要です。</span><span class="sxs-lookup"><span data-stu-id="fc853-105">Multithreading requires careful programming.</span></span> <span data-ttu-id="fc853-106">ほとんどのタスクでは、スレッド プールのスレッドを使って実行の要求をキューに置くことによって、処理の複雑さを軽減できます。</span><span class="sxs-lookup"><span data-stu-id="fc853-106">For most tasks, you can reduce complexity by queuing requests for execution by thread pool threads.</span></span> <span data-ttu-id="fc853-107">このトピックでは、マルチ スレッド動作の調整や、ブロックするスレッドの処理など、より難しい状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="fc853-107">This topic addresses more difficult situations, such as coordinating the work of multiple threads, or handling threads that block.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc853-108">.NET Framework 4 以降では、マルチスレッド プログラミングの複雑さとリスクを軽減する API が Task Parallel Library および PLINQ に用意されています。</span><span class="sxs-lookup"><span data-stu-id="fc853-108">Starting with .NET Framework 4, the Task Parallel Library and PLINQ provide APIs that reduce some of the complexity and risks of multi-threaded programming.</span></span> <span data-ttu-id="fc853-109">詳細については、[.NET の並列プログラミング](../parallel-programming/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="fc853-109">For more information, see [Parallel Programming in .NET](../parallel-programming/index.md).</span></span>  
  
## <a name="deadlocks-and-race-conditions"></a><span data-ttu-id="fc853-110">デッドロックと競合状態</span><span class="sxs-lookup"><span data-stu-id="fc853-110">Deadlocks and race conditions</span></span>  
 <span data-ttu-id="fc853-111">マルチスレッドはスループットと応答速度の問題を解決しますが、その一方で、デッドロックと競合状態という新たな問題を発生させます。</span><span class="sxs-lookup"><span data-stu-id="fc853-111">Multithreading solves problems with throughput and responsiveness, but in doing so it introduces new problems: deadlocks and race conditions.</span></span>  
  
### <a name="deadlocks"></a><span data-ttu-id="fc853-112">デッドロック</span><span class="sxs-lookup"><span data-stu-id="fc853-112">Deadlocks</span></span>  
 <span data-ttu-id="fc853-113">デッドロックは、2 つのスレッドのうちの一方が、もう一方によって既にロックされているリソースをロックしようとすると発生します。</span><span class="sxs-lookup"><span data-stu-id="fc853-113">A deadlock occurs when each of two threads tries to lock a resource the other has already locked.</span></span> <span data-ttu-id="fc853-114">こうなると、どちらのスレッドも続行できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fc853-114">Neither thread can make any further progress.</span></span>  
  
 <span data-ttu-id="fc853-115">マネージド スレッド処理クラスの多くのメソッドには、ロックアウトを検出するためのタイムアウト機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="fc853-115">Many methods of the managed threading classes provide time-outs to help you detect deadlocks.</span></span> <span data-ttu-id="fc853-116">たとえば、`lockObject` というオブジェクトへのロックの取得を試みるコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fc853-116">For example, the following code attempts to acquire a lock on an object named `lockObject`.</span></span> <span data-ttu-id="fc853-117">ロックが 300 ミリ秒の間に得られない場合は、<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> は `false` を返します。</span><span class="sxs-lookup"><span data-stu-id="fc853-117">If the lock is not obtained in 300 milliseconds, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> returns `false`.</span></span>  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a><span data-ttu-id="fc853-118">競合状態</span><span class="sxs-lookup"><span data-stu-id="fc853-118">Race conditions</span></span>  
 <span data-ttu-id="fc853-119">競合状態は、2 つ以上のスレッドのうちのどれが特定のコード ブロックに最初に到達するかによって、プログラムの結果が変わってしまうバグのことです。</span><span class="sxs-lookup"><span data-stu-id="fc853-119">A race condition is a bug that occurs when the outcome of a program depends on which of two or more threads reaches a particular block of code first.</span></span> <span data-ttu-id="fc853-120">プログラムを何回か実行すると、異なる結果が得られ、実行の結果は予測できません。</span><span class="sxs-lookup"><span data-stu-id="fc853-120">Running the program many times produces different results, and the result of any given run cannot be predicted.</span></span>  
  
 <span data-ttu-id="fc853-121">競合状態の簡単な例として、フィールドのインクリメントがあります。</span><span class="sxs-lookup"><span data-stu-id="fc853-121">A simple example of a race condition is incrementing a field.</span></span> <span data-ttu-id="fc853-122">クラスにプライベートの **static** フィールド (Visual Basic では **Shared** ) があり、このフィールドは、`objCt++;` (C# の場合) または `objCt += 1` (Visual Basic の場合) のようなコードを使用して、クラスのインスタンスが生成されるたびにインクリメントされるものとします。</span><span class="sxs-lookup"><span data-stu-id="fc853-122">Suppose a class has a private **static** field ( **Shared** in Visual Basic) that is incremented every time an instance of the class is created, using code such as `objCt++;` (C#) or `objCt += 1` (Visual Basic).</span></span> <span data-ttu-id="fc853-123">この演算によって、`objCt` からレジスタへの値の読み込み、値のインクリメント、および `objCt` への値の格納が行われます。</span><span class="sxs-lookup"><span data-stu-id="fc853-123">This operation requires loading the value from `objCt` into a register, incrementing the value, and storing it in `objCt`.</span></span>  
  
 <span data-ttu-id="fc853-124">マルチスレッドされたアプリケーションでは、値の読み込みとインクリメントを行ったスレッドが、この 3 つの処理を実行する別のスレッドに先を越される可能性があります。最初のスレッドは、実行を再開して値を格納するとき、待機中に値が変更されたかどうかを考慮せずに、`objCt` の値を上書きしてしまいます。</span><span class="sxs-lookup"><span data-stu-id="fc853-124">In a multithreaded application, a thread that has loaded and incremented the value might be preempted by another thread which performs all three steps; when the first thread resumes execution and stores its value, it overwrites `objCt` without taking into account the fact that the value has changed in the interim.</span></span>  
  
 <span data-ttu-id="fc853-125">このような特定の競合状態は、<xref:System.Threading.Interlocked> など、<xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> クラスのメソッドを使用することによって容易に回避できます。</span><span class="sxs-lookup"><span data-stu-id="fc853-125">This particular race condition is easily avoided by using methods of the <xref:System.Threading.Interlocked> class, such as <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fc853-126">複数のスレッド間でデータを同期する他の手法については、「[マルチスレッド処理のためのデータの同期](synchronizing-data-for-multithreading.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-126">To read about other techniques for synchronizing data among multiple threads, see [Synchronizing Data for Multithreading](synchronizing-data-for-multithreading.md).</span></span>  
  
 <span data-ttu-id="fc853-127">競合状態は、複数のスレッドの動作を同期するときにも発生します。</span><span class="sxs-lookup"><span data-stu-id="fc853-127">Race conditions can also occur when you synchronize the activities of multiple threads.</span></span> <span data-ttu-id="fc853-128">コードを記述するときには、そのコードの行 (または行を構成する各マシン命令) を実行するスレッドが別のスレッドに追い越された場合に何が起きるのかを考慮しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc853-128">Whenever you write a line of code, you must consider what might happen if a thread were preempted before executing the line (or before any of the individual machine instructions that make up the line), and another thread overtook it.</span></span>  
  
## <a name="static-members-and-static-constructors"></a><span data-ttu-id="fc853-129">静的メンバーと静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="fc853-129">Static members and static constructors</span></span>  
 <span data-ttu-id="fc853-130">クラスは、そのクラス コンストラクター (C# では `static` コンストラクター、Visual Basic では `Shared Sub New`) の実行が完了するまで初期化されません。</span><span class="sxs-lookup"><span data-stu-id="fc853-130">A class is not initialized until its class constructor (`static` constructor in C#, `Shared Sub New` in Visual Basic) has finished running.</span></span> <span data-ttu-id="fc853-131">初期化されていない型のコードの実行を防止するため、共通言語ランタイムは、クラス コンストラクターの実行が完了するまで、他のスレッドからのそのクラスの `static` メンバー (Visual Basic では `Shared` メンバー) 呼び出しをすべてブロックします。</span><span class="sxs-lookup"><span data-stu-id="fc853-131">To prevent the execution of code on a type that is not initialized, the common language runtime blocks all calls from other threads to `static` members of the class (`Shared` members in Visual Basic) until the class constructor has finished running.</span></span>  
  
 <span data-ttu-id="fc853-132">たとえば、クラス コンストラクターが新しいスレッドを起動し、そのスレッドのプロシージャがクラスの `static` メンバーを呼び出した場合、その新しいスレッドは、クラス コンストラクターが完了するまでブロックされます。</span><span class="sxs-lookup"><span data-stu-id="fc853-132">For example, if a class constructor starts a new thread, and the thread procedure calls a `static` member of the class, the new thread blocks until the class constructor completes.</span></span>  
  
 <span data-ttu-id="fc853-133">このことは、`static` コンストラクターを持つことができるすべての型に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="fc853-133">This applies to any type that can have a `static` constructor.</span></span>  

## <a name="number-of-processors"></a><span data-ttu-id="fc853-134">プロセッサの数</span><span class="sxs-lookup"><span data-stu-id="fc853-134">Number of processors</span></span>

<span data-ttu-id="fc853-135">システムで利用できるプロセッサの数 (複数か 1 つだけか) がマルチスレッド アーキテクチャに影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="fc853-135">Whether there are multiple processors or only one processor available on a system can influence multithreaded architecture.</span></span> <span data-ttu-id="fc853-136">詳細については、「[プロセッサの数](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-136">For more information, see [Number of Processors](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors).</span></span>

<span data-ttu-id="fc853-137">実行時に利用できるプロセッサの数を判断するには <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc853-137">Use the <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> property to determine the number of processors available at run time.</span></span>
  
## <a name="general-recommendations"></a><span data-ttu-id="fc853-138">一般的な推奨事項</span><span class="sxs-lookup"><span data-stu-id="fc853-138">General recommendations</span></span>  
 <span data-ttu-id="fc853-139">マルチスレッドを使用するときは、以下のガイドラインを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-139">Consider the following guidelines when using multiple threads:</span></span>  
  
- <span data-ttu-id="fc853-140">他のスレッドを終了させるために <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> を使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="fc853-140">Don't use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate other threads.</span></span> <span data-ttu-id="fc853-141">他のスレッド **Abort** を呼び出すことは、そのスレッドの処理がどこまで到達しているかを把握せずに例外をスローするのと同じことになります。</span><span class="sxs-lookup"><span data-stu-id="fc853-141">Calling **Abort** on another thread is akin to throwing an exception on that thread, without knowing what point that thread has reached in its processing.</span></span>  
  
- <span data-ttu-id="fc853-142"><xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> と <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> を使用して複数のスレッドの動作を同期することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="fc853-142">Don't use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> to synchronize the activities of multiple threads.</span></span> <span data-ttu-id="fc853-143"><xref:System.Threading.Mutex>、<xref:System.Threading.ManualResetEvent>、<xref:System.Threading.AutoResetEvent>、および <xref:System.Threading.Monitor> を使用してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-143">Do use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, and <xref:System.Threading.Monitor>.</span></span>  
  
- <span data-ttu-id="fc853-144">メイン プログラムから、イベントなどを使用して、ワーカー スレッドの実行を制御しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc853-144">Don't control the execution of worker threads from your main program (using events, for example).</span></span> <span data-ttu-id="fc853-145">ワーカー スレッドの側で、作業ができるようになるまでの待機、作業の実行、および実行終了後のプログラムへの通知を行うように、プログラムをデザインします。</span><span class="sxs-lookup"><span data-stu-id="fc853-145">Instead, design your program so that worker threads are responsible for waiting until work is available, executing it, and notifying other parts of your program when finished.</span></span> <span data-ttu-id="fc853-146">ワーカー スレッドによるブロックを行わない場合は、スレッド プールのスレッドを使用することを考慮します。</span><span class="sxs-lookup"><span data-stu-id="fc853-146">If your worker threads do not block, consider using thread pool threads.</span></span> <span data-ttu-id="fc853-147">ワーカー スレッドがブロックを行う場合は、<xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fc853-147"><xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> is useful in situations where worker threads block.</span></span>  
  
- <span data-ttu-id="fc853-148">ロック オブジェクトとして型を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc853-148">Don't use types as lock objects.</span></span> <span data-ttu-id="fc853-149">つまり、C# の `lock(typeof(X))`、Visual Basic の `SyncLock(GetType(X))` などのコードを使用すること、または <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> を <xref:System.Type> オブジェクトと組み合わせて使用することを避けます。</span><span class="sxs-lookup"><span data-stu-id="fc853-149">That is, avoid code such as `lock(typeof(X))` in C# or `SyncLock(GetType(X))` in Visual Basic, or the use of <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> with <xref:System.Type> objects.</span></span> <span data-ttu-id="fc853-150"><xref:System.Type?displayProperty=nameWithType> のインスタンスは、1 つの型につきアプリケーション ドメインごとに 1 つのみです。</span><span class="sxs-lookup"><span data-stu-id="fc853-150">For a given type, there is only one instance of <xref:System.Type?displayProperty=nameWithType> per application domain.</span></span> <span data-ttu-id="fc853-151">ロックする型がパブリックの場合、自分以外のコードでもその型をロックできるため、デッドロックになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fc853-151">If the type you take a lock on is public, code other than your own can take locks on it, leading to deadlocks.</span></span> <span data-ttu-id="fc853-152">詳細については、「[信頼性に関するベスト プラクティス](../../framework/performance/reliability-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-152">For additional issues, see [Reliability Best Practices](../../framework/performance/reliability-best-practices.md).</span></span>  
  
- <span data-ttu-id="fc853-153">インスタンスをロックする場合 (たとえば、C# の `lock(this)`、Visual Basic の `SyncLock(Me)`) には注意してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-153">Use caution when locking on instances, for example `lock(this)` in C# or `SyncLock(Me)` in Visual Basic.</span></span> <span data-ttu-id="fc853-154">アプリケーション内の、その型以外の他のコードがオブジェクトをロックすると、デッドロックが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc853-154">If other code in your application, external to the type, takes a lock on the object, deadlocks could occur.</span></span>  
  
- <span data-ttu-id="fc853-155">モニター状態に入った (ロックを取得した) スレッドは、モニター状態である間に例外が発生した場合でも、必ずモニター状態から出すようにします。</span><span class="sxs-lookup"><span data-stu-id="fc853-155">Do ensure that a thread that has entered a monitor always leaves that monitor, even if an exception occurs while the thread is in the monitor.</span></span> <span data-ttu-id="fc853-156">C# の [lock](../../csharp/language-reference/keywords/lock-statement.md) ステートメントと Visual Basic の [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) ステートメントは、 **finally** ブロックを使用して <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> が呼び出されるようにすることで、この動作を自動的に提供します。</span><span class="sxs-lookup"><span data-stu-id="fc853-156">The C# [lock](../../csharp/language-reference/keywords/lock-statement.md) statement and the Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) statement provide this behavior automatically, employing a **finally** block to ensure that <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> is called.</span></span> <span data-ttu-id="fc853-157">**Exit** を確実に呼び出すことができない場合は、 **Mutex** を使用するようにデザインを変更することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-157">If you cannot ensure that **Exit** will be called, consider changing your design to use **Mutex**.</span></span> <span data-ttu-id="fc853-158">ミューテックスは、現在それを保持しているスレッドが終了すると、自動的に解放されます。</span><span class="sxs-lookup"><span data-stu-id="fc853-158">A mutex is automatically released when the thread that currently owns it terminates.</span></span>  
  
- <span data-ttu-id="fc853-159">マルチ スレッドは異なるリソースを必要とするタスクに使用し、1 つのリソースに複数のスレッドを割り当てることがないように注意します。</span><span class="sxs-lookup"><span data-stu-id="fc853-159">Do use multiple threads for tasks that require different resources, and avoid assigning multiple threads to a single resource.</span></span> <span data-ttu-id="fc853-160">たとえば、I/O を含む作業であれば、その作業専用のスレッドを用意すると有益です。I/O 操作の間、このスレッドはブロックを行いますが、他のスレッドは実行できるからです。</span><span class="sxs-lookup"><span data-stu-id="fc853-160">For example, any task involving I/O benefits from having its own thread, because that thread will block during I/O operations and thus allow other threads to execute.</span></span> <span data-ttu-id="fc853-161">ユーザー入力も、専用のスレッドが役に立つリソースの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="fc853-161">User input is another resource that benefits from a dedicated thread.</span></span> <span data-ttu-id="fc853-162">シングル プロセッサのコンピューターでは、計算中心のタスクがユーザー入力や I/O タスクと共存することはできますが、計算中心タスクどうしは競合してしまいます。</span><span class="sxs-lookup"><span data-stu-id="fc853-162">On a single-processor computer, a task that involves intensive computation coexists with user input and with tasks that involve I/O, but multiple computation-intensive tasks contend with each other.</span></span>  
  
- <span data-ttu-id="fc853-163">単純な状態変更については、<xref:System.Threading.Interlocked> ステートメント (Visual Basic では `lock`) ではなく、`SyncLock` クラスのメソッドの使用を検討します。</span><span class="sxs-lookup"><span data-stu-id="fc853-163">Consider using methods of the <xref:System.Threading.Interlocked> class for simple state changes, instead of using the `lock` statement (`SyncLock` in Visual Basic).</span></span> <span data-ttu-id="fc853-164">`lock` ステートメントは汎用的なツールとして優れていますが、<xref:System.Threading.Interlocked> クラスは、分離不可能な状態であることが必要な更新のパフォーマンスに優れています。</span><span class="sxs-lookup"><span data-stu-id="fc853-164">The `lock` statement is a good general-purpose tool, but the <xref:System.Threading.Interlocked> class provides better performance for updates that must be atomic.</span></span> <span data-ttu-id="fc853-165">内部的には、競合がない場合は、単一の lock プレフィックスが実行されます。</span><span class="sxs-lookup"><span data-stu-id="fc853-165">Internally, it executes a single lock prefix if there is no contention.</span></span> <span data-ttu-id="fc853-166">コードの校閲で、次に示す例のようなコードを探します。</span><span class="sxs-lookup"><span data-stu-id="fc853-166">In code reviews, watch for code like that shown in the following examples.</span></span> <span data-ttu-id="fc853-167">最初の例では、状態変数をインクリメントしています。</span><span class="sxs-lookup"><span data-stu-id="fc853-167">In the first example, a state variable is incremented:</span></span>  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)
    {  
        myField++;  
    }  
    ```  
  
     <span data-ttu-id="fc853-168"><xref:System.Threading.Interlocked.Increment%2A> ステートメントの代わりに `lock` メソッドを次のように使用すると、パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="fc853-168">You can improve performance by using the <xref:System.Threading.Interlocked.Increment%2A> method instead of the `lock` statement, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="fc853-169">1 より大きい分割不可能インクリメントには <xref:System.Threading.Interlocked.Add%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc853-169">Use the <xref:System.Threading.Interlocked.Add%2A> method for atomic increments larger than 1.</span></span>  
  
     <span data-ttu-id="fc853-170">2 番目の例では、参照型の変数を、null 参照 (Visual Basic では `Nothing`) の場合にのみ更新しています。</span><span class="sxs-lookup"><span data-stu-id="fc853-170">In the second example, a reference type variable is updated only if it is a null reference (`Nothing` in Visual Basic).</span></span>  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            x ??= y;
        }  
    }  
    ```  
  
     <span data-ttu-id="fc853-171">この代わりに <xref:System.Threading.Interlocked.CompareExchange%2A> メソッドを次のように使用すると、パフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="fc853-171">Performance can be improved by using the <xref:System.Threading.Interlocked.CompareExchange%2A> method instead, as follows:</span></span>  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="fc853-172"><xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> メソッド オーバーロードから参照型に対してタイプ セーフの代替が提供されます。</span><span class="sxs-lookup"><span data-stu-id="fc853-172">The <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> method overload provides a type-safe alternative for reference types.</span></span>
  
## <a name="recommendations-for-class-libraries"></a><span data-ttu-id="fc853-173">クラス ライブラリに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="fc853-173">Recommendations for class libraries</span></span>  
 <span data-ttu-id="fc853-174">マルチスレッド用のクラス ライブラリをデザインするときには、次のガイドラインを検討します。</span><span class="sxs-lookup"><span data-stu-id="fc853-174">Consider the following guidelines when designing class libraries for multithreading:</span></span>  
  
- <span data-ttu-id="fc853-175">可能な限り、同期の必要を避けるようにします。</span><span class="sxs-lookup"><span data-stu-id="fc853-175">Avoid the need for synchronization, if possible.</span></span> <span data-ttu-id="fc853-176">これは、頻繁に使用するコードの場合に特に言えます。</span><span class="sxs-lookup"><span data-stu-id="fc853-176">This is especially true for heavily used code.</span></span> <span data-ttu-id="fc853-177">たとえば、競合状態をなくすのではなく、競合状態に対応できるようにアルゴリズムを調整できる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fc853-177">For example, an algorithm might be adjusted to tolerate a race condition rather than eliminate it.</span></span> <span data-ttu-id="fc853-178">不要な同期があると、パフォーマンスが低下し、デッドロックや競合状態が発生する可能性が生じます。</span><span class="sxs-lookup"><span data-stu-id="fc853-178">Unnecessary synchronization decreases performance and creates the possibility of deadlocks and race conditions.</span></span>  
  
- <span data-ttu-id="fc853-179">静的なデータ (Visual Basic では `Shared`) は既定でスレッド セーフにします。</span><span class="sxs-lookup"><span data-stu-id="fc853-179">Make static data (`Shared` in Visual Basic) thread safe by default.</span></span>  
  
- <span data-ttu-id="fc853-180">インスタンス データは既定でスレッド セーフにしないようにします。</span><span class="sxs-lookup"><span data-stu-id="fc853-180">Do not make instance data thread safe by default.</span></span> <span data-ttu-id="fc853-181">スレッド セーフなコードを作成するロックを追加すると、パフォーマンスが低下し、ロックの競合が増加し、デッドロックが発生する可能性が生じます。</span><span class="sxs-lookup"><span data-stu-id="fc853-181">Adding locks to create thread-safe code decreases performance, increases lock contention, and creates the possibility for deadlocks to occur.</span></span> <span data-ttu-id="fc853-182">一般的なアプリケーション モデルでは、一度にユーザー コードを実行するスレッドは 1 つだけにして、スレッド セーフを実現する必要を最小限に抑えます。</span><span class="sxs-lookup"><span data-stu-id="fc853-182">In common application models, only one thread at a time executes user code, which minimizes the need for thread safety.</span></span> <span data-ttu-id="fc853-183">この理由から、.NET のクラス ライブラリは既定ではスレッド セーフではないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="fc853-183">For this reason, the .NET class libraries are not thread safe by default.</span></span>  
  
- <span data-ttu-id="fc853-184">静的状態を変更する静的メソッドは提供しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc853-184">Avoid providing static methods that alter static state.</span></span> <span data-ttu-id="fc853-185">一般的なサーバーのシナリオでは、静的状態は要求間で共有されます。つまり、複数のスレッドがそのコードを同時に実行できます。</span><span class="sxs-lookup"><span data-stu-id="fc853-185">In common server scenarios, static state is shared across requests, which means multiple threads can execute that code at the same time.</span></span> <span data-ttu-id="fc853-186">これにより、スレッド処理のバグが発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="fc853-186">This opens up the possibility of threading bugs.</span></span> <span data-ttu-id="fc853-187">要求間で共有されないインスタンスにデータをカプセル化するデザイン パターンの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="fc853-187">Consider using a design pattern that encapsulates data into instances that are not shared across requests.</span></span> <span data-ttu-id="fc853-188">加えて、静的なデータを同期する場合は、状態を変更する呼び出しが静的メソッド間にあると、デッドロックや冗長な同期が生じる可能性があり、パフォーマンスに悪影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="fc853-188">Furthermore, if static data are synchronized, calls between static methods that alter state can result in deadlocks or redundant synchronization, adversely affecting performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc853-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc853-189">See also</span></span>

- [<span data-ttu-id="fc853-190">スレッド化</span><span class="sxs-lookup"><span data-stu-id="fc853-190">Threading</span></span>](index.md)
- [<span data-ttu-id="fc853-191">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="fc853-191">Threads and Threading</span></span>](threads-and-threading.md)
