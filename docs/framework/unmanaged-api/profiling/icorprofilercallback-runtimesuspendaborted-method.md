---
title: ICorProfilerCallback::RuntimeSuspendAborted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: 4b6eb59dd771e4013106e6a77fc7475b77b2b007
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732022"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a><span data-ttu-id="c7ab8-102">ICorProfilerCallback::RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="c7ab8-102">ICorProfilerCallback::RuntimeSuspendAborted Method</span></span>

<span data-ttu-id="c7ab8-103">実行中のランタイムの中断をランタイムが中止したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c7ab8-103">Notifies the profiler that the runtime has aborted the runtime suspension that was occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7ab8-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7ab8-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7ab8-105">解説</span><span class="sxs-lookup"><span data-stu-id="c7ab8-105">Remarks</span></span>  

 <span data-ttu-id="c7ab8-106">2つのスレッドが同時にランタイムを中断しようとすると、実行時の中断が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c7ab8-106">The run-time suspension might be aborted if two threads simultaneously attempt to suspend the runtime.</span></span>  
  
 <span data-ttu-id="c7ab8-107">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)コールバックまたは `RuntimeSuspendAborted` コールバックは、 [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)コールバックの後に1つのスレッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="c7ab8-107">Either the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) callback or the `RuntimeSuspendAborted` callback will occur on a single thread following a [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
 <span data-ttu-id="c7ab8-108">コールバックは、 `RuntimeSuspendAborted` コールバックと同じスレッドで行われることが保証され `RuntimeSuspendStarted` ます。</span><span class="sxs-lookup"><span data-stu-id="c7ab8-108">The `RuntimeSuspendAborted` callback is guaranteed to occur on the same thread as the `RuntimeSuspendStarted` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7ab8-109">要件</span><span class="sxs-lookup"><span data-stu-id="c7ab8-109">Requirements</span></span>  

 <span data-ttu-id="c7ab8-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7ab8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7ab8-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c7ab8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c7ab8-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7ab8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7ab8-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7ab8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7ab8-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7ab8-114">See also</span></span>

- [<span data-ttu-id="c7ab8-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7ab8-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
