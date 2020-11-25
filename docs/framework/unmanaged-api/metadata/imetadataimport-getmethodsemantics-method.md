---
title: IMetaDataImport::GetMethodSemantics メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: cc01a417c3246ad2554c506f21e37a3cbbdeb991
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733188"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="941cd-102">IMetaDataImport::GetMethodSemantics メソッド</span><span class="sxs-lookup"><span data-stu-id="941cd-102">IMetaDataImport::GetMethodSemantics Method</span></span>

<span data-ttu-id="941cd-103">指定した MethodDef トークンによって参照されるメソッドと、指定した EventProp トークンによって参照されるペアのプロパティおよびイベントの間のリレーションシップを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="941cd-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="941cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="941cd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="941cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="941cd-105">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="941cd-106">からセマンティックロール情報を取得するメソッドを表す MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="941cd-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="941cd-107">からメソッドのロールを取得するための、ペアのプロパティとイベントを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="941cd-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="941cd-108">入出力関連付けられているセマンティクスフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="941cd-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="941cd-109">この値は、 [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) 列挙体のビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="941cd-109">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="941cd-110">注釈</span><span class="sxs-lookup"><span data-stu-id="941cd-110">Remarks</span></span>  

 <span data-ttu-id="941cd-111">[IMetaDataEmit::D efineProperty](imetadataemit-defineproperty-method.md)メソッドは、メソッドのセマンティクスフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="941cd-111">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="941cd-112">要件</span><span class="sxs-lookup"><span data-stu-id="941cd-112">Requirements</span></span>  

 <span data-ttu-id="941cd-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="941cd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="941cd-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="941cd-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="941cd-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="941cd-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="941cd-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="941cd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="941cd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="941cd-117">See also</span></span>

- [<span data-ttu-id="941cd-118">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="941cd-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="941cd-119">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="941cd-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
