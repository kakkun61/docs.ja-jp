---
title: IHostSyncManager::CreateRWLockReaderEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
ms.openlocfilehash: 7c9bf2186d3dc4500694225ea4023df3609b9010
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704384"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="8f82f-102">IHostSyncManager::CreateRWLockReaderEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="8f82f-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>

<span data-ttu-id="8f82f-103">リーダーロックの実装のための手動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="8f82f-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f82f-104">構文</span><span class="sxs-lookup"><span data-stu-id="8f82f-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f82f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8f82f-105">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="8f82f-106">[入力] `true` を `ppEvent` シグナル状態にする必要がある場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="8f82f-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="8f82f-107">からリーダーロックに関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="8f82f-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="8f82f-108">入出力 [IHostManualEvent](ihostmanualevent-interface.md) インスタンスのアドレスへのポインター。イベントオブジェクトを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="8f82f-108">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f82f-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="8f82f-109">Return Value</span></span>  
  
|<span data-ttu-id="8f82f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8f82f-110">HRESULT</span></span>|<span data-ttu-id="8f82f-111">説明</span><span class="sxs-lookup"><span data-stu-id="8f82f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8f82f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="8f82f-112">S_OK</span></span>|<span data-ttu-id="8f82f-113">`CreateRWLockReaderEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8f82f-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="8f82f-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8f82f-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8f82f-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="8f82f-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8f82f-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8f82f-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8f82f-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8f82f-117">The call timed out.</span></span>|  
|<span data-ttu-id="8f82f-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8f82f-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8f82f-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8f82f-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8f82f-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8f82f-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8f82f-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="8f82f-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8f82f-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8f82f-122">E_FAIL</span></span>|<span data-ttu-id="8f82f-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8f82f-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8f82f-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8f82f-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8f82f-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8f82f-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8f82f-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8f82f-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8f82f-127">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="8f82f-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f82f-128">注釈</span><span class="sxs-lookup"><span data-stu-id="8f82f-128">Remarks</span></span>  

 <span data-ttu-id="8f82f-129">CLR は、を呼び出して、 `CreateRWLockReaderEvent` `IHostManualEvent` リーダーロックの実装で使用するインスタンスへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="8f82f-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="8f82f-130">ホストは cookie を使用して、 [ICLRSyncManager](iclrsyncmanager-interface.md) インターフェイスを照会することによって、リーダーロックを待機しているタスクを特定できます。</span><span class="sxs-lookup"><span data-stu-id="8f82f-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f82f-131">要件</span><span class="sxs-lookup"><span data-stu-id="8f82f-131">Requirements</span></span>  

 <span data-ttu-id="8f82f-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f82f-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f82f-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8f82f-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8f82f-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8f82f-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f82f-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f82f-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f82f-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f82f-136">See also</span></span>

- [<span data-ttu-id="8f82f-137">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f82f-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8f82f-138">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f82f-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8f82f-139">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f82f-139">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="8f82f-140">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8f82f-140">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
