---
title: COR_GC_STATS 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 53a70c53a06ac55a2dab7c646018d63189ee0b36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726224"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="c68ce-102">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="c68ce-102">COR_GC_STATS Structure</span></span>

<span data-ttu-id="c68ce-103">共通言語ランタイム (CLR) のガベージコレクション機構に関する統計情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="c68ce-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c68ce-104">構文</span><span class="sxs-lookup"><span data-stu-id="c68ce-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="c68ce-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c68ce-105">Members</span></span>  
  
|<span data-ttu-id="c68ce-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c68ce-106">Member</span></span>|<span data-ttu-id="c68ce-107">説明</span><span class="sxs-lookup"><span data-stu-id="c68ce-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="c68ce-108">計算および返されるフィールド値を示します。</span><span class="sxs-lookup"><span data-stu-id="c68ce-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="c68ce-109">外部要求によって強制されたガベージコレクションの数を示します。</span><span class="sxs-lookup"><span data-stu-id="c68ce-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="c68ce-110">生成のたびに実行されるガベージコレクションの数を示します。</span><span class="sxs-lookup"><span data-stu-id="c68ce-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="c68ce-111">すべてのヒープでコミットされた合計キロバイト数。</span><span class="sxs-lookup"><span data-stu-id="c68ce-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="c68ce-112">すべてのヒープに予約されているキロバイト数の合計です。</span><span class="sxs-lookup"><span data-stu-id="c68ce-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="c68ce-113">ジェネレーションゼロヒープのサイズ (kb 単位)。</span><span class="sxs-lookup"><span data-stu-id="c68ce-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="c68ce-114">ジェネレーション1のヒープのサイズ (kb 単位)。</span><span class="sxs-lookup"><span data-stu-id="c68ce-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="c68ce-115">ジェネレーション2のヒープのサイズ (kb 単位)。</span><span class="sxs-lookup"><span data-stu-id="c68ce-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="c68ce-116">ラージオブジェクトヒープのサイズ (kb 単位)。</span><span class="sxs-lookup"><span data-stu-id="c68ce-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="c68ce-117">ジェネレーション0からジェネレーション1に昇格されたオブジェクトのサイズ (kb 単位)。</span><span class="sxs-lookup"><span data-stu-id="c68ce-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="c68ce-118">ジェネレーション1からジェネレーション2に昇格されたオブジェクトのサイズ (kb 単位)。</span><span class="sxs-lookup"><span data-stu-id="c68ce-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c68ce-119">注釈</span><span class="sxs-lookup"><span data-stu-id="c68ce-119">Remarks</span></span>  

 <span data-ttu-id="c68ce-120">[ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md)メソッドでは、 `Flags` 構造体のフィールドを `COR_GC_STATS` [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md)列挙体の1つ以上の値に設定して、どの統計を設定するかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c68ce-120">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="c68ce-121">次の表は、この構造体によって提供される統計を、2つの [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 列挙値、およびにマップし `COR_GC_COUNTS` `COR_GC_MEMORYUSAGE` ます。</span><span class="sxs-lookup"><span data-stu-id="c68ce-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="c68ce-122">指定された COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="c68ce-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="c68ce-123">指定された COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="c68ce-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="c68ce-124">使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c68ce-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c68ce-125">要件</span><span class="sxs-lookup"><span data-stu-id="c68ce-125">Requirements</span></span>  

 <span data-ttu-id="c68ce-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c68ce-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c68ce-127">**ヘッダー:** GCHost</span><span class="sxs-lookup"><span data-stu-id="c68ce-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="c68ce-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="c68ce-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c68ce-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c68ce-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c68ce-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c68ce-130">See also</span></span>

- [<span data-ttu-id="c68ce-131">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="c68ce-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="c68ce-132">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="c68ce-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="c68ce-133">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="c68ce-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
