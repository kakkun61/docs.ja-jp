---
title: ICLRGCManager::Collect メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::Collect
helpviewer_keywords:
- ICLRGCManager::Collect method [.NET Framework hosting]
- Collect method, ICLRGCManager interface [.NET Framework hosting]
ms.assetid: 0c6cbbea-c27c-4695-bda3-17c1910d8ddb
topic_type:
- apiref
ms.openlocfilehash: 90ce4e888ddb3a10dd0dfd7e68463311db86742f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677766"
---
# <a name="iclrgcmanagercollect-method"></a><span data-ttu-id="662ca-102">ICLRGCManager::Collect メソッド</span><span class="sxs-lookup"><span data-stu-id="662ca-102">ICLRGCManager::Collect Method</span></span>

<span data-ttu-id="662ca-103">指定したジェネレーションのガベージコレクションを強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="662ca-103">Forces a garbage collection for the specified generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="662ca-104">構文</span><span class="sxs-lookup"><span data-stu-id="662ca-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="662ca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="662ca-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="662ca-106">から収集するジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="662ca-106">[in] The generation to collect.</span></span> <span data-ttu-id="662ca-107">値が-1 の場合は、すべてのジェネレーションのコレクションが強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="662ca-107">A value of -1 forces a collection of all generations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="662ca-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="662ca-108">Return Value</span></span>  
  
|<span data-ttu-id="662ca-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="662ca-109">HRESULT</span></span>|<span data-ttu-id="662ca-110">説明</span><span class="sxs-lookup"><span data-stu-id="662ca-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="662ca-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="662ca-111">S_OK</span></span>|<span data-ttu-id="662ca-112">`Collect` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="662ca-112">`Collect` returned successfully.</span></span>|  
|<span data-ttu-id="662ca-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="662ca-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="662ca-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="662ca-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="662ca-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="662ca-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="662ca-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="662ca-116">The call timed out.</span></span>|  
|<span data-ttu-id="662ca-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="662ca-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="662ca-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="662ca-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="662ca-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="662ca-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="662ca-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="662ca-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="662ca-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="662ca-121">E_FAIL</span></span>|<span data-ttu-id="662ca-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="662ca-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="662ca-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="662ca-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="662ca-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="662ca-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="662ca-125">注釈</span><span class="sxs-lookup"><span data-stu-id="662ca-125">Remarks</span></span>  

 <span data-ttu-id="662ca-126">メソッドは、 `Collect` 現在の状態に関係なく、CLR のガベージコレクターがコレクションを実行するように強制します。</span><span class="sxs-lookup"><span data-stu-id="662ca-126">The `Collect` method forces the CLR's garbage collector to perform a collection regardless of its current state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="662ca-127">要件</span><span class="sxs-lookup"><span data-stu-id="662ca-127">Requirements</span></span>  

 <span data-ttu-id="662ca-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="662ca-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="662ca-129">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="662ca-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="662ca-130">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="662ca-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="662ca-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="662ca-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="662ca-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="662ca-132">See also</span></span>

- [<span data-ttu-id="662ca-133">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="662ca-133">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="662ca-134">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="662ca-134">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="662ca-135">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="662ca-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="662ca-136">ICLRGCManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="662ca-136">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="662ca-137">CLR ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="662ca-137">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="662ca-138">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="662ca-138">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="662ca-139">ホスティング</span><span class="sxs-lookup"><span data-stu-id="662ca-139">Hosting</span></span>](index.md)
