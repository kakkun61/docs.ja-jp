---
title: ICorDebugManagedCallback::ExitThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: 2ccb06b974cb17dff987ba42b647224cdc4c4ff2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688936"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="f9a0c-102">ICorDebugManagedCallback::ExitThread メソッド</span><span class="sxs-lookup"><span data-stu-id="f9a0c-102">ICorDebugManagedCallback::ExitThread Method</span></span>

<span data-ttu-id="f9a0c-103">マネージコードを実行していたスレッドが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="f9a0c-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a0c-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9a0c-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9a0c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9a0c-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="f9a0c-106">からマネージスレッドを含むアプリケーションドメインを表す、コードの Appdomain オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9a0c-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="f9a0c-107">からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9a0c-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9a0c-108">注釈</span><span class="sxs-lookup"><span data-stu-id="f9a0c-108">Remarks</span></span>  

 <span data-ttu-id="f9a0c-109">`ExitThread`コールバックが発生すると、スレッドはスレッド列挙に表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="f9a0c-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9a0c-110">要件</span><span class="sxs-lookup"><span data-stu-id="f9a0c-110">Requirements</span></span>  

 <span data-ttu-id="f9a0c-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9a0c-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a0c-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9a0c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9a0c-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9a0c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9a0c-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a0c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a0c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9a0c-115">See also</span></span>

- [<span data-ttu-id="f9a0c-116">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9a0c-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
