---
title: IHostSemaphore::Wait メソッド
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: 69b2338e6992c386a3cd34a632d69b73a67f14fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683005"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="8c416-102">IHostSemaphore::Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="8c416-102">IHostSemaphore::Wait Method</span></span>

<span data-ttu-id="8c416-103">現在の [IHostSemaphore](ihostsemaphore-interface.md) インスタンスが所有されるか、指定された時間が経過するまで待機するようにします。</span><span class="sxs-lookup"><span data-stu-id="8c416-103">Causes the current [IHostSemaphore](ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c416-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c416-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c416-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c416-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="8c416-106">から現在のインスタンスが所有されていない場合に、を返す前に待機するミリ秒数 `IHostSemaphore` 。</span><span class="sxs-lookup"><span data-stu-id="8c416-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="8c416-107">から [WAIT_OPTION](wait-option-enumeration.md) 値の1つ。この操作がブロックされた場合にホストが実行するアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="8c416-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c416-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c416-108">Return Value</span></span>  
  
|<span data-ttu-id="8c416-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c416-109">HRESULT</span></span>|<span data-ttu-id="8c416-110">説明</span><span class="sxs-lookup"><span data-stu-id="8c416-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c416-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c416-111">S_OK</span></span>|<span data-ttu-id="8c416-112">`Wait` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8c416-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="8c416-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c416-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c416-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="8c416-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c416-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c416-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c416-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8c416-116">The call timed out.</span></span>|  
|<span data-ttu-id="8c416-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c416-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c416-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8c416-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c416-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c416-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c416-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="8c416-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c416-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c416-121">E_FAIL</span></span>|<span data-ttu-id="8c416-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8c416-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c416-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8c416-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c416-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8c416-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8c416-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="8c416-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="8c416-126">待機間隔中にホストがデッドロックを検出し、現在の `IHostSemaphore` インスタンスをデッドロックの対象として選択しました。</span><span class="sxs-lookup"><span data-stu-id="8c416-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c416-127">要件</span><span class="sxs-lookup"><span data-stu-id="8c416-127">Requirements</span></span>  

 <span data-ttu-id="8c416-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c416-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c416-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8c416-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c416-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8c416-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c416-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c416-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c416-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c416-132">See also</span></span>

- [<span data-ttu-id="8c416-133">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c416-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8c416-134">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c416-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8c416-135">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c416-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="8c416-136">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c416-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="8c416-137">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c416-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
