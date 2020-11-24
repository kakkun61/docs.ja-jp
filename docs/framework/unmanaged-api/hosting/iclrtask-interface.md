---
title: ICLRTask インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask
helpviewer_keywords:
- ICLRTask interface [.NET Framework hosting]
ms.assetid: b3a44df3-578a-4451-b55e-70c8e7695f5e
topic_type:
- apiref
ms.openlocfilehash: 5ecc42950775a620796a1c775e5f088f461a12c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690825"
---
# <a name="iclrtask-interface"></a><span data-ttu-id="10bf3-102">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10bf3-102">ICLRTask Interface</span></span>

<span data-ttu-id="10bf3-103">ホストが共通言語ランタイム (CLR) の要求を行うことができるようにするメソッド、または関連付けられたタスクについて CLR に通知を提供するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-103">Provides methods that allow the host to make requests of the common language runtime (CLR), or to provide notification to the CLR about the associated task.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10bf3-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-104">Methods</span></span>  
  
|<span data-ttu-id="10bf3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-105">Method</span></span>|<span data-ttu-id="10bf3-106">説明</span><span class="sxs-lookup"><span data-stu-id="10bf3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10bf3-107">Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-107">Abort Method</span></span>](iclrtask-abort-method.md)|<span data-ttu-id="10bf3-108">現在のインスタンスが表すタスクを CLR が中止することを要求 `ICLRTask` します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-108">Requests that the CLR abort the task that the current `ICLRTask` instance represents.</span></span>|  
|[<span data-ttu-id="10bf3-109">ExitTask メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-109">ExitTask Method</span></span>](iclrtask-exittask-method.md)|<span data-ttu-id="10bf3-110">現在のインスタンスに関連付けられているタスクが終了したことを CLR に通知 `ICLRTask` し、タスクを正常にシャットダウンしようとします。</span><span class="sxs-lookup"><span data-stu-id="10bf3-110">Notifies the CLR that the task associated with the current `ICLRTask` instance is ending, and attempts to shut the task down gracefully.</span></span>|  
|[<span data-ttu-id="10bf3-111">GetMemStats メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-111">GetMemStats Method</span></span>](iclrtask-getmemstats-method.md)|<span data-ttu-id="10bf3-112">現在のインスタンスによって表されるタスクによるメモリリソースの使用に関する統計情報を取得し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-112">Gets statistical information on the use of memory resources by the task represented by the current `ICLRTask` instance.</span></span>|  
|[<span data-ttu-id="10bf3-113">LocksHeld メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-113">LocksHeld Method</span></span>](iclrtask-locksheld-method.md)|<span data-ttu-id="10bf3-114">タスクに現在保持されているロックの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-114">Gets the number of locks currently held on the task.</span></span>|  
|[<span data-ttu-id="10bf3-115">NeedsPriorityScheduling メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-115">NeedsPriorityScheduling Method</span></span>](iclrtask-needspriorityscheduling-method.md)|<span data-ttu-id="10bf3-116">現在のインスタンスによって表されるタスクを再スケジュールするために、優先順位の高いホストを割り当てる必要があるかどうかを示す値を取得し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-116">Gets a value indicating whether the host should assign a high priority to rescheduling the task represented by the current `ICLRTask` instance.</span></span>|  
|[<span data-ttu-id="10bf3-117">Reset メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-117">Reset Method</span></span>](iclrtask-reset-method.md)|<span data-ttu-id="10bf3-118">ホストがタスクを完了したことを CLR に通知し、CLR が現在のインスタンスを再利用して別のタスクを表すことができるようにし `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-118">Informs the CLR that the host has completed a task, and enables the CLR to reuse the current `ICLRTask` instance to represent another task.</span></span>|  
|[<span data-ttu-id="10bf3-119">RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-119">RudeAbort Method</span></span>](iclrtask-rudeabort-method.md)|<span data-ttu-id="10bf3-120">CLR が、 `ICLRTask` ファイナライザーが実行されることを保証せずに、現在のインスタンスによって表されるタスクをすぐに中止します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-120">Causes the CLR to abort the task represented by the current `ICLRTask` instance immediately, without a guarantee that finalizers will be executed.</span></span>|  
|[<span data-ttu-id="10bf3-121">SetTaskIdentifier メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-121">SetTaskIdentifier Method</span></span>](iclrtask-settaskidentifier-method.md)|<span data-ttu-id="10bf3-122">デバッグに使用するために、現在のインスタンスによって表されるタスクの一意の識別子を設定し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-122">Sets a unique identifier for the task represented by the current `ICLRTask` instance, for use in debugging.</span></span>|  
|[<span data-ttu-id="10bf3-123">SwitchIn メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-123">SwitchIn Method</span></span>](iclrtask-switchin-method.md)|<span data-ttu-id="10bf3-124">現在のインスタンスによって表されるタスクが操作可能な状態であることを CLR に通知し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-124">Notifies the CLR that the task represented by the current `ICLRTask` instance is in an operable state.</span></span>|  
|[<span data-ttu-id="10bf3-125">SwitchOut メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-125">SwitchOut Method</span></span>](iclrtask-switchout-method.md)|<span data-ttu-id="10bf3-126">現在のインスタンスによって表されるタスクが操作可能 `ICLRTask` な状態ではなくなったことを CLR に通知します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-126">Notifies the CLR that the task represented by the current `ICLRTask` instance is no longer in an operable state.</span></span>|  
|[<span data-ttu-id="10bf3-127">YieldTask メソッド</span><span class="sxs-lookup"><span data-stu-id="10bf3-127">YieldTask Method</span></span>](iclrtask-yieldtask-method.md)|<span data-ttu-id="10bf3-128">CLR がプロセッサ時間を他のタスクで使用できるようにすることを要求します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-128">Requests that the CLR make processor time available to other tasks.</span></span> <span data-ttu-id="10bf3-129">CLR では、処理時間を生成できる状態にタスクが配置されるという保証はありません。</span><span class="sxs-lookup"><span data-stu-id="10bf3-129">The CLR makes no guarantee that the task will be put in a state where it can yield processing time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10bf3-130">注釈</span><span class="sxs-lookup"><span data-stu-id="10bf3-130">Remarks</span></span>  

 <span data-ttu-id="10bf3-131">`ICLRTask`は、CLR のタスクの表現です。</span><span class="sxs-lookup"><span data-stu-id="10bf3-131">An `ICLRTask` is the representation of a task for the CLR.</span></span> <span data-ttu-id="10bf3-132">コードの実行中はいつでも、実行中または実行の待機中のいずれかのタスクを記述できます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-132">At any point during code execution, a task can be described either as running or waiting to run.</span></span> <span data-ttu-id="10bf3-133">ホストは、メソッドを呼び出して、 `ICLRTask::SwitchIn` 現在のインスタンスが表すタスクが操作可能 `ICLRTask` な状態になったことを CLR に通知します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-133">The host calls the `ICLRTask::SwitchIn` method to notify the CLR that the task that the current `ICLRTask` instance represents is now in an operable state.</span></span> <span data-ttu-id="10bf3-134">を呼び出した後、 `ICLRTask::SwitchIn` ホストは任意のオペレーティングシステムスレッドでタスクをスケジュールできます。ただし、 [IHostTaskManager:: beginthreadaffinity](ihosttaskmanager-beginthreadaffinity-method.md) メソッドと [IHostTaskManager:: endthreadaffinity](ihosttaskmanager-endthreadaffinity-method.md) メソッドの呼び出しで指定されているように、ランタイムにスレッドアフィニティが必要な場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-134">After a call to `ICLRTask::SwitchIn`, the host can schedule the task on any operating system thread, except in cases where the runtime requires thread-affinity, as specified by calls to the [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md) and [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md) methods.</span></span> <span data-ttu-id="10bf3-135">しばらくすると、オペレーティングシステムは、スレッドからタスクを削除して、実行されていない状態にする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="10bf3-135">Some time later, the operating system might decide to remove the task from the thread and place it in a non-running state.</span></span> <span data-ttu-id="10bf3-136">たとえば、タスクが同期プリミティブでブロックされた場合や、i/o 操作が完了するまで待機している場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="10bf3-136">For example, this might happen whenever the task blocks on synchronization primitives, or waits for I/O operations to complete.</span></span> <span data-ttu-id="10bf3-137">ホストは [Switchout](iclrtask-switchout-method.md) を呼び出して、現在のインスタンスによって表されるタスクが操作可能 `ICLRTask` な状態ではなくなったことを CLR に通知します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-137">The host calls [SwitchOut](iclrtask-switchout-method.md) to notify the CLR that the task represented by the current `ICLRTask` instance is no longer in an operable state.</span></span>  
  
 <span data-ttu-id="10bf3-138">タスクは通常、コード実行の終了時に終了します。</span><span class="sxs-lookup"><span data-stu-id="10bf3-138">A task typically terminates at the end of code execution.</span></span> <span data-ttu-id="10bf3-139">その時点で、ホストは `ICLRTask::ExitTask` を呼び出して、関連付けられているを破棄し `ICLRTask` ます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-139">At that time, the host calls `ICLRTask::ExitTask` to destroy the associated `ICLRTask`.</span></span> <span data-ttu-id="10bf3-140">ただし、の呼び出しを使用してタスクをリサイクルすることもでき `ICLRTask::Reset` ます。これにより、 `ICLRTask` インスタンスを再度使用できます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-140">However, tasks can also be recycled by using a call to `ICLRTask::Reset`, which allows the `ICLRTask` instance to be used again.</span></span> <span data-ttu-id="10bf3-141">この方法では、インスタンスを繰り返し作成および破棄するオーバーヘッドを回避できます。</span><span class="sxs-lookup"><span data-stu-id="10bf3-141">This approach prevents the overhead of repeatedly creating and destroying instances.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10bf3-142">要件</span><span class="sxs-lookup"><span data-stu-id="10bf3-142">Requirements</span></span>  

 <span data-ttu-id="10bf3-143">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10bf3-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10bf3-144">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="10bf3-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10bf3-145">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="10bf3-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10bf3-146">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10bf3-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10bf3-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="10bf3-147">See also</span></span>

- [<span data-ttu-id="10bf3-148">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10bf3-148">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="10bf3-149">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10bf3-149">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="10bf3-150">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10bf3-150">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="10bf3-151">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10bf3-151">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="10bf3-152">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10bf3-152">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
