---
title: IMetaDataEmit::DeletePinvokeMap メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 6fc6cf9b7333dd4caad3c5a4b081fecb060c8f86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722090"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="047f5-102">IMetaDataEmit::DeletePinvokeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="047f5-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>

<span data-ttu-id="047f5-103">指定したトークンによって参照されるオブジェクトの PInvoke マッピングメタデータを破棄します。</span><span class="sxs-lookup"><span data-stu-id="047f5-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="047f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="047f5-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="047f5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="047f5-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="047f5-106">から `mdFieldDef` `mdMethodDef` PInvoke マッピングメタデータを削除する対象のオブジェクトを表すまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="047f5-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="047f5-107">要件</span><span class="sxs-lookup"><span data-stu-id="047f5-107">Requirements</span></span>  

 <span data-ttu-id="047f5-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="047f5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="047f5-109">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="047f5-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="047f5-110">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="047f5-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="047f5-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="047f5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047f5-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="047f5-112">See also</span></span>

- [<span data-ttu-id="047f5-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="047f5-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="047f5-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="047f5-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
