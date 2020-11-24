---
title: ICLRTask::RudeAbort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.RudeAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::RudeAbort
helpviewer_keywords:
- RudeAbort method, ICLRTask interface [.NET Framework hosting]
- ICLRTask::RudeAbort method [.NET Framework hosting]
ms.assetid: b5785468-fcd7-4cc3-8a5d-8796337b53fc
topic_type:
- apiref
ms.openlocfilehash: 5b0e2265810b00fe0760d4e25c0f9904a96d9f2a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691046"
---
# <a name="iclrtaskrudeabort-method"></a><span data-ttu-id="53653-102">ICLRTask::RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="53653-102">ICLRTask::RudeAbort Method</span></span>

<span data-ttu-id="53653-103">現在の [ICLRTask インターフェイス](iclrtask-interface.md) インスタンスによって表されるタスクをすぐに無条件で中止するように、共通言語ランタイム (CLR) に指示します。</span><span class="sxs-lookup"><span data-stu-id="53653-103">Instructs the common language runtime (CLR) to abort the task represented by the current [ICLRTask Interface](iclrtask-interface.md) instance immediately and unconditionally.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53653-104">構文</span><span class="sxs-lookup"><span data-stu-id="53653-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();
```  
  
## <a name="return-value"></a><span data-ttu-id="53653-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="53653-105">Return Value</span></span>  
  
|<span data-ttu-id="53653-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="53653-106">HRESULT</span></span>|<span data-ttu-id="53653-107">説明</span><span class="sxs-lookup"><span data-stu-id="53653-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="53653-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="53653-108">S_OK</span></span>|<span data-ttu-id="53653-109">`RudeAbort` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="53653-109">`RudeAbort` returned successfully.</span></span>|  
|<span data-ttu-id="53653-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="53653-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="53653-111">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="53653-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="53653-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="53653-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="53653-113">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="53653-113">The call timed out.</span></span>|  
|<span data-ttu-id="53653-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="53653-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="53653-115">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="53653-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="53653-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="53653-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="53653-117">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="53653-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="53653-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="53653-118">E_FAIL</span></span>|<span data-ttu-id="53653-119">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="53653-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="53653-120">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="53653-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="53653-121">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="53653-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53653-122">注釈</span><span class="sxs-lookup"><span data-stu-id="53653-122">Remarks</span></span>  

 <span data-ttu-id="53653-123">ホストは、 `RudeAbort` タスクをすぐに中止するためにを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="53653-123">A host calls `RudeAbort` to abort a task immediately.</span></span> <span data-ttu-id="53653-124">ファイナライザーと例外処理ルーチンは、必ずしも実行されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="53653-124">Finalizers and exception handling routines are not guaranteed to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53653-125">要件</span><span class="sxs-lookup"><span data-stu-id="53653-125">Requirements</span></span>  

 <span data-ttu-id="53653-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="53653-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53653-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="53653-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="53653-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="53653-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="53653-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53653-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53653-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="53653-130">See also</span></span>

- [<span data-ttu-id="53653-131">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53653-131">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="53653-132">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53653-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="53653-133">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53653-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="53653-134">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="53653-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
