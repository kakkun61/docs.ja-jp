---
title: IHostTask::SetCLRTask メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.SetCLRTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::SetCLRTask
helpviewer_keywords:
- SetCLRTask method [.NET Framework hosting]
- IHostTask::SetCLRTask method [.NET Framework hosting]
ms.assetid: e9d39c80-41a1-49e7-bb5e-ea3433bfb5d7
topic_type:
- apiref
ms.openlocfilehash: e6b9a4015a6139d6c8d7101fa7811c7ad9134e4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720465"
---
# <a name="ihosttasksetclrtask-method"></a><span data-ttu-id="29150-102">IHostTask::SetCLRTask メソッド</span><span class="sxs-lookup"><span data-stu-id="29150-102">IHostTask::SetCLRTask Method</span></span>

<span data-ttu-id="29150-103">インスタンスを `ICLRTask` 現在の [IHostTask](ihosttask-interface.md) インスタンスに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="29150-103">Associates an `ICLRTask` instance with the current [IHostTask](ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29150-104">構文</span><span class="sxs-lookup"><span data-stu-id="29150-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTask (  
    [in] ICLRTask *pCLRTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29150-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="29150-105">Parameters</span></span>  

 `pCLRTask`  
 <span data-ttu-id="29150-106">から `ICLRTask` 現在のインスタンスに関連付けられるインスタンスへのインターフェイスポインター `IHostTask` 。</span><span class="sxs-lookup"><span data-stu-id="29150-106">[in] An interface pointer to the `ICLRTask` instance to be associated with the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29150-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="29150-107">Return Value</span></span>  
  
|<span data-ttu-id="29150-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29150-108">HRESULT</span></span>|<span data-ttu-id="29150-109">説明</span><span class="sxs-lookup"><span data-stu-id="29150-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29150-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="29150-110">S_OK</span></span>|<span data-ttu-id="29150-111">`SetCLRTask` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="29150-111">`SetCLRTask` returned successfully.</span></span>|  
|<span data-ttu-id="29150-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29150-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29150-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="29150-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29150-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="29150-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="29150-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="29150-115">The call timed out.</span></span>|  
|<span data-ttu-id="29150-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="29150-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="29150-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="29150-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="29150-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="29150-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="29150-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="29150-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="29150-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29150-120">E_FAIL</span></span>|<span data-ttu-id="29150-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="29150-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29150-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="29150-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29150-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="29150-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29150-124">注釈</span><span class="sxs-lookup"><span data-stu-id="29150-124">Remarks</span></span>  

 <span data-ttu-id="29150-125">CLR は `SetCLRTask` を呼び出して、インスタンスを現在のインスタンスに関連付けます `ICLRTask` `IHostTask` 。これは [IHostTaskManager:: createtask](ihosttaskmanager-createtask-method.md)の呼び出しによって作成されたものです。</span><span class="sxs-lookup"><span data-stu-id="29150-125">The CLR calls `SetCLRTask` to associate an `ICLRTask` instance with the current `IHostTask` instance, which was created by a call to [IHostTaskManager::CreateTask](ihosttaskmanager-createtask-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29150-126">要件</span><span class="sxs-lookup"><span data-stu-id="29150-126">Requirements</span></span>  

 <span data-ttu-id="29150-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29150-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29150-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="29150-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29150-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="29150-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29150-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29150-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29150-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="29150-131">See also</span></span>

- [<span data-ttu-id="29150-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29150-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="29150-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29150-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="29150-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29150-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="29150-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29150-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
