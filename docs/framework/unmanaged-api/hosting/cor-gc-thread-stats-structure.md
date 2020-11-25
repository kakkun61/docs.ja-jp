---
title: COR_GC_THREAD_STATS 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 25a90965dc5466b7cf1a07140705424cf2ba4cd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699236"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="b6c18-102">COR_GC_THREAD_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="b6c18-102">COR_GC_THREAD_STATS Structure</span></span>

<span data-ttu-id="b6c18-103">ガベージコレクションに関連するスレッドごとの統計情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b6c18-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6c18-104">構文</span><span class="sxs-lookup"><span data-stu-id="b6c18-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="b6c18-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b6c18-105">Members</span></span>  
  
|<span data-ttu-id="b6c18-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b6c18-106">Member</span></span>|<span data-ttu-id="b6c18-107">説明</span><span class="sxs-lookup"><span data-stu-id="b6c18-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="b6c18-108">現在のインスタンスに関連付けられているスレッドに割り当てられたメモリのバイト数 `COR_GC_THREAD_STATS` 。</span><span class="sxs-lookup"><span data-stu-id="b6c18-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="b6c18-109">ジェネレーション0のガベージコレクションが発生するたびに、この数値はゼロにクリアされます。</span><span class="sxs-lookup"><span data-stu-id="b6c18-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="b6c18-110">最新のガベージコレクションで上位のジェネレーションに昇格されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="b6c18-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6c18-111">注釈</span><span class="sxs-lookup"><span data-stu-id="b6c18-111">Remarks</span></span>  

 <span data-ttu-id="b6c18-112">[ICLRTask:: GetMemStats](iclrtask-getmemstats-method.md) は、型の出力パラメーターを受け取り `COR_GC_THREAD_STATS` ます。</span><span class="sxs-lookup"><span data-stu-id="b6c18-112">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6c18-113">要件</span><span class="sxs-lookup"><span data-stu-id="b6c18-113">Requirements</span></span>  

 <span data-ttu-id="b6c18-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c18-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6c18-115">**ヘッダー:** GCHost</span><span class="sxs-lookup"><span data-stu-id="b6c18-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="b6c18-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="b6c18-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b6c18-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6c18-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6c18-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6c18-118">See also</span></span>

- [<span data-ttu-id="b6c18-119">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="b6c18-119">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="b6c18-120">IHostTask インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b6c18-120">IHostTask Interface</span></span>](ihosttask-interface.md)
