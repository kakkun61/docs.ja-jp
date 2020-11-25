---
title: IHostThreadPoolManager インターフェイス
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: b6625b0ef4dc3de4067514a0b39849c7a958d5c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730761"
---
# <a name="ihostthreadpoolmanager-interface"></a><span data-ttu-id="7e5fb-102">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e5fb-102">IHostThreadPoolManager Interface</span></span>

<span data-ttu-id="7e5fb-103">共通言語ランタイム (CLR) がスレッドプールを構成し、作業項目をスレッドプールにキューするようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-103">Provides methods that enable the common language runtime (CLR) to configure the thread pool and to queue work items to the thread pool.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7e5fb-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-104">Methods</span></span>  
  
|<span data-ttu-id="7e5fb-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-105">Method</span></span>|<span data-ttu-id="7e5fb-106">説明</span><span class="sxs-lookup"><span data-stu-id="7e5fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7e5fb-107">GetAvailableThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-107">GetAvailableThreads Method</span></span>](ihostthreadpoolmanager-getavailablethreads-method.md)|<span data-ttu-id="7e5fb-108">現在作業項目を処理していないスレッドプール内のスレッドの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-108">Gets the number of threads in the thread pool that are not currently processing work items.</span></span>|  
|[<span data-ttu-id="7e5fb-109">GetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-109">GetMaxThreads Method</span></span>](ihostthreadpoolmanager-getmaxthreads-method.md)|<span data-ttu-id="7e5fb-110">ホストがスレッドプール内で同時に保持するスレッドの最大数を取得します。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-110">Gets the maximum number of threads that the host maintains concurrently in the thread pool.</span></span>|  
|[<span data-ttu-id="7e5fb-111">GetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-111">GetMinThreads Method</span></span>](ihostthreadpoolmanager-getminthreads-method.md)|<span data-ttu-id="7e5fb-112">要求を処理するためにホストが保持するアイドル状態のスレッドの最小数を取得します。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-112">Gets the minimum number of idle threads that the host maintains in anticipation of requests.</span></span>|  
|[<span data-ttu-id="7e5fb-113">QueueUserWorkItem メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-113">QueueUserWorkItem Method</span></span>](ihostthreadpoolmanager-queueuserworkitem-method.md)|<span data-ttu-id="7e5fb-114">実行する関数をキューに配置し、関数によって使用されるデータを格納しているオブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-114">Queues a function for execution, and provides an object containing data to be used by the function.</span></span>|  
|[<span data-ttu-id="7e5fb-115">SetMaxThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-115">SetMaxThreads Method</span></span>](ihostthreadpoolmanager-setmaxthreads-method.md)|<span data-ttu-id="7e5fb-116">ホストがスレッドプールで保持できるスレッドの最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-116">Sets the maximum number of threads that the host can maintain in the thread pool.</span></span>|  
|[<span data-ttu-id="7e5fb-117">SetMinThreads メソッド</span><span class="sxs-lookup"><span data-stu-id="7e5fb-117">SetMinThreads Method</span></span>](ihostthreadpoolmanager-setminthreads-method.md)|<span data-ttu-id="7e5fb-118">ホストが要求を見越して保持する必要があるアイドル状態のスレッドの最小数を設定します。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-118">Sets the minimum number of idle threads that the host must maintain in anticipation of requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e5fb-119">注釈</span><span class="sxs-lookup"><span data-stu-id="7e5fb-119">Remarks</span></span>  

 <span data-ttu-id="7e5fb-120">ホストは、 `SetMaxThreads` メソッドおよびメソッドの呼び出しで指定された値を使用して、スレッドプールを構成する必要はありません `SetMinThreads` 。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-120">The host is not required to configure the thread pool by using the values specified in calls to the `SetMaxThreads` and `SetMinThreads` methods.</span></span> <span data-ttu-id="7e5fb-121">この場合、ホストは、これらのメソッドから E_NOTIMPL の HRESULT 値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-121">In this case, the host should return an HRESULT value of E_NOTIMPL from these methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e5fb-122">要件</span><span class="sxs-lookup"><span data-stu-id="7e5fb-122">Requirements</span></span>  

 <span data-ttu-id="7e5fb-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e5fb-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e5fb-124">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7e5fb-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e5fb-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7e5fb-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e5fb-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e5fb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e5fb-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e5fb-127">See also</span></span>

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [<span data-ttu-id="7e5fb-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e5fb-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
