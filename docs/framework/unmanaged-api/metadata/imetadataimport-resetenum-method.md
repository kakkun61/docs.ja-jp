---
title: IMetaDataImport::ResetEnum メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResetEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResetEnum
helpviewer_keywords:
- ResetEnum method [.NET Framework metadata]
- IMetaDataImport::ResetEnum method [.NET Framework metadata]
ms.assetid: dda867b5-1050-49ba-b01c-fcc83b7a5617
topic_type:
- apiref
ms.openlocfilehash: 52c35b3bd726d4c83c6745bf99940faa44ea7338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702850"
---
# <a name="imetadataimportresetenum-method"></a><span data-ttu-id="30d72-102">IMetaDataImport::ResetEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="30d72-102">IMetaDataImport::ResetEnum Method</span></span>

<span data-ttu-id="30d72-103">指定した列挙子を指定した位置にリセットします。</span><span class="sxs-lookup"><span data-stu-id="30d72-103">Resets the specified enumerator to the specified position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d72-104">構文</span><span class="sxs-lookup"><span data-stu-id="30d72-104">Syntax</span></span>  
  
```cpp  
HRESULT ResetEnum (  
   [in] HCORENUM    hEnum,
   [in] ULONG       ulPos  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30d72-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30d72-105">Parameters</span></span>  

 `hEnum`  
 <span data-ttu-id="30d72-106">からリセットする列挙子。</span><span class="sxs-lookup"><span data-stu-id="30d72-106">[in] The enumerator to reset.</span></span>  
  
 `ulPos`  
 <span data-ttu-id="30d72-107">から列挙子を配置する新しい位置。</span><span class="sxs-lookup"><span data-stu-id="30d72-107">[in] The new position at which to place the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30d72-108">要件</span><span class="sxs-lookup"><span data-stu-id="30d72-108">Requirements</span></span>  

 <span data-ttu-id="30d72-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30d72-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30d72-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="30d72-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30d72-111">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="30d72-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30d72-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30d72-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30d72-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="30d72-113">See also</span></span>

- [<span data-ttu-id="30d72-114">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30d72-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="30d72-115">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30d72-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
