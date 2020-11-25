---
title: IHostTask::Join メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 37156b03b184d06e0c7b03d7d7a9a018793bbb98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721635"
---
# <a name="ihosttaskjoin-method"></a><span data-ttu-id="3d4fc-102">IHostTask::Join メソッド</span><span class="sxs-lookup"><span data-stu-id="3d4fc-102">IHostTask::Join Method</span></span>

<span data-ttu-id="3d4fc-103">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されるタスクが完了するまで、または指定された時間が経過するか、または [IHostTask:: Alert](ihosttask-alert-method.md) が呼び出されるまで、呼び出し元のタスクをブロックします。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-103">Blocks the calling task until the task represented by the current [IHostTask](ihosttask-interface.md) instance completes, the specified time interval elapses, or [IHostTask::Alert](ihosttask-alert-method.md) is called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d4fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d4fc-104">Syntax</span></span>  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d4fc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d4fc-105">Parameters</span></span>  

 `milliseconds`  
 <span data-ttu-id="3d4fc-106">からタスクの終了を待機する時間間隔 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-106">[in] The time interval, in milliseconds, to wait for the task to terminate.</span></span> <span data-ttu-id="3d4fc-107">タスクが終了する前にこの間隔が経過すると、呼び出し元のタスクがブロック解除されます。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-107">If this interval elapses before the task terminates, the calling task unblocks.</span></span>  
  
 `option`  
 <span data-ttu-id="3d4fc-108">から [WAIT_OPTION](wait-option-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-108">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values.</span></span> <span data-ttu-id="3d4fc-109">値 WAIT_ALERTABLE `Alert` は、が経過する前にが呼び出された場合に、タスクをウェイクアップするようにホストに指示 `milliseconds` します。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-109">A value of WAIT_ALERTABLE instructs the host to wake the task if `Alert` is called before `milliseconds` elapses.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d4fc-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d4fc-110">Return Value</span></span>  
  
|<span data-ttu-id="3d4fc-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d4fc-111">HRESULT</span></span>|<span data-ttu-id="3d4fc-112">説明</span><span class="sxs-lookup"><span data-stu-id="3d4fc-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3d4fc-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3d4fc-113">S_OK</span></span>|<span data-ttu-id="3d4fc-114">`Join` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-114">`Join` returned successfully.</span></span>|  
|<span data-ttu-id="3d4fc-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3d4fc-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3d4fc-116">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3d4fc-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3d4fc-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3d4fc-118">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-118">The call timed out.</span></span>|  
|<span data-ttu-id="3d4fc-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3d4fc-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3d4fc-120">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3d4fc-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3d4fc-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3d4fc-122">ブロックされたスレッドまたはファイバーが待機中であるか、または現在の `IHostTask` インスタンスがタスクに関連付けられていないときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-122">An event was canceled while a blocked thread or fiber was waiting on it, or the current `IHostTask` instance is not associated with a task.</span></span>|  
|<span data-ttu-id="3d4fc-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3d4fc-123">E_FAIL</span></span>|<span data-ttu-id="3d4fc-124">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3d4fc-125">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3d4fc-126">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d4fc-127">要件</span><span class="sxs-lookup"><span data-stu-id="3d4fc-127">Requirements</span></span>  

 <span data-ttu-id="3d4fc-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d4fc-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d4fc-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3d4fc-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3d4fc-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3d4fc-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d4fc-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d4fc-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d4fc-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d4fc-132">See also</span></span>

- [<span data-ttu-id="3d4fc-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d4fc-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="3d4fc-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d4fc-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="3d4fc-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d4fc-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="3d4fc-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d4fc-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="3d4fc-137">WAIT_OPTION 列挙型</span><span class="sxs-lookup"><span data-stu-id="3d4fc-137">WAIT_OPTION Enumeration</span></span>](wait-option-enumeration.md)
