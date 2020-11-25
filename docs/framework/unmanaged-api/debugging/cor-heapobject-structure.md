---
title: COR_HEAPOBJECT 構造体
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
ms.openlocfilehash: 54af02b48dabdf2042763954805f0d454323ac89
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726367"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="a1e50-102">COR_HEAPOBJECT 構造体</span><span class="sxs-lookup"><span data-stu-id="a1e50-102">COR_HEAPOBJECT Structure</span></span>

<span data-ttu-id="a1e50-103">マネージド ヒープ上のオブジェクトに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="a1e50-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1e50-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1e50-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="a1e50-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a1e50-105">Members</span></span>  
  
|<span data-ttu-id="a1e50-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a1e50-106">Member</span></span>|<span data-ttu-id="a1e50-107">説明</span><span class="sxs-lookup"><span data-stu-id="a1e50-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="a1e50-108">メモリ内のオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="a1e50-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="a1e50-109">オブジェクトの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="a1e50-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="a1e50-110">オブジェクトの型を表す [COR_TYPEID](cor-typeid-structure.md) トークン。</span><span class="sxs-lookup"><span data-stu-id="a1e50-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1e50-111">注釈</span><span class="sxs-lookup"><span data-stu-id="a1e50-111">Remarks</span></span>  

 <span data-ttu-id="a1e50-112">`COR_HEAPOBJECT`インスタンスを取得するには、 [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md)メソッドを呼び出すことによって設定される、表示されている[heapheapenum](icordebugheapenum-interface.md)インターフェイスオブジェクトを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a1e50-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="a1e50-113">インスタンスは、 `COR_HEAPOBJECT` マネージヒープ上のライブオブジェクトに関する情報、またはオブジェクトではなく、ガベージコレクターによってまだ収集されていないオブジェクトに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a1e50-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="a1e50-114">パフォーマンスを向上させるために、この `COR_HEAPOBJECT.address` フィールドは `CORDB_ADDRESS` デバッグ API の多くで使用される ICorDebugValue インターフェイス値ではなく、値になります。</span><span class="sxs-lookup"><span data-stu-id="a1e50-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="a1e50-115">指定されたオブジェクトアドレスの ICorDebugValue オブジェクトを取得するには、 `CORDB_ADDRESS` [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) メソッドに値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a1e50-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="a1e50-116">パフォーマンスを向上させるために、この `COR_HEAPOBJECT.type` フィールドは、 `COR_TYPEID` デバッグ API の多くで使用されている、テキスト型のインターフェイス値ではなく、値です。</span><span class="sxs-lookup"><span data-stu-id="a1e50-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="a1e50-117">指定された型 ID の `COR_TYPEID` [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) メソッドに値を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="a1e50-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="a1e50-118">構造体には、 `COR_HEAPOBJECT` 参照カウントの COM インターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1e50-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="a1e50-119">のインスタンスを列挙子から取得する場合は、次の `COR_HEAPOBJECT` メソッドを呼び出す必要があります。その後、参照を解放する必要があります。 [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md)</span><span class="sxs-lookup"><span data-stu-id="a1e50-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1e50-120">要件</span><span class="sxs-lookup"><span data-stu-id="a1e50-120">Requirements</span></span>  

 <span data-ttu-id="a1e50-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e50-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e50-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1e50-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1e50-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1e50-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1e50-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e50-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e50-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1e50-125">See also</span></span>

- [<span data-ttu-id="a1e50-126">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="a1e50-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="a1e50-127">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a1e50-127">Debugging</span></span>](index.md)
