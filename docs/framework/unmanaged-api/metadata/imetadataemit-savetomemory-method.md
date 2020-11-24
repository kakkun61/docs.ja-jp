---
title: IMetaDataEmit::SaveToMemory メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: 1cd5e34d6afefab2fda7e20d4bf73b373ad42787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688589"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="65024-102">IMetaDataEmit::SaveToMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="65024-102">IMetaDataEmit::SaveToMemory Method</span></span>

<span data-ttu-id="65024-103">現在のスコープ内のすべてのメタデータを、指定したメモリ領域に保存します。</span><span class="sxs-lookup"><span data-stu-id="65024-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65024-104">構文</span><span class="sxs-lookup"><span data-stu-id="65024-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65024-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="65024-105">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="65024-106">入出力メタデータの書き込みを開始するアドレス。</span><span class="sxs-lookup"><span data-stu-id="65024-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="65024-107">から割り当てられたメモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="65024-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65024-108">要件</span><span class="sxs-lookup"><span data-stu-id="65024-108">Requirements</span></span>  

 <span data-ttu-id="65024-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="65024-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65024-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="65024-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65024-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="65024-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65024-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65024-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65024-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="65024-113">See also</span></span>

- [<span data-ttu-id="65024-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65024-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="65024-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65024-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
