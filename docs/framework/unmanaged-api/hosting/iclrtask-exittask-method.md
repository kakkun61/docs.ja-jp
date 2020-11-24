---
title: ICLRTask::ExitTask メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.ExitTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::ExitTask
helpviewer_keywords:
- ExitTask method [.NET Framework hosting]
- ICLRTask::ExitTask method [.NET Framework hosting]
ms.assetid: 746c85a6-4b33-4f72-a2e9-379fdf2e96af
topic_type:
- apiref
ms.openlocfilehash: bcd1cac47e4b59cc47c95145f0ccf60c92ea54fe
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690839"
---
# <a name="iclrtaskexittask-method"></a><span data-ttu-id="51d8a-102">ICLRTask::ExitTask メソッド</span><span class="sxs-lookup"><span data-stu-id="51d8a-102">ICLRTask::ExitTask Method</span></span>

<span data-ttu-id="51d8a-103">現在の [ICLRTask](iclrtask-interface.md) インスタンスによって表されるタスクが終了していることを共通言語ランタイム (CLR) に通知し、タスクを正常にシャットダウンすることを試みます。</span><span class="sxs-lookup"><span data-stu-id="51d8a-103">Notifies the common language runtime (CLR) that the task represented by the current [ICLRTask](iclrtask-interface.md) instance is ending, and attempts to shut the task down gracefully.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51d8a-104">構文</span><span class="sxs-lookup"><span data-stu-id="51d8a-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitTask ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="51d8a-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="51d8a-105">Return Value</span></span>  
  
|<span data-ttu-id="51d8a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="51d8a-106">HRESULT</span></span>|<span data-ttu-id="51d8a-107">説明</span><span class="sxs-lookup"><span data-stu-id="51d8a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51d8a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="51d8a-108">S_OK</span></span>|<span data-ttu-id="51d8a-109">`ExitTask` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="51d8a-109">`ExitTask` returned successfully.</span></span>|  
|<span data-ttu-id="51d8a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="51d8a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="51d8a-111">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="51d8a-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="51d8a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="51d8a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="51d8a-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="51d8a-113">The call timed out.</span></span>|  
|<span data-ttu-id="51d8a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="51d8a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="51d8a-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="51d8a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="51d8a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="51d8a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="51d8a-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="51d8a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="51d8a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="51d8a-118">E_FAIL</span></span>|<span data-ttu-id="51d8a-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="51d8a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="51d8a-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="51d8a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="51d8a-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="51d8a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51d8a-122">注釈</span><span class="sxs-lookup"><span data-stu-id="51d8a-122">Remarks</span></span>  

 <span data-ttu-id="51d8a-123">`ExitTask` アンマネージタイプライブラリからスレッドをデタッチするのと同様の方法で、タスクのクリーンシャットダウンを試みます。</span><span class="sxs-lookup"><span data-stu-id="51d8a-123">`ExitTask` attempts a clean shutdown of a task, in a manner analogous to detaching a thread from an unmanaged type library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51d8a-124">要件</span><span class="sxs-lookup"><span data-stu-id="51d8a-124">Requirements</span></span>  

 <span data-ttu-id="51d8a-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51d8a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51d8a-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="51d8a-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="51d8a-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="51d8a-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51d8a-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51d8a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d8a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="51d8a-129">See also</span></span>

- [<span data-ttu-id="51d8a-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51d8a-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="51d8a-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51d8a-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="51d8a-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51d8a-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="51d8a-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51d8a-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
