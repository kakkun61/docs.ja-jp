---
title: IHostTask::Alert メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: 5a4870a4472081a78cd1fade51f441c22aa5eb48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720478"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="2bfd4-102">IHostTask::Alert メソッド</span><span class="sxs-lookup"><span data-stu-id="2bfd4-102">IHostTask::Alert Method</span></span>

<span data-ttu-id="2bfd4-103">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されるタスクをホストがスリープ解除するように要求します。これにより、タスクを中止できます。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-103">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bfd4-104">構文</span><span class="sxs-lookup"><span data-stu-id="2bfd4-104">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2bfd4-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="2bfd4-105">Return Value</span></span>  
  
|<span data-ttu-id="2bfd4-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2bfd4-106">HRESULT</span></span>|<span data-ttu-id="2bfd4-107">説明</span><span class="sxs-lookup"><span data-stu-id="2bfd4-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2bfd4-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2bfd4-108">S_OK</span></span>|<span data-ttu-id="2bfd4-109">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-109">The method returned successfully.</span></span>|  
|<span data-ttu-id="2bfd4-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2bfd4-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2bfd4-111">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2bfd4-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2bfd4-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2bfd4-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-113">The call timed out.</span></span>|  
|<span data-ttu-id="2bfd4-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2bfd4-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2bfd4-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2bfd4-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2bfd4-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2bfd4-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2bfd4-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2bfd4-118">E_FAIL</span></span>|<span data-ttu-id="2bfd4-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2bfd4-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2bfd4-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bfd4-122">注釈</span><span class="sxs-lookup"><span data-stu-id="2bfd4-122">Remarks</span></span>  

 <span data-ttu-id="2bfd4-123">`Alert` <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> がユーザーコードから呼び出された場合、または <xref:System.AppDomain> 現在のに関連付けられているがシャットダウンした場合、CLR はメソッドを呼び出し <xref:System.Threading.Thread> ます。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-123">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="2bfd4-124">呼び出しは非同期的に行われるため、ホストはすぐに制御を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-124">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="2bfd4-125">ホストがすぐにタスクを警告できない場合は、次にアラートが通知される状態になったときに起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-125">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2bfd4-126">`Alert`は、ランタイムが[Join](ihosttask-join-method.md)などのメソッドに WAIT_ALERTABLE の[WAIT_OPTION](wait-option-enumeration.md)値を渡したタスクにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-126">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bfd4-127">要件</span><span class="sxs-lookup"><span data-stu-id="2bfd4-127">Requirements</span></span>  

 <span data-ttu-id="2bfd4-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bfd4-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bfd4-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="2bfd4-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2bfd4-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="2bfd4-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2bfd4-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bfd4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bfd4-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bfd4-132">See also</span></span>

- [<span data-ttu-id="2bfd4-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bfd4-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="2bfd4-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bfd4-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="2bfd4-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bfd4-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="2bfd4-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bfd4-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
