---
title: ICorProfilerCallback::RuntimeThreadResumed メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: 0996d7eb5b7354a67106ec7aa8818d5e4d46232e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717262"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="5f86c-102">ICorProfilerCallback::RuntimeThreadResumed メソッド</span><span class="sxs-lookup"><span data-stu-id="5f86c-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>

<span data-ttu-id="5f86c-103">指定したスレッドが中断された後に再開されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5f86c-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f86c-104">構文</span><span class="sxs-lookup"><span data-stu-id="5f86c-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f86c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5f86c-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="5f86c-106">から再開されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="5f86c-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f86c-107">要件</span><span class="sxs-lookup"><span data-stu-id="5f86c-107">Requirements</span></span>  

 <span data-ttu-id="5f86c-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5f86c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f86c-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f86c-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f86c-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f86c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f86c-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f86c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f86c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f86c-112">See also</span></span>

- [<span data-ttu-id="5f86c-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5f86c-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="5f86c-114">RuntimeThreadSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="5f86c-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
