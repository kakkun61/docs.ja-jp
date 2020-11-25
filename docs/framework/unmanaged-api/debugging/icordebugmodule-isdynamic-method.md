---
title: ICorDebugModule::IsDynamic メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 98c01993a85ed07d961902d8a098a96df4702c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709831"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="57c03-102">ICorDebugModule::IsDynamic メソッド</span><span class="sxs-lookup"><span data-stu-id="57c03-102">ICorDebugModule::IsDynamic Method</span></span>

<span data-ttu-id="57c03-103">このモジュールが動的かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="57c03-103">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57c03-104">構文</span><span class="sxs-lookup"><span data-stu-id="57c03-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57c03-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57c03-105">Parameters</span></span>  

 `pDynamic`  
 <span data-ttu-id="57c03-106">[出力] `true` このモジュールが動的である場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="57c03-106">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57c03-107">注釈</span><span class="sxs-lookup"><span data-stu-id="57c03-107">Remarks</span></span>  

 <span data-ttu-id="57c03-108">動的モジュールは、モジュールが読み込まれた後でも、新しいクラスを追加したり、既存のクラスを削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="57c03-108">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="57c03-109">は、クラスが追加または削除されたときに、 [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) [Callback:: loadclass](icordebugmanagedcallback-loadclass-method.md)コールバックとによって、デバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="57c03-109">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57c03-110">要件</span><span class="sxs-lookup"><span data-stu-id="57c03-110">Requirements</span></span>  

 <span data-ttu-id="57c03-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57c03-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57c03-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="57c03-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57c03-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57c03-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57c03-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57c03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
