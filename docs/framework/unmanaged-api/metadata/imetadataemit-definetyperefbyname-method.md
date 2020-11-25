---
title: IMetaDataEmit::DefineTypeRefByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: b83c868f1a804d4e6f32adffc190ae086aa5e0a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719334"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="912ce-102">IMetaDataEmit::DefineTypeRefByName メソッド</span><span class="sxs-lookup"><span data-stu-id="912ce-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>

<span data-ttu-id="912ce-103">現在のスコープ外にある、指定されたスコープで定義されている型のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="912ce-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912ce-104">構文</span><span class="sxs-lookup"><span data-stu-id="912ce-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="912ce-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="912ce-105">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="912ce-106">から解決スコープを指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="912ce-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="912ce-107">有効なトークンの種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="912ce-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="912ce-108">`mdModuleRef`型が、呼び出し元が定義されている同じアセンブリ内で定義されている場合は。</span><span class="sxs-lookup"><span data-stu-id="912ce-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="912ce-109">`mdAssemblyRef`型が、呼び出し元が定義されているアセンブリ以外のアセンブリで定義されている場合は。</span><span class="sxs-lookup"><span data-stu-id="912ce-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="912ce-110">`mdTypeRef`型が入れ子にされた型の場合は。</span><span class="sxs-lookup"><span data-stu-id="912ce-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="912ce-111">`mdModule`型が、呼び出し元が定義されている同じモジュールで定義されている場合は。</span><span class="sxs-lookup"><span data-stu-id="912ce-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="912ce-112">型がグローバルに定義されている場合は Null。</span><span class="sxs-lookup"><span data-stu-id="912ce-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="912ce-113">からUnicode での対象の型の名前。</span><span class="sxs-lookup"><span data-stu-id="912ce-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="912ce-114">入出力 `mdTypeRef` 型に割り当てられているトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="912ce-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="912ce-115">要件</span><span class="sxs-lookup"><span data-stu-id="912ce-115">Requirements</span></span>  

 <span data-ttu-id="912ce-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="912ce-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="912ce-117">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="912ce-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="912ce-118">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="912ce-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="912ce-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="912ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912ce-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="912ce-120">See also</span></span>

- [<span data-ttu-id="912ce-121">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="912ce-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="912ce-122">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="912ce-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
