---
title: ICorThreadpool::CorGetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: 511b6e463bcd0d975cf7be96f870baefe27fc77b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720517"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="d5ee4-102">ICorThreadpool::CorGetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d5ee4-102">ICorThreadpool::CorGetMaxThreads Method</span></span>

<span data-ttu-id="d5ee4-103">このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5ee4-104">構文</span><span class="sxs-lookup"><span data-stu-id="d5ee4-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d5ee4-105">必要条件</span><span class="sxs-lookup"><span data-stu-id="d5ee4-105">Requirements</span></span>  

 <span data-ttu-id="d5ee4-106">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d5ee4-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5ee4-107">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d5ee4-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d5ee4-108">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d5ee4-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d5ee4-109">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5ee4-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5ee4-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="d5ee4-110">See also</span></span>

- [<span data-ttu-id="d5ee4-111">ICorThreadpool インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d5ee4-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
