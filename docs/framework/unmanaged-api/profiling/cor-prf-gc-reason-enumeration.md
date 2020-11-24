---
title: COR_PRF_GC_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: f41f00a9699d6fc135ca3b9c0b4b470ca0359279
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682381"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="6c297-102">COR_PRF_GC_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="6c297-102">COR_PRF_GC_REASON Enumeration</span></span>

<span data-ttu-id="6c297-103">ガベージ コレクションが発生している理由を示します。</span><span class="sxs-lookup"><span data-stu-id="6c297-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c297-104">構文</span><span class="sxs-lookup"><span data-stu-id="6c297-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="6c297-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="6c297-105">Members</span></span>  
  
|<span data-ttu-id="6c297-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6c297-106">Member</span></span>|<span data-ttu-id="6c297-107">説明</span><span class="sxs-lookup"><span data-stu-id="6c297-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="6c297-108">ガベージコレクションは、メソッドによって発生しました <xref:System.GC.Collect%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6c297-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="6c297-109">理由が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="6c297-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c297-110">要件</span><span class="sxs-lookup"><span data-stu-id="6c297-110">Requirements</span></span>  

 <span data-ttu-id="6c297-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c297-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c297-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c297-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c297-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c297-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c297-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c297-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c297-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c297-115">See also</span></span>

- [<span data-ttu-id="6c297-116">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="6c297-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
