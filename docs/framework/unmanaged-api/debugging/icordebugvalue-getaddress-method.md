---
title: ICorDebugValue::GetAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 47c0c4dfa78e85bcc83f0bb2a333955c8e8666fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728369"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="e628e-102">ICorDebugValue::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="e628e-102">ICorDebugValue::GetAddress Method</span></span>

<span data-ttu-id="e628e-103">この "ICorDebugValue" オブジェクトのアドレスを取得します。このオブジェクトはデバッグ中です。</span><span class="sxs-lookup"><span data-stu-id="e628e-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e628e-104">構文</span><span class="sxs-lookup"><span data-stu-id="e628e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e628e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e628e-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="e628e-106">入出力 `CORDB_ADDRESS` この値オブジェクトのアドレスを指定するオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e628e-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e628e-107">注釈</span><span class="sxs-lookup"><span data-stu-id="e628e-107">Remarks</span></span>  

 <span data-ttu-id="e628e-108">値が使用できない場合は、0 (ゼロ) が返されます。</span><span class="sxs-lookup"><span data-stu-id="e628e-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="e628e-109">これは、値がレジスタの少なくとも一部の場合、またはガベージコレクターハンドル () に格納されている場合に発生する可能性が `GCHandle` あります。</span><span class="sxs-lookup"><span data-stu-id="e628e-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e628e-110">要件</span><span class="sxs-lookup"><span data-stu-id="e628e-110">Requirements</span></span>  

 <span data-ttu-id="e628e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e628e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e628e-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e628e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e628e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e628e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e628e-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e628e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e628e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e628e-115">See also</span></span>
