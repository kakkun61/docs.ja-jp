---
title: CorDebugBlockingObject 構造体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
ms.openlocfilehash: b16feb1af0d4975411876e78940d21096750d2ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726588"
---
# <a name="cordebugblockingobject-structure"></a><span data-ttu-id="77093-102">CorDebugBlockingObject 構造体</span><span class="sxs-lookup"><span data-stu-id="77093-102">CorDebugBlockingObject Structure</span></span>

<span data-ttu-id="77093-103">スレッドをブロックしているオブジェクトと、スレッドがブロックされている具体的な理由を定義します。</span><span class="sxs-lookup"><span data-stu-id="77093-103">Defines an object that is blocking a thread and the specific reason that the thread is blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77093-104">構文</span><span class="sxs-lookup"><span data-stu-id="77093-104">Syntax</span></span>  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a><span data-ttu-id="77093-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="77093-105">Members</span></span>  
  
|<span data-ttu-id="77093-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="77093-106">Member</span></span>|<span data-ttu-id="77093-107">説明</span><span class="sxs-lookup"><span data-stu-id="77093-107">Description</span></span>|  
|------------|-----------------|  
|`pBlockingObject`|<span data-ttu-id="77093-108">スレッドがブロックされているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="77093-108">The object on which the thread is blocking.</span></span> <span data-ttu-id="77093-109">このオブジェクトは、現在の同期済みの状態の間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="77093-109">This object is valid only for the duration of the current synchronized state.</span></span> <span data-ttu-id="77093-110">2つのスレッドが同じ同期状態内の同じオブジェクトでブロックしている場合は、 [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) メソッドで同じ値が返されることが予想されます。</span><span class="sxs-lookup"><span data-stu-id="77093-110">If two threads are blocking on the same object within the same synchronized state, you may expect the [ICorDebugValue::GetAddress](icordebugvalue-getaddress-method.md) method to return the same value.</span></span> <span data-ttu-id="77093-111">ただし、インターフェイスは、同等のポインターである場合とない場合があります。</span><span class="sxs-lookup"><span data-stu-id="77093-111">However, the interfaces may or may not be pointer equivalent.</span></span>|  
|`dwTimeout`|<span data-ttu-id="77093-112">ブロッキング操作がタイムアウトするまでのミリ秒数。または、タイムアウトしないことを示す値が無限であることを示します。タイムアウト値は、残りの時間ではなく、ブロック操作の合計時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="77093-112">The number of milliseconds before the blocking operation will time out, or the value INFINITE, which indicates that it will not time out. The time-out value specifies the total length of time for the blocking operation, not the time that is still remaining.</span></span>|  
|`blockingReason`|<span data-ttu-id="77093-113">このオブジェクトでスレッドがブロックされた理由。</span><span class="sxs-lookup"><span data-stu-id="77093-113">The reason that the thread is blocked on this object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77093-114">解説</span><span class="sxs-lookup"><span data-stu-id="77093-114">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77093-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="77093-115">Requirements</span></span>  

 <span data-ttu-id="77093-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77093-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77093-117">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="77093-117">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="77093-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77093-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77093-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77093-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77093-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="77093-120">See also</span></span>

- [<span data-ttu-id="77093-121">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="77093-121">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="77093-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="77093-122">Debugging</span></span>](index.md)
