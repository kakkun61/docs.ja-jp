---
title: IMetaDataEmit::SaveToStream メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToStream
helpviewer_keywords:
- IMetaDataEmit::SaveToStream method [.NET Framework metadata]
- SaveToStream method [.NET Framework metadata]
ms.assetid: e0290a49-3818-4a43-ad46-3014faa34f97
topic_type:
- apiref
ms.openlocfilehash: 3f8da08b96c47c90ecccae28dd1662a7abffaf1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688563"
---
# <a name="imetadataemitsavetostream-method"></a><span data-ttu-id="f587f-102">IMetaDataEmit::SaveToStream メソッド</span><span class="sxs-lookup"><span data-stu-id="f587f-102">IMetaDataEmit::SaveToStream Method</span></span>

<span data-ttu-id="f587f-103">現在のスコープ内のすべてのメタデータを、指定したに保存し `IStream` ます。</span><span class="sxs-lookup"><span data-stu-id="f587f-103">Saves all metadata in the current scope to the specified `IStream`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f587f-104">構文</span><span class="sxs-lookup"><span data-stu-id="f587f-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToStream (
    [in]  IStream     *pIStream,  
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f587f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f587f-105">Parameters</span></span>  

 `pIStream`  
 <span data-ttu-id="f587f-106">から保存先の書き込み可能なストリーム。</span><span class="sxs-lookup"><span data-stu-id="f587f-106">[in] The writable stream to save to.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="f587f-107">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="f587f-107">[in] Reserved.</span></span> <span data-ttu-id="f587f-108">ゼロを指定してください。</span><span class="sxs-lookup"><span data-stu-id="f587f-108">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f587f-109">要件</span><span class="sxs-lookup"><span data-stu-id="f587f-109">Requirements</span></span>  

 <span data-ttu-id="f587f-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f587f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f587f-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f587f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f587f-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f587f-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f587f-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f587f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f587f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f587f-114">See also</span></span>

- [<span data-ttu-id="f587f-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f587f-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f587f-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f587f-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
