---
title: ICLRSyncManager::DeleteRWLockOwnerIterator メソッド
ms.date: 03/30/2017
api_name:
- ICLRSyncManager.DeleteRWLockOwnerIterator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator
helpviewer_keywords:
- ICLRSyncManager::DeleteRWLockOwnerIterator method [.NET Framework hosting]
- DeleteRWLockOwnerIterator method [.NET Framework hosting]
ms.assetid: fcfd340a-b7d6-44e4-8167-2c05b789d483
topic_type:
- apiref
ms.openlocfilehash: db651e3fe51f90b84449874f2c60a12050b0350e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687113"
---
# <a name="iclrsyncmanagerdeleterwlockowneriterator-method"></a><span data-ttu-id="93c7d-102">ICLRSyncManager::DeleteRWLockOwnerIterator メソッド</span><span class="sxs-lookup"><span data-stu-id="93c7d-102">ICLRSyncManager::DeleteRWLockOwnerIterator Method</span></span>

<span data-ttu-id="93c7d-103">[ICLRSyncManager:: CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md)の呼び出しによって作成された反復子を、共通言語ランタイム (CLR) が破棄することを要求します。</span><span class="sxs-lookup"><span data-stu-id="93c7d-103">Requests that the common language runtime (CLR) destroy an iterator that was created by a call to [ICLRSyncManager::CreateRWLockOwnerIterator](iclrsyncmanager-createrwlockowneriterator-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93c7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="93c7d-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteRWLockOwnerIterator (  
    [in] SIZE_T  Iterator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93c7d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="93c7d-105">Parameters</span></span>  

 `Iterator`  
 <span data-ttu-id="93c7d-106">からの呼び出しを使用して作成された反復子 `CreateRWLockOwnerIterator` 。</span><span class="sxs-lookup"><span data-stu-id="93c7d-106">[in] The iterator that was created by using a call to `CreateRWLockOwnerIterator`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93c7d-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="93c7d-107">Return Value</span></span>  
  
|<span data-ttu-id="93c7d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93c7d-108">HRESULT</span></span>|<span data-ttu-id="93c7d-109">説明</span><span class="sxs-lookup"><span data-stu-id="93c7d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93c7d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="93c7d-110">S_OK</span></span>|<span data-ttu-id="93c7d-111">`DeleteRWLockOwnerIterator` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="93c7d-111">`DeleteRWLockOwnerIterator` returned successfully.</span></span>|  
|<span data-ttu-id="93c7d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93c7d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93c7d-113">CLR がプロセスに読み込まれていないか、マネージコードを実行できないか、または呼び出しを正常に処理できない状態になっています。</span><span class="sxs-lookup"><span data-stu-id="93c7d-113">The CLR has not been loaded into a process, or is in a state in which it cannot run managed code or successfully process the call.</span></span>|  
|<span data-ttu-id="93c7d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="93c7d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="93c7d-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="93c7d-115">The call timed out.</span></span>|  
|<span data-ttu-id="93c7d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="93c7d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="93c7d-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="93c7d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="93c7d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="93c7d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="93c7d-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="93c7d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="93c7d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93c7d-120">E_FAIL</span></span>|<span data-ttu-id="93c7d-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="93c7d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="93c7d-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="93c7d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="93c7d-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="93c7d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93c7d-124">注釈</span><span class="sxs-lookup"><span data-stu-id="93c7d-124">Remarks</span></span>  

 <span data-ttu-id="93c7d-125">ホストは、このメソッドを呼び出して、 `CreateRWLockOwnerIterator` スレッドの実装が同期された状態を維持することができます。</span><span class="sxs-lookup"><span data-stu-id="93c7d-125">The host can call this method and `CreateRWLockOwnerIterator` to ensure that its threading implementation remains synchronized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93c7d-126">要件</span><span class="sxs-lookup"><span data-stu-id="93c7d-126">Requirements</span></span>  

 <span data-ttu-id="93c7d-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93c7d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93c7d-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="93c7d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93c7d-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="93c7d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93c7d-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93c7d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93c7d-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="93c7d-131">See also</span></span>

- [<span data-ttu-id="93c7d-132">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93c7d-132">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="93c7d-133">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="93c7d-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
