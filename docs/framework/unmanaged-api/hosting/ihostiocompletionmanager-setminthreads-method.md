---
title: IHostIoCompletionManager::SetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetMinThreads
helpviewer_keywords:
- SetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::SetMinThreads method [.NET Framework hosting]
ms.assetid: dea34b81-8d2b-4cc3-8696-0ad4291d8a92
topic_type:
- apiref
ms.openlocfilehash: 64ea9fdd477ec005b089f451101b742278ab4266
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672410"
---
# <a name="ihostiocompletionmanagersetminthreads-method"></a><span data-ttu-id="887a6-102">IHostIoCompletionManager::SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="887a6-102">IHostIoCompletionManager::SetMinThreads Method</span></span>

<span data-ttu-id="887a6-103">ホストが i/o 完了に割り当てる必要があるスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="887a6-103">Sets the minimum number of threads that the host should allot to I/O completion.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="887a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="887a6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMinThreads (  
    [in] DWORD dwMinIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="887a6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="887a6-105">Parameters</span></span>  

 `dwMinIoCompletionThreads`  
 <span data-ttu-id="887a6-106">からホストが作成する必要がある i/o 完了スレッドの最小数。</span><span class="sxs-lookup"><span data-stu-id="887a6-106">[in] The minimum number of I/O completion threads that the host should create.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="887a6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="887a6-107">Return Value</span></span>  
  
|<span data-ttu-id="887a6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="887a6-108">HRESULT</span></span>|<span data-ttu-id="887a6-109">説明</span><span class="sxs-lookup"><span data-stu-id="887a6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="887a6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="887a6-110">S_OK</span></span>|<span data-ttu-id="887a6-111">`SetMinThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="887a6-111">`SetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="887a6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="887a6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="887a6-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="887a6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="887a6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="887a6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="887a6-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="887a6-115">The call timed out.</span></span>|  
|<span data-ttu-id="887a6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="887a6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="887a6-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="887a6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="887a6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="887a6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="887a6-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="887a6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="887a6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="887a6-120">E_FAIL</span></span>|<span data-ttu-id="887a6-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="887a6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="887a6-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="887a6-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="887a6-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="887a6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="887a6-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="887a6-124">E_NOTIMPL</span></span>|<span data-ttu-id="887a6-125">ホストはの実装を提供していません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="887a6-125">The host does not provide an implementation of `SetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="887a6-126">注釈</span><span class="sxs-lookup"><span data-stu-id="887a6-126">Remarks</span></span>  

 <span data-ttu-id="887a6-127">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、i/o 要求を処理するために割り当てることができるスレッドの数を排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="887a6-127">A host might want exclusive control over the number of threads that can be allotted to process I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="887a6-128">このため、ホストでを実装する必要はありません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="887a6-128">For this reason, the host is not required to implement `SetMinThreads`.</span></span> <span data-ttu-id="887a6-129">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="887a6-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="887a6-130">要件</span><span class="sxs-lookup"><span data-stu-id="887a6-130">Requirements</span></span>  

 <span data-ttu-id="887a6-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="887a6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="887a6-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="887a6-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="887a6-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="887a6-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="887a6-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="887a6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="887a6-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="887a6-135">See also</span></span>

- [<span data-ttu-id="887a6-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="887a6-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="887a6-137">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="887a6-137">SetMaxThreads Method</span></span>](ihostiocompletionmanager-setmaxthreads-method.md)
- [<span data-ttu-id="887a6-138">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="887a6-138">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
