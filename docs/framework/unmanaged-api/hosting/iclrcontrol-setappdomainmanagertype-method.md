---
title: ICLRControl::SetAppDomainManagerType メソッド
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
ms.openlocfilehash: 28fdd5340aee0fcd9875dd983c8c7649b5491c04
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674711"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="a813e-102">ICLRControl::SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="a813e-102">ICLRControl::SetAppDomainManagerType Method</span></span>

<span data-ttu-id="a813e-103">から派生した型を、 <xref:System.AppDomainManager> アプリケーションドメインマネージャーの型として設定します。</span><span class="sxs-lookup"><span data-stu-id="a813e-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a813e-104">構文</span><span class="sxs-lookup"><span data-stu-id="a813e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a813e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a813e-105">Parameters</span></span>  

 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="a813e-106">からから派生した、要求された型が実装されているアセンブリの名前 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="a813e-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="a813e-107">から `pwzAppDomainManagerAssembly` の機能を実装するパラメーターに実装されている型の名前 <xref:System.AppDomainManager> 。</span><span class="sxs-lookup"><span data-stu-id="a813e-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a813e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="a813e-108">Return Value</span></span>  
  
|<span data-ttu-id="a813e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a813e-109">HRESULT</span></span>|<span data-ttu-id="a813e-110">説明</span><span class="sxs-lookup"><span data-stu-id="a813e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a813e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a813e-111">S_OK</span></span>|<span data-ttu-id="a813e-112">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="a813e-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="a813e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a813e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a813e-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="a813e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a813e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a813e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a813e-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a813e-116">The call timed out.</span></span>|  
|<span data-ttu-id="a813e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a813e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a813e-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="a813e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a813e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a813e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a813e-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="a813e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a813e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a813e-121">E_FAIL</span></span>|<span data-ttu-id="a813e-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a813e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a813e-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a813e-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a813e-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a813e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a813e-125">要件</span><span class="sxs-lookup"><span data-stu-id="a813e-125">Requirements</span></span>  

 <span data-ttu-id="a813e-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a813e-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a813e-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a813e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a813e-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a813e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a813e-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a813e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a813e-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="a813e-130">See also</span></span>

- [<span data-ttu-id="a813e-131">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a813e-131">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="a813e-132">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a813e-132">IHostControl Interface</span></span>](ihostcontrol-interface.md)
