---
title: IHostCrst::SetSpinCount メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: 22274759f931da614a234efe0a6f6eb3aade027c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729565"
---
# <a name="ihostcrstsetspincount-method"></a><span data-ttu-id="9a138-102">IHostCrst::SetSpinCount メソッド</span><span class="sxs-lookup"><span data-stu-id="9a138-102">IHostCrst::SetSpinCount Method</span></span>

<span data-ttu-id="9a138-103">現在の [IHostCrst](ihostcrst-interface.md) インスタンスのスピンカウントを設定します。</span><span class="sxs-lookup"><span data-stu-id="9a138-103">Sets the spin count for the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a138-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a138-104">Syntax</span></span>  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a138-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9a138-105">Parameters</span></span>  

 `dwSpinCount`  
 <span data-ttu-id="9a138-106">から現在のインスタンスの新しいスピンカウント `IHostCrst` 。</span><span class="sxs-lookup"><span data-stu-id="9a138-106">[in] The new spin count for the current `IHostCrst` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a138-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a138-107">Return Value</span></span>  
  
|<span data-ttu-id="9a138-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a138-108">HRESULT</span></span>|<span data-ttu-id="9a138-109">説明</span><span class="sxs-lookup"><span data-stu-id="9a138-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a138-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a138-110">S_OK</span></span>|<span data-ttu-id="9a138-111">`SetSpinCount` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9a138-111">`SetSpinCount` returned successfully.</span></span>|  
|<span data-ttu-id="9a138-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a138-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a138-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9a138-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a138-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a138-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a138-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9a138-115">The call timed out.</span></span>|  
|<span data-ttu-id="9a138-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a138-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a138-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9a138-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a138-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a138-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a138-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9a138-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a138-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a138-120">E_FAIL</span></span>|<span data-ttu-id="9a138-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9a138-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a138-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9a138-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a138-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9a138-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a138-124">注釈</span><span class="sxs-lookup"><span data-stu-id="9a138-124">Remarks</span></span>  

 <span data-ttu-id="9a138-125">マルチプロセッサシステムでは、現在のインスタンスによって表されるクリティカルセクション `IHostCrst` が使用できない場合、呼び出し元のスレッドは、 `dwSpinCount` クリティカルセクションに関連付けられているセマフォで [IHostSemaphore:: Wait](ihostsemaphore-wait-method.md) を呼び出す前に時間をスピンします。</span><span class="sxs-lookup"><span data-stu-id="9a138-125">On multi-processor systems, if the critical section represented by the current `IHostCrst` instance is unavailable, a calling thread spins `dwSpinCount` times before calling [IHostSemaphore::Wait](ihostsemaphore-wait-method.md) on a semaphore associated with the critical section.</span></span> <span data-ttu-id="9a138-126">スピン操作中にクリティカルセクションが解放されると、呼び出し元のスレッドは待機操作を回避します。</span><span class="sxs-lookup"><span data-stu-id="9a138-126">If the critical section becomes free during the spin operation, the calling thread avoids the wait operation.</span></span>  
  
 <span data-ttu-id="9a138-127">の使用方法 `dwSpinCount` は、Win32 関数で同じ名前のパラメーターを使用する場合と同じです `InitializeCriticalSectionAndSpinCount` 。</span><span class="sxs-lookup"><span data-stu-id="9a138-127">The usage of `dwSpinCount` is identical to the usage of the parameter of the same name in the Win32 `InitializeCriticalSectionAndSpinCount` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a138-128">要件</span><span class="sxs-lookup"><span data-stu-id="9a138-128">Requirements</span></span>  

 <span data-ttu-id="9a138-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a138-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a138-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9a138-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a138-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9a138-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a138-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a138-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a138-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a138-133">See also</span></span>

- [<span data-ttu-id="9a138-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a138-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="9a138-135">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a138-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="9a138-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a138-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
