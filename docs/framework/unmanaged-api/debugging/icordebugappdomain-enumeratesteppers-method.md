---
title: ICorDebugAppDomain::EnumerateSteppers メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
ms.openlocfilehash: fd9243d9e0c12b572613694538661fd553e8a487
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715928"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="c9290-102">ICorDebugAppDomain::EnumerateSteppers メソッド</span><span class="sxs-lookup"><span data-stu-id="c9290-102">ICorDebugAppDomain::EnumerateSteppers Method</span></span>

<span data-ttu-id="c9290-103">アプリケーションドメイン内のすべてのアクティブな steppers の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="c9290-103">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9290-104">構文</span><span class="sxs-lookup"><span data-stu-id="c9290-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9290-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c9290-105">Parameters</span></span>  

 `ppSteppers`  
 <span data-ttu-id="c9290-106">入出力アプリケーションドメイン内のすべてのアクティブな steppers の列挙子である、ツールオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c9290-106">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9290-107">要件</span><span class="sxs-lookup"><span data-stu-id="c9290-107">Requirements</span></span>  

 <span data-ttu-id="c9290-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9290-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9290-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9290-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9290-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9290-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9290-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9290-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
