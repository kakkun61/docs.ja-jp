---
title: IHostControl::SetAppDomainManager メソッド
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: 2f4c004db39c14e7a71b0caa55a6089e8f69ca3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680659"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="6206f-102">IHostControl::SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="6206f-102">IHostControl::SetAppDomainManager Method</span></span>

<span data-ttu-id="6206f-103">アプリケーションドメインが作成されたことをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="6206f-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6206f-104">構文</span><span class="sxs-lookup"><span data-stu-id="6206f-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6206f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6206f-105">Parameters</span></span>  

 `dwAppDomainID`  
 <span data-ttu-id="6206f-106">から選択されたの数値識別子 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="6206f-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="6206f-107">から <xref:System.AppDomainManager> ホストがとして実装しているオブジェクトへのポインター `IUnknown` 。</span><span class="sxs-lookup"><span data-stu-id="6206f-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6206f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="6206f-108">Return Value</span></span>  
  
|<span data-ttu-id="6206f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6206f-109">HRESULT</span></span>|<span data-ttu-id="6206f-110">説明</span><span class="sxs-lookup"><span data-stu-id="6206f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6206f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="6206f-111">S_OK</span></span>|<span data-ttu-id="6206f-112">`SetAppDomainManager` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6206f-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="6206f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6206f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6206f-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6206f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6206f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6206f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6206f-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6206f-116">The call timed out.</span></span>|  
|<span data-ttu-id="6206f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6206f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6206f-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6206f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6206f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6206f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6206f-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6206f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6206f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6206f-121">E_FAIL</span></span>|<span data-ttu-id="6206f-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6206f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6206f-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6206f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6206f-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6206f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6206f-125">注釈</span><span class="sxs-lookup"><span data-stu-id="6206f-125">Remarks</span></span>  

 <span data-ttu-id="6206f-126">は、 <xref:System.AppDomainManager> マネージコードにブートストラップし、それぞれの作成と設定を制御するためのメカニズムをホストに提供し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="6206f-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="6206f-127">は、作成される <xref:System.AppDomainManager> ときにそれぞれに読み込まれ <xref:System.AppDomain> <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="6206f-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="6206f-128">このオプションを選択した場合、CLR は、パラメーターの値を設定することによって、アプリケーションドメインが作成されたことをホストに通知 `pUnkAppDomainManager` します。</span><span class="sxs-lookup"><span data-stu-id="6206f-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="6206f-129">メソッドの実装では、 `SetAppDomainManager` ホストはアプリケーションドメインマネージャーのアセンブリ名と型を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6206f-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6206f-130">要件</span><span class="sxs-lookup"><span data-stu-id="6206f-130">Requirements</span></span>  

 <span data-ttu-id="6206f-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6206f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6206f-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6206f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6206f-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6206f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6206f-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6206f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6206f-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="6206f-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="6206f-136">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6206f-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
