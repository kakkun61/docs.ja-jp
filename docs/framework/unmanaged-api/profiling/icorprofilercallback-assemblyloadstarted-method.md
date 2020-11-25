---
title: ICorProfilerCallback::AssemblyLoadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadStarted method [.NET Framework profiling]
- AssemblyLoadStarted method [.NET Framework profiling]
ms.assetid: 67e8209d-a0ca-4118-a6e6-c1ee0abc2221
topic_type:
- apiref
ms.openlocfilehash: c2fbc0ae8cdeb79b65cbad9a055a8051acf67e50
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700419"
---
# <a name="icorprofilercallbackassemblyloadstarted-method"></a><span data-ttu-id="31f78-102">ICorProfilerCallback::AssemblyLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="31f78-102">ICorProfilerCallback::AssemblyLoadStarted Method</span></span>

<span data-ttu-id="31f78-103">アセンブリが読み込まれていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="31f78-103">Notifies the profiler that an assembly is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f78-104">構文</span><span class="sxs-lookup"><span data-stu-id="31f78-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadStarted(  
    [in] AssemblyID assemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f78-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31f78-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="31f78-106">\[in] は、読み込むアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="31f78-106">\[in] Identifies the assembly that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="31f78-107">注釈</span><span class="sxs-lookup"><span data-stu-id="31f78-107">Remarks</span></span>  

 <span data-ttu-id="31f78-108">の値 `assemblyId` は、 [ICorProfilerCallback:: AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) メソッドが呼び出されるまで、情報要求に対して無効です。</span><span class="sxs-lookup"><span data-stu-id="31f78-108">The value of `assemblyId` is not valid for an information request until the [ICorProfilerCallback::AssemblyLoadFinished](icorprofilercallback-assemblyloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f78-109">要件</span><span class="sxs-lookup"><span data-stu-id="31f78-109">Requirements</span></span>  

 <span data-ttu-id="31f78-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31f78-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f78-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31f78-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31f78-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31f78-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31f78-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f78-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f78-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="31f78-114">See also</span></span>

- [<span data-ttu-id="31f78-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31f78-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
