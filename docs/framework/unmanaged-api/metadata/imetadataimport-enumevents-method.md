---
title: IMetaDataImport::EnumEvents メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 3a181f1ef29810058c57bdb13338a01aa1fe7dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700471"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="6b897-102">IMetaDataImport::EnumEvents メソッド</span><span class="sxs-lookup"><span data-stu-id="6b897-102">IMetaDataImport::EnumEvents Method</span></span>

<span data-ttu-id="6b897-103">指定した TypeDef トークンのイベント定義トークンを列挙します。</span><span class="sxs-lookup"><span data-stu-id="6b897-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b897-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b897-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b897-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6b897-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="6b897-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6b897-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="6b897-107">からイベント定義を列挙する TypeDef トークン。</span><span class="sxs-lookup"><span data-stu-id="6b897-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="6b897-108">入出力返されたイベントの配列。</span><span class="sxs-lookup"><span data-stu-id="6b897-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="6b897-109">[in] `rEvents` 配列の最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="6b897-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="6b897-110">入出力で返されるイベントの実際の数 `rEvents` 。</span><span class="sxs-lookup"><span data-stu-id="6b897-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b897-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="6b897-111">Return Value</span></span>  
  
|<span data-ttu-id="6b897-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b897-112">HRESULT</span></span>|<span data-ttu-id="6b897-113">説明</span><span class="sxs-lookup"><span data-stu-id="6b897-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="6b897-114">`EnumEvents` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6b897-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="6b897-115">列挙するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="6b897-115">There are no events to enumerate.</span></span> <span data-ttu-id="6b897-116">この場合、 `pcEvents` は0になります。</span><span class="sxs-lookup"><span data-stu-id="6b897-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b897-117">要件</span><span class="sxs-lookup"><span data-stu-id="6b897-117">Requirements</span></span>  

 <span data-ttu-id="6b897-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b897-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b897-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="6b897-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b897-120">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6b897-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b897-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b897-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b897-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b897-122">See also</span></span>

- [<span data-ttu-id="6b897-123">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b897-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6b897-124">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b897-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
