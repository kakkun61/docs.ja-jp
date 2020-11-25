---
title: ICorProfilerInfo3::RequestProfilerDetach メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
ms.openlocfilehash: 2ea39c94a5a0f3d24d4123d6405115ac75105e26
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721583"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="02e58-102">ICorProfilerInfo3::RequestProfilerDetach メソッド</span><span class="sxs-lookup"><span data-stu-id="02e58-102">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>

<span data-ttu-id="02e58-103">プロファイラーをデタッチするようにランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="02e58-103">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e58-104">構文</span><span class="sxs-lookup"><span data-stu-id="02e58-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02e58-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="02e58-105">Parameters</span></span>  

 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="02e58-106">[in] プロファイラーをアンロードするのが安全かどうかを確認するチェックを行うまでに共通言語ランタイム (CLR) が待機する時間 (ミリ秒)。</span><span class="sxs-lookup"><span data-stu-id="02e58-106">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02e58-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="02e58-107">Return Value</span></span>  

 <span data-ttu-id="02e58-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="02e58-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="02e58-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02e58-109">HRESULT</span></span>|<span data-ttu-id="02e58-110">説明</span><span class="sxs-lookup"><span data-stu-id="02e58-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02e58-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="02e58-111">S_OK</span></span>|<span data-ttu-id="02e58-112">デタッチ要求は有効です。またデタッチ プロシージャは別のスレッドで継続しています。</span><span class="sxs-lookup"><span data-stu-id="02e58-112">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="02e58-113">デタッチが完了すると、`ProfilerDetachSucceeded` イベントが発行されます。</span><span class="sxs-lookup"><span data-stu-id="02e58-113">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="02e58-114">E_CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="02e58-114">E_CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="02e58-115">プロファイラーは、 [ICorProfilerCallback3](icorprofilercallback3-interface.md)インターフェイスの[IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))の試行に失敗しました。デタッチ操作をサポートするには、このインターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02e58-115">The profiler failed an [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) attempt for the [ICorProfilerCallback3](icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="02e58-116">デタッチは試行されませんでした。</span><span class="sxs-lookup"><span data-stu-id="02e58-116">Detach was not attempted.</span></span>|  
|<span data-ttu-id="02e58-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="02e58-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="02e58-118">プロファイラーが起動時に変更できないフラグを設定しているため、デタッチできません。</span><span class="sxs-lookup"><span data-stu-id="02e58-118">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="02e58-119">デタッチは試行されませんでした。プロファイラーは完全にアタッチされたままです。</span><span class="sxs-lookup"><span data-stu-id="02e58-119">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="02e58-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="02e58-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="02e58-121">プロファイラーが MSIL (Microsoft 中間言語) コードまたは挿入フックを使用しているため、デタッチは不可能です `enter` / `leave` 。</span><span class="sxs-lookup"><span data-stu-id="02e58-121">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="02e58-122">デタッチは試行されませんでした。プロファイラーは完全にアタッチされたままです。</span><span class="sxs-lookup"><span data-stu-id="02e58-122">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="02e58-123">**メモ** インストルメント化された MSIL はコードであり、 [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) メソッドを使用してプロファイラーによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="02e58-123">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="02e58-124">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="02e58-124">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="02e58-125">マネージド アプリケーションでランタイムがまだ初期化されていません。</span><span class="sxs-lookup"><span data-stu-id="02e58-125">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="02e58-126">(つまり、ランタイムが完全に読み込まれていません)。このエラーコードは、プロファイラーコールバックの [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) メソッド内でデタッチが要求された場合に返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="02e58-126">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="02e58-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="02e58-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="02e58-128">サポートされていないタイミングで `RequestProfilerDetach` が呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="02e58-128">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="02e58-129">このエラーは、メソッドがマネージスレッドで呼び出されたが、 [ICorProfilerCallback](icorprofilercallback-interface.md) メソッド内、またはガベージコレクションを許容できない [ICorProfilerCallback](icorprofilercallback-interface.md) メソッド内から呼び出されなかった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="02e58-129">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="02e58-130">詳細については、「 [HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02e58-130">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02e58-131">注釈</span><span class="sxs-lookup"><span data-stu-id="02e58-131">Remarks</span></span>  

 <span data-ttu-id="02e58-132">デタッチ プロシージャの実行中に、デタッチ スレッド (プロファイラーのデタッチのために作成されたスレッド) は、すべてのスレッドがプロファイラーのコードを終了したかどうかを時々チェックします。</span><span class="sxs-lookup"><span data-stu-id="02e58-132">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="02e58-133">プロファイラーは、退避が終了するまでの予想時間を、`dwExpectedCompletionMilliseconds` パラメーターを介して提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02e58-133">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="02e58-134">使用に適した値は、特定の `ICorProfilerCallback*` メソッド内でプロファイラーが使う通常の時間です。この値は、プロファイラーが使うと想定される最大時間の半分未満にしないでください。</span><span class="sxs-lookup"><span data-stu-id="02e58-134">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="02e58-135">デタッチ スレッドでは `dwExpectedCompletionMilliseconds` を使用して、プロファイラーのコールバック コードがすべてのスタックからポップされたかどうかをチェックする前にスリープする時間の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="02e58-135">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="02e58-136">次のアルゴリズムの詳細は今後の CLR のリリースで変更される可能性がありますが、これはプロファイラーをアンロードしても安全なタイミングを決定するために `dwExpectedCompletionMilliseconds` を利用する 1 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="02e58-136">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="02e58-137">デタッチ スレッドはまず `dwExpectedCompletionMilliseconds` ミリ秒間、スリープ状態になります。</span><span class="sxs-lookup"><span data-stu-id="02e58-137">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="02e58-138">復帰のスリープ状態を解除した後、プロファイラーのコールバックコードがまだ存在していることが CLR によって検出された場合、この場合は2倍のミリ秒間、デタッチスレッドが再びスリープ状態に `dwExpectedCompletionMilliseconds` なります。</span><span class="sxs-lookup"><span data-stu-id="02e58-138">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="02e58-139">この 2 回目のスリープから復帰した後に、プロファイラーのコールバック コードがまだ存在することがデタッチ スレッドで検出された場合、再チェックが行われる前に 10 分間、スリープ状態になります。</span><span class="sxs-lookup"><span data-stu-id="02e58-139">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="02e58-140">デタッチ スレッドは継続して 10 分ごとに再チェックを行います。</span><span class="sxs-lookup"><span data-stu-id="02e58-140">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="02e58-141">プロファイラーが `dwExpectedCompletionMilliseconds` を 0 (ゼロ) に指定している場合、CLR は既定値 5000 を使用します。この設定では、チェックが 5 秒後に行われ、その次は 10 秒後に、それ以降は 10 分ごとに再チェックが行われます。</span><span class="sxs-lookup"><span data-stu-id="02e58-141">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e58-142">要件</span><span class="sxs-lookup"><span data-stu-id="02e58-142">Requirements</span></span>  

 <span data-ttu-id="02e58-143">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02e58-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02e58-144">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02e58-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02e58-145">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02e58-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02e58-146">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02e58-146">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e58-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="02e58-147">See also</span></span>

- [<span data-ttu-id="02e58-148">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02e58-148">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="02e58-149">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="02e58-149">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="02e58-150">プロファイル</span><span class="sxs-lookup"><span data-stu-id="02e58-150">Profiling</span></span>](index.md)
