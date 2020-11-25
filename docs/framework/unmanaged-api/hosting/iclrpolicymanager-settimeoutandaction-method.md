---
title: ICLRPolicyManager::SetTimeoutAndAction メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
ms.openlocfilehash: 41e13e20a1cf5a7000907b1cc7d8d2af5174ceba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728975"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="1349e-102">ICLRPolicyManager::SetTimeoutAndAction メソッド</span><span class="sxs-lookup"><span data-stu-id="1349e-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>

<span data-ttu-id="1349e-103">指定された操作のタイムアウト値を設定し、操作が発生したときに共通言語ランタイム (CLR) が実行するポリシーアクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="1349e-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1349e-104">構文</span><span class="sxs-lookup"><span data-stu-id="1349e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1349e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1349e-105">Parameters</span></span>  

 `operation`  
 <span data-ttu-id="1349e-106">からタイムアウトとポリシーを設定する操作を示す [EClrOperation](eclroperation-enumeration.md) 値の1つ `action` 。</span><span class="sxs-lookup"><span data-stu-id="1349e-106">[in] One of the [EClrOperation](eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="1349e-107">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1349e-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="1349e-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="1349e-108">OPR_AppDomainUnload</span></span>  
  
- <span data-ttu-id="1349e-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="1349e-109">OPR_ProcessExit</span></span>  
  
- <span data-ttu-id="1349e-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="1349e-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
- <span data-ttu-id="1349e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="1349e-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="1349e-112">から新しいタイムアウト値 (ミリ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="1349e-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="1349e-113">値が無限であると、 `operation` タイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="1349e-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="1349e-114">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。 CLR が発生したときに実行するポリシーアクションを示し `operation` ます。</span><span class="sxs-lookup"><span data-stu-id="1349e-114">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1349e-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="1349e-115">Return Value</span></span>  
  
|<span data-ttu-id="1349e-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1349e-116">HRESULT</span></span>|<span data-ttu-id="1349e-117">説明</span><span class="sxs-lookup"><span data-stu-id="1349e-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1349e-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="1349e-118">S_OK</span></span>|<span data-ttu-id="1349e-119">`SetTimeoutAndAction` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="1349e-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="1349e-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1349e-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1349e-121">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="1349e-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1349e-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1349e-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1349e-123">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="1349e-123">The call timed out.</span></span>|  
|<span data-ttu-id="1349e-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1349e-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1349e-125">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="1349e-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1349e-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1349e-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1349e-127">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="1349e-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1349e-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1349e-128">E_FAIL</span></span>|<span data-ttu-id="1349e-129">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="1349e-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1349e-130">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1349e-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1349e-131">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="1349e-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1349e-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="1349e-132">E_INVALIDARG</span></span>|<span data-ttu-id="1349e-133">指定されたに対してタイムアウトを設定できない `operation` か、に無効な値が指定されました `action` 。</span><span class="sxs-lookup"><span data-stu-id="1349e-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1349e-134">注釈</span><span class="sxs-lookup"><span data-stu-id="1349e-134">Remarks</span></span>  

 <span data-ttu-id="1349e-135">`SetTimeoutAndAction`[ICLRPolicyManager:: SetTimeout](iclrpolicymanager-settimeout-method.md)メソッドと[ICLRPolicyManager:: SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md)メソッドの機能をカプセル化し、これら2つのメソッドの順次呼び出しの代わりに呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="1349e-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1349e-136">すべてのポリシーアクション値は、CLR 操作のタイムアウト動作として指定できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="1349e-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="1349e-137">有効な値については、これら2つの方法に関するトピックの「解説」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1349e-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1349e-138">要件</span><span class="sxs-lookup"><span data-stu-id="1349e-138">Requirements</span></span>  

 <span data-ttu-id="1349e-139">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1349e-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1349e-140">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1349e-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1349e-141">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="1349e-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1349e-142">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1349e-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1349e-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="1349e-143">See also</span></span>

- [<span data-ttu-id="1349e-144">EClrOperation 列挙型</span><span class="sxs-lookup"><span data-stu-id="1349e-144">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="1349e-145">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="1349e-145">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="1349e-146">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1349e-146">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="1349e-147">SetActionOnTimeout メソッド</span><span class="sxs-lookup"><span data-stu-id="1349e-147">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="1349e-148">ICLRPolicyManager:: SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="1349e-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](iclrpolicymanager-settimeoutandaction-method.md)
