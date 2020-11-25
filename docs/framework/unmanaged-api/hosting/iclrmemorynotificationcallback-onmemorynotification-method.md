---
title: ICLRMemoryNotificationCallback::OnMemoryNotification メソッド
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: f9b2715801ebcaff3d97962540a4b1b103bbd53b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730475"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="27303-102">ICLRMemoryNotificationCallback::OnMemoryNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="27303-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>

<span data-ttu-id="27303-103">コンピューターのメモリ負荷の共通言語ランタイム (CLR) に通知します。</span><span class="sxs-lookup"><span data-stu-id="27303-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27303-104">構文</span><span class="sxs-lookup"><span data-stu-id="27303-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27303-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="27303-105">Parameters</span></span>  

 `eMemoryAvailable`  
 <span data-ttu-id="27303-106">から [EMemoryAvailable](ememoryavailable-enumeration.md) 値の1つ。コンピューターが現在発生しているメモリ不足を示します。</span><span class="sxs-lookup"><span data-stu-id="27303-106">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27303-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="27303-107">Return Value</span></span>  
  
|<span data-ttu-id="27303-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27303-108">HRESULT</span></span>|<span data-ttu-id="27303-109">説明</span><span class="sxs-lookup"><span data-stu-id="27303-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27303-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="27303-110">S_OK</span></span>|<span data-ttu-id="27303-111">`OnMemoryNotification` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="27303-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="27303-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="27303-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="27303-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="27303-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="27303-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="27303-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="27303-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="27303-115">The call timed out.</span></span>|  
|<span data-ttu-id="27303-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="27303-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="27303-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="27303-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="27303-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="27303-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="27303-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="27303-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="27303-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27303-120">E_FAIL</span></span>|<span data-ttu-id="27303-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="27303-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="27303-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="27303-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="27303-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="27303-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27303-124">注釈</span><span class="sxs-lookup"><span data-stu-id="27303-124">Remarks</span></span>  

 <span data-ttu-id="27303-125">CLR は、 `OnMemoryNotification` [IHostMemoryManager:: RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) メソッドの呼び出しを使用して、コールバックをに登録します。</span><span class="sxs-lookup"><span data-stu-id="27303-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="27303-126">ランタイムは、コールバックで返された情報を使用して、メモリリソースが不足していることをホストが報告したときに追加のメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="27303-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27303-127">を呼び出しても `OnMemoryNotification` ブロックされません。</span><span class="sxs-lookup"><span data-stu-id="27303-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="27303-128">常に直ちに返されます。</span><span class="sxs-lookup"><span data-stu-id="27303-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27303-129">要件</span><span class="sxs-lookup"><span data-stu-id="27303-129">Requirements</span></span>  

 <span data-ttu-id="27303-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27303-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27303-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="27303-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27303-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="27303-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27303-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27303-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27303-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="27303-134">See also</span></span>

- [<span data-ttu-id="27303-135">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27303-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="27303-136">RegisterMemoryNotificationCallback メソッド</span><span class="sxs-lookup"><span data-stu-id="27303-136">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="27303-137">ICLRMemoryNotificationCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="27303-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
