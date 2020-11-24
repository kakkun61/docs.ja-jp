---
title: CorDebugBlockingReason 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
ms.openlocfilehash: ddd03d70656ad52fd9d577beedc60b51c7b305d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672852"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="add75-102">CorDebugBlockingReason 列挙体</span><span class="sxs-lookup"><span data-stu-id="add75-102">CorDebugBlockingReason Enumeration</span></span>

<span data-ttu-id="add75-103">指定されたオブジェクト上でスレッドがブロックされる理由を指定します。</span><span class="sxs-lookup"><span data-stu-id="add75-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="add75-104">構文</span><span class="sxs-lookup"><span data-stu-id="add75-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="add75-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="add75-105">Members</span></span>  
  
|<span data-ttu-id="add75-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="add75-106">Member</span></span>|<span data-ttu-id="add75-107">説明</span><span class="sxs-lookup"><span data-stu-id="add75-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="add75-108">内部使用のみ。</span><span class="sxs-lookup"><span data-stu-id="add75-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="add75-109">スレッドが、オブジェクトのモニターロックに関連付けられているクリティカルセクションを取得しようとしています。</span><span class="sxs-lookup"><span data-stu-id="add75-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="add75-110">通常、このエラー <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> は、メソッドまたはメソッドのいずれかを呼び出すと発生し <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="add75-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="add75-111">スレッドが、オブジェクトのモニターロックに関連付けられているイベントを待機しています。</span><span class="sxs-lookup"><span data-stu-id="add75-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="add75-112">通常、これは、メソッドのいずれかを呼び出すと発生し <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` ます。</span><span class="sxs-lookup"><span data-stu-id="add75-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="add75-113">注釈</span><span class="sxs-lookup"><span data-stu-id="add75-113">Remarks</span></span>  

 <span data-ttu-id="add75-114">`BLOCKING_MONITOR_CRITICAL_SECTION`メンバーまたは `BLOCKING_MONITOR_EVENT` メンバーが[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体で使用されている場合、 `pBlockingObject` 構造体のメンバーは、入力されるオブジェクトを表す "ICorDebugValue" インターフェイスを指します。</span><span class="sxs-lookup"><span data-stu-id="add75-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="add75-115">また、 [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) インターフェイスを実装することも保証されます。</span><span class="sxs-lookup"><span data-stu-id="add75-115">It is also guaranteed to implement the [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="add75-116">要件</span><span class="sxs-lookup"><span data-stu-id="add75-116">Requirements</span></span>  

 <span data-ttu-id="add75-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="add75-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="add75-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="add75-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="add75-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="add75-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="add75-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="add75-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="add75-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="add75-121">See also</span></span>

- [<span data-ttu-id="add75-122">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="add75-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="add75-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="add75-123">Debugging</span></span>](index.md)
