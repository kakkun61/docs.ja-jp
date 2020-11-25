---
title: IMetaDataImport::EnumModuleRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumModuleRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumModuleRefs
helpviewer_keywords:
- EnumModuleRefs method [.NET Framework metadata]
- IMetaDataImport::EnumModuleRefs method [.NET Framework metadata]
ms.assetid: 53441f3a-68d2-477c-906e-37c55dfcfb4d
topic_type:
- apiref
ms.openlocfilehash: 788fd1815415bf8bcfa20d431a5451679d2025bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728278"
---
# <a name="imetadataimportenummodulerefs-method"></a><span data-ttu-id="b67ed-102">IMetaDataImport::EnumModuleRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="b67ed-102">IMetaDataImport::EnumModuleRefs Method</span></span>

<span data-ttu-id="b67ed-103">インポートされたモジュールを表す ModuleRef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="b67ed-103">Enumerates ModuleRef tokens that represent imported modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b67ed-104">構文</span><span class="sxs-lookup"><span data-stu-id="b67ed-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModuleRefs (  
   [in, out] HCORENUM     *phEnum,  
   [out]     mdModuleRef  rModuleRefs[],  
   [in]      ULONG        cMax,  
   [out]     ULONG        *pcModuleRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b67ed-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b67ed-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="b67ed-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b67ed-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="b67ed-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b67ed-107">This must be NULL for the first call of this method.</span></span>  
  
 `rModuleRefs`  
 <span data-ttu-id="b67ed-108">入出力ModuleRef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="b67ed-108">[out] The array used to store the ModuleRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b67ed-109">[in] `rModuleRefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="b67ed-109">[in] The maximum size of the `rModuleRefs` array.</span></span>  
  
 `pcModuleRefs`  
 <span data-ttu-id="b67ed-110">入出力で返された ModuleRef トークンの数 `rModuleRefs` 。</span><span class="sxs-lookup"><span data-stu-id="b67ed-110">[out] The number of ModuleRef tokens returned in `rModuleRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b67ed-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="b67ed-111">Return Value</span></span>  
  
|<span data-ttu-id="b67ed-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b67ed-112">HRESULT</span></span>|<span data-ttu-id="b67ed-113">説明</span><span class="sxs-lookup"><span data-stu-id="b67ed-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b67ed-114">`EnumModuleRefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b67ed-114">`EnumModuleRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b67ed-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="b67ed-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b67ed-116">この場合、 `pcModuleRefs` は0になります。</span><span class="sxs-lookup"><span data-stu-id="b67ed-116">In that case, `pcModuleRefs` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b67ed-117">要件</span><span class="sxs-lookup"><span data-stu-id="b67ed-117">Requirements</span></span>  

 <span data-ttu-id="b67ed-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b67ed-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b67ed-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b67ed-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b67ed-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b67ed-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b67ed-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b67ed-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b67ed-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b67ed-122">See also</span></span>

- [<span data-ttu-id="b67ed-123">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b67ed-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b67ed-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b67ed-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
