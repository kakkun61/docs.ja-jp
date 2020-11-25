---
title: ICorDebugManagedCallback::EditAndContinueRemap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: 1d8aa2cca9dbbeaa9e03813b177ca59125770803
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721284"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="740fe-102">ICorDebugManagedCallback::EditAndContinueRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="740fe-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>

<span data-ttu-id="740fe-103">このメソッドの使用は非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="740fe-103">This method has been deprecated.</span></span> <span data-ttu-id="740fe-104">これは、マップイベントが統合開発環境 (IDE) に送信されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="740fe-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="740fe-105">構文</span><span class="sxs-lookup"><span data-stu-id="740fe-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="740fe-106">解説</span><span class="sxs-lookup"><span data-stu-id="740fe-106">Remarks</span></span>  

 <span data-ttu-id="740fe-107">更新された `EditAndContinueRemap` 関数の古いバージョンでコードを実行しようとすると、メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="740fe-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="740fe-108">共通言語ランタイムは、メソッドを呼び出して、 `EditAndContinueRemap` リマップイベントを IDE に送信します。</span><span class="sxs-lookup"><span data-stu-id="740fe-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="740fe-109">要件</span><span class="sxs-lookup"><span data-stu-id="740fe-109">Requirements</span></span>  

 <span data-ttu-id="740fe-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="740fe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="740fe-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="740fe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="740fe-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="740fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="740fe-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="740fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="740fe-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="740fe-114">See also</span></span>

- [<span data-ttu-id="740fe-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="740fe-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
