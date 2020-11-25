---
title: IHostTaskManager::Sleep メソッド
ms.date: 03/30/2017
api_name:
- IHostTaskManager.Sleep
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::Sleep
helpviewer_keywords:
- IHostTaskManager::Sleep method [.NET Framework hosting]
- Sleep method, IHostTaskManager interface [.NET Framework hosting]
ms.assetid: f67d25f3-9199-4c5f-b1e8-1c819243cfd5
topic_type:
- apiref
ms.openlocfilehash: 372b15a565f8a7484c1c42c387098a38f7bbf428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702057"
---
# <a name="ihosttaskmanagersleep-method"></a><span data-ttu-id="f8bc6-102">IHostTaskManager::Sleep メソッド</span><span class="sxs-lookup"><span data-stu-id="f8bc6-102">IHostTaskManager::Sleep Method</span></span>

<span data-ttu-id="f8bc6-103">現在のタスクがスリープ状態になることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-103">Notifies the host that the current task is going to sleep.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bc6-104">構文</span><span class="sxs-lookup"><span data-stu-id="f8bc6-104">Syntax</span></span>  
  
```cpp  
HRESULT Sleep (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8bc6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f8bc6-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="f8bc6-106">からスレッドがスリープする時間間隔 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-106">[in] The time interval, in milliseconds, that the thread will sleep.</span></span>  
  
 `option`  
 <span data-ttu-id="f8bc6-107">から [WAIT_OPTION](wait-option-enumeration.md) 列挙値の1つ。このアクションがブロックされた場合にホストが実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) enumeration values, indicating what action the host should take if this action blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8bc6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f8bc6-108">Return Value</span></span>  
  
|<span data-ttu-id="f8bc6-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8bc6-109">HRESULT</span></span>|<span data-ttu-id="f8bc6-110">説明</span><span class="sxs-lookup"><span data-stu-id="f8bc6-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8bc6-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8bc6-111">S_OK</span></span>|<span data-ttu-id="f8bc6-112">`Sleep` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-112">`Sleep` returned successfully.</span></span>|  
|<span data-ttu-id="f8bc6-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8bc6-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8bc6-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8bc6-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8bc6-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8bc6-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-116">The call timed out.</span></span>|  
|<span data-ttu-id="f8bc6-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8bc6-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8bc6-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8bc6-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8bc6-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8bc6-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8bc6-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8bc6-121">E_FAIL</span></span>|<span data-ttu-id="f8bc6-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8bc6-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8bc6-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8bc6-125">注釈</span><span class="sxs-lookup"><span data-stu-id="f8bc6-125">Remarks</span></span>  

 <span data-ttu-id="f8bc6-126">CLR は、通常 `IHostTaskManager::Sleep` 、 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> がユーザーコードから呼び出されたときにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-126">The CLR typically calls `IHostTaskManager::Sleep` when <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is called from user code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8bc6-127">要件</span><span class="sxs-lookup"><span data-stu-id="f8bc6-127">Requirements</span></span>  

 <span data-ttu-id="f8bc6-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8bc6-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8bc6-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="f8bc6-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8bc6-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f8bc6-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8bc6-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8bc6-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bc6-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8bc6-132">See also</span></span>

- [<span data-ttu-id="f8bc6-133">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8bc6-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="f8bc6-134">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8bc6-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="f8bc6-135">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8bc6-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="f8bc6-136">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f8bc6-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
