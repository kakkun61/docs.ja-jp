---
title: ITypeName::GetModifierLength メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifierLength
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifierLength
helpviewer_keywords:
- ITypeName::GetModifierLength method [.NET Framework hosting]
- GetModifierLength method [.NET Framework hosting]
ms.assetid: ac45f261-03f9-4728-b5d7-dd7cbb05f9e6
topic_type:
- apiref
ms.openlocfilehash: 324e14d38bdb5ad57b3504f4bd2729409d5e1349
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669187"
---
# <a name="itypenamegetmodifierlength-method"></a><span data-ttu-id="49e17-102">ITypeName::GetModifierLength メソッド</span><span class="sxs-lookup"><span data-stu-id="49e17-102">ITypeName::GetModifierLength Method</span></span>

<span data-ttu-id="49e17-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="49e17-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49e17-104">構文</span><span class="sxs-lookup"><span data-stu-id="49e17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifierLength (  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="49e17-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="49e17-105">Requirements</span></span>  

 <span data-ttu-id="49e17-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49e17-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49e17-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="49e17-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49e17-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="49e17-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49e17-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49e17-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49e17-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="49e17-110">See also</span></span>

- [<span data-ttu-id="49e17-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49e17-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
