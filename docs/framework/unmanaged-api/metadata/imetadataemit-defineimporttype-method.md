---
title: IMetaDataEmit::DefineImportType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 94ce4443be210fdfeb1bab197c3e603255e1cc4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723247"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="c5c27-102">IMetaDataEmit::DefineImportType メソッド</span><span class="sxs-lookup"><span data-stu-id="c5c27-102">IMetaDataEmit::DefineImportType Method</span></span>

<span data-ttu-id="c5c27-103">現在のスコープの外部で定義されている指定した型への参照を作成し、その参照のトークンを定義します。</span><span class="sxs-lookup"><span data-stu-id="c5c27-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c27-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5c27-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c27-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5c27-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="c5c27-106">から対象の型のインポート元のアセンブリを表す [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c5c27-106">[in] An [IMetaDataAssemblyImport](imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="c5c27-107">からによって指定されたアセンブリのハッシュを格納している配列 `pAssemImport` 。</span><span class="sxs-lookup"><span data-stu-id="c5c27-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="c5c27-108">[in] `pbHashValue` 配列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="c5c27-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="c5c27-109">から対象の型のインポート元のメタデータスコープを表す [IMetaDataImport](imetadataimport-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c5c27-109">[in] An [IMetaDataImport](imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="c5c27-110">から `mdTypeDef` 対象の型を指定するトークンです。</span><span class="sxs-lookup"><span data-stu-id="c5c27-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="c5c27-111">からターゲット型がインポートされるアセンブリを表す [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="c5c27-111">[in] An [IMetaDataAssemblyEmit](imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="c5c27-112">入出力 `mdTypeRef` 型参照の現在のスコープで定義されているトークン。</span><span class="sxs-lookup"><span data-stu-id="c5c27-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c27-113">注釈</span><span class="sxs-lookup"><span data-stu-id="c5c27-113">Remarks</span></span>  

 <span data-ttu-id="c5c27-114">[IMetaDataEmit::D efineImportMember](imetadataemit-defineimportmember-method.md)メソッドを呼び出す前に、メソッドを使用して、 `DefineImportType` メンバーの親クラスまたは親インターフェイスの型参照を現在のスコープ内に作成できます。</span><span class="sxs-lookup"><span data-stu-id="c5c27-114">Prior to calling the [IMetaDataEmit::DefineImportMember](imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c27-115">要件</span><span class="sxs-lookup"><span data-stu-id="c5c27-115">Requirements</span></span>  

 <span data-ttu-id="c5c27-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5c27-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c27-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c5c27-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5c27-118">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5c27-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5c27-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c27-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c27-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5c27-120">See also</span></span>

- [<span data-ttu-id="c5c27-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5c27-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c5c27-122">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5c27-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
