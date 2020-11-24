---
title: ICorProfilerCallback::ObjectAllocated メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674344"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="2bc51-102">ICorProfilerCallback::ObjectAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="2bc51-102">ICorProfilerCallback::ObjectAllocated Method</span></span>

<span data-ttu-id="2bc51-103">ヒープ内のメモリがオブジェクトに割り当てられたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2bc51-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc51-104">構文</span><span class="sxs-lookup"><span data-stu-id="2bc51-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bc51-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2bc51-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="2bc51-106">からメモリが割り当てられたオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="2bc51-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="2bc51-107">からオブジェクトがインスタンスとして使用されているクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="2bc51-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc51-108">注釈</span><span class="sxs-lookup"><span data-stu-id="2bc51-108">Remarks</span></span>  

 <span data-ttu-id="2bc51-109">メソッドは、 `ObjectedAllocated` スタックまたはアンマネージメモリからの割り当てのために呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="2bc51-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="2bc51-110">パラメーターは、 `classId` まだ読み込まれていないマネージコード内のクラスを参照できます。</span><span class="sxs-lookup"><span data-stu-id="2bc51-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="2bc51-111">プロファイラーは、コールバックの直後に、そのクラスのクラス読み込みコールバックを受け取り `ObjectAllocated` ます。</span><span class="sxs-lookup"><span data-stu-id="2bc51-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc51-112">要件</span><span class="sxs-lookup"><span data-stu-id="2bc51-112">Requirements</span></span>  

 <span data-ttu-id="2bc51-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2bc51-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc51-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2bc51-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2bc51-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bc51-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bc51-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bc51-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc51-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bc51-117">See also</span></span>

- [<span data-ttu-id="2bc51-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bc51-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2bc51-119">ClassLoadStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="2bc51-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="2bc51-120">ClassLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="2bc51-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
