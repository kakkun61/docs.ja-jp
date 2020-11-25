---
title: IMetaDataImport::EnumFieldsWithName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFieldsWithName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFieldsWithName
helpviewer_keywords:
- IMetaDataImport::EnumFieldsWithName method [.NET Framework metadata]
- EnumFieldsWithName method [.NET Framework metadata]
ms.assetid: 42145e8d-000f-4d0b-ae43-c08201190fa2
topic_type:
- apiref
ms.openlocfilehash: 0a254587282dea43a3507fbbeca35bd7aa9604f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711573"
---
# <a name="imetadataimportenumfieldswithname-method"></a><span data-ttu-id="16416-102">IMetaDataImport::EnumFieldsWithName メソッド</span><span class="sxs-lookup"><span data-stu-id="16416-102">IMetaDataImport::EnumFieldsWithName Method</span></span>

<span data-ttu-id="16416-103">指定した名前を持つ指定した型の FieldDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="16416-103">Enumerates FieldDef tokens of the specified type with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16416-104">構文</span><span class="sxs-lookup"><span data-stu-id="16416-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFieldsWithName (  
   [in, out] HCORENUM    *phEnum,
   [in]  mdTypeDef       cl,
   [in]  LPCWSTR         szName,
   [out] mdFieldDef      rFields[],
   [in]  ULONG           cMax,
   [out] ULONG           *pcTokens
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16416-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16416-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="16416-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="16416-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="16416-107">からフィールドを列挙する型のトークン。</span><span class="sxs-lookup"><span data-stu-id="16416-107">[in] The token of the type whose fields are to be enumerated.</span></span>  
  
 `szName`  
 <span data-ttu-id="16416-108">から列挙型のスコープを制限するフィールド名。</span><span class="sxs-lookup"><span data-stu-id="16416-108">[in] The field name that limits the scope of the enumeration.</span></span>  
  
 `rFields`  
 <span data-ttu-id="16416-109">入出力FieldDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="16416-109">[out] Array used to store the FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="16416-110">[in] `rFields` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="16416-110">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="16416-111">入出力で返された FieldDef トークンの実際の数 `rFields` 。</span><span class="sxs-lookup"><span data-stu-id="16416-111">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16416-112">注釈</span><span class="sxs-lookup"><span data-stu-id="16416-112">Remarks</span></span>  

 <span data-ttu-id="16416-113">[IMetaDataImport:: EnumFields](imetadataimport-enumfields-method.md)とは異なり、は `EnumFieldsWithName` 指定された名前のないすべてのフィールドトークンを破棄します。</span><span class="sxs-lookup"><span data-stu-id="16416-113">Unlike [IMetaDataImport::EnumFields](imetadataimport-enumfields-method.md), `EnumFieldsWithName` discards all field tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16416-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="16416-114">Return Value</span></span>  
  
|<span data-ttu-id="16416-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16416-115">HRESULT</span></span>|<span data-ttu-id="16416-116">説明</span><span class="sxs-lookup"><span data-stu-id="16416-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="16416-117">`EnumFieldsWithName` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="16416-117">`EnumFieldsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="16416-118">列挙するフィールドがありません。</span><span class="sxs-lookup"><span data-stu-id="16416-118">There are no fields to enumerate.</span></span> <span data-ttu-id="16416-119">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="16416-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="16416-120">要件</span><span class="sxs-lookup"><span data-stu-id="16416-120">Requirements</span></span>  

 <span data-ttu-id="16416-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16416-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16416-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="16416-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16416-123">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="16416-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16416-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16416-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16416-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="16416-125">See also</span></span>

- [<span data-ttu-id="16416-126">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16416-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="16416-127">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16416-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
