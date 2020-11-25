---
title: ICorProfilerCallback::ExceptionSearchCatcherFound メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: ef25d55defee2fdcfc7d744e481060eb7a7782ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699886"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="a0f8f-102">ICorProfilerCallback::ExceptionSearchCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="a0f8f-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>

<span data-ttu-id="a0f8f-103">例外処理の検索フェーズによってスローされた例外のハンドラーが見つかったことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a0f8f-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f8f-104">構文</span><span class="sxs-lookup"><span data-stu-id="a0f8f-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0f8f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0f8f-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="a0f8f-106">\[in] 例外ハンドラーを含む関数の ID。</span><span class="sxs-lookup"><span data-stu-id="a0f8f-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="a0f8f-107">要件</span><span class="sxs-lookup"><span data-stu-id="a0f8f-107">Requirements</span></span>  

 <span data-ttu-id="a0f8f-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0f8f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0f8f-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0f8f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0f8f-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0f8f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0f8f-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0f8f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0f8f-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0f8f-112">See also</span></span>

- [<span data-ttu-id="a0f8f-113">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0f8f-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
