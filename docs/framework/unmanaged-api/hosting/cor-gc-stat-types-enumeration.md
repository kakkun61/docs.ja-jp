---
title: COR_GC_STAT_TYPES 列挙体
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: c14e27b67fc600e2684f8c967af30bb9a5cee126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716742"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="fcf1c-102">COR_GC_STAT_TYPES 列挙体</span><span class="sxs-lookup"><span data-stu-id="fcf1c-102">COR_GC_STAT_TYPES Enumeration</span></span>

<span data-ttu-id="fcf1c-103">ガベージコレクション用に記録する統計を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcf1c-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcf1c-104">構文</span><span class="sxs-lookup"><span data-stu-id="fcf1c-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="fcf1c-105">解説</span><span class="sxs-lookup"><span data-stu-id="fcf1c-105">Remarks</span></span>  

 <span data-ttu-id="fcf1c-106">この列挙体は、 [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md)メソッドによって設定される[COR_GC_STATS](cor-gc-stats-structure.md)構造内の統計を指定します。</span><span class="sxs-lookup"><span data-stu-id="fcf1c-106">This enumeration specifies which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="fcf1c-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="fcf1c-107">Members</span></span>  
  
|<span data-ttu-id="fcf1c-108">メンバー</span><span class="sxs-lookup"><span data-stu-id="fcf1c-108">Member</span></span>|<span data-ttu-id="fcf1c-109">説明</span><span class="sxs-lookup"><span data-stu-id="fcf1c-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="fcf1c-110">生成されるたびに実行されるガベージコレクションの数を記録します。</span><span class="sxs-lookup"><span data-stu-id="fcf1c-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="fcf1c-111">メモリ使用量とガベージコレクションサイズの統計情報を記録します。</span><span class="sxs-lookup"><span data-stu-id="fcf1c-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fcf1c-112">要件</span><span class="sxs-lookup"><span data-stu-id="fcf1c-112">Requirements</span></span>  

 <span data-ttu-id="fcf1c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcf1c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcf1c-114">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="fcf1c-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="fcf1c-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcf1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf1c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcf1c-116">See also</span></span>

- [<span data-ttu-id="fcf1c-117">COR_GC_STATS 構造体</span><span class="sxs-lookup"><span data-stu-id="fcf1c-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="fcf1c-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="fcf1c-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
