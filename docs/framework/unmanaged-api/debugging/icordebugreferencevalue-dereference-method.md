---
title: ICorDebugReferenceValue::Dereference メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: cbcee923ecbb1106bb129f05d2e602a0fd17258d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732488"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="82f7f-102">ICorDebugReferenceValue::Dereference メソッド</span><span class="sxs-lookup"><span data-stu-id="82f7f-102">ICorDebugReferenceValue::Dereference Method</span></span>

<span data-ttu-id="82f7f-103">参照されているオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="82f7f-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f7f-104">構文</span><span class="sxs-lookup"><span data-stu-id="82f7f-104">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82f7f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82f7f-105">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="82f7f-106">入出力この値のオブジェクトが指すオブジェクトを表す ICorDebugValue のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="82f7f-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82f7f-107">注釈</span><span class="sxs-lookup"><span data-stu-id="82f7f-107">Remarks</span></span>  

 <span data-ttu-id="82f7f-108">`ICorDebugValue`オブジェクトは、その参照がまだ無効になっていない場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="82f7f-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f7f-109">要件</span><span class="sxs-lookup"><span data-stu-id="82f7f-109">Requirements</span></span>  

 <span data-ttu-id="82f7f-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82f7f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f7f-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82f7f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82f7f-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82f7f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82f7f-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f7f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
