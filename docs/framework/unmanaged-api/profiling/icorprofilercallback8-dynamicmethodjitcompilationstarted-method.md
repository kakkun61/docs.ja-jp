---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 46a25fc6e9119481f728275e0569429cc6c46dc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725431"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="a6201-102">ICorProfilerCallback8::D ynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="a6201-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>

<span data-ttu-id="a6201-103">[.NET Framework 4.7 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="a6201-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="a6201-104">動的メソッドの JIT コンパイルが開始されるたびにプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a6201-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6201-105">構文</span><span class="sxs-lookup"><span data-stu-id="a6201-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6201-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6201-106">Parameters</span></span>  

<span data-ttu-id="a6201-107">[入力] `functionId`</span><span class="sxs-lookup"><span data-stu-id="a6201-107">[in] `functionId`</span></span>  
<span data-ttu-id="a6201-108">JIT コンパイルが開始されるメモリ内関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="a6201-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="a6201-109">[入力] `fIsSafeToBlock` 
 `true`ブロックが原因で、ランタイムが呼び出し元のスレッドがこのコールバックから戻るのを待機する場合があることを示します。`false`ブロックがランタイムの動作に影響を与えないことを示す場合。</span><span class="sxs-lookup"><span data-stu-id="a6201-109">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="a6201-110">[入力] `pILHeader` メソッドの IL ヘッダーの最初のバイトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6201-110">[in] `pILHeader` A pointer to the first byte of the method's IL header.</span></span>

<span data-ttu-id="a6201-111">[入力] `cbILHeader` IL ヘッダー内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="a6201-111">[in] `cbILHeader` The number of bytes in the IL header.</span></span>

## <a name="remarks"></a><span data-ttu-id="a6201-112">注釈</span><span class="sxs-lookup"><span data-stu-id="a6201-112">Remarks</span></span>  

<span data-ttu-id="a6201-113">このコールバックは、動的メソッドが JIT コンパイルされるたびにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="a6201-113">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="a6201-114">これには、さまざまな IL スタブおよび LCG メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a6201-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="a6201-115">その目的は、コンパイルされたメソッドをユーザーに識別するのに十分な情報をプロファイラーライターに提供することです。</span><span class="sxs-lookup"><span data-stu-id="a6201-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="a6201-116">`functionId` 動的メソッドにはメタデータがないため、値を使用してメタデータトークンを解決することはできません。</span><span class="sxs-lookup"><span data-stu-id="a6201-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="a6201-117">`pILHeader`ポインターは、コールバック中にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="a6201-117">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="a6201-118">要件</span><span class="sxs-lookup"><span data-stu-id="a6201-118">Requirements</span></span>  

 <span data-ttu-id="a6201-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a6201-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6201-120">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6201-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6201-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6201-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6201-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a6201-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6201-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6201-123">See also</span></span>

- [<span data-ttu-id="a6201-124">DynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="a6201-124">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [<span data-ttu-id="a6201-125">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6201-125">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
