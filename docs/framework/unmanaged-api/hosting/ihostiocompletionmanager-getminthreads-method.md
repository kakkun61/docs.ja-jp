---
title: IHostIoCompletionManager::GetMinThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetMinThreads
helpviewer_keywords:
- GetMinThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetMinThreads method [.NET Framework hosting]
ms.assetid: d7a7f733-677d-481c-b3d5-444fcc502b8e
topic_type:
- apiref
ms.openlocfilehash: d321ce08edf4780fc5f26ac627849b9129c2f283
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673229"
---
# <a name="ihostiocompletionmanagergetminthreads-method"></a><span data-ttu-id="ba68f-102">IHostIoCompletionManager::GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="ba68f-102">IHostIoCompletionManager::GetMinThreads Method</span></span>

<span data-ttu-id="ba68f-103">ホストが i/o 要求を処理するために提供するスレッドの最小数を取得します。</span><span class="sxs-lookup"><span data-stu-id="ba68f-103">Gets the minimum number of threads that the host provides for processing I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba68f-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba68f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMinThreads (  
    [out] DWORD *pdwMinIOCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba68f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba68f-105">Parameters</span></span>  

 `pdwMinIOCompletionThreads`  
 <span data-ttu-id="ba68f-106">入出力I/o 要求を処理するためにホストが提供するスレッドの最小数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ba68f-106">[out] A pointer to the minimum number of threads that the host provides to process I/O requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba68f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="ba68f-107">Return Value</span></span>  
  
|<span data-ttu-id="ba68f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba68f-108">HRESULT</span></span>|<span data-ttu-id="ba68f-109">説明</span><span class="sxs-lookup"><span data-stu-id="ba68f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba68f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba68f-110">S_OK</span></span>|<span data-ttu-id="ba68f-111">`GetMinThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ba68f-111">`GetMinThreads` returned successfully.</span></span>|  
|<span data-ttu-id="ba68f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ba68f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ba68f-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ba68f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ba68f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ba68f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ba68f-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ba68f-115">The call timed out.</span></span>|  
|<span data-ttu-id="ba68f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ba68f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ba68f-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ba68f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ba68f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ba68f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ba68f-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ba68f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ba68f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ba68f-120">E_FAIL</span></span>|<span data-ttu-id="ba68f-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ba68f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ba68f-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ba68f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ba68f-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ba68f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ba68f-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ba68f-124">E_NOTIMPL</span></span>|<span data-ttu-id="ba68f-125">ホストはの実装を提供していません `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="ba68f-125">The host does not provide an implementation of `GetMinThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba68f-126">注釈</span><span class="sxs-lookup"><span data-stu-id="ba68f-126">Remarks</span></span>  

 <span data-ttu-id="ba68f-127">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、サービス i/o 要求に割り当てられたスレッド数を排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="ba68f-127">A host might want exclusive control over the number of threads allotted to service I/O requests, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="ba68f-128">このため、ホストでを実装する必要はありません `GetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="ba68f-128">For this reason, the host is not required to implement `GetMinThreads`.</span></span> <span data-ttu-id="ba68f-129">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba68f-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba68f-130">要件</span><span class="sxs-lookup"><span data-stu-id="ba68f-130">Requirements</span></span>  

 <span data-ttu-id="ba68f-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba68f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba68f-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ba68f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba68f-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ba68f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba68f-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba68f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba68f-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba68f-135">See also</span></span>

- [<span data-ttu-id="ba68f-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba68f-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="ba68f-137">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba68f-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
