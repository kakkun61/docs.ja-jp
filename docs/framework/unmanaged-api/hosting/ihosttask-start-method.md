---
title: IHostTask::Start メソッド
ms.date: 03/30/2017
api_name:
- IHostTask.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Start
helpviewer_keywords:
- IHostTask::Start method [.NET Framework hosting]
- Start method, IHostTask interface [.NET Framework hosting]
ms.assetid: b18742b0-d8c4-401c-ae89-e6eccdaa81d0
topic_type:
- apiref
ms.openlocfilehash: 4143c3d25dd5262a10b53708a249910cc79f5314
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720439"
---
# <a name="ihosttaskstart-method"></a><span data-ttu-id="a48a3-102">IHostTask::Start メソッド</span><span class="sxs-lookup"><span data-stu-id="a48a3-102">IHostTask::Start Method</span></span>

<span data-ttu-id="a48a3-103">現在の [IHostTask](ihosttask-interface.md) インスタンスによって表されているタスクを、中断されているからライブ状態 (コードを実行できる) に移動するようホストに要求します。</span><span class="sxs-lookup"><span data-stu-id="a48a3-103">Requests that the host move the task represented by the current [IHostTask](ihosttask-interface.md) instance from a suspended to a live state, in which code can be executed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a48a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="a48a3-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a48a3-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="a48a3-105">Return Value</span></span>  
  
|<span data-ttu-id="a48a3-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a48a3-106">HRESULT</span></span>|<span data-ttu-id="a48a3-107">説明</span><span class="sxs-lookup"><span data-stu-id="a48a3-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a48a3-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a48a3-108">S_OK</span></span>|<span data-ttu-id="a48a3-109">Start が正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="a48a3-109">Start returned successfully.</span></span>|  
|<span data-ttu-id="a48a3-110">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a48a3-110">E_FAIL</span></span>|<span data-ttu-id="a48a3-111">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a48a3-111">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a48a3-112">メソッドから E_FAIL が返された場合、そのプロセス内で共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a48a3-112">When a method returns E_FAIL, the common language runtime (CLR) is no longer usable within the process.</span></span> <span data-ttu-id="a48a3-113">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="a48a3-113">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a48a3-114">注釈</span><span class="sxs-lookup"><span data-stu-id="a48a3-114">Remarks</span></span>  

 <span data-ttu-id="a48a3-115">`Start` 重大なエラーが発生した場合を除き、は常に S_OK の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="a48a3-115">`Start` always returns an HRESULT value of S_OK, except in cases where a catastrophic failure has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a48a3-116">要件</span><span class="sxs-lookup"><span data-stu-id="a48a3-116">Requirements</span></span>  

 <span data-ttu-id="a48a3-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a48a3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a48a3-118">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="a48a3-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a48a3-119">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a48a3-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a48a3-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a48a3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48a3-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a48a3-121">See also</span></span>

- [<span data-ttu-id="a48a3-122">ICLRTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a48a3-122">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="a48a3-123">ICLRTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a48a3-123">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="a48a3-124">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a48a3-124">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="a48a3-125">IHostTaskManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a48a3-125">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
