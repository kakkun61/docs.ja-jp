---
title: IMetaDataImport::FindMethod メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindMethod
helpviewer_keywords:
- FindMethod method [.NET Framework metadata]
- IMetaDataImport::FindMethod method [.NET Framework metadata]
ms.assetid: 0f9bde1d-e306-438d-941b-d0925b322304
topic_type:
- apiref
ms.openlocfilehash: 111e42a6d8f413c616779bc44e0722ab38781588
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711339"
---
# <a name="imetadataimportfindmethod-method"></a><span data-ttu-id="4f136-102">IMetaDataImport::FindMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="4f136-102">IMetaDataImport::FindMethod Method</span></span>

<span data-ttu-id="4f136-103">指定した <xref:System.Type> と指定した名前とメタデータシグネチャを持つメソッドの MethodDef トークンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4f136-103">Gets a pointer to the MethodDef token for the method that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f136-104">構文</span><span class="sxs-lookup"><span data-stu-id="4f136-104">Syntax</span></span>  
  
```cpp  
HRESULT FindMethod (  
   [in]  mdTypeDef          td,  
   [in]  LPCWSTR            szName,
   [in]  PCCOR_SIGNATURE    pvSigBlob,
   [in]  ULONG              cbSigBlob,
   [out] mdMethodDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f136-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4f136-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="4f136-106">から検索対象の `mdTypeDef` メンバーを囲む型 (クラスまたはインターフェイス) のトークン。</span><span class="sxs-lookup"><span data-stu-id="4f136-106">[in] The `mdTypeDef` token for the type (a class or interface) that encloses the member to search for.</span></span> <span data-ttu-id="4f136-107">この値がの場合は `mdTokenNil` 、グローバル関数の参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="4f136-107">If this value is `mdTokenNil`, then the lookup is done for a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="4f136-108">から検索するメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="4f136-108">[in] The name of the method to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4f136-109">からメソッドのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4f136-109">[in] A pointer to the binary metadata signature of the method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="4f136-110">からのサイズ (バイト単位) `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="4f136-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="4f136-111">入出力一致する MethodDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4f136-111">[out] A pointer to the matching MethodDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f136-112">注釈</span><span class="sxs-lookup"><span data-stu-id="4f136-112">Remarks</span></span>  

 <span data-ttu-id="4f136-113">メソッドは、外側のクラスまたはインターフェイス ( `td` )、その名前 ( `szName` )、および必要に応じてシグネチャ () を使用して指定し `pvSigBlob` ます。</span><span class="sxs-lookup"><span data-stu-id="4f136-113">You specify the method using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span> <span data-ttu-id="4f136-114">クラスまたはインターフェイスに同じ名前のメソッドが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f136-114">There might be multiple methods with the same name in a class or interface.</span></span> <span data-ttu-id="4f136-115">その場合は、メソッドのシグネチャを渡して、一意の一致を検索します。</span><span class="sxs-lookup"><span data-stu-id="4f136-115">In that case, pass the method's signature to find the unique match.</span></span>  
  
 <span data-ttu-id="4f136-116">署名は特定のスコープにバインドされるため、に渡されるシグネチャは、 `FindMethod` 現在のスコープで生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f136-116">The signature passed to `FindMethod` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="4f136-117">署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="4f136-117">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="4f136-118">トークンは、ローカルの TypeDef テーブルのインデックスです。</span><span class="sxs-lookup"><span data-stu-id="4f136-118">The token is an index into the local TypeDef table.</span></span> <span data-ttu-id="4f136-119">現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名を入力として使用してへの入力として使用することはできません `FindMethod` 。</span><span class="sxs-lookup"><span data-stu-id="4f136-119">You cannot build a run-time signature outside the context of the current scope and use that signature as input to input to `FindMethod`.</span></span>  
  
 <span data-ttu-id="4f136-120">`FindMethod` クラスまたはインターフェイスで直接定義されたメソッドのみを検索します。継承されたメソッドは見つかりません。</span><span class="sxs-lookup"><span data-stu-id="4f136-120">`FindMethod` finds only methods that were defined directly in the class or interface; it does not find inherited methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f136-121">要件</span><span class="sxs-lookup"><span data-stu-id="4f136-121">Requirements</span></span>  

 <span data-ttu-id="4f136-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f136-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f136-123">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4f136-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4f136-124">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4f136-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4f136-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f136-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f136-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f136-126">See also</span></span>

- <xref:System.Reflection.MethodInfo>
- [<span data-ttu-id="4f136-127">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f136-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4f136-128">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4f136-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
