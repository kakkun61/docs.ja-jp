---
title: ICorDebugManagedCallback::NameChange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 0307ad5794d641833c2da1a1674e455ebff24861
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726523"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a><span data-ttu-id="32725-102">ICorDebugManagedCallback::NameChange メソッド</span><span class="sxs-lookup"><span data-stu-id="32725-102">ICorDebugManagedCallback::NameChange Method</span></span>

<span data-ttu-id="32725-103">アプリケーションドメインまたはスレッドの名前が変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="32725-103">Notifies the debugger that the name of either an application domain or a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32725-104">構文</span><span class="sxs-lookup"><span data-stu-id="32725-104">Syntax</span></span>  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32725-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="32725-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="32725-106">から名前が変更されたか、または名前の変更があったスレッドを含むアプリケーションドメインを表す、ツールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="32725-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that either had a name change or that contains the thread that had a name change.</span></span>  
  
 `pThread`  
 <span data-ttu-id="32725-107">から名前の変更があったスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="32725-107">[in] A pointer to an ICorDebugThread object that represents the thread that had a name change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32725-108">要件</span><span class="sxs-lookup"><span data-stu-id="32725-108">Requirements</span></span>  

 <span data-ttu-id="32725-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32725-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32725-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32725-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32725-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32725-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32725-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32725-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32725-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="32725-113">See also</span></span>

- [<span data-ttu-id="32725-114">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="32725-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
