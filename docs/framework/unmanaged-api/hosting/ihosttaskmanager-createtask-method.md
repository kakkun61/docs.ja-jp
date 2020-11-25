---
title: IHostTaskManager::CreateTask メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: 7fdf25d44bdf630e306cf0f5dcb3387a3b0f7c76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731684"
---
# <a name="ihosttaskmanagercreatetask-method"></a><span data-ttu-id="72ce5-102">IHostTaskManager::CreateTask メソッド</span><span class="sxs-lookup"><span data-stu-id="72ce5-102">IHostTaskManager::CreateTask Method</span></span>

<span data-ttu-id="72ce5-103">ホストが新しいタスクを作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="72ce5-103">Requests that the host create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ce5-104">構文</span><span class="sxs-lookup"><span data-stu-id="72ce5-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72ce5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72ce5-105">Parameters</span></span>  

 `stacksize`  
 <span data-ttu-id="72ce5-106">から要求されたスタックの要求されたサイズ (バイト単位)、または既定のサイズの 0 (ゼロ)。</span><span class="sxs-lookup"><span data-stu-id="72ce5-106">[in] The requested size, in bytes, of the requested stack, or 0 (zero) for the default size.</span></span>  
  
 `pStartAddress`  
 <span data-ttu-id="72ce5-107">からタスクが実行する関数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="72ce5-107">[in] A pointer to the function the task is to execute.</span></span>  
  
 `pParameter`  
 <span data-ttu-id="72ce5-108">から関数に渡されるユーザーデータへのポインター。関数がパラメーターを受け取らない場合は null。</span><span class="sxs-lookup"><span data-stu-id="72ce5-108">[in] A pointer to the user data to be passed to the function, or null if the function takes no parameters.</span></span>  
  
 `ppTask`  
 <span data-ttu-id="72ce5-109">入出力ホストによって作成された [IHostTask](ihosttask-interface.md) インスタンスのアドレスへのポインター。タスクを作成できない場合は null。</span><span class="sxs-lookup"><span data-stu-id="72ce5-109">[out] A pointer to the address of an [IHostTask](ihosttask-interface.md) instance created by the host, or null if the task cannot be created.</span></span> <span data-ttu-id="72ce5-110">このタスクは、 [IHostTask:: Start](ihosttask-start-method.md)の呼び出しによって明示的に開始されるまで、中断状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="72ce5-110">The task remains in a suspended state until it is explicitly started by a call to [IHostTask::Start](ihosttask-start-method.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72ce5-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="72ce5-111">Return Value</span></span>  
  
|<span data-ttu-id="72ce5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72ce5-112">HRESULT</span></span>|<span data-ttu-id="72ce5-113">説明</span><span class="sxs-lookup"><span data-stu-id="72ce5-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72ce5-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="72ce5-114">S_OK</span></span>|<span data-ttu-id="72ce5-115">`CreateTask` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="72ce5-115">`CreateTask` returned successfully.</span></span>|  
|<span data-ttu-id="72ce5-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72ce5-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72ce5-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="72ce5-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72ce5-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72ce5-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72ce5-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="72ce5-119">The call timed out.</span></span>|  
|<span data-ttu-id="72ce5-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72ce5-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72ce5-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="72ce5-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72ce5-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72ce5-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72ce5-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="72ce5-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72ce5-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72ce5-124">E_FAIL</span></span>|<span data-ttu-id="72ce5-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="72ce5-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72ce5-126">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="72ce5-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72ce5-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="72ce5-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="72ce5-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="72ce5-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="72ce5-129">要求されたタスクを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="72ce5-129">Not enough memory was available to create the requested task.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72ce5-130">注釈</span><span class="sxs-lookup"><span data-stu-id="72ce5-130">Remarks</span></span>  

 <span data-ttu-id="72ce5-131">CLR はを呼び出して、 `CreateTask` ホストが新しいタスクを作成することを要求します。</span><span class="sxs-lookup"><span data-stu-id="72ce5-131">The CLR calls `CreateTask` to request that the host create a new task.</span></span> <span data-ttu-id="72ce5-132">ホストは、インスタンスへのインターフェイスポインターを返し `IHostTask` ます。</span><span class="sxs-lookup"><span data-stu-id="72ce5-132">The host returns an interface pointer to an `IHostTask` instance.</span></span> <span data-ttu-id="72ce5-133">を呼び出すことによって明示的に開始されるまで、返されたタスクは中断されたままである必要があり `IHostTask::Start` ます。</span><span class="sxs-lookup"><span data-stu-id="72ce5-133">The returned task must remain suspended until it is explicitly started by a call to `IHostTask::Start`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72ce5-134">要件</span><span class="sxs-lookup"><span data-stu-id="72ce5-134">Requirements</span></span>  

 <span data-ttu-id="72ce5-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72ce5-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72ce5-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="72ce5-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72ce5-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="72ce5-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72ce5-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72ce5-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ce5-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="72ce5-139">See also</span></span>

- [<span data-ttu-id="72ce5-140">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72ce5-140">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="72ce5-141">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72ce5-141">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="72ce5-142">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72ce5-142">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="72ce5-143">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72ce5-143">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
