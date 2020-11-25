---
title: ICorDebugILFrame3::GetReturnValueForILOffset メソッド
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
api_name:
- ICorDebugILFrame3.GetReturnValueForILOffset
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type:
- apiref
ms.openlocfilehash: 11207298b071527151535144330790df767c2101
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725002"
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a><span data-ttu-id="d895e-102">ICorDebugILFrame3::GetReturnValueForILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="d895e-102">ICorDebugILFrame3::GetReturnValueForILOffset Method</span></span>

<span data-ttu-id="d895e-103">関数の戻り値をカプセル化する "ICorDebugValue" オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="d895e-103">Gets an "ICorDebugValue" object that encapsulates the return value of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d895e-104">構文</span><span class="sxs-lookup"><span data-stu-id="d895e-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d895e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d895e-105">Parameters</span></span>  

 `ILOffset`  
 <span data-ttu-id="d895e-106">オフセット IL。</span><span class="sxs-lookup"><span data-stu-id="d895e-106">The IL offset.</span></span> <span data-ttu-id="d895e-107">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d895e-107">See the Remarks section.</span></span>  
  
 `ppReturnValue`  
 <span data-ttu-id="d895e-108">関数呼び出しの戻り値に関する情報を提供する "ICorDebugValue" インターフェイスオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d895e-108">A pointer to the address of an "ICorDebugValue" interface object that provides information about the return value of a function call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d895e-109">注釈</span><span class="sxs-lookup"><span data-stu-id="d895e-109">Remarks</span></span>  

 <span data-ttu-id="d895e-110">このメソッドは、メソッドの戻り値を取得するために、 [ICorDebugCode3:: Getreturnvalu Veoffset](icordebugcode3-getreturnvalueliveoffset-method.md) メソッドと共に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d895e-110">This method is used along with the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method to get the return value of a method.</span></span> <span data-ttu-id="d895e-111">次の 2 つのコード例で示すように、これは戻り値が無視されるメソッドの場合に特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d895e-111">It is particularly useful in the case of methods whose return values are ignored, as in the following two code examples.</span></span> <span data-ttu-id="d895e-112">1 番目の例では、<xref:System.Int32.TryParse%2A?displayProperty=nameWithType> メソッドを呼び出しますが、メソッドの戻り値を無視します。</span><span class="sxs-lookup"><span data-stu-id="d895e-112">The first example calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method, but ignores the method's return value.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 <span data-ttu-id="d895e-113">2 番目の例は、より一般的なデバッグの問題を示しています。</span><span class="sxs-lookup"><span data-stu-id="d895e-113">The second example illustrates a much more common problem in debugging.</span></span> <span data-ttu-id="d895e-114">メソッド呼び出しで引数としてメソッドが使用されるため、デバッガーで呼び出されたメソッドをステップ実行する場合に限り、戻り値にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d895e-114">Because a method is used as an argument in a method call, its return value is accessible only when the debugger steps through the called method.</span></span> <span data-ttu-id="d895e-115">多くの場合、特に呼び出されたメソッドが外部ライブラリで定義されている場合にはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="d895e-115">In many cases, particularly when the called method is defined in an external library, that is not possible.</span></span>  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 <span data-ttu-id="d895e-116">[ICorDebugCode3:: Getreturnvalu veoffset](icordebugcode3-getreturnvalueliveoffset-method.md)メソッドに関数呼び出しサイトへの IL オフセットを渡すと、1つ以上のネイティブオフセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="d895e-116">If you pass the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method an IL offset to a function call site, it returns one or more native offsets.</span></span> <span data-ttu-id="d895e-117">これによってデバッガーは、関数内のこうしたネイティブ オフセット上でブレークポイントを設定できます。</span><span class="sxs-lookup"><span data-stu-id="d895e-117">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="d895e-118">デバッガーがいずれかのブレークポイントに到達すると、戻り値を取得するためにこのメソッドに同じ IL オフセットを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d895e-118">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to get the return value.</span></span> <span data-ttu-id="d895e-119">この場合、デバッガーは設定したブレークポイントすべてをクリアする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d895e-119">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d895e-120">[ICorDebugCode3:: Getreturnvalu Veoffset メソッド](icordebugcode3-getreturnvalueliveoffset-method.md)とメソッドを使用すると、 `ICorDebugILFrame3::GetReturnValueForILOffset` 参照型の戻り値の情報のみを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d895e-120">The [ICorDebugCode3::GetReturnValueLiveOffset Method](icordebugcode3-getreturnvalueliveoffset-method.md) and `ICorDebugILFrame3::GetReturnValueForILOffset` methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="d895e-121">値型 (つまり、<xref:System.ValueType> から派生するすべての型) からの戻り値情報の取得はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d895e-121">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="d895e-122">パラメーターで指定された IL オフセットは `ILOffset` 関数呼び出しサイトに存在する必要があります。また、同じ il オフセットの [ICorDebugCode3:: Getreturnvalu veoffset](icordebugcode3-getreturnvalueliveoffset-method.md) メソッドによって返されるネイティブオフセットに設定されているブレークポイントで、デバッグ対象を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d895e-122">The IL offset specified by the `ILOffset` parameter should be at a function call site, and the debuggee should be stopped at a breakpoint set at the native offset returned by the [ICorDebugCode3::GetReturnValueLiveOffset](icordebugcode3-getreturnvalueliveoffset-method.md) method for the same IL offset.</span></span> <span data-ttu-id="d895e-123">デバッグ対象が指定の IL オフセットに対して正確な場所で停止しない場合、API は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d895e-123">If the debuggee is not stopped at the correct location for the specified IL offset, the API will fail.</span></span>  
  
 <span data-ttu-id="d895e-124">関数呼び出しで値が返されない場合、API は失敗します。</span><span class="sxs-lookup"><span data-stu-id="d895e-124">If the function call doesn't return a value, the API will fail.</span></span>  
  
 <span data-ttu-id="d895e-125">`ICorDebugILFrame3::GetReturnValueForILOffset` メソッドは、x86 ベースおよび AMD64 システムでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="d895e-125">The `ICorDebugILFrame3::GetReturnValueForILOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d895e-126">要件</span><span class="sxs-lookup"><span data-stu-id="d895e-126">Requirements</span></span>  

 <span data-ttu-id="d895e-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d895e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d895e-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d895e-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d895e-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d895e-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d895e-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d895e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d895e-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d895e-131">See also</span></span>

- [<span data-ttu-id="d895e-132">GetReturnValueLiveOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="d895e-132">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)
- [<span data-ttu-id="d895e-133">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d895e-133">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
