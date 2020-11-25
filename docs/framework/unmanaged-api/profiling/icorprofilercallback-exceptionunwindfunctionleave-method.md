---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 9f88a3fde7d7cb5941e3a7f44a7d94056a959ab8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733920"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="492e0-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="492e0-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>

<span data-ttu-id="492e0-103">例外処理のアンワインドフェーズが関数のアンワインドを完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="492e0-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="492e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="492e0-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="492e0-105">解説</span><span class="sxs-lookup"><span data-stu-id="492e0-105">Remarks</span></span>  

 <span data-ttu-id="492e0-106">`ExceptionUnwindFunctionLeave`メソッドが呼び出されると、関数インスタンスとそのスタックデータがスタックから削除されます。</span><span class="sxs-lookup"><span data-stu-id="492e0-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="492e0-107">スタックがガベージコレクションを許可する状態ではなく、したがって、プリエンプティブガベージコレクションを有効にできないため、この呼び出し中にプロファイラーはブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="492e0-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="492e0-108">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="492e0-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="492e0-109">また、この呼び出しでは、プロファイラーはマネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="492e0-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="492e0-110">要件</span><span class="sxs-lookup"><span data-stu-id="492e0-110">Requirements</span></span>  

 <span data-ttu-id="492e0-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="492e0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="492e0-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="492e0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="492e0-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="492e0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="492e0-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="492e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="492e0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="492e0-115">See also</span></span>

- [<span data-ttu-id="492e0-116">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="492e0-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="492e0-117">ExceptionUnwindFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="492e0-117">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
