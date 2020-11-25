---
title: IHostTaskManager::BeginThreadAffinity メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 6f6d57a52d960c975d468f370477b5d7e29c3aa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727342"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="b7cfd-102">IHostTaskManager::BeginThreadAffinity メソッド</span><span class="sxs-lookup"><span data-stu-id="b7cfd-102">IHostTaskManager::BeginThreadAffinity Method</span></span>

<span data-ttu-id="b7cfd-103">マネージコードが、現在のタスクを別のオペレーティングシステムのスレッドに移動できない期間を入力していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7cfd-104">構文</span><span class="sxs-lookup"><span data-stu-id="b7cfd-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b7cfd-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="b7cfd-105">Return Value</span></span>  
  
|<span data-ttu-id="b7cfd-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7cfd-106">HRESULT</span></span>|<span data-ttu-id="b7cfd-107">説明</span><span class="sxs-lookup"><span data-stu-id="b7cfd-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7cfd-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7cfd-108">S_OK</span></span>|<span data-ttu-id="b7cfd-109">`BeginThreadAffinity` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="b7cfd-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7cfd-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7cfd-111">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b7cfd-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b7cfd-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b7cfd-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-113">The call timed out.</span></span>|  
|<span data-ttu-id="b7cfd-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b7cfd-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b7cfd-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b7cfd-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b7cfd-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b7cfd-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b7cfd-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7cfd-118">E_FAIL</span></span>|<span data-ttu-id="b7cfd-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b7cfd-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b7cfd-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7cfd-122">注釈</span><span class="sxs-lookup"><span data-stu-id="b7cfd-122">Remarks</span></span>  

 <span data-ttu-id="b7cfd-123">CLR は、通常、 `IHostTaskManager::BeginThreadAffinity` の呼び出しのコンテキストでを呼び出し <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b7cfd-124">[IHostTaskManager:: EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md)に対応する呼び出しが行われるまで、現在のタスクを再スケジュールすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="b7cfd-125">タスクは切り替えることができますが、切り替えられたときには、切り替え元のオペレーティングシステムスレッドに割り当てられている必要があります。 `BeginThreadAffinity` 呼び出しは現在のタスクを参照しているので、の入れ子になった呼び出しは無効です。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7cfd-126">要件</span><span class="sxs-lookup"><span data-stu-id="b7cfd-126">Requirements</span></span>  

 <span data-ttu-id="b7cfd-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7cfd-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7cfd-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b7cfd-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7cfd-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b7cfd-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7cfd-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7cfd-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7cfd-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7cfd-131">See also</span></span>

- [<span data-ttu-id="b7cfd-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7cfd-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="b7cfd-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7cfd-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="b7cfd-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7cfd-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="b7cfd-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7cfd-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
