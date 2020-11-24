---
title: ICorDebugValueEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum::Next
helpviewer_keywords:
- ICorDebugValueEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: f5ef94dd-dfee-49d3-a398-b110f8906dd8
topic_type:
- apiref
ms.openlocfilehash: e1c8d94a90092b1497267c78d5fadf5a6e6de707
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684331"
---
# <a name="icordebugvalueenumnext-method"></a><span data-ttu-id="94074-102">ICorDebugValueEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="94074-102">ICorDebugValueEnum::Next Method</span></span>

<span data-ttu-id="94074-103">現在の位置から開始して、指定した数の "ICorDebugValue" インスタンスを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="94074-103">Gets the specified number of "ICorDebugValue" instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94074-104">構文</span><span class="sxs-lookup"><span data-stu-id="94074-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugValue *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94074-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94074-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="94074-106">から `ICorDebugValue` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="94074-106">[in] The number of `ICorDebugValue` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="94074-107">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugValue` ます。</span><span class="sxs-lookup"><span data-stu-id="94074-107">[out] An array of pointers, each of which points to an `ICorDebugValue` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="94074-108">入出力実際に返されたインスタンスの数へのポインター `ICorDebugValue` 。</span><span class="sxs-lookup"><span data-stu-id="94074-108">[out] Pointer to the number of `ICorDebugValue` instances actually returned.</span></span> <span data-ttu-id="94074-109">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="94074-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94074-110">要件</span><span class="sxs-lookup"><span data-stu-id="94074-110">Requirements</span></span>  

 <span data-ttu-id="94074-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94074-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94074-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94074-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94074-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94074-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94074-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94074-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94074-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="94074-115">See also</span></span>
