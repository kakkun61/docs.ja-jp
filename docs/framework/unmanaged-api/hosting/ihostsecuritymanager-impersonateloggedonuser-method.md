---
title: IHostSecurityManager::ImpersonateLoggedOnUser メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.ImpersonateLoggedOnUser
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::ImpersonateLoggedOnUser
helpviewer_keywords:
- ImpersonateLoggedOnUser method [.NET Framework hosting]
- IHostSecurityManager::ImpersonateLoggedOnUser method [.NET Framework hosting]
ms.assetid: acc49ba0-f1d9-45ad-871f-9d053a89dcbe
topic_type:
- apiref
ms.openlocfilehash: dd1d1af8072ac11e37bd2eb1a47d76b12685cb31
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724781"
---
# <a name="ihostsecuritymanagerimpersonateloggedonuser-method"></a><span data-ttu-id="16260-102">IHostSecurityManager::ImpersonateLoggedOnUser メソッド</span><span class="sxs-lookup"><span data-stu-id="16260-102">IHostSecurityManager::ImpersonateLoggedOnUser Method</span></span>

<span data-ttu-id="16260-103">現在のユーザー id の資格情報を使用して、コードの実行を要求します。</span><span class="sxs-lookup"><span data-stu-id="16260-103">Requests that code be executed using the credentials of the current user identity.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16260-104">構文</span><span class="sxs-lookup"><span data-stu-id="16260-104">Syntax</span></span>  
  
```cpp  
HRESULT ImpersonateLoggedOnUser (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16260-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="16260-105">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="16260-106">から権限を借用するユーザーの資格情報を表すトークン。</span><span class="sxs-lookup"><span data-stu-id="16260-106">[in] A token representing the credentials of the user to be impersonated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16260-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="16260-107">Return Value</span></span>  
  
|<span data-ttu-id="16260-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="16260-108">HRESULT</span></span>|<span data-ttu-id="16260-109">説明</span><span class="sxs-lookup"><span data-stu-id="16260-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16260-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="16260-110">S_OK</span></span>|<span data-ttu-id="16260-111">`ImpersonateLoggedOnUser` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="16260-111">`ImpersonateLoggedOnUser` returned successfully.</span></span>|  
|<span data-ttu-id="16260-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="16260-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="16260-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="16260-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="16260-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="16260-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="16260-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="16260-115">The call timed out.</span></span>|  
|<span data-ttu-id="16260-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="16260-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="16260-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="16260-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="16260-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="16260-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="16260-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="16260-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="16260-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="16260-120">E_FAIL</span></span>|<span data-ttu-id="16260-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="16260-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="16260-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="16260-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="16260-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="16260-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16260-124">注釈</span><span class="sxs-lookup"><span data-stu-id="16260-124">Remarks</span></span>  

 <span data-ttu-id="16260-125">を呼び出す `LogonUser` か、または関連する Win32 関数を呼び出して、現在のユーザー id の資格情報を識別するハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="16260-125">Call `LogonUser` or a related Win32 function to get a handle to the credentials of the current user identity.</span></span>  
  
 <span data-ttu-id="16260-126">`HANDLE`この型は COM に準拠していません。つまり、そのサイズはオペレーティングシステムに固有であり、カスタムマーシャリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="16260-126">The `HANDLE` type is not COM-compliant, that is, its size is specific to an operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="16260-127">したがって、このトークンは、CLR とホストの間でプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="16260-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16260-128">要件</span><span class="sxs-lookup"><span data-stu-id="16260-128">Requirements</span></span>  

 <span data-ttu-id="16260-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="16260-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16260-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="16260-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16260-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="16260-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16260-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16260-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16260-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="16260-133">See also</span></span>

- [<span data-ttu-id="16260-134">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16260-134">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="16260-135">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="16260-135">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="16260-136">RevertToSelf メソッド</span><span class="sxs-lookup"><span data-stu-id="16260-136">RevertToSelf Method</span></span>](ihostsecuritymanager-reverttoself-method.md)
