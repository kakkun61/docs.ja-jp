---
title: IHostIoCompletionManager::SetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: ebad4f40-d9f1-4dc6-9b27-a89c9eb3926f
topic_type:
- apiref
ms.openlocfilehash: 3cb001db74587beb5417bf57738c5efb9a274591
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724820"
---
# <a name="ihostiocompletionmanagersetmaxthreads-method"></a><span data-ttu-id="ecf8b-102">IHostIoCompletionManager::SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="ecf8b-102">IHostIoCompletionManager::SetMaxThreads Method</span></span>

<span data-ttu-id="ecf8b-103">ホストが大量の i/o 要求を処理するスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-103">Sets the maximum number of threads that the host allots to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecf8b-104">構文</span><span class="sxs-lookup"><span data-stu-id="ecf8b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMaxThreads (  
    [in] DWORD dwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecf8b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecf8b-105">Parameters</span></span>  

 `dwMaxIoCompletionThreads`  
 <span data-ttu-id="ecf8b-106">からI/o 要求に割り当てるスレッドの最大数。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-106">[in] The maximum number of threads to allot for I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecf8b-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="ecf8b-107">Return Value</span></span>  
  
|<span data-ttu-id="ecf8b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ecf8b-108">HRESULT</span></span>|<span data-ttu-id="ecf8b-109">説明</span><span class="sxs-lookup"><span data-stu-id="ecf8b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ecf8b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecf8b-110">S_OK</span></span>|<span data-ttu-id="ecf8b-111">`SetMaxThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-111">`SetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="ecf8b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ecf8b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ecf8b-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ecf8b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ecf8b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ecf8b-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-115">The call timed out.</span></span>|  
|<span data-ttu-id="ecf8b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ecf8b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ecf8b-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ecf8b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ecf8b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ecf8b-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ecf8b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ecf8b-120">E_FAIL</span></span>|<span data-ttu-id="ecf8b-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ecf8b-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ecf8b-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ecf8b-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ecf8b-124">E_NOTIMPL</span></span>|<span data-ttu-id="ecf8b-125">ホストはの実装を提供していません `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-125">The host does not provide an implementation of `SetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecf8b-126">注釈</span><span class="sxs-lookup"><span data-stu-id="ecf8b-126">Remarks</span></span>  

 <span data-ttu-id="ecf8b-127">`SetMaxThreads` i/o ポートでサービス要求に使用できるスレッドの最大数を設定する機会を CLR に提供します。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-127">`SetMaxThreads` provides the CLR with an opportunity to set the maximum number of threads that are available to service requests on I/O ports.</span></span> <span data-ttu-id="ecf8b-128">ホストには、実装、パフォーマンス、スケーラビリティなどの理由から、スレッドプールのサイズを排他的に制御する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-128">A host might need exclusive control over the size of the thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="ecf8b-129">このため、ホストでを実装する必要はありません `SetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-129">For this reason, the host is not required to implement `SetMaxThreads`.</span></span> <span data-ttu-id="ecf8b-130">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-130">In this case, a host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecf8b-131">要件</span><span class="sxs-lookup"><span data-stu-id="ecf8b-131">Requirements</span></span>  

 <span data-ttu-id="ecf8b-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ecf8b-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecf8b-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ecf8b-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ecf8b-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ecf8b-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecf8b-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecf8b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecf8b-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecf8b-136">See also</span></span>

- [<span data-ttu-id="ecf8b-137">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecf8b-137">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="ecf8b-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecf8b-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
