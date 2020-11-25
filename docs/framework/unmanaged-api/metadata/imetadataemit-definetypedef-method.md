---
title: IMetaDataEmit::DefineTypeDef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeDef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeDef
helpviewer_keywords:
- IMetaDataEmit::DefineTypeDef method [.NET Framework metadata]
- DefineTypeDef method [.NET Framework metadata]
ms.assetid: dd11c485-be95-4b97-9cd8-68679a4fb432
topic_type:
- apiref
ms.openlocfilehash: 2e75b6322e40fe010e9e0a3412a99c0d3460afae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719360"
---
# <a name="imetadataemitdefinetypedef-method"></a><span data-ttu-id="aecc5-102">IMetaDataEmit::DefineTypeDef メソッド</span><span class="sxs-lookup"><span data-stu-id="aecc5-102">IMetaDataEmit::DefineTypeDef Method</span></span>

<span data-ttu-id="aecc5-103">共通言語ランタイム型の型定義を作成し、その型定義のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="aecc5-103">Creates a type definition for a common language runtime type, and gets a metadata token for that type definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aecc5-104">構文</span><span class="sxs-lookup"><span data-stu-id="aecc5-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeDef (
    [in]  LPCWSTR     szTypeDef,
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aecc5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aecc5-105">Parameters</span></span>  

 `szTypeDef`  
 <span data-ttu-id="aecc5-106">からUnicode での型の名前。</span><span class="sxs-lookup"><span data-stu-id="aecc5-106">[in] The name of the type in Unicode.</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="aecc5-107">[入力] `TypeDef` アトリビュート.</span><span class="sxs-lookup"><span data-stu-id="aecc5-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="aecc5-108">これは、値のビットマスクです `CoreTypeAttr` 。</span><span class="sxs-lookup"><span data-stu-id="aecc5-108">This is a bitmask of `CoreTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="aecc5-109">から基本クラスのトークン。</span><span class="sxs-lookup"><span data-stu-id="aecc5-109">[in] The token of the base class.</span></span> <span data-ttu-id="aecc5-110">またはトークンのいずれかである必要があり `mdTypeDef` `mdTypeRef` ます。</span><span class="sxs-lookup"><span data-stu-id="aecc5-110">It must be either an `mdTypeDef` or an `mdTypeRef` token.</span></span>  
  
 `rtkImplements`  
 <span data-ttu-id="aecc5-111">からこのクラスまたはインターフェイスが実装するインターフェイスを指定するトークンの配列。</span><span class="sxs-lookup"><span data-stu-id="aecc5-111">[in] An array of tokens specifying the interfaces that this class or interface implements.</span></span>  
  
 `ptd`  
 <span data-ttu-id="aecc5-112">入出力 `mdTypeDef` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="aecc5-112">[out] The `mdTypeDef` token assigned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aecc5-113">注釈</span><span class="sxs-lookup"><span data-stu-id="aecc5-113">Remarks</span></span>  

 <span data-ttu-id="aecc5-114">のフラグは、 `dwTypeDefFlags` 作成される型が共通型システム参照型 (クラスまたはインターフェイス) であるか、共通型システム値型であるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="aecc5-114">A flag in `dwTypeDefFlags` specifies whether the type being created is a common type system reference type (class or interface) or a common type system value type.</span></span>  
  
 <span data-ttu-id="aecc5-115">このメソッドは、指定されたパラメーターに応じて、 `mdInterfaceImpl` この型によって継承または実装される各インターフェイスのレコードを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="aecc5-115">Depending on the parameters supplied, this method, as a side effect, may also create an `mdInterfaceImpl` record for each interface that is inherited or implemented by this type.</span></span> <span data-ttu-id="aecc5-116">ただし、このメソッドはこれらのトークンを返しません `mdInterfaceImpl` 。</span><span class="sxs-lookup"><span data-stu-id="aecc5-116">However, this method does not return any of these `mdInterfaceImpl` tokens.</span></span> <span data-ttu-id="aecc5-117">クライアントが後でトークンを追加または変更する場合は、 `mdInterfaceImpl` インターフェイスを使用してトークンを列挙する必要があり `IMetaDataImport` ます。</span><span class="sxs-lookup"><span data-stu-id="aecc5-117">If a client wants to later add or modify an `mdInterfaceImpl` token, it must use the `IMetaDataImport` interface to enumerate them.</span></span> <span data-ttu-id="aecc5-118">インターフェイスの COM セマンティクスを使用する場合は `[default]` 、既定のインターフェイスをの最初の要素として指定する必要があり `rtkImplements` ます。クラスに設定されたカスタム属性は、クラスに既定のインターフェイスがあることを示します (これは常に、クラスに対して宣言されている最初のトークンと見なされ `mdInterfaceImpl` ます)。</span><span class="sxs-lookup"><span data-stu-id="aecc5-118">If you want to use COM semantics of the `[default]` interface, you should supply the default interface as the first element in `rtkImplements`; a custom attribute set on the class will indicate that the class has a default interface (which is always assumed to be the first `mdInterfaceImpl` token declared for the class).</span></span>  
  
 <span data-ttu-id="aecc5-119">配列の各要素 `rtkImplements` `mdTypeDef` は、または `mdTypeRef` トークンを保持します。</span><span class="sxs-lookup"><span data-stu-id="aecc5-119">Each element of the `rtkImplements` array holds an `mdTypeDef` or `mdTypeRef` token.</span></span> <span data-ttu-id="aecc5-120">配列の最後の要素は、である必要があり `mdTokenNil` ます。</span><span class="sxs-lookup"><span data-stu-id="aecc5-120">The last element in the array must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aecc5-121">要件</span><span class="sxs-lookup"><span data-stu-id="aecc5-121">Requirements</span></span>  

 <span data-ttu-id="aecc5-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aecc5-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aecc5-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="aecc5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aecc5-124">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="aecc5-124">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aecc5-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aecc5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecc5-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="aecc5-126">See also</span></span>

- [<span data-ttu-id="aecc5-127">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aecc5-127">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="aecc5-128">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aecc5-128">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
