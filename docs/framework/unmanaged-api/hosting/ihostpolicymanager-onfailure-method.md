---
title: IHostPolicyManager::OnFailure メソッド
ms.date: 03/30/2017
api_name:
- IHostPolicyManager.OnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager::OnFailure
helpviewer_keywords:
- OnFailure method [.NET Framework hosting]
- IHostPolicyManager::OnFailure method [.NET Framework hosting]
ms.assetid: 77d3f31e-9a53-4349-9c02-610a71736d42
topic_type:
- apiref
ms.openlocfilehash: efa7b9d49ea9807af2164bb6ee54422dd72b14e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730423"
---
# <a name="ihostpolicymanageronfailure-method"></a><span data-ttu-id="ea603-102">IHostPolicyManager::OnFailure メソッド</span><span class="sxs-lookup"><span data-stu-id="ea603-102">IHostPolicyManager::OnFailure Method</span></span>

<span data-ttu-id="ea603-103">リソース割り当てまたは再利用の失敗に応じて、 [ICLRPolicyManager:: SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) メソッドの呼び出しによって指定されたアクションを共通言語ランタイム (CLR) が実行しようとしていることをホストに通知します。</span><span class="sxs-lookup"><span data-stu-id="ea603-103">Notifies the host that the common language runtime (CLR) is about to take the action specified by a call to the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method in response to a resource allocation or reclamation failure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea603-104">構文</span><span class="sxs-lookup"><span data-stu-id="ea603-104">Syntax</span></span>  
  
```cpp  
HRESULT OnFailure(  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea603-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea603-105">Parameters</span></span>  

 `failure`  
 <span data-ttu-id="ea603-106">から [Eclrfailure](eclrfailure-enumeration.md) 値の1つ。 CLR が応答しているエラーの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="ea603-106">[in] One of the [EClrFailure](eclrfailure-enumeration.md) values, indicating the kind of failure to which the CLR is responding.</span></span>  
  
 `action`  
 <span data-ttu-id="ea603-107">から [Epolicyaction](epolicyaction-enumeration.md) 値の1つ。 CLR がに応答して実行しているアクションを示し `failure` ます。</span><span class="sxs-lookup"><span data-stu-id="ea603-107">[in] One of the [EPolicyAction](epolicyaction-enumeration.md) values, indicating the action the CLR is taking in response to `failure`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea603-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ea603-108">Return Value</span></span>  
  
|<span data-ttu-id="ea603-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea603-109">HRESULT</span></span>|<span data-ttu-id="ea603-110">説明</span><span class="sxs-lookup"><span data-stu-id="ea603-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea603-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea603-111">S_OK</span></span>|<span data-ttu-id="ea603-112">`OnFailure` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ea603-112">`OnFailure` returned successfully.</span></span>|  
|<span data-ttu-id="ea603-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea603-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea603-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ea603-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ea603-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ea603-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ea603-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ea603-116">The call timed out.</span></span>|  
|<span data-ttu-id="ea603-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ea603-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ea603-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ea603-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ea603-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ea603-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ea603-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ea603-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ea603-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea603-121">E_FAIL</span></span>|<span data-ttu-id="ea603-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ea603-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ea603-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ea603-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ea603-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ea603-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea603-125">要件</span><span class="sxs-lookup"><span data-stu-id="ea603-125">Requirements</span></span>  

 <span data-ttu-id="ea603-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea603-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea603-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ea603-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea603-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ea603-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea603-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea603-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea603-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea603-130">See also</span></span>

- [<span data-ttu-id="ea603-131">EClrFailure 列挙型</span><span class="sxs-lookup"><span data-stu-id="ea603-131">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="ea603-132">EPolicyAction 列挙型</span><span class="sxs-lookup"><span data-stu-id="ea603-132">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="ea603-133">ICLRPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea603-133">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="ea603-134">IHostPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea603-134">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
