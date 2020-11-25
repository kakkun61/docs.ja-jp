---
title: IHostTask::SetPriority メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.SetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetPriority
helpviewer_keywords:
- IHostTask::SetPriority method [.NET Framework hosting]
- SetPriority method [.NET Framework hosting]
ms.assetid: cd8c379b-c7a0-434f-8e23-899bd26be75d
topic_type:
- apiref
ms.openlocfilehash: 80b4bb2f6a547250acbc16a89e7396c60cc50d87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720452"
---
# <a name="ihosttasksetpriority-method"></a><span data-ttu-id="1bd5e-102">IHostTask::SetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="1bd5e-102">IHostTask::SetPriority Method</span></span>

<span data-ttu-id="1bd5e-103">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されるタスクのスレッドの優先度レベルをホストが調整するように要求します。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-103">Requests that the host adjust the thread priority level for the task represented by the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1bd5e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPriority (  
    [in] int newPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bd5e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1bd5e-105">Parameters</span></span>  

 `newPriority`  
 <span data-ttu-id="1bd5e-106">から現在のインスタンスによって表されるタスクについて、要求されたスレッドの優先順位値を表す整数 `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-106">[in] An integer that represents the requested thread priority value for the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1bd5e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="1bd5e-107">Return Value</span></span>  
  
|<span data-ttu-id="1bd5e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bd5e-108">HRESULT</span></span>|<span data-ttu-id="1bd5e-109">説明</span><span class="sxs-lookup"><span data-stu-id="1bd5e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bd5e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bd5e-110">S_OK</span></span>|<span data-ttu-id="1bd5e-111">`SetPriority` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-111">`SetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="1bd5e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1bd5e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1bd5e-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1bd5e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1bd5e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1bd5e-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-115">The call timed out.</span></span>|  
|<span data-ttu-id="1bd5e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1bd5e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1bd5e-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1bd5e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1bd5e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1bd5e-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1bd5e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1bd5e-120">E_FAIL</span></span>|<span data-ttu-id="1bd5e-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1bd5e-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1bd5e-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bd5e-124">注釈</span><span class="sxs-lookup"><span data-stu-id="1bd5e-124">Remarks</span></span>  

 <span data-ttu-id="1bd5e-125">スレッドには、スレッドの優先度レベルに基づいたラウンドロビンシステムを使用した処理時間が与えられます。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-125">Threads are granted processing time using a round-robin system that is partly based on a thread's priority level.</span></span> <span data-ttu-id="1bd5e-126">`SetPriority` CLR が現在のタスクに対して、そのスレッドの優先度レベルを設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-126">`SetPriority` allows the CLR to set that thread priority level for the current task.</span></span> <span data-ttu-id="1bd5e-127">次の `newPriority` 値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-127">The following `newPriority` values are supported.</span></span>  
  
- <span data-ttu-id="1bd5e-128">THREAD_PRIORITY_ABOVE_NORMAL</span><span class="sxs-lookup"><span data-stu-id="1bd5e-128">THREAD_PRIORITY_ABOVE_NORMAL</span></span>  
  
- <span data-ttu-id="1bd5e-129">THREAD_PRIORITY_BELOW_NORMAL</span><span class="sxs-lookup"><span data-stu-id="1bd5e-129">THREAD_PRIORITY_BELOW_NORMAL</span></span>  
  
- <span data-ttu-id="1bd5e-130">THREAD_PRIORITY_HIGHEST</span><span class="sxs-lookup"><span data-stu-id="1bd5e-130">THREAD_PRIORITY_HIGHEST</span></span>  
  
- <span data-ttu-id="1bd5e-131">THREAD_PRIORITY_IDLE</span><span class="sxs-lookup"><span data-stu-id="1bd5e-131">THREAD_PRIORITY_IDLE</span></span>  
  
- <span data-ttu-id="1bd5e-132">THREAD_PRIORITY_LOWEST</span><span class="sxs-lookup"><span data-stu-id="1bd5e-132">THREAD_PRIORITY_LOWEST</span></span>  
  
- <span data-ttu-id="1bd5e-133">THREAD_PRIORITY_NORMAL</span><span class="sxs-lookup"><span data-stu-id="1bd5e-133">THREAD_PRIORITY_NORMAL</span></span>  
  
- <span data-ttu-id="1bd5e-134">THREAD_PRIORITY_TIME_CRITICAL</span><span class="sxs-lookup"><span data-stu-id="1bd5e-134">THREAD_PRIORITY_TIME_CRITICAL</span></span>  
  
 <span data-ttu-id="1bd5e-135">CLR は `SetPriority` 、の値 <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> がユーザーコードによって変更されたときにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-135">The CLR calls `SetPriority` when the value of the <xref:System.Threading.Thread.Priority%2A?displayProperty=nameWithType> is modified by user code.</span></span> <span data-ttu-id="1bd5e-136">ホストは、スレッドの優先度割り当てに対して独自のアルゴリズムを定義でき、この要求を無視することができます。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-136">A host can define its own algorithms for thread priority assignment, and is free to ignore this request.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bd5e-137">`SetPriority` では、スレッドの優先度レベルが変更されたかどうかは報告されません。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-137">`SetPriority` does not report whether the thread priority level was changed.</span></span> <span data-ttu-id="1bd5e-138">[IHostTask:: GetPriority](ihosttask-getpriority-method.md)を呼び出して、タスクのスレッド優先度レベルの値を決定します。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-138">Call [IHostTask::GetPriority](ihosttask-getpriority-method.md) to determine the value of the task's thread priority level.</span></span>  
  
 <span data-ttu-id="1bd5e-139">スレッドの優先度レベルの値は、Win32 関数によって定義され `SetThreadPriority` ます。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-139">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span> <span data-ttu-id="1bd5e-140">スレッドの優先順位の詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-140">For more information about thread priority, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd5e-141">要件</span><span class="sxs-lookup"><span data-stu-id="1bd5e-141">Requirements</span></span>  

 <span data-ttu-id="1bd5e-142">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bd5e-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd5e-143">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1bd5e-143">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bd5e-144">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1bd5e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bd5e-145">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd5e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd5e-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bd5e-146">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="1bd5e-147">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bd5e-147">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1bd5e-148">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bd5e-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1bd5e-149">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bd5e-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1bd5e-150">GetPriority メソッド</span><span class="sxs-lookup"><span data-stu-id="1bd5e-150">GetPriority Method</span></span>](ihosttask-getpriority-method.md)
- [<span data-ttu-id="1bd5e-151">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bd5e-151">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
