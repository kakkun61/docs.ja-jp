---
title: ICorDebugVirtualUnwinder::GetContext メソッド
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: a5a1afa47e52eff7c930698a3354a03d8c62259f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679456"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="68840-102">ICorDebugVirtualUnwinder::GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="68840-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>

<span data-ttu-id="68840-103">このアンワインダーの現在のコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="68840-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68840-104">構文</span><span class="sxs-lookup"><span data-stu-id="68840-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68840-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68840-105">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="68840-106">[in] (WinNT.h で定義されている) コンテキストのどの部分を返すかを指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="68840-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="68840-107">[in] `contextBuf` のバイト数。</span><span class="sxs-lookup"><span data-stu-id="68840-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="68840-108">[out] `contextBuf` に実際に書き込まれたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="68840-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="68840-109">[out] このアンワインダーの現在のコンテキストが格納されているバイト配列。</span><span class="sxs-lookup"><span data-stu-id="68840-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68840-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="68840-110">Return Value</span></span>  

 <span data-ttu-id="68840-111">mscordbi によって受信された失敗を示す HRESULT 値は致命的と見なされ、ICorDebug API によって `CORDBG_E_DATA_TARGET_ERROR` が返されます。</span><span class="sxs-lookup"><span data-stu-id="68840-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68840-112">注釈</span><span class="sxs-lookup"><span data-stu-id="68840-112">Remarks</span></span>  

 <span data-ttu-id="68840-113">引数の初期値は、「 `contextBuf` [GetContext](icordebugstackwalk-getcontext-method.md) 」メソッドを呼び出すことによって返されるコンテキストバッファーに設定します。</span><span class="sxs-lookup"><span data-stu-id="68840-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="68840-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="68840-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="68840-115">アンワインドではレジスタのサブセット (例: 不揮発性レジスタのみ) だけが復元されるため、コンテキストが、実際のメソッド呼び出し時点でのレジスタの状態と正確には一致しないことがあります。</span><span class="sxs-lookup"><span data-stu-id="68840-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68840-116">要件</span><span class="sxs-lookup"><span data-stu-id="68840-116">Requirements</span></span>  

 <span data-ttu-id="68840-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68840-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68840-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68840-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68840-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68840-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68840-120">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68840-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68840-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="68840-121">See also</span></span>

- [<span data-ttu-id="68840-122">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68840-122">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="68840-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="68840-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
