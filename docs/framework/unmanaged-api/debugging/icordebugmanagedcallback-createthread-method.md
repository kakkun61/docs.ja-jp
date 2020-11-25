---
title: ICorDebugManagedCallback::CreateThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 56ec7c56b167c29c9951638c5eee159e1d3c7ffb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721297"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="407a8-102">ICorDebugManagedCallback::CreateThread メソッド</span><span class="sxs-lookup"><span data-stu-id="407a8-102">ICorDebugManagedCallback::CreateThread Method</span></span>

<span data-ttu-id="407a8-103">スレッドがマネージコードの実行を開始したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="407a8-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407a8-104">構文</span><span class="sxs-lookup"><span data-stu-id="407a8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="407a8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="407a8-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="407a8-106">からスレッドを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="407a8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="407a8-107">からスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="407a8-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="407a8-108">注釈</span><span class="sxs-lookup"><span data-stu-id="407a8-108">Remarks</span></span>  

 <span data-ttu-id="407a8-109">スレッドは、実行される最初のマネージコード命令に配置されます。</span><span class="sxs-lookup"><span data-stu-id="407a8-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="407a8-110">要件</span><span class="sxs-lookup"><span data-stu-id="407a8-110">Requirements</span></span>  

 <span data-ttu-id="407a8-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="407a8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="407a8-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="407a8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="407a8-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="407a8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="407a8-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="407a8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407a8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="407a8-115">See also</span></span>

- [<span data-ttu-id="407a8-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="407a8-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
