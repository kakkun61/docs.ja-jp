---
title: ICorDebugManagedCallback::EvalException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalException
helpviewer_keywords:
- EvalException method [.NET Framework debugging]
- ICorDebugManagedCallback::EvalException method [.NET Framework debugging]
ms.assetid: d6036345-18a3-45c1-a302-b1c6f2dced9b
topic_type:
- apiref
ms.openlocfilehash: 6c59ede004ce02ee3d14a448fc61d1c092bd0d61
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721271"
---
# <a name="icordebugmanagedcallbackevalexception-method"></a><span data-ttu-id="6a88a-102">ICorDebugManagedCallback::EvalException メソッド</span><span class="sxs-lookup"><span data-stu-id="6a88a-102">ICorDebugManagedCallback::EvalException Method</span></span>

<span data-ttu-id="6a88a-103">ハンドルされない例外で評価が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6a88a-103">Notifies the debugger that an evaluation has terminated with an unhandled exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a88a-104">構文</span><span class="sxs-lookup"><span data-stu-id="6a88a-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalException (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a88a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6a88a-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="6a88a-106">から評価が終了したアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a88a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation terminated.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6a88a-107">から評価が終了したスレッドを表す、のスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a88a-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation terminated.</span></span>  
  
 `pEval`  
 <span data-ttu-id="6a88a-108">から評価を実行したコードを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6a88a-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a88a-109">要件</span><span class="sxs-lookup"><span data-stu-id="6a88a-109">Requirements</span></span>  

 <span data-ttu-id="6a88a-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a88a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a88a-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a88a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a88a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a88a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a88a-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a88a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a88a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a88a-114">See also</span></span>

- [<span data-ttu-id="6a88a-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6a88a-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
