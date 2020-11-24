---
title: IMetaDataAssemblyEmit::DefineExportedType メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
ms.openlocfilehash: 6b30218cc7373494870ec54a3196857fcc5c08a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689421"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a><span data-ttu-id="fd6bd-102">IMetaDataAssemblyEmit::DefineExportedType メソッド</span><span class="sxs-lookup"><span data-stu-id="fd6bd-102">IMetaDataAssemblyEmit::DefineExportedType Method</span></span>

<span data-ttu-id="fd6bd-103">指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-103">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd6bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="fd6bd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd6bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fd6bd-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="fd6bd-106">からエクスポートする型の名前。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-106">[in] The name of type to be exported.</span></span> <span data-ttu-id="fd6bd-107">共通言語ランタイムのバージョン1.1 では、エクスポートされた型の名前が、型ので指定された名前と完全に一致している必要があり `TypeDef` ます。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-107">For version 1.1 of the common language runtime, the name of the exported type must exactly match the name given in the `TypeDef` for the type.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="fd6bd-108">からエクスポートされた型を実装する場所を指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-108">[in] A token specifying where the exported type is implemented.</span></span> <span data-ttu-id="fd6bd-109">有効な値とそれに関連付けられている意味は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-109">The valid values and their associated meanings are:</span></span>  
  
- <span data-ttu-id="fd6bd-110">`mdFile` この型は、このアセンブリ内の別のファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-110">`mdFile` The type is implemented in a different file within this assembly.</span></span>  
  
- <span data-ttu-id="fd6bd-111">`mdAssemblyRef` 型が別のアセンブリに実装されています。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-111">`mdAssemblyRef` The type is implemented in a different assembly.</span></span>  
  
- <span data-ttu-id="fd6bd-112">`mdExportedTYpe` 型が他の型の中で入れ子になっています。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-112">`mdExportedTYpe` The type is nested within some other type.</span></span>  
  
- <span data-ttu-id="fd6bd-113">`mdFileNil` この型はマニフェストと同じファイル内にあり、入れ子にされた型ではありません。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-113">`mdFileNil` The type is in the same file as the manifest and is not a nested type.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="fd6bd-114">からエクスポートする型を指定するメタデータのトークン。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-114">[in] A token to the metadata that specifies the type to be exported.</span></span> <span data-ttu-id="fd6bd-115">この値は、型を実装するファイルのテーブルに入力され、 `TypeDef` そのファイルがこのアセンブリ内にある場合にのみ関連します。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-115">This value is entered in the `TypeDef` table in the file that implements the type and is relevant only if that file is in this assembly.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="fd6bd-116">からエクスポートされた型のプロパティ設定を定義する [Cortypeattr](cortypeattr-enumeration.md) 列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-116">[in] A bitwise combination of [CorTypeAttr](cortypeattr-enumeration.md) enumeration values that define the property settings for the exported type.</span></span>  
  
 `pmdct`  
 <span data-ttu-id="fd6bd-117">入出力エクスポートされた型を示す、返されたメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-117">[out] A pointer to the returned metadata token that indicates the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd6bd-118">注釈</span><span class="sxs-lookup"><span data-stu-id="fd6bd-118">Remarks</span></span>  

 <span data-ttu-id="fd6bd-119">`ExportedType`このアセンブリによって公開され、マニフェストを含むモジュール以外のモジュールで実装される型ごとに、メタデータ構造を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-119">An `ExportedType` metadata structure must be defined for each type that is exposed by this assembly and that is implemented in a module other than the one containing the manifest.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd6bd-120">要件</span><span class="sxs-lookup"><span data-stu-id="fd6bd-120">Requirements</span></span>  

 <span data-ttu-id="fd6bd-121">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-121">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd6bd-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="fd6bd-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fd6bd-123">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="fd6bd-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fd6bd-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd6bd-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd6bd-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd6bd-125">See also</span></span>

- [<span data-ttu-id="fd6bd-126">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fd6bd-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
