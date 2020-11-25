---
title: ICorDebugObjectValue::IsValueClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
ms.openlocfilehash: 7b637889986425767fd7e1166c73df3301075422
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695284"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a><span data-ttu-id="f9f29-102">ICorDebugObjectValue::IsValueClass メソッド</span><span class="sxs-lookup"><span data-stu-id="f9f29-102">ICorDebugObjectValue::IsValueClass Method</span></span>

<span data-ttu-id="f9f29-103">このオブジェクトの値が値の型であるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="f9f29-103">Gets a value that indicates whether this object value is a value type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f29-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9f29-104">Syntax</span></span>  
  
```cpp  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9f29-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9f29-105">Parameters</span></span>  

 `pbIsValueClass`  
 <span data-ttu-id="f9f29-106">入出力 `true` この "いい Objectvalue" で表されるオブジェクト値が参照型ではなく値型である場合は、ブール値へのポインター。それ以外の場合は、 `pbIsValueClass` が `false` です。</span><span class="sxs-lookup"><span data-stu-id="f9f29-106">[out] A pointer to a Boolean value that is `true` if the object value, represented by this "ICorDebugObjectValue", is a value type rather than a reference type; otherwise, `pbIsValueClass` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9f29-107">要件</span><span class="sxs-lookup"><span data-stu-id="f9f29-107">Requirements</span></span>  

 <span data-ttu-id="f9f29-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9f29-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9f29-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9f29-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9f29-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9f29-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9f29-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9f29-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f29-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9f29-112">See also</span></span>
