---
title: IGCThreadControl::SuspensionEnding メソッド
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 4638672b1d64a9ea07618212cc514d00996470eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721674"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="07e96-102">IGCThreadControl::SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="07e96-102">IGCThreadControl::SuspensionEnding Method</span></span>

<span data-ttu-id="07e96-103">ランタイムがガベージコレクションまたはその他の中断後にスレッドを再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="07e96-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e96-104">構文</span><span class="sxs-lookup"><span data-stu-id="07e96-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e96-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07e96-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="07e96-106">からガベージコレクションが実行された生成。</span><span class="sxs-lookup"><span data-stu-id="07e96-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e96-107">注釈</span><span class="sxs-lookup"><span data-stu-id="07e96-107">Remarks</span></span>  

 <span data-ttu-id="07e96-108">コールバック中にスレッドを再スケジュールしないでください `SuspensionEnding` 。</span><span class="sxs-lookup"><span data-stu-id="07e96-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e96-109">要件</span><span class="sxs-lookup"><span data-stu-id="07e96-109">Requirements</span></span>  

 <span data-ttu-id="07e96-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07e96-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e96-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="07e96-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07e96-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="07e96-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07e96-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e96-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e96-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="07e96-114">See also</span></span>

- [<span data-ttu-id="07e96-115">IGCThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="07e96-115">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
