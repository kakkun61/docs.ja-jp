---
title: ICorProfilerCallback3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: fd482bfe8e95a53cafd1530c88f09df146a1b150
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729435"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="79fa5-102">ICorProfilerCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79fa5-102">ICorProfilerCallback3 Interface</span></span>

<span data-ttu-id="79fa5-103">共通言語ランタイム (CLR) が、プロファイラーにアタッチおよびデタッチ状態情報を伝達するために使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="79fa5-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79fa5-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="79fa5-104">Methods</span></span>  
  
|<span data-ttu-id="79fa5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="79fa5-105">Method</span></span>|<span data-ttu-id="79fa5-106">説明</span><span class="sxs-lookup"><span data-stu-id="79fa5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79fa5-107">InitializeForAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="79fa5-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="79fa5-108">アタッチ操作後にその状態を初期化する機会をプロファイラーに与えるために、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="79fa5-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="79fa5-109">ProfilerAttachComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="79fa5-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="79fa5-110">プロファイラーがキャッチアップメソッドを呼び出せるようになったことを示すために、CLR によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="79fa5-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="79fa5-111">ProfilerDetachSucceeded メソッド</span><span class="sxs-lookup"><span data-stu-id="79fa5-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="79fa5-112">共通言語ランタイム (CLR: Common Language Runtime) がプロファイラー DLL をアンロードしようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="79fa5-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79fa5-113">解説</span><span class="sxs-lookup"><span data-stu-id="79fa5-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79fa5-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="79fa5-114">Requirements</span></span>  

 <span data-ttu-id="79fa5-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79fa5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79fa5-116">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="79fa5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79fa5-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79fa5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79fa5-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79fa5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79fa5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="79fa5-119">See also</span></span>

- [<span data-ttu-id="79fa5-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="79fa5-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="79fa5-121">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79fa5-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="79fa5-122">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79fa5-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="79fa5-123">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79fa5-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
