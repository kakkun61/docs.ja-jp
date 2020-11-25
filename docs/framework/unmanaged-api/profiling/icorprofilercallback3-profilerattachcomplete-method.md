---
title: ICorProfilerCallback3::ProfilerAttachComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: a16e77619ec85ebdf47a2b821309bbb3af63282b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705320"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="bdd74-102">ICorProfilerCallback3::ProfilerAttachComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="bdd74-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>

<span data-ttu-id="bdd74-103">プロファイラーが [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) および [ICorProfilerInfo3:: enummodules](icorprofilerinfo3-enummodules-method.md) のキャッチアップメソッドを呼び出せるようになったことを示すために、共通言語ランタイム (CLR) によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bdd74-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdd74-104">構文</span><span class="sxs-lookup"><span data-stu-id="bdd74-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bdd74-105">解説</span><span class="sxs-lookup"><span data-stu-id="bdd74-105">Remarks</span></span>  

 <span data-ttu-id="bdd74-106">`ProfilerAttachComplete`コールバックは、 [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)メソッドが呼び出された後に発行されます。</span><span class="sxs-lookup"><span data-stu-id="bdd74-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="bdd74-107">これは、次のことを示します。</span><span class="sxs-lookup"><span data-stu-id="bdd74-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="bdd74-108">`InitializeForAttach` でプロファイラーによって要求されたコールバックがアクティブ化されました。</span><span class="sxs-lookup"><span data-stu-id="bdd74-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="bdd74-109">プロファイラーは、通知されないことを心配せずに、関連付けられた ID でキャッチアップを実行できます。</span><span class="sxs-lookup"><span data-stu-id="bdd74-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="bdd74-110">CLR はこのコールバックからの戻り値を無視します。</span><span class="sxs-lookup"><span data-stu-id="bdd74-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdd74-111">要件</span><span class="sxs-lookup"><span data-stu-id="bdd74-111">Requirements</span></span>  

 <span data-ttu-id="bdd74-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bdd74-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdd74-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bdd74-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bdd74-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdd74-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdd74-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdd74-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdd74-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bdd74-116">See also</span></span>

- [<span data-ttu-id="bdd74-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdd74-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="bdd74-118">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdd74-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="bdd74-119">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bdd74-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="bdd74-120">プロファイル</span><span class="sxs-lookup"><span data-stu-id="bdd74-120">Profiling</span></span>](index.md)
