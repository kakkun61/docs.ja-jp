---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: 8da9c9fea5cf5b3a27eeb9d0222f0845c832b7da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714199"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="6785f-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="6785f-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>

<span data-ttu-id="6785f-103">指定したアセンブリのバインディングポリシーを変更し、新しいバージョンのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6785f-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6785f-104">構文</span><span class="sxs-lookup"><span data-stu-id="6785f-104">Syntax</span></span>  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6785f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6785f-105">Parameters</span></span>  

 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="6785f-106">から変更するアセンブリの id。</span><span class="sxs-lookup"><span data-stu-id="6785f-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="6785f-107">から変更されたアセンブリの新しい id。</span><span class="sxs-lookup"><span data-stu-id="6785f-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="6785f-108">から変更するアセンブリのバインディングポリシーデータを格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6785f-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="6785f-109">から置換されるバインディングポリシーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="6785f-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="6785f-110">からリダイレクトの制御を示す [Ehostbindingpolicymodifyflags](ehostbindingpolicymodifyflags-enumeration.md) 値の論理的または組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="6785f-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="6785f-111">入出力新しいバインドポリシーデータを格納しているバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6785f-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="6785f-112">[入力、出力]新しいバインドポリシーバッファーのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6785f-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6785f-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="6785f-113">Return Value</span></span>  
  
|<span data-ttu-id="6785f-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6785f-114">HRESULT</span></span>|<span data-ttu-id="6785f-115">説明</span><span class="sxs-lookup"><span data-stu-id="6785f-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6785f-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="6785f-116">S_OK</span></span>|<span data-ttu-id="6785f-117">ポリシーが正常に変更されました。</span><span class="sxs-lookup"><span data-stu-id="6785f-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="6785f-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6785f-118">E_INVALIDARG</span></span>|<span data-ttu-id="6785f-119">`pwzSourceAssemblyIdentity` または `pwzTargetAssemblyIdentity` が null 参照です。</span><span class="sxs-lookup"><span data-stu-id="6785f-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="6785f-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="6785f-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="6785f-121">`pbNewApplicationPolicy` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="6785f-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="6785f-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6785f-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6785f-123">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6785f-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6785f-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6785f-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6785f-125">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6785f-125">The call timed out.</span></span>|  
|<span data-ttu-id="6785f-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6785f-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6785f-127">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6785f-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6785f-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6785f-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6785f-129">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6785f-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6785f-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6785f-130">E_FAIL</span></span>|<span data-ttu-id="6785f-131">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6785f-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6785f-132">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6785f-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6785f-133">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6785f-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6785f-134">注釈</span><span class="sxs-lookup"><span data-stu-id="6785f-134">Remarks</span></span>  

 <span data-ttu-id="6785f-135">メソッドは、 `ModifyApplicationPolicy` 2 回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="6785f-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="6785f-136">最初の呼び出しでは、パラメーターに null 値を指定する必要があり `pbNewApplicationPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="6785f-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="6785f-137">この呼び出しは、に必要な値で返され `pcbNewAppPolicySize` ます。</span><span class="sxs-lookup"><span data-stu-id="6785f-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="6785f-138">2番目の呼び出しでは、にこの値を指定 `pcbNewAppPolicySize` し、のサイズのバッファーを指す必要があり `pbNewApplicationPolicy` ます。</span><span class="sxs-lookup"><span data-stu-id="6785f-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6785f-139">要件</span><span class="sxs-lookup"><span data-stu-id="6785f-139">Requirements</span></span>  

 <span data-ttu-id="6785f-140">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6785f-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6785f-141">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6785f-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6785f-142">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6785f-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6785f-143">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6785f-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6785f-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="6785f-144">See also</span></span>

- [<span data-ttu-id="6785f-145">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6785f-145">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
