---
title: IGCThreadControl::SuspensionStarting メソッド
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
ms.openlocfilehash: 9d39ee79f7734f7dd099a07640ecb06f4f8dcbb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721661"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="021e3-102">IGCThreadControl::SuspensionStarting メソッド</span><span class="sxs-lookup"><span data-stu-id="021e3-102">IGCThreadControl::SuspensionStarting Method</span></span>

<span data-ttu-id="021e3-103">ランタイムがガベージコレクションまたは他の中断のためにスレッドの中断を開始していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="021e3-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="021e3-104">構文</span><span class="sxs-lookup"><span data-stu-id="021e3-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="021e3-105">解説</span><span class="sxs-lookup"><span data-stu-id="021e3-105">Remarks</span></span>  

 <span data-ttu-id="021e3-106">コールバック中にスレッドを再スケジュールしないでください `SuspensionStarting` 。</span><span class="sxs-lookup"><span data-stu-id="021e3-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="021e3-107">要件</span><span class="sxs-lookup"><span data-stu-id="021e3-107">Requirements</span></span>  

 <span data-ttu-id="021e3-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="021e3-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="021e3-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="021e3-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="021e3-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="021e3-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="021e3-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="021e3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="021e3-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="021e3-112">See also</span></span>

- [<span data-ttu-id="021e3-113">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="021e3-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
