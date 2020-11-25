---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 18aed5c5314fc1057767b599c538952a1d4d6b57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722233"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="52b36-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks メソッド</span><span class="sxs-lookup"><span data-stu-id="52b36-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>

<span data-ttu-id="52b36-103">マネージ関数の "enter"、"leave"、および "tailcall" フックで呼び出されるプロファイラー実装関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="52b36-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52b36-104">構文</span><span class="sxs-lookup"><span data-stu-id="52b36-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52b36-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52b36-105">Parameters</span></span>  

 `pFuncEnter`  
 <span data-ttu-id="52b36-106">から [Functionenter](functionenter-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="52b36-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="52b36-107">から [Functionleave](functionleave-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="52b36-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="52b36-108">から [FunctionTailcall](functiontailcall-function.md) コールバックとして使用される実装へのポインター。</span><span class="sxs-lookup"><span data-stu-id="52b36-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52b36-109">注釈</span><span class="sxs-lookup"><span data-stu-id="52b36-109">Remarks</span></span>  

 <span data-ttu-id="52b36-110">.NET Framework バージョン1.0 では、対応するコールバックを無効にするために、各関数ポインターを null にすることができます。</span><span class="sxs-lookup"><span data-stu-id="52b36-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="52b36-111">一度にアクティブにできるコールバックのセットは1つだけです。</span><span class="sxs-lookup"><span data-stu-id="52b36-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="52b36-112">したがって、プロファイラーが `SetEnterLeaveFunctionHooks` と [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)の両方を呼び出すと、が `SetEnterLeaveFunctionHooks2` 優先されます。</span><span class="sxs-lookup"><span data-stu-id="52b36-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="52b36-113">`SetEnterLeaveFunctionHooks`メソッドを呼び出すことができるのは、プロファイラーの[ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)コールバックからだけです。</span><span class="sxs-lookup"><span data-stu-id="52b36-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52b36-114">要件</span><span class="sxs-lookup"><span data-stu-id="52b36-114">Requirements</span></span>  

 <span data-ttu-id="52b36-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52b36-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52b36-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52b36-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52b36-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52b36-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52b36-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52b36-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b36-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="52b36-119">See also</span></span>

- [<span data-ttu-id="52b36-120">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52b36-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
