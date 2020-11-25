---
title: ICorDebugValue::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 9f5688ae4f76f9ddfde231aa6252d666c9152eec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731082"
---
# <a name="icordebugvaluegetsize-method"></a><span data-ttu-id="70f7d-102">ICorDebugValue::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="70f7d-102">ICorDebugValue::GetSize Method</span></span>

<span data-ttu-id="70f7d-103">この "ICorDebugValue" オブジェクトのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="70f7d-103">Gets the size, in bytes, of this "ICorDebugValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70f7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="70f7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70f7d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="70f7d-105">Parameters</span></span>  

 `pSize`  
 <span data-ttu-id="70f7d-106">入出力この値オブジェクトのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="70f7d-106">[out] The size, in bytes, of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70f7d-107">注釈</span><span class="sxs-lookup"><span data-stu-id="70f7d-107">Remarks</span></span>  

 <span data-ttu-id="70f7d-108">値の型が参照型の場合、このメソッドはオブジェクトのサイズではなく、ポインターのサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="70f7d-108">If the value's type is a reference type, this method returns the size of the pointer rather than the size of the object.</span></span>  
  
 <span data-ttu-id="70f7d-109">`ICorDebugValue::GetSize` `COR_E_OVERFLOW` 64 ビットプラットフォームで 4 GB を超えるオブジェクトの場合、メソッドはを返します。</span><span class="sxs-lookup"><span data-stu-id="70f7d-109">The `ICorDebugValue::GetSize` method returns `COR_E_OVERFLOW` for objects that are larger than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="70f7d-110">4 GB を超えるオブジェクトには、代わりに [ICorDebugValue3:: GetSize64](icordebugvalue3-getsize64-method.md) メソッドを使用してください。</span><span class="sxs-lookup"><span data-stu-id="70f7d-110">Use the [ICorDebugValue3::GetSize64](icordebugvalue3-getsize64-method.md) method instead for objects that are larger than 4 GB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70f7d-111">要件</span><span class="sxs-lookup"><span data-stu-id="70f7d-111">Requirements</span></span>  

 <span data-ttu-id="70f7d-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70f7d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70f7d-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70f7d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70f7d-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70f7d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70f7d-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70f7d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70f7d-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="70f7d-116">See also</span></span>

- [<span data-ttu-id="70f7d-117">GetSize64 メソッド</span><span class="sxs-lookup"><span data-stu-id="70f7d-117">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)
