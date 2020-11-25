---
title: ICorDebugEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
ms.openlocfilehash: ae88336b9640b68b97522d252b3e8334c20ed9bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705866"
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="d0930-102">ICorDebugEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="d0930-102">ICorDebugEnum::Skip Method</span></span>

<span data-ttu-id="d0930-103">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="d0930-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0930-104">構文</span><span class="sxs-lookup"><span data-stu-id="d0930-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0930-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0930-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d0930-106">からカーソルを前方に移動する項目の数。</span><span class="sxs-lookup"><span data-stu-id="d0930-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0930-107">要件</span><span class="sxs-lookup"><span data-stu-id="d0930-107">Requirements</span></span>  

 <span data-ttu-id="d0930-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0930-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0930-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0930-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0930-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0930-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0930-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0930-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0930-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0930-112">See also</span></span>

- [<span data-ttu-id="d0930-113">ICorDebugEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0930-113">ICorDebugEnum Interface</span></span>](icordebugenum-interface1.md)
