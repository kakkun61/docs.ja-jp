---
title: IDebuggerThreadControl::StartBlockingForDebugger メソッド
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
ms.openlocfilehash: 1e0cb52a6b9f03209256e5398415b4ec632fb5e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705507"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="64781-102">IDebuggerThreadControl::StartBlockingForDebugger メソッド</span><span class="sxs-lookup"><span data-stu-id="64781-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>

<span data-ttu-id="64781-103">デバッグサービスがすべてのスレッドのブロックを開始しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="64781-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64781-104">構文</span><span class="sxs-lookup"><span data-stu-id="64781-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64781-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="64781-105">Parameters</span></span>  

 `dwUnused`  
 <span data-ttu-id="64781-106">から将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="64781-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64781-107">注釈</span><span class="sxs-lookup"><span data-stu-id="64781-107">Remarks</span></span>  

 <span data-ttu-id="64781-108">`StartBlockingForDebugger`ランタイムスレッドでメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="64781-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64781-109">要件</span><span class="sxs-lookup"><span data-stu-id="64781-109">Requirements</span></span>  

 <span data-ttu-id="64781-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64781-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64781-111">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="64781-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="64781-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="64781-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="64781-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64781-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64781-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="64781-114">See also</span></span>

- [<span data-ttu-id="64781-115">IDebuggerThreadControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="64781-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
