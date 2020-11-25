---
title: COR_PRF_GC_GENERATION 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
ms.openlocfilehash: 1d7489e997868a9486f77d176580cee18213a99d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718562"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="48e9b-102">COR_PRF_GC_GENERATION 列挙型</span><span class="sxs-lookup"><span data-stu-id="48e9b-102">COR_PRF_GC_GENERATION Enumeration</span></span>

<span data-ttu-id="48e9b-103">ガベージコレクションの生成を識別します。</span><span class="sxs-lookup"><span data-stu-id="48e9b-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e9b-104">構文</span><span class="sxs-lookup"><span data-stu-id="48e9b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="48e9b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="48e9b-105">Members</span></span>  
  
|<span data-ttu-id="48e9b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="48e9b-106">Member</span></span>|<span data-ttu-id="48e9b-107">説明</span><span class="sxs-lookup"><span data-stu-id="48e9b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="48e9b-108">オブジェクトは、ジェネレーション0として格納されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="48e9b-109">オブジェクトは、ジェネレーション1として格納されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="48e9b-110">オブジェクトは、ジェネレーション2として格納されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="48e9b-111">オブジェクトは、ラージオブジェクトヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-111">The object is stored in the large-object heap.</span></span>|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|<span data-ttu-id="48e9b-112">オブジェクトは、固定されたオブジェクトヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-112">The object is stored in the pinned-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48e9b-113">注釈</span><span class="sxs-lookup"><span data-stu-id="48e9b-113">Remarks</span></span>  

 <span data-ttu-id="48e9b-114">ガベージコレクターは、オブジェクトを経過期間に基づいてジェネレーションに分割することによって、メモリ管理のパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-114">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="48e9b-115">現在、ガベージコレクターは、番号0、1、および2の3つのジェネレーションと、2つの特殊なヒープセグメント (大きなオブジェクト用とピン留めオブジェクト用) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="48e9b-115">The garbage collector currently uses three generations, numbered 0, 1, and 2, and two special heap segments, one for large objects and one for pinned objects.</span></span>
  
 <span data-ttu-id="48e9b-116">サイズがしきい値を超えるオブジェクトは、大きなオブジェクトヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-116">Objects whose size is larger than a threshold value are stored in the large-object heap.</span></span> <span data-ttu-id="48e9b-117">ピン留めされたオブジェクトは、通常のヒープに割り当てた場合のパフォーマンスコストを回避するために、固定されたオブジェクトヒープに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-117">Pinned objects can be allocated to the pinned-object heap to avoid the performance cost of allocating them on the normal heaps.</span></span> <span data-ttu-id="48e9b-118">割り当てられた他のオブジェクトは、ジェネレーション0に属しています。</span><span class="sxs-lookup"><span data-stu-id="48e9b-118">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="48e9b-119">ジェネレーション0でガベージコレクションが発生した後に存在するすべてのオブジェクトは、ジェネレーション1に昇格されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-119">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="48e9b-120">ジェネレーション1でガベージコレクションが発生した後に存在するオブジェクトは、ジェネレーション2に移動します。</span><span class="sxs-lookup"><span data-stu-id="48e9b-120">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="48e9b-121">ジェネレーションを使用することは、ガベージコレクターが、割り当てられたオブジェクトのサブセットだけを一度に処理する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="48e9b-121">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="48e9b-122">`COR_PRF_GC_GENERATION`列挙体は、 [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)構造体によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="48e9b-122">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e9b-123">要件</span><span class="sxs-lookup"><span data-stu-id="48e9b-123">Requirements</span></span>  

 <span data-ttu-id="48e9b-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48e9b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48e9b-125">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="48e9b-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48e9b-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48e9b-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48e9b-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48e9b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e9b-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="48e9b-128">See also</span></span>

- [<span data-ttu-id="48e9b-129">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="48e9b-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
