---
title: COR_PRF_SUSPEND_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: f7d76c72ed5db95425f5b1fa2db5e4346983daa4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696675"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="86e06-102">COR_PRF_SUSPEND_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="86e06-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>

<span data-ttu-id="86e06-103">ランタイムが中断された理由を示します。</span><span class="sxs-lookup"><span data-stu-id="86e06-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e06-104">構文</span><span class="sxs-lookup"><span data-stu-id="86e06-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="86e06-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="86e06-105">Members</span></span>  
  
|<span data-ttu-id="86e06-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="86e06-106">Member</span></span>|<span data-ttu-id="86e06-107">説明</span><span class="sxs-lookup"><span data-stu-id="86e06-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="86e06-108">ランタイムは、不特定の理由で中断されています。</span><span class="sxs-lookup"><span data-stu-id="86e06-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="86e06-109">ランタイムは、ガベージコレクション要求を処理するために中断されています。</span><span class="sxs-lookup"><span data-stu-id="86e06-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="86e06-110">ガベージコレクションに関連するコールバックは、 [ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) と [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) コールバックの間で発生します。</span><span class="sxs-lookup"><span data-stu-id="86e06-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="86e06-111">をシャットダウンできるように、ランタイムは中断されてい `AppDomain` ます。</span><span class="sxs-lookup"><span data-stu-id="86e06-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="86e06-112">ランタイムが中断されている間、ランタイムは、シャットダウンされている内のスレッドを特定 `AppDomain` し、再開時に中止するように設定します。</span><span class="sxs-lookup"><span data-stu-id="86e06-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="86e06-113">`AppDomain`この中断期間中は、固有のコールバックはありません。</span><span class="sxs-lookup"><span data-stu-id="86e06-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="86e06-114">コードピッチが発生するようにランタイムが中断されています。</span><span class="sxs-lookup"><span data-stu-id="86e06-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="86e06-115">Code ピッチ ensues は、just-in-time (JIT) コンパイラがアクティブであり、コードピッチが有効になっている場合にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="86e06-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="86e06-116">コードピッチコールバックは、 `ICorProfilerCallback::RuntimeSuspendFinished` コールバックとコールバックの間で発生し `ICorProfilerCallback::RuntimeResumeStarted` ます。</span><span class="sxs-lookup"><span data-stu-id="86e06-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="86e06-117">**注:**  CLR JIT は .NET Framework バージョン2.0 の関数のピッチを調整しないため、この値は2.0 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="86e06-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="86e06-118">ランタイムは、シャットダウンできるように中断されています。</span><span class="sxs-lookup"><span data-stu-id="86e06-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="86e06-119">操作を完了するには、すべてのスレッドを中断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86e06-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="86e06-120">ランタイムは、インプロセスデバッグのために中断されています。</span><span class="sxs-lookup"><span data-stu-id="86e06-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="86e06-121">ランタイムは、ガベージコレクションの準備のために中断されています。</span><span class="sxs-lookup"><span data-stu-id="86e06-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="86e06-122">ランタイムは JIT 再コンパイルのために中断されています。</span><span class="sxs-lookup"><span data-stu-id="86e06-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86e06-123">注釈</span><span class="sxs-lookup"><span data-stu-id="86e06-123">Remarks</span></span>  

 <span data-ttu-id="86e06-124">アンマネージコード内のすべてのランタイムスレッドは、ランタイムを再入力しようとするまで実行を継続することができます。ランタイムは、ランタイムが再開されるまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="86e06-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="86e06-125">これは、ランタイムに入る新しいスレッドにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="86e06-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="86e06-126">ランタイム内のすべてのスレッドは、中断可能なコードに含まれている場合はすぐに中断されます。または、中断可能なコードに到着したときに中断するように求められます。</span><span class="sxs-lookup"><span data-stu-id="86e06-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86e06-127">要件</span><span class="sxs-lookup"><span data-stu-id="86e06-127">Requirements</span></span>  

 <span data-ttu-id="86e06-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86e06-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e06-129">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86e06-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86e06-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86e06-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86e06-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86e06-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e06-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="86e06-132">See also</span></span>

- [<span data-ttu-id="86e06-133">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="86e06-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
