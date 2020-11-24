---
title: ICLRTask::Abort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.Abort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::Abort
helpviewer_keywords:
- ICLRTask::Abort method [.NET Framework hosting]
- Abort method, ICLRTask interface [.NET Framework hosting]
ms.assetid: b3594b5f-2e41-4e36-9096-3586276a138c
topic_type:
- apiref
ms.openlocfilehash: aadbbb5fc6abd3829f14670e42149174f6ef238d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690851"
---
# <a name="iclrtaskabort-method"></a><span data-ttu-id="bcb6f-102">ICLRTask::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="bcb6f-102">ICLRTask::Abort Method</span></span>

<span data-ttu-id="bcb6f-103">現在の [ICLRTask](iclrtask-interface.md) インスタンスが表すタスクを共通言語ランタイム (CLR) が中止することを要求します。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-103">Requests that the common language runtime (CLR) abort the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcb6f-104">構文</span><span class="sxs-lookup"><span data-stu-id="bcb6f-104">Syntax</span></span>  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="bcb6f-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="bcb6f-105">Return Value</span></span>  
  
|<span data-ttu-id="bcb6f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bcb6f-106">HRESULT</span></span>|<span data-ttu-id="bcb6f-107">説明</span><span class="sxs-lookup"><span data-stu-id="bcb6f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bcb6f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="bcb6f-108">S_OK</span></span>|<span data-ttu-id="bcb6f-109">`Abort` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-109">`Abort` returned successfully.</span></span>|  
|<span data-ttu-id="bcb6f-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bcb6f-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bcb6f-111">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bcb6f-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bcb6f-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bcb6f-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-113">The call timed out.</span></span>|  
|<span data-ttu-id="bcb6f-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bcb6f-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bcb6f-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bcb6f-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bcb6f-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bcb6f-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bcb6f-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bcb6f-118">E_FAIL</span></span>|<span data-ttu-id="bcb6f-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bcb6f-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bcb6f-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcb6f-122">注釈</span><span class="sxs-lookup"><span data-stu-id="bcb6f-122">Remarks</span></span>  

 <span data-ttu-id="bcb6f-123">CLR は、 <xref:System.Threading.ThreadAbortException> ホストがを呼び出したときにを発生させ `Abort` ます。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-123">The CLR raises a <xref:System.Threading.ThreadAbortException> when the host calls `Abort`.</span></span> <span data-ttu-id="bcb6f-124">ファイナライザーや例外処理機構などのユーザーコードが実行されるのを待たずに、例外情報が初期化された直後に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-124">It returns immediately after the exception information is initialized, without waiting for user code, such as finalizers or exception handling mechanisms, to execute.</span></span> <span data-ttu-id="bcb6f-125">を呼び出すと、が `Abort` すぐに返されます。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-125">Calls to `Abort` thus return quickly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcb6f-126">要件</span><span class="sxs-lookup"><span data-stu-id="bcb6f-126">Requirements</span></span>  

 <span data-ttu-id="bcb6f-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcb6f-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcb6f-128">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bcb6f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcb6f-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bcb6f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcb6f-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcb6f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb6f-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="bcb6f-131">See also</span></span>

- [<span data-ttu-id="bcb6f-132">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bcb6f-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bcb6f-133">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bcb6f-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bcb6f-134">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bcb6f-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bcb6f-135">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bcb6f-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
