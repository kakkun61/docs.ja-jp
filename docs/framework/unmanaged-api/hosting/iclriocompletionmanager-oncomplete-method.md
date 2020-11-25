---
title: ICLRIoCompletionManager::OnComplete メソッド
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: 15119974acf74b49669e5ffbee59fbff9e5c84c9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714108"
---
# <a name="iclriocompletionmanageroncomplete-method"></a><span data-ttu-id="cc974-102">ICLRIoCompletionManager::OnComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="cc974-102">ICLRIoCompletionManager::OnComplete Method</span></span>

<span data-ttu-id="cc974-103">[Ihohooの](ihostiocompletionmanager-bind-method.md)呼び出しを使用して作成された i/o 要求の状態を共通言語ランタイム (CLR) に通知します:: Bind メソッド。</span><span class="sxs-lookup"><span data-stu-id="cc974-103">Notifies the common language runtime (CLR) of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc974-104">構文</span><span class="sxs-lookup"><span data-stu-id="cc974-104">Syntax</span></span>  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc974-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cc974-105">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="cc974-106">からバインド操作の状態を示す HRESULT 値です。</span><span class="sxs-lookup"><span data-stu-id="cc974-106">[in] An HRESULT value that indicates the status of the bind operation.</span></span>  
  
- <span data-ttu-id="cc974-107">S_OK は、操作が正常に完了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cc974-107">S_OK indicates that the operation completed successfully.</span></span>  
  
- <span data-ttu-id="cc974-108">HOST_E_INTERRUPTED は、呼び出しが完了前に終了したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cc974-108">HOST_E_INTERRUPTED indicates that the call terminated before completion.</span></span>  
  
- <span data-ttu-id="cc974-109">E_FAIL は、不明で回復不可能な重大なエラーが発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="cc974-109">E_FAIL indicates that an unknown, unrecoverable, catastrophic failure occurred.</span></span>  
  
 `NumberOfBytesTransferred`  
 <span data-ttu-id="cc974-110">からI/o 要求の処理中に転送されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="cc974-110">[in] The number of bytes transferred during the processing of the I/O request.</span></span>  
  
 `pvOverlapped`  
 <span data-ttu-id="cc974-111">から `OVERLAPPED` メソッドの呼び出しに渡された構造体へのポインター `IHostIoCompletionManager::Bind` 。</span><span class="sxs-lookup"><span data-stu-id="cc974-111">[in] A pointer to the `OVERLAPPED` structure that was passed to the call to the `IHostIoCompletionManager::Bind` method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc974-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="cc974-112">Return Value</span></span>  
  
|<span data-ttu-id="cc974-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc974-113">HRESULT</span></span>|<span data-ttu-id="cc974-114">説明</span><span class="sxs-lookup"><span data-stu-id="cc974-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc974-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc974-115">S_OK</span></span>|<span data-ttu-id="cc974-116">`OnComplete` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="cc974-116">`OnComplete` returned successfully.</span></span>|  
|<span data-ttu-id="cc974-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc974-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc974-118">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="cc974-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cc974-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cc974-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cc974-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="cc974-120">The call timed out.</span></span>|  
|<span data-ttu-id="cc974-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cc974-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cc974-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="cc974-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cc974-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cc974-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cc974-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="cc974-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cc974-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc974-125">E_FAIL</span></span>|<span data-ttu-id="cc974-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cc974-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cc974-127">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cc974-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cc974-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc974-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc974-129">注釈</span><span class="sxs-lookup"><span data-stu-id="cc974-129">Remarks</span></span>  

 <span data-ttu-id="cc974-130">ホストで i/o 完了の抽象化が実装されている場合、CLR は [Iho/ocompletion manager](ihostiocompletionmanager-interface.md)のメソッドを使用して、ホストを介して i/o 要求を行います。</span><span class="sxs-lookup"><span data-stu-id="cc974-130">If the host implements an I/O completion abstraction, the CLR makes I/O requests through the host by using methods of [IHostIoCompletionManager](ihostiocompletionmanager-interface.md).</span></span> <span data-ttu-id="cc974-131">次に、ホストはメソッドを呼び出して、その `OnComplete` ような要求の結果をランタイムに通知します。</span><span class="sxs-lookup"><span data-stu-id="cc974-131">The host then calls the `OnComplete` method to notify the runtime of the outcome of such requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc974-132">要件</span><span class="sxs-lookup"><span data-stu-id="cc974-132">Requirements</span></span>  

 <span data-ttu-id="cc974-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc974-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc974-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cc974-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc974-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="cc974-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc974-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc974-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc974-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc974-137">See also</span></span>

- [<span data-ttu-id="cc974-138">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc974-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="cc974-139">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc974-139">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="cc974-140">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cc974-140">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
