---
title: ICLRRuntimeHost::ExecuteInAppDomain メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: 4c28c4a5cc64b20c9ac9c57e1aef5e7b90a20e01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728889"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a><span data-ttu-id="ae998-102">ICLRRuntimeHost::ExecuteInAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="ae998-102">ICLRRuntimeHost::ExecuteInAppDomain Method</span></span>

<span data-ttu-id="ae998-103">指定し <xref:System.AppDomain> たマネージコードを実行するを指定します。</span><span class="sxs-lookup"><span data-stu-id="ae998-103">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae998-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae998-104">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae998-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae998-105">Parameters</span></span>  

 `AppDomainId`  
 <span data-ttu-id="ae998-106">から <xref:System.AppDomain> 指定したメソッドを実行するの数値 ID。</span><span class="sxs-lookup"><span data-stu-id="ae998-106">[in] The numeric ID of the <xref:System.AppDomain> in which to execute the specified method.</span></span>  
  
 `pCallback`  
 <span data-ttu-id="ae998-107">から指定した内で実行する関数へのポインター <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="ae998-107">[in] A pointer to the function to execute within the specified <xref:System.AppDomain>.</span></span>  
  
 `cookie`  
 <span data-ttu-id="ae998-108">から非透過的な呼び出し元に割り当てられたメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae998-108">[in] A pointer to opaque caller-allocated memory.</span></span> <span data-ttu-id="ae998-109">このパラメーターは、共通言語ランタイム (CLR) によってドメインコールバックに渡されます。</span><span class="sxs-lookup"><span data-stu-id="ae998-109">This parameter is passed by the common language runtime (CLR) to the domain callback.</span></span> <span data-ttu-id="ae998-110">ランタイムによって管理されるヒープメモリではありません。このメモリの割り当てと有効期間は、どちらも呼び出し元によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="ae998-110">It is not runtime-managed heap memory; both the allocation and lifetime of this memory are controlled by the caller.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae998-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae998-111">Return Value</span></span>  
  
|<span data-ttu-id="ae998-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ae998-112">HRESULT</span></span>|<span data-ttu-id="ae998-113">説明</span><span class="sxs-lookup"><span data-stu-id="ae998-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae998-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ae998-114">S_OK</span></span>|<span data-ttu-id="ae998-115">`ExecuteInAppDomain` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="ae998-115">`ExecuteInAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="ae998-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ae998-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ae998-117">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="ae998-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ae998-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ae998-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ae998-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ae998-119">The call timed out.</span></span>|  
|<span data-ttu-id="ae998-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ae998-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ae998-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ae998-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ae998-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ae998-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ae998-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="ae998-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ae998-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ae998-124">E_FAIL</span></span>|<span data-ttu-id="ae998-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ae998-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ae998-126">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="ae998-126">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ae998-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="ae998-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae998-128">注釈</span><span class="sxs-lookup"><span data-stu-id="ae998-128">Remarks</span></span>  

 <span data-ttu-id="ae998-129">`ExecuteInAppDomain` 指定したマネージメソッドを実行する管理対象をホストで制御できるように <xref:System.AppDomain> します。</span><span class="sxs-lookup"><span data-stu-id="ae998-129">`ExecuteInAppDomain` allows the host to exercise control over which managed <xref:System.AppDomain> the specified managed method should be executed in.</span></span> <span data-ttu-id="ae998-130">アプリケーションドメインの識別子の値を取得できます。これは、 <xref:System.AppDomain.Id%2A> [GetCurrentAppDomainId メソッド](iclrruntimehost-getcurrentappdomainid-method.md)を呼び出すことによって、プロパティの値に対応します。</span><span class="sxs-lookup"><span data-stu-id="ae998-130">You can get the value of an application domain's identifier, which corresponds to the value of the <xref:System.AppDomain.Id%2A> property, by calling [GetCurrentAppDomainId Method](iclrruntimehost-getcurrentappdomainid-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae998-131">要件</span><span class="sxs-lookup"><span data-stu-id="ae998-131">Requirements</span></span>  

 <span data-ttu-id="ae998-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae998-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae998-133">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="ae998-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae998-134">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ae998-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae998-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae998-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae998-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae998-136">See also</span></span>

- [<span data-ttu-id="ae998-137">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae998-137">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
