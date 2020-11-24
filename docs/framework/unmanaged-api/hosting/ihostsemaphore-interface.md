---
title: IHostSemaphore インターフェイス
ms.date: 03/30/2017
api_name:
- IHostSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore
helpviewer_keywords:
- IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type:
- apiref
ms.openlocfilehash: cccbf9a28b16ffee14b3fd3ec43c376109d6ccec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683057"
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="8870c-102">IHostSemaphore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8870c-102">IHostSemaphore Interface</span></span>

<span data-ttu-id="8870c-103">スレッド処理のためのセマフォのホストの実装を表します。</span><span class="sxs-lookup"><span data-stu-id="8870c-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8870c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8870c-104">Methods</span></span>  
  
|<span data-ttu-id="8870c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8870c-105">Method</span></span>|<span data-ttu-id="8870c-106">説明</span><span class="sxs-lookup"><span data-stu-id="8870c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8870c-107">ReleaseSemaphore メソッド</span><span class="sxs-lookup"><span data-stu-id="8870c-107">ReleaseSemaphore Method</span></span>](ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="8870c-108">現在のインスタンスの数を `IHostSemaphore` 指定された量だけ増やします。</span><span class="sxs-lookup"><span data-stu-id="8870c-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="8870c-109">Wait メソッド</span><span class="sxs-lookup"><span data-stu-id="8870c-109">Wait Method</span></span>](ihostsemaphore-wait-method.md)|<span data-ttu-id="8870c-110">現在の `IHostSemaphore` インスタンスが所有されるか、指定された時間が経過するまで待機するようにします。</span><span class="sxs-lookup"><span data-stu-id="8870c-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8870c-111">要件</span><span class="sxs-lookup"><span data-stu-id="8870c-111">Requirements</span></span>  

 <span data-ttu-id="8870c-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8870c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8870c-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8870c-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8870c-114">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8870c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8870c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8870c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8870c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="8870c-116">See also</span></span>

- [<span data-ttu-id="8870c-117">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8870c-117">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8870c-118">IHostAutoEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8870c-118">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8870c-119">IHostManualEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8870c-119">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="8870c-120">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8870c-120">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="8870c-121">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8870c-121">Hosting Interfaces</span></span>](hosting-interfaces.md)
