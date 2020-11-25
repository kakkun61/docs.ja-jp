---
title: ICorProfilerInfo4::GetFunctionFromIP2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: a522df8abfba1c5837e3136f966935ff1f56d8d2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721544"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a><span data-ttu-id="54922-102">ICorProfilerInfo4::GetFunctionFromIP2 メソッド</span><span class="sxs-lookup"><span data-stu-id="54922-102">ICorProfilerInfo4::GetFunctionFromIP2 Method</span></span>

<span data-ttu-id="54922-103">マネージコード命令ポインターを JIT 再コンパイルされた関数のバージョンにマップします。</span><span class="sxs-lookup"><span data-stu-id="54922-103">Maps a managed code instruction pointer to the JIT-recompiled version of a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54922-104">構文</span><span class="sxs-lookup"><span data-stu-id="54922-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54922-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="54922-105">Parameters</span></span>  

 `ip`  
 <span data-ttu-id="54922-106">からマネージコード内の命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="54922-106">[in] The instruction pointer in managed code.</span></span>  
  
 `pFunctionId`  
 <span data-ttu-id="54922-107">入出力関数 ID。</span><span class="sxs-lookup"><span data-stu-id="54922-107">[out] The function ID.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="54922-108">入出力関数の JIT 再コンパイルバージョンの id。</span><span class="sxs-lookup"><span data-stu-id="54922-108">[out] The identity of the JIT-recompiled version of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54922-109">注釈</span><span class="sxs-lookup"><span data-stu-id="54922-109">Remarks</span></span>  

 <span data-ttu-id="54922-110">`GetFunctionFromIP2` はと似てい `GetFunctionFromIP` ますが、指定された IP アドレスを含む関数の関数 id ではなく、JIT 再コンパイルされた id を取得する点が異なります。</span><span class="sxs-lookup"><span data-stu-id="54922-110">`GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54922-111">`GetFunctionFromIP2` はガベージコレクションをトリガーできますが、で `GetFunctionFromIP` は発生しません。</span><span class="sxs-lookup"><span data-stu-id="54922-111">`GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.</span></span>  <span data-ttu-id="54922-112">詳細については、「 [HRESULT CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54922-112">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54922-113">要件</span><span class="sxs-lookup"><span data-stu-id="54922-113">Requirements</span></span>  

 <span data-ttu-id="54922-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="54922-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54922-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="54922-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="54922-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54922-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54922-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54922-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54922-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="54922-118">See also</span></span>

- [<span data-ttu-id="54922-119">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="54922-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
