---
title: IMetaDataEmit::DeleteFieldMarshal メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
ms.openlocfilehash: 5989c45782b4f83ecfa285cb305080320abf6a3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700549"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="07e91-102">IMetaDataEmit::DeleteFieldMarshal メソッド</span><span class="sxs-lookup"><span data-stu-id="07e91-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>

<span data-ttu-id="07e91-103">指定したトークンによって参照されるオブジェクトの PInvoke マーシャリングメタデータ署名を破棄します。</span><span class="sxs-lookup"><span data-stu-id="07e91-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e91-104">構文</span><span class="sxs-lookup"><span data-stu-id="07e91-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e91-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07e91-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="07e91-106">から `mdFieldDef` `mdParamDef` マーシャリングメタデータ署名を削除する対象のフィールドまたはパラメーターを表すまたはトークン。</span><span class="sxs-lookup"><span data-stu-id="07e91-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e91-107">要件</span><span class="sxs-lookup"><span data-stu-id="07e91-107">Requirements</span></span>  

 <span data-ttu-id="07e91-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07e91-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e91-109">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="07e91-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="07e91-110">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="07e91-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07e91-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e91-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e91-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="07e91-112">See also</span></span>

- [<span data-ttu-id="07e91-113">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07e91-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="07e91-114">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07e91-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
