---
title: IMetaDataImport::GetModuleFromScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
ms.openlocfilehash: 2eddd7a80c2b9c1b71f3e7fc5b1e4686ba11bccd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733166"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="b011b-102">IMetaDataImport::GetModuleFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="b011b-102">IMetaDataImport::GetModuleFromScope Method</span></span>

<span data-ttu-id="b011b-103">現在のメタデータスコープで参照されているモジュールのメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="b011b-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b011b-104">構文</span><span class="sxs-lookup"><span data-stu-id="b011b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b011b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b011b-105">Parameters</span></span>  

 `pmd`  
 <span data-ttu-id="b011b-106">入出力現在のメタデータスコープで参照されているモジュールを表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b011b-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b011b-107">要件</span><span class="sxs-lookup"><span data-stu-id="b011b-107">Requirements</span></span>  

 <span data-ttu-id="b011b-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b011b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b011b-109">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="b011b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b011b-110">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b011b-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b011b-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b011b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b011b-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b011b-112">See also</span></span>

- [<span data-ttu-id="b011b-113">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b011b-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="b011b-114">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b011b-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
