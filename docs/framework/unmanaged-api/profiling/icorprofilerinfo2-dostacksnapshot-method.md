---
title: ICorProfilerInfo2::DoStackSnapshot メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
ms.openlocfilehash: 10cc9dedfa34cd5235df721d7010bbd928fbc3ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727238"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a><span data-ttu-id="afe81-102">ICorProfilerInfo2::DoStackSnapshot メソッド</span><span class="sxs-lookup"><span data-stu-id="afe81-102">ICorProfilerInfo2::DoStackSnapshot Method</span></span>

<span data-ttu-id="afe81-103">指定したスレッドのスタック上のマネージフレームをウォークし、コールバックを介してプロファイラーに情報を送信します。</span><span class="sxs-lookup"><span data-stu-id="afe81-103">Walks the managed frames on the stack for the specified thread, and sends information to the profiler through a callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afe81-104">構文</span><span class="sxs-lookup"><span data-stu-id="afe81-104">Syntax</span></span>  
  
```cpp  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afe81-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="afe81-105">Parameters</span></span>  

 `thread`  
 <span data-ttu-id="afe81-106">からターゲットスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="afe81-106">[in] The ID of the target thread.</span></span>  
  
 <span data-ttu-id="afe81-107">に null を渡すと `thread` 、現在のスレッドのスナップショットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="afe81-107">Passing null in `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="afe81-108">`ThreadID`別のスレッドのが渡された場合、共通言語ランタイム (CLR) はそのスレッドを中断し、スナップショットを実行して、再開します。</span><span class="sxs-lookup"><span data-stu-id="afe81-108">If a `ThreadID` of a different thread is passed, the common language runtime (CLR) suspends that thread, performs the snapshot, and resumes.</span></span>  
  
 `callback`  
 <span data-ttu-id="afe81-109">から [Stacksnapshotcallback](stacksnapshotcallback-function.md) メソッドの実装へのポインター。プロファイラーは、各マネージフレームと、アンマネージフレームの各実行に関する情報を提供するために、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="afe81-109">[in] A pointer to the implementation of the [StackSnapshotCallback](stacksnapshotcallback-function.md) method, which is called by the CLR to provide the profiler with information on each managed frame and each run of unmanaged frames.</span></span>  
  
 <span data-ttu-id="afe81-110">メソッドは、 `StackSnapshotCallback` プロファイラーライターによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="afe81-110">The `StackSnapshotCallback` method is implemented by the profiler writer.</span></span>  
  
 `infoFlags`  
 <span data-ttu-id="afe81-111">からによって各フレームに返されるデータ量を指定する [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) 列挙体の値 `StackSnapshotCallback` 。</span><span class="sxs-lookup"><span data-stu-id="afe81-111">[in] A value of the [COR_PRF_SNAPSHOT_INFO](cor-prf-snapshot-info-enumeration.md) enumeration, which specifies the amount of data to be passed back for each frame by `StackSnapshotCallback`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="afe81-112">からクライアントデータへのポインター。これは、コールバック関数に直接渡され `StackSnapshotCallback` ます。</span><span class="sxs-lookup"><span data-stu-id="afe81-112">[in] A pointer to the client data, which is passed straight through to the `StackSnapshotCallback` callback function.</span></span>  
  
 `context`  
 <span data-ttu-id="afe81-113">からスタックウォークをシード処理するために使用される Win32 構造体へのポインター `CONTEXT` 。</span><span class="sxs-lookup"><span data-stu-id="afe81-113">[in] A pointer to a Win32 `CONTEXT` structure, which is used to seed the stack walk.</span></span> <span data-ttu-id="afe81-114">Win32 構造体には、 `CONTEXT` cpu レジスタの値が含まれており、特定の時点における cpu の状態を表します。</span><span class="sxs-lookup"><span data-stu-id="afe81-114">The Win32 `CONTEXT` structure contains values of the CPU registers and represents the state of the CPU at a particular moment in time.</span></span>  
  
 <span data-ttu-id="afe81-115">スタックの最上位がアンマネージヘルパーコードの場合、このシードを使用すると、CLR はスタックウォークの開始位置を決定できます。それ以外の場合、シードは無視されます。</span><span class="sxs-lookup"><span data-stu-id="afe81-115">The seed helps the CLR determine where to begin the stack walk, if the top of the stack is unmanaged helper code; otherwise, the seed is ignored.</span></span> <span data-ttu-id="afe81-116">非同期ウォークにはシードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="afe81-116">A seed must be supplied for an asynchronous walk.</span></span> <span data-ttu-id="afe81-117">同期ウォークを実行する場合、シードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="afe81-117">If you are doing a synchronous walk, no seed is necessary.</span></span>  
  
 <span data-ttu-id="afe81-118">パラメーターは、 `context` パラメーターで COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効です `infoFlags` 。</span><span class="sxs-lookup"><span data-stu-id="afe81-118">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in the `infoFlags` parameter.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="afe81-119">から `CONTEXT` パラメーターによって参照される構造体のサイズ `context` 。</span><span class="sxs-lookup"><span data-stu-id="afe81-119">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afe81-120">注釈</span><span class="sxs-lookup"><span data-stu-id="afe81-120">Remarks</span></span>  

 <span data-ttu-id="afe81-121">に null を渡す `thread` と、現在のスレッドのスナップショットが生成されます。</span><span class="sxs-lookup"><span data-stu-id="afe81-121">Passing null for `thread` yields a snapshot of the current thread.</span></span> <span data-ttu-id="afe81-122">スナップショットは、その時点でターゲットスレッドが中断されている場合にのみ、他のスレッドで取得できます。</span><span class="sxs-lookup"><span data-stu-id="afe81-122">Snapshots can be taken of other threads only if the target thread is suspended at the time.</span></span>  
  
 <span data-ttu-id="afe81-123">プロファイラーがスタックをウォークする場合は、を呼び出し `DoStackSnapshot` ます。</span><span class="sxs-lookup"><span data-stu-id="afe81-123">When the profiler wants to walk the stack, it calls `DoStackSnapshot`.</span></span> <span data-ttu-id="afe81-124">その呼び出しから CLR が戻る前に、 `StackSnapshotCallback` スタック上のマネージフレーム (またはアンマネージフレームの実行) ごとに、を複数回呼び出します。</span><span class="sxs-lookup"><span data-stu-id="afe81-124">Before the CLR returns from that call, it calls your `StackSnapshotCallback` several times, once for each managed frame (or run of unmanaged frames) on the stack.</span></span> <span data-ttu-id="afe81-125">アンマネージフレームが検出されたら、それらを自分で調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="afe81-125">When unmanaged frames are encountered, you must walk them yourself.</span></span>  
  
 <span data-ttu-id="afe81-126">スタックがウォークされる順序は、フレームがスタックにプッシュされた方法と逆になります。リーフ (最後にプッシュされた) フレームは、最初にメイン (最初にプッシュされた) フレームに最後に配置されます。</span><span class="sxs-lookup"><span data-stu-id="afe81-126">The order in which the stack is walked is the reverse of how the frames were pushed onto the stack: leaf (last-pushed) frame first, main (first-pushed) frame last.</span></span>  
  
 <span data-ttu-id="afe81-127">プロファイラーをプログラミングしてマネージスタックをウォークする方法の詳細については、「 [.NET Framework 2.0: 基本およびそれ以降のプロファイラースタックウォーク](/previous-versions/dotnet/articles/bb264782(v=msdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afe81-127">For more information about how to program the profiler to walk managed stacks, see [Profiler Stack Walking in the .NET Framework 2.0: Basics and Beyond](/previous-versions/dotnet/articles/bb264782(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="afe81-128">次のセクションで説明するように、スタックウォークは同期または非同期にすることができます。</span><span class="sxs-lookup"><span data-stu-id="afe81-128">A stack walk can be synchronous or asynchronous, as explained in the following sections.</span></span>  
  
## <a name="synchronous-stack-walk"></a><span data-ttu-id="afe81-129">同期スタックウォーク</span><span class="sxs-lookup"><span data-stu-id="afe81-129">Synchronous Stack Walk</span></span>  

 <span data-ttu-id="afe81-130">同期スタックウォークでは、コールバックへの応答として現在のスレッドのスタックを調べる必要があります。</span><span class="sxs-lookup"><span data-stu-id="afe81-130">A synchronous stack walk involves walking the stack of the current thread in response to a callback.</span></span> <span data-ttu-id="afe81-131">シード処理や中断を必要としません。</span><span class="sxs-lookup"><span data-stu-id="afe81-131">It does not require seeding or suspending.</span></span>  
  
 <span data-ttu-id="afe81-132">プロファイラーの [ICorProfilerCallback](icorprofilercallback-interface.md) (または [ICorProfilerCallback2](icorprofilercallback2-interface.md)) メソッドのいずれかを呼び出す CLR に応答してを呼び出す場合は、を呼び出して、 `DoStackSnapshot` 現在のスレッドのスタックをウォークします。</span><span class="sxs-lookup"><span data-stu-id="afe81-132">You make a synchronous call when, in response to the CLR calling one of your profiler's [ICorProfilerCallback](icorprofilercallback-interface.md) (or [ICorProfilerCallback2](icorprofilercallback2-interface.md)) methods, you call `DoStackSnapshot` to walk the stack of the current thread.</span></span> <span data-ttu-id="afe81-133">これは、 [ICorProfilerCallback:: ObjectAllocated](icorprofilercallback-objectallocated-method.md)などの通知でスタックがどのように見えるかを確認する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="afe81-133">This is useful when you want to see what the stack looks like at a notification such as [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span> <span data-ttu-id="afe81-134">メソッド内からを呼び出すだけで `DoStackSnapshot` `ICorProfilerCallback` 、パラメーターとパラメーターで null を渡すことができ `context` `thread` ます。</span><span class="sxs-lookup"><span data-stu-id="afe81-134">You just call `DoStackSnapshot` from within your `ICorProfilerCallback` method, passing null in the `context` and `thread` parameters.</span></span>  
  
## <a name="asynchronous-stack-walk"></a><span data-ttu-id="afe81-135">非同期スタックウォーク</span><span class="sxs-lookup"><span data-stu-id="afe81-135">Asynchronous Stack Walk</span></span>  

 <span data-ttu-id="afe81-136">非同期スタックウォークでは、別のスレッドのスタックを調べたり、コールバックに応答せずに現在のスレッドの命令ポインターをハイジャックしたりして、現在のスレッドのスタックを調べます。</span><span class="sxs-lookup"><span data-stu-id="afe81-136">An asynchronous stack walk entails walking the stack of a different thread, or walking the stack of the current thread, not in response to a callback, but by hijacking the current thread's instruction pointer.</span></span> <span data-ttu-id="afe81-137">スタックの最上位が、プラットフォーム呼び出し (PInvoke) または COM 呼び出しの一部ではなく、CLR 自体のヘルパーコードであるアンマネージコードである場合、非同期ウォークにはシードが必要です。</span><span class="sxs-lookup"><span data-stu-id="afe81-137">An asynchronous walk requires a seed if the top of the stack is unmanaged code that is not part of a platform invoke (PInvoke) or COM call, but helper code in the CLR itself.</span></span> <span data-ttu-id="afe81-138">たとえば、ジャストインタイム (JIT) コンパイルまたはガベージコレクションを実行するコードは、ヘルパーコードです。</span><span class="sxs-lookup"><span data-stu-id="afe81-138">For example, code that does just-in-time (JIT) compiling or garbage collection is helper code.</span></span>  
  
 <span data-ttu-id="afe81-139">最上位のマネージフレームが見つかるまで、ターゲットスレッドを直接中断し、自分でスタックを調査することで、シードを取得します。</span><span class="sxs-lookup"><span data-stu-id="afe81-139">You obtain a seed by directly suspending the target thread and walking its stack yourself, until you find the topmost managed frame.</span></span> <span data-ttu-id="afe81-140">ターゲットスレッドが中断された後、ターゲットスレッドの現在のレジスタコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="afe81-140">After the target thread is suspended, get the target thread's current register context.</span></span> <span data-ttu-id="afe81-141">次に、 [ICorProfilerInfo:: GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) を呼び出すことによって、登録コンテキストがアンマネージコードを指しているかどうかを確認します。0と等しいを返す場合 `FunctionID` 、フレームはアンマネージコードです。</span><span class="sxs-lookup"><span data-stu-id="afe81-141">Next, determine whether the register context points to unmanaged code by calling [ICorProfilerInfo::GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md) — if it returns a `FunctionID` equal to zero, the frame is unmanaged code.</span></span> <span data-ttu-id="afe81-142">次に、最初のマネージフレームに達するまでスタックをウォークし、そのフレームのレジスタコンテキストに基づいてシードコンテキストを計算します。</span><span class="sxs-lookup"><span data-stu-id="afe81-142">Now, walk the stack until you reach the first managed frame, and then calculate the seed context based on the register context for that frame.</span></span>  
  
 <span data-ttu-id="afe81-143">`DoStackSnapshot`シードコンテキストでを呼び出して、非同期スタックウォークを開始します。</span><span class="sxs-lookup"><span data-stu-id="afe81-143">Call `DoStackSnapshot` with your seed context to begin the asynchronous stack walk.</span></span> <span data-ttu-id="afe81-144">シードを指定しないと、では `DoStackSnapshot` スタックの一番上にあるマネージフレームがスキップされ、その結果、不完全なスタックウォークが発生します。</span><span class="sxs-lookup"><span data-stu-id="afe81-144">If you do not supply a seed, `DoStackSnapshot` might skip managed frames at the top of the stack and, consequently, will give you an incomplete stack walk.</span></span> <span data-ttu-id="afe81-145">シードを指定する場合は、JIT コンパイルまたはネイティブイメージジェネレーター (Ngen.exe) で生成されたコードをポイントする必要があります。それ以外の場合は、 `DoStackSnapshot` エラーコード CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX を返します。</span><span class="sxs-lookup"><span data-stu-id="afe81-145">If you do supply a seed, it must point to JIT-compiled or Native Image Generator (Ngen.exe)-generated code; otherwise, `DoStackSnapshot` returns the failure code, CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX.</span></span>  
  
 <span data-ttu-id="afe81-146">非同期スタックウォークは、次のガイドラインに従っている場合を除き、デッドロックまたはアクセス違反を簡単に引き起こすことができます。</span><span class="sxs-lookup"><span data-stu-id="afe81-146">Asynchronous stack walks can easily cause deadlocks or access violations, unless you follow these guidelines:</span></span>  
  
- <span data-ttu-id="afe81-147">スレッドを直接中断する場合は、マネージコードを実行していないスレッドだけが別のスレッドを中断できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="afe81-147">When you directly suspend threads, remember that only a thread that has never run managed code can suspend another thread.</span></span>  
  
- <span data-ttu-id="afe81-148">[ICorProfilerCallback:: ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md)コールバックは、そのスレッドのスタックウォークが完了するまで常にブロックします。</span><span class="sxs-lookup"><span data-stu-id="afe81-148">Always block in your [ICorProfilerCallback::ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md) callback until that thread's stack walk is complete.</span></span>  
  
- <span data-ttu-id="afe81-149">プロファイラーがガベージコレクションをトリガーできる CLR 関数を呼び出している間は、ロックを保持しないでください。</span><span class="sxs-lookup"><span data-stu-id="afe81-149">Do not hold a lock while your profiler calls into a CLR function that can trigger a garbage collection.</span></span> <span data-ttu-id="afe81-150">つまり、所有スレッドがガベージコレクションをトリガーする呼び出しを行う場合は、ロックを保持しません。</span><span class="sxs-lookup"><span data-stu-id="afe81-150">That is, do not hold a lock if the owning thread might make a call that triggers a garbage collection.</span></span>  
  
 <span data-ttu-id="afe81-151">また、 `DoStackSnapshot` プロファイラーによって作成されたスレッドからを呼び出した場合に、別のターゲットスレッドのスタックを調べることができるように、デッドロックのリスクもあります。</span><span class="sxs-lookup"><span data-stu-id="afe81-151">There is also a risk of deadlock if you call `DoStackSnapshot` from a thread that your profiler has created so that you can walk the stack of a separate target thread.</span></span> <span data-ttu-id="afe81-152">最初に作成したスレッドが特定の `ICorProfilerInfo*` メソッド (を含む) を入力すると、clr はスレッド `DoStackSnapshot` ごとに clr 固有の初期化を実行します。</span><span class="sxs-lookup"><span data-stu-id="afe81-152">The first time the thread you created enters certain `ICorProfilerInfo*` methods (including `DoStackSnapshot`), the CLR will perform per-thread, CLR-specific initialization on that thread.</span></span> <span data-ttu-id="afe81-153">プロファイラーが、ウォークしようとしているスタックを持つターゲットスレッドを中断し、そのターゲットスレッドがこのスレッドごとの初期化を実行するために必要なロックを所有していた場合、デッドロックが発生します。</span><span class="sxs-lookup"><span data-stu-id="afe81-153">If your profiler has suspended the target thread whose stack you are trying to walk, and if that target thread happened to own a lock necessary for performing this per-thread initialization, a deadlock will occur.</span></span> <span data-ttu-id="afe81-154">このデッドロックを回避するには、プロファイラーによっ `DoStackSnapshot` て作成されたスレッドからへの最初の呼び出しを行い、個別のターゲットスレッドをウォークしますが、先にターゲットスレッドを中断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="afe81-154">To avoid this deadlock, make an initial call into `DoStackSnapshot` from your profiler-created thread to walk a separate target thread, but do not suspend the target thread first.</span></span> <span data-ttu-id="afe81-155">この最初の呼び出しにより、スレッドごとの初期化がデッドロックなしで完了することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="afe81-155">This initial call ensures that the per-thread initialization can complete without deadlock.</span></span> <span data-ttu-id="afe81-156">が `DoStackSnapshot` 成功し、少なくとも1つのフレームを報告した場合は、その時点以降に、プロファイラーによって作成されたスレッドは、任意のターゲットスレッドを中断し、を呼び出して `DoStackSnapshot` ターゲットスレッドのスタックをたどることができます。</span><span class="sxs-lookup"><span data-stu-id="afe81-156">If `DoStackSnapshot` succeeds and reports at least one frame, after that point, it will be safe for that profiler-created thread to suspend any target thread and call `DoStackSnapshot` to walk the stack of that target thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afe81-157">要件</span><span class="sxs-lookup"><span data-stu-id="afe81-157">Requirements</span></span>  

 <span data-ttu-id="afe81-158">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afe81-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afe81-159">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="afe81-159">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="afe81-160">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afe81-160">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afe81-161">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afe81-161">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afe81-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="afe81-162">See also</span></span>

- [<span data-ttu-id="afe81-163">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="afe81-163">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="afe81-164">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="afe81-164">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
