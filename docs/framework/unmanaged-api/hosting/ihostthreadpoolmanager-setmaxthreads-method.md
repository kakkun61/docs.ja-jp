---
title: IHostThreadPoolManager::SetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type:
- apiref
ms.openlocfilehash: 68e806daa63d13ad6c1f3b5de634c20ca02e8eb4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730717"
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a><span data-ttu-id="b3bba-102">IHostThreadPoolManager::SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="b3bba-102">IHostThreadPoolManager::SetMaxThreads Method</span></span>

<span data-ttu-id="b3bba-103">ホストがスレッドプールで保持できるスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="b3bba-103">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3bba-104">構文</span><span class="sxs-lookup"><span data-stu-id="b3bba-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3bba-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b3bba-105">Parameters</span></span>  

 `MaxThreads`  
 <span data-ttu-id="b3bba-106">スレッド プール内のワーカー スレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="b3bba-106">The maximum number of worker threads in the thread pool.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3bba-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b3bba-107">Return Value</span></span>  
  
|<span data-ttu-id="b3bba-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b3bba-108">HRESULT</span></span>|<span data-ttu-id="b3bba-109">説明</span><span class="sxs-lookup"><span data-stu-id="b3bba-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b3bba-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3bba-110">S_OK</span></span>|<span data-ttu-id="b3bba-111">`SetMaxThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b3bba-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="b3bba-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b3bba-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b3bba-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="b3bba-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b3bba-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b3bba-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b3bba-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="b3bba-115">The call timed out.</span></span>|  
|<span data-ttu-id="b3bba-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b3bba-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b3bba-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="b3bba-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b3bba-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b3bba-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b3bba-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="b3bba-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b3bba-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b3bba-120">E_FAIL</span></span>|<span data-ttu-id="b3bba-121">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="b3bba-121">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b3bba-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="b3bba-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b3bba-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="b3bba-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b3bba-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="b3bba-124">E_NOTIMPL</span></span>|<span data-ttu-id="b3bba-125">ホストはの実装を提供していません `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="b3bba-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3bba-126">注釈</span><span class="sxs-lookup"><span data-stu-id="b3bba-126">Remarks</span></span>  

 <span data-ttu-id="b3bba-127">CLR がスレッドプールのサイズを構成できるようにするために、ホストは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="b3bba-127">A host is not required to allow the CLR to configure the size of the thread pool.</span></span> <span data-ttu-id="b3bba-128">ホストによっては、実装、パフォーマンス、スケーラビリティなどの理由から、スレッドプールを排他的に制御することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b3bba-128">Some hosts might want exclusive control over the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="b3bba-129">この場合、ホストは E_NOTIMPL の HRESULT 値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3bba-129">In this case, a host should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3bba-130">要件</span><span class="sxs-lookup"><span data-stu-id="b3bba-130">Requirements</span></span>  

 <span data-ttu-id="b3bba-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3bba-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3bba-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b3bba-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3bba-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b3bba-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3bba-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3bba-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3bba-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3bba-135">See also</span></span>

- <xref:System.Threading.ThreadPool.SetMaxThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="b3bba-136">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="b3bba-136">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)
- [<span data-ttu-id="b3bba-137">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="b3bba-137">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)
- [<span data-ttu-id="b3bba-138">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3bba-138">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
