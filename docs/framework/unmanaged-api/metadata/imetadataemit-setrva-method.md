---
title: IMetaDataEmit::SetRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetRVA
helpviewer_keywords:
- IMetaDataEmit::SetRVA method [.NET Framework metadata]
- SetRVA method [.NET Framework metadata]
ms.assetid: 4d69fb6d-ee35-4318-8224-5eea2bd16818
topic_type:
- apiref
ms.openlocfilehash: df9dc1a36a9adcef3f93a9929565cef117e84d75
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704228"
---
# <a name="imetadataemitsetrva-method"></a><span data-ttu-id="8ccd1-102">IMetaDataEmit::SetRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="8ccd1-102">IMetaDataEmit::SetRVA Method</span></span>

<span data-ttu-id="8ccd1-103">指定したメソッドの相対仮想アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="8ccd1-103">Sets the relative virtual address of the specified method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ccd1-104">構文</span><span class="sxs-lookup"><span data-stu-id="8ccd1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRVA (  
    [in]  mdMethodDef  md,
    [in]  ULONG        ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ccd1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8ccd1-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="8ccd1-106">から対象のメソッドまたはメソッドの実装のトークン。</span><span class="sxs-lookup"><span data-stu-id="8ccd1-106">[in] The token for the target method or method implementation.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="8ccd1-107">からコードまたはデータ領域のアドレス。</span><span class="sxs-lookup"><span data-stu-id="8ccd1-107">[in] The address of the code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ccd1-108">要件</span><span class="sxs-lookup"><span data-stu-id="8ccd1-108">Requirements</span></span>  

 <span data-ttu-id="8ccd1-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ccd1-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ccd1-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="8ccd1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ccd1-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="8ccd1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ccd1-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ccd1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ccd1-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ccd1-113">See also</span></span>

- [<span data-ttu-id="8ccd1-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ccd1-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="8ccd1-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8ccd1-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
