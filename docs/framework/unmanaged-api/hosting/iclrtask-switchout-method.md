---
title: ICLRTask::SwitchOut メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.SwitchOut
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SwitchOut
helpviewer_keywords:
- ICLRTask::SwitchOut method [.NET Framework hosting]
- SwitchOut method [.NET Framework hosting]
ms.assetid: b6fb168c-b24b-4ecf-a390-2b5ba3317ae6
topic_type:
- apiref
ms.openlocfilehash: 1b27983b3f10eba225442dcd2f5df02062e53ed4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720273"
---
# <a name="iclrtaskswitchout-method"></a><span data-ttu-id="bb0c2-102">ICLRTask::SwitchOut メソッド</span><span class="sxs-lookup"><span data-stu-id="bb0c2-102">ICLRTask::SwitchOut Method</span></span>

<span data-ttu-id="bb0c2-103">現在の [ICLRTask](iclrtask-interface.md) インスタンスによって表されるタスクが操作可能な状態ではなくなったことを、共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is no longer in an operable state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb0c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb0c2-104">Syntax</span></span>  
  
```cpp  
HRESULT SwitchOut ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bb0c2-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="bb0c2-105">Return Value</span></span>  
  
|<span data-ttu-id="bb0c2-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb0c2-106">HRESULT</span></span>|<span data-ttu-id="bb0c2-107">説明</span><span class="sxs-lookup"><span data-stu-id="bb0c2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb0c2-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb0c2-108">S_OK</span></span>|<span data-ttu-id="bb0c2-109">`SwitchOut` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-109">`SwitchOut` returned successfully.</span></span>|  
|<span data-ttu-id="bb0c2-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb0c2-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb0c2-111">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb0c2-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb0c2-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb0c2-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-113">The call timed out.</span></span>|  
|<span data-ttu-id="bb0c2-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb0c2-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb0c2-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb0c2-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb0c2-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb0c2-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb0c2-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb0c2-118">E_FAIL</span></span>|<span data-ttu-id="bb0c2-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb0c2-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb0c2-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb0c2-122">注釈</span><span class="sxs-lookup"><span data-stu-id="bb0c2-122">Remarks</span></span>  

 <span data-ttu-id="bb0c2-123">ホストは、 `SwitchOut` 現在のインスタンスが表すタスクの実行を一時的に停止したことを CLR に通知し、タスクを再 `ICLRTask` スケジュールします。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-123">A host calls `SwitchOut` to inform the CLR that it has temporarily stopped executing the task that the current `ICLRTask` instance represents, and will reschedule the task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb0c2-124">要件</span><span class="sxs-lookup"><span data-stu-id="bb0c2-124">Requirements</span></span>  

 <span data-ttu-id="bb0c2-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb0c2-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb0c2-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bb0c2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb0c2-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bb0c2-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb0c2-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb0c2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb0c2-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb0c2-129">See also</span></span>

- [<span data-ttu-id="bb0c2-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb0c2-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bb0c2-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb0c2-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bb0c2-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb0c2-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bb0c2-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb0c2-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
