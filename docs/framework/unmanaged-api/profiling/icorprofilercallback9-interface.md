---
title: ICorProfilerCallback9 インターフェイス
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 23b91a2a58c6e76b31b94e0fa3661dfbc8e18e33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712769"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="0d2a6-102">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d2a6-102">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="0d2a6-103">[.NET Framework 4.7.2 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="0d2a6-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="0d2a6-104">動的メソッドがガベージコレクションされ、その後アンロードされたことをプロファイラーに通知するために、共通言語ランタイムによって使用されるコールバックメソッドを提供する [ICorProfilerCallback8](icorprofilercallback8-interface.md) のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="0d2a6-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d2a6-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0d2a6-105">Methods</span></span>  
  
|<span data-ttu-id="0d2a6-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="0d2a6-106">Method</span></span>|<span data-ttu-id="0d2a6-107">説明</span><span class="sxs-lookup"><span data-stu-id="0d2a6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d2a6-108">DynamicMethodUnloaded メソッド</span><span class="sxs-lookup"><span data-stu-id="0d2a6-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="0d2a6-109">動的メソッドがガベージコレクションされ、その後アンロードされたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0d2a6-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d2a6-110">要件</span><span class="sxs-lookup"><span data-stu-id="0d2a6-110">Requirements</span></span>  

 <span data-ttu-id="0d2a6-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d2a6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d2a6-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d2a6-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="0d2a6-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0d2a6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0d2a6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d2a6-114">See also</span></span>

- [<span data-ttu-id="0d2a6-115">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d2a6-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0d2a6-116">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d2a6-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="0d2a6-117">ICorProfilerCallback8 DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="0d2a6-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="0d2a6-118">ICorProfilerCallback8 DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="0d2a6-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
