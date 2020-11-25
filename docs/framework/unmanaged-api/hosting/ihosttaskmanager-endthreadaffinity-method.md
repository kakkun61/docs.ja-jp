---
title: IHostTaskManager::EndThreadAffinity メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndThreadAffinity
helpviewer_keywords:
- EndThreadAffinity method [.NET Framework hosting]
- IHostTaskManager::EndThreadAffinity method [.NET Framework hosting]
ms.assetid: 7738a904-0cd7-4fde-a3eb-2323a5533157
topic_type:
- apiref
ms.openlocfilehash: c662e242cf6745223b1e87716ce4f64971347d2a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731658"
---
# <a name="ihosttaskmanagerendthreadaffinity-method"></a><span data-ttu-id="aa266-102">IHostTaskManager::EndThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="aa266-102">IHostTaskManager::EndThreadAffinity Method</span></span>

<span data-ttu-id="aa266-103">以前に [IHostTaskManager:: BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md)を呼び出した後に、マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を終了していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="aa266-103">Notifies the host that managed code is exiting the period in which the current task must not be moved to another operating system thread, following an earlier call to [IHostTaskManager::BeginThreadAffinity](ihosttaskmanager-beginthreadaffinity-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa266-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa266-104">Syntax</span></span>  
  
```cpp  
HRESULT EndThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aa266-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa266-105">Return Value</span></span>  
  
|<span data-ttu-id="aa266-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa266-106">HRESULT</span></span>|<span data-ttu-id="aa266-107">説明</span><span class="sxs-lookup"><span data-stu-id="aa266-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa266-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa266-108">S_OK</span></span>|<span data-ttu-id="aa266-109">`EndThreadAffinity` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="aa266-109">`EndThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="aa266-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa266-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa266-111">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="aa266-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa266-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa266-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa266-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="aa266-113">The call timed out.</span></span>|  
|<span data-ttu-id="aa266-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa266-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa266-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="aa266-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa266-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa266-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa266-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="aa266-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa266-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa266-118">E_FAIL</span></span>|<span data-ttu-id="aa266-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="aa266-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa266-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="aa266-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa266-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa266-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="aa266-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="aa266-122">E_UNEXPECTED</span></span>|<span data-ttu-id="aa266-123">`EndThreadAffinity` は、以前に対応するへの呼び出しなしで呼び出されました `BeginThreadAffinity` 。</span><span class="sxs-lookup"><span data-stu-id="aa266-123">`EndThreadAffinity` was called without an earlier corresponding call to `BeginThreadAffinity`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa266-124">注釈</span><span class="sxs-lookup"><span data-stu-id="aa266-124">Remarks</span></span>  

 <span data-ttu-id="aa266-125">CLR は、を `BeginThreadAffinity` 呼び出す前に、現在のタスクに対して、に対応する呼び出しを行い `EndThreadAffinity` ます。</span><span class="sxs-lookup"><span data-stu-id="aa266-125">The CLR makes a corresponding call to `BeginThreadAffinity` on the current task before calling `EndThreadAffinity`.</span></span> <span data-ttu-id="aa266-126">このような対応する呼び出しがない場合、ホストの [IHostTaskManager](ihosttaskmanager-interface.md) の実装は E_UNEXPECTED を返し、アクションを実行しません。</span><span class="sxs-lookup"><span data-stu-id="aa266-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED, and take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa266-127">要件</span><span class="sxs-lookup"><span data-stu-id="aa266-127">Requirements</span></span>  

 <span data-ttu-id="aa266-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa266-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa266-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="aa266-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa266-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="aa266-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa266-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa266-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa266-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa266-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="aa266-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa266-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="aa266-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa266-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="aa266-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa266-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="aa266-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aa266-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
