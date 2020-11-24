---
title: ICorThreadpool::CorCallOrQueueUserWorkItem メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCallOrQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallOrQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorCallOrQueueUserWorkItem method [.NET Framework hosting]
- CorCallOrQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: a2081223-84ca-4331-a8d3-9352f422f3e7
topic_type:
- apiref
ms.openlocfilehash: 6046ff8486b356ca781a42a34a5a18bdae8c4c73
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690019"
---
# <a name="icorthreadpoolcorcallorqueueuserworkitem-method"></a><span data-ttu-id="dab9d-102">ICorThreadpool::CorCallOrQueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="dab9d-102">ICorThreadpool::CorCallOrQueueUserWorkItem Method</span></span>

<span data-ttu-id="dab9d-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="dab9d-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab9d-104">構文</span><span class="sxs-lookup"><span data-stu-id="dab9d-104">Syntax</span></span>  
  
```cpp  
HRESULT CorCallOrQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="dab9d-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="dab9d-105">Requirements</span></span>  

 <span data-ttu-id="dab9d-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dab9d-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab9d-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="dab9d-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dab9d-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dab9d-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dab9d-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab9d-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab9d-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="dab9d-110">See also</span></span>

- [<span data-ttu-id="dab9d-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dab9d-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
