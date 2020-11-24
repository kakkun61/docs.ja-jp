---
title: ICorDebugILCode2::GetInstrumentedILMap メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
ms.openlocfilehash: 097502f4321531922d6c4385e2eccbf32f66f026
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688355"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a><span data-ttu-id="4c391-102">ICorDebugILCode2::GetInstrumentedILMap メソッド</span><span class="sxs-lookup"><span data-stu-id="4c391-102">ICorDebugILCode2::GetInstrumentedILMap Method</span></span>

<span data-ttu-id="4c391-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="4c391-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4c391-104">このインスタンスについて、プロファイラー インストルメント中間言語 (IL: intermediate language) オフセットから、元のメソッドの IL オフセットまでのマップを返します。</span><span class="sxs-lookup"><span data-stu-id="4c391-104">Returns a map from profiler-instrumented intermediate language (IL) offsets to original method IL offsets for this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c391-105">構文</span><span class="sxs-lookup"><span data-stu-id="4c391-105">Syntax</span></span>  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c391-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4c391-106">Parameters</span></span>  

 <span data-ttu-id="4c391-107">cMap</span><span class="sxs-lookup"><span data-stu-id="4c391-107">cMap</span></span>  
 <span data-ttu-id="4c391-108">[入力] `map` 配列の記憶容量。</span><span class="sxs-lookup"><span data-stu-id="4c391-108">[in] The storage capacity of the `map` array.</span></span> <span data-ttu-id="4c391-109">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c391-109">See the Remarks section for more information.</span></span>  
  
 <span data-ttu-id="4c391-110">pcMap</span><span class="sxs-lookup"><span data-stu-id="4c391-110">pcMap</span></span>  
 <span data-ttu-id="4c391-111">[出力] マップ配列へ書き込まれる COR_IL_MAP 値の数。</span><span class="sxs-lookup"><span data-stu-id="4c391-111">[out] The number of COR_IL_MAP values written to the map array.</span></span>  
  
 <span data-ttu-id="4c391-112">map</span><span class="sxs-lookup"><span data-stu-id="4c391-112">map</span></span>  
 <span data-ttu-id="4c391-113">[出力] プロファイラー インストルメント IL から元のメソッドである IL へのマッピングについて情報を提供する COR_IL_MAP 値の配列。</span><span class="sxs-lookup"><span data-stu-id="4c391-113">[out] An array of COR_IL_MAP values that provide information on mappings from profiler-instrumented IL to the IL of the original method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c391-114">注釈</span><span class="sxs-lookup"><span data-stu-id="4c391-114">Remarks</span></span>  

 <span data-ttu-id="4c391-115">プロファイラーが [ICorProfilerInfo:: SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) メソッドを呼び出すことによってマッピングを設定した場合、デバッガーはこのメソッドを呼び出してマッピングを取得し、スタックトレースと変数の有効期間の IL オフセットを計算するときに、内部的なマッピングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c391-115">If the profiler sets the mapping by calling the [ICorProfilerInfo::SetILInstrumentedCodeMap](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method, the debugger can call this method to retrieve the mapping and to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
 <span data-ttu-id="4c391-116">`cMap`が0で、 `pcMap` が **null** 以外の場合、 `pcMap` は使用可能な COR_IL_MAP 値の数に設定されます。</span><span class="sxs-lookup"><span data-stu-id="4c391-116">If `cMap` is 0 and `pcMap` is non-**null**, `pcMap` is set to the number of available COR_IL_MAP values.</span></span> <span data-ttu-id="4c391-117">`cMap` が 0 以外の場合は、`map` アレイの記憶容量を表します。</span><span class="sxs-lookup"><span data-stu-id="4c391-117">If `cMap` is non-zero, it represents the storage capacity of the `map` array.</span></span> <span data-ttu-id="4c391-118">メソッドから制御が戻るとき、に `map` は最大項目が含まれて `cMap` おり、 `pcMap` は配列に実際に書き込まれた COR_IL_MAP 値の数に設定され `map` ます。</span><span class="sxs-lookup"><span data-stu-id="4c391-118">When the method returns, `map` contains a maximum of `cMap` items, and `pcMap` is set to the number of COR_IL_MAP values actually written to the `map` array.</span></span>  
  
 <span data-ttu-id="4c391-119">IL がインストルメント化されていない、またはプロファイラーによってマッピングが指定されなかった場合、このメソッドは `S_OK` を返し、`pcMap` を 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="4c391-119">If the IL hasn't been instrumented or the mapping wasn't provided by a profiler, this method returns `S_OK` and sets `pcMap` to 0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c391-120">要件</span><span class="sxs-lookup"><span data-stu-id="4c391-120">Requirements</span></span>  

 <span data-ttu-id="4c391-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c391-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c391-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c391-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c391-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c391-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c391-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c391-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c391-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c391-125">See also</span></span>

- [<span data-ttu-id="4c391-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span><span class="sxs-lookup"><span data-stu-id="4c391-126">ICorProfilerInfo::SetILInstrumentedCodeMap</span></span>](../profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)
- [<span data-ttu-id="4c391-127">ICorDebugILCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c391-127">ICorDebugILCode2 Interface</span></span>](icordebugilcode2-interface.md)
- [<span data-ttu-id="4c391-128">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="4c391-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
