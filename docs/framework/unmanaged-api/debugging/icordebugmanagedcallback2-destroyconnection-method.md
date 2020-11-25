---
title: ICorDebugManagedCallback2::DestroyConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.DestroyConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::DestroyConnection
helpviewer_keywords:
- DestroyConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::DestroyConnection method [.NET Framework debugging]
ms.assetid: cf7940e9-4558-4319-925c-09f6c98c8fcd
topic_type:
- apiref
ms.openlocfilehash: d725cbe89e0631630affb6b0540a7d5f57ab6b89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720114"
---
# <a name="icordebugmanagedcallback2destroyconnection-method"></a><span data-ttu-id="161da-102">ICorDebugManagedCallback2::DestroyConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="161da-102">ICorDebugManagedCallback2::DestroyConnection Method</span></span>

<span data-ttu-id="161da-103">指定された接続が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="161da-103">Notifies the debugger that the specified connection has been terminated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161da-104">構文</span><span class="sxs-lookup"><span data-stu-id="161da-104">Syntax</span></span>  
  
```cpp  
HRESULT DestroyConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="161da-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="161da-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="161da-106">から破棄された接続を含むプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="161da-106">[in] A pointer to an ICorDebugProcess object that represents the process containing the connection that was destroyed.</span></span>  
  
 `dwConnectionId`  
 <span data-ttu-id="161da-107">から破棄された接続の ID。</span><span class="sxs-lookup"><span data-stu-id="161da-107">[in] The ID of the connection that was destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="161da-108">注釈</span><span class="sxs-lookup"><span data-stu-id="161da-108">Remarks</span></span>  

 <span data-ttu-id="161da-109">ホストがホスト `DestroyConnection` [API](../hosting/index.md)で[ICLRDebugManager:: endconnection](../hosting/iclrdebugmanager-endconnection-method.md)を呼び出すと、コールバックが発生します。</span><span class="sxs-lookup"><span data-stu-id="161da-109">A `DestroyConnection` callback will be fired when a host calls [ICLRDebugManager::EndConnection](../hosting/iclrdebugmanager-endconnection-method.md) in the [Hosting API](../hosting/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="161da-110">要件</span><span class="sxs-lookup"><span data-stu-id="161da-110">Requirements</span></span>  

 <span data-ttu-id="161da-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="161da-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="161da-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="161da-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="161da-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="161da-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="161da-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="161da-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161da-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="161da-115">See also</span></span>

- [<span data-ttu-id="161da-116">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="161da-116">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="161da-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="161da-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
