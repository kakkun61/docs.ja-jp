---
title: ICorProfilerCallback::ObjectsAllocatedByClass メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
ms.openlocfilehash: 70d43d7526376c40d0f8358ebd65e4a00a41b969
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701668"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a><span data-ttu-id="2a59b-102">ICorProfilerCallback::ObjectsAllocatedByClass メソッド</span><span class="sxs-lookup"><span data-stu-id="2a59b-102">ICorProfilerCallback::ObjectsAllocatedByClass Method</span></span>

<span data-ttu-id="2a59b-103">最後のガベージコレクション以降に作成された、指定した各クラスのインスタンスの数をプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2a59b-103">Notifies the profiler about the number of instances of each specified class that have been created since the most recent garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a59b-104">構文</span><span class="sxs-lookup"><span data-stu-id="2a59b-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a59b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2a59b-105">Parameters</span></span>  

 `cClassCount`  
 <span data-ttu-id="2a59b-106">から `classIds` 配列と配列のサイズ `cObjects` 。</span><span class="sxs-lookup"><span data-stu-id="2a59b-106">[in] The size of the `classIds` and `cObjects` arrays.</span></span>  
  
 `classIds`  
 <span data-ttu-id="2a59b-107">からクラス Id の配列。各 ID は、1つ以上のインスタンスを持つクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2a59b-107">[in] An array of class IDs, where each ID specifies a class with one or more instances.</span></span>  
  
 `cObjects`  
 <span data-ttu-id="2a59b-108">から整数の配列。各整数は、配列内の対応するクラスのインスタンスの数を指定し `classIds` ます。</span><span class="sxs-lookup"><span data-stu-id="2a59b-108">[in] An array of integers, where each integer specifies the number of instances for the corresponding class in the `classIds` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a59b-109">注釈</span><span class="sxs-lookup"><span data-stu-id="2a59b-109">Remarks</span></span>  

 <span data-ttu-id="2a59b-110">`classIds`配列と `cObjects` 配列は並列配列です。</span><span class="sxs-lookup"><span data-stu-id="2a59b-110">The `classIds` and `cObjects` arrays are parallel arrays.</span></span> <span data-ttu-id="2a59b-111">たとえば、 `classIds[i]` とは `cObjects[i]` 同じクラスを参照します。</span><span class="sxs-lookup"><span data-stu-id="2a59b-111">For example, `classIds[i]` and `cObjects[i]` reference the same class.</span></span> <span data-ttu-id="2a59b-112">前のガベージコレクションの後にクラスのインスタンスが作成されていない場合、クラスは省略されます。</span><span class="sxs-lookup"><span data-stu-id="2a59b-112">If no instance of a class has been created since the previous garbage collection, the class is omitted.</span></span> <span data-ttu-id="2a59b-113">`ObjectsAllocatedByClass`コールバックは、大きなオブジェクトヒープに割り当てられたオブジェクトを報告しません。</span><span class="sxs-lookup"><span data-stu-id="2a59b-113">The `ObjectsAllocatedByClass` callback will not report objects allocated in the large object heap.</span></span>  
  
 <span data-ttu-id="2a59b-114">によって報告 `ObjectsAllocatedByClass` される数値は、推定値のみです。</span><span class="sxs-lookup"><span data-stu-id="2a59b-114">The numbers reported by `ObjectsAllocatedByClass` are only estimates.</span></span> <span data-ttu-id="2a59b-115">正確にカウントするには、 [ICorProfilerCallback:: ObjectAllocated](icorprofilercallback-objectallocated-method.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="2a59b-115">For exact counts, use [ICorProfilerCallback::ObjectAllocated](icorprofilercallback-objectallocated-method.md).</span></span>  
  
 <span data-ttu-id="2a59b-116">`classIds`対応する配列にアンロード中の型がある場合、配列には1つ以上の null エントリが含まれ `cObjects` ます。</span><span class="sxs-lookup"><span data-stu-id="2a59b-116">The `classIds` array may contain one or more null entries if the corresponding `cObjects` array has types that are unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a59b-117">要件</span><span class="sxs-lookup"><span data-stu-id="2a59b-117">Requirements</span></span>  

 <span data-ttu-id="2a59b-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a59b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a59b-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a59b-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a59b-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a59b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a59b-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a59b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a59b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a59b-122">See also</span></span>

- [<span data-ttu-id="2a59b-123">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2a59b-123">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
