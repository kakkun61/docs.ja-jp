---
title: IHostSecurityManager::SetThreadToken メソッド
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.SetThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::SetThreadToken
helpviewer_keywords:
- SetThreadToken method [.NET Framework hosting]
- IHostSecurityManager::SetThreadToken method [.NET Framework hosting]
ms.assetid: e951c345-8a86-4587-911b-a1a57bc6428a
topic_type:
- apiref
ms.openlocfilehash: 5a2b2e5560c292598f0110de9445eb66ba794997
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683109"
---
# <a name="ihostsecuritymanagersetthreadtoken-method"></a><span data-ttu-id="8c037-102">IHostSecurityManager::SetThreadToken メソッド</span><span class="sxs-lookup"><span data-stu-id="8c037-102">IHostSecurityManager::SetThreadToken Method</span></span>

<span data-ttu-id="8c037-103">現在実行中のスレッドのハンドルを設定します。</span><span class="sxs-lookup"><span data-stu-id="8c037-103">Sets a handle for the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c037-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c037-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadToken (  
    [in] HANDLE hToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c037-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c037-105">Parameters</span></span>  

 `hToken`  
 <span data-ttu-id="8c037-106">から現在実行中のスレッドに設定するトークンへのハンドル。</span><span class="sxs-lookup"><span data-stu-id="8c037-106">[in] A handle to the token to set for the currently executing thread.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c037-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c037-107">Return Value</span></span>  
  
|<span data-ttu-id="8c037-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c037-108">HRESULT</span></span>|<span data-ttu-id="8c037-109">説明</span><span class="sxs-lookup"><span data-stu-id="8c037-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c037-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c037-110">S_OK</span></span>|<span data-ttu-id="8c037-111">`SetThreadToken` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="8c037-111">`SetThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="8c037-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c037-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c037-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="8c037-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c037-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c037-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c037-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8c037-115">The call timed out.</span></span>|  
|<span data-ttu-id="8c037-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c037-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c037-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8c037-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c037-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c037-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c037-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="8c037-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c037-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c037-120">E_FAIL</span></span>|<span data-ttu-id="8c037-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8c037-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c037-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8c037-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c037-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8c037-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c037-124">注釈</span><span class="sxs-lookup"><span data-stu-id="8c037-124">Remarks</span></span>  

 <span data-ttu-id="8c037-125">`IHostSecurityManager::SetThreadToken` は、同じ名前の対応する Win32 関数と同じように動作します。ただし、Win32 関数では、呼び出し元が任意のスレッドへのハンドルを渡すことができますが、 `IHostSecurityManager::SetThreadToken` は現在実行中のスレッドにのみトークンを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="8c037-125">`IHostSecurityManager::SetThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::SetThreadToken` can associate a token only with the currently executing thread.</span></span>  
  
 <span data-ttu-id="8c037-126">`HANDLE`型は COM に準拠していません。つまり、そのサイズはオペレーティングシステムに固有であり、カスタムマーシャリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="8c037-126">The `HANDLE` type is not COM-compliant; that is, its size is specific to an operating system and it requires custom marshaling.</span></span> <span data-ttu-id="8c037-127">したがって、このトークンは、CLR とホストの間でプロセス内でのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="8c037-127">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c037-128">要件</span><span class="sxs-lookup"><span data-stu-id="8c037-128">Requirements</span></span>  

 <span data-ttu-id="8c037-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c037-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c037-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8c037-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c037-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8c037-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c037-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c037-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c037-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c037-133">See also</span></span>

- [<span data-ttu-id="8c037-134">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c037-134">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="8c037-135">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c037-135">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
