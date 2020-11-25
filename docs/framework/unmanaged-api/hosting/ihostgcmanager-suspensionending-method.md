---
title: IHostGCManager::SuspensionEnding メソッド
ms.date: 03/30/2017
api_name:
- IHostGCManager.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostGCManager::SuspensionEnding
helpviewer_keywords:
- SuspensionEnding method, IHostGCManager interface [.NET Framework hosting]
- IHostGCManager::SuspensionEnding method [.NET Framework hosting]
ms.assetid: 8849a1db-17f0-44b7-880a-bd36d431eb91
topic_type:
- apiref
ms.openlocfilehash: e2624f5fce168662fac8fd5f4324617c7acf802c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729552"
---
# <a name="ihostgcmanagersuspensionending-method"></a><span data-ttu-id="569c9-102">IHostGCManager::SuspensionEnding メソッド</span><span class="sxs-lookup"><span data-stu-id="569c9-102">IHostGCManager::SuspensionEnding Method</span></span>

<span data-ttu-id="569c9-103">共通言語ランタイム (CLR) がガベージコレクションのために中断されたスレッドでタスクの実行を再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="569c9-103">Notifies the host that the common language runtime (CLR) is resuming execution of tasks on threads that had been suspended for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="569c9-104">構文</span><span class="sxs-lookup"><span data-stu-id="569c9-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="569c9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="569c9-105">Parameters</span></span>  

 `generation`  
 <span data-ttu-id="569c9-106">からスレッドが再開される直前に終了するガベージコレクション生成。</span><span class="sxs-lookup"><span data-stu-id="569c9-106">[in] The garbage collection generation that is just finishing, from which the thread is resuming.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="569c9-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="569c9-107">Return Value</span></span>  
  
|<span data-ttu-id="569c9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="569c9-108">HRESULT</span></span>|<span data-ttu-id="569c9-109">説明</span><span class="sxs-lookup"><span data-stu-id="569c9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="569c9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="569c9-110">S_OK</span></span>|<span data-ttu-id="569c9-111">`SuspensionEnding` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="569c9-111">`SuspensionEnding` returned successfully.</span></span>|  
|<span data-ttu-id="569c9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="569c9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="569c9-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="569c9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="569c9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="569c9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="569c9-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="569c9-115">The call timed out.</span></span>|  
|<span data-ttu-id="569c9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="569c9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="569c9-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="569c9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="569c9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="569c9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="569c9-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="569c9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="569c9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="569c9-120">E_FAIL</span></span>|<span data-ttu-id="569c9-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="569c9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="569c9-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="569c9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="569c9-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="569c9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="569c9-124">注釈</span><span class="sxs-lookup"><span data-stu-id="569c9-124">Remarks</span></span>  

 <span data-ttu-id="569c9-125">CLR は、 `SuspensionEnding` ガベージコレクションを実行した後にを呼び出して、スレッドが実行を再開していることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="569c9-125">The CLR calls `SuspensionEnding` after it performs a garbage collection, to inform the host that the thread is resuming execution.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="569c9-126">メソッドの呼び出しが行われたスレッドを再スケジュールしないでください。</span><span class="sxs-lookup"><span data-stu-id="569c9-126">Do not reschedule the thread the method call was made from.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="569c9-127">要件</span><span class="sxs-lookup"><span data-stu-id="569c9-127">Requirements</span></span>  

 <span data-ttu-id="569c9-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="569c9-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="569c9-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="569c9-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="569c9-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="569c9-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="569c9-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="569c9-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="569c9-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="569c9-132">See also</span></span>

- [<span data-ttu-id="569c9-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="569c9-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="569c9-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="569c9-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="569c9-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="569c9-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="569c9-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="569c9-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="569c9-137">IHostGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="569c9-137">IHostGCManager Interface</span></span>](ihostgcmanager-interface.md)
