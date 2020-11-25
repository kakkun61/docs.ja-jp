---
title: ICorDebugDataTarget2::CreateVirtualUnwinder メソッド
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 0967b1cda86eab35015279edeed9a6b9852036b6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713939"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="1f379-102">ICorDebugDataTarget2::CreateVirtualUnwinder メソッド</span><span class="sxs-lookup"><span data-stu-id="1f379-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>

<span data-ttu-id="1f379-103">初期コンテキストからアンワインドを開始する新しいスタック アンワインダーを作成します (これは、必ずしもスレッドのリーフではありません)。</span><span class="sxs-lookup"><span data-stu-id="1f379-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f379-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f379-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f379-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f379-105">Parameters</span></span>  

 <span data-ttu-id="1f379-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="1f379-106">nativeThreadID</span></span>  
 <span data-ttu-id="1f379-107">[入力] スタックをアンワインドするスレッドのネイティブ スレッド ID。</span><span class="sxs-lookup"><span data-stu-id="1f379-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="1f379-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="1f379-108">contextFlags</span></span>  
 <span data-ttu-id="1f379-109">[入力] コンテキストのどの部分が `initialContext` で定義されるかを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="1f379-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="1f379-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="1f379-110">cbContext</span></span>  
 <span data-ttu-id="1f379-111">[入力] `initialContext` のサイズ。</span><span class="sxs-lookup"><span data-stu-id="1f379-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="1f379-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="1f379-112">initialContext</span></span>  
 <span data-ttu-id="1f379-113">[入力] コンテキストのデータ。</span><span class="sxs-lookup"><span data-stu-id="1f379-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="1f379-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="1f379-114">ppUnwinder</span></span>  
 <span data-ttu-id="1f379-115">[出力] ICorDebugVirtualUnwinder インターフェイス オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1f379-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f379-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="1f379-116">Return Value</span></span>  

 <span data-ttu-id="1f379-117">正常終了した場合は、`S_OK`。</span><span class="sxs-lookup"><span data-stu-id="1f379-117">`S_OK` if successful.</span></span> <span data-ttu-id="1f379-118">それ以外の `HRESULT` は失敗を示します。</span><span class="sxs-lookup"><span data-stu-id="1f379-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="1f379-119">`HRESULT`Mscordbi.dll によって受信された失敗は、致命的と見なされ、 [ICorDebug](icordebug-interface.md)メソッドによって返さ `CORDBG_E_DATA_TARGET_ERROR` れます。</span><span class="sxs-lookup"><span data-stu-id="1f379-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f379-120">注釈</span><span class="sxs-lookup"><span data-stu-id="1f379-120">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f379-121">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="1f379-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f379-122">要件</span><span class="sxs-lookup"><span data-stu-id="1f379-122">Requirements</span></span>  

 <span data-ttu-id="1f379-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f379-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f379-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f379-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f379-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f379-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f379-126">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f379-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f379-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f379-127">See also</span></span>

- [<span data-ttu-id="1f379-128">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f379-128">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="1f379-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f379-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
