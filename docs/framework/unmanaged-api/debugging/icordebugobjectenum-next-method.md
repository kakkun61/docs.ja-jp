---
title: ICorDebugObjectEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugObjectEnum interface [.NET Framework debugging]
- ICorDebugObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 10093e3d-26b6-4ad7-8ef3-bbf66243fc02
topic_type:
- apiref
ms.openlocfilehash: 8e188f304908a8029a57bb059046205c35346f3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724690"
---
# <a name="icordebugobjectenumnext-method"></a><span data-ttu-id="45305-102">ICorDebugObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="45305-102">ICorDebugObjectEnum::Next Method</span></span>

<span data-ttu-id="45305-103">列挙から、指定した数のオブジェクトの相対仮想アドレス (RVAs) を取得します。この値は、現在の位置から開始されます。</span><span class="sxs-lookup"><span data-stu-id="45305-103">Gets the relative virtual addresses (RVAs) of the specified number of objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45305-104">構文</span><span class="sxs-lookup"><span data-stu-id="45305-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        CORDB_ADDRESS objects[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45305-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="45305-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="45305-106">[in] 取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="45305-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="45305-107">入出力ポインターの配列。それぞれが CORDB_ADDRESS オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="45305-107">[out] An array of pointers, each of which points to a CORDB_ADDRESS object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="45305-108">入出力実際に返されたオブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="45305-108">[out] Pointer to the number of objects actually returned.</span></span> <span data-ttu-id="45305-109">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="45305-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45305-110">要件</span><span class="sxs-lookup"><span data-stu-id="45305-110">Requirements</span></span>  

 <span data-ttu-id="45305-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45305-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45305-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45305-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45305-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45305-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45305-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45305-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45305-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="45305-115">See also</span></span>
