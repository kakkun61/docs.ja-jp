---
title: IHostIoCompletionManager::SetCLRIoCompletionManager メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
ms.openlocfilehash: d370cc81942269bd79e06e0fa57fe5d79832b3c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724846"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="3a083-102">IHostIoCompletionManager::SetCLRIoCompletionManager メソッド</span><span class="sxs-lookup"><span data-stu-id="3a083-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>

<span data-ttu-id="3a083-103">共通言語ランタイム (CLR) によって実装された [Iclrioの](iclriocompletionmanager-interface.md) インスタンスへのインターフェイスポインターをホストに提供します。</span><span class="sxs-lookup"><span data-stu-id="3a083-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a083-104">構文</span><span class="sxs-lookup"><span data-stu-id="3a083-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a083-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3a083-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="3a083-106">から `ICLRIoCompletionManager` CLR によって提供されるインスタンスへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="3a083-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a083-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3a083-107">Return Value</span></span>  
  
|<span data-ttu-id="3a083-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3a083-108">HRESULT</span></span>|<span data-ttu-id="3a083-109">説明</span><span class="sxs-lookup"><span data-stu-id="3a083-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a083-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3a083-110">S_OK</span></span>|<span data-ttu-id="3a083-111">`SetCLRIoCompletionManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3a083-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="3a083-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3a083-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3a083-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3a083-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3a083-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3a083-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3a083-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3a083-115">The call timed out.</span></span>|  
|<span data-ttu-id="3a083-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3a083-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3a083-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3a083-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3a083-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3a083-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3a083-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3a083-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3a083-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3a083-120">E_FAIL</span></span>|<span data-ttu-id="3a083-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3a083-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3a083-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3a083-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3a083-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3a083-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a083-124">注釈</span><span class="sxs-lookup"><span data-stu-id="3a083-124">Remarks</span></span>  

 <span data-ttu-id="3a083-125">CLR が呼び出された後 `SetCLRIoCompletionManager` 、ホストは [Iclriocompleted manager:: oncomplete](iclriocompletionmanager-oncomplete-method.md) を呼び出して、i/o 要求が完了したことを clr に通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a083-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a083-126">要件</span><span class="sxs-lookup"><span data-stu-id="3a083-126">Requirements</span></span>  

 <span data-ttu-id="3a083-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a083-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a083-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3a083-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a083-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3a083-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a083-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a083-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a083-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a083-131">See also</span></span>

- [<span data-ttu-id="3a083-132">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a083-132">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="3a083-133">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a083-133">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
