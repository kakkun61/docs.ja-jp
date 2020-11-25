---
title: ICorDebugManagedCallback2::FunctionRemapComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
ms.openlocfilehash: 7eb7fb55a5077d2914eb85a67ca62163a1aa8cc0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704592"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a><span data-ttu-id="5fdcc-102">ICorDebugManagedCallback2::FunctionRemapComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="5fdcc-102">ICorDebugManagedCallback2::FunctionRemapComplete Method</span></span>

<span data-ttu-id="5fdcc-103">コードの実行が編集された関数の新しいバージョンに切り替わったことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="5fdcc-103">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fdcc-104">構文</span><span class="sxs-lookup"><span data-stu-id="5fdcc-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fdcc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5fdcc-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="5fdcc-106">から編集された関数を含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5fdcc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the edited function.</span></span>  
  
 `pThread`  
 <span data-ttu-id="5fdcc-107">からリマップブレークポイントが検出されたスレッドを表す、スレッドオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5fdcc-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the remap breakpoint was encountered.</span></span>  
  
 `pFunction`  
 <span data-ttu-id="5fdcc-108">からスレッドで現在実行されている関数のバージョンを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5fdcc-108">[in] A pointer to an ICorDebugFunction object that represents the version of the function currently running on the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fdcc-109">注釈</span><span class="sxs-lookup"><span data-stu-id="5fdcc-109">Remarks</span></span>  

 <span data-ttu-id="5fdcc-110">このコールバックは、以前に存在していたすべての steppers を再作成する機会をデバッガーに与えます。</span><span class="sxs-lookup"><span data-stu-id="5fdcc-110">This callback gives the debugger an opportunity to recreate any steppers that previously existed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fdcc-111">要件</span><span class="sxs-lookup"><span data-stu-id="5fdcc-111">Requirements</span></span>  

 <span data-ttu-id="5fdcc-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5fdcc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fdcc-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fdcc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fdcc-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fdcc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fdcc-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fdcc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdcc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5fdcc-116">See also</span></span>

- [<span data-ttu-id="5fdcc-117">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fdcc-117">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="5fdcc-118">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5fdcc-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
