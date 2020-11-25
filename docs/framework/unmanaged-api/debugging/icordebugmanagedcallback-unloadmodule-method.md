---
title: ICorDebugManagedCallback::UnloadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
ms.openlocfilehash: f24d49189ee81a80397b94ee4113c9514c083dbc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723988"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a><span data-ttu-id="c2a97-102">ICorDebugManagedCallback::UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="c2a97-102">ICorDebugManagedCallback::UnloadModule Method</span></span>

<span data-ttu-id="c2a97-103">共通言語ランタイムモジュール (DLL) がアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c2a97-103">Notifies the debugger that a common language runtime module (DLL) has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2a97-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2a97-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2a97-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2a97-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="c2a97-106">からモジュールを含んでいるアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c2a97-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the module.</span></span>  
  
 `pModule`  
 <span data-ttu-id="c2a97-107">からモジュールを表す、のモジュールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c2a97-107">[in] A pointer to an ICorDebugModule object that represents the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2a97-108">注釈</span><span class="sxs-lookup"><span data-stu-id="c2a97-108">Remarks</span></span>  

 <span data-ttu-id="c2a97-109">この呼び出しの後にモジュールを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="c2a97-109">The module should not be used after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2a97-110">要件</span><span class="sxs-lookup"><span data-stu-id="c2a97-110">Requirements</span></span>  

 <span data-ttu-id="c2a97-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2a97-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2a97-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2a97-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2a97-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2a97-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2a97-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2a97-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2a97-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2a97-115">See also</span></span>

- [<span data-ttu-id="c2a97-116">LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="c2a97-116">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)
- [<span data-ttu-id="c2a97-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2a97-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
