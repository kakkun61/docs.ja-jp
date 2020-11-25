---
title: GetAppIdAuthority 関数
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: 5e731ac1c652b8b4505073a3a10463ae0ce21ac0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724495"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="5ccef-102">GetAppIdAuthority 関数</span><span class="sxs-lookup"><span data-stu-id="5ccef-102">GetAppIdAuthority Function</span></span>

<span data-ttu-id="5ccef-103">アプリケーション id と参照のキーを管理する [Iappidauthority](iappidauthority-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="5ccef-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ccef-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ccef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ccef-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5ccef-105">Parameters</span></span>  

 `ppIAppIdAuthority`  
 <span data-ttu-id="5ccef-106">入出力返された `IAppIdAuthority` ポインター。</span><span class="sxs-lookup"><span data-stu-id="5ccef-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ccef-107">要件</span><span class="sxs-lookup"><span data-stu-id="5ccef-107">Requirements</span></span>  

 <span data-ttu-id="5ccef-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ccef-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ccef-109">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="5ccef-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="5ccef-110">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ccef-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ccef-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ccef-111">See also</span></span>

- [<span data-ttu-id="5ccef-112">IAppIdAuthority インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5ccef-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="5ccef-113">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="5ccef-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
