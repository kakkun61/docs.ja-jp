---
title: ICLRPolicyManager::SetActionOnFailure メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
ms.openlocfilehash: 8f44247ca7904a40f5ebc092d95c2e08b6048438
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725574"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a><span data-ttu-id="d6aa8-102">ICLRPolicyManager::SetActionOnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="d6aa8-102">ICLRPolicyManager::SetActionOnFailure Method</span></span>

<span data-ttu-id="d6aa8-103">指定したエラーが発生したときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-103">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6aa8-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6aa8-104">Syntax</span></span>  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6aa8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6aa8-105">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="d6aa8-106">から [Eclrfailure](eclrfailure-enumeration.md) 値の1つで、アクションを実行するエラーの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the type of failure for which to take action.</span></span>  
  
 `action`  
 <span data-ttu-id="d6aa8-107">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。エラーが発生したときに実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action to be taken when a failure occurs.</span></span> <span data-ttu-id="d6aa8-108">サポートされている値の一覧については、「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-108">For a list of supported values, see the Remarks section.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6aa8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d6aa8-109">Return Value</span></span>  
  
|<span data-ttu-id="d6aa8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6aa8-110">HRESULT</span></span>|<span data-ttu-id="d6aa8-111">説明</span><span class="sxs-lookup"><span data-stu-id="d6aa8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6aa8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6aa8-112">S_OK</span></span>|<span data-ttu-id="d6aa8-113">`SetActionOnFailure` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-113">`SetActionOnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="d6aa8-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6aa8-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6aa8-115">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-115">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6aa8-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6aa8-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6aa8-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-117">The call timed out.</span></span>|  
|<span data-ttu-id="d6aa8-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6aa8-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6aa8-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6aa8-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6aa8-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6aa8-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6aa8-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6aa8-122">E_FAIL</span></span>|<span data-ttu-id="d6aa8-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6aa8-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-124">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6aa8-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d6aa8-126">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d6aa8-126">E_INVALIDARG</span></span>|<span data-ttu-id="d6aa8-127">指定された操作に対してポリシーアクションを設定できないか、操作に無効なポリシーアクションが指定されました。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-127">A policy action cannot be set for the specified operation, or an invalid policy action was specified for the operation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6aa8-128">注釈</span><span class="sxs-lookup"><span data-stu-id="d6aa8-128">Remarks</span></span>  

 <span data-ttu-id="d6aa8-129">既定では、メモリなどのリソースの割り当てに失敗した場合、CLR は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-129">By default, the CLR throws an exception when it fails to allocate a resource such as memory.</span></span> <span data-ttu-id="d6aa8-130">`SetActionOnFailure` エラー発生時に実行するポリシーアクションを指定して、ホストがこの動作をオーバーライドできるようにします。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-130">`SetActionOnFailure` allows the host to override this behavior by specifying the policy action to take upon failure.</span></span> <span data-ttu-id="d6aa8-131">次の表は、サポートされている [Eclrfailure](eclrfailure-enumeration.md) 値と [epolicyaction](epolicyaction-enumeration.md) 値の組み合わせを示しています。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-131">The following table shows the combinations of [EClrFailure](eclrfailure-enumeration.md) and [EPolicyAction](epolicyaction-enumeration.md) values that are supported.</span></span> <span data-ttu-id="d6aa8-132">(FAIL_ プレフィックスは [Eclrfailure](eclrfailure-enumeration.md) 値から省略されています)。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-132">(The FAIL_ prefix is omitted from [EClrFailure](eclrfailure-enumeration.md) values.)</span></span>  
  
