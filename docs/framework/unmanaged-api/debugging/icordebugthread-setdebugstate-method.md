---
title: ICorDebugThread::SetDebugState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: e28d37e4477862ff2ebeeb05ea5f5386e157cd83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678743"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="849ec-102">ICorDebugThread::SetDebugState メソッド</span><span class="sxs-lookup"><span data-stu-id="849ec-102">ICorDebugThread::SetDebugState Method</span></span>

<span data-ttu-id="849ec-103">このスレッドのデバッグ状態を記述するフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="849ec-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="849ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="849ec-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="849ec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="849ec-105">Parameters</span></span>  

 `state`  
 <span data-ttu-id="849ec-106">からこのスレッドのデバッグ状態を指定する CorDebugThreadState 列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="849ec-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="849ec-107">注釈</span><span class="sxs-lookup"><span data-stu-id="849ec-107">Remarks</span></span>  

 <span data-ttu-id="849ec-108">`SetDebugState` スレッドの現在のデバッグ状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="849ec-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="849ec-109">("現在のデバッグ状態" は、プロセスが継続されていて、実際の現在の状態ではない場合は、デバッグ状態を表します)。この場合の通常の値は THREAD_RUN です。</span><span class="sxs-lookup"><span data-stu-id="849ec-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="849ec-110">デバッガーだけが、スレッドのデバッグ状態に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="849ec-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="849ec-111">デバッグ状態は最後まで継続して実行されるので、スレッド THREAD_SUSPENDed を複数回継続したままにする場合は、1回設定するだけで、それ以降は心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="849ec-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="849ec-112">スレッドを中断してプロセスを再開するとデッドロックが発生する可能性がありますが、通常はそうではありません。</span><span class="sxs-lookup"><span data-stu-id="849ec-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="849ec-113">これは、スレッドとプロセスの組み込みの品質であり、設計によるものです。</span><span class="sxs-lookup"><span data-stu-id="849ec-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="849ec-114">デバッガーは、非同期的にスレッドを中断して再開し、デッドロックを解除することができます。</span><span class="sxs-lookup"><span data-stu-id="849ec-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="849ec-115">スレッドのユーザー状態に USER_UNSAFE_POINT が含まれている場合、スレッドはガベージコレクション (GC) をブロックする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="849ec-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="849ec-116">これは、中断されたスレッドがデッドロックの原因となる可能性が非常に高いことを意味します。</span><span class="sxs-lookup"><span data-stu-id="849ec-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="849ec-117">これは、既にキューに登録されているデバッグイベントには影響しません。</span><span class="sxs-lookup"><span data-stu-id="849ec-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="849ec-118">したがって、デバッガーは、スレッドを中断または再開する前に、イベントキュー全体 ( [HasQueuedCallbacks::](icordebugcontroller-hasqueuedcallbacks-method.md)を呼び出すことによって) をドレインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="849ec-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="849ec-119">それ以外の場合は、既に中断されていると思われるスレッドでイベントを取得することがあります。</span><span class="sxs-lookup"><span data-stu-id="849ec-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="849ec-120">要件</span><span class="sxs-lookup"><span data-stu-id="849ec-120">Requirements</span></span>  

 <span data-ttu-id="849ec-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="849ec-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="849ec-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="849ec-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="849ec-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="849ec-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="849ec-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="849ec-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
