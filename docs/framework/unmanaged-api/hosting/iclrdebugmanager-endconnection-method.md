---
title: ICLRDebugManager::EndConnection メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: d6f22d6185f4063078463043a6ffd46e56289267
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719854"
---
# <a name="iclrdebugmanagerendconnection-method"></a><span data-ttu-id="67b68-102">ICLRDebugManager::EndConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="67b68-102">ICLRDebugManager::EndConnection Method</span></span>

<span data-ttu-id="67b68-103">タスクのリストと id とフレンドリ名の間の関連付けを削除します。</span><span class="sxs-lookup"><span data-stu-id="67b68-103">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b68-104">構文</span><span class="sxs-lookup"><span data-stu-id="67b68-104">Syntax</span></span>  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67b68-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="67b68-105">Parameters</span></span>  

 `dwConnectionId`  
 <span data-ttu-id="67b68-106">から接続のホスト固有の識別子と、関連付けられている共通言語ランタイム (CLR) タスクのリスト。</span><span class="sxs-lookup"><span data-stu-id="67b68-106">[in] The host-specific identifier for the connection and the associated list of common language runtime (CLR) tasks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67b68-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="67b68-107">Return Value</span></span>  
  
|<span data-ttu-id="67b68-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67b68-108">HRESULT</span></span>|<span data-ttu-id="67b68-109">説明</span><span class="sxs-lookup"><span data-stu-id="67b68-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67b68-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="67b68-110">S_OK</span></span>|<span data-ttu-id="67b68-111">`EndConnection` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="67b68-111">`EndConnection` returned successfully.</span></span>|  
|<span data-ttu-id="67b68-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="67b68-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="67b68-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="67b68-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="67b68-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="67b68-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="67b68-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="67b68-115">The call timed out.</span></span>|  
|<span data-ttu-id="67b68-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="67b68-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="67b68-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="67b68-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="67b68-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="67b68-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="67b68-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="67b68-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="67b68-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67b68-120">E_FAIL</span></span>|<span data-ttu-id="67b68-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="67b68-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="67b68-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="67b68-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="67b68-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="67b68-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="67b68-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="67b68-124">E_INVALIDARG</span></span>|<span data-ttu-id="67b68-125">[Beginconnection](iclrdebugmanager-beginconnection-method.md) がを使用して呼び出されていない `dwConnectionId` か、または `dwConnectionId` が0でした。</span><span class="sxs-lookup"><span data-stu-id="67b68-125">[BeginConnection](iclrdebugmanager-beginconnection-method.md) was never called using `dwConnectionId`, or `dwConnectionId` was zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67b68-126">注釈</span><span class="sxs-lookup"><span data-stu-id="67b68-126">Remarks</span></span>  

 <span data-ttu-id="67b68-127">[ICLRDebugManager](iclrdebugmanager-interface.md)には、、setconnectiontasks、およびの3つのメソッドが用意されており、 `BeginConnection` [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md) `EndConnection` タスクリストを識別子と表示名に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="67b68-127">[ICLRDebugManager](iclrdebugmanager-interface.md) provides three methods, `BeginConnection`, [SetConnectionTasks](iclrdebugmanager-setconnectiontasks-method.md), and `EndConnection`, for associating task lists with identifiers and friendly names.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="67b68-128">これら3つのメソッドは、一連のタスクごとに特定の順序で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="67b68-128">These three methods must be called in a specific order for each set of tasks.</span></span> <span data-ttu-id="67b68-129">`BeginConnection` は、新しい接続を確立するために最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="67b68-129">`BeginConnection` is called first to establish a new connection.</span></span> <span data-ttu-id="67b68-130">`SetConnectionTasks` は、その接続に関連する一連のタスクを提供するために、次に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="67b68-130">`SetConnectionTasks` is called next to provide the set of tasks to be associated with that connection.</span></span> <span data-ttu-id="67b68-131">`EndConnection` は、タスク一覧と識別子とフレンドリ名の間の関連付けを削除するために最後に呼び出されます。ただし、異なる接続の呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="67b68-131">`EndConnection` is called last to remove the association between the task list and the identifier and friendly name.However, calls for different connections can be nested.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b68-132">要件</span><span class="sxs-lookup"><span data-stu-id="67b68-132">Requirements</span></span>  

 <span data-ttu-id="67b68-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67b68-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67b68-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="67b68-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67b68-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="67b68-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67b68-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67b68-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b68-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="67b68-137">See also</span></span>

- [<span data-ttu-id="67b68-138">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67b68-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="67b68-139">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67b68-139">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="67b68-140">BeginConnection メソッド</span><span class="sxs-lookup"><span data-stu-id="67b68-140">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)
- [<span data-ttu-id="67b68-141">SetConnectionTasks メソッド</span><span class="sxs-lookup"><span data-stu-id="67b68-141">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)
- [<span data-ttu-id="67b68-142">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="67b68-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
