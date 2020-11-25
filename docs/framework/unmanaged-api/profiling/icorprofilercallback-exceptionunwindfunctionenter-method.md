---
title: ICorProfilerCallback::ExceptionUnwindFunctionEnter メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionEnter method [.NET Framework profiling]
- ExceptionUnwindFunctionEnter method [.NET Framework profiling]
ms.assetid: ea3dc625-5650-4bf4-8e67-01e42be065b1
topic_type:
- apiref
ms.openlocfilehash: d3a09a6caf3febd04296fce518ade42e8676a4b8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731008"
---
# <a name="icorprofilercallbackexceptionunwindfunctionenter-method"></a><span data-ttu-id="2b969-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="2b969-102">ICorProfilerCallback::ExceptionUnwindFunctionEnter Method</span></span>

<span data-ttu-id="2b969-103">例外処理のアンワインドフェーズが関数のアンワインドを開始したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2b969-103">Notifies the profiler that the unwind phase of exception handling has begun to unwind a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b969-104">構文</span><span class="sxs-lookup"><span data-stu-id="2b969-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b969-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2b969-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="2b969-106">\[in] アンワインドされている関数の ID。</span><span class="sxs-lookup"><span data-stu-id="2b969-106">\[in] The ID of the function that is being unwound.</span></span>

## <a name="remarks"></a><span data-ttu-id="2b969-107">注釈</span><span class="sxs-lookup"><span data-stu-id="2b969-107">Remarks</span></span>  

 <span data-ttu-id="2b969-108">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="2b969-108">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="2b969-109">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="2b969-109">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="2b969-110">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="2b969-110">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b969-111">要件</span><span class="sxs-lookup"><span data-stu-id="2b969-111">Requirements</span></span>  

 <span data-ttu-id="2b969-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b969-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b969-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b969-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b969-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b969-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b969-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b969-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b969-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b969-116">See also</span></span>

- [<span data-ttu-id="2b969-117">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2b969-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2b969-118">ExceptionUnwindFunctionLeave メソッド</span><span class="sxs-lookup"><span data-stu-id="2b969-118">ExceptionUnwindFunctionLeave Method</span></span>](icorprofilercallback-exceptionunwindfunctionleave-method.md)
