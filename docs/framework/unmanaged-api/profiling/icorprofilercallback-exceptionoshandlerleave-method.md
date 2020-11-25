---
title: ICorProfilerCallback::ExceptionOSHandlerLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: 37e3c9139a202e3cb31bd824d182389ae10b7389
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699925"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="309c6-102">ICorProfilerCallback::ExceptionOSHandlerLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="309c6-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>

<span data-ttu-id="309c6-103">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="309c6-103">Not implemented.</span></span> <span data-ttu-id="309c6-104">アンマネージ例外情報を必要とするプロファイラーは、他の方法でこの情報を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="309c6-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="309c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="309c6-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="309c6-106">必要条件</span><span class="sxs-lookup"><span data-stu-id="309c6-106">Requirements</span></span>  

 <span data-ttu-id="309c6-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="309c6-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="309c6-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="309c6-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="309c6-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="309c6-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="309c6-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="309c6-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309c6-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="309c6-111">See also</span></span>

- [<span data-ttu-id="309c6-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="309c6-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
