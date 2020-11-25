---
title: IMetaDataImport::EnumMethods メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 00726b7e74bdedc658886cccbc4329eaf3ae76d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696805"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="c2481-102">IMetaDataImport::EnumMethods メソッド</span><span class="sxs-lookup"><span data-stu-id="c2481-102">IMetaDataImport::EnumMethods Method</span></span>

<span data-ttu-id="c2481-103">指定した型のメソッドを表す MethodDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="c2481-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2481-104">構文</span><span class="sxs-lookup"><span data-stu-id="c2481-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2481-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c2481-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="c2481-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="c2481-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c2481-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2481-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="c2481-108">から列挙するメソッドを持つ型を表す TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="c2481-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="c2481-109">入出力MethodDef トークンを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="c2481-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c2481-110">からMethodDef 配列の最大サイズ `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="c2481-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="c2481-111">入出力で返される MethodDef トークンの数 `rMethods` 。</span><span class="sxs-lookup"><span data-stu-id="c2481-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2481-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="c2481-112">Return Value</span></span>  
  
|<span data-ttu-id="c2481-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2481-113">HRESULT</span></span>|<span data-ttu-id="c2481-114">説明</span><span class="sxs-lookup"><span data-stu-id="c2481-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c2481-115">`EnumMethods` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="c2481-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c2481-116">列挙する MethodDef トークンがありません。</span><span class="sxs-lookup"><span data-stu-id="c2481-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="c2481-117">この場合、 `pcTokens` は0になります。</span><span class="sxs-lookup"><span data-stu-id="c2481-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c2481-118">要件</span><span class="sxs-lookup"><span data-stu-id="c2481-118">Requirements</span></span>  

 <span data-ttu-id="c2481-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2481-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2481-120">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c2481-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2481-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c2481-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c2481-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2481-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2481-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2481-123">See also</span></span>

- [<span data-ttu-id="c2481-124">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2481-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c2481-125">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c2481-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
