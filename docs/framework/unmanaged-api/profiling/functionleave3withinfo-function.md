---
title: FunctionLeave3WithInfo 関数
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: 69ee0ea78e0c7edbb61999ef8fba1791e6f682bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722246"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="7decf-102">FunctionLeave3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="7decf-102">FunctionLeave3WithInfo Function</span></span>

<span data-ttu-id="7decf-103">関数から制御が返されていることをプロファイラーに通知し、スタックフレームと戻り値を取得するために [ICorProfilerInfo3:: GetFunctionLeave3Info メソッド](icorprofilerinfo3-getfunctionleave3info-method.md) に渡すことができるハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="7decf-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7decf-104">構文</span><span class="sxs-lookup"><span data-stu-id="7decf-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7decf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7decf-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="7decf-106">\[in] コントロールが返される関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="7decf-106">\[in] The identifier of the function from which control is returned.</span></span>

- `eltInfo`

  <span data-ttu-id="7decf-107">\[in) 特定のスタックフレームに関する情報を表す不透明なハンドル。</span><span class="sxs-lookup"><span data-stu-id="7decf-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="7decf-108">このハンドルは、渡されるコールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="7decf-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="7decf-109">注釈</span><span class="sxs-lookup"><span data-stu-id="7decf-109">Remarks</span></span>  

 <span data-ttu-id="7decf-110">`FunctionLeave3WithInfo`コールバックメソッドは、関数が呼び出されたことをプロファイラーに通知します。また、プロファイラーは[ICorProfilerInfo3:: GetFunctionLeave3Info メソッド](icorprofilerinfo3-getfunctionleave3info-method.md)を使用して、戻り値を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="7decf-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="7decf-111">戻り値の情報にアクセスするには、 `COR_PRF_ENABLE_FUNCTION_RETVAL` フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7decf-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="7decf-112">プロファイラーは、 [ICorProfilerInfo:: SetEventMask メソッド](icorprofilerinfo-seteventmask-method.md) を使用してイベントフラグを設定し、 [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo メソッド](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) を使用してこの関数の実装を登録できます。</span><span class="sxs-lookup"><span data-stu-id="7decf-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7decf-113">`FunctionLeave3WithInfo`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7decf-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="7decf-114">実装では、ストレージクラス属性を使用する必要があり `__declspec(naked)` ます。</span><span class="sxs-lookup"><span data-stu-id="7decf-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7decf-115">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="7decf-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7decf-116">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7decf-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7decf-117">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7decf-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7decf-118">の実装では `FunctionLeave3WithInfo` 、ガベージコレクションが遅延するため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="7decf-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="7decf-119">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7decf-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7decf-120">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionLeave3WithInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="7decf-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="7decf-121">関数は、 `FunctionLeave3WithInfo` マネージコードを呼び出さないようにするか、マネージメモリの割り当てを任意の方法で発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="7decf-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7decf-122">要件</span><span class="sxs-lookup"><span data-stu-id="7decf-122">Requirements</span></span>  

 <span data-ttu-id="7decf-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7decf-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7decf-124">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="7decf-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7decf-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7decf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7decf-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7decf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7decf-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7decf-127">See also</span></span>

- [<span data-ttu-id="7decf-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="7decf-128">GetFunctionLeave3Info</span></span>](icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="7decf-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="7decf-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="7decf-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="7decf-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="7decf-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="7decf-131">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="7decf-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7decf-132">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="7decf-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7decf-133">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7decf-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="7decf-134">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="7decf-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7decf-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="7decf-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7decf-136">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="7decf-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="7decf-137">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="7decf-138">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="7decf-138">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
