---
title: IHostSyncManager::CreateManualEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateManualEvent
helpviewer_keywords:
- CreateManualEvent method [.NET Framework hosting]
- IHostSyncManager::CreateManualEvent method [.NET Framework hosting]
ms.assetid: 68661fbd-09cf-46dc-890b-e694f8a3880a
topic_type:
- apiref
ms.openlocfilehash: 67af8f125b2be39138bac5d51148215f3a3acf86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723871"
---
# <a name="ihostsyncmanagercreatemanualevent-method"></a><span data-ttu-id="94880-102">IHostSyncManager::CreateManualEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="94880-102">IHostSyncManager::CreateManualEvent Method</span></span>

<span data-ttu-id="94880-103">手動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="94880-103">Creates a manual-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94880-104">構文</span><span class="sxs-lookup"><span data-stu-id="94880-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateManualEvent (  
    [in]  BOOL bInitialState,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94880-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="94880-105">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="94880-106">[in] `true` オブジェクトがシグナル状態の場合は、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="94880-106">[in] `true`, if the object is signaled; otherwise, `false`.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="94880-107">入出力 [IHostManualEvent](ihostmanualevent-interface.md) インスタンスのアドレスへのポインター。イベントを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="94880-107">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94880-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="94880-108">Return Value</span></span>  
  
|<span data-ttu-id="94880-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94880-109">HRESULT</span></span>|<span data-ttu-id="94880-110">説明</span><span class="sxs-lookup"><span data-stu-id="94880-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94880-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="94880-111">S_OK</span></span>|<span data-ttu-id="94880-112">`CreateManualEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="94880-112">`CreateManualEvent` returned successfully.</span></span>|  
|<span data-ttu-id="94880-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="94880-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="94880-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="94880-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="94880-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="94880-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="94880-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="94880-116">The call timed out.</span></span>|  
|<span data-ttu-id="94880-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="94880-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="94880-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="94880-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="94880-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="94880-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="94880-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="94880-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="94880-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="94880-121">E_FAIL</span></span>|<span data-ttu-id="94880-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="94880-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="94880-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="94880-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="94880-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="94880-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="94880-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="94880-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="94880-126">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="94880-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94880-127">注釈</span><span class="sxs-lookup"><span data-stu-id="94880-127">Remarks</span></span>  

 <span data-ttu-id="94880-128">`CreateManualEvent``IHostManualEvent` [IHostManualEvent:: reset](ihostmanualevent-reset-method.md)メソッドを呼び出してシグナル状態以外の状態に設定する必要がある、手動リセットイベントオブジェクトのを作成します。</span><span class="sxs-lookup"><span data-stu-id="94880-128">`CreateManualEvent` creates an `IHostManualEvent`, a manual-reset event object that requires a call to the [IHostManualEvent::Reset](ihostmanualevent-reset-method.md) method to set it to a non-signaled state.</span></span> <span data-ttu-id="94880-129">`CreateManualEvent``CreateEvent` `true` パラメーターに指定された値を使用して、Win32 関数をミラー化し `bManualReset` ます。</span><span class="sxs-lookup"><span data-stu-id="94880-129">`CreateManualEvent` mirrors the Win32 `CreateEvent` function with a value of `true` specified for the `bManualReset` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94880-130">要件</span><span class="sxs-lookup"><span data-stu-id="94880-130">Requirements</span></span>  

 <span data-ttu-id="94880-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94880-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94880-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="94880-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="94880-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="94880-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="94880-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94880-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94880-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="94880-135">See also</span></span>

- [<span data-ttu-id="94880-136">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94880-136">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="94880-137">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94880-137">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="94880-138">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94880-138">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
