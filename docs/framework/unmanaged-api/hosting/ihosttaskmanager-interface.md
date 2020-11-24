---
title: IHostTaskManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
ms.openlocfilehash: deb14d291bfd511e8f3534f3c5e32787c259c5e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673112"
---
# <a name="ihosttaskmanager-interface"></a><span data-ttu-id="8c192-102">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c192-102">IHostTaskManager Interface</span></span>

<span data-ttu-id="8c192-103">標準のオペレーティングシステムのスレッド処理やファイバー関数を使用する代わりに、共通言語ランタイム (CLR) がホストを通じてタスクを操作できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8c192-103">Provides methods that allow the common language runtime (CLR) to work with tasks through the host instead of using the standard operating system threading or fiber functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8c192-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-104">Methods</span></span>  
  
|<span data-ttu-id="8c192-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-105">Method</span></span>|<span data-ttu-id="8c192-106">説明</span><span class="sxs-lookup"><span data-stu-id="8c192-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8c192-107">BeginDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-107">BeginDelayAbort Method</span></span>](ihosttaskmanager-begindelayabort-method.md)|<span data-ttu-id="8c192-108">マネージコードが、現在のタスクを中止できない期間を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-108">Notifies the host that managed code is entering a period in which the current task must not be aborted.</span></span>|  
|[<span data-ttu-id="8c192-109">BeginThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-109">BeginThreadAffinity Method</span></span>](ihosttaskmanager-beginthreadaffinity-method.md)|<span data-ttu-id="8c192-110">マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-110">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>|  
|[<span data-ttu-id="8c192-111">CallNeedsHostHook メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-111">CallNeedsHostHook Method</span></span>](ihosttaskmanager-callneedshosthook-method.md)|<span data-ttu-id="8c192-112">共通言語ランタイムがアンマネージ関数に対して指定された呼び出しをインライン展開できるかどうかを指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8c192-112">Enables the host to specify whether the common language runtime can inline the specified call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="8c192-113">CreateTask メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-113">CreateTask Method</span></span>](ihosttaskmanager-createtask-method.md)|<span data-ttu-id="8c192-114">ホストが新しいタスクを作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="8c192-114">Requests that the host create a new task.</span></span>|  
|[<span data-ttu-id="8c192-115">EndDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-115">EndDelayAbort Method</span></span>](ihosttaskmanager-enddelayabort-method.md)|<span data-ttu-id="8c192-116">を以前に呼び出した後に、マネージコードが現在のタスクを中止できない期間を終了することをホストに通知し `BeginDelayAbort` ます。</span><span class="sxs-lookup"><span data-stu-id="8c192-116">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to `BeginDelayAbort`.</span></span>|  
|[<span data-ttu-id="8c192-117">EndThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-117">EndThreadAffinity Method</span></span>](ihosttaskmanager-endthreadaffinity-method.md)|<span data-ttu-id="8c192-118">以前にを呼び出した後に、マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を終了していることをホストに通知し `BeginThreadAffinity` ます。</span><span class="sxs-lookup"><span data-stu-id="8c192-118">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to `BeginThreadAffinity`.</span></span>|  
|[<span data-ttu-id="8c192-119">EnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-119">EnterRuntime Method</span></span>](ihosttaskmanager-enterruntime-method.md)|<span data-ttu-id="8c192-120">プラットフォーム呼び出しメソッドなどのアンマネージメソッドへの呼び出しが実行制御を CLR に返すことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-120">Notifies the host that a call to an unmanaged method, such as a platform invoke method, is returning execution control to the CLR.</span></span>|  
|[<span data-ttu-id="8c192-121">GetCurrentTask メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-121">GetCurrentTask Method</span></span>](ihosttaskmanager-getcurrenttask-method.md)|<span data-ttu-id="8c192-122">この呼び出しが行われたオペレーティングシステムスレッドで現在実行されているタスクへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8c192-122">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>|  
|[<span data-ttu-id="8c192-123">GetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-123">GetStackGuarantee Method</span></span>](ihosttaskmanager-getstackguarantee-method.md)|<span data-ttu-id="8c192-124">スタック操作が完了した後、プロセスが終了する前に使用可能であることが保証されているスタック領域の量を取得します。</span><span class="sxs-lookup"><span data-stu-id="8c192-124">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>|  
|[<span data-ttu-id="8c192-125">LeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-125">LeaveRuntime Method</span></span>](ihosttaskmanager-leaveruntime-method.md)|<span data-ttu-id="8c192-126">マネージコードがアンマネージ関数の呼び出しを実行しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-126">Notifies the host that managed code is about to make a call to an unmanaged function.</span></span>|  
|[<span data-ttu-id="8c192-127">ReverseEnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-127">ReverseEnterRuntime Method</span></span>](ihosttaskmanager-reverseenterruntime-method.md)|<span data-ttu-id="8c192-128">アンマネージコードから共通言語ランタイム (CLR) への呼び出しが行われていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-128">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>|  
|[<span data-ttu-id="8c192-129">ReverseLeaveRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-129">ReverseLeaveRuntime Method</span></span>](ihosttaskmanager-reverseleaveruntime-method.md)|<span data-ttu-id="8c192-130">コントロールが CLR から出ていること、およびマネージコードから呼び出されたアンマネージ関数を入力したことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-130">Notifies the host that control is leaving the CLR and entering an unmanaged function that was, in turn, called from managed code.</span></span>|  
|[<span data-ttu-id="8c192-131">SetCLRTaskManager メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-131">SetCLRTaskManager Method</span></span>](ihosttaskmanager-setclrtaskmanager-method.md)|<span data-ttu-id="8c192-132">CLR によって実装された [ICLRTaskManager](iclrtaskmanager-interface.md) インスタンスへのインターフェイスポインターをホストに提供します。</span><span class="sxs-lookup"><span data-stu-id="8c192-132">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the CLR.</span></span>|  
|[<span data-ttu-id="8c192-133">SetLocale メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-133">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)|<span data-ttu-id="8c192-134">CLR によって現在のタスクのロケールが変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-134">Notifies the host that the CLR has changed the locale on the current task.</span></span>|  
|[<span data-ttu-id="8c192-135">SetStackGuarantee メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-135">SetStackGuarantee Method</span></span>](ihosttaskmanager-setstackguarantee-method.md)|<span data-ttu-id="8c192-136">内部使用専用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="8c192-136">Reserved for internal use only.</span></span>|  
|[<span data-ttu-id="8c192-137">SetUILocale メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-137">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)|<span data-ttu-id="8c192-138">現在のタスクでユーザーインターフェイスのロケールが変更されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-138">Notifies the host that the user interface locale has been changed on the current task.</span></span>|  
|[<span data-ttu-id="8c192-139">Sleep メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-139">Sleep Method</span></span>](ihosttaskmanager-sleep-method.md)|<span data-ttu-id="8c192-140">現在のタスクがスリープ状態になることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-140">Notifies the host that the current task is going to sleep.</span></span>|  
|[<span data-ttu-id="8c192-141">SwitchToTask メソッド</span><span class="sxs-lookup"><span data-stu-id="8c192-141">SwitchToTask Method</span></span>](ihosttaskmanager-switchtotask-method.md)|<span data-ttu-id="8c192-142">現在のタスクを切り替える必要があることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="8c192-142">Notifies the host that it should switch out the current task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c192-143">注釈</span><span class="sxs-lookup"><span data-stu-id="8c192-143">Remarks</span></span>  

 <span data-ttu-id="8c192-144">`IHostTaskManager` CLR がタスクを作成および管理できるようにします。また、コントロールからアンマネージコードへの転送を制御するときにホストがアクションを実行できるようにしたり、コードの実行中にホストが実行できない特定のアクションを指定したりできるようにします。</span><span class="sxs-lookup"><span data-stu-id="8c192-144">`IHostTaskManager` allows the CLR to create and manage tasks, to provide hooks for the host to take action when control transfers from managed to unmanaged code and vice versa, and to specify certain actions the host can and cannot take during code execution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c192-145">要件</span><span class="sxs-lookup"><span data-stu-id="8c192-145">Requirements</span></span>  

 <span data-ttu-id="8c192-146">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c192-146">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c192-147">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8c192-147">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c192-148">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8c192-148">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c192-149">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c192-149">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c192-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c192-150">See also</span></span>

- [<span data-ttu-id="8c192-151">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c192-151">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8c192-152">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c192-152">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8c192-153">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c192-153">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8c192-154">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c192-154">Hosting Interfaces</span></span>](hosting-interfaces.md)
