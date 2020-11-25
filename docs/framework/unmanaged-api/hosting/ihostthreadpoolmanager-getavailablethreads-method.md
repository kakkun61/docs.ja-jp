---
title: IHostThreadPoolManager::GetAvailableThreads メソッド
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetAvailableThreads
helpviewer_keywords:
- GetAvailableThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
- IHostThreadPoolManager::GetAvailableThreads method [.NET Framework hosting]
ms.assetid: 61d26dfd-7f24-4e7d-a63e-b30a463f08e1
topic_type:
- apiref
ms.openlocfilehash: 64d5ba9ad5557f99b175c277d48003529d77861c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730800"
---
# <a name="ihostthreadpoolmanagergetavailablethreads-method"></a><span data-ttu-id="0b3ae-102">IHostThreadPoolManager::GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="0b3ae-102">IHostThreadPoolManager::GetAvailableThreads Method</span></span>

<span data-ttu-id="0b3ae-103">現在作業項目を処理していないスレッドプール内のスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-103">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b3ae-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b3ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAvailableThreads (  
    [out] DWORD *pdwAvailableWorkerThreads  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b3ae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b3ae-105">Parameters</span></span>  

 `pdwAvailableWorkerThreads`  
 <span data-ttu-id="0b3ae-106">入出力現在作業項目を処理していないスレッドプール内のスレッドの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-106">[out] Pointer to the number of threads in the thread pool that are not currently processing work items.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b3ae-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0b3ae-107">Return Value</span></span>  
  
|<span data-ttu-id="0b3ae-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b3ae-108">HRESULT</span></span>|<span data-ttu-id="0b3ae-109">説明</span><span class="sxs-lookup"><span data-stu-id="0b3ae-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b3ae-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b3ae-110">S_OK</span></span>|<span data-ttu-id="0b3ae-111">`GetAvailableThreads` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-111">`GetAvailableThreads` returned successfully.</span></span>|  
|<span data-ttu-id="0b3ae-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b3ae-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b3ae-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b3ae-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b3ae-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b3ae-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-115">The call timed out.</span></span>|  
|<span data-ttu-id="0b3ae-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b3ae-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b3ae-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b3ae-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b3ae-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b3ae-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b3ae-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0b3ae-120">E_FAIL</span></span>|<span data-ttu-id="0b3ae-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b3ae-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b3ae-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0b3ae-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0b3ae-124">E_NOTIMPL</span></span>|<span data-ttu-id="0b3ae-125">ホストはの実装を提供していません `GetAvailableThreads` 。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-125">The host does not provide an implementation of `GetAvailableThreads`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b3ae-126">注釈</span><span class="sxs-lookup"><span data-stu-id="0b3ae-126">Remarks</span></span>  

 <span data-ttu-id="0b3ae-127">ホストがの実装を提供していない場合 `GetAvailableThreads` 、E_NOTIMPL の HRESULT 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-127">If the host does not provide an implementation of `GetAvailableThreads`, it should return an HRESULT value of E_NOTIMPL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b3ae-128">要件</span><span class="sxs-lookup"><span data-stu-id="0b3ae-128">Requirements</span></span>  

 <span data-ttu-id="0b3ae-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b3ae-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b3ae-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0b3ae-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b3ae-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0b3ae-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b3ae-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b3ae-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b3ae-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b3ae-133">See also</span></span>

- <xref:System.Threading.ThreadPool.GetAvailableThreads%2A>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="0b3ae-134">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b3ae-134">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
