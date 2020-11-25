---
title: IMetaDataImport::EnumTypeDefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 4545f5f8d78e588c655a72340210a785b0feb619
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720413"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="76115-102">IMetaDataImport::EnumTypeDefs メソッド</span><span class="sxs-lookup"><span data-stu-id="76115-102">IMetaDataImport::EnumTypeDefs Method</span></span>

<span data-ttu-id="76115-103">現在のスコープ内のすべての型を表す TypeDef トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="76115-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76115-104">構文</span><span class="sxs-lookup"><span data-stu-id="76115-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76115-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="76115-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="76115-106">入出力新しい列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="76115-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="76115-107">このメソッドの最初の呼び出しでは、この値は NULL である必要があります。</span><span class="sxs-lookup"><span data-stu-id="76115-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="76115-108">からTypeDef トークンを格納するために使用される配列。</span><span class="sxs-lookup"><span data-stu-id="76115-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="76115-109">[in] `rTypeDefs` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="76115-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="76115-110">入出力で返された TypeDef トークンの数 `rTypeDefs` 。</span><span class="sxs-lookup"><span data-stu-id="76115-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76115-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="76115-111">Return Value</span></span>  
  
|<span data-ttu-id="76115-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="76115-112">HRESULT</span></span>|<span data-ttu-id="76115-113">説明</span><span class="sxs-lookup"><span data-stu-id="76115-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="76115-114">`EnumTypeDefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="76115-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="76115-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="76115-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="76115-116">この場合、 `pcTypeDefs` は0になります。</span><span class="sxs-lookup"><span data-stu-id="76115-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76115-117">注釈</span><span class="sxs-lookup"><span data-stu-id="76115-117">Remarks</span></span>  

 <span data-ttu-id="76115-118">TypeDef トークンは、クラスやインターフェイスなどの型、および拡張メカニズムを使用して追加された型を表します。</span><span class="sxs-lookup"><span data-stu-id="76115-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76115-119">要件</span><span class="sxs-lookup"><span data-stu-id="76115-119">Requirements</span></span>  

 <span data-ttu-id="76115-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="76115-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76115-121">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="76115-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="76115-122">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="76115-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76115-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76115-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76115-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="76115-124">See also</span></span>

- [<span data-ttu-id="76115-125">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="76115-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="76115-126">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="76115-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
