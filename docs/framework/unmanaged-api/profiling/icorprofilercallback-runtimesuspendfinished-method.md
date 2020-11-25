---
title: ICorProfilerCallback::RuntimeSuspendFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: 17dd0cc8d26c328bf6128795f02d751b7ae9e471
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717250"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a><span data-ttu-id="10848-102">ICorProfilerCallback::RuntimeSuspendFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="10848-102">ICorProfilerCallback::RuntimeSuspendFinished Method</span></span>

<span data-ttu-id="10848-103">ランタイムがすべてのランタイムスレッドの中断を完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="10848-103">Notifies the profiler that the runtime has completed suspension of all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10848-104">構文</span><span class="sxs-lookup"><span data-stu-id="10848-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="10848-105">解説</span><span class="sxs-lookup"><span data-stu-id="10848-105">Remarks</span></span>  

 <span data-ttu-id="10848-106">アンマネージコード内のすべてのランタイムスレッドは、ランタイムを再入力しようとするまで実行を継続できます。</span><span class="sxs-lookup"><span data-stu-id="10848-106">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="10848-107">その時点で、ランタイムが再開されるまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="10848-107">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="10848-108">これは、ランタイムに入る新しいスレッドにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="10848-108">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="10848-109">ランタイム内のすべてのスレッドは、割り込み可能なコードに既に存在する場合は直ちに中断されます。または、割り込み可能なコードになると中断するように求められます。</span><span class="sxs-lookup"><span data-stu-id="10848-109">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
 <span data-ttu-id="10848-110">`RuntimeSuspendFinished`コールバックは、 [ICorProfilerCallback:: RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)コールバックと同じスレッドで行われることが保証されています。</span><span class="sxs-lookup"><span data-stu-id="10848-110">The `RuntimeSuspendFinished` callback is guaranteed to occur on the same thread as the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10848-111">要件</span><span class="sxs-lookup"><span data-stu-id="10848-111">Requirements</span></span>  

 <span data-ttu-id="10848-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10848-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10848-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="10848-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10848-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10848-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10848-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10848-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10848-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="10848-116">See also</span></span>

- [<span data-ttu-id="10848-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10848-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="10848-118">RuntimeSuspendAborted メソッド</span><span class="sxs-lookup"><span data-stu-id="10848-118">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
