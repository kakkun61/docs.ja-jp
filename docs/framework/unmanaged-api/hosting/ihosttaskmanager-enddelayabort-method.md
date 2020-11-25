---
title: IHostTaskManager::EndDelayAbort メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.EndDelayAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::EndDelayAbort
helpviewer_keywords:
- EndDelayAbort method [.NET Framework hosting]
- IHostTaskManager::EndDelayAbort method [.NET Framework hosting]
ms.assetid: 6e02facb-2504-4356-9af5-0cee1f8436a7
topic_type:
- apiref
ms.openlocfilehash: 6add3cf4d83796b2d95de46cb64f5880a835b6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731671"
---
# <a name="ihosttaskmanagerenddelayabort-method"></a><span data-ttu-id="9757c-102">IHostTaskManager::EndDelayAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="9757c-102">IHostTaskManager::EndDelayAbort Method</span></span>

<span data-ttu-id="9757c-103">以前に [IHostTaskManager:: BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md)を呼び出した後に、マネージコードが現在のタスクを中止できない期間を終了することをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="9757c-103">Notifies the host that managed code is exiting the period in which the current task must not be aborted, following an earlier call to [IHostTaskManager::BeginDelayAbort](ihosttaskmanager-begindelayabort-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9757c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9757c-104">Syntax</span></span>  
  
```cpp  
HRESULT EndDelayAbort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9757c-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="9757c-105">Return Value</span></span>  
  
|<span data-ttu-id="9757c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9757c-106">HRESULT</span></span>|<span data-ttu-id="9757c-107">説明</span><span class="sxs-lookup"><span data-stu-id="9757c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9757c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9757c-108">S_OK</span></span>|<span data-ttu-id="9757c-109">`EndDelayAbort` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9757c-109">`EndDelayAbort` returned successfully.</span></span>|  
|<span data-ttu-id="9757c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9757c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9757c-111">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9757c-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9757c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9757c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9757c-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9757c-113">The call timed out.</span></span>|  
|<span data-ttu-id="9757c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9757c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9757c-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9757c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9757c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9757c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9757c-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9757c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9757c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9757c-118">E_FAIL</span></span>|<span data-ttu-id="9757c-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9757c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9757c-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9757c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9757c-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9757c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9757c-122">E_UNEXPECTED</span><span class="sxs-lookup"><span data-stu-id="9757c-122">E_UNEXPECTED</span></span>|<span data-ttu-id="9757c-123">`EndDelayAbort` は、への対応する呼び出しなしで呼び出されました `BeginDelayAbort` 。</span><span class="sxs-lookup"><span data-stu-id="9757c-123">`EndDelayAbort` was called without a corresponding call to `BeginDelayAbort`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9757c-124">注釈</span><span class="sxs-lookup"><span data-stu-id="9757c-124">Remarks</span></span>  

 <span data-ttu-id="9757c-125">CLR は、を `BeginDelayAbort` 呼び出す前に、現在のタスクに対して、に対応する呼び出しを行い `EndDelayAbort` ます。</span><span class="sxs-lookup"><span data-stu-id="9757c-125">The CLR makes a corresponding call to `BeginDelayAbort` on the current task before calling `EndDelayAbort`.</span></span> <span data-ttu-id="9757c-126">このような対応する呼び出しがない場合、ホストの [IHostTaskManager](ihosttaskmanager-interface.md) の実装はから E_UNEXPECTED を返す必要があり、アクションを実行する必要はあり `EndDelayAbort` ません。</span><span class="sxs-lookup"><span data-stu-id="9757c-126">In the absence of such a corresponding call, the host's implementation of [IHostTaskManager](ihosttaskmanager-interface.md) should return E_UNEXPECTED from `EndDelayAbort`, and should take no action.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9757c-127">要件</span><span class="sxs-lookup"><span data-stu-id="9757c-127">Requirements</span></span>  

 <span data-ttu-id="9757c-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9757c-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9757c-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9757c-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9757c-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9757c-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9757c-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9757c-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9757c-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="9757c-132">See also</span></span>

- <xref:System.Threading>
- [<span data-ttu-id="9757c-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9757c-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9757c-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9757c-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9757c-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9757c-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9757c-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9757c-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
