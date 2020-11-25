---
title: ICorDebugReferenceValue::SetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::SetValue
helpviewer_keywords:
- SetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::SetValue method [.NET Framework debugging]
ms.assetid: 3d3f6eec-d772-401f-a028-1a2ecdc31e95
topic_type:
- apiref
ms.openlocfilehash: 3fdd3180a01e4609ac40fd358879c0d2569234ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728382"
---
# <a name="icordebugreferencevaluesetvalue-method"></a><span data-ttu-id="f5148-102">ICorDebugReferenceValue::SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="f5148-102">ICorDebugReferenceValue::SetValue Method</span></span>

<span data-ttu-id="f5148-103">指定されたメモリアドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="f5148-103">Sets the specified memory address.</span></span> <span data-ttu-id="f5148-104">つまり、このメソッドは、オブジェクトを指すようにこの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f5148-104">That is, this method sets this ICorDebugReferenceValue to point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5148-105">構文</span><span class="sxs-lookup"><span data-stu-id="f5148-105">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] CORDB_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5148-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5148-106">Parameters</span></span>  

 `value`  
 <span data-ttu-id="f5148-107">から `CORDB_ADDRESS` このが指すオブジェクトのアドレスを示す値です `ICorDebugReferenceValue` 。</span><span class="sxs-lookup"><span data-stu-id="f5148-107">[in] A `CORDB_ADDRESS` value that specifies the address of the object to which this `ICorDebugReferenceValue` points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5148-108">要件</span><span class="sxs-lookup"><span data-stu-id="f5148-108">Requirements</span></span>  

 <span data-ttu-id="f5148-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5148-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5148-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f5148-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f5148-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5148-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5148-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5148-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
