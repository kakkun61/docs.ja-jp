---
title: IMetaDataEmit::SetFieldRVA メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 8468b0e7faa520fe2d27e17674af5503871d3b62
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730384"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="f867d-102">IMetaDataEmit::SetFieldRVA メソッド</span><span class="sxs-lookup"><span data-stu-id="f867d-102">IMetaDataEmit::SetFieldRVA Method</span></span>

<span data-ttu-id="f867d-103">指定したトークンによって参照されるフィールドの相対仮想アドレスのグローバル変数値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f867d-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f867d-104">構文</span><span class="sxs-lookup"><span data-stu-id="f867d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (
    [in]  mdFieldDef  fd,
    [in]  ULONG       ulRVA
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f867d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f867d-105">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="f867d-106">からターゲットフィールドのトークン。</span><span class="sxs-lookup"><span data-stu-id="f867d-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="f867d-107">からコードまたはデータ領域のアドレス。</span><span class="sxs-lookup"><span data-stu-id="f867d-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f867d-108">要件</span><span class="sxs-lookup"><span data-stu-id="f867d-108">Requirements</span></span>  

 <span data-ttu-id="f867d-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f867d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f867d-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="f867d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f867d-111">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="f867d-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f867d-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f867d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f867d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f867d-113">See also</span></span>

- [<span data-ttu-id="f867d-114">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f867d-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="f867d-115">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f867d-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
