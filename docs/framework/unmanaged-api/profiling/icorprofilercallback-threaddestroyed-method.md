---
title: ICorProfilerCallback::ThreadDestroyed メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 0cef868861155d553aba42fe28c3f1f1b86763b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731970"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="133ff-102">ICorProfilerCallback::ThreadDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="133ff-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>

<span data-ttu-id="133ff-103">スレッドが破棄されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="133ff-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="133ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="133ff-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="133ff-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="133ff-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="133ff-106">から破棄されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="133ff-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="133ff-107">注釈</span><span class="sxs-lookup"><span data-stu-id="133ff-107">Remarks</span></span>  

 <span data-ttu-id="133ff-108">`threadId`この呼び出しの時点では、この値は無効になっています。</span><span class="sxs-lookup"><span data-stu-id="133ff-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="133ff-109">要件</span><span class="sxs-lookup"><span data-stu-id="133ff-109">Requirements</span></span>  

 <span data-ttu-id="133ff-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="133ff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="133ff-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="133ff-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="133ff-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="133ff-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="133ff-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="133ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133ff-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="133ff-114">See also</span></span>

- [<span data-ttu-id="133ff-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="133ff-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="133ff-116">ThreadCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="133ff-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
