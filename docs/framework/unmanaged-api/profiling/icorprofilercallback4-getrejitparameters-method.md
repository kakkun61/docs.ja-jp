---
title: ICorProfilerCallback4::GetReJITParameters メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: 2cee763674da7472ca48355e7eaba3b7dfb7adbe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730306"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a><span data-ttu-id="27f1b-102">ICorProfilerCallback4::GetReJITParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="27f1b-102">ICorProfilerCallback4::GetReJITParameters Method</span></span>

<span data-ttu-id="27f1b-103">再コンパイルされた新しいメソッド本体の代替コード生成フラグをコードプロファイラーで設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="27f1b-103">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f1b-104">構文</span><span class="sxs-lookup"><span data-stu-id="27f1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27f1b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27f1b-105">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="27f1b-106">からCLR が JIT 再コンパイルパラメーターを必要とするメソッドを含むモジュール。</span><span class="sxs-lookup"><span data-stu-id="27f1b-106">[in] The module that contains the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `methodId`  
 <span data-ttu-id="27f1b-107">から `MethodDef` CLR が JIT 再コンパイルパラメーターを必要とするメソッドの。</span><span class="sxs-lookup"><span data-stu-id="27f1b-107">[in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.</span></span>  
  
 `pFunctionControl`  
 <span data-ttu-id="27f1b-108">から再コンパイルされるメソッドの JIT 再コンパイル情報を提供するためにプロファイラーが使用できる [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) インターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="27f1b-108">[in] A pointer to an [ICorProfilerFunctionControl](icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27f1b-109">注釈</span><span class="sxs-lookup"><span data-stu-id="27f1b-109">Remarks</span></span>  

 <span data-ttu-id="27f1b-110">CLR は、 `GetReJITParameters` 指定されたメソッドを再コンパイルするためのパラメーターをプロファイラーが指定できるように、コールバックを発行します。</span><span class="sxs-lookup"><span data-stu-id="27f1b-110">The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method.</span></span> <span data-ttu-id="27f1b-111">`GetReJITParameters`コールバックは、関数ごとに1回だけ発行されます。プロファイラーによって提供されるパラメーターは、その関数のすべてのインスタンスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="27f1b-111">The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27f1b-112">要件</span><span class="sxs-lookup"><span data-stu-id="27f1b-112">Requirements</span></span>  

 <span data-ttu-id="27f1b-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27f1b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f1b-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27f1b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27f1b-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27f1b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27f1b-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27f1b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f1b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="27f1b-117">See also</span></span>

- [<span data-ttu-id="27f1b-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27f1b-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="27f1b-119">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27f1b-119">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="27f1b-120">JITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="27f1b-120">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="27f1b-121">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="27f1b-121">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
