---
title: IMetaDataImport::FindField メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 9b42f0f7c8e2878ee3ec140344f51517a24247c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729864"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="e2a22-102">IMetaDataImport::FindField メソッド</span><span class="sxs-lookup"><span data-stu-id="e2a22-102">IMetaDataImport::FindField Method</span></span>

<span data-ttu-id="e2a22-103">指定した <xref:System.Type> と指定した名前とメタデータシグネチャを持つフィールドの FieldDef トークンへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="e2a22-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a22-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2a22-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2a22-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2a22-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="e2a22-106">から検索対象のフィールドを囲むクラスまたはインターフェイスの TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="e2a22-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="e2a22-107">この値がの場合 `mdTokenNil` 、グローバル変数に対して参照が行われます。</span><span class="sxs-lookup"><span data-stu-id="e2a22-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="e2a22-108">から検索するフィールドの名前。</span><span class="sxs-lookup"><span data-stu-id="e2a22-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="e2a22-109">からフィールドのバイナリメタデータシグネチャへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e2a22-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="e2a22-110">からのサイズ (バイト単位) `pvSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="e2a22-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="e2a22-111">入出力一致する FieldDef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e2a22-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2a22-112">注釈</span><span class="sxs-lookup"><span data-stu-id="e2a22-112">Remarks</span></span>  

 <span data-ttu-id="e2a22-113">フィールドは、外側のクラスまたはインターフェイス ( `td` )、その名前 ( `szName` )、および必要に応じてシグネチャ () を使用して指定し `pvSigBlob` ます。</span><span class="sxs-lookup"><span data-stu-id="e2a22-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="e2a22-114">署名は特定のスコープにバインドされるため、に渡されるシグネチャは、 `FindField` 現在のスコープで生成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2a22-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="e2a22-115">署名には、外側のクラスまたは値の型を識別するトークンを埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e2a22-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="e2a22-116">(トークンは、ローカルの TypeDef テーブルのインデックスです)。</span><span class="sxs-lookup"><span data-stu-id="e2a22-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="e2a22-117">現在のスコープのコンテキスト外でランタイムシグネチャを作成し、その署名をへの入力として使用することはできません `FindField` 。</span><span class="sxs-lookup"><span data-stu-id="e2a22-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="e2a22-118">`FindField` クラスまたはインターフェイスで直接定義されたフィールドのみを検索します。継承されたフィールドは見つかりません。</span><span class="sxs-lookup"><span data-stu-id="e2a22-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2a22-119">要件</span><span class="sxs-lookup"><span data-stu-id="e2a22-119">Requirements</span></span>  

 <span data-ttu-id="e2a22-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e2a22-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2a22-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e2a22-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2a22-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e2a22-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e2a22-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2a22-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2a22-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2a22-124">See also</span></span>

- [<span data-ttu-id="e2a22-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e2a22-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="e2a22-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e2a22-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
