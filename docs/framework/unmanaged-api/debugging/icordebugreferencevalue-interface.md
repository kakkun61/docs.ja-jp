---
title: ICorDebugReferenceValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
ms.openlocfilehash: 343e504e086e740236d7b5977452cc0d789883fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728408"
---
# <a name="icordebugreferencevalue-interface"></a><span data-ttu-id="51248-102">ICorDebugReferenceValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="51248-102">ICorDebugReferenceValue Interface</span></span>

<span data-ttu-id="51248-103">オブジェクトへの参照である値を管理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="51248-103">Provides methods that manage a value that is a reference to an object.</span></span> <span data-ttu-id="51248-104">(つまり、このインターフェイスには、ポインターを管理するメソッドが用意されています)。このインターフェイスは、"ICorDebugValue" を実装します。</span><span class="sxs-lookup"><span data-stu-id="51248-104">(That is, this interface provides methods that manage a pointer.) This interface implements "ICorDebugValue".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51248-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="51248-105">Methods</span></span>  
  
|<span data-ttu-id="51248-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="51248-106">Method</span></span>|<span data-ttu-id="51248-107">説明</span><span class="sxs-lookup"><span data-stu-id="51248-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51248-108">Dereference メソッド</span><span class="sxs-lookup"><span data-stu-id="51248-108">Dereference Method</span></span>](icordebugreferencevalue-dereference-method.md)|<span data-ttu-id="51248-109">参照されているオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="51248-109">Gets the object that is referenced.</span></span>|  
|[<span data-ttu-id="51248-110">DereferenceStrong メソッド</span><span class="sxs-lookup"><span data-stu-id="51248-110">DereferenceStrong Method</span></span>](icordebugreferencevalue-dereferencestrong-method.md)|<span data-ttu-id="51248-111">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="51248-111">Not implemented.</span></span> <span data-ttu-id="51248-112">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="51248-112">Do not call this method.</span></span>|  
|[<span data-ttu-id="51248-113">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="51248-113">GetValue Method</span></span>](icordebugreferencevalue-getvalue-method.md)|<span data-ttu-id="51248-114">参照先のオブジェクトの現在のメモリアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="51248-114">Gets the current memory address of the referenced object.</span></span>|  
|[<span data-ttu-id="51248-115">IsNull メソッド</span><span class="sxs-lookup"><span data-stu-id="51248-115">IsNull Method</span></span>](icordebugreferencevalue-isnull-method.md)|<span data-ttu-id="51248-116">このが null 値であるかどうかを示す値を取得します。この値を指定した `ICorDebugReferenceValue` 場合、は `ICorDebugReferenceValue` オブジェクトをポイントしません。</span><span class="sxs-lookup"><span data-stu-id="51248-116">Gets a value that indicates whether this `ICorDebugReferenceValue` is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>|  
|[<span data-ttu-id="51248-117">SetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="51248-117">SetValue Method</span></span>](icordebugreferencevalue-setvalue-method.md)|<span data-ttu-id="51248-118">現在のメモリアドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="51248-118">Sets the current memory address.</span></span> <span data-ttu-id="51248-119">つまり、このメソッドは、 `ICorDebugReferenceValue` オブジェクトを指すようにこれを設定します。</span><span class="sxs-lookup"><span data-stu-id="51248-119">That is, this method sets this `ICorDebugReferenceValue` to point to an object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51248-120">注釈</span><span class="sxs-lookup"><span data-stu-id="51248-120">Remarks</span></span>  

 <span data-ttu-id="51248-121">共通言語ランタイム (CLR) は、デバッグされたプロセスが続行されると、オブジェクトのガベージコレクションを実行する場合があります。</span><span class="sxs-lookup"><span data-stu-id="51248-121">The common language runtime (CLR) may do a garbage collection on objects when the debugged process is continued.</span></span> <span data-ttu-id="51248-122">ガベージコレクションでは、メモリ内でオブジェクトを移動できます。</span><span class="sxs-lookup"><span data-stu-id="51248-122">The garbage collection may move objects around in memory.</span></span> <span data-ttu-id="51248-123">はガベージコレクションと連携して、ガベージコレクション `ICorDebugReferenceValue` の後に情報が更新されるか、ガベージコレクションの前に暗黙的に無効にされます。</span><span class="sxs-lookup"><span data-stu-id="51248-123">An `ICorDebugReferenceValue` will either cooperate with the garbage collection so that its information is updated after the garbage collection, or it will be invalidated implicitly before the garbage collection.</span></span>  
  
 <span data-ttu-id="51248-124">`ICorDebugReferenceValue`デバッグされたプロセスが続行されると、オブジェクトは暗黙的に無効になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="51248-124">The `ICorDebugReferenceValue` object may be implicitly invalidated after the debugged process has been continued.</span></span> <span data-ttu-id="51248-125">派生された "の値" は、明示的に解放または公開されるまで無効になりません。</span><span class="sxs-lookup"><span data-stu-id="51248-125">The derived "ICorDebugHandleValue" is not invalidated until it is explicitly released or exposed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51248-126">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="51248-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51248-127">要件</span><span class="sxs-lookup"><span data-stu-id="51248-127">Requirements</span></span>  

 <span data-ttu-id="51248-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="51248-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51248-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51248-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51248-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51248-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51248-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51248-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51248-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="51248-132">See also</span></span>

- [<span data-ttu-id="51248-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="51248-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
