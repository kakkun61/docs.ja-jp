---
title: ICLRTask::Reset メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Reset
helpviewer_keywords:
- ICLRTask::Reset method [.NET Framework hosting]
- Reset method, ICLRTask interface [.NET Framework hosting]
ms.assetid: 1bfb5d3a-0ffd-4bb4-9bf6-aec00cb675b7
topic_type:
- apiref
ms.openlocfilehash: b87bc026a2cac2d0b913128c43142d56aee03025
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725197"
---
# <a name="iclrtaskreset-method"></a><span data-ttu-id="47afc-102">ICLRTask::Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="47afc-102">ICLRTask::Reset Method</span></span>

<span data-ttu-id="47afc-103">ホストがタスクを完了したことを共通言語ランタイム (CLR) に通知し、CLR が現在の [ICLRTask](iclrtask-interface.md) インスタンスを再利用して別のタスクを表すことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="47afc-103">Informs the common language runtime (CLR) that the host has completed a task, and enables the CLR to reuse the current [ICLRTask](iclrtask-interface.md) instance to represent another task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47afc-104">構文</span><span class="sxs-lookup"><span data-stu-id="47afc-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset (  
    [in] BOOL fFull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47afc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="47afc-105">Parameters</span></span>  

 `fFull`  
 <span data-ttu-id="47afc-106">[in] `true` 。ランタイムが、現在のインスタンスに関連するセキュリティおよびロケール情報に加えて、スレッドに関連するすべての静的な値をリセットする必要がある場合は `ICLRTask` 。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="47afc-106">[in] `true`, if the runtime should reset all thread-related static values in addition to the security and locale information related to the current `ICLRTask` instance; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="47afc-107">値がの場合 `true` 、ランタイムはまたはを使用して格納されたデータをリセットし <xref:System.Threading.Thread.AllocateDataSlot%2A> <xref:System.Threading.Thread.AllocateNamedDataSlot%2A> ます。</span><span class="sxs-lookup"><span data-stu-id="47afc-107">If the value is `true`, the runtime resets data that was stored using <xref:System.Threading.Thread.AllocateDataSlot%2A> or <xref:System.Threading.Thread.AllocateNamedDataSlot%2A>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47afc-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="47afc-108">Return Value</span></span>  
  
|<span data-ttu-id="47afc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47afc-109">HRESULT</span></span>|<span data-ttu-id="47afc-110">説明</span><span class="sxs-lookup"><span data-stu-id="47afc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47afc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="47afc-111">S_OK</span></span>|<span data-ttu-id="47afc-112">`Reset` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="47afc-112">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="47afc-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="47afc-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="47afc-114">CLR がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しを処理できません。</span><span class="sxs-lookup"><span data-stu-id="47afc-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call.</span></span> <span data-ttu-id="47afc-115">なく</span><span class="sxs-lookup"><span data-stu-id="47afc-115">successfully</span></span>|  
|<span data-ttu-id="47afc-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="47afc-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="47afc-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="47afc-117">The call timed out.</span></span>|  
|<span data-ttu-id="47afc-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="47afc-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="47afc-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="47afc-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="47afc-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="47afc-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="47afc-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="47afc-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="47afc-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47afc-122">E_FAIL</span></span>|<span data-ttu-id="47afc-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="47afc-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="47afc-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="47afc-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="47afc-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="47afc-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47afc-126">注釈</span><span class="sxs-lookup"><span data-stu-id="47afc-126">Remarks</span></span>  

 <span data-ttu-id="47afc-127">CLR では、 `ICLRTask` 新しいタスクが必要になるたびに新しいインスタンスを繰り返し作成するオーバーヘッドを回避するために、以前に作成されたインスタンスをリサイクルできます。</span><span class="sxs-lookup"><span data-stu-id="47afc-127">The CLR can recycle previously created `ICLRTask` instances to avoid the overhead of repeatedly creating new instances every time it needs a fresh task.</span></span> <span data-ttu-id="47afc-128">ホストは、 `ICLRTask::Reset` タスクを完了したときに、 [ICLRTask:: exittask](iclrtask-exittask-method.md) ではなくを呼び出すことにより、この機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="47afc-128">The host enables this feature by calling `ICLRTask::Reset` instead of [ICLRTask::ExitTask](iclrtask-exittask-method.md) when it has completed a task.</span></span> <span data-ttu-id="47afc-129">インスタンスの通常のライフサイクルの概要を次に示し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="47afc-129">The following list summarizes the normal life cycle of an `ICLRTask` instance:</span></span>  
  
1. <span data-ttu-id="47afc-130">ランタイムは、新しいインスタンスを作成し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="47afc-130">The runtime creates a new `ICLRTask` instance.</span></span>  
  
2. <span data-ttu-id="47afc-131">ランタイムは、 [IHostTaskManager:: GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) を呼び出して、現在のホストタスクへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="47afc-131">The runtime calls [IHostTaskManager::GetCurrentTask](ihosttaskmanager-getcurrenttask-method.md) to get a reference to the current host task.</span></span>  
  
3. <span data-ttu-id="47afc-132">ランタイムは、新しいインスタンスをホストタスクに関連付けるために、 [IHostTask:: SetCLRTask](ihosttask-setclrtask-method.md) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="47afc-132">The runtime calls [IHostTask::SetCLRTask](ihosttask-setclrtask-method.md) to associate the new instance with the host task.</span></span>  
  
4. <span data-ttu-id="47afc-133">タスクが実行され、完了します。</span><span class="sxs-lookup"><span data-stu-id="47afc-133">The task executes and completes.</span></span>  
  
5. <span data-ttu-id="47afc-134">ホストは、を呼び出すことによってタスクを破棄し `ICLRTask::ExitTask` ます。</span><span class="sxs-lookup"><span data-stu-id="47afc-134">The host destroys the task by calling `ICLRTask::ExitTask`.</span></span>  
  
 <span data-ttu-id="47afc-135">`Reset` では、このシナリオを次の2つの方法で変更します。</span><span class="sxs-lookup"><span data-stu-id="47afc-135">`Reset` alters this scenario in two ways.</span></span> <span data-ttu-id="47afc-136">上記の手順5では、ホストがを呼び出して `Reset` タスクをクリーンな状態にリセットし、その `ICLRTask` インスタンスを関連する [IHostTask](ihosttask-interface.md) インスタンスから切り離します。</span><span class="sxs-lookup"><span data-stu-id="47afc-136">In step 5 above, the host calls `Reset` to reset the task to a clean state, and then decouples the `ICLRTask` instance from its associated [IHostTask](ihosttask-interface.md) instance.</span></span> <span data-ttu-id="47afc-137">必要に応じて、ホストはインスタンスをキャッシュして再利用することもでき `IHostTask` ます。</span><span class="sxs-lookup"><span data-stu-id="47afc-137">If desired, the host can also cache the `IHostTask` instance for reuse.</span></span> <span data-ttu-id="47afc-138">上記の手順 1. では、ランタイムは、 `ICLRTask` 新しいインスタンスを作成する代わりに、キャッシュからリサイクルしたを取得します。</span><span class="sxs-lookup"><span data-stu-id="47afc-138">In step 1 above, the runtime pulls a recycled `ICLRTask` from the cache instead of creating a new instance.</span></span>  
  
 <span data-ttu-id="47afc-139">この方法は、ホストに再利用可能なワーカータスクのプールがある場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="47afc-139">This approach works well when the host also has a pool of reusable worker tasks.</span></span> <span data-ttu-id="47afc-140">ホストがそのインスタンスの1つを破棄すると、を `IHostTask` `ICLRTask` 呼び出すことによって、対応するを破棄し `ExitTask` ます。</span><span class="sxs-lookup"><span data-stu-id="47afc-140">When the host destroys one of its `IHostTask` instances, it destroys the corresponding `ICLRTask` by calling `ExitTask`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47afc-141">要件</span><span class="sxs-lookup"><span data-stu-id="47afc-141">Requirements</span></span>  

 <span data-ttu-id="47afc-142">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47afc-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47afc-143">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="47afc-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47afc-144">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="47afc-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47afc-145">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47afc-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47afc-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="47afc-146">See also</span></span>

- [<span data-ttu-id="47afc-147">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47afc-147">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="47afc-148">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47afc-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="47afc-149">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47afc-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="47afc-150">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47afc-150">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
