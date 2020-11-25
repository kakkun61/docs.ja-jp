---
title: IHostSyncManager::SetCLRSyncManager メソッド
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: 79a41b6705b41414f0926c2ed819e437ecfb51d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714836"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="eefda-102">IHostSyncManager::SetCLRSyncManager メソッド</span><span class="sxs-lookup"><span data-stu-id="eefda-102">IHostSyncManager::SetCLRSyncManager Method</span></span>

<span data-ttu-id="eefda-103">現在の[IHostSyncManager](ihostsyncmanager-interface.md)インスタンスに関連付ける[ICLRSyncManager](iclrsyncmanager-interface.md)インスタンスを設定します。</span><span class="sxs-lookup"><span data-stu-id="eefda-103">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eefda-104">構文</span><span class="sxs-lookup"><span data-stu-id="eefda-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eefda-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eefda-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="eefda-106">から `ICLRSyncManager` 共通言語ランタイム (CLR) によって提供されるインスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="eefda-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eefda-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="eefda-107">Return Value</span></span>  
  
|<span data-ttu-id="eefda-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="eefda-108">HRESULT</span></span>|<span data-ttu-id="eefda-109">説明</span><span class="sxs-lookup"><span data-stu-id="eefda-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="eefda-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="eefda-110">S_OK</span></span>|<span data-ttu-id="eefda-111">`SetCLRSyncManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="eefda-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="eefda-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="eefda-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="eefda-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="eefda-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="eefda-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="eefda-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="eefda-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="eefda-115">The call timed out.</span></span>|  
|<span data-ttu-id="eefda-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="eefda-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="eefda-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="eefda-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="eefda-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="eefda-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="eefda-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="eefda-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="eefda-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="eefda-120">E_FAIL</span></span>|<span data-ttu-id="eefda-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="eefda-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="eefda-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="eefda-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="eefda-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="eefda-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eefda-124">注釈</span><span class="sxs-lookup"><span data-stu-id="eefda-124">Remarks</span></span>  

 <span data-ttu-id="eefda-125">ホストと CLR の間の通信を容易にするために、ホストインターフェイスは通常、ペアになっています。</span><span class="sxs-lookup"><span data-stu-id="eefda-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="eefda-126">ペアの1つのメンバーはホストによって実装され、もう一方のメンバーは CLR によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="eefda-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="eefda-127">ホスト側の実装として、 `IHostSyncManager` インターフェイスは、 `ICLRSyncManager` CLR によって実装されるインターフェイスに対応します。</span><span class="sxs-lookup"><span data-stu-id="eefda-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="eefda-128">CLR は、を呼び出して、 `SetCLRSyncManager` `ICLRSyncManager` 現在のインスタンスに関連付けられているホストのインスタンスを指定 `IHostSyncManager` します。</span><span class="sxs-lookup"><span data-stu-id="eefda-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eefda-129">要件</span><span class="sxs-lookup"><span data-stu-id="eefda-129">Requirements</span></span>  

 <span data-ttu-id="eefda-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eefda-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eefda-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="eefda-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eefda-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="eefda-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eefda-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eefda-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eefda-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="eefda-134">See also</span></span>

- [<span data-ttu-id="eefda-135">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eefda-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="eefda-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eefda-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
