---
title: ICorDebugReferenceValue::GetValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::GetValue
helpviewer_keywords:
- GetValue method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::GetValue method [.NET Framework debugging]
ms.assetid: 5da07f99-6c70-46ec-b997-5ab6fb7106cd
topic_type:
- apiref
ms.openlocfilehash: cbdba623b02ccc85c6d4784a9539adf14fd256e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691202"
---
# <a name="icordebugreferencevaluegetvalue-method"></a><span data-ttu-id="04289-102">ICorDebugReferenceValue::GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="04289-102">ICorDebugReferenceValue::GetValue Method</span></span>

<span data-ttu-id="04289-103">参照先のオブジェクトの現在のメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="04289-103">Gets the current memory address of the referenced object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04289-104">構文</span><span class="sxs-lookup"><span data-stu-id="04289-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] CORDB_ADDRESS   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04289-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="04289-105">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="04289-106">入出力このは、 `CORDB_ADDRESS` この参照値オブジェクトが指すオブジェクトのアドレスを指定する値へのポインターです。</span><span class="sxs-lookup"><span data-stu-id="04289-106">[out] A pointer to a `CORDB_ADDRESS` value that specifies the address of the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04289-107">要件</span><span class="sxs-lookup"><span data-stu-id="04289-107">Requirements</span></span>  

 <span data-ttu-id="04289-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04289-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04289-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04289-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04289-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04289-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04289-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04289-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
