---
title: ICorProfilerCallback9::D ynamicMethodUnloaded メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9.DynamicMethodUnloaded
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e6fe3430696c16405d4ae414436bb12882c08a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732349"
---
# <a name="icorprofilercallback9dynamicmethodunloaded-method"></a><span data-ttu-id="701ef-102">ICorProfilerCallback9::D ynamicMethodUnloaded メソッド</span><span class="sxs-lookup"><span data-stu-id="701ef-102">ICorProfilerCallback9::DynamicMethodUnloaded Method</span></span>

<span data-ttu-id="701ef-103">[.NET Framework 4.7.2 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="701ef-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  
  
<span data-ttu-id="701ef-104">動的メソッドがガベージコレクションされ、その後アンロードされるたびに、プロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="701ef-104">Notifies the profiler whenever a dynamic method is garbage collected and subsequently unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701ef-105">構文</span><span class="sxs-lookup"><span data-stu-id="701ef-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodUnloaded(  
     [in]  FunctionID  functionId
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="701ef-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="701ef-106">Parameters</span></span>  

<span data-ttu-id="701ef-107">[入力] `functionId`</span><span class="sxs-lookup"><span data-stu-id="701ef-107">[in] `functionId`</span></span>  
<span data-ttu-id="701ef-108">ガベージコレクションおよびアンロードされたメモリ内の関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="701ef-108">The identifier of the in-memory function that has been garbage collected and unloaded.</span></span>

## <a name="requirements"></a><span data-ttu-id="701ef-109">要件</span><span class="sxs-lookup"><span data-stu-id="701ef-109">Requirements</span></span>  

 <span data-ttu-id="701ef-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="701ef-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="701ef-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="701ef-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="701ef-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="701ef-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="701ef-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="701ef-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="701ef-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="701ef-114">See also</span></span>

- [<span data-ttu-id="701ef-115">ICorProfilerCallback8 DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="701ef-115">ICorProfilerCallback8.DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="701ef-116">ICorProfilerCallback8 DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="701ef-116">ICorProfilerCallback8.DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="701ef-117">ICorProfilerCallback9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="701ef-117">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="701ef-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span><span class="sxs-lookup"><span data-stu-id="701ef-118">COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS</span></span>](cor-prf-high-monitor-enumeration.md)
