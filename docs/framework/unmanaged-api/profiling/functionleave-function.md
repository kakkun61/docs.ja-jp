---
title: FunctionLeave 関数
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 13636da9c3e8ac4aa9e8dc1fa02b2e33afef4717
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722259"
---
# <a name="functionleave-function"></a><span data-ttu-id="8d0c8-102">FunctionLeave 関数</span><span class="sxs-lookup"><span data-stu-id="8d0c8-102">FunctionLeave Function</span></span>

<span data-ttu-id="8d0c8-103">関数が呼び出し元に戻りようとしていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d0c8-104">`FunctionLeave`関数は、.NET Framework 2.0 では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="8d0c8-105">これは引き続き機能しますが、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="8d0c8-106">代わりに、 [FunctionLeave2](functionleave2-function.md) 関数を使用してください。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-106">Use the [FunctionLeave2](functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d0c8-107">構文</span><span class="sxs-lookup"><span data-stu-id="8d0c8-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d0c8-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8d0c8-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="8d0c8-109">\[in] を返す関数の識別子。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-109">\[in] The identifier of the function that is returning.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d0c8-110">注釈</span><span class="sxs-lookup"><span data-stu-id="8d0c8-110">Remarks</span></span>  

 <span data-ttu-id="8d0c8-111">`FunctionLeave`関数はコールバックであるため、実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="8d0c8-112">実装では、 `__declspec` ( `naked` ) ストレージクラス属性を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="8d0c8-113">この関数を呼び出す前に、実行エンジンはレジスタを保存しません。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="8d0c8-114">入力時には、浮動小数点単位 (FPU) に含まれるすべてのレジスタを含め、使用するすべてのレジスタを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="8d0c8-115">終了時に、呼び出し元によってプッシュされたすべてのパラメーターをポップして、スタックを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="8d0c8-116">の実装は、 `FunctionLeave` ガベージコレクションを遅延させるため、ブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="8d0c8-117">スタックがガベージコレクションに対応していない可能性があるため、この実装ではガベージコレクションを実行しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="8d0c8-118">ガベージコレクションが試行された場合、ランタイムはが返されるまでブロックし `FunctionLeave` ます。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="8d0c8-119">また、 `FunctionLeave` 関数はマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d0c8-120">要件</span><span class="sxs-lookup"><span data-stu-id="8d0c8-120">Requirements</span></span>  

 <span data-ttu-id="8d0c8-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d0c8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d0c8-122">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="8d0c8-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="8d0c8-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d0c8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d0c8-124">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="8d0c8-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d0c8-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d0c8-125">See also</span></span>

- [<span data-ttu-id="8d0c8-126">FunctionEnter2 関数</span><span class="sxs-lookup"><span data-stu-id="8d0c8-126">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="8d0c8-127">FunctionLeave2 関数</span><span class="sxs-lookup"><span data-stu-id="8d0c8-127">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="8d0c8-128">FunctionTailcall2 関数</span><span class="sxs-lookup"><span data-stu-id="8d0c8-128">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="8d0c8-129">SetEnterLeaveFunctionHooks2 メソッド</span><span class="sxs-lookup"><span data-stu-id="8d0c8-129">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="8d0c8-130">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="8d0c8-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
