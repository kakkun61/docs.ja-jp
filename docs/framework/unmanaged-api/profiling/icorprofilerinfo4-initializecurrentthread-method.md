---
title: ICorProfilerInfo4::InitializeCurrentThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: 51f16523c00cc3dd95b786f1586ccfd75ce8d5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733829"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="11388-102">ICorProfilerInfo4::InitializeCurrentThread メソッド</span><span class="sxs-lookup"><span data-stu-id="11388-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>

<span data-ttu-id="11388-103">デッドロックを回避できるように、同じスレッドで、後続のプロファイラー API 呼び出しの前に現在のスレッドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="11388-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11388-104">構文</span><span class="sxs-lookup"><span data-stu-id="11388-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="11388-105">解説</span><span class="sxs-lookup"><span data-stu-id="11388-105">Remarks</span></span>  

 <span data-ttu-id="11388-106">中断された `InitializeCurrentThread` スレッドがある間は、PROFILER API を呼び出すスレッドでを呼び出すことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11388-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="11388-107">このメソッドは、通常、 [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) メソッドを呼び出して、ターゲットスレッドが中断されている間にスタックウォークを実行する独自のスレッドを作成する、サンプリングプロファイラーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="11388-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="11388-108">プロファイラーでは、最初にサンプリングスレッドを作成するときにを呼び出すことによって `InitializeCurrentThread` 、 `DoStackSnapshot` 他のスレッドが中断されていないときに、CLR がの最初の呼び出し時に実行する、スレッドごとの遅延初期化を安全に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="11388-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11388-109">`InitializeCurrentThread` は、ロックを受け取るタスクを完了するために事前に初期化し、デッドロックが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11388-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="11388-110">`InitializeCurrentThread`中断されたスレッドが存在しない場合にのみ、を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="11388-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11388-111">要件</span><span class="sxs-lookup"><span data-stu-id="11388-111">Requirements</span></span>  

 <span data-ttu-id="11388-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11388-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11388-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="11388-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11388-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11388-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11388-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11388-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11388-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="11388-116">See also</span></span>

- [<span data-ttu-id="11388-117">ICorProfilerInfo4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11388-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="11388-118">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="11388-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="11388-119">プロファイル</span><span class="sxs-lookup"><span data-stu-id="11388-119">Profiling</span></span>](index.md)
