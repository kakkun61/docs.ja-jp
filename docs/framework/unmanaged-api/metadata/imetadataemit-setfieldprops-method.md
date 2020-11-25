---
title: IMetaDataEmit::SetFieldProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: 0f98fb64b43822c437c39df2f3c51a222ef386b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730397"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="3344a-102">IMetaDataEmit::SetFieldProps メソッド</span><span class="sxs-lookup"><span data-stu-id="3344a-102">IMetaDataEmit::SetFieldProps Method</span></span>

<span data-ttu-id="3344a-103">指定したフィールドトークンによって参照されるフィールドの既定値を設定または更新します。</span><span class="sxs-lookup"><span data-stu-id="3344a-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3344a-104">構文</span><span class="sxs-lookup"><span data-stu-id="3344a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3344a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3344a-105">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="3344a-106">からターゲットフィールドのトークン。</span><span class="sxs-lookup"><span data-stu-id="3344a-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="3344a-107">からフィールド属性。</span><span class="sxs-lookup"><span data-stu-id="3344a-107">[in] Field attributes.</span></span> <span data-ttu-id="3344a-108">これは、値のビットマスクです `CorFieldAttr` 。</span><span class="sxs-lookup"><span data-stu-id="3344a-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="3344a-109">から`ELEMENT_TYPE_` *\** 定数値の。</span><span class="sxs-lookup"><span data-stu-id="3344a-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="3344a-110">これは `CorElementType` 値です。</span><span class="sxs-lookup"><span data-stu-id="3344a-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="3344a-111">定数が定義されていない場合は、この値をに設定 `ELEMENT_TYPE_END` します。</span><span class="sxs-lookup"><span data-stu-id="3344a-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3344a-112">からフィールドの定数値。</span><span class="sxs-lookup"><span data-stu-id="3344a-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="3344a-113">からのサイズ (Unicode 文字) `pValue` 。</span><span class="sxs-lookup"><span data-stu-id="3344a-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3344a-114">要件</span><span class="sxs-lookup"><span data-stu-id="3344a-114">Requirements</span></span>  

 <span data-ttu-id="3344a-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3344a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3344a-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3344a-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3344a-117">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="3344a-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3344a-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3344a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3344a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3344a-119">See also</span></span>

- [<span data-ttu-id="3344a-120">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3344a-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3344a-121">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3344a-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
