---
title: IMetaDataEmit::DefineNestedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
ms.openlocfilehash: 99dc141cca0f911c8dd65645f6c22d950cc678d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719542"
---
# <a name="imetadataemitdefinenestedtype-method"></a><span data-ttu-id="44d9b-102">IMetaDataEmit::DefineNestedType メソッド</span><span class="sxs-lookup"><span data-stu-id="44d9b-102">IMetaDataEmit::DefineNestedType Method</span></span>

<span data-ttu-id="44d9b-103">型定義のメタデータシグネチャを作成し、 `mdTypeDef` その型のトークンを返します。また、定義された型がパラメーターによって参照される型のメンバーであることを指定し `tdEncloser` ます。</span><span class="sxs-lookup"><span data-stu-id="44d9b-103">Creates the metadata signature of a type definition, returns an `mdTypeDef` token for that type, and specifies that the defined type is a member of the type referenced by the `tdEncloser` parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44d9b-104">構文</span><span class="sxs-lookup"><span data-stu-id="44d9b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44d9b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="44d9b-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="44d9b-106">からUnicode での型の名前。</span><span class="sxs-lookup"><span data-stu-id="44d9b-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="44d9b-107">[入力] `TypeDef` アトリビュート.</span><span class="sxs-lookup"><span data-stu-id="44d9b-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="44d9b-108">これは、値のビットマスクです `CorTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="44d9b-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="44d9b-109">から基本クラスのトークン。</span><span class="sxs-lookup"><span data-stu-id="44d9b-109">[in] The token of the base class.</span></span> <span data-ttu-id="44d9b-110">これは、 `mdTypeDef` またはトークンのいずれか `mdTypeRef` です。</span><span class="sxs-lookup"><span data-stu-id="44d9b-110">This is either a `mdTypeDef` or a `mdTypeRef` token.</span></span>  
  
 <span data-ttu-id="44d9b-111">`rtkImplements`[]</span><span class="sxs-lookup"><span data-stu-id="44d9b-111">`rtkImplements`[]</span></span>  
 <span data-ttu-id="44d9b-112">からこのクラスまたはインターフェイスが実装するインターフェイスを指定するトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="44d9b-112">[in] An array of tokens that specify the interfaces that this class or interface implements.</span></span>  
  
 `tdEncloser`  
 <span data-ttu-id="44d9b-113">から外側の型のトークン。</span><span class="sxs-lookup"><span data-stu-id="44d9b-113">[in] The token of the enclosing type.</span></span> <span data-ttu-id="44d9b-114">配列の最後の要素は、である必要があり `mdTokenNil` ます。</span><span class="sxs-lookup"><span data-stu-id="44d9b-114">The last element of the array must be `mdTokenNil`.</span></span>  
  
 `ptd`  
 <span data-ttu-id="44d9b-115">入出力 `mdTypeDef` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="44d9b-115">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44d9b-116">要件</span><span class="sxs-lookup"><span data-stu-id="44d9b-116">Requirements</span></span>  

 <span data-ttu-id="44d9b-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="44d9b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44d9b-118">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="44d9b-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44d9b-119">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="44d9b-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44d9b-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44d9b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d9b-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="44d9b-121">See also</span></span>

- [<span data-ttu-id="44d9b-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44d9b-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="44d9b-123">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="44d9b-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
