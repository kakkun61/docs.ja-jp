---
title: ICorPublishEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
ms.openlocfilehash: 888cc40c194cb86b0f898f5556ea14b8897e08c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693308"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="ad25a-102">ICorPublishEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="ad25a-102">ICorPublishEnum::Skip Method</span></span>

<span data-ttu-id="ad25a-103">指定した数の項目だけ、列挙内でカーソルを前方に移動します。</span><span class="sxs-lookup"><span data-stu-id="ad25a-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad25a-104">構文</span><span class="sxs-lookup"><span data-stu-id="ad25a-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad25a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ad25a-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ad25a-106">からカーソルを前方に移動する項目の数。</span><span class="sxs-lookup"><span data-stu-id="ad25a-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad25a-107">要件</span><span class="sxs-lookup"><span data-stu-id="ad25a-107">Requirements</span></span>  

 <span data-ttu-id="ad25a-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad25a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad25a-109">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="ad25a-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ad25a-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad25a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad25a-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad25a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad25a-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad25a-112">See also</span></span>

- [<span data-ttu-id="ad25a-113">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ad25a-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
