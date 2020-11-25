---
title: COR_HEAPINFO 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPINFO
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPINFO
helpviewer_keywords:
- COR_HEAPINFO structure [.NET Framework debugging]
ms.assetid: bfb2cd39-3e0b-4d51-ba0c-f009755c1456
topic_type:
- apiref
ms.openlocfilehash: 5400350e1c489ec4c2ff3cddf83a4f1a8a0c7947
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726601"
---
# <a name="cor_heapinfo-structure"></a><span data-ttu-id="a5e4a-102">COR_HEAPINFO 構造体</span><span class="sxs-lookup"><span data-stu-id="a5e4a-102">COR_HEAPINFO Structure</span></span>

<span data-ttu-id="a5e4a-103">列挙可能かどうかなど、ガベージ コレクション ヒープに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-103">Provides general information about the garbage collection heap, including whether it is enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e4a-104">構文</span><span class="sxs-lookup"><span data-stu-id="a5e4a-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPINFO {  
    BOOL areGCStructuresValid;
    DWORD pointerSize;
    DWORD numHeaps;  
    BOOL concurrent;
    CorDebugGCType gcType;
} COR_HEAPINFO;  
```  
  
## <a name="members"></a><span data-ttu-id="a5e4a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a5e4a-105">Members</span></span>  
  
|<span data-ttu-id="a5e4a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a5e4a-106">Member</span></span>|<span data-ttu-id="a5e4a-107">説明</span><span class="sxs-lookup"><span data-stu-id="a5e4a-107">Description</span></span>|  
|------------|-----------------|  
|`areGCStructuresValid`|<span data-ttu-id="a5e4a-108">`true` ガベージコレクション構造体が有効で、ヒープを列挙できる場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-108">`true` if garbage collection structures are valid and the heap can be enumerated; otherwise, `false`.</span></span>|  
|`pointerSize`|<span data-ttu-id="a5e4a-109">ターゲットアーキテクチャのポインターのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-109">The size, in bytes, of pointers on the target architecture.</span></span>|  
|`numHeaps`|<span data-ttu-id="a5e4a-110">プロセス内の論理ガベージコレクションヒープの数。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-110">The number of logical garbage collection heaps in the process.</span></span>|  
|`concurrent`|<span data-ttu-id="a5e4a-111">`TRUE` 同時実行 (バックグラウンド) ガベージコレクションが有効な場合は。それ以外の場合は `FALSE` 。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-111">`TRUE` if concurrent (background) garbage collection is enabled; otherwise, `FALSE`.</span></span>|  
|`gcType`|<span data-ttu-id="a5e4a-112">ガベージコレクターがワークステーションまたはサーバーのどちらで実行されているかを示す [CorDebugGCType](cordebuggctype-enumeration.md) 列挙体のメンバー。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-112">A member of the [CorDebugGCType](cordebuggctype-enumeration.md) enumeration that indicates whether the garbage collector is running on a workstation or a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5e4a-113">注釈</span><span class="sxs-lookup"><span data-stu-id="a5e4a-113">Remarks</span></span>  

 <span data-ttu-id="a5e4a-114">構造体のインスタンス `COR_HEAPINFO` は、 [ICorDebugProcess5:: Getg apinformation](icordebugprocess5-getgcheapinformation-method.md) メソッドを呼び出すことによって返されます。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-114">An instance of the `COR_HEAPINFO` structure is returned by calling the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
 <span data-ttu-id="a5e4a-115">ガベージコレクションヒープ上のオブジェクトを列挙する前に、必ずフィールドをチェックし `areGCStructuresValid` て、ヒープが列挙可能な状態であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-115">Before enumerating objects on the garbage collection heap, you must always check the `areGCStructuresValid` field to ensure that the heap is in an enumerable state.</span></span> <span data-ttu-id="a5e4a-116">詳細については、「 [ICorDebugProcess5:: Getg](icordebugprocess5-getgcheapinformation-method.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-116">For more information, see the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5e4a-117">要件</span><span class="sxs-lookup"><span data-stu-id="a5e4a-117">Requirements</span></span>  

 <span data-ttu-id="a5e4a-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a5e4a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e4a-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5e4a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5e4a-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e4a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e4a-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e4a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e4a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5e4a-122">See also</span></span>

- [<span data-ttu-id="a5e4a-123">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="a5e4a-123">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a5e4a-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a5e4a-124">Debugging</span></span>](index.md)
