---
title: ICLRIoCompletionManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: e23675351e1fd0de510243c9ee8b3a6dd6f29cec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714121"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="17ed0-102">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17ed0-102">ICLRIoCompletionManager Interface</span></span>

<span data-ttu-id="17ed0-103">ホストが、指定された i/o 要求のステータスの共通言語ランタイム (CLR) に通知するためのコールバックメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="17ed0-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17ed0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="17ed0-104">Methods</span></span>  
  
|<span data-ttu-id="17ed0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="17ed0-105">Method</span></span>|<span data-ttu-id="17ed0-106">説明</span><span class="sxs-lookup"><span data-stu-id="17ed0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17ed0-107">OnComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="17ed0-107">OnComplete Method</span></span>](iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="17ed0-108">[Ihohooの](ihostiocompletionmanager-bind-method.md)呼び出しを使用して作成された i/o 要求の状態を CLR に通知します:: Bind メソッド。</span><span class="sxs-lookup"><span data-stu-id="17ed0-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17ed0-109">注釈</span><span class="sxs-lookup"><span data-stu-id="17ed0-109">Remarks</span></span>  

 <span data-ttu-id="17ed0-110">ホストは、 [Ihohoocompletion manager](ihostiocompletionmanager-interface.md) インターフェイスを使用して i/o 完了の抽象化を実装します。</span><span class="sxs-lookup"><span data-stu-id="17ed0-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="17ed0-111">CLR はこのインターフェイスを介して i/o 要求を行い、ホストはインターフェイスを使用して、そのような要求の結果をランタイムに通知し `ICLRIoCompletionManager` ます。</span><span class="sxs-lookup"><span data-stu-id="17ed0-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17ed0-112">要件</span><span class="sxs-lookup"><span data-stu-id="17ed0-112">Requirements</span></span>  

 <span data-ttu-id="17ed0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17ed0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17ed0-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="17ed0-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17ed0-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="17ed0-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17ed0-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17ed0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ed0-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="17ed0-117">See also</span></span>

- [<span data-ttu-id="17ed0-118">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17ed0-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="17ed0-119">IHostThreadPoolManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17ed0-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="17ed0-120">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17ed0-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
