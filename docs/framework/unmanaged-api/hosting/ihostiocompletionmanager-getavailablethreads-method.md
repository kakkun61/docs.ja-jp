---
title: IHostIoCompletionManager::GetAvailableThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostIoCompletionManager interface [.NET Framework hosting]
- IHostIoCompletionManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: bab363d1-b859-47a4-9884-5661c611cce7
topic_type:
- apiref
ms.openlocfilehash: 3e9f4e98962532efe4b2e2a779add841b7b3a835
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724261"
---
# <a name="ihostiocompletionmanagergetavailablethreads-method"></a><span data-ttu-id="62d73-102">IHostIoCompletionManager::GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="62d73-102">IHostIoCompletionManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="62d73-103">ホストによって管理されているスレッドの合計数に対する i/o 完了スレッドの数を取得します。これは現在、要求を処理していません。</span><span class="sxs-lookup"><span data-stu-id="62d73-103">Gets the number of I/O completion threads, of the total number of threads managed by the host, that are not currently servicing requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62d73-104">構文</span><span class="sxs-lookup"><span data-stu-id="62d73-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableIoCompletionThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62d73-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="62d73-105">Parameters</span></span>  

 `pdwAvailableIoCompletionThreads`  
 <span data-ttu-id="62d73-106">入出力現在サービス要求で使用できるホストによって管理されている i/o 完了スレッドの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="62d73-106">[out] A pointer to the number of I/O completion threads managed by the host that are currently available to service requests.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="62d73-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="62d73-107">Return Value</span></span>  
  
|<span data-ttu-id="62d73-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="62d73-108">HRESULT</span></span>|<span data-ttu-id="62d73-109">説明</span><span class="sxs-lookup"><span data-stu-id="62d73-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="62d73-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="62d73-110">S_OK</span></span>|<span data-ttu-id="62d73-111">`GetAvailableThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="62d73-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="62d73-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="62d73-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="62d73-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="62d73-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="62d73-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="62d73-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="62d73-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="62d73-115">The call timed out.</span></span>|  
|<span data-ttu-id="62d73-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="62d73-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="62d73-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="62d73-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="62d73-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="62d73-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="62d73-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="62d73-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="62d73-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="62d73-120">E_FAIL</span></span>|<span data-ttu-id="62d73-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="62d73-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="62d73-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="62d73-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="62d73-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="62d73-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="62d73-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="62d73-124">E_NOTIMPL</span></span>|<span data-ttu-id="62d73-125">ホストはの実装を提供していません `GetAvailableThreads` 。</span><span class="sxs-lookup"><span data-stu-id="62d73-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62d73-126">注釈</span><span class="sxs-lookup"><span data-stu-id="62d73-126">Remarks</span></span>  

 <span data-ttu-id="62d73-127">ホストは、実装、パフォーマンス、スケーラビリティなどの理由から、i/o 完了スレッドプールのサイズを排他的に制御することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="62d73-127">A host might want exclusive control over the size of the I/O completion thread pool, for reasons such as implementation, performance, or scalability.</span></span> <span data-ttu-id="62d73-128">したがって、ホストでを実装する必要はありません `GetAvailableThreads` 。</span><span class="sxs-lookup"><span data-stu-id="62d73-128">Therefore, the host is not required to implement `GetAvailableThreads`.</span></span> <span data-ttu-id="62d73-129">この場合、ホストはこのメソッドから E_NOTIMPL を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="62d73-129">In this case, the host should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62d73-130">要件</span><span class="sxs-lookup"><span data-stu-id="62d73-130">Requirements</span></span>  

 <span data-ttu-id="62d73-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="62d73-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62d73-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="62d73-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62d73-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="62d73-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62d73-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62d73-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62d73-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="62d73-135">See also</span></span>

- [<span data-ttu-id="62d73-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62d73-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="62d73-137">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="62d73-137">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
