---
title: ICorProfilerInfo2::GetObjectGeneration メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
ms.openlocfilehash: 4ba404692bef84c0522a799c61f07eac341eaab4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703851"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="8259a-102">ICorProfilerInfo2::GetObjectGeneration メソッド</span><span class="sxs-lookup"><span data-stu-id="8259a-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>

<span data-ttu-id="8259a-103">指定されたオブジェクトを格納しているヒープのセグメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="8259a-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8259a-104">構文</span><span class="sxs-lookup"><span data-stu-id="8259a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8259a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8259a-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="8259a-106">からオブジェクトの ID です。</span><span class="sxs-lookup"><span data-stu-id="8259a-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="8259a-107">入出力ガベージコレクション中のジェネレーション内のメモリの範囲 (つまり、ブロック) を記述する [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8259a-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="8259a-108">この範囲には、指定されたオブジェクトが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8259a-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8259a-109">注釈</span><span class="sxs-lookup"><span data-stu-id="8259a-109">Remarks</span></span>  

 <span data-ttu-id="8259a-110">`GetObjectGeneration`ガベージコレクションが実行されていない場合は、任意のプロファイラーコールバックからメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8259a-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="8259a-111">つまり、 [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) と [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)の間で発生するものを除き、任意のコールバックから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8259a-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8259a-112">要件</span><span class="sxs-lookup"><span data-stu-id="8259a-112">Requirements</span></span>  

 <span data-ttu-id="8259a-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8259a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8259a-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8259a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8259a-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8259a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8259a-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8259a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8259a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8259a-117">See also</span></span>

- [<span data-ttu-id="8259a-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8259a-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8259a-119">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8259a-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
