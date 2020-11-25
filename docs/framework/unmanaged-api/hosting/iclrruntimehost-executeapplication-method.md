---
title: ICLRRuntimeHost::ExecuteApplication メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
ms.openlocfilehash: ef043dd2308c4b76e975bd2ad1f68725579e8fc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728911"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="c7e68-102">ICLRRuntimeHost::ExecuteApplication メソッド</span><span class="sxs-lookup"><span data-stu-id="c7e68-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>

<span data-ttu-id="c7e68-103">新しいドメインでアクティブ化するアプリケーションを指定するために、マニフェストベースの ClickOnce 配置シナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c7e68-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="c7e68-104">これらのシナリオの詳細については、「 [ClickOnce のセキュリティと配置](/visualstudio/deployment/clickonce-security-and-deployment)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7e68-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e68-105">構文</span><span class="sxs-lookup"><span data-stu-id="c7e68-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7e68-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7e68-106">Parameters</span></span>  

 `pwzAppFullName`  
 <span data-ttu-id="c7e68-107">からに定義されているアプリケーションの完全名 <xref:System.ApplicationIdentity> 。</span><span class="sxs-lookup"><span data-stu-id="c7e68-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="c7e68-108">から配列に格納されている文字列の数 `ppwzManifestPaths` 。</span><span class="sxs-lookup"><span data-stu-id="c7e68-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="c7e68-109">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="c7e68-109">[in] Optional.</span></span> <span data-ttu-id="c7e68-110">アプリケーションのマニフェストパスを格納する文字列配列。</span><span class="sxs-lookup"><span data-stu-id="c7e68-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="c7e68-111">から配列に格納されている文字列の数 `ppwzActivationData` 。</span><span class="sxs-lookup"><span data-stu-id="c7e68-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="c7e68-112">[in] オプション。</span><span class="sxs-lookup"><span data-stu-id="c7e68-112">[in] Optional.</span></span> <span data-ttu-id="c7e68-113">Web に配置されたアプリケーションの URL のクエリ文字列部分など、アプリケーションのアクティベーションデータを格納する文字列配列。</span><span class="sxs-lookup"><span data-stu-id="c7e68-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="c7e68-114">入出力アプリケーションのエントリポイントから返される値。</span><span class="sxs-lookup"><span data-stu-id="c7e68-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7e68-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="c7e68-115">Return Value</span></span>  
  
|<span data-ttu-id="c7e68-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7e68-116">HRESULT</span></span>|<span data-ttu-id="c7e68-117">説明</span><span class="sxs-lookup"><span data-stu-id="c7e68-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7e68-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7e68-118">S_OK</span></span>|<span data-ttu-id="c7e68-119">`ExecuteApplication` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="c7e68-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="c7e68-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7e68-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7e68-121">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="c7e68-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7e68-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7e68-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7e68-123">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c7e68-123">The call timed out.</span></span>|  
|<span data-ttu-id="c7e68-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7e68-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7e68-125">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c7e68-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7e68-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7e68-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7e68-127">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="c7e68-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7e68-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7e68-128">E_FAIL</span></span>|<span data-ttu-id="c7e68-129">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c7e68-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7e68-130">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c7e68-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7e68-131">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="c7e68-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7e68-132">注釈</span><span class="sxs-lookup"><span data-stu-id="c7e68-132">Remarks</span></span>  

 <span data-ttu-id="c7e68-133">`ExecuteApplication` は、新しく作成されたアプリケーションドメインで ClickOnce アプリケーションをアクティブ化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c7e68-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="c7e68-134">`pReturnValue`出力パラメーターは、アプリケーションによって返される値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c7e68-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="c7e68-135">に null 値を指定した場合 `pReturnValue` 、 `ExecuteApplication` は失敗しませんが、値を返しません。</span><span class="sxs-lookup"><span data-stu-id="c7e68-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c7e68-136">メソッドを呼び出してからマニフェストベースのアプリケーションをアクティブ化する前に、 [Start メソッド](iclrruntimehost-start-method.md) メソッドを呼び出さないでください `ExecuteApplication` 。</span><span class="sxs-lookup"><span data-stu-id="c7e68-136">Do not call the [Start Method](iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="c7e68-137">`Start`メソッドが最初に呼び出された場合、 `ExecuteApplication` メソッドの呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c7e68-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7e68-138">要件</span><span class="sxs-lookup"><span data-stu-id="c7e68-138">Requirements</span></span>  

 <span data-ttu-id="c7e68-139">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7e68-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7e68-140">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c7e68-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7e68-141">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c7e68-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7e68-142">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7e68-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e68-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7e68-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="c7e68-144">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7e68-144">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="c7e68-145">SetAppDomainManager メソッド</span><span class="sxs-lookup"><span data-stu-id="c7e68-145">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="c7e68-146">チュートリアル: デザイナーを使用して ClickOnce 配置 API で必要に応じてアセンブリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="c7e68-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
