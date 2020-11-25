---
title: ICorDebugProcess5 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
ms.openlocfilehash: cef69ac7e3572b67dd676ce8408e4210d93accf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717579"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="622f8-102">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="622f8-102">ICorDebugProcess5 Interface</span></span>

<span data-ttu-id="622f8-103">は、アプリケーションインターフェイスを拡張して、マネージヒープへのアクセスをサポートし、マネージオブジェクトのガベージコレクションに関する情報を提供し、デバッガーがアプリケーションのローカルネイティブイメージキャッシュからイメージを読み込むかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="622f8-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="622f8-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-104">Methods</span></span>  
  
|<span data-ttu-id="622f8-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-105">Method</span></span>|<span data-ttu-id="622f8-106">説明</span><span class="sxs-lookup"><span data-stu-id="622f8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="622f8-107">EnableNGenPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-107">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="622f8-108">マネージデバッガーで実行中にアプリケーションがネイティブイメージを読み込む方法を決定する値を設定します。</span><span class="sxs-lookup"><span data-stu-id="622f8-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="622f8-109">EnumerateGCReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-109">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="622f8-110">プロセスでガベージコレクトされるすべてのオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="622f8-111">EnumerateHandles メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-111">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="622f8-112">プロセス内のオブジェクトハンドルの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="622f8-113">EnumerateHeap メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-113">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="622f8-114">マネージヒープ上のオブジェクトの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="622f8-115">EnumerateHeapRegions メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-115">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="622f8-116">マネージヒープの領域の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="622f8-117">GetArrayLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-117">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="622f8-118">メモリ内の配列のレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="622f8-119">GetGCHeapInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-119">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="622f8-120">マネージヒープでガベージコレクトされるオブジェクトに関する情報を格納している [COR_HEAPINFO](cor-heapinfo-structure.md) 構造体へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-120">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="622f8-121">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-121">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="622f8-122">マネージヒープ上のオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="622f8-123">GetTypeFields メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-123">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="622f8-124">型の識別子に基づいて、型のフィールド情報を格納している配列へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="622f8-125">GetTypeForTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-125">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="622f8-126">型識別子に基づいてオブジェクトに関する情報を提供する型オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="622f8-127">GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-127">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="622f8-128">指定したアドレスにあるオブジェクトの型識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="622f8-129">GetTypeLayout メソッド</span><span class="sxs-lookup"><span data-stu-id="622f8-129">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="622f8-130">型識別子に基づいて、メモリ内のオブジェクトのレイアウトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="622f8-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="622f8-131">注釈</span><span class="sxs-lookup"><span data-stu-id="622f8-131">Remarks</span></span>  

 <span data-ttu-id="622f8-132">このインターフェイスは、ICorDebugProcess2、ICorDebugProcess3、および[ICorDebugProcess3](icordebugprocess3-interface.md)の各インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="622f8-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="622f8-133">このインターフェイスは、別のコンピューターまたは別のプロセスからのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="622f8-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="622f8-134">要件</span><span class="sxs-lookup"><span data-stu-id="622f8-134">Requirements</span></span>  

 <span data-ttu-id="622f8-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="622f8-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="622f8-136">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="622f8-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="622f8-137">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="622f8-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="622f8-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="622f8-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622f8-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="622f8-139">See also</span></span>

- [<span data-ttu-id="622f8-140">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="622f8-140">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="622f8-141">デバッグ</span><span class="sxs-lookup"><span data-stu-id="622f8-141">Debugging</span></span>](index.md)
