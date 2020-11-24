---
title: COR_PRF_GC_ROOT_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 6b4c71a099e1ddb03b8a5287b56b750f7119e34e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682355"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a><span data-ttu-id="61780-102">COR_PRF_GC_ROOT_FLAGS 列挙型</span><span class="sxs-lookup"><span data-stu-id="61780-102">COR_PRF_GC_ROOT_FLAGS Enumeration</span></span>

<span data-ttu-id="61780-103">ガベージコレクションのルートのプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="61780-103">Indicates a property of a garbage collection root.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61780-104">構文</span><span class="sxs-lookup"><span data-stu-id="61780-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="61780-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="61780-105">Members</span></span>  
  
|<span data-ttu-id="61780-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="61780-106">Member</span></span>|<span data-ttu-id="61780-107">説明</span><span class="sxs-lookup"><span data-stu-id="61780-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|<span data-ttu-id="61780-108">ルートは、ガベージコレクションがオブジェクトを移動できないようにします。</span><span class="sxs-lookup"><span data-stu-id="61780-108">The root prevents a garbage collection from moving the object.</span></span>|  
|`COR_PRF_GC_ROOT_WEAKREF`|<span data-ttu-id="61780-109">ルートによってガベージコレクションが妨げられることはありません。</span><span class="sxs-lookup"><span data-stu-id="61780-109">The root does not prevent garbage collection.</span></span>|  
|`COR_PRF_GC_ROOT_INTERIOR`|<span data-ttu-id="61780-110">ルートは、オブジェクト自体ではなく、オブジェクトのフィールドを参照します。</span><span class="sxs-lookup"><span data-stu-id="61780-110">The root refers to a field of the object rather than the object itself.</span></span>|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|<span data-ttu-id="61780-111">オブジェクトの参照カウントが特定の値の場合、ルートはガベージコレクションを防止します。</span><span class="sxs-lookup"><span data-stu-id="61780-111">The root prevents garbage collection if the reference count of the object is a certain value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61780-112">注釈</span><span class="sxs-lookup"><span data-stu-id="61780-112">Remarks</span></span>  

 <span data-ttu-id="61780-113">`COR_PRF_GC_ROOT_FLAGS` は、特別なルートに関する追加情報を提供するビットマスクです。</span><span class="sxs-lookup"><span data-stu-id="61780-113">`COR_PRF_GC_ROOT_FLAGS` is a bitmask that provides additional information about special roots.</span></span> <span data-ttu-id="61780-114">ただし、すべてのルートが特別であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="61780-114">However, not all roots are special.</span></span> <span data-ttu-id="61780-115">たとえば、一部のルートは、弱い参照、内部ポインター、ピン留め、または参照カウントされていません。</span><span class="sxs-lookup"><span data-stu-id="61780-115">For example, some roots are not weak references, interior pointers, pinned, or reference-counted.</span></span> <span data-ttu-id="61780-116">このようなルートの場合、伝えるフラグはありません。</span><span class="sxs-lookup"><span data-stu-id="61780-116">For such roots, there are no flags to convey.</span></span> <span data-ttu-id="61780-117">したがって、 [ICorProfilerCallback2:: RootReferences2](icorprofilercallback2-rootreferences2-method.md) メソッドなど、この列挙を使用するメソッドは、フラグのビットマスクとして0を送信し、すべてのフラグがオフになっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="61780-117">Therefore, methods that use this enumeration, such as the [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method, send 0 for the flags bitmask, indicating that all flags are turned off.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61780-118">要件</span><span class="sxs-lookup"><span data-stu-id="61780-118">Requirements</span></span>  

 <span data-ttu-id="61780-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="61780-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61780-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61780-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61780-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61780-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61780-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61780-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61780-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="61780-123">See also</span></span>

- [<span data-ttu-id="61780-124">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="61780-124">Profiling Enumerations</span></span>](profiling-enumerations.md)
