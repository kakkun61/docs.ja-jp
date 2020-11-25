---
title: ICLRRuntimeHost::UnloadAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
ms.openlocfilehash: cc5d0d65d213d952c0897a72d8ec38ea6b8b22db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700666"
---
# <a name="iclrruntimehostunloadappdomain-method"></a><span data-ttu-id="3ea90-102">ICLRRuntimeHost::UnloadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="3ea90-102">ICLRRuntimeHost::UnloadAppDomain Method</span></span>

<span data-ttu-id="3ea90-103"><xref:System.AppDomain>指定した数値識別子に対応するマネージをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="3ea90-103">Unloads the managed <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ea90-104">構文</span><span class="sxs-lookup"><span data-stu-id="3ea90-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ea90-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3ea90-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="3ea90-106">からアンロードするアプリケーションドメインの数値識別子。</span><span class="sxs-lookup"><span data-stu-id="3ea90-106">[in] The numeric identifier of the application domain to unload.</span></span>  
  
 `fWaitUntilDone`  
 <span data-ttu-id="3ea90-107">[入力] `true` アプリケーションドメインのアンロードを試行する前に、共通言語ランタイム (CLR) がアプリケーションの現在のスレッドの実行を完了するまで待機する必要があることを示す場合は。</span><span class="sxs-lookup"><span data-stu-id="3ea90-107">[in] `true` to indicate that the common language runtime( CLR) must wait until it has finished executing the application's current thread before attempting to unload the application domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ea90-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="3ea90-108">Return Value</span></span>  
  
|<span data-ttu-id="3ea90-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ea90-109">HRESULT</span></span>|<span data-ttu-id="3ea90-110">説明</span><span class="sxs-lookup"><span data-stu-id="3ea90-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ea90-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="3ea90-111">S_OK</span></span>|<span data-ttu-id="3ea90-112">`UnloadAppDomain` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3ea90-112">`UnloadAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="3ea90-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3ea90-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3ea90-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3ea90-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3ea90-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3ea90-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3ea90-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3ea90-116">The call timed out.</span></span>|  
|<span data-ttu-id="3ea90-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3ea90-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3ea90-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3ea90-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3ea90-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3ea90-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3ea90-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3ea90-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3ea90-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3ea90-121">E_FAIL</span></span>|<span data-ttu-id="3ea90-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3ea90-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3ea90-123">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3ea90-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3ea90-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3ea90-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ea90-125">注釈</span><span class="sxs-lookup"><span data-stu-id="3ea90-125">Remarks</span></span>  

 <span data-ttu-id="3ea90-126">[GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md)を呼び出すことにより、現在のスレッドが実行されているアプリケーションドメインの数値識別子を取得できます。</span><span class="sxs-lookup"><span data-stu-id="3ea90-126">You can get the numeric identifier of the application domain in which the current thread is executing by calling [GetCurrentAppDomainId](iclrruntimehost-getcurrentappdomainid-method.md).</span></span> <span data-ttu-id="3ea90-127">この識別子は <xref:System.AppDomain.Id%2A> 、マネージ型のプロパティに対応 <xref:System.AppDomain> しています。</span><span class="sxs-lookup"><span data-stu-id="3ea90-127">This identifier corresponds to the <xref:System.AppDomain.Id%2A> property of the managed <xref:System.AppDomain> type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ea90-128">要件</span><span class="sxs-lookup"><span data-stu-id="3ea90-128">Requirements</span></span>  

 <span data-ttu-id="3ea90-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ea90-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ea90-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3ea90-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3ea90-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3ea90-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3ea90-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ea90-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ea90-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ea90-133">See also</span></span>

- [<span data-ttu-id="3ea90-134">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3ea90-134">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
