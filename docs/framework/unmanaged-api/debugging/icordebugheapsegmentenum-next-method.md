---
title: ICorDebugHeapSegmentEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 6398fa2962b347a260e23e4fed8cf272a2916a9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704618"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="4f9de-102">ICorDebugHeapSegmentEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="4f9de-102">ICorDebugHeapSegmentEnum::Next Method</span></span>

<span data-ttu-id="4f9de-103">マネージヒープのメモリ領域に関する情報を格納している、指定した数の [COR_SEGMENT](cor-segment-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f9de-103">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f9de-104">構文</span><span class="sxs-lookup"><span data-stu-id="4f9de-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f9de-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f9de-105">Parameters</span></span>  

 <span data-ttu-id="4f9de-106">celt</span><span class="sxs-lookup"><span data-stu-id="4f9de-106">celt</span></span>  
 <span data-ttu-id="4f9de-107">から取得するセグメントの数。</span><span class="sxs-lookup"><span data-stu-id="4f9de-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="4f9de-108">セグメント</span><span class="sxs-lookup"><span data-stu-id="4f9de-108">segments</span></span>  
 <span data-ttu-id="4f9de-109">入出力ポインターの配列。各ポインターは、マネージヒープ内のメモリ領域に関する情報を提供する [COR_SEGMENT](cor-segment-structure.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="4f9de-109">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="4f9de-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="4f9de-110">pceltFetched</span></span>  
 <span data-ttu-id="4f9de-111">入出力実際にで返される [COR_SEGMENT](cor-segment-structure.md) オブジェクトの数へのポインター `segments` 。</span><span class="sxs-lookup"><span data-stu-id="4f9de-111">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="4f9de-112">`celt` が 1 の場合、この値は`null` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="4f9de-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f9de-113">解説</span><span class="sxs-lookup"><span data-stu-id="4f9de-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f9de-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="4f9de-114">Requirements</span></span>  

 <span data-ttu-id="4f9de-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f9de-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f9de-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f9de-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f9de-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f9de-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f9de-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f9de-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f9de-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f9de-119">See also</span></span>

- [<span data-ttu-id="4f9de-120">ICorDebugHeapSegmentEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f9de-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="4f9de-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f9de-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
