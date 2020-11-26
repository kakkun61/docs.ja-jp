---
title: loaderLock MDA
description: .NET の loaderLock マネージデバッグアシスタント (MDA) を確認します。これにより、Windows OS ローダーロックを保持しているスレッドでマネージコードを実行しようとしたことが検出されます。
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
ms.openlocfilehash: 0e8946a3482798f0a20d6304c7d42d2a5832ae61
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240564"
---
# <a name="loaderlock-mda"></a><span data-ttu-id="3efd1-103">loaderLock MDA</span><span class="sxs-lookup"><span data-stu-id="3efd1-103">loaderLock MDA</span></span>

<span data-ttu-id="3efd1-104">`loaderLock` マネージド デバッグ アシスタント (MDA) は、Microsoft Windows オペレーティング システムのローダー ロックを保持しているスレッド上でマネージド コードを実行する試行を検出します。</span><span class="sxs-lookup"><span data-stu-id="3efd1-104">The `loaderLock` managed debugging assistant (MDA) detects attempts to execute managed code on a thread that holds the Microsoft Windows operating system loader lock.</span></span>  <span data-ttu-id="3efd1-105">このような実行は、デッドロックの原因になる可能性があり、オペレーティング システムのローダーが初期化する前に DLL が使用される可能性があるため、不適切です。</span><span class="sxs-lookup"><span data-stu-id="3efd1-105">Any such execution is illegal because it can lead to deadlocks and to use of DLLs before they have been initialized by the operating system's loader.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3efd1-106">現象</span><span class="sxs-lookup"><span data-stu-id="3efd1-106">Symptoms</span></span>  

 <span data-ttu-id="3efd1-107">オペレーティング システムのローダー ロック内でコードを実行する場合に発生する最も一般的なエラーは、ローダー ロックを必要とする他の Win32 関数を呼び出そうとしたときにスレッドがデッドロックする問題です。</span><span class="sxs-lookup"><span data-stu-id="3efd1-107">The most common failure when executing code inside the operating system's loader lock is that threads will deadlock when attempting to call other Win32 functions that also require the loader lock.</span></span>  <span data-ttu-id="3efd1-108">このような関数の例として、`LoadLibrary`、`GetProcAddress`、`FreeLibrary`、`GetModuleHandle` があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-108">Examples of such functions are `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, and `GetModuleHandle`.</span></span>  <span data-ttu-id="3efd1-109">アプリケーションはこれらの関数を直接呼び出さない可能性があります。<xref:System.Reflection.Assembly.Load%2A> など高位の呼び出しや、プラットフォーム呼び出しメソッドの最初の呼び出しの結果として共通言語ランタイム (CLR) からこれらの関数が呼び出される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-109">The application might not directly call these functions; the common language runtime (CLR) might call these functions as the result of a higher level call like <xref:System.Reflection.Assembly.Load%2A> or the first call to a platform invoke method.</span></span>  
  
 <span data-ttu-id="3efd1-110">スレッドが別スレッドの開始または完了を待機している場合にもデッドロックが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-110">Deadlocks can also occur if a thread is waiting for another thread to start or finish.</span></span>  <span data-ttu-id="3efd1-111">スレッドが実行を開始または完了した場合、影響を受ける DLL にイベントを配信するためにオペレーティング システムのローダー ロックを獲得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-111">When a thread starts or finishes executing, it must acquire the operating system's loader lock to deliver events to affected DLLs.</span></span>  
  
 <span data-ttu-id="3efd1-112">最後に、オペレーティング システムのローダーが DLL を適切に初期化する前に、それらの DLL の呼び出しが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-112">Finally, there are cases where calls into DLLs can occur before those DLLs have been properly initialized by the operating system's loader.</span></span>  <span data-ttu-id="3efd1-113">デッドロック エラーの場合、デッドロックに関係する全スレッドのスタックを調べることで診断できますが、この MDA を使用せずに初期化されていない DLL の使用を診断することは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="3efd1-113">Unlike the deadlock failures, which can be diagnosed by examining the stacks of all the threads involved in the deadlock, it is very difficult to diagnose the use of uninitialized DLLs without using this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3efd1-114">原因</span><span class="sxs-lookup"><span data-stu-id="3efd1-114">Cause</span></span>  

 <span data-ttu-id="3efd1-115">.NET Framework バージョン 1.0 または 1.1 用に構築されたマネージド/アンマネージド混在 C++ アセンブリの場合、特別な措置 (**/NOENTRY** とリンクするなど) を取っていなければ、一般的にローダー ロック内でマネージド コードを実行しようとします。</span><span class="sxs-lookup"><span data-stu-id="3efd1-115">Mixed managed/unmanaged C++ assemblies built for .NET Framework versions 1.0 or 1.1 generally attempt to execute managed code inside the loader lock unless special care has been taken, for example, linking with **/NOENTRY**.</span></span>
  
 <span data-ttu-id="3efd1-116">.NET Framework バージョン 2.0 用に構築されたマネージ/アンマネージ混在 C++ アセンブリの場合、このような問題の影響をあまり受けません。オペレーティング システムのルールに違反するアンマネージ DLL を使用するアプリケーションと同程度に少ないリスクです。</span><span class="sxs-lookup"><span data-stu-id="3efd1-116">Mixed managed/unmanaged C++ assemblies built for .NET Framework version 2.0 are less susceptible to these problems, having the same reduced risk as applications using unmanaged DLLs that violate the operating system's rules.</span></span>  <span data-ttu-id="3efd1-117">たとえば、アンマネージド DLL の `DllMain` エントリ ポイントが `CoCreateInstance` を呼び出して、COM に公開されているマネージド オブジェクトを取得する場合、結果として、ローダー ロック内のマネージド コードを実行することになります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-117">For example, if an unmanaged DLL's `DllMain` entry point calls `CoCreateInstance` to obtain a managed object that has been exposed to COM, the result is an attempt to execute managed code inside the loader lock.</span></span> <span data-ttu-id="3efd1-118">.NET Framework バージョン 2.0 以降のローダー ロックの問題については、「[混在アセンブリの初期化](/cpp/dotnet/initialization-of-mixed-assemblies)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3efd1-118">For more information about loader lock issues in the .NET Framework version 2.0 and later, see [Initialization of Mixed Assemblies](/cpp/dotnet/initialization-of-mixed-assemblies).</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3efd1-119">解像度</span><span class="sxs-lookup"><span data-stu-id="3efd1-119">Resolution</span></span>  

 <span data-ttu-id="3efd1-120">Visual C++ .NET 2002 および Visual C++ .NET 2003 では、`/clr` コンパイラ オプションを指定してコンパイルされた DLL は、読み込み時に非確定的にデッドロックを生じる可能性があります。この問題は、混在モード DLL 読み込み時の問題 (またはローダー ロックの問題) と呼ばれていました。</span><span class="sxs-lookup"><span data-stu-id="3efd1-120">In Visual C++ .NET 2002 and Visual C++ .NET 2003, DLLs compiled with the `/clr` compiler option could non-deterministically deadlock when loaded; this issue was called the mixed DLL loading or loader lock issue.</span></span> <span data-ttu-id="3efd1-121">Visual C++ 2005 以降の場合、混在モード DLL の読み込みプロセスで、このような確定的でない場合の問題はほとんどなくなりました。</span><span class="sxs-lookup"><span data-stu-id="3efd1-121">In Visual C++ 2005 and later, almost all non-determinism has been removed from the mixed DLL loading process.</span></span> <span data-ttu-id="3efd1-122">ただし、ローダー ロックが (確定的に) 発生する可能性のあるシナリオはいくつか残っています。</span><span class="sxs-lookup"><span data-stu-id="3efd1-122">However, there are a few remaining scenarios for which loader lock can (deterministically) occur.</span></span> <span data-ttu-id="3efd1-123">その他のローダー ロック問題の原因と解決策の詳細については、「[混在アセンブリの初期化](/cpp/dotnet/initialization-of-mixed-assemblies)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3efd1-123">For a detailed account of the causes and resolutions for the remaining loader lock issues, see [Initialization of Mixed Assemblies](/cpp/dotnet/initialization-of-mixed-assemblies).</span></span> <span data-ttu-id="3efd1-124">このトピックでローダー ロックの問題が特定できない場合は、スレッドのスタックを調べて、ローダー ロックが発生している理由と問題の解決方法を判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-124">If that topic does not identify your loader lock problem, you have to examine the thread's stack to determine why the loader lock is occurring and how to correct the problem.</span></span> <span data-ttu-id="3efd1-125">この MDA をアクティブにしたスレッドのスタック トレースを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3efd1-125">Look at the stack trace for the thread that has activated this MDA.</span></span>  <span data-ttu-id="3efd1-126">オペレーティング システムのローダー ロックを保持しているときに、スレッドが不正にマネージド コードを呼び出そうとしています。</span><span class="sxs-lookup"><span data-stu-id="3efd1-126">The thread is attempting to illegally call into managed code while holding the operating system's loader lock.</span></span>  <span data-ttu-id="3efd1-127">スタックに DLL の `DllMain` または同等のエントリ ポイントが存在するはずです。</span><span class="sxs-lookup"><span data-stu-id="3efd1-127">You will probably see a DLL's `DllMain` or equivalent entry point on the stack.</span></span>  <span data-ttu-id="3efd1-128">このようなエントリ ポイント内から実行が許可されることについて、オペレーティング システムのルールは非常に制限されています。</span><span class="sxs-lookup"><span data-stu-id="3efd1-128">The operating system's rules for what you can legally do from inside such an entry point are quite limited.</span></span>  <span data-ttu-id="3efd1-129">オペレーティング システムのルールでは、あらゆるマネージド実行が除外されています。</span><span class="sxs-lookup"><span data-stu-id="3efd1-129">These rules preclude any managed execution.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3efd1-130">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="3efd1-130">Effect on the Runtime</span></span>  

 <span data-ttu-id="3efd1-131">通常、プロセス内の複数のスレッドでデッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="3efd1-131">Typically, several threads inside the process will deadlock.</span></span>  <span data-ttu-id="3efd1-132">多くの場合、このようなスレッドの 1 つはガベージ コレクションの実行を担当しているため、このデッドロックによってプロセス全体に重大な影響が及ぶ可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-132">One of those threads is likely to be a thread responsible for performing a garbage collection, so this deadlock can have a major impact on the entire process.</span></span>  <span data-ttu-id="3efd1-133">さらに、オペレーティング システムのローダー ロックが必要な追加の操作も実行できなくなります。たとえば、アセンブリの読み込みまたはアンロード、スレッドの開始や終了などの操作です。</span><span class="sxs-lookup"><span data-stu-id="3efd1-133">Furthermore, it will prevent any additional operations that require the operating system's loader lock, like loading and unloading assemblies or DLLs and starting or stopping threads.</span></span>  
  
 <span data-ttu-id="3efd1-134">まれではありますが、初期化される前に呼び出された DLL で、アクセス違反などの問題が発生する可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-134">In some unusual cases, it is also possible for access violations or similar problems to be triggered in DLLs which are called before they have been initialized.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3efd1-135">出力</span><span class="sxs-lookup"><span data-stu-id="3efd1-135">Output</span></span>  

 <span data-ttu-id="3efd1-136">この MDA は、不正なマネージド実行が試行されていることを報告しています。</span><span class="sxs-lookup"><span data-stu-id="3efd1-136">This MDA reports that an illegal managed execution is being attempted.</span></span>  <span data-ttu-id="3efd1-137">スレッドのスタックを調べて、ローダー ロックが発生している理由と問題の解決方法を判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3efd1-137">You need to examine the thread's stack to determine why the loader lock is occurring and how to correct the problem.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3efd1-138">構成</span><span class="sxs-lookup"><span data-stu-id="3efd1-138">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3efd1-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="3efd1-139">See also</span></span>

- [<span data-ttu-id="3efd1-140">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="3efd1-140">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
