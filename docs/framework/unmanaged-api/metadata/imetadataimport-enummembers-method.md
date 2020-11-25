---
title: IMetaDataImport::EnumMembers メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: 92503df60ae44dfd44819fe3eda8e6a0549b2b66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720992"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="a4712-102">IMetaDataImport::EnumMembers メソッド</span><span class="sxs-lookup"><span data-stu-id="a4712-102">IMetaDataImport::EnumMembers Method</span></span>

<span data-ttu-id="a4712-103">指定した型のメンバーを表す MemberDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a4712-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4712-104">構文</span><span class="sxs-lookup"><span data-stu-id="a4712-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4712-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4712-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="a4712-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a4712-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="a4712-107">からメンバーを列挙する型を表す TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="a4712-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="a4712-108">入出力MemberDef トークンを保持するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="a4712-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a4712-109">[in] `rMembers` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="a4712-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="a4712-110">入出力で返された MemberDef トークンの実際の数 `rMembers` 。</span><span class="sxs-lookup"><span data-stu-id="a4712-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4712-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="a4712-111">Return Value</span></span>  
  
|<span data-ttu-id="a4712-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4712-112">HRESULT</span></span>|<span data-ttu-id="a4712-113">説明</span><span class="sxs-lookup"><span data-stu-id="a4712-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a4712-114">`EnumMembers` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a4712-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a4712-115">列挙する MemberDef トークンがありません。</span><span class="sxs-lookup"><span data-stu-id="a4712-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="a4712-116">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="a4712-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4712-117">注釈</span><span class="sxs-lookup"><span data-stu-id="a4712-117">Remarks</span></span>  

 <span data-ttu-id="a4712-118">クラスのメンバーのコレクションを列挙するときに、 `EnumMembers` クラスで直接定義されたメンバー (プロパティまたはイベントでは **ない** ) のみを返します。</span><span class="sxs-lookup"><span data-stu-id="a4712-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="a4712-119">クラスが継承されたメンバーの実装を提供している場合でも、クラスが継承するメンバーは返しません。</span><span class="sxs-lookup"><span data-stu-id="a4712-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="a4712-120">継承されたメンバーを列挙するには、呼び出し元が継承チェーンを明示的にウォークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4712-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="a4712-121">継承チェーンの規則は、元のメタデータを出力した言語またはコンパイラによって異なる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a4712-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="a4712-122">プロパティとイベントは、によって列挙されません `EnumMembers` 。</span><span class="sxs-lookup"><span data-stu-id="a4712-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="a4712-123">これらを列挙するには、 [Enumproperties](imetadataimport-enumproperties-method.md) または [enumproperties](imetadataimport-enumevents-method.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="a4712-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="a4712-124">要件</span><span class="sxs-lookup"><span data-stu-id="a4712-124">Requirements</span></span>  

 <span data-ttu-id="a4712-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4712-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4712-126">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a4712-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a4712-127">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a4712-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a4712-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4712-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4712-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4712-129">See also</span></span>

- [<span data-ttu-id="a4712-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4712-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="a4712-131">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4712-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
