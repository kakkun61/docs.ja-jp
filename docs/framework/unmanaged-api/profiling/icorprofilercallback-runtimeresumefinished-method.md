---
title: ICorProfilerCallback::RuntimeResumeFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeResumeFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeResumeFinished
helpviewer_keywords:
- RuntimeResumeFinished method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeResumeFinished method [.NET Framework profiling]
ms.assetid: 76de0494-dc49-426b-887d-bee98806a982
topic_type:
- apiref
ms.openlocfilehash: e7bd07205a87ecefb658e01db17100a48681b54b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732035"
---
# <a name="icorprofilercallbackruntimeresumefinished-method"></a><span data-ttu-id="68c4c-102">ICorProfilerCallback::RuntimeResumeFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="68c4c-102">ICorProfilerCallback::RuntimeResumeFinished Method</span></span>

<span data-ttu-id="68c4c-103">ランタイムがすべてのランタイムスレッドを再開し、通常の動作に戻ったことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="68c4c-103">Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c4c-104">構文</span><span class="sxs-lookup"><span data-stu-id="68c4c-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeResumeFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="68c4c-105">解説</span><span class="sxs-lookup"><span data-stu-id="68c4c-105">Remarks</span></span>  

 <span data-ttu-id="68c4c-106">`RuntimeResumeFinished`コールバックは、 [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)コールバックと同じスレッドで実行されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="68c4c-106">The `RuntimeResumeFinished` callback is not guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span> <span data-ttu-id="68c4c-107">ただし、 [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) コールバックと同じスレッドで発生することは保証されています。</span><span class="sxs-lookup"><span data-stu-id="68c4c-107">However, it is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68c4c-108">要件</span><span class="sxs-lookup"><span data-stu-id="68c4c-108">Requirements</span></span>  

 <span data-ttu-id="68c4c-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68c4c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68c4c-110">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="68c4c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="68c4c-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68c4c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68c4c-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68c4c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c4c-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="68c4c-113">See also</span></span>

- [<span data-ttu-id="68c4c-114">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68c4c-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
