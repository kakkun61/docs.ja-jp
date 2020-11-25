---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: df0b2d96963ad03e04bd8770d8a8078c6c20b8ff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728867"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="c0dfe-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="c0dfe-102">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>

<span data-ttu-id="c0dfe-103">指定したマネージアセンブリの指定した型の指定したメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-103">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0dfe-104">構文</span><span class="sxs-lookup"><span data-stu-id="c0dfe-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0dfe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0dfe-105">Parameters</span></span>  

 `pwzAssemblyPath`  
 <span data-ttu-id="c0dfe-106">からメソッドを呼び出すを <xref:System.Reflection.Assembly> 定義するへのパス <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-106">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="c0dfe-107">から <xref:System.Type> 呼び出すメソッドを定義するの名前。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-107">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="c0dfe-108">から呼び出すメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-108">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="c0dfe-109">からメソッドに渡す文字列パラメーター。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-109">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="c0dfe-110">入出力呼び出されたメソッドによって返される整数値。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-110">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0dfe-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="c0dfe-111">Return Value</span></span>  
  
|<span data-ttu-id="c0dfe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c0dfe-112">HRESULT</span></span>|<span data-ttu-id="c0dfe-113">説明</span><span class="sxs-lookup"><span data-stu-id="c0dfe-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c0dfe-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c0dfe-114">S_OK</span></span>|<span data-ttu-id="c0dfe-115">`ExecuteInDefaultAppDomain` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-115">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="c0dfe-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c0dfe-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c0dfe-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c0dfe-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c0dfe-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c0dfe-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-119">The call timed out.</span></span>|  
|<span data-ttu-id="c0dfe-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c0dfe-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c0dfe-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c0dfe-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c0dfe-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c0dfe-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c0dfe-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c0dfe-124">E_FAIL</span></span>|<span data-ttu-id="c0dfe-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c0dfe-126">メソッドから E_FAIL が返された場合、その CRL はプロセス内で使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-126">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="c0dfe-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0dfe-128">注釈</span><span class="sxs-lookup"><span data-stu-id="c0dfe-128">Remarks</span></span>  

 <span data-ttu-id="c0dfe-129">呼び出されたメソッドには、次のシグネチャが必要です。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-129">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="c0dfe-130">は `pwzMethodName` 呼び出されたメソッドの名前を表し、は `pwzArgument` そのメソッドにパラメーターとして渡される文字列値を表します。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-130">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="c0dfe-131">HRESULT 値が S_OK に設定されている場合、は、呼び出された `pReturnValue` メソッドによって返される整数値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-131">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="c0dfe-132">それ以外の場合、 `pReturnValue` は設定されません。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-132">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0dfe-133">要件</span><span class="sxs-lookup"><span data-stu-id="c0dfe-133">Requirements</span></span>  

 <span data-ttu-id="c0dfe-134">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0dfe-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0dfe-135">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c0dfe-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0dfe-136">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c0dfe-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0dfe-137">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0dfe-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0dfe-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0dfe-138">See also</span></span>

- [<span data-ttu-id="c0dfe-139">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0dfe-139">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
