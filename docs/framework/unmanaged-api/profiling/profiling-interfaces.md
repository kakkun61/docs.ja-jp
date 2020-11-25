---
title: プロファイリングのインターフェイス
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
ms.openlocfilehash: dd6999e9f9e16264bde3cf62ce3a888841347607
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727472"
---
# <a name="profiling-interfaces"></a><span data-ttu-id="a1d9d-102">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-102">Profiling Interfaces</span></span>

<span data-ttu-id="a1d9d-103">ここでは、共通言語ランタイム (CLR) で実行中のプログラムに対してプロファイルを可能にするアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-103">This section describes the unmanaged interfaces that enable you to profile a program that is being executed by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1d9d-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a1d9d-104">In This Section</span></span>  

 [<span data-ttu-id="a1d9d-105">ICLRProfiling インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-105">ICLRProfiling Interface</span></span>](iclrprofiling-interface.md)  
 <span data-ttu-id="a1d9d-106">[Attachprofiler](iclrprofiling-attachprofiler-method.md)メソッドを提供します。これにより、実行中のプロセスにプロファイラーをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-106">Provides the [AttachProfiler](iclrprofiling-attachprofiler-method.md) method, which enables a profiler to attach to a running process.</span></span>  
  
 [<span data-ttu-id="a1d9d-107">ICorProfilerAssemblyReferenceProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-107">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)  
 <span data-ttu-id="a1d9d-108">プロファイラーが [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) コールバックに追加するアセンブリ参照を CLR に通知できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-108">Enables the profiler to inform the CLR of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
 [<span data-ttu-id="a1d9d-109">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-109">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)  
 <span data-ttu-id="a1d9d-110">プロファイラーがサブスクライブしたイベントが発生したときにコード プロファイラーに通知するために、CLR が使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-110">Provides methods that are used by the CLR to notify a code profiler when the events to which the profiler has subscribed occur.</span></span>  
  
 [<span data-ttu-id="a1d9d-111">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-111">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)  
 <span data-ttu-id="a1d9d-112">.NET Framework 2.0 以降でサポートされるコールバックによって、`ICorProfilerCallback` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-112">Extends the `ICorProfilerCallback` interface with callbacks supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="a1d9d-113">ICorProfilerCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-113">ICorProfilerCallback3 Interface</span></span>](icorprofilercallback3-interface.md)  
 <span data-ttu-id="a1d9d-114">CLR がプロファイラーにアタッチとデタッチの状態情報を伝えるために使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-114">Provides callback methods that the CLR uses to communicate attach and detach state information to the profiler.</span></span>  
  
 [<span data-ttu-id="a1d9d-115">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-115">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)  
 <span data-ttu-id="a1d9d-116">プロファイラーと情報をやりとりするために CLR が使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-116">Provides callback methods that the CLR uses to communicate information to the profiler.</span></span>  
  
 [<span data-ttu-id="a1d9d-117">ICorProfilerCallback5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-117">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)  
 <span data-ttu-id="a1d9d-118">ガベージ コレクションのルートによって参照されるオブジェクトの遷移的なクロージャを識別するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-118">Provides a method that identifies the transitive closure of objects referenced by garbage collection roots.</span></span>  
  
 [<span data-ttu-id="a1d9d-119">ICorProfilerCallback6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-119">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)  
 <span data-ttu-id="a1d9d-120">CLR が プロファイラーに対して、アセンブリがロード中であることを通知するために使用するコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-120">Provides a callback method that the CLR uses to notify a profiler that an assembly is loading.</span></span>  
  
 [<span data-ttu-id="a1d9d-121">ICorProfilerCallback7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-121">ICorProfilerCallback7 Interface</span></span>](icorprofilercallback7-interface.md)  
 <span data-ttu-id="a1d9d-122">メモリ内モジュールに関連付けられているシンボルストリームが更新されたことをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-122">Provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  

[<span data-ttu-id="a1d9d-123">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)  
<span data-ttu-id="a1d9d-124">動的メソッドの JIT コンパイルが開始および終了したことをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-124">Provides callback methods that the common language runtime uses to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>

[<span data-ttu-id="a1d9d-125">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-125">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)  
<span data-ttu-id="a1d9d-126">動的メソッドがガベージコレクションされ、その後アンロードされることをプロファイラーに通知するために共通言語ランタイムが使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-126">Provides a callback method that the common language runtime uses to notify the profiler that a dynamic method is garbage collected and subsequently unloaded.</span></span>

 [<span data-ttu-id="a1d9d-127">ICorProfilerFunctionControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-127">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)  
 <span data-ttu-id="a1d9d-128">コード プロファイラーが CLR と通信できるようにするためのメソッドを提供します。これは特定のメソッドを再コンパイルするときに、JIT コンパイラーがどのようにしてコードを生成するかを制御するためのものです。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-128">Provides methods that allow a code profiler to communicate with the CLR to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
 [<span data-ttu-id="a1d9d-129">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-129">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)  
 <span data-ttu-id="a1d9d-130">CLR で関数のコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-130">Provides methods to sequentially iterate through a collection of functions in the CLR.</span></span>  
  
 [<span data-ttu-id="a1d9d-131">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-131">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)  
 <span data-ttu-id="a1d9d-132">コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-132">Provides methods for use by code profilers to communicate with the CLR to control event monitoring and request information.</span></span>  
  
 [<span data-ttu-id="a1d9d-133">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-133">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)  
 <span data-ttu-id="a1d9d-134">.NET Framework 2.0 以降でサポートされるメソッドによって、`ICorProfilerInfo` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-134">Extends the `ICorProfilerInfo` interface with methods supported in the .NET Framework 2.0 and later versions.</span></span>  
  
 [<span data-ttu-id="a1d9d-135">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-135">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)  
 <span data-ttu-id="a1d9d-136">`ICorProfilerInfo2`.NET Framework 4 以降のバージョンでサポートされているメソッドを使用して、インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-136">Extends the `ICorProfilerInfo2` interface with methods supported in the .NET Framework 4 and later versions.</span></span>  
  
 [<span data-ttu-id="a1d9d-137">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-137">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)  
 <span data-ttu-id="a1d9d-138">コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-138">Provides methods that code profilers use to communicate with the CLR to control event monitoring and to request information.</span></span>  
  
 [<span data-ttu-id="a1d9d-139">ICorProfilerInfo5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-139">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)  
 <span data-ttu-id="a1d9d-140">コード プロファイラーが、イベントの監視を制御するために CLR との通信で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-140">Provides methods for use by code profilers to communicate with the CLR to control event monitoring.</span></span>  
  
 [<span data-ttu-id="a1d9d-141">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-141">ICorProfilerInfo6 Interface</span></span>](icorprofilerinfo6-interface.md)  
 <span data-ttu-id="a1d9d-142">特定の NGen モジュールに属し、特定のメソッドの本体にインライン化されているすべてのメソッドに列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-142">Provides an enumerator to all the methods that belong to a given NGen module and that are inlined in the body of a given method.</span></span>  
  
 [<span data-ttu-id="a1d9d-143">ICorProfilerInfo7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-143">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)  
 <span data-ttu-id="a1d9d-144">新しく定義されたメタデータをモジュールに適用し、メモリ内シンボルストリームへのアクセスを提供するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-144">Provides a method to apply newly defined metadata to a module and that provides access to an in-memory symbol stream.</span></span>  
  
 [<span data-ttu-id="a1d9d-145">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-145">ICorProfilerModuleEnum Interface</span></span>](icorprofilermoduleenum-interface.md)  
 <span data-ttu-id="a1d9d-146">アプリケーションまたはプロファイラーによってロードされたモジュールのコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-146">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
 [<span data-ttu-id="a1d9d-147">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-147">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)  
 <span data-ttu-id="a1d9d-148">[Ngen.exe (ネイティブイメージジェネレーター)](../../tools/ngen-exe-native-image-generator.md)によって生成される固定されたオブジェクトのコレクションを順番に反復処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-148">Provides methods to sequentially iterate through a collection of frozen objects that are generated by [Ngen.exe (Native Image Generator)](../../tools/ngen-exe-native-image-generator.md).</span></span>  
  
 [<span data-ttu-id="a1d9d-149">ICorProfilerThreadEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-149">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)  
 <span data-ttu-id="a1d9d-150">CLR でスレッドのコレクションを順番に反復処理するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-150">Provides methods to sequentially iterate through a collection of threads in the CLR.</span></span>  
  
 [<span data-ttu-id="a1d9d-151">IMethodMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1d9d-151">IMethodMalloc Interface</span></span>](imethodmalloc-interface.md)  
 <span data-ttu-id="a1d9d-152">新しい Microsoft 中間言語 (MSIL) 関数の本体にメモリを割り当てるための [Alloc](imethodmalloc-alloc-method.md) メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a1d9d-152">Provides the [Alloc](imethodmalloc-alloc-method.md) method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a1d9d-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1d9d-153">Related Sections</span></span>  

 [<span data-ttu-id="a1d9d-154">プロファイリングの概要</span><span class="sxs-lookup"><span data-stu-id="a1d9d-154">Profiling Overview</span></span>](profiling-overview.md)  
  
 [<span data-ttu-id="a1d9d-155">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="a1d9d-155">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)  
  
 [<span data-ttu-id="a1d9d-156">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="a1d9d-156">Profiling Enumerations</span></span>](profiling-enumerations.md)  
  
 [<span data-ttu-id="a1d9d-157">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="a1d9d-157">Profiling Structures</span></span>](profiling-structures.md)
