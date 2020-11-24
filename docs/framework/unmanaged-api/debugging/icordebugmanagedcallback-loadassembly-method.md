---
title: ICorDebugManagedCallback::LoadAssembly メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
ms.openlocfilehash: 243a1661ce2910cf1713ef8884bb6ae5422e8013
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679690"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="b924d-102">ICorDebugManagedCallback::LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="b924d-102">ICorDebugManagedCallback::LoadAssembly Method</span></span>

<span data-ttu-id="b924d-103">共通言語ランタイム (CLR) アセンブリが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="b924d-103">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b924d-104">構文</span><span class="sxs-lookup"><span data-stu-id="b924d-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b924d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b924d-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="b924d-106">からアセンブリが読み込まれたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b924d-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="b924d-107">からアセンブリを表す、オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b924d-107">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b924d-108">要件</span><span class="sxs-lookup"><span data-stu-id="b924d-108">Requirements</span></span>  

 <span data-ttu-id="b924d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b924d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b924d-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b924d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b924d-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b924d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b924d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b924d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b924d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b924d-113">See also</span></span>

- [<span data-ttu-id="b924d-114">UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="b924d-114">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="b924d-115">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b924d-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
