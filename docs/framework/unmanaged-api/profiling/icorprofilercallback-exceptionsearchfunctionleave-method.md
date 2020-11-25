---
title: ICorProfilerCallback::ExceptionSearchFunctionLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
ms.openlocfilehash: 064f87fe0cee8d0ad7efcba478e9cf1954a3f291
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699756"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="4e9fa-102">ICorProfilerCallback::ExceptionSearchFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="4e9fa-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>

<span data-ttu-id="4e9fa-103">例外処理の検索フェーズで関数の検索が終了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4e9fa-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e9fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e9fa-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="4e9fa-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="4e9fa-105">Requirements</span></span>  

 <span data-ttu-id="4e9fa-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e9fa-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e9fa-107">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e9fa-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e9fa-108">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e9fa-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e9fa-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e9fa-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e9fa-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e9fa-110">See also</span></span>

- [<span data-ttu-id="4e9fa-111">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4e9fa-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4e9fa-112">ExceptionSearchFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="4e9fa-112">ExceptionSearchFunctionEnter Method</span></span>](icorprofilercallback-exceptionsearchfunctionenter-method.md)
