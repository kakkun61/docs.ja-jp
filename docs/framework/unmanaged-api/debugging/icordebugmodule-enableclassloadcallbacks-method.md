---
title: ICorDebugModule::EnableClassLoadCallbacks メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: 1f6c6ae3b7cb45b049d0fb0d88bbf89121bccfd7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710416"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a><span data-ttu-id="aa84b-102">ICorDebugModule::EnableClassLoadCallbacks メソッド</span><span class="sxs-lookup"><span data-stu-id="aa84b-102">ICorDebugModule::EnableClassLoadCallbacks Method</span></span>

<span data-ttu-id="aa84b-103">このモジュールに対して、" [UnloadClass](icordebugmanagedcallback-unloadclass-method.md) " コール[バック:: loadclass](icordebugmanagedcallback-loadclass-method.md)との各コールバックを呼び出すかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="aa84b-103">Controls whether the [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks are called for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa84b-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa84b-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa84b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa84b-105">Parameters</span></span>  

 `bClassLoadCallbacks`  
 <span data-ttu-id="aa84b-106">からこの値をに設定する `true` と、共通言語ランタイム (CLR) が、 `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` 関連付けられたイベントが発生したときにメソッドとメソッドを呼び出すことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="aa84b-106">[in] Set this value to `true` to enable the common language runtime (CLR) to call the `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` methods when their associated events occur.</span></span>  
  
 <span data-ttu-id="aa84b-107">既定値は `false` 非動的モジュールの場合はです。</span><span class="sxs-lookup"><span data-stu-id="aa84b-107">The default value is `false` for non-dynamic modules.</span></span> <span data-ttu-id="aa84b-108">値は、動的モジュールの場合は常にであり `true` 、変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa84b-108">The value is always `true` for dynamic modules and cannot be changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa84b-109">注釈</span><span class="sxs-lookup"><span data-stu-id="aa84b-109">Remarks</span></span>  

 <span data-ttu-id="aa84b-110">`ICorDebugManagedCallback::LoadClass`および `ICorDebugManagedCallback::UnloadClass` コールバックは動的モジュールに対して常に有効であり、無効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="aa84b-110">The `ICorDebugManagedCallback::LoadClass` and `ICorDebugManagedCallback::UnloadClass` callbacks are always enabled for dynamic modules and cannot be disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa84b-111">要件</span><span class="sxs-lookup"><span data-stu-id="aa84b-111">Requirements</span></span>  

 <span data-ttu-id="aa84b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa84b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa84b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa84b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa84b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa84b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa84b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa84b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa84b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa84b-116">See also</span></span>
