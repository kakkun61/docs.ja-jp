---
title: ICorProfilerCallback4::ReJITCompilationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: a6c2209433a652523fd8e3a7cc2db1272600e1bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730267"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="11216-102">ICorProfilerCallback4::ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="11216-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>

<span data-ttu-id="11216-103">Just-in-time (JIT) コンパイラが関数の再コンパイルを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="11216-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11216-104">構文</span><span class="sxs-lookup"><span data-stu-id="11216-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11216-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11216-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="11216-106">から再コンパイルされた関数の ID。</span><span class="sxs-lookup"><span data-stu-id="11216-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="11216-107">[in] JIT 再コンパイルされた関数のID。</span><span class="sxs-lookup"><span data-stu-id="11216-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="11216-108">からJIT 再コンパイルが成功したかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="11216-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="11216-109">[入力] `true` ブロックが原因で、ランタイムが呼び出し元のスレッドがこのコールバックから戻るのを待機する場合があることを示します。 `false` ブロックがランタイムの動作に影響を与えないことを示す場合。</span><span class="sxs-lookup"><span data-stu-id="11216-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="11216-110">の値は、 `true` ランタイムには影響しませんが、プロファイルの結果に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11216-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11216-111">要件</span><span class="sxs-lookup"><span data-stu-id="11216-111">Requirements</span></span>  

 <span data-ttu-id="11216-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11216-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11216-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11216-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11216-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11216-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11216-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11216-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11216-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="11216-116">See also</span></span>

- [<span data-ttu-id="11216-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11216-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="11216-118">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11216-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="11216-119">JITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="11216-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="11216-120">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="11216-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
