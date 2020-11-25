---
title: ITypeName::GetTypeArgumentCount メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArgumentCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArgumentCount
helpviewer_keywords:
- GetTypeArgumentCount method [.NET Framework hosting]
- ITypeName::GetTypeArgumentCount method [.NET Framework hosting]
ms.assetid: ecb5480c-761a-4b02-83e0-b79abc67fd08
topic_type:
- apiref
ms.openlocfilehash: b8684cf9f19070e25e5ed23c072a16473a008903
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727797"
---
# <a name="itypenamegettypeargumentcount-method"></a><span data-ttu-id="1aa85-102">ITypeName::GetTypeArgumentCount メソッド</span><span class="sxs-lookup"><span data-stu-id="1aa85-102">ITypeName::GetTypeArgumentCount Method</span></span>

<span data-ttu-id="1aa85-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="1aa85-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aa85-104">構文</span><span class="sxs-lookup"><span data-stu-id="1aa85-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeArgumentCount (  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1aa85-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="1aa85-105">Requirements</span></span>  

 <span data-ttu-id="1aa85-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1aa85-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aa85-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1aa85-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1aa85-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1aa85-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1aa85-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aa85-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aa85-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="1aa85-110">See also</span></span>

- [<span data-ttu-id="1aa85-111">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1aa85-111">Hosting Interfaces</span></span>](hosting-interfaces.md)
