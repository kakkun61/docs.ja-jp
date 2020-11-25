---
title: ICorProfilerCallback::ThreadCreated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 72b074d1794a6039060cbd84aabb0bc0155c154e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717271"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="adcfc-102">ICorProfilerCallback::ThreadCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="adcfc-102">ICorProfilerCallback::ThreadCreated Method</span></span>

<span data-ttu-id="adcfc-103">スレッドが作成されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="adcfc-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adcfc-104">構文</span><span class="sxs-lookup"><span data-stu-id="adcfc-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="adcfc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="adcfc-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="adcfc-106">から作成されたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="adcfc-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adcfc-107">注釈</span><span class="sxs-lookup"><span data-stu-id="adcfc-107">Remarks</span></span>  

 <span data-ttu-id="adcfc-108">この `threadId` 値はすぐに有効です。</span><span class="sxs-lookup"><span data-stu-id="adcfc-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adcfc-109">要件</span><span class="sxs-lookup"><span data-stu-id="adcfc-109">Requirements</span></span>  

 <span data-ttu-id="adcfc-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adcfc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adcfc-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="adcfc-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="adcfc-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="adcfc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="adcfc-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adcfc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adcfc-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="adcfc-114">See also</span></span>

- [<span data-ttu-id="adcfc-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="adcfc-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="adcfc-116">ThreadDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="adcfc-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
