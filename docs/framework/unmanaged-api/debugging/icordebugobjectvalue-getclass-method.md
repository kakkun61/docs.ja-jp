---
title: ICorDebugObjectValue::GetClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: 42e5ffeeb81bc5e9a99c8ada8d58296fc9f610d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695401"
---
# <a name="icordebugobjectvaluegetclass-method"></a><span data-ttu-id="b405c-102">ICorDebugObjectValue::GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="b405c-102">ICorDebugObjectValue::GetClass Method</span></span>

<span data-ttu-id="b405c-103">このオブジェクト値のクラスを取得します。</span><span class="sxs-lookup"><span data-stu-id="b405c-103">Gets the class of this object value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b405c-104">構文</span><span class="sxs-lookup"><span data-stu-id="b405c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b405c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b405c-105">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="b405c-106">入出力この "いい Objectvalue" オブジェクトによって表されるオブジェクト値のクラスを表す "のクラス" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b405c-106">[out] A pointer to the address of an "ICorDebugClass" object that represents the class of the object value represented by this "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b405c-107">注釈</span><span class="sxs-lookup"><span data-stu-id="b405c-107">Remarks</span></span>  

 <span data-ttu-id="b405c-108">`GetClass`および[ICorDebugValue:: GetType](icordebugvalue-gettype-method.md)メソッドはそれぞれ、値の型に関する情報を返します。これらはどちらも、ジェネリック対応[ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md)に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b405c-108">The `GetClass` and [ICorDebugValue::GetType](icordebugvalue-gettype-method.md) methods each return information about the type of a value; they are both superseded by the generics-aware [ICorDebugValue2::GetExactType](icordebugvalue2-getexacttype-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b405c-109">要件</span><span class="sxs-lookup"><span data-stu-id="b405c-109">Requirements</span></span>  

 <span data-ttu-id="b405c-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b405c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b405c-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b405c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b405c-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b405c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b405c-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b405c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b405c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b405c-114">See also</span></span>
