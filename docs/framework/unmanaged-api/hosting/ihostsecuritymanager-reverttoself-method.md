---
title: IHostSecurityManager::RevertToSelf メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.RevertToSelf
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::RevertToSelf
helpviewer_keywords:
- RevertToSelf method [.NET Framework hosting]
- IHostSecurityManager::RevertToSelf method [.NET Framework hosting]
ms.assetid: 189f28f8-f9a1-4192-aedc-91084e4f8b99
topic_type:
- apiref
ms.openlocfilehash: a54c25cb0cae906dc2d030900b9a1e1dbbbb2f1e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680522"
---
# <a name="ihostsecuritymanagerreverttoself-method"></a><span data-ttu-id="e9679-102">IHostSecurityManager::RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="e9679-102">IHostSecurityManager::RevertToSelf Method</span></span>

<span data-ttu-id="e9679-103">現在のユーザー id の偽装を終了し、元のスレッドトークンを返します。</span><span class="sxs-lookup"><span data-stu-id="e9679-103">Terminates impersonation of the current user identity and returns the original thread token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9679-104">構文</span><span class="sxs-lookup"><span data-stu-id="e9679-104">Syntax</span></span>  
  
```cpp  
HRESULT RevertToSelf ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9679-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="e9679-105">Return Value</span></span>  
  
|<span data-ttu-id="e9679-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9679-106">HRESULT</span></span>|<span data-ttu-id="e9679-107">説明</span><span class="sxs-lookup"><span data-stu-id="e9679-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9679-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9679-108">S_OK</span></span>|<span data-ttu-id="e9679-109">`RevertToSelf` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="e9679-109">`RevertToSelf` returned successfully.</span></span>|  
|<span data-ttu-id="e9679-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9679-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9679-111">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="e9679-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9679-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9679-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9679-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e9679-113">The call timed out.</span></span>|  
|<span data-ttu-id="e9679-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9679-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9679-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e9679-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9679-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9679-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9679-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="e9679-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9679-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9679-118">E_FAIL</span></span>|<span data-ttu-id="e9679-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e9679-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9679-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e9679-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9679-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="e9679-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9679-122">注釈</span><span class="sxs-lookup"><span data-stu-id="e9679-122">Remarks</span></span>  

 <span data-ttu-id="e9679-123">`RevertToSelf` は、 [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) メソッドを以前に呼び出した後、元のスレッドトークンに戻るために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e9679-123">`RevertToSelf` is called to return to the original thread token, after an earlier call to the [ImpersonateLoggedOnUser](ihostsecuritymanager-impersonateloggedonuser-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9679-124">要件</span><span class="sxs-lookup"><span data-stu-id="e9679-124">Requirements</span></span>  

 <span data-ttu-id="e9679-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9679-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9679-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e9679-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9679-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e9679-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9679-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9679-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9679-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9679-129">See also</span></span>

- [<span data-ttu-id="e9679-130">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9679-130">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="e9679-131">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9679-131">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="e9679-132">ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="e9679-132">ImpersonateLoggedOnUser Method</span></span>](ihostsecuritymanager-impersonateloggedonuser-method.md)
