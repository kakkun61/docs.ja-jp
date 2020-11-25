---
title: ICorProfilerCallback4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 942ee8234b79c6579acc009960f4571801fc3185
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730293"
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="0540b-102">ICorProfilerCallback4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0540b-102">ICorProfilerCallback4 Interface</span></span>

<span data-ttu-id="0540b-103">プロファイラーに情報を伝達するために共通言語ランタイム (CLR) が使用するコールバックメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0540b-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0540b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-104">Methods</span></span>  
  
|<span data-ttu-id="0540b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-105">Method</span></span>|<span data-ttu-id="0540b-106">説明</span><span class="sxs-lookup"><span data-stu-id="0540b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0540b-107">GetReJITParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-107">GetReJITParameters Method</span></span>](icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="0540b-108">再コンパイルされた新しいメソッド本体の代替コード生成フラグをコードプロファイラーで設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0540b-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="0540b-109">MovedReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-109">MovedReferences2 Method</span></span>](icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="0540b-110">圧縮ガベージコレクションの結果として、ヒープ内のオブジェクトの新しいレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="0540b-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="0540b-111">ReJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-111">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="0540b-112">Just-in-time (JIT) コンパイラが関数の再コンパイルを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0540b-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="0540b-113">ReJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-113">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="0540b-114">Just-in-time (JIT) コンパイラが関数の再コンパイルを開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0540b-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="0540b-115">ReJITError メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-115">ReJITError Method</span></span>](icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="0540b-116">Recompile 要求の処理中に発生したエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="0540b-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="0540b-117">SurvivingReferences2 メソッド</span><span class="sxs-lookup"><span data-stu-id="0540b-117">SurvivingReferences2 Method</span></span>](icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="0540b-118">非圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトのレイアウトを報告します。</span><span class="sxs-lookup"><span data-stu-id="0540b-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0540b-119">解説</span><span class="sxs-lookup"><span data-stu-id="0540b-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0540b-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="0540b-120">Requirements</span></span>  

 <span data-ttu-id="0540b-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0540b-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0540b-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0540b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0540b-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0540b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0540b-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0540b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0540b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0540b-125">See also</span></span>

- [<span data-ttu-id="0540b-126">ICorProfilerCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0540b-126">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="0540b-127">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0540b-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0540b-128">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0540b-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
