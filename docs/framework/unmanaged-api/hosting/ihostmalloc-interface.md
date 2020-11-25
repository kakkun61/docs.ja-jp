---
title: IHostMalloc インターフェイス
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
ms.openlocfilehash: 2530c7fcd63f81b566d6623a533bd8e2af084047
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702161"
---
# <a name="ihostmalloc-interface"></a><span data-ttu-id="b3102-102">IHostMalloc インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3102-102">IHostMalloc Interface</span></span>

<span data-ttu-id="b3102-103">共通言語ランタイム (CLR) がホストを介してヒープから細かい割り当てを要求できるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="b3102-103">Provides methods that allow the common language runtime (CLR) to request fine-grained allocations from the heap through the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3102-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b3102-104">Methods</span></span>  
  
|<span data-ttu-id="b3102-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b3102-105">Method</span></span>|<span data-ttu-id="b3102-106">説明</span><span class="sxs-lookup"><span data-stu-id="b3102-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3102-107">Alloc メソッド</span><span class="sxs-lookup"><span data-stu-id="b3102-107">Alloc Method</span></span>](ihostmalloc-alloc-method.md)|<span data-ttu-id="b3102-108">ホストがヒープから要求された量のメモリを割り当てることを要求します。</span><span class="sxs-lookup"><span data-stu-id="b3102-108">Requests that the host allocate the requested amount of memory from the heap.</span></span>|  
|[<span data-ttu-id="b3102-109">DebugAlloc メソッド</span><span class="sxs-lookup"><span data-stu-id="b3102-109">DebugAlloc Method</span></span>](ihostmalloc-debugalloc-method.md)|<span data-ttu-id="b3102-110">は、要求されたメモリ量をヒープから割り当て、さらにメモリが割り当てられた場所を追跡することをホストに要求します。</span><span class="sxs-lookup"><span data-stu-id="b3102-110">Requests that the host allocate the requested amount of memory from the heap, and additionally track where the memory was allocated.</span></span>|  
|[<span data-ttu-id="b3102-111">Free メソッド</span><span class="sxs-lookup"><span data-stu-id="b3102-111">Free Method</span></span>](ihostmalloc-free-method.md)|<span data-ttu-id="b3102-112">メソッドを使用して割り当てられたメモリを解放し `Alloc` ます。</span><span class="sxs-lookup"><span data-stu-id="b3102-112">Frees memory that was allocated by using the `Alloc` method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3102-113">注釈</span><span class="sxs-lookup"><span data-stu-id="b3102-113">Remarks</span></span>  

 <span data-ttu-id="b3102-114">CLR は、 `IHostMalloc` [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) メソッドを呼び出すことによって、インスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="b3102-114">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3102-115">要件</span><span class="sxs-lookup"><span data-stu-id="b3102-115">Requirements</span></span>  

 <span data-ttu-id="b3102-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3102-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3102-117">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="b3102-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3102-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b3102-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3102-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3102-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3102-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3102-120">See also</span></span>

- [<span data-ttu-id="b3102-121">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3102-121">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="b3102-122">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b3102-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
