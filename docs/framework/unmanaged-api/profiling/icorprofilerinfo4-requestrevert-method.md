---
title: ICorProfilerInfo4::RequestRevert メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: b80de5e0e03f6b3a424ac59a099e361dd6c50c86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733816"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="34bf4-102">ICorProfilerInfo4::RequestRevert メソッド</span><span class="sxs-lookup"><span data-stu-id="34bf4-102">ICorProfilerInfo4::RequestRevert Method</span></span>

<span data-ttu-id="34bf4-103">指定された関数のすべてのインスタンスを元のバージョンに戻します。</span><span class="sxs-lookup"><span data-stu-id="34bf4-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34bf4-104">構文</span><span class="sxs-lookup"><span data-stu-id="34bf4-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34bf4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="34bf4-105">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="34bf4-106">[in] 元に戻す関数の数。</span><span class="sxs-lookup"><span data-stu-id="34bf4-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="34bf4-107">[in] 元に戻す関数を識別する (`module`、`methodDef`) ペアの `moduleId` の部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="34bf4-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="34bf4-108">[in] 元に戻す関数を識別する (`module`、`methodDef`) ペアの `methodId` の部分を指定します。</span><span class="sxs-lookup"><span data-stu-id="34bf4-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="34bf4-109">[out] このトピックの「状態 HRESULT」のセクションで後述する HRESULT の配列。</span><span class="sxs-lookup"><span data-stu-id="34bf4-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="34bf4-110">各 HRESULT は、並列配列 `moduleIds` と `methodIds` で指定された各関数を元に戻す操作の成功または失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="34bf4-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34bf4-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="34bf4-111">Return Value</span></span>  

 <span data-ttu-id="34bf4-112">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="34bf4-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="34bf4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="34bf4-113">HRESULT</span></span>|<span data-ttu-id="34bf4-114">説明</span><span class="sxs-lookup"><span data-stu-id="34bf4-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="34bf4-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="34bf4-115">S_OK</span></span>|<span data-ttu-id="34bf4-116">すべての要求を元に戻す操作が試行されました。ただし、返された状態配列を確認して、どの関数が正常に元に戻されたかを判断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34bf4-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="34bf4-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="34bf4-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="34bf4-118">プロファイラーは、この呼び出しがサポートされるように、 [ICorProfilerCallback4](icorprofilercallback4-interface.md) インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="34bf4-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="34bf4-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="34bf4-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="34bf4-120">JIT 再コンパイルが有効になっていませんでした。</span><span class="sxs-lookup"><span data-stu-id="34bf4-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="34bf4-121">[ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md)メソッドを使用してフラグを設定することにより、初期化中に JIT 再コンパイルを有効にする必要があり `COR_PRF_ENABLE_REJIT` ます。</span><span class="sxs-lookup"><span data-stu-id="34bf4-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="34bf4-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34bf4-122">E_INVALIDARG</span></span>|<span data-ttu-id="34bf4-123">`cFunctions` が 0 であるか、`moduleIds` または `methodIds` が `NULL` です。</span><span class="sxs-lookup"><span data-stu-id="34bf4-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="34bf4-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="34bf4-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="34bf4-125">メモリが不足しているために、CLR は要求を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="34bf4-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="34bf4-126">状態 HRESULT</span><span class="sxs-lookup"><span data-stu-id="34bf4-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="34bf4-127">状態配列 HRESULT</span><span class="sxs-lookup"><span data-stu-id="34bf4-127">Status array HRESULT</span></span>|<span data-ttu-id="34bf4-128">説明</span><span class="sxs-lookup"><span data-stu-id="34bf4-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="34bf4-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="34bf4-129">S_OK</span></span>|<span data-ttu-id="34bf4-130">対応する関数は正常に元に戻されました。</span><span class="sxs-lookup"><span data-stu-id="34bf4-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="34bf4-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="34bf4-131">E_INVALIDARG</span></span>|<span data-ttu-id="34bf4-132">`moduleID` パラメーターまたは `methodDef` パラメーターが `NULL` です。</span><span class="sxs-lookup"><span data-stu-id="34bf4-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="34bf4-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="34bf4-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="34bf4-134">モジュールが完全に読み込まれていないか、またはアンロード中です。</span><span class="sxs-lookup"><span data-stu-id="34bf4-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="34bf4-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="34bf4-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="34bf4-136">指定されたモジュールは (`Reflection.Emit` などにより) 動的に生成されました。</span><span class="sxs-lookup"><span data-stu-id="34bf4-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="34bf4-137">したがって、このメソッドではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="34bf4-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="34bf4-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="34bf4-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="34bf4-139">CLR は、対応するアクティブな再コンパイル要求が見つからなかったために、指定された関数を元に戻すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="34bf4-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="34bf4-140">再コンパイルが要求されていないか、または関数は既に元に戻されています。</span><span class="sxs-lookup"><span data-stu-id="34bf4-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="34bf4-141">その他</span><span class="sxs-lookup"><span data-stu-id="34bf4-141">Other</span></span>|<span data-ttu-id="34bf4-142">オペレーティング システムは、CLR 制御範囲外のエラーを返しました。</span><span class="sxs-lookup"><span data-stu-id="34bf4-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="34bf4-143">たとえば、メモリ ページのアクセスの保護を変更するシステム コールに失敗した場合、オペレーティング システムのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="34bf4-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34bf4-144">注釈</span><span class="sxs-lookup"><span data-stu-id="34bf4-144">Remarks</span></span>  

 <span data-ttu-id="34bf4-145">次に、元に戻された関数のいずれかのインスタンスが呼び出されると、その関数の元のバージョンが実行されます。</span><span class="sxs-lookup"><span data-stu-id="34bf4-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="34bf4-146">既に実行中の関数は、実行中のバージョンの実行を完了させます。</span><span class="sxs-lookup"><span data-stu-id="34bf4-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34bf4-147">要件</span><span class="sxs-lookup"><span data-stu-id="34bf4-147">Requirements</span></span>  

 <span data-ttu-id="34bf4-148">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="34bf4-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34bf4-149">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34bf4-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34bf4-150">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34bf4-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34bf4-151">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34bf4-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34bf4-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="34bf4-152">See also</span></span>

- [<span data-ttu-id="34bf4-153">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="34bf4-153">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="34bf4-154">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="34bf4-154">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="34bf4-155">プロファイル</span><span class="sxs-lookup"><span data-stu-id="34bf4-155">Profiling</span></span>](index.md)
