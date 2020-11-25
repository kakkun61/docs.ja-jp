---
title: GetIdentityAuthority 関数
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
ms.openlocfilehash: e9631211993afbfe968c7122828251746f15c3f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732126"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="c5a1a-102">GetIdentityAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="c5a1a-102">GetIdentityAuthority Function</span></span>

<span data-ttu-id="c5a1a-103">コードオブジェクトのキーを管理する [Iidentity authority](iidentityauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c5a1a-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5a1a-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5a1a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5a1a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5a1a-105">Parameters</span></span>  

 `ppIIdentityAuthority`  
 <span data-ttu-id="c5a1a-106">入出力返された `IIdentityAuthority` ポインター。</span><span class="sxs-lookup"><span data-stu-id="c5a1a-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5a1a-107">要件</span><span class="sxs-lookup"><span data-stu-id="c5a1a-107">Requirements</span></span>  

 <span data-ttu-id="c5a1a-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5a1a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5a1a-109">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="c5a1a-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="c5a1a-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5a1a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5a1a-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5a1a-111">See also</span></span>

- [<span data-ttu-id="c5a1a-112">IIdentityAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c5a1a-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="c5a1a-113">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="c5a1a-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
