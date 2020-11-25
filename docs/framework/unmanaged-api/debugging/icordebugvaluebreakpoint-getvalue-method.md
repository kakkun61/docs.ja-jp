---
title: ICorDebugValueBreakpoint::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugValueBreakpoint interface [.NET Framework debugging]
- ICorDebugValueBreakpoint::GetValue method [.NET Framework debugging]
ms.assetid: 52a73654-bc47-48b6-b2b1-a4456b10140c
topic_type:
- apiref
ms.openlocfilehash: 8b0ab22d4a782bb21e09d29c9121ef83782a4571
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722324"
---
# <a name="icordebugvaluebreakpointgetvalue-method"></a><span data-ttu-id="1eaea-102">ICorDebugValueBreakpoint::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="1eaea-102">ICorDebugValueBreakpoint::GetValue Method</span></span>

<span data-ttu-id="1eaea-103">ブレークポイントが設定されているオブジェクトの値を表す "ICorDebugValue" オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="1eaea-103">Gets an interface pointer to an "ICorDebugValue" object that represents the value of the object on which the breakpoint is set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1eaea-104">構文</span><span class="sxs-lookup"><span data-stu-id="1eaea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1eaea-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1eaea-105">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="1eaea-106">入出力オブジェクトのアドレスへのポインター `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="1eaea-106">[out] A pointer to the address of an `ICorDebugValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1eaea-107">要件</span><span class="sxs-lookup"><span data-stu-id="1eaea-107">Requirements</span></span>  

 <span data-ttu-id="1eaea-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1eaea-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1eaea-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1eaea-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1eaea-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1eaea-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1eaea-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1eaea-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eaea-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1eaea-112">See also</span></span>
