---
title: IMetaDataFilter::MarkToken メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: c942838fb62bf86c4054761f4e7f2ef0518b3d89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701810"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="e4c26-102">IMetaDataFilter::MarkToken メソッド</span><span class="sxs-lookup"><span data-stu-id="e4c26-102">IMetaDataFilter::MarkToken Method</span></span>

<span data-ttu-id="e4c26-103">指定したメタデータトークンが処理されたことを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="e4c26-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4c26-104">構文</span><span class="sxs-lookup"><span data-stu-id="e4c26-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4c26-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e4c26-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="e4c26-106">から処理済みとしてマークするトークン。</span><span class="sxs-lookup"><span data-stu-id="e4c26-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4c26-107">要件</span><span class="sxs-lookup"><span data-stu-id="e4c26-107">Requirements</span></span>  

 <span data-ttu-id="e4c26-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4c26-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4c26-109">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="e4c26-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4c26-110">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="e4c26-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4c26-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4c26-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4c26-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4c26-112">See also</span></span>

- [<span data-ttu-id="e4c26-113">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4c26-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
