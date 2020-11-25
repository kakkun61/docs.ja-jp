---
title: ICorProfilerCallback::ExceptionOSHandlerEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerEnter
helpviewer_keywords:
- ExceptionOSHandlerEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerEnter method [.NET Framework profiling]
ms.assetid: 09238b9b-9359-4780-89dc-2f5e4f57920e
topic_type:
- apiref
ms.openlocfilehash: 273c3cefa2e67a7d8c429982b4da4126168b2830
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699964"
---
# <a name="icorprofilercallbackexceptionoshandlerenter-method"></a><span data-ttu-id="6f280-102">ICorProfilerCallback::ExceptionOSHandlerEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="6f280-102">ICorProfilerCallback::ExceptionOSHandlerEnter Method</span></span>

<span data-ttu-id="6f280-103">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="6f280-103">Not implemented.</span></span> <span data-ttu-id="6f280-104">アンマネージ例外情報を必要とするプロファイラーは、他の方法でこの情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f280-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f280-105">構文</span><span class="sxs-lookup"><span data-stu-id="6f280-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerEnter(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6f280-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="6f280-106">Requirements</span></span>  

 <span data-ttu-id="6f280-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f280-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f280-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f280-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f280-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f280-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f280-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f280-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f280-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f280-111">See also</span></span>

- [<span data-ttu-id="6f280-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f280-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
