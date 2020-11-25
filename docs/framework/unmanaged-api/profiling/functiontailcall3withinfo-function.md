---
title: FunctionTailcall3WithInfo 関数
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: c23c791197c9925038f71e70409e4ca3ebabb23e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722865"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="f41b9-102">FunctionTailcall3WithInfo 関数</span><span class="sxs-lookup"><span data-stu-id="f41b9-102">FunctionTailcall3WithInfo Function</span></span>

<span data-ttu-id="f41b9-103">現在実行中の関数が別の関数の末尾呼び出しを実行しようとしていることをプロファイラーに通知し、スタックフレームを取得するために [ICorProfilerInfo3:: GetFunctionTailcall3Info メソッド](icorprofilerinfo3-getfunctiontailcall3info-method.md) に渡すことができるハンドルを提供します。</span><span class="sxs-lookup"><span data-stu-id="f41b9-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f41b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="f41b9-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f41b9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f41b9-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="f41b9-106">\[in] 末尾呼び出しを実行しようとしている現在実行中の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="f41b9-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="f41b9-107">\[in) 特定のスタックフレームに関する情報を表す不透明なハンドル。</span><span class="sxs-lookup"><span data-stu-id="f41b9-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="f41b9-108">このハンドルは、渡されるコールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="f41b9-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="f41b9-109">注釈</span><span class="sxs-lookup"><span data-stu-id="f41b9-109">Remarks</span></span>  

 <span data-ttu-id="f41b9-110">`FunctionTailcall3WithInfo`コールバックメソッドは、関数が呼び出されたことをプロファイラーに通知します。また、プロファイラーは[ICorProfilerInfo3:: GetFunctionTailcall3Info メソッド](icorprofilerinfo3-getfunctiontailcall3info-method.md)を使用してスタックフレームを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="f41b9-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="f41b9-111">スタックフレーム情報にアクセスするには、 `COR_PRF_ENABLE_FRAME_INFO` フラグを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f41b9-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="f41b9-112">プロファイラーは、 [ICorProfilerInfo:: SetEventMask メソッド](icorprofilerinfo-seteventmask-method.md) を使用してイベントフラグを設定し、 [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo メソッド](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) を使用してこの関数の実装を登録できます。</span><span class="sxs-lookup"><span data-stu-id="f41b9-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="f41b9-113">`FunctionTailcall3WithInfo`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f41b9-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="f41b9-114">実装では、ストレージクラス属性を使用する必要があり `__declspec(naked)` ます。</span><span class="sxs-lookup"><span data-stu-id="f41b9-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="f41b9-115">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="f41b9-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="f41b9-116">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f41b9-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="f41b9-117">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f41b9-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f41b9-118">の実装では `FunctionTailcall3WithInfo` 、ガベージコレクションが遅延するため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="f41b9-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="f41b9-119">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f41b9-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f41b9-120">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionTailcall3WithInfo` ます。</span><span class="sxs-lookup"><span data-stu-id="f41b9-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="f41b9-121">また、FunctionTailcall3WithInfo 関数は、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f41b9-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f41b9-122">要件</span><span class="sxs-lookup"><span data-stu-id="f41b9-122">Requirements</span></span>  

 <span data-ttu-id="f41b9-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f41b9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f41b9-124">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="f41b9-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f41b9-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f41b9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f41b9-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f41b9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f41b9-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="f41b9-127">See also</span></span>

- [<span data-ttu-id="f41b9-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="f41b9-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="f41b9-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="f41b9-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="f41b9-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="f41b9-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="f41b9-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f41b9-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="f41b9-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f41b9-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="f41b9-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="f41b9-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="f41b9-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="f41b9-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="f41b9-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="f41b9-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="f41b9-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="f41b9-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="f41b9-137">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="f41b9-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
