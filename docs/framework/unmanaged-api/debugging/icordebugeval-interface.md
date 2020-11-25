---
title: ICorDebugEval インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
ms.openlocfilehash: 5d8fd79b242f2b88b82c5c3d78dfe45d80f1194f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729786"
---
# <a name="icordebugeval-interface"></a><span data-ttu-id="72b6c-102">ICorDebugEval インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72b6c-102">ICorDebugEval Interface</span></span>

<span data-ttu-id="72b6c-103">デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="72b6c-103">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72b6c-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-104">Methods</span></span>  
  
|<span data-ttu-id="72b6c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-105">Method</span></span>|<span data-ttu-id="72b6c-106">説明</span><span class="sxs-lookup"><span data-stu-id="72b6c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72b6c-107">Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-107">Abort Method</span></span>](icordebugeval-abort-method.md)|<span data-ttu-id="72b6c-108">このオブジェクトが現在実行している計算を中止し `ICorDebugEval` ます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-108">Aborts the computation this `ICorDebugEval` object is currently performing.</span></span>|  
|[<span data-ttu-id="72b6c-109">CallFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-109">CallFunction Method</span></span>](icordebugeval-callfunction-method.md)|<span data-ttu-id="72b6c-110">指定された関数の呼び出しを設定します。</span><span class="sxs-lookup"><span data-stu-id="72b6c-110">Sets up a call to the specified function.</span></span> <span data-ttu-id="72b6c-111">(.NET Framework バージョン2.0 で廃止されました。代わりに [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) を使用してください。)</span><span class="sxs-lookup"><span data-stu-id="72b6c-111">(Obsolete in the .NET Framework version 2.0; use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.)</span></span>|  
|[<span data-ttu-id="72b6c-112">CreateValue メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-112">CreateValue Method</span></span>](icordebugeval-createvalue-method.md)|<span data-ttu-id="72b6c-113">初期値0または null を指定して、指定した型の "ICorDebugValue" オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="72b6c-113">Gets an interface pointer to an "ICorDebugValue" object of the specified type, with an initial value of zero or null.</span></span> <span data-ttu-id="72b6c-114">(.NET Framework 2.0 で廃止されました。代わりに [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) を使用してください。)</span><span class="sxs-lookup"><span data-stu-id="72b6c-114">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.)</span></span>|  
|[<span data-ttu-id="72b6c-115">GetResult メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-115">GetResult Method</span></span>](icordebugeval-getresult-method.md)|<span data-ttu-id="72b6c-116">評価の結果を格納しているへのインターフェイスポインターを取得し `ICorDebugValue` ます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-116">Gets an interface pointer to an `ICorDebugValue` that contains the results of the evaluation.</span></span>|  
|[<span data-ttu-id="72b6c-117">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-117">GetThread Method</span></span>](icordebugeval-getthread-method.md)|<span data-ttu-id="72b6c-118">この評価が実行されているか実行される "表示スレッド" へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="72b6c-118">Gets an interface pointer to the "ICorDebugThread" where this evaluation is executing or will execute.</span></span>|  
|[<span data-ttu-id="72b6c-119">IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-119">IsActive Method</span></span>](icordebugeval-isactive-method.md)|<span data-ttu-id="72b6c-120">このオブジェクトが現在実行中かどうかを示す値を取得し `ICorDebugEval` ます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-120">Gets a value that indicates whether this `ICorDebugEval` object is currently executing.</span></span>|  
|[<span data-ttu-id="72b6c-121">NewArray メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-121">NewArray Method</span></span>](icordebugeval-newarray-method.md)|<span data-ttu-id="72b6c-122">指定した要素の型と次元の新しい配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-122">Allocates a new array of the specified element type and dimensions.</span></span> <span data-ttu-id="72b6c-123">(.NET Framework 2.0 で廃止されました。代わりに [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) を使用してください。)</span><span class="sxs-lookup"><span data-stu-id="72b6c-123">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.)</span></span>|  
|[<span data-ttu-id="72b6c-124">NewObject メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-124">NewObject Method</span></span>](icordebugeval-newobject-method.md)|<span data-ttu-id="72b6c-125">新しいオブジェクトインスタンスを割り当て、指定したコンストラクターメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="72b6c-125">Allocates a new object instance and calls the specified constructor method.</span></span> <span data-ttu-id="72b6c-126">(.NET Framework 2.0 で廃止されました。代わりに [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) を使用してください。)</span><span class="sxs-lookup"><span data-stu-id="72b6c-126">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.)</span></span>|  
|[<span data-ttu-id="72b6c-127">NewObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-127">NewObjectNoConstructor Method</span></span>](icordebugeval-newobjectnoconstructor-method.md)|<span data-ttu-id="72b6c-128">コンストラクターメソッドを呼び出さずに、指定した型の新しいオブジェクトインスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-128">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span> <span data-ttu-id="72b6c-129">(.NET Framework 2.0 で廃止されました。代わりに [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) を使用してください。)</span><span class="sxs-lookup"><span data-stu-id="72b6c-129">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.)</span></span>|  
|[<span data-ttu-id="72b6c-130">NewString メソッド</span><span class="sxs-lookup"><span data-stu-id="72b6c-130">NewString Method</span></span>](icordebugeval-newstring-method.md)|<span data-ttu-id="72b6c-131">指定された内容を持つ新しい文字列オブジェクトを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-131">Allocates a new string object with the specified contents.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72b6c-132">注釈</span><span class="sxs-lookup"><span data-stu-id="72b6c-132">Remarks</span></span>  

 <span data-ttu-id="72b6c-133">`ICorDebugEval`オブジェクトは、評価を実行するために使用される特定のスレッドのコンテキストで作成されます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-133">An `ICorDebugEval` object is created in the context of a specific thread that is used to perform the evaluations.</span></span> <span data-ttu-id="72b6c-134">特定の評価で使用されるすべてのオブジェクトと型は、同じアプリケーションドメイン内に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72b6c-134">All objects and types used in a given evaluation must reside within the same application domain.</span></span> <span data-ttu-id="72b6c-135">このアプリケーションドメインは、スレッドの現在のアプリケーションドメインと同じである必要はありません。</span><span class="sxs-lookup"><span data-stu-id="72b6c-135">That application domain need not be the same as the current application domain of the thread.</span></span> <span data-ttu-id="72b6c-136">評価は入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-136">Evaluations can be nested.</span></span>  
  
 <span data-ttu-id="72b6c-137">評価の操作が完了しないのは、デバッガーが "を実行してい [ます:: Continue](icordebugcontroller-continue-method.md)" というメッセージを呼び出し、次に、"は、" は、"は、" のようなコール [バック](icordebugmanagedcallback-evalcomplete-method.md) を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="72b6c-137">The evaluation's operations do not complete until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md), and then receives an [ICorDebugManagedCallback::EvalComplete](icordebugmanagedcallback-evalcomplete-method.md) callback.</span></span> <span data-ttu-id="72b6c-138">他のスレッドの実行を許可せずに評価機能を使用する必要がある場合は、"が表示されない[ようにし](icordebugcontroller-stop-method.md)てください:: [SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md)またはのいずれかを使用してスレッドを中断する::[続行](icordebugcontroller-continue-method.md)します。</span><span class="sxs-lookup"><span data-stu-id="72b6c-138">If you need to use the evaluation functionality without allowing other threads to run, suspend the threads by using either [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) or [ICorDebugController::Stop](icordebugcontroller-stop-method.md) before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
 <span data-ttu-id="72b6c-139">評価の進行中にユーザーコードが実行されているので、クラスの読み込みやブレークポイントなどのデバッグイベントが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72b6c-139">Because user code is running when the evaluation is in progress, any debug events can occur, including class loads and breakpoints.</span></span> <span data-ttu-id="72b6c-140">デバッガーは、これらのイベントに対して通常どおりコールバックを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="72b6c-140">The debugger will receive callbacks, as normal, for these events.</span></span> <span data-ttu-id="72b6c-141">評価の状態は、通常のプログラムの状態の検査の一部として表示されます。</span><span class="sxs-lookup"><span data-stu-id="72b6c-141">The state of the evaluation will be seen as part of the inspection of the normal program state.</span></span> <span data-ttu-id="72b6c-142">スタックチェーンはチェーンになり `CHAIN_FUNC_EVAL` ます ("CorDebugStepReason" 列挙型と、「の場合は、" [: getreason](icordebugchain-getreason-method.md) " メソッドを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="72b6c-142">The stack chain will be a `CHAIN_FUNC_EVAL` chain (see the "CorDebugStepReason" enumeration and the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method).</span></span> <span data-ttu-id="72b6c-143">完全なデバッガー API は通常どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="72b6c-143">The full debugger API will continue to operate as normal.</span></span>  
  
 <span data-ttu-id="72b6c-144">デッドロックまたは無限ループの状態が発生した場合、ユーザーコードが完全に完了することはありません。</span><span class="sxs-lookup"><span data-stu-id="72b6c-144">If a deadlocked or infinite looping situation arises, the user code may never complete.</span></span> <span data-ttu-id="72b6c-145">このような場合は、プログラムを再開する前に、「いいね! [: Abort](icordebugeval-abort-method.md) 」を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="72b6c-145">In such a case, you must call [ICorDebugEval::Abort](icordebugeval-abort-method.md) before resuming the program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72b6c-146">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="72b6c-146">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72b6c-147">要件</span><span class="sxs-lookup"><span data-stu-id="72b6c-147">Requirements</span></span>  

 <span data-ttu-id="72b6c-148">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="72b6c-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72b6c-149">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72b6c-149">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72b6c-150">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72b6c-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72b6c-151">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72b6c-151">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b6c-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="72b6c-152">See also</span></span>

- [<span data-ttu-id="72b6c-153">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="72b6c-153">Debugging Interfaces</span></span>](debugging-interfaces.md)
