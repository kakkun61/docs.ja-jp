---
title: ICLRDebugManager::IsDebuggerAttached メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: 71e11d7db3bd679e7972fb2f6ce098edc3399885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731021"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="e586f-102">ICLRDebugManager::IsDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="e586f-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>

<span data-ttu-id="e586f-103">デバッガーがプロセスにアタッチされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="e586f-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e586f-104">構文</span><span class="sxs-lookup"><span data-stu-id="e586f-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e586f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e586f-105">Parameters</span></span>  

 `pbAttached`  
 <span data-ttu-id="e586f-106">[出力] `true` デバッガーがプロセスにアタッチされている場合は、それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="e586f-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e586f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="e586f-107">Return Value</span></span>  
  
|<span data-ttu-id="e586f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e586f-108">HRESULT</span></span>|<span data-ttu-id="e586f-109">説明</span><span class="sxs-lookup"><span data-stu-id="e586f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e586f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e586f-110">S_OK</span></span>|<span data-ttu-id="e586f-111">`IsDebuggerAttached` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="e586f-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="e586f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e586f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e586f-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="e586f-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e586f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e586f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e586f-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="e586f-115">The call timed out.</span></span>|  
|<span data-ttu-id="e586f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e586f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e586f-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="e586f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e586f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e586f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e586f-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="e586f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e586f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e586f-120">E_FAIL</span></span>|<span data-ttu-id="e586f-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="e586f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e586f-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="e586f-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e586f-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="e586f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e586f-124">注釈</span><span class="sxs-lookup"><span data-stu-id="e586f-124">Remarks</span></span>  

 <span data-ttu-id="e586f-125">`IsDebuggerAttached` デバッガーがプロセスにアタッチされているかどうかを判断するために、ホストが CLR を照会できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e586f-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e586f-126">要件</span><span class="sxs-lookup"><span data-stu-id="e586f-126">Requirements</span></span>  

 <span data-ttu-id="e586f-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e586f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e586f-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e586f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e586f-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="e586f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e586f-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e586f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e586f-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="e586f-131">See also</span></span>

- [<span data-ttu-id="e586f-132">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e586f-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="e586f-133">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e586f-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="e586f-134">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e586f-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)
