---
title: IHostThreadPoolManager::SetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: 10409db9-9fd2-4e4d-b8cd-cf6fec0afaa2
topic_type:
- apiref
ms.openlocfilehash: d6f56f689a35fa025a924be0db67c893f160fc7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730735"
---
# <a name="ihostthreadpoolmanagersetminthreads-method"></a><span data-ttu-id="d60a6-102">IHostThreadPoolManager::SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d60a6-102">IHostThreadPoolManager::SetMinThreads Method</span></span>

<span data-ttu-id="d60a6-103">ホストが要求を見越して保持する必要があるアイドル状態のスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="d60a6-103">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d60a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="d60a6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD MinThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d60a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d60a6-105">Parameters</span></span>  

 `MinThreads`  
 <span data-ttu-id="d60a6-106">からホストが保持する必要があるスレッドの新しい最小数。</span><span class="sxs-lookup"><span data-stu-id="d60a6-106">[in] The new minimum number of threads that the host must maintain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d60a6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="d60a6-107">Return Value</span></span>  
  
|<span data-ttu-id="d60a6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d60a6-108">HRESULT</span></span>|<span data-ttu-id="d60a6-109">説明</span><span class="sxs-lookup"><span data-stu-id="d60a6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d60a6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d60a6-110">S_OK</span></span>|<span data-ttu-id="d60a6-111">`SetMinThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d60a6-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="d60a6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d60a6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d60a6-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d60a6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d60a6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d60a6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d60a6-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d60a6-115">The call timed out.</span></span>|  
|<span data-ttu-id="d60a6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d60a6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d60a6-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d60a6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d60a6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d60a6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d60a6-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d60a6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d60a6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d60a6-120">E_FAIL</span></span>|<span data-ttu-id="d60a6-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d60a6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d60a6-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d60a6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d60a6-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d60a6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d60a6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d60a6-124">E_NOTIMPL</span></span>|<span data-ttu-id="d60a6-125">ホストはの実装を提供していません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="d60a6-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d60a6-126">注釈</span><span class="sxs-lookup"><span data-stu-id="d60a6-126">Remarks</span></span>  

 <span data-ttu-id="d60a6-127">ホストは、の実装を提供する必要はありません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="d60a6-127">A host is not required to provide an implementation of `SetMinThreads`.</span></span> <span data-ttu-id="d60a6-128">この場合、E_NOTIMPL の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="d60a6-128">In this case, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d60a6-129">要件</span><span class="sxs-lookup"><span data-stu-id="d60a6-129">Requirements</span></span>  

 <span data-ttu-id="d60a6-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d60a6-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d60a6-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d60a6-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d60a6-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d60a6-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d60a6-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d60a6-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d60a6-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="d60a6-134">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="d60a6-135">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d60a6-135">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="d60a6-136">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="d60a6-136">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="d60a6-137">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d60a6-137">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
