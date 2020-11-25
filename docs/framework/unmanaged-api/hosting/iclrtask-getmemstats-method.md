---
title: ICLRTask::GetMemStats メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask.GetMemStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::GetMemStats
helpviewer_keywords:
- ICLRTask::GetMemStats method [.NET Framework hosting]
- GetMemStats method [.NET Framework hosting]
ms.assetid: c9e07657-1682-4c30-a336-f8658ff1a125
topic_type:
- apiref
ms.openlocfilehash: 5d57bc742ebcba00f9fbe569a4be27b82a5f8055
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726510"
---
# <a name="iclrtaskgetmemstats-method"></a><span data-ttu-id="9ff92-102">ICLRTask::GetMemStats メソッド</span><span class="sxs-lookup"><span data-stu-id="9ff92-102">ICLRTask::GetMemStats Method</span></span>

<span data-ttu-id="9ff92-103">現在の [ICLRTask](iclrtask-interface.md) インスタンスが表すタスクに関連する統計的メモリ使用量情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="9ff92-103">Gets statistical memory usage information related to the task that the current [ICLRTask](iclrtask-interface.md) instance represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ff92-104">構文</span><span class="sxs-lookup"><span data-stu-id="9ff92-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemStats (  
    [out] COR_GC_THREAD_STATS *pMemUsage  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ff92-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9ff92-105">Parameters</span></span>  

 `pMemUsage`  
 <span data-ttu-id="9ff92-106">入出力割り当てられたバイト数を含む、タスクのメモリ使用量に関する詳細を格納している [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9ff92-106">[out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) instance that contains details about the memory usage of the task, including the number of bytes allocated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ff92-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="9ff92-107">Return Value</span></span>  
  
|<span data-ttu-id="9ff92-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ff92-108">HRESULT</span></span>|<span data-ttu-id="9ff92-109">説明</span><span class="sxs-lookup"><span data-stu-id="9ff92-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ff92-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ff92-110">S_OK</span></span>|<span data-ttu-id="9ff92-111">`GetMemStats` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="9ff92-111">`GetMemStats` returned successfully.</span></span>|  
|<span data-ttu-id="9ff92-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ff92-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ff92-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="9ff92-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ff92-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ff92-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ff92-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="9ff92-115">The call timed out.</span></span>|  
|<span data-ttu-id="9ff92-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ff92-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ff92-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="9ff92-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ff92-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ff92-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ff92-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="9ff92-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ff92-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ff92-120">E_FAIL</span></span>|<span data-ttu-id="9ff92-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9ff92-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ff92-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="9ff92-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ff92-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="9ff92-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ff92-124">要件</span><span class="sxs-lookup"><span data-stu-id="9ff92-124">Requirements</span></span>  

 <span data-ttu-id="9ff92-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ff92-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ff92-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9ff92-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ff92-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9ff92-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ff92-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ff92-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ff92-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ff92-129">See also</span></span>

- [<span data-ttu-id="9ff92-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ff92-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9ff92-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ff92-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9ff92-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ff92-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9ff92-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9ff92-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
