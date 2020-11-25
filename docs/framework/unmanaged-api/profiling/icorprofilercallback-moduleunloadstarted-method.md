---
title: ICorProfilerCallback::ModuleUnloadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
ms.openlocfilehash: 12d5f7e073337af6034b8f313a2e0161620a65ea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720959"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="2919e-102">ICorProfilerCallback::ModuleUnloadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="2919e-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>

<span data-ttu-id="2919e-103">モジュールがアンロードされていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2919e-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2919e-104">構文</span><span class="sxs-lookup"><span data-stu-id="2919e-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);
```  
  
## <a name="parameters"></a><span data-ttu-id="2919e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2919e-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="2919e-106">からアンロードされるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="2919e-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2919e-107">注釈</span><span class="sxs-lookup"><span data-stu-id="2919e-107">Remarks</span></span>  

 <span data-ttu-id="2919e-108">の値は、 `moduleId` メソッドから制御が戻った後の情報要求に対して有効ではありません `ModuleUnloadStarted` 。これは、このモジュールに関する情報を取得する最後の機会です。</span><span class="sxs-lookup"><span data-stu-id="2919e-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2919e-109">要件</span><span class="sxs-lookup"><span data-stu-id="2919e-109">Requirements</span></span>  

 <span data-ttu-id="2919e-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2919e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2919e-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2919e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2919e-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2919e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2919e-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2919e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2919e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2919e-114">See also</span></span>

- [<span data-ttu-id="2919e-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2919e-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2919e-116">ModuleUnloadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="2919e-116">ModuleUnloadFinished Method</span></span>](icorprofilercallback-moduleunloadfinished-method.md)
