---
title: ICorDebugHeapEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: 312052fcd683acbccb9ca616992bd635490aa2a5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724365"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="e7b04-102">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7b04-102">ICorDebugHeapEnum Interface</span></span>

<span data-ttu-id="e7b04-103">マネージド ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="e7b04-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="e7b04-104">このインターフェイスは、ICorDebugEnum インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="e7b04-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7b04-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b04-105">Methods</span></span>  
  
|<span data-ttu-id="e7b04-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b04-106">Method</span></span>|<span data-ttu-id="e7b04-107">説明</span><span class="sxs-lookup"><span data-stu-id="e7b04-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7b04-108">Next メソッド</span><span class="sxs-lookup"><span data-stu-id="e7b04-108">Next Method</span></span>](icordebugheapenum-next-method.md)|<span data-ttu-id="e7b04-109">マネージヒープ上のオブジェクトに関する情報を格納している、指定した数の [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e7b04-109">Gets the specified number of [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7b04-110">注釈</span><span class="sxs-lookup"><span data-stu-id="e7b04-110">Remarks</span></span>  

 <span data-ttu-id="e7b04-111">`ICorDebugHeapEnum`インターフェイスは、ICorDebugEnum インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="e7b04-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="e7b04-112">`ICorDebugHeapEnum`インスタンスには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって[COR_HEAPOBJECT](cor-heapobject-structure.md)インスタンスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="e7b04-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="e7b04-113">コレクション内の各 [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスは、ヒープ上のライブオブジェクト、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="e7b04-113">Each [COR_HEAPOBJECT](cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="e7b04-114">コレクション内の [COR_HEAPOBJECT](cor-heapobject-structure.md) オブジェクトを列挙するには、 [次](icordebugheapenum-next-method.md) のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="e7b04-114">The [COR_HEAPOBJECT](cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b04-115">要件</span><span class="sxs-lookup"><span data-stu-id="e7b04-115">Requirements</span></span>  

 <span data-ttu-id="e7b04-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7b04-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b04-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e7b04-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7b04-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7b04-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7b04-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b04-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b04-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7b04-120">See also</span></span>

- [<span data-ttu-id="e7b04-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e7b04-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
