---
title: ICorDebugEval2::RudeAbort メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
ms.openlocfilehash: 478772925dfb7ca7389b5267433f9b06ace3d5a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729617"
---
# <a name="icordebugeval2rudeabort-method"></a><span data-ttu-id="2cbf5-102">ICorDebugEval2::RudeAbort メソッド</span><span class="sxs-lookup"><span data-stu-id="2cbf5-102">ICorDebugEval2::RudeAbort Method</span></span>

<span data-ttu-id="2cbf5-103">このが現在実行している計算を中止し `ICorDebugEval2` ます。</span><span class="sxs-lookup"><span data-stu-id="2cbf5-103">Aborts the computation that this `ICorDebugEval2` is currently performing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbf5-104">構文</span><span class="sxs-lookup"><span data-stu-id="2cbf5-104">Syntax</span></span>  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="2cbf5-105">解説</span><span class="sxs-lookup"><span data-stu-id="2cbf5-105">Remarks</span></span>  

 <span data-ttu-id="2cbf5-106">`RudeAbort` は、エバリュエーターによって保持されているロックを解放しないため、デバッグセッションは安全ではない状態のままになります。</span><span class="sxs-lookup"><span data-stu-id="2cbf5-106">`RudeAbort` does not release any locks that the evaluator holds, so it leaves the debugging session in an unsafe state.</span></span> <span data-ttu-id="2cbf5-107">このメソッドは細心の注意を払って呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="2cbf5-107">Call this method with extreme caution.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cbf5-108">要件</span><span class="sxs-lookup"><span data-stu-id="2cbf5-108">Requirements</span></span>  

 <span data-ttu-id="2cbf5-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2cbf5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cbf5-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cbf5-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cbf5-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cbf5-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cbf5-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cbf5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
