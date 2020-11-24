---
title: IHostManualEvent::Set メソッド
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: bc2b178c6c26a6de62982c35d5aeb9ea5359c2bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679131"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="6b2a7-102">IHostManualEvent::Set メソッド</span><span class="sxs-lookup"><span data-stu-id="6b2a7-102">IHostManualEvent::Set Method</span></span>

<span data-ttu-id="6b2a7-103">現在の [IHostManualEvent](ihostmanualevent-interface.md) インスタンスをシグナル状態に設定します。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-103">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b2a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b2a7-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6b2a7-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="6b2a7-105">Return Value</span></span>  
  
|<span data-ttu-id="6b2a7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b2a7-106">HRESULT</span></span>|<span data-ttu-id="6b2a7-107">説明</span><span class="sxs-lookup"><span data-stu-id="6b2a7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b2a7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b2a7-108">S_OK</span></span>|<span data-ttu-id="6b2a7-109">`Set` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="6b2a7-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b2a7-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b2a7-111">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6b2a7-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6b2a7-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6b2a7-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-113">The call timed out.</span></span>|  
|<span data-ttu-id="6b2a7-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6b2a7-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6b2a7-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6b2a7-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6b2a7-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6b2a7-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6b2a7-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b2a7-118">E_FAIL</span></span>|<span data-ttu-id="6b2a7-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6b2a7-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6b2a7-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b2a7-122">要件</span><span class="sxs-lookup"><span data-stu-id="6b2a7-122">Requirements</span></span>  

 <span data-ttu-id="6b2a7-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b2a7-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b2a7-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6b2a7-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b2a7-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6b2a7-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b2a7-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b2a7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2a7-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b2a7-127">See also</span></span>

- [<span data-ttu-id="6b2a7-128">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b2a7-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6b2a7-129">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b2a7-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="6b2a7-130">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b2a7-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="6b2a7-131">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b2a7-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="6b2a7-132">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6b2a7-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
