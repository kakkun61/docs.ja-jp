---
title: COR_GC_THREAD_STATS_TYPES 列挙体
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 122536877b2fd5f0e5c64118bd978b54c4a8b3df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696818"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="d2a26-102">COR_GC_THREAD_STATS_TYPES 列挙体</span><span class="sxs-lookup"><span data-stu-id="d2a26-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>

<span data-ttu-id="d2a26-103">スレッドのガベージコレクションの統計を示します。</span><span class="sxs-lookup"><span data-stu-id="d2a26-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2a26-104">構文</span><span class="sxs-lookup"><span data-stu-id="d2a26-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="d2a26-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d2a26-105">Members</span></span>  
  
|<span data-ttu-id="d2a26-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d2a26-106">Member</span></span>|<span data-ttu-id="d2a26-107">説明</span><span class="sxs-lookup"><span data-stu-id="d2a26-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="d2a26-108">スレッドには、最新のガベージコレクションで昇格されたバイト数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d2a26-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2a26-109">要件</span><span class="sxs-lookup"><span data-stu-id="d2a26-109">Requirements</span></span>  

 <span data-ttu-id="d2a26-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2a26-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2a26-111">**ヘッダー:** GCHost、GCHost</span><span class="sxs-lookup"><span data-stu-id="d2a26-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="d2a26-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2a26-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2a26-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="d2a26-113">See also</span></span>

- [<span data-ttu-id="d2a26-114">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="d2a26-114">Hosting Enumerations</span></span>](hosting-enumerations.md)
