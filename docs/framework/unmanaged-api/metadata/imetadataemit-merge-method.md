---
title: IMetaDataEmit::Merge メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: e64d644b511f7c3249c48b9642bfd3163142af3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722012"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="1fa8b-102">IMetaDataEmit::Merge メソッド</span><span class="sxs-lookup"><span data-stu-id="1fa8b-102">IMetaDataEmit::Merge Method</span></span>

<span data-ttu-id="1fa8b-103">マージするスコープの一覧に、指定したインポートされたスコープを追加します。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="1fa8b-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fa8b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1fa8b-105">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="1fa8b-106">からマージするインポートされたスコープを識別する [IMetaDataImport](imetadataimport-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="1fa8b-107">からトークンの再マップを指定する [IMapToken](imaptoken-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="1fa8b-108">からエラーを指定する [IUnknown](/cpp/atl/iunknown) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fa8b-109">注釈</span><span class="sxs-lookup"><span data-stu-id="1fa8b-109">Remarks</span></span>  

 <span data-ttu-id="1fa8b-110">[IMetaDataEmit:: MergeEnd](imetadataemit-mergeend-method.md)を呼び出して、メタデータの1つのスコープへのマージをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fa8b-111">要件</span><span class="sxs-lookup"><span data-stu-id="1fa8b-111">Requirements</span></span>  

 <span data-ttu-id="1fa8b-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fa8b-113">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1fa8b-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1fa8b-114">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1fa8b-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fa8b-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fa8b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa8b-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fa8b-116">See also</span></span>

- [<span data-ttu-id="1fa8b-117">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1fa8b-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1fa8b-118">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1fa8b-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
