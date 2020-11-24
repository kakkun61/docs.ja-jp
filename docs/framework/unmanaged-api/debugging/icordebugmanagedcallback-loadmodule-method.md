---
title: ICorDebugManagedCallback::LoadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 698a5cb88884febc4dfb3b916c00df20c1a77819
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679651"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="ccdce-102">ICorDebugManagedCallback::LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="ccdce-102">ICorDebugManagedCallback::LoadModule Method</span></span>

<span data-ttu-id="ccdce-103">共通言語ランタイム (CLR) モジュールが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ccdce-103">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccdce-104">構文</span><span class="sxs-lookup"><span data-stu-id="ccdce-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccdce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccdce-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="ccdce-106">からモジュールが読み込まれたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccdce-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="ccdce-107">からCLR モジュールを表す、のモジュールオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccdce-107">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccdce-108">注釈</span><span class="sxs-lookup"><span data-stu-id="ccdce-108">Remarks</span></span>  

 <span data-ttu-id="ccdce-109">`LoadModule`コールバックは、モジュールのメタデータを確認したり、just-in-time (JIT) コンパイラフラグを設定したり、モジュールのクラス読み込みコールバックを有効または無効にしたりするための適切な時間を提供します。</span><span class="sxs-lookup"><span data-stu-id="ccdce-109">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccdce-110">要件</span><span class="sxs-lookup"><span data-stu-id="ccdce-110">Requirements</span></span>  

 <span data-ttu-id="ccdce-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ccdce-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccdce-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccdce-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccdce-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccdce-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccdce-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccdce-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccdce-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccdce-115">See also</span></span>

- [<span data-ttu-id="ccdce-116">UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="ccdce-116">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="ccdce-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ccdce-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
