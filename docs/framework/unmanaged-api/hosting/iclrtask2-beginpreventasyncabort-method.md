---
title: ICLRTask2::BeginPreventAsyncAbort メソッド
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
ms.openlocfilehash: daf211fcc496f63ef71575abf6a28655004db264
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720244"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a><span data-ttu-id="0806f-102">ICLRTask2::BeginPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="0806f-102">ICLRTask2::BeginPreventAsyncAbort Method</span></span>

<span data-ttu-id="0806f-103">現在のスレッドでのスレッドの中止要求から、新しいスレッド中止要求を遅延します。</span><span class="sxs-lookup"><span data-stu-id="0806f-103">Delays new thread abort requests from resulting in thread aborts on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0806f-104">構文</span><span class="sxs-lookup"><span data-stu-id="0806f-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0806f-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="0806f-105">Return Value</span></span>  

 <span data-ttu-id="0806f-106">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="0806f-106">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0806f-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0806f-107">HRESULT</span></span>|<span data-ttu-id="0806f-108">説明</span><span class="sxs-lookup"><span data-stu-id="0806f-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0806f-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="0806f-109">S_OK</span></span>|<span data-ttu-id="0806f-110">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="0806f-110">The method completed successfully.</span></span>|  
|<span data-ttu-id="0806f-111">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="0806f-111">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="0806f-112">メソッドは、現在のスレッドではないスレッドで呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="0806f-112">The method was called on a thread which is not the current thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0806f-113">注釈</span><span class="sxs-lookup"><span data-stu-id="0806f-113">Remarks</span></span>  

 <span data-ttu-id="0806f-114">このメソッドを呼び出すと、現在のスレッドの遅延スレッド中止カウンターが1つ増加します。</span><span class="sxs-lookup"><span data-stu-id="0806f-114">Calling this method increments the delay-thread-abort counter for the current thread by one.</span></span>  
  
 <span data-ttu-id="0806f-115">`BeginPreventAsyncAbort`と[ICLRTask2:: EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md)の呼び出しは入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="0806f-115">Calls to `BeginPreventAsyncAbort` and [ICLRTask2::EndPreventAsyncAbort](iclrtask2-endpreventasyncabort-method.md) can be nested.</span></span> <span data-ttu-id="0806f-116">カウンターがゼロより大きい限り、現在のスレッドのスレッド中止は遅延されます。</span><span class="sxs-lookup"><span data-stu-id="0806f-116">As long as the counter is greater than zero, thread aborts for the current thread are delayed.</span></span> <span data-ttu-id="0806f-117">この呼び出しがメソッドの呼び出しとペアリングされていない場合 `EndPreventAsyncAbort` 、スレッドの中止が現在のスレッドに配信されない状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0806f-117">If this call is not paired with a call to the `EndPreventAsyncAbort` method, it is possible to reach a state in which thread aborts cannot be delivered to the current thread.</span></span>  
  
 <span data-ttu-id="0806f-118">遅延は、それ自体を中止するスレッドには適用されません。</span><span class="sxs-lookup"><span data-stu-id="0806f-118">The delay is not honored for a thread that aborts itself.</span></span>  
  
 <span data-ttu-id="0806f-119">この機能によって公開されている機能は、仮想マシン (VM) によって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0806f-119">The functionality that is exposed by this feature is used internally by the virtual machine (VM).</span></span> <span data-ttu-id="0806f-120">これらの方法を誤用すると、VM で特定できない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0806f-120">Misuse of these methods may cause unspecified behavior in the VM.</span></span> <span data-ttu-id="0806f-121">たとえば、最初に `EndPreventAsyncAbort` を呼び出しないでを呼び出す `BeginPreventAsyncAbort` と、VM で以前にインクリメントしたカウンターが0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0806f-121">For example, calling `EndPreventAsyncAbort` without first calling `BeginPreventAsyncAbort` could set the counter to zero when the VM has previously incremented it.</span></span> <span data-ttu-id="0806f-122">同様に、内部カウンターのオーバーフローはチェックされません。</span><span class="sxs-lookup"><span data-stu-id="0806f-122">Similarly, the internal counter is not checked for overflow.</span></span> <span data-ttu-id="0806f-123">ホストと VM の両方によってインクリメントされるために整数の制限を超えた場合、結果として得られる動作は指定されません。</span><span class="sxs-lookup"><span data-stu-id="0806f-123">If it exceeds its integral limit because it is incremented by both the host and the VM, the resulting behavior is unspecified.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0806f-124">要件</span><span class="sxs-lookup"><span data-stu-id="0806f-124">Requirements</span></span>  

 <span data-ttu-id="0806f-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0806f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0806f-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0806f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0806f-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0806f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0806f-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0806f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0806f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="0806f-129">See also</span></span>

- [<span data-ttu-id="0806f-130">EndPreventAsyncAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="0806f-130">EndPreventAsyncAbort Method</span></span>](iclrtask2-endpreventasyncabort-method.md)
- [<span data-ttu-id="0806f-131">ICLRTask2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0806f-131">ICLRTask2 Interface</span></span>](iclrtask2-interface.md)
- [<span data-ttu-id="0806f-132">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0806f-132">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="0806f-133">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0806f-133">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="0806f-134">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0806f-134">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="0806f-135">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0806f-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
