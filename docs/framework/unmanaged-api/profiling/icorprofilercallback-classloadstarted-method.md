---
title: ICorProfilerCallback::ClassLoadStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
ms.openlocfilehash: fbdc9345c8364f33ac69da452dd91155fd5eede9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700276"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="28404-102">ICorProfilerCallback::ClassLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="28404-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>

<span data-ttu-id="28404-103">クラスが読み込まれていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="28404-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28404-104">構文</span><span class="sxs-lookup"><span data-stu-id="28404-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28404-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28404-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="28404-106">\[in] は、読み込むクラスを識別します。</span><span class="sxs-lookup"><span data-stu-id="28404-106">\[in] Identifies the class that is being loaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="28404-107">注釈</span><span class="sxs-lookup"><span data-stu-id="28404-107">Remarks</span></span>  

 <span data-ttu-id="28404-108">の値 `classId` は、 [ICorProfilerCallback:: ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) メソッドが呼び出されるまで、情報要求に対して無効です。</span><span class="sxs-lookup"><span data-stu-id="28404-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28404-109">要件</span><span class="sxs-lookup"><span data-stu-id="28404-109">Requirements</span></span>  

 <span data-ttu-id="28404-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28404-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28404-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="28404-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="28404-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28404-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28404-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28404-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28404-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="28404-114">See also</span></span>

- [<span data-ttu-id="28404-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="28404-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
