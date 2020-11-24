---
title: IHostTaskManager::ReverseEnterRuntime メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.ReverseEnterRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::ReverseEnterRuntime
helpviewer_keywords:
- IHostTaskManager::ReverseEnterRuntime method [.NET Framework hosting]
- ReverseEnterRuntime method [.NET Framework hosting]
ms.assetid: b1e26bff-d3ea-436e-9867-29720df999f4
topic_type:
- apiref
ms.openlocfilehash: 163bf3327219f1198c5ed078308096ac3d0325be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672956"
---
# <a name="ihosttaskmanagerreverseenterruntime-method"></a><span data-ttu-id="9a81c-102">IHostTaskManager::ReverseEnterRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="9a81c-102">IHostTaskManager::ReverseEnterRuntime Method</span></span>

<span data-ttu-id="9a81c-103">アンマネージコードから共通言語ランタイム (CLR) への呼び出しが行われていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="9a81c-103">Notifies the host that a call is being made into the common language runtime (CLR) from unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a81c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9a81c-104">Syntax</span></span>  
  
```cpp  
HRESULT ReverseEnterRuntime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9a81c-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="9a81c-105">Return Value</span></span>  
  
|<span data-ttu-id="9a81c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a81c-106">HRESULT</span></span>|<span data-ttu-id="9a81c-107">説明</span><span class="sxs-lookup"><span data-stu-id="9a81c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a81c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a81c-108">S_OK</span></span>|<span data-ttu-id="9a81c-109">`ReverseEnterRuntime` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9a81c-109">`ReverseEnterRuntime` returned successfully.</span></span>|  
|<span data-ttu-id="9a81c-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a81c-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a81c-111">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9a81c-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9a81c-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9a81c-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9a81c-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9a81c-113">The call timed out.</span></span>|  
|<span data-ttu-id="9a81c-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9a81c-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9a81c-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9a81c-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9a81c-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9a81c-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9a81c-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9a81c-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9a81c-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a81c-118">E_FAIL</span></span>|<span data-ttu-id="9a81c-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9a81c-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9a81c-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9a81c-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9a81c-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9a81c-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a81c-122">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9a81c-122">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9a81c-123">要求されたリソース割り当てを完了するために必要なメモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="9a81c-123">Not enough memory is available to complete the requested resource allocation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a81c-124">注釈</span><span class="sxs-lookup"><span data-stu-id="9a81c-124">Remarks</span></span>  

 <span data-ttu-id="9a81c-125">マネージコードで開始されたシーケンスから CLR への呼び出しが行われる場合、への各呼び出しは、 `ReverseEnterRuntime` [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)の呼び出しに対応します。</span><span class="sxs-lookup"><span data-stu-id="9a81c-125">If the call into the CLR is made from a sequence that originated in managed code, each call to `ReverseEnterRuntime` corresponds to a call to [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a81c-126">呼び出しは、入れ子になっていなくてもアンマネージコードから発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9a81c-126">Calls can originate from unmanaged code without being nested.</span></span> <span data-ttu-id="9a81c-127">この場合、 [Enterruntime](ihosttaskmanager-enterruntime-method.md)、all [veruntime](ihosttaskmanager-leaveruntime-method.md)、またはが呼び出され `ReverseLeaveRuntime` ておらず、への呼び出しの回数がの `ReverseEnterRuntime` 呼び出しの数と等しくありません `ReverseLeaveRuntime` 。</span><span class="sxs-lookup"><span data-stu-id="9a81c-127">In this case, there is no call to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), or `ReverseLeaveRuntime`, and the number of calls to `ReverseEnterRuntime` does not equal the number of calls to `ReverseLeaveRuntime`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a81c-128">要件</span><span class="sxs-lookup"><span data-stu-id="9a81c-128">Requirements</span></span>  

 <span data-ttu-id="9a81c-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a81c-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a81c-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9a81c-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a81c-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9a81c-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a81c-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a81c-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a81c-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a81c-133">See also</span></span>

- [<span data-ttu-id="9a81c-134">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a81c-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9a81c-135">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a81c-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9a81c-136">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a81c-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9a81c-137">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a81c-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
