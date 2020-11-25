---
title: IMetaDataImport::FindMember メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMember
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMember
helpviewer_keywords:
- IMetaDataImport::FindMember method [.NET Framework metadata]
- FindMember method [.NET Framework metadata]
ms.assetid: ad32fb84-c2b6-41cd-888d-787ff3a90449
topic_type:
- apiref
ms.openlocfilehash: bcd9499d0aef34fb34065ed58c0f0d69cc4ecedc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711443"
---
# <a name="imetadataimportfindmember-method"></a><span data-ttu-id="4d5d3-102">IMetaDataImport::FindMember メソッド</span><span class="sxs-lookup"><span data-stu-id="4d5d3-102">IMetaDataImport::FindMember Method</span></span>

<span data-ttu-id="4d5d3-103">指定した <xref:System.Type> と指定した名前とメタデータシグネチャを持つフィールドまたはメソッドの MemberDef トークンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-103">Gets a pointer to the MemberDef token for field or method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d5d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="4d5d3-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMember (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,
   [in]  PCCOR_SIGNATURE   pvSigBlob,
   [in]  ULONG             cbSigBlob,
   [out] mdToken           *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d5d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4d5d3-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="4d5d3-106">から検索対象のメンバーを囲むクラスまたはインターフェイスの TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-106">[in] The TypeDef token for the class or interface that encloses the member to search for.</span></span> <span data-ttu-id="4d5d3-107">この値がの場合 `mdTokenNil` 、グローバル変数またはグローバル関数の参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-107">If this value is `mdTokenNil`, the lookup is done for a global-variable or global-function.</span></span>  
  
 `szName`  
 <span data-ttu-id="4d5d3-108">から検索対象のメンバーの名前。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-108">[in] The name of the member to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4d5d3-109">からメンバーのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-109">[in] A pointer to the binary metadata signature of the member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4d5d3-110">からのサイズ (バイト単位) `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="4d5d3-111">入出力一致する MemberDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-111">[out] A pointer to the matching MemberDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d5d3-112">注釈</span><span class="sxs-lookup"><span data-stu-id="4d5d3-112">Remarks</span></span>  

 <span data-ttu-id="4d5d3-113">メンバーは、外側のクラスまたはインターフェイス ( `td` )、その名前 ( `szName` )、および必要に応じてシグネチャ () を使用して指定し `pvSigBlob` ます。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-113">You specify the member using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="4d5d3-114">クラスまたはインターフェイスに同じ名前のメンバーが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-114">There might be multiple members with the same name in a class or interface.</span></span> <span data-ttu-id="4d5d3-115">その場合は、メンバーのシグネチャを渡して、一意の一致を検索します。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-115">In that case, pass the member's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="4d5d3-116">署名は特定のスコープにバインドされるため、に渡されるシグネチャは、 `FindMember` 現在のスコープで生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-116">The signature passed to `FindMember` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="4d5d3-117">署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="4d5d3-118">トークンは、ローカルの TypeDef テーブルのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="4d5d3-119">現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名を入力として使用してへの入力として使用することはできません `FindMember` 。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMember`.</span></span>  
  
 <span data-ttu-id="4d5d3-120">`FindMember` クラスまたはインターフェイスで直接定義されたメンバーのみを検索します。継承されたメンバーは見つかりません。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-120">`FindMember` finds only members that were defined directly in the class or interface; it does not find inherited members.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d5d3-121">`FindMember` は、ヘルパーメソッドです。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-121">`FindMember` is a helper method.</span></span> <span data-ttu-id="4d5d3-122">[IMetaDataImport:: FindMethod](imetadataimport-findmethod-method.md); を呼び出します。この呼び出しで一致するものが見つからない場合は、 `FindMember` [IMetaDataImport:: findfield](imetadataimport-findfield-method.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-122">It calls [IMetaDataImport::FindMethod](imetadataimport-findmethod-method.md); if that call does not find a match, `FindMember` then calls [IMetaDataImport::FindField](imetadataimport-findfield-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d5d3-123">要件</span><span class="sxs-lookup"><span data-stu-id="4d5d3-123">Requirements</span></span>  

 <span data-ttu-id="4d5d3-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d5d3-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d5d3-125">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4d5d3-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4d5d3-126">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4d5d3-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4d5d3-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d5d3-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d5d3-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d5d3-128">See also</span></span>

- [<span data-ttu-id="4d5d3-129">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d5d3-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4d5d3-130">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4d5d3-130">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
