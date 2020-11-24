---
title: COR_PRF_GC_GENERATION_RANGE 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: a0ee2c9ce38272caef4960bfe5949c11083c12dd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674932"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="74fd1-102">COR_PRF_GC_GENERATION_RANGE 構造体</span><span class="sxs-lookup"><span data-stu-id="74fd1-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>

<span data-ttu-id="74fd1-103">ガーベッジ コレクションを実行中のメモリ範囲 (ブロック) を説明します。</span><span class="sxs-lookup"><span data-stu-id="74fd1-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74fd1-104">構文</span><span class="sxs-lookup"><span data-stu-id="74fd1-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="74fd1-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="74fd1-105">Members</span></span>  
  
|<span data-ttu-id="74fd1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="74fd1-106">Member</span></span>|<span data-ttu-id="74fd1-107">説明</span><span class="sxs-lookup"><span data-stu-id="74fd1-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="74fd1-108">メモリブロックが属するジェネレーションを指定する [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) 列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="74fd1-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="74fd1-109">メモリブロックの開始位置を指定するオブジェクトの ID。</span><span class="sxs-lookup"><span data-stu-id="74fd1-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="74fd1-110">メモリブロックの使用されている部分のサイズ (つまり、ブロック内で使用されているメモリの量) を指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="74fd1-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="74fd1-111">メモリブロックのサイズ (つまり、ブロックに予約されているメモリの量) を指定する整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="74fd1-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74fd1-112">注釈</span><span class="sxs-lookup"><span data-stu-id="74fd1-112">Remarks</span></span>  

 <span data-ttu-id="74fd1-113">値は、 `rangeLength` [ICorProfilerInfo2:: GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) または [ICorProfilerInfo2:: getobjectgeneration](icorprofilerinfo2-getobjectgeneration-method.md)(両方とも構造体を使用する) `COR_PRF_GC_GENERATION_RANGE` が [ICorProfilerCallback2:: GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) メソッドまたは [ICorProfilerCallback2:: GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) メソッドから呼び出された場合にのみ正確であることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="74fd1-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74fd1-114">要件</span><span class="sxs-lookup"><span data-stu-id="74fd1-114">Requirements</span></span>  

 <span data-ttu-id="74fd1-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74fd1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74fd1-116">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="74fd1-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="74fd1-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74fd1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74fd1-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74fd1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74fd1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="74fd1-119">See also</span></span>

- [<span data-ttu-id="74fd1-120">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="74fd1-120">Profiling Structures</span></span>](profiling-structures.md)
