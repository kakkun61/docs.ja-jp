---
title: FunctionIDMapper2 関数
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: 7aa90b92d129f1269d901f1cbb5c6a0750de9a90
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728538"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="0115d-102">FunctionIDMapper2 関数</span><span class="sxs-lookup"><span data-stu-id="0115d-102">FunctionIDMapper2 Function</span></span>

<span data-ttu-id="0115d-103">指定された関数の識別子が、その関数の [FunctionEnter3](functionenter3-function.md)、 [FunctionLeave3](functionleave3-function.md)、 [FunctionTailcall3](functiontailcall3-function.md)、または[FunctionEnter3WithInfo](functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](functionleave3withinfo-function.md)、および [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) コールバックで使用される代替 ID に再マップされる可能性があることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0115d-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md), or[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="0115d-104">また `FunctionIDMapper2` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="0115d-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0115d-105">構文</span><span class="sxs-lookup"><span data-stu-id="0115d-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0115d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0115d-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="0115d-107">\[in) 再マップする関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="0115d-107">\[in] The function identifier to be remapped.</span></span>

- `clientData`

  <span data-ttu-id="0115d-108">\[では、ランタイム間を明確に区別するために使用されるデータへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0115d-108">\[in] A pointer to data that is used to disambiguate among runtimes.</span></span>

- `pbHookFunction`

  <span data-ttu-id="0115d-109">\[out] プロファイラーが、、、、、、、の各コールバックを受信する場合は、に設定する値へのポインター `true` `FunctionEnter3` `FunctionLeave3` `FunctionTailcall3` `FunctionEnter3WithInfo` `FunctionLeave3WithInfo` `FunctionTailcall3WithInfo` 。それ以外の場合は、この値をに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="0115d-109">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="0115d-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="0115d-110">Return Value</span></span>  

 <span data-ttu-id="0115d-111">プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。</span><span class="sxs-lookup"><span data-stu-id="0115d-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="0115d-112">`false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0115d-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="0115d-113">これ以外の状況で戻り値を null にすると、プロセスの中止など、予測できない結果が発生します。</span><span class="sxs-lookup"><span data-stu-id="0115d-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0115d-114">注釈</span><span class="sxs-lookup"><span data-stu-id="0115d-114">Remarks</span></span>  

 <span data-ttu-id="0115d-115">このメソッドは、クライアントデータを渡すために使用される追加のパラメーターを使用して [Functionidmapper](functionidmapper-function.md) 関数を拡張します。</span><span class="sxs-lookup"><span data-stu-id="0115d-115">This method extends the [FunctionIDMapper](functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="0115d-116">クライアント データを使用すると、ランタイム間のあいまいさが解消されます。</span><span class="sxs-lookup"><span data-stu-id="0115d-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0115d-117">要件</span><span class="sxs-lookup"><span data-stu-id="0115d-117">Requirements</span></span>  

 <span data-ttu-id="0115d-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0115d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0115d-119">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="0115d-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0115d-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0115d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0115d-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0115d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0115d-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0115d-122">See also</span></span>

- [<span data-ttu-id="0115d-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="0115d-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="0115d-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="0115d-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="0115d-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="0115d-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="0115d-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="0115d-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="0115d-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="0115d-127">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="0115d-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0115d-128">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="0115d-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0115d-129">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="0115d-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0115d-130">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="0115d-131">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="0115d-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
