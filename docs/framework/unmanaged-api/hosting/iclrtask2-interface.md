---
title: ICLRTask2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
ms.openlocfilehash: 9332b3462ba389783a113d173e32850d40427ce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720231"
---
# <a name="iclrtask2-interface"></a><span data-ttu-id="9a94c-102">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a94c-102">ICLRTask2 Interface</span></span>

<span data-ttu-id="9a94c-103">には、 [ICLRTask](iclrtask-interface.md) インターフェイスのすべての機能が用意されています。また、には、現在のスレッドでスレッドの中止を遅延させることができるメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9a94c-103">Provides all the functionality of the [ICLRTask](iclrtask-interface.md) interface; in addition, provides methods that allow thread aborts to be delayed on the current thread.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a94c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="9a94c-104">Methods</span></span>  
  
|<span data-ttu-id="9a94c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9a94c-105">Method</span></span>|<span data-ttu-id="9a94c-106">説明</span><span class="sxs-lookup"><span data-stu-id="9a94c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a94c-107">BeginPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="9a94c-107">BeginPreventAsyncAbort Method</span></span>](iclrtask2-beginpreventasyncabort-method.md)|<span data-ttu-id="9a94c-108">現在のスレッドの新しいスレッド中止要求を遅延します。</span><span class="sxs-lookup"><span data-stu-id="9a94c-108">Delays new thread abort requests on the current thread.</span></span>|  
|[<span data-ttu-id="9a94c-109">EndPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="9a94c-109">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)|<span data-ttu-id="9a94c-110">新しいまたは保留中のスレッド中止要求に対して、現在のスレッドでのスレッドの中止を許可します。</span><span class="sxs-lookup"><span data-stu-id="9a94c-110">Allows new or pending thread abort requests to result in thread aborts on the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a94c-111">注釈</span><span class="sxs-lookup"><span data-stu-id="9a94c-111">Remarks</span></span>  

 <span data-ttu-id="9a94c-112">インターフェイスは、 `ICLRTask2` インターフェイスを継承 `ICLRTask` し、ホストがスレッドの中止を遅らせて、失敗しないコードの領域を保護できるようにするメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="9a94c-112">The `ICLRTask2` interface inherits the `ICLRTask` interface and adds methods that allow the host to delay thread aborts, to protect a region of code that must not fail.</span></span> <span data-ttu-id="9a94c-113">を呼び出す `BeginPreventAsyncAbort` と、現在のスレッドの遅延スレッド中止カウンターがインクリメントされ、を呼び出すと、 `EndPreventAsyncAbort` そのカウンターがデクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="9a94c-113">Calling `BeginPreventAsyncAbort` increments the delay-thread-abort counter for the current thread, and calling `EndPreventAsyncAbort` decrements it.</span></span> <span data-ttu-id="9a94c-114">およびへの呼び出しは入れ子にする `BeginPreventAsyncAbort` `EndPreventAsyncAbort` ことができます。</span><span class="sxs-lookup"><span data-stu-id="9a94c-114">Calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` can be nested.</span></span> <span data-ttu-id="9a94c-115">カウンターがゼロより大きい限り、現在のスレッドのスレッド中止は遅延されます。</span><span class="sxs-lookup"><span data-stu-id="9a94c-115">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span>  
  
 <span data-ttu-id="9a94c-116">との呼び出し `BeginPreventAsyncAbort` がペアになって `EndPreventAsyncAbort` いない場合、現在のスレッドにスレッド中止を配信できない状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a94c-116">If calls to `BeginPreventAsyncAbort` and `EndPreventAsyncAbort` are not paired, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="9a94c-117">遅延は、それ自体を中止するスレッドには適用されません。</span><span class="sxs-lookup"><span data-stu-id="9a94c-117">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="9a94c-118">この機能によって公開されている機能は、仮想マシン (VM) によって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a94c-118">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="9a94c-119">これらの方法を誤用すると、VM で特定できない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9a94c-119">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="9a94c-120">たとえば、最初に `EndPreventAsyncAbort` を呼び出しないでを呼び出す `BeginPreventAsyncAbort` と、VM で以前にインクリメントしたカウンターが0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9a94c-120">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="9a94c-121">同様に、内部カウンターのオーバーフローはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="9a94c-121">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="9a94c-122">ホストと VM の両方によってインクリメントされるために整数の制限を超えた場合、結果として得られる動作は指定されません。</span><span class="sxs-lookup"><span data-stu-id="9a94c-122">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
 <span data-ttu-id="9a94c-123">から継承されたメンバー `ICLRTask` と、このインターフェイスの他の用途については、「 [ICLRTask](iclrtask-interface.md) インターフェイス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a94c-123">For information about members inherited from `ICLRTask` and about the other uses of this interface, see the [ICLRTask](iclrtask-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a94c-124">要件</span><span class="sxs-lookup"><span data-stu-id="9a94c-124">Requirements</span></span>  

 <span data-ttu-id="9a94c-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a94c-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a94c-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9a94c-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a94c-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="9a94c-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a94c-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a94c-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a94c-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="9a94c-129">See also</span></span>

- [<span data-ttu-id="9a94c-130">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a94c-130">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9a94c-131">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a94c-131">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9a94c-132">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a94c-132">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9a94c-133">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a94c-133">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="9a94c-134">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9a94c-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
