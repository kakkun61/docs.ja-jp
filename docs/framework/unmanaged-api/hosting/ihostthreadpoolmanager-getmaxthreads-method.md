---
title: IHostThreadPoolManager::GetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type:
- apiref
ms.openlocfilehash: 3aecebe2803d3a795db801491d0f60a5eb7c00ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730787"
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a><span data-ttu-id="834d1-102">IHostThreadPoolManager::GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="834d1-102">IHostThreadPoolManager::GetMaxThreads Method</span></span>

<span data-ttu-id="834d1-103">ホストがスレッドプール内で同時に保持するスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="834d1-103">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="834d1-104">構文</span><span class="sxs-lookup"><span data-stu-id="834d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="834d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="834d1-105">Parameters</span></span>  

 `pdwMaxWorkerThreads`  
 <span data-ttu-id="834d1-106">入出力ホストがスレッドプールで保持するスレッドの最大数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="834d1-106">[out] A pointer to the maximum number of threads that the host maintains in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="834d1-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="834d1-107">Return Value</span></span>  
  
|<span data-ttu-id="834d1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="834d1-108">HRESULT</span></span>|<span data-ttu-id="834d1-109">説明</span><span class="sxs-lookup"><span data-stu-id="834d1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="834d1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="834d1-110">S_OK</span></span>|<span data-ttu-id="834d1-111">`GetMaxThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="834d1-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="834d1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="834d1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="834d1-113">共通言語ランタイム (CLR (プロセスに読み込まれていない)、または CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="834d1-113">The common language runtime (CLR( has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="834d1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="834d1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="834d1-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="834d1-115">The call timed out.</span></span>|  
|<span data-ttu-id="834d1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="834d1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="834d1-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="834d1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="834d1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="834d1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="834d1-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="834d1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="834d1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="834d1-120">E_FAIL</span></span>|<span data-ttu-id="834d1-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="834d1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="834d1-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="834d1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="834d1-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="834d1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="834d1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="834d1-124">E_NOTIMPL</span></span>|<span data-ttu-id="834d1-125">ホストはの実装を提供していません `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="834d1-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="834d1-126">注釈</span><span class="sxs-lookup"><span data-stu-id="834d1-126">Remarks</span></span>  

 <span data-ttu-id="834d1-127">CLR はを呼び出して、 `GetMaxThreads` スレッドプール内のスレッドの合計数を確認します。</span><span class="sxs-lookup"><span data-stu-id="834d1-127">The CLR calls `GetMaxThreads` to determine the total number of threads in the thread pool.</span></span> <span data-ttu-id="834d1-128">[Get利用スレッド](ihostthreadpoolmanager-getavailablethreads-method.md)メソッドは、現在作業項目を処理していないスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="834d1-128">The [GetAvailableThreads](ihostthreadpoolmanager-getavailablethreads-method.md) method gets the number of threads that are not currently processing work items.</span></span> <span data-ttu-id="834d1-129">パラメーターの戻り値を超えるすべての要求は `pdwMaxWorkerThreads` 、スレッドが使用可能になるまでキューに置かれたままになります。</span><span class="sxs-lookup"><span data-stu-id="834d1-129">All requests above the returned value of the `pdwMaxWorkerThreads` parameter remain queued until threads become available.</span></span>  
  
 <span data-ttu-id="834d1-130">ホストがの実装を提供していない場合 `GetMaxThreads` 、E_NOTIMPL の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="834d1-130">If the host does not provide an implementation of `GetMaxThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="834d1-131">要件</span><span class="sxs-lookup"><span data-stu-id="834d1-131">Requirements</span></span>  

 <span data-ttu-id="834d1-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="834d1-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="834d1-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="834d1-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="834d1-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="834d1-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="834d1-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="834d1-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="834d1-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="834d1-136">See also</span></span>

- <xref:System.Threading.ThreadPool.GetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="834d1-137">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="834d1-137">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)
- [<span data-ttu-id="834d1-138">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="834d1-138">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)
- [<span data-ttu-id="834d1-139">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="834d1-139">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
