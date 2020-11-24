---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
ms.openlocfilehash: 490648ab8883b1dba257b82c0d0fa3c8e4783814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684162"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="622e0-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="622e0-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>

<span data-ttu-id="622e0-103">デバッグサービスがブロックされているすべてのスレッドを解放しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="622e0-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="622e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="622e0-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="622e0-105">解説</span><span class="sxs-lookup"><span data-stu-id="622e0-105">Remarks</span></span>  

 <span data-ttu-id="622e0-106">メソッドは、 `ReleaseAllRuntimeThreads` ランタイムスレッドでは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="622e0-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="622e0-107">ホストにランタイムスレッドがブロックされている場合は、この時点で解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="622e0-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="622e0-108">要件</span><span class="sxs-lookup"><span data-stu-id="622e0-108">Requirements</span></span>  

 <span data-ttu-id="622e0-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622e0-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="622e0-110">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="622e0-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="622e0-111">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="622e0-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="622e0-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="622e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622e0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="622e0-113">See also</span></span>

- [<span data-ttu-id="622e0-114">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="622e0-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
