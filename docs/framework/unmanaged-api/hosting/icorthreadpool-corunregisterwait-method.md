---
title: ICorThreadpool::CorUnregisterWait メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 38b3655da75750ffc3ea1c7983ce3b549d76f087
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733972"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="5263f-102">ICorThreadpool::CorUnregisterWait メソッド</span><span class="sxs-lookup"><span data-stu-id="5263f-102">ICorThreadpool::CorUnregisterWait Method</span></span>

<span data-ttu-id="5263f-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="5263f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5263f-104">構文</span><span class="sxs-lookup"><span data-stu-id="5263f-104">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5263f-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="5263f-105">Requirements</span></span>  

 <span data-ttu-id="5263f-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5263f-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5263f-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="5263f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5263f-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="5263f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5263f-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5263f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5263f-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5263f-110">See also</span></span>

- [<span data-ttu-id="5263f-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5263f-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
