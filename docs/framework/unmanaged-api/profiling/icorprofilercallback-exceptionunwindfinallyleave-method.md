---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: e02716350aa2bf32bdd7c4b2e01841405de6dc14
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720400"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="f7cad-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="f7cad-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>

<span data-ttu-id="f7cad-103">例外処理のアンワインドフェーズが句の後にあることをプロファイラーに通知し `finally` ます。</span><span class="sxs-lookup"><span data-stu-id="f7cad-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7cad-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7cad-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="f7cad-105">解説</span><span class="sxs-lookup"><span data-stu-id="f7cad-105">Remarks</span></span>  

 <span data-ttu-id="f7cad-106">スタックがガベージコレクションを許可する状態ではなく、したがって、プリエンプティブガベージコレクションを有効にできないため、この呼び出し中にプロファイラーはブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="f7cad-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="f7cad-107">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="f7cad-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="f7cad-108">また、この呼び出しでは、プロファイラーはマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="f7cad-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7cad-109">要件</span><span class="sxs-lookup"><span data-stu-id="f7cad-109">Requirements</span></span>  

 <span data-ttu-id="f7cad-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7cad-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7cad-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7cad-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7cad-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7cad-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7cad-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7cad-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7cad-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7cad-114">See also</span></span>

- [<span data-ttu-id="f7cad-115">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7cad-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="f7cad-116">ExceptionUnwindFinallyEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="f7cad-116">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
