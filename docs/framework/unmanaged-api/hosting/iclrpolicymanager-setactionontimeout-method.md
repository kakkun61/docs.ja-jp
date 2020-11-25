---
title: ICLRPolicyManager::SetActionOnTimeout メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnTimeout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnTimeout
helpviewer_keywords:
- SetActionOnTimeout method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnTimeout method [.NET Framework hosting]
ms.assetid: 38439fa1-2b99-4fa8-a6ec-08afc0f83b9c
topic_type:
- apiref
ms.openlocfilehash: 3ddd78ea35d5709abb30af085b2212a09b28c2ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725561"
---
# <a name="iclrpolicymanagersetactionontimeout-method"></a><span data-ttu-id="3b30e-102">ICLRPolicyManager::SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="3b30e-102">ICLRPolicyManager::SetActionOnTimeout Method</span></span>

<span data-ttu-id="3b30e-103">指定された操作がタイムアウトしたときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="3b30e-103">Specifies the policy action the common language runtime (CLR) should take when the specified operation times out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b30e-104">構文</span><span class="sxs-lookup"><span data-stu-id="3b30e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnTimeout (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b30e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3b30e-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="3b30e-106">からタイムアウトアクションを指定する操作を示す [EClrOperation](eclroperation-enumeration.md) 値の1つ。</span><span class="sxs-lookup"><span data-stu-id="3b30e-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to specify the timeout action.</span></span> <span data-ttu-id="3b30e-107">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3b30e-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="3b30e-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3b30e-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="3b30e-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3b30e-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="3b30e-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3b30e-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="3b30e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3b30e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `action`  
 <span data-ttu-id="3b30e-112">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。操作がタイムアウトしたときに実行されるポリシーアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="3b30e-112">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action to be taken when the operation times out.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b30e-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="3b30e-113">Return Value</span></span>  
  
|<span data-ttu-id="3b30e-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3b30e-114">HRESULT</span></span>|<span data-ttu-id="3b30e-115">説明</span><span class="sxs-lookup"><span data-stu-id="3b30e-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3b30e-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="3b30e-116">S_OK</span></span>|<span data-ttu-id="3b30e-117">`SetActionOnTimeout` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="3b30e-117">`SetActionOnTimeout` returned successfully.</span></span>|  
|<span data-ttu-id="3b30e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3b30e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3b30e-119">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="3b30e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3b30e-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3b30e-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3b30e-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="3b30e-121">The call timed out.</span></span>|  
|<span data-ttu-id="3b30e-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3b30e-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3b30e-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="3b30e-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3b30e-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3b30e-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3b30e-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="3b30e-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3b30e-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3b30e-126">E_FAIL</span></span>|<span data-ttu-id="3b30e-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3b30e-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3b30e-128">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="3b30e-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3b30e-129">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="3b30e-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3b30e-130">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="3b30e-130">E_INVALIDARG</span></span>|<span data-ttu-id="3b30e-131">指定されたに対してタイムアウトを設定できない `operation` か、に無効な値が指定されました `operation` 。</span><span class="sxs-lookup"><span data-stu-id="3b30e-131">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `operation`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b30e-132">注釈</span><span class="sxs-lookup"><span data-stu-id="3b30e-132">Remarks</span></span>  

 <span data-ttu-id="3b30e-133">タイムアウト値は、CLR によって設定された既定のタイムアウトか、 [ICLRPolicyManager:: SetTimeout](iclrpolicymanager-settimeout-method.md) メソッドの呼び出しでホストによって指定された値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="3b30e-133">The timeout value can be either the default timeout set by the CLR, or a value specified by the host in a call to the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) method.</span></span>  
  
 <span data-ttu-id="3b30e-134">すべてのポリシーアクション値は、CLR 操作のタイムアウト動作として指定できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3b30e-134">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="3b30e-135">`SetActionOnTimeout` は、通常、動作をエスカレートするためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="3b30e-135">`SetActionOnTimeout` is typically used only to escalate behavior.</span></span> <span data-ttu-id="3b30e-136">たとえば、ホストは、スレッドの中止をルースレッドの中止に変換するように指定できますが、逆のを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3b30e-136">For example, a host can specify that thread aborts be turned into rude thread aborts, but cannot specify the opposite.</span></span> <span data-ttu-id="3b30e-137">次の表は、 `action` 有効な値の有効な値を示して `operation` います。</span><span class="sxs-lookup"><span data-stu-id="3b30e-137">The table below describes the valid `action` values for valid `operation` values.</span></span>  
  
|<span data-ttu-id="3b30e-138">の値 `operation`</span><span class="sxs-lookup"><span data-stu-id="3b30e-138">Value for `operation`</span></span>|<span data-ttu-id="3b30e-139">`action` の有効な値</span><span class="sxs-lookup"><span data-stu-id="3b30e-139">Valid values for `action`</span></span>|  
|---------------------------|-------------------------------|  
|<span data-ttu-id="3b30e-140">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3b30e-140">OPR_ThreadRudeAbortInNonCriticalRegion</span></span><br /><br /> <span data-ttu-id="3b30e-141">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="3b30e-141">OPR_ThreadRudeAbortInCriticalRegion</span></span>|<span data-ttu-id="3b30e-142">-eRudeAbortThread</span><span class="sxs-lookup"><span data-stu-id="3b30e-142">-   eRudeAbortThread</span></span><br /><span data-ttu-id="3b30e-143">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3b30e-143">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3b30e-144">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3b30e-144">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3b30e-145">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-145">-   eExitProcess</span></span><br /><span data-ttu-id="3b30e-146">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-146">-   eFastExitProcess</span></span><br /><span data-ttu-id="3b30e-147">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-147">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3b30e-148">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3b30e-148">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3b30e-149">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="3b30e-149">OPR_AppDomainUnload</span></span>|<span data-ttu-id="3b30e-150">- eUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3b30e-150">-   eUnloadAppDomain</span></span><br /><span data-ttu-id="3b30e-151">- eRudeUnloadAppDomain</span><span class="sxs-lookup"><span data-stu-id="3b30e-151">-   eRudeUnloadAppDomain</span></span><br /><span data-ttu-id="3b30e-152">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-152">-   eExitProcess</span></span><br /><span data-ttu-id="3b30e-153">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-153">-   eFastExitProcess</span></span><br /><span data-ttu-id="3b30e-154">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-154">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3b30e-155">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3b30e-155">-   eDisableRuntime</span></span>|  
|<span data-ttu-id="3b30e-156">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="3b30e-156">OPR_ProcessExit</span></span>|<span data-ttu-id="3b30e-157">- eExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-157">-   eExitProcess</span></span><br /><span data-ttu-id="3b30e-158">- eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-158">-   eFastExitProcess</span></span><br /><span data-ttu-id="3b30e-159">- eRudeExitProcess</span><span class="sxs-lookup"><span data-stu-id="3b30e-159">-   eRudeExitProcess</span></span><br /><span data-ttu-id="3b30e-160">-eDisableRuntime</span><span class="sxs-lookup"><span data-stu-id="3b30e-160">-   eDisableRuntime</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b30e-161">要件</span><span class="sxs-lookup"><span data-stu-id="3b30e-161">Requirements</span></span>  

 <span data-ttu-id="3b30e-162">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b30e-162">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b30e-163">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3b30e-163">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b30e-164">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3b30e-164">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b30e-165">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b30e-165">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b30e-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b30e-166">See also</span></span>

- [<span data-ttu-id="3b30e-167">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="3b30e-167">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="3b30e-168">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="3b30e-168">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="3b30e-169">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b30e-169">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="3b30e-170">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3b30e-170">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
