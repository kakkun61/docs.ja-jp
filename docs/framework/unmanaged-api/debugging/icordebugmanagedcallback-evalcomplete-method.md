---
title: ICorDebugManagedCallback::EvalComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
ms.openlocfilehash: e95874447528989af68f5c97825691532195889f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731801"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="b7af3-102">ICorDebugManagedCallback::EvalComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="b7af3-102">ICorDebugManagedCallback::EvalComplete Method</span></span>

<span data-ttu-id="b7af3-103">評価が完了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b7af3-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7af3-104">構文</span><span class="sxs-lookup"><span data-stu-id="b7af3-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7af3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b7af3-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="b7af3-106">から評価が実行されたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7af3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="b7af3-107">から評価が実行されたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7af3-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="b7af3-108">から評価を実行したコードを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7af3-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7af3-109">要件</span><span class="sxs-lookup"><span data-stu-id="b7af3-109">Requirements</span></span>  

 <span data-ttu-id="b7af3-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7af3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7af3-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7af3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7af3-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7af3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7af3-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7af3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7af3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7af3-114">See also</span></span>

- [<span data-ttu-id="b7af3-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7af3-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
