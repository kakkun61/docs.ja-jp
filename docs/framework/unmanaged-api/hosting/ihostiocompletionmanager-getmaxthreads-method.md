---
title: IHostIoCompletionManager::GetMaxThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMaxThreads
helpviewer_keywords:
- IHostIoCompletionManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: e7a6cadc-2433-4472-a701-58891abcde45
topic_type:
- apiref
ms.openlocfilehash: 0b16305bc88854f1ab2ab89ab6b0d4d3e6881cf1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689472"
---
# <a name="ihostiocompletionmanagergetmaxthreads-method"></a><span data-ttu-id="82212-102">IHostIoCompletionManager::GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="82212-102">IHostIoCompletionManager::GetMaxThreads Method</span></span>

<span data-ttu-id="82212-103">ホストがサービス i/o 要求に割り当てることができるスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="82212-103">Gets the maximum number of threads that the host can allot to service I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82212-104">構文</span><span class="sxs-lookup"><span data-stu-id="82212-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82212-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82212-105">Parameters</span></span>  

 `pdwMaxIoCompletionThreads`  
 <span data-ttu-id="82212-106">入出力ホストが i/o 要求を処理するために割り当てることができるスレッドプール内のスレッドの最大数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="82212-106">[out] A pointer to the maximum number of threads in the thread pool that the host can allot to service I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82212-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="82212-107">Return Value</span></span>  
  
|<span data-ttu-id="82212-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="82212-108">HRESULT</span></span>|<span data-ttu-id="82212-109">説明</span><span class="sxs-lookup"><span data-stu-id="82212-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="82212-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="82212-110">S_OK</span></span>|<span data-ttu-id="82212-111">`GetMaxThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="82212-111">`GetMaxThreads` returned successfully.</span></span>|  
|<span data-ttu-id="82212-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="82212-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="82212-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="82212-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="82212-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="82212-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="82212-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="82212-115">The call timed out.</span></span>|  
|<span data-ttu-id="82212-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="82212-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="82212-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="82212-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="82212-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="82212-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="82212-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="82212-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="82212-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="82212-120">E_FAIL</span></span>|<span data-ttu-id="82212-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="82212-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="82212-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="82212-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="82212-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="82212-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="82212-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="82212-124">E_NOTIMPL</span></span>|<span data-ttu-id="82212-125">ホストはの実装を提供していません `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="82212-125">The host does not provide an implementation of `GetMaxThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82212-126">注釈</span><span class="sxs-lookup"><span data-stu-id="82212-126">Remarks</span></span>  

 <span data-ttu-id="82212-127">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、i/o 要求を処理するために割り当てることができるスレッドの数を排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="82212-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="82212-128">このため、ホストでを実装する必要はありません `GetMaxThreads` 。</span><span class="sxs-lookup"><span data-stu-id="82212-128">For this reason, the host is not required to implement `GetMaxThreads`.</span></span> <span data-ttu-id="82212-129">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="82212-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82212-130">要件</span><span class="sxs-lookup"><span data-stu-id="82212-130">Requirements</span></span>  

 <span data-ttu-id="82212-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82212-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82212-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="82212-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="82212-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="82212-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="82212-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82212-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82212-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="82212-135">See also</span></span>

- [<span data-ttu-id="82212-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82212-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="82212-137">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82212-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
