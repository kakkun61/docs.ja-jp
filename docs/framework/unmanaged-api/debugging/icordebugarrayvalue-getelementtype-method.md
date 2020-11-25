---
title: ICorDebugArrayValue::GetElementType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementType
helpviewer_keywords:
- ICorDebugArrayValue::GetElementType method [.NET Framework debugging]
- GetElementType method [.NET Framework debugging]
ms.assetid: ed71961e-ae9b-4dfc-9554-06637696d697
topic_type:
- apiref
ms.openlocfilehash: 1deadef7517772460adc96cd0dd630d85cb21c9f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698167"
---
# <a name="icordebugarrayvaluegetelementtype-method"></a><span data-ttu-id="3e003-102">ICorDebugArrayValue::GetElementType メソッド</span><span class="sxs-lookup"><span data-stu-id="3e003-102">ICorDebugArrayValue::GetElementType Method</span></span>

<span data-ttu-id="3e003-103">配列内の要素の単純型を示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="3e003-103">Gets a value that indicates the simple type of the elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e003-104">構文</span><span class="sxs-lookup"><span data-stu-id="3e003-104">Syntax</span></span>  
  
```cpp  
HRESULT GetElementType (  
    [out] CorElementType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e003-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3e003-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="3e003-106">入出力型を示す CorElementType 列挙値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3e003-106">[out] A pointer to a value of the CorElementType enumeration that indicates the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e003-107">要件</span><span class="sxs-lookup"><span data-stu-id="3e003-107">Requirements</span></span>  

 <span data-ttu-id="3e003-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e003-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e003-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e003-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e003-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e003-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e003-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e003-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
