---
title: ICorDebugGCReferenceEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
ms.openlocfilehash: e55c53b9610dcadee92ba9871bf52e3dacb5796b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726237"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="2d9ba-102">ICorDebugGCReferenceEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="2d9ba-102">ICorDebugGCReferenceEnum::Next Method</span></span>

<span data-ttu-id="2d9ba-103">ガベージコレクトされるオブジェクトに関する情報を格納している、指定した数の [COR_GC_REFERENCE](cor-gc-reference-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2d9ba-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d9ba-104">構文</span><span class="sxs-lookup"><span data-stu-id="2d9ba-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d9ba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2d9ba-105">Parameters</span></span>  

 <span data-ttu-id="2d9ba-106">celt</span><span class="sxs-lookup"><span data-stu-id="2d9ba-106">celt</span></span>  
 <span data-ttu-id="2d9ba-107">から取得するルートの数。</span><span class="sxs-lookup"><span data-stu-id="2d9ba-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="2d9ba-108">ca</span><span class="sxs-lookup"><span data-stu-id="2d9ba-108">roots</span></span>  
 <span data-ttu-id="2d9ba-109">入出力ポインターの配列。各ポインターは、ガベージコレクトされるオブジェクトのルートを表す [COR_GC_REFERENCE](cor-gc-reference-structure.md) オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="2d9ba-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="2d9ba-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="2d9ba-110">pceltFetched</span></span>  
 <span data-ttu-id="2d9ba-111">入出力実際にで返される [COR_GC_REFERENCE](cor-gc-reference-structure.md) オブジェクトの数へのポインター `roots` 。</span><span class="sxs-lookup"><span data-stu-id="2d9ba-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="2d9ba-112">`celt` が 1 の場合、この値は`null` になることがあります。</span><span class="sxs-lookup"><span data-stu-id="2d9ba-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d9ba-113">解説</span><span class="sxs-lookup"><span data-stu-id="2d9ba-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d9ba-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="2d9ba-114">Requirements</span></span>  

 <span data-ttu-id="2d9ba-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d9ba-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d9ba-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d9ba-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d9ba-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d9ba-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d9ba-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d9ba-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d9ba-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d9ba-119">See also</span></span>

- [<span data-ttu-id="2d9ba-120">ICorDebugGCReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d9ba-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="2d9ba-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2d9ba-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
