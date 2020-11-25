---
title: IMetaDataEmit::SetTypeDefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type:
- apiref
ms.openlocfilehash: 2f572f66f16ff701350fde3b05be822b9e8c78b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706831"
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="8c9de-102">IMetaDataEmit::SetTypeDefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="8c9de-102">IMetaDataEmit::SetTypeDefProps Method</span></span>

<span data-ttu-id="8c9de-103">[IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md)の前の呼び出しで定義された型の機能を設定します。</span><span class="sxs-lookup"><span data-stu-id="8c9de-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c9de-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c9de-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[]
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c9de-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c9de-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="8c9de-106">から `mdTypeDef` [IMetaDataEmit::D efineTypeDef](imetadataemit-definetypedef-method.md)の元の呼び出しから取得されたトークン。</span><span class="sxs-lookup"><span data-stu-id="8c9de-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="8c9de-107">[入力] `TypeDef` アトリビュート.</span><span class="sxs-lookup"><span data-stu-id="8c9de-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="8c9de-108">これは、値のビットマスクです `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="8c9de-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="8c9de-109">から `mdToken` 基本クラスの。</span><span class="sxs-lookup"><span data-stu-id="8c9de-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="8c9de-110">[IMetaDataEmit::D efineImportType](imetadataemit-defineimporttype-method.md)、またはの以前の呼び出しから取得さ `null` れます。</span><span class="sxs-lookup"><span data-stu-id="8c9de-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="8c9de-111">からこの型が実装するインターフェイスのトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="8c9de-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="8c9de-112">これらの `mdTypeRef` トークンは、 [IMetaDataEmit::D efineImportType](imetadataemit-defineimporttype-method.md)を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="8c9de-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="8c9de-113">配列の最後の要素は、である必要があり `mdTokenNil` ます。</span><span class="sxs-lookup"><span data-stu-id="8c9de-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c9de-114">要件</span><span class="sxs-lookup"><span data-stu-id="8c9de-114">Requirements</span></span>  

 <span data-ttu-id="8c9de-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c9de-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c9de-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8c9de-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c9de-117">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c9de-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c9de-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c9de-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c9de-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c9de-119">See also</span></span>

- [<span data-ttu-id="8c9de-120">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c9de-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8c9de-121">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c9de-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
