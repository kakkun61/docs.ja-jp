---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished メソッド
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 6354667e754da42692cc0de2dc5330c56f951aa1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725444"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="ea2e2-102">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="ea2e2-102">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>

<span data-ttu-id="ea2e2-103">[.NET Framework 4.7 以降のバージョンでサポートされています]</span><span class="sxs-lookup"><span data-stu-id="ea2e2-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="ea2e2-104">動的メソッドの JIT コンパイルが完了するたびにプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-104">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="ea2e2-105">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea2e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea2e2-106">Parameters</span></span>  

<span data-ttu-id="ea2e2-107">[入力] `functionId`</span><span class="sxs-lookup"><span data-stu-id="ea2e2-107">[in] `functionId`</span></span>  
<span data-ttu-id="ea2e2-108">JIT コンパイルが開始されるメモリ内関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="ea2e2-109">[入力] `hrStatus` JIT コンパイルが成功したかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-109">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="ea2e2-110">[入力] `fIsSafeToBlock` 
 `true`ブロックが原因で、ランタイムが呼び出し元のスレッドがこのコールバックから戻るのを待機する場合があることを示します。`false`ブロックがランタイムの動作に影響を与えないことを示す場合。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-110">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="ea2e2-111">注釈</span><span class="sxs-lookup"><span data-stu-id="ea2e2-111">Remarks</span></span>  

<span data-ttu-id="ea2e2-112">このコールバックは、動的メソッドの JIT コンパイルが完了するたびにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-112">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="ea2e2-113">これには、さまざまな IL スタブおよび LCG メソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-113">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="ea2e2-114">その目的は、コンパイルされたメソッドをユーザーに識別するのに十分な情報をプロファイラーライターに提供することです。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-114">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="ea2e2-115">`functionId` 動的メソッドにはメタデータがないため、値を使用してメタデータトークンを解決することはできません。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-115">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea2e2-116">要件</span><span class="sxs-lookup"><span data-stu-id="ea2e2-116">Requirements</span></span>  

 <span data-ttu-id="ea2e2-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea2e2-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea2e2-118">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea2e2-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea2e2-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea2e2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea2e2-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea2e2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2e2-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea2e2-121">See also</span></span>

- [<span data-ttu-id="ea2e2-122">DynamicMethodJITCompilationStarted メソッド</span><span class="sxs-lookup"><span data-stu-id="ea2e2-122">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="ea2e2-123">ICorProfilerCallback8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea2e2-123">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
