---
title: IHostSyncManager::CreateMonitorEvent メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: 7fc431861ac8f5c0e47e12e688f4ca004313c062
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704449"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a><span data-ttu-id="72415-102">IHostSyncManager::CreateMonitorEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="72415-102">IHostSyncManager::CreateMonitorEvent Method</span></span>

<span data-ttu-id="72415-103">監視対象の自動リセットイベントオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="72415-103">Creates a monitored auto-reset event object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72415-104">構文</span><span class="sxs-lookup"><span data-stu-id="72415-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72415-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72415-105">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="72415-106">からイベントオブジェクトに関連付けるクッキー。</span><span class="sxs-lookup"><span data-stu-id="72415-106">[in] A cookie to associate with the event object.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="72415-107">入出力 [IHostAutoEvent](ihostautoevent-interface.md) インスタンスのアドレスへのポインター。イベントオブジェクトを作成できなかった場合は null。</span><span class="sxs-lookup"><span data-stu-id="72415-107">[out] A pointer to the address of an [IHostAutoEvent](ihostautoevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72415-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="72415-108">Return Value</span></span>  
  
|<span data-ttu-id="72415-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72415-109">HRESULT</span></span>|<span data-ttu-id="72415-110">説明</span><span class="sxs-lookup"><span data-stu-id="72415-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72415-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="72415-111">S_OK</span></span>|<span data-ttu-id="72415-112">`CreateMonitorEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="72415-112">`CreateMonitorEvent` returned successfully.</span></span>|  
|<span data-ttu-id="72415-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72415-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72415-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="72415-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72415-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72415-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72415-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="72415-116">The call timed out.</span></span>|  
|<span data-ttu-id="72415-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72415-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72415-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="72415-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72415-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72415-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72415-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="72415-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72415-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72415-121">E_FAIL</span></span>|<span data-ttu-id="72415-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="72415-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72415-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="72415-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72415-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="72415-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="72415-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="72415-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="72415-126">要求されたイベントオブジェクトを作成するのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="72415-126">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72415-127">注釈</span><span class="sxs-lookup"><span data-stu-id="72415-127">Remarks</span></span>  

 <span data-ttu-id="72415-128">`CreateMonitorEvent``IHostAutoEvent`CLR がマネージ型の実装で使用するを返し <xref:System.Threading.Monitor?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="72415-128">`CreateMonitorEvent` returns an `IHostAutoEvent` that the CLR uses in its implementation of the managed <xref:System.Threading.Monitor?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="72415-129">このメソッドは、 `CreateEvent` `false` パラメーターに指定された値を使用して、Win32 関数をミラー化し `bManualReset` ます。</span><span class="sxs-lookup"><span data-stu-id="72415-129">This method mirrors the Win32 `CreateEvent` function, with a value of `false` specified for the `bManualReset` parameter.</span></span>  
  
 <span data-ttu-id="72415-130">ホストは cookie を使用して、 [ICLRSyncManager:: GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) メソッドを呼び出すことによって、どのタスクがモニターで待機しているかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="72415-130">The host can use the cookie to determine which task is waiting on the monitor by calling the [ICLRSyncManager::GetMonitorOwner](iclrsyncmanager-getmonitorowner-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72415-131">要件</span><span class="sxs-lookup"><span data-stu-id="72415-131">Requirements</span></span>  

 <span data-ttu-id="72415-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72415-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72415-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="72415-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72415-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="72415-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72415-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72415-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72415-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="72415-136">See also</span></span>

- [<span data-ttu-id="72415-137">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72415-137">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="72415-138">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72415-138">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="72415-139">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72415-139">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