||<span data-ttu-id="d6aa8-133">NonCriticalResource</span><span class="sxs-lookup"><span data-stu-id="d6aa8-133">NonCriticalResource</span></span>|<span data-ttu-id="d6aa8-134">CriticalResource</span><span class="sxs-lookup"><span data-stu-id="d6aa8-134">CriticalResource</span></span>|<span data-ttu-id="d6aa8-135">Fat (Alruntime)</span><span class="sxs-lookup"><span data-stu-id="d6aa8-135">FatalRuntime</span></span>|<span data-ttu-id="d6aa8-136">OrphanedLock</span><span class="sxs-lookup"><span data-stu-id="d6aa8-136">OrphanedLock</span></span>|<span data-ttu-id="d6aa8-137">StackOverflow</span><span class="sxs-lookup"><span data-stu-id="d6aa8-137">StackOverflow</span></span>|<span data-ttu-id="d6aa8-138">AccessViolation</span><span class="sxs-lookup"><span data-stu-id="d6aa8-138">AccessViolation</span></span>|<span data-ttu-id="d6aa8-139">CodeContract</span><span class="sxs-lookup"><span data-stu-id="d6aa8-139">CodeContract</span></span>|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|<span data-ttu-id="d6aa8-140">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-140">X</span></span>|<span data-ttu-id="d6aa8-141">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-141">X</span></span>||||<span data-ttu-id="d6aa8-142">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-142">N/A</span></span>||  
|<span data-ttu-id="d6aa8-143">の例外</span><span class="sxs-lookup"><span data-stu-id="d6aa8-143">eThrowException</span></span>|<span data-ttu-id="d6aa8-144">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-144">X</span></span>|<span data-ttu-id="d6aa8-145">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-145">X</span></span>||||<span data-ttu-id="d6aa8-146">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-146">N/A</span></span>||  
|`eAbortThread`|<span data-ttu-id="d6aa8-147">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-147">X</span></span>|<span data-ttu-id="d6aa8-148">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-148">X</span></span>||||<span data-ttu-id="d6aa8-149">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-149">N/A</span></span>|<span data-ttu-id="d6aa8-150">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-150">X</span></span>|  
|`eRudeAbortThread`|<span data-ttu-id="d6aa8-151">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-151">X</span></span>|<span data-ttu-id="d6aa8-152">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-152">X</span></span>||||<span data-ttu-id="d6aa8-153">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-153">N/A</span></span>|<span data-ttu-id="d6aa8-154">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-154">X</span></span>|  
|`eUnloadAppDomain`|<span data-ttu-id="d6aa8-155">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-155">X</span></span>|<span data-ttu-id="d6aa8-156">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-156">X</span></span>||<span data-ttu-id="d6aa8-157">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-157">X</span></span>||<span data-ttu-id="d6aa8-158">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-158">N/A</span></span>|<span data-ttu-id="d6aa8-159">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-159">X</span></span>|  
|`eRudeUnloadAppDomain`|<span data-ttu-id="d6aa8-160">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-160">X</span></span>|<span data-ttu-id="d6aa8-161">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-161">X</span></span>||<span data-ttu-id="d6aa8-162">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-162">X</span></span>|<span data-ttu-id="d6aa8-163">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-163">X</span></span>|<span data-ttu-id="d6aa8-164">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-164">N/A</span></span>|<span data-ttu-id="d6aa8-165">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-165">X</span></span>|  
|`eExitProcess`|<span data-ttu-id="d6aa8-166">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-166">X</span></span>|<span data-ttu-id="d6aa8-167">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-167">X</span></span>||<span data-ttu-id="d6aa8-168">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-168">X</span></span>|<span data-ttu-id="d6aa8-169">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-169">X</span></span>|<span data-ttu-id="d6aa8-170">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-170">N/A</span></span>|<span data-ttu-id="d6aa8-171">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-171">X</span></span>|  
|<span data-ttu-id="d6aa8-172">eFastExitProcess</span><span class="sxs-lookup"><span data-stu-id="d6aa8-172">eFastExitProcess</span></span>|<span data-ttu-id="d6aa8-173">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-173">X</span></span>|<span data-ttu-id="d6aa8-174">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-174">X</span></span>||<span data-ttu-id="d6aa8-175">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-175">X</span></span>|<span data-ttu-id="d6aa8-176">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-176">X</span></span>|<span data-ttu-id="d6aa8-177">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-177">N/A</span></span>||  
|`eRudeExitProcess`|<span data-ttu-id="d6aa8-178">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-178">X</span></span>|<span data-ttu-id="d6aa8-179">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-179">X</span></span>|<span data-ttu-id="d6aa8-180">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-180">X</span></span>|<span data-ttu-id="d6aa8-181">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-181">X</span></span>|<span data-ttu-id="d6aa8-182">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-182">X</span></span>|<span data-ttu-id="d6aa8-183">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-183">N/A</span></span>||  
|`eDisableRuntime`|<span data-ttu-id="d6aa8-184">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-184">X</span></span>|<span data-ttu-id="d6aa8-185">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-185">X</span></span>|<span data-ttu-id="d6aa8-186">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-186">X</span></span>|<span data-ttu-id="d6aa8-187">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-187">X</span></span>|<span data-ttu-id="d6aa8-188">X</span><span class="sxs-lookup"><span data-stu-id="d6aa8-188">X</span></span>|<span data-ttu-id="d6aa8-189">該当なし</span><span class="sxs-lookup"><span data-stu-id="d6aa8-189">N/A</span></span>||  
  
## <a name="requirements"></a><span data-ttu-id="d6aa8-190">要件</span><span class="sxs-lookup"><span data-stu-id="d6aa8-190">Requirements</span></span>  

 <span data-ttu-id="d6aa8-191">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6aa8-191">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6aa8-192">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d6aa8-192">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6aa8-193">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d6aa8-193">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6aa8-194">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6aa8-194">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6aa8-195">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6aa8-195">See also</span></span>

- [<span data-ttu-id="d6aa8-196">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="d6aa8-196">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="d6aa8-197">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="d6aa8-197">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="d6aa8-198">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6aa8-198">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="d6aa8-199">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6aa8-199">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
