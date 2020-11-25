---
title: IHostMemoryManager::RegisterMemoryNotificationCallback メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: edb29378412583d7cdec804b08f8f622d642b02f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731307"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="81106-102">IHostMemoryManager::RegisterMemoryNotificationCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="81106-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>

<span data-ttu-id="81106-103">コンピューターの現在のメモリ負荷を共通言語ランタイム (CLR) に通知するために、ホストが呼び出すコールバック関数へのポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="81106-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81106-104">構文</span><span class="sxs-lookup"><span data-stu-id="81106-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81106-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="81106-105">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="81106-106">からCLR によって実装される [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) インスタンスへのインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="81106-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81106-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="81106-107">Return Value</span></span>  
  
|<span data-ttu-id="81106-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="81106-108">HRESULT</span></span>|<span data-ttu-id="81106-109">説明</span><span class="sxs-lookup"><span data-stu-id="81106-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="81106-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="81106-110">S_OK</span></span>|<span data-ttu-id="81106-111">`RegisterMemoryNotificationCallback` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="81106-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="81106-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="81106-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="81106-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="81106-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="81106-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="81106-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="81106-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="81106-115">The call timed out.</span></span>|  
|<span data-ttu-id="81106-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="81106-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="81106-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="81106-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="81106-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="81106-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="81106-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="81106-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="81106-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="81106-120">E_FAIL</span></span>|<span data-ttu-id="81106-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="81106-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="81106-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="81106-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="81106-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="81106-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81106-124">注釈</span><span class="sxs-lookup"><span data-stu-id="81106-124">Remarks</span></span>  

 <span data-ttu-id="81106-125">インターフェイスで `ICLRMemoryNotificationCallback` 定義されるメソッドは1つだけであるため ([ICLRMemoryNotificationCallback:: OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md))、 `pCallback` は `ICLRMemoryNotificationCallback` CLR によって提供されるインスタンスへのポインターであるため、コールバック関数自体に対して実際に登録が行われます。</span><span class="sxs-lookup"><span data-stu-id="81106-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="81106-126">ホストは、 `OnMemoryNotification` 標準の Win32 関数を使用するのではなく、メモリ不足状態を報告するためにを呼び出し `CreateMemoryResourceNotification` ます。</span><span class="sxs-lookup"><span data-stu-id="81106-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="81106-127">詳細については、Windows プラットフォームのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="81106-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81106-128">を呼び出しても `OnMemoryNotification` ブロックされません。</span><span class="sxs-lookup"><span data-stu-id="81106-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="81106-129">常に直ちに返されます。</span><span class="sxs-lookup"><span data-stu-id="81106-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81106-130">要件</span><span class="sxs-lookup"><span data-stu-id="81106-130">Requirements</span></span>  

 <span data-ttu-id="81106-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81106-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81106-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="81106-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81106-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="81106-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81106-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81106-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81106-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="81106-135">See also</span></span>

- [<span data-ttu-id="81106-136">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81106-136">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="81106-137">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="81106-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
