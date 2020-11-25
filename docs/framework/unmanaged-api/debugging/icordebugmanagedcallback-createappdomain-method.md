---
title: ICorDebugManagedCallback::CreateAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateAppDomain
helpviewer_keywords:
- CreateAppDomain method [.NET Framework debugging]
- ICorDebugManagedCallback::CreateAppDomain method [.NET Framework debugging]
ms.assetid: 48d410d7-6749-4125-a8fd-f9562c7088e9
topic_type:
- apiref
ms.openlocfilehash: 5f831f0f42231f594e170567535af75216e68c45
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721310"
---
# <a name="icordebugmanagedcallbackcreateappdomain-method"></a><span data-ttu-id="7aaa1-102">ICorDebugManagedCallback::CreateAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="7aaa1-102">ICorDebugManagedCallback::CreateAppDomain Method</span></span>

<span data-ttu-id="7aaa1-103">アプリケーションドメインが作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="7aaa1-103">Notifies the debugger that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7aaa1-104">構文</span><span class="sxs-lookup"><span data-stu-id="7aaa1-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAppDomain (  
    [in] ICorDebugProcess   *pProcess,  
    [in] ICorDebugAppDomain *pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7aaa1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7aaa1-105">Parameters</span></span>  

 `pProcess`  
 <span data-ttu-id="7aaa1-106">からアプリケーションドメインが作成されたプロセスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7aaa1-106">[in] A pointer to an ICorDebugProcess object that represents the process in which the application domain was created.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="7aaa1-107">から作成されたアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="7aaa1-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that has been created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7aaa1-108">要件</span><span class="sxs-lookup"><span data-stu-id="7aaa1-108">Requirements</span></span>  

 <span data-ttu-id="7aaa1-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7aaa1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7aaa1-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7aaa1-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7aaa1-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7aaa1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7aaa1-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7aaa1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aaa1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="7aaa1-113">See also</span></span>

- [<span data-ttu-id="7aaa1-114">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7aaa1-114">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
