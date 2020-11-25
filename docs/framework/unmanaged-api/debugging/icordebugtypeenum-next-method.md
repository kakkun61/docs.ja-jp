---
title: ICorDebugTypeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: 78ea76033b0b83c84446e16fb330bd3ba34c6e21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725704"
---
# <a name="icordebugtypeenumnext-method"></a><span data-ttu-id="d5768-102">ICorDebugTypeEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="d5768-102">ICorDebugTypeEnum::Next Method</span></span>

<span data-ttu-id="d5768-103">によって指定された "の型" インスタンスの数を列挙から取得します。この数は `celt` 、現在の位置から開始します。</span><span class="sxs-lookup"><span data-stu-id="d5768-103">Gets the number of "ICorDebugType" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5768-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5768-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5768-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d5768-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d5768-106">から `ICorDebugType` 取得するインスタンスの数。</span><span class="sxs-lookup"><span data-stu-id="d5768-106">[in] The number of `ICorDebugType` instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="d5768-107">入出力ポインターの配列。それぞれがオブジェクトを指し `ICorDebugType` ます。</span><span class="sxs-lookup"><span data-stu-id="d5768-107">[out] An array of pointers, each of which points to an `ICorDebugType` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d5768-108">入出力実際に返されたインスタンスの数へのポインター `ICorDebugType` 。</span><span class="sxs-lookup"><span data-stu-id="d5768-108">[out] Pointer to the number of `ICorDebugType` instances actually returned.</span></span> <span data-ttu-id="d5768-109">が1の場合、この値は null `celt` になります。</span><span class="sxs-lookup"><span data-stu-id="d5768-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5768-110">要件</span><span class="sxs-lookup"><span data-stu-id="d5768-110">Requirements</span></span>  

 <span data-ttu-id="d5768-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5768-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5768-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5768-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5768-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5768-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5768-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5768-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5768-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5768-115">See also</span></span>
