---
title: ICorProfilerCallback::JITFunctionPitched メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: 51fec26837b3c7f0a0328a7b64ff4a02148283da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725513"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="0cf59-102">ICorProfilerCallback::JITFunctionPitched メソッド</span><span class="sxs-lookup"><span data-stu-id="0cf59-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>

<span data-ttu-id="0cf59-103">Just-in-time (JIT) でコンパイルされた関数がメモリから削除されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="0cf59-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cf59-104">構文</span><span class="sxs-lookup"><span data-stu-id="0cf59-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cf59-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0cf59-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="0cf59-106">から削除された関数の ID。</span><span class="sxs-lookup"><span data-stu-id="0cf59-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cf59-107">注釈</span><span class="sxs-lookup"><span data-stu-id="0cf59-107">Remarks</span></span>  

 <span data-ttu-id="0cf59-108">削除された関数が呼び出されると、関数が再コンパイルされると、プロファイラーは新しい JIT コンパイルイベントを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0cf59-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="0cf59-109">現在、共通言語ランタイム (CLR) の JIT コンパイラでは、メモリから関数が削除されないため、このコールバックは現在使用されていないため、プロファイラーによって受信されません。</span><span class="sxs-lookup"><span data-stu-id="0cf59-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="0cf59-110">の値 `functionId` は、関数が再コンパイルされるまで有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="0cf59-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="0cf59-111">関数を再コンパイルすると、同じ `functionId` 値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0cf59-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cf59-112">要件</span><span class="sxs-lookup"><span data-stu-id="0cf59-112">Requirements</span></span>  

 <span data-ttu-id="0cf59-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0cf59-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cf59-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0cf59-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0cf59-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cf59-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cf59-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf59-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf59-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="0cf59-117">See also</span></span>

- [<span data-ttu-id="0cf59-118">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0cf59-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
