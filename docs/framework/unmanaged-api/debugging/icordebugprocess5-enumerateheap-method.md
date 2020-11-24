---
title: ICorDebugProcess5::EnumerateHeap メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 22ab29f8a204a4b27dafdefcd3652cc3dcf9769c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671136"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="a2df7-102">ICorDebugProcess5::EnumerateHeap メソッド</span><span class="sxs-lookup"><span data-stu-id="a2df7-102">ICorDebugProcess5::EnumerateHeap Method</span></span>

<span data-ttu-id="a2df7-103">マネージヒープ上のオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a2df7-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2df7-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2df7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2df7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2df7-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="a2df7-106">入出力マネージヒープ上に存在するオブジェクト [の列挙子](icordebugheapenum-interface.md) である、コードオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a2df7-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2df7-107">注釈</span><span class="sxs-lookup"><span data-stu-id="a2df7-107">Remarks</span></span>  

 <span data-ttu-id="a2df7-108">メソッドを呼び出す前に `ICorDebugProcess5::EnumerateHeap` 、 [ICorDebugProcess5:: Getg](icordebugprocess5-getgcheapinformation-method.md) メソッドを呼び出し、 `areGCStructuresValid` 返された [COR_HEAPINFO](cor-heapinfo-structure.md) オブジェクトのフィールドの値を調べて、現在の状態のガベージコレクションヒープが列挙可能であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2df7-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="a2df7-109">さらに、は `ICorDebugProcess5::EnumerateHeap` 、 `E_FAIL` プロセスの有効期間が早すぎると、マネージヒープのメモリが割り当てられる前に、を返します。</span><span class="sxs-lookup"><span data-stu-id="a2df7-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="a2df7-110">は [、ICorDebugEnum](icordebugheapenum-interface.md) インターフェイスから派生した標準列挙子であり、 [COR_HEAPOBJECT](cor-heapobject-structure.md) オブジェクトを列挙できます。</span><span class="sxs-lookup"><span data-stu-id="a2df7-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="a2df7-111">このメソッド [は、すべてのオブジェクト](icordebugheapenum-interface.md) に関する情報を提供する [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスを使用して、このコレクションオブジェクトを設定します。</span><span class="sxs-lookup"><span data-stu-id="a2df7-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="a2df7-112">コレクションには、オブジェクトによってルートされていないが、まだガベージコレクターによって収集されていないオブジェクトに関する情報を提供する [COR_HEAPOBJECT](cor-heapobject-structure.md) インスタンスを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="a2df7-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2df7-113">要件</span><span class="sxs-lookup"><span data-stu-id="a2df7-113">Requirements</span></span>  

 <span data-ttu-id="a2df7-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2df7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2df7-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2df7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2df7-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2df7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2df7-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2df7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2df7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2df7-118">See also</span></span>

- [<span data-ttu-id="a2df7-119">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2df7-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a2df7-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2df7-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
