---
title: ICLRRuntimeHost::GetCurrentAppDomainId メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 2b1c9e99604664c99960a0741de6eae6b38fe963
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728850"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="6c77e-102">ICLRRuntimeHost::GetCurrentAppDomainId メソッド</span><span class="sxs-lookup"><span data-stu-id="6c77e-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>

<span data-ttu-id="6c77e-103">現在実行中のの数値識別子を取得し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="6c77e-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c77e-104">構文</span><span class="sxs-lookup"><span data-stu-id="6c77e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c77e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6c77e-105">Parameters</span></span>  

 `pdwAppDomainId`  
 <span data-ttu-id="6c77e-106">入出力現在実行中のの数値識別子 <xref:System.AppDomain> 。</span><span class="sxs-lookup"><span data-stu-id="6c77e-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c77e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="6c77e-107">Return Value</span></span>  
  
|<span data-ttu-id="6c77e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c77e-108">HRESULT</span></span>|<span data-ttu-id="6c77e-109">説明</span><span class="sxs-lookup"><span data-stu-id="6c77e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c77e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c77e-110">S_OK</span></span>|<span data-ttu-id="6c77e-111">`GetCurrentAppDomainId` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="6c77e-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="6c77e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c77e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c77e-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6c77e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c77e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c77e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c77e-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="6c77e-115">The call timed out.</span></span>|  
|<span data-ttu-id="6c77e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c77e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c77e-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="6c77e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c77e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c77e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c77e-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="6c77e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c77e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c77e-120">E_FAIL</span></span>|<span data-ttu-id="6c77e-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6c77e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c77e-122">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6c77e-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c77e-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6c77e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c77e-124">注釈</span><span class="sxs-lookup"><span data-stu-id="6c77e-124">Remarks</span></span>  

 <span data-ttu-id="6c77e-125">`pdwAppDomainId`パラメーターは <xref:System.AppDomain.Id%2A> 、 <xref:System.AppDomain> 現在のスレッドが実行されているのプロパティの値に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6c77e-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c77e-126">要件</span><span class="sxs-lookup"><span data-stu-id="6c77e-126">Requirements</span></span>  

 <span data-ttu-id="6c77e-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c77e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c77e-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6c77e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c77e-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6c77e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c77e-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c77e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c77e-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c77e-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="6c77e-132">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c77e-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
