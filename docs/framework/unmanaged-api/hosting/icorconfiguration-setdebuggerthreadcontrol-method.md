---
title: ICorConfiguration::SetDebuggerThreadControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
ms.openlocfilehash: 05df50d80c6b8962b3bdfe2708d5f9d30c58aaea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723923"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="ed2bd-102">ICorConfiguration::SetDebuggerThreadControl メソッド</span><span class="sxs-lookup"><span data-stu-id="ed2bd-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>

<span data-ttu-id="ed2bd-103">共通言語ランタイム (CLR) スレッドがブロックされ、デバッグのためにブロック解除されると、デバッグサービスが呼び出すコールバックインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="ed2bd-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="ed2bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed2bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed2bd-105">Parameters</span></span>  

 `pDebuggerThreadControl`  
 <span data-ttu-id="ed2bd-106">からデバッグサービスによるスレッドのブロックおよびブロック解除についてホストに通知する [Iデバッガ Threadcontrol](idebuggerthreadcontrol-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed2bd-106">[in] A pointer to an [IDebuggerThreadControl](idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed2bd-107">要件</span><span class="sxs-lookup"><span data-stu-id="ed2bd-107">Requirements</span></span>  

 <span data-ttu-id="ed2bd-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2bd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed2bd-109">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ed2bd-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ed2bd-110">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ed2bd-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ed2bd-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed2bd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed2bd-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed2bd-112">See also</span></span>

- [<span data-ttu-id="ed2bd-113">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed2bd-113">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
