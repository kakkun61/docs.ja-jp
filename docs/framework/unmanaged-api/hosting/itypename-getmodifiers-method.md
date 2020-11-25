---
title: ITypeName::GetModifiers メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
ms.openlocfilehash: 64751032c017473ffd82248b310b14c087f74129
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727836"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="9bf6d-102">ITypeName::GetModifiers メソッド</span><span class="sxs-lookup"><span data-stu-id="9bf6d-102">ITypeName::GetModifiers Method</span></span>

<span data-ttu-id="9bf6d-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="9bf6d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf6d-104">構文</span><span class="sxs-lookup"><span data-stu-id="9bf6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9bf6d-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="9bf6d-105">Requirements</span></span>  

 <span data-ttu-id="9bf6d-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bf6d-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bf6d-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9bf6d-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9bf6d-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9bf6d-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9bf6d-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bf6d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf6d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bf6d-110">See also</span></span>

- [<span data-ttu-id="9bf6d-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9bf6d-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
