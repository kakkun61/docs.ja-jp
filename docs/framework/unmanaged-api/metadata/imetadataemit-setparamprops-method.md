---
title: IMetaDataEmit::SetParamProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParamProps
helpviewer_keywords:
- IMetaDataEmit::SetParamProps method [.NET Framework metadata]
- SetParamProps method [.NET Framework metadata]
ms.assetid: a95a3908-9f87-4084-937e-8e01ef03ad63
topic_type:
- apiref
ms.openlocfilehash: b0cc28807938bcfb9b2465093ff4cfb94066ee98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675062"
---
# <a name="imetadataemitsetparamprops-method"></a><span data-ttu-id="bb6ad-102">IMetaDataEmit::SetParamProps メソッド</span><span class="sxs-lookup"><span data-stu-id="bb6ad-102">IMetaDataEmit::SetParamProps Method</span></span>

<span data-ttu-id="bb6ad-103">[IMetaDataEmit::D efineParam](imetadataemit-defineparam-method.md)の前の呼び出しで定義されたメソッドパラメーターの機能を設定または変更します。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-103">Sets or changes features of a method parameter that was defined by a prior call to [IMetaDataEmit::DefineParam](imetadataemit-defineparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb6ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb6ad-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParamProps (
    [in]  mdParamDef  pd,
    [in]  LPCWSTR     szName,
    [in]  DWORD       dwParamFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb6ad-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb6ad-105">Parameters</span></span>  

 `pd`  
 <span data-ttu-id="bb6ad-106">から対象のパラメーターのトークン。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-106">[in] The token for the target parameter.</span></span>  
  
 `szName`  
 <span data-ttu-id="bb6ad-107">からUnicode でのパラメーターの名前。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-107">[in] The name of the parameter in Unicode.</span></span>  
  
 `dwParamFlags`  
 <span data-ttu-id="bb6ad-108">からパラメーターのフラグ。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-108">[in] The flags for the parameter.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="bb6ad-109">から定数値の ELEMENT_TYPE_ \*。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-109">[in] The ELEMENT_TYPE_\* for the constant value.</span></span>  
  
 `pValue`  
 <span data-ttu-id="bb6ad-110">からパラメーターの定数値。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-110">[in] The constant value for the parameter.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="bb6ad-111">からの (Unicode) 文字のサイズ `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-111">[in] The size in (Unicode) characters of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb6ad-112">要件</span><span class="sxs-lookup"><span data-stu-id="bb6ad-112">Requirements</span></span>  

 <span data-ttu-id="bb6ad-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb6ad-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="bb6ad-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb6ad-115">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="bb6ad-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb6ad-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb6ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb6ad-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb6ad-117">See also</span></span>

- [<span data-ttu-id="bb6ad-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6ad-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="bb6ad-119">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb6ad-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
