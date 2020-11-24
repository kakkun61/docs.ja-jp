---
title: ICorPublishEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
ms.openlocfilehash: 44ecba99999d04603477f411e68834548f6a7cda
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693555"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="c8b79-102">ICorPublishEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="c8b79-102">ICorPublishEnum::Clone Method</span></span>

<span data-ttu-id="c8b79-103">この [ICorPublishEnum](icorpublishenum-interface.md) オブジェクトのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8b79-103">Creates a copy of this [ICorPublishEnum](icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b79-104">構文</span><span class="sxs-lookup"><span data-stu-id="c8b79-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8b79-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c8b79-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="c8b79-106">入出力 `ICorPublishEnum` このオブジェクトのコピーであるオブジェクトのアドレスへのポインター `ICorPublishEnum` 。</span><span class="sxs-lookup"><span data-stu-id="c8b79-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8b79-107">要件</span><span class="sxs-lookup"><span data-stu-id="c8b79-107">Requirements</span></span>  

 <span data-ttu-id="c8b79-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8b79-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8b79-109">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="c8b79-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c8b79-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8b79-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8b79-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8b79-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8b79-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8b79-112">See also</span></span>

- [<span data-ttu-id="c8b79-113">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c8b79-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)
