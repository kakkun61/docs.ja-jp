---
title: IMetaDataImport2::EnumGenericParams メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumGenericParams
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumGenericParams
helpviewer_keywords:
- EnumGenericParams method [.NET Framework metadata]
- IMetaDataImport2::EnumGenericParams method [.NET Framework metadata]
ms.assetid: b50488a5-3cf0-483c-82dc-2892a3ec61ac
topic_type:
- apiref
ms.openlocfilehash: 6b1a8e66eea6caec9dfc8d99e343c987cefa1b0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702759"
---
# <a name="imetadataimport2enumgenericparams-method"></a><span data-ttu-id="0fe74-102">IMetaDataImport2::EnumGenericParams メソッド</span><span class="sxs-lookup"><span data-stu-id="0fe74-102">IMetaDataImport2::EnumGenericParams Method</span></span>

<span data-ttu-id="0fe74-103">指定した TypeDef または MethodDef トークンに関連付けられているジェネリックパラメータートークンの配列の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="0fe74-103">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe74-104">構文</span><span class="sxs-lookup"><span data-stu-id="0fe74-104">Syntax</span></span>  
  
```cpp
HRESULT EnumGenericParams (  
   [in, out] HCORENUM     *phEnum,
   [in]  mdToken          tk,  
   [out] mdGenericParam   rGenericParams[],
   [in]  ULONG            cMax,
   [out] ULONG            *pcGenericParams  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fe74-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0fe74-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="0fe74-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0fe74-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="0fe74-107">からジェネリックパラメーターを列挙する TypeDef または MethodDef トークン。</span><span class="sxs-lookup"><span data-stu-id="0fe74-107">[in] The TypeDef or MethodDef token whose generic parameters are to be enumerated.</span></span>  
  
 `rGenericParams`  
 <span data-ttu-id="0fe74-108">入出力列挙するジェネリックパラメーターの配列。</span><span class="sxs-lookup"><span data-stu-id="0fe74-108">[out] The array of generic parameters to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="0fe74-109">からに格納するトークンの要求された最大数 `rGenericParams` 。</span><span class="sxs-lookup"><span data-stu-id="0fe74-109">[in] The requested maximum number of tokens to place in `rGenericParams`.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="0fe74-110">入出力に格納された、返されたトークンの数 `rGenericParams` 。</span><span class="sxs-lookup"><span data-stu-id="0fe74-110">[out] The returned number of tokens placed in `rGenericParams`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fe74-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="0fe74-111">Return Value</span></span>  
  
|<span data-ttu-id="0fe74-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0fe74-112">HRESULT</span></span>|<span data-ttu-id="0fe74-113">説明</span><span class="sxs-lookup"><span data-stu-id="0fe74-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="0fe74-114">`EnumGenericParams` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="0fe74-114">`EnumGenericParams` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="0fe74-115">`phEnum` にメンバー要素がありません。</span><span class="sxs-lookup"><span data-stu-id="0fe74-115">`phEnum` has no member elements.</span></span> <span data-ttu-id="0fe74-116">この場合、 `pcGenericParams` は 0 (ゼロ) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0fe74-116">In this case, `pcGenericParams` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0fe74-117">要件</span><span class="sxs-lookup"><span data-stu-id="0fe74-117">Requirements</span></span>  

 <span data-ttu-id="0fe74-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe74-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fe74-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0fe74-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0fe74-120">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0fe74-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0fe74-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fe74-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fe74-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fe74-122">See also</span></span>

- [<span data-ttu-id="0fe74-123">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0fe74-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="0fe74-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0fe74-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
