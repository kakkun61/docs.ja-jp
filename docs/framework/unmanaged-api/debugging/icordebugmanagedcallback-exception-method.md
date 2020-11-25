---
title: ICorDebugManagedCallback::Exception メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: 05fed13a556cbcc3b8362e41d73c2b659b1e5eeb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731788"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="6f511-102">ICorDebugManagedCallback::Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="6f511-102">ICorDebugManagedCallback::Exception Method</span></span>

<span data-ttu-id="6f511-103">マネージコードから例外がスローされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6f511-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f511-104">構文</span><span class="sxs-lookup"><span data-stu-id="6f511-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f511-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6f511-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="6f511-106">から例外がスローされたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f511-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="6f511-107">から例外がスローされたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6f511-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="6f511-108">からこの値がの場合、 `false` アプリケーションによって例外がまだ処理されていません。それ以外の場合、例外はハンドルされず、プロセスを終了します。</span><span class="sxs-lookup"><span data-stu-id="6f511-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f511-109">注釈</span><span class="sxs-lookup"><span data-stu-id="6f511-109">Remarks</span></span>  

 <span data-ttu-id="6f511-110">スレッドオブジェクトから特定の例外を取得できます。</span><span class="sxs-lookup"><span data-stu-id="6f511-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f511-111">要件</span><span class="sxs-lookup"><span data-stu-id="6f511-111">Requirements</span></span>  

 <span data-ttu-id="6f511-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f511-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f511-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f511-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f511-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f511-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f511-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f511-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f511-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f511-116">See also</span></span>

- [<span data-ttu-id="6f511-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6f511-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
