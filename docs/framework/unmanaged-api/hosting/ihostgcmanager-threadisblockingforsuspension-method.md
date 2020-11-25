---
title: IHostGCManager::ThreadIsBlockingForSuspension メソッド
ms.date: 03/30/2017
api_name:
- IHostGCManager.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension
helpviewer_keywords:
- IHostGCManager::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: 2657d45d-26d2-4d0a-8473-32b652e3321d
topic_type:
- apiref
ms.openlocfilehash: 9120085f6a241bcda04946a843799987bf82bb84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723884"
---
# <a name="ihostgcmanagerthreadisblockingforsuspension-method"></a><span data-ttu-id="fdce7-102">IHostGCManager::ThreadIsBlockingForSuspension メソッド</span><span class="sxs-lookup"><span data-stu-id="fdce7-102">IHostGCManager::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="fdce7-103">メソッド呼び出しが行われたスレッドがガベージコレクションに対してブロックされようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="fdce7-103">Notifies the host that the thread from which the method call was made is about to block for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdce7-104">構文</span><span class="sxs-lookup"><span data-stu-id="fdce7-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="fdce7-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="fdce7-105">Return Value</span></span>  
  
|<span data-ttu-id="fdce7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdce7-106">HRESULT</span></span>|<span data-ttu-id="fdce7-107">説明</span><span class="sxs-lookup"><span data-stu-id="fdce7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdce7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdce7-108">S_OK</span></span>|<span data-ttu-id="fdce7-109">`ThreadIsBlockingForSuspension` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="fdce7-109">`ThreadIsBlockingForSuspension` returned successfully.</span></span>|  
|<span data-ttu-id="fdce7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fdce7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fdce7-111">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="fdce7-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fdce7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fdce7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fdce7-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="fdce7-113">The call timed out.</span></span>|  
|<span data-ttu-id="fdce7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fdce7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fdce7-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="fdce7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fdce7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fdce7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fdce7-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="fdce7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fdce7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fdce7-118">E_FAIL</span></span>|<span data-ttu-id="fdce7-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="fdce7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fdce7-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="fdce7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fdce7-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="fdce7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdce7-122">注釈</span><span class="sxs-lookup"><span data-stu-id="fdce7-122">Remarks</span></span>  

 <span data-ttu-id="fdce7-123">CLR は、通常、 `ThreadIsBlockForSuspension` ガベージコレクションの準備としてメソッドを呼び出し、ホストがアンマネージタスクのスレッドを再スケジュールできるようにします。</span><span class="sxs-lookup"><span data-stu-id="fdce7-123">The CLR typically calls the `ThreadIsBlockForSuspension` method in preparation for a garbage collection, to give the host an opportunity to reschedule the thread for unmanaged tasks.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="fdce7-124">ホストは、を呼び出した後にのみタスクを再スケジュールでき `ThreadIsBlockingForSuspension` ます。</span><span class="sxs-lookup"><span data-stu-id="fdce7-124">The host can reschedule tasks only after a call to `ThreadIsBlockingForSuspension`.</span></span> <span data-ttu-id="fdce7-125">ランタイムが [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md)を呼び出した後、ホストはタスクを再スケジュールする必要がありません。</span><span class="sxs-lookup"><span data-stu-id="fdce7-125">After the runtime calls [SuspensionStarting](ihostgcmanager-suspensionstarting-method.md), the host must not reschedule a task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdce7-126">要件</span><span class="sxs-lookup"><span data-stu-id="fdce7-126">Requirements</span></span>  

 <span data-ttu-id="fdce7-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdce7-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdce7-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fdce7-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fdce7-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="fdce7-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdce7-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdce7-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdce7-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdce7-131">See also</span></span>

- [<span data-ttu-id="fdce7-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fdce7-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fdce7-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fdce7-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fdce7-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fdce7-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fdce7-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fdce7-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="fdce7-136">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fdce7-136">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
