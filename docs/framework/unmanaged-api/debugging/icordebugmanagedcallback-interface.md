---
title: ICorDebugManagedCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
ms.openlocfilehash: 6eebabc3a08027eab4ac55c1e46dd75b1f75bd21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679703"
---
# <a name="icordebugmanagedcallback-interface"></a><span data-ttu-id="e40bc-102">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e40bc-102">ICorDebugManagedCallback Interface</span></span>

<span data-ttu-id="e40bc-103">デバッガーのコールバックを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-103">Provides methods to process debugger callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e40bc-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-104">Methods</span></span>  
  
|<span data-ttu-id="e40bc-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-105">Method</span></span>|<span data-ttu-id="e40bc-106">説明</span><span class="sxs-lookup"><span data-stu-id="e40bc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e40bc-107">Break メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-107">Break Method</span></span>](icordebugmanagedcallback-break-method.md)|<span data-ttu-id="e40bc-108"><xref:System.Reflection.Emit.OpCodes.Break>コードストリーム内の命令が実行されたときに、デバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-108">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>|  
|[<span data-ttu-id="e40bc-109">Breakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-109">Breakpoint Method</span></span>](icordebugmanagedcallback-breakpoint-method.md)|<span data-ttu-id="e40bc-110">ブレークポイントが検出されたときにデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-110">Notifies the debugger when a breakpoint is encountered.</span></span>|  
|[<span data-ttu-id="e40bc-111">BreakpointSetError メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-111">BreakpointSetError Method</span></span>](icordebugmanagedcallback-breakpointseterror-method.md)|<span data-ttu-id="e40bc-112">関数が just-in-time (JIT) コンパイルされる前に設定されたブレークポイントを共通言語ランタイム (CLR) が正しくバインドできなかったことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-112">Notifies the debugger that the common language runtime (CLR) was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>|  
|[<span data-ttu-id="e40bc-113">ControlCTrap メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-113">ControlCTrap Method</span></span>](icordebugmanagedcallback-controlctrap-method.md)|<span data-ttu-id="e40bc-114">デバッグ中のプロセスで CTRL + C がトラップされることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-114">Notifies the debugger that a CTRL+C is trapped in the process being debugged.</span></span>|  
|[<span data-ttu-id="e40bc-115">CreateAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-115">CreateAppDomain Method</span></span>](icordebugmanagedcallback-createappdomain-method.md)|<span data-ttu-id="e40bc-116">アプリケーションドメインが作成されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-116">Notifies the debugger that an application domain has been created.</span></span>|  
|[<span data-ttu-id="e40bc-117">CreateProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-117">CreateProcess Method</span></span>](icordebugmanagedcallback-createprocess-method.md)|<span data-ttu-id="e40bc-118">プロセスが初めてアタッチまたは開始されたときにデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-118">Notifies the debugger when a process has been attached or started for the first time.</span></span>|  
|[<span data-ttu-id="e40bc-119">CreateThread メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-119">CreateThread Method</span></span>](icordebugmanagedcallback-createthread-method.md)|<span data-ttu-id="e40bc-120">スレッドがマネージコードの実行を開始したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-120">Notifies the debugger that a thread has started executing managed code.</span></span>|  
|[<span data-ttu-id="e40bc-121">DebuggerError メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-121">DebuggerError Method</span></span>](icordebugmanagedcallback-debuggererror-method.md)|<span data-ttu-id="e40bc-122">CLR からのイベントを処理しようとしたときにエラーが発生したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-122">Notifies the debugger that an error has occurred while attempting to handle an event from the CLR.</span></span>|  
|[<span data-ttu-id="e40bc-123">EditAndContinueRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-123">EditAndContinueRemap Method</span></span>](icordebugmanagedcallback-editandcontinueremap-method.md)|<span data-ttu-id="e40bc-124">非推奨。</span><span class="sxs-lookup"><span data-stu-id="e40bc-124">Deprecated.</span></span> <span data-ttu-id="e40bc-125">リマップイベントが IDE に送信されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-125">Notifies the debugger that a remap event has been sent to the IDE.</span></span>|  
|[<span data-ttu-id="e40bc-126">EvalComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-126">EvalComplete Method</span></span>](icordebugmanagedcallback-evalcomplete-method.md)|<span data-ttu-id="e40bc-127">評価が完了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-127">Notifies the debugger that an evaluation has been completed.</span></span>|  
|[<span data-ttu-id="e40bc-128">EvalException メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-128">EvalException Method</span></span>](icordebugmanagedcallback-evalexception-method.md)|<span data-ttu-id="e40bc-129">ハンドルされない例外で評価が終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-129">Notifies the debugger that an evaluation has been terminated with an unhandled exception.</span></span>|  
|[<span data-ttu-id="e40bc-130">Exception メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-130">Exception Method</span></span>](icordebugmanagedcallback-exception-method.md)|<span data-ttu-id="e40bc-131">マネージコードから例外がスローされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-131">Notifies the debugger that an exception has been thrown from managed code.</span></span>|  
|[<span data-ttu-id="e40bc-132">ExitAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-132">ExitAppDomain Method</span></span>](icordebugmanagedcallback-exitappdomain-method.md)|<span data-ttu-id="e40bc-133">アプリケーションドメインが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-133">Notifies the debugger that an application domain has exited.</span></span>|  
|[<span data-ttu-id="e40bc-134">ExitProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-134">ExitProcess Method</span></span>](icordebugmanagedcallback-exitprocess-method.md)|<span data-ttu-id="e40bc-135">プロセスが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-135">Notifies the debugger that a process has exited.</span></span>|  
|[<span data-ttu-id="e40bc-136">ExitThread メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-136">ExitThread Method</span></span>](icordebugmanagedcallback-exitthread-method.md)|<span data-ttu-id="e40bc-137">マネージコードを実行していたスレッドが終了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-137">Notifies the debugger that a thread that was executing managed code has exited.</span></span>|  
|[<span data-ttu-id="e40bc-138">LoadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-138">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)|<span data-ttu-id="e40bc-139">CLR アセンブリが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-139">Notifies the debugger that a CLR assembly has been successfully loaded.</span></span>|  
|[<span data-ttu-id="e40bc-140">LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-140">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)|<span data-ttu-id="e40bc-141">クラスが読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-141">Notifies the debugger that a class has been loaded.</span></span>|  
|[<span data-ttu-id="e40bc-142">LoadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-142">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)|<span data-ttu-id="e40bc-143">CLR モジュールが正常に読み込まれたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-143">Notifies the debugger that a CLR module has been successfully loaded.</span></span>|  
|[<span data-ttu-id="e40bc-144">LogMessage メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-144">LogMessage Method</span></span>](icordebugmanagedcallback-logmessage-method.md)|<span data-ttu-id="e40bc-145">CLR マネージスレッドが <xref:System.Diagnostics.EventLog> イベントをログに記録するためにクラスのメソッドを呼び出したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-145">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>|  
|[<span data-ttu-id="e40bc-146">LogSwitch メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-146">LogSwitch Method</span></span>](icordebugmanagedcallback-logswitch-method.md)|<span data-ttu-id="e40bc-147">CLR マネージスレッドが、 <xref:System.Diagnostics.Switch> デバッグ/トレーススイッチを作成、変更、または削除するために、クラスのメソッドを呼び出したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-147">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>|  
|[<span data-ttu-id="e40bc-148">NameChange メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-148">NameChange Method</span></span>](icordebugmanagedcallback-namechange-method.md)|<span data-ttu-id="e40bc-149">アプリケーションドメインまたはスレッドの名前が変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-149">Notifies the debugger that the name of either an application domain or thread has changed.</span></span>|  
|[<span data-ttu-id="e40bc-150">StepComplete メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-150">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)|<span data-ttu-id="e40bc-151">ステップが完了したことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-151">Notifies the debugger that a step has completed.</span></span>|  
|[<span data-ttu-id="e40bc-152">UnloadAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-152">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)|<span data-ttu-id="e40bc-153">CLR アセンブリがアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-153">Notifies the debugger that a CLR assembly has been unloaded.</span></span>|  
|[<span data-ttu-id="e40bc-154">UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-154">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)|<span data-ttu-id="e40bc-155">クラスがアンロードされていることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-155">Notifies the debugger that a class is being unloaded.</span></span>|  
|[<span data-ttu-id="e40bc-156">UnloadModule メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-156">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)|<span data-ttu-id="e40bc-157">CLR モジュール (DLL) がアンロードされたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-157">Notifies the debugger that a CLR module (DLL) has been unloaded.</span></span>|  
|[<span data-ttu-id="e40bc-158">UpdateModuleSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="e40bc-158">UpdateModuleSymbols Method</span></span>](icordebugmanagedcallback-updatemodulesymbols-method.md)|<span data-ttu-id="e40bc-159">CLR モジュールのシンボルが変更されたことをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-159">Notifies the debugger that the symbols for a CLR module have changed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e40bc-160">注釈</span><span class="sxs-lookup"><span data-stu-id="e40bc-160">Remarks</span></span>  

 <span data-ttu-id="e40bc-161">すべてのコールバックがシリアル化され、同じスレッドで呼び出され、プロセスと同期された状態で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e40bc-161">All callbacks are serialized, called in the same thread, and called with the process in the synchronized state.</span></span>  
  
 <span data-ttu-id="e40bc-162">各コールバックの実装では、実行を再開するために、「いいね! [:: Continue](icordebugcontroller-continue-method.md) 」を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e40bc-162">Each callback implementation must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to resume execution.</span></span> <span data-ttu-id="e40bc-163">`ICorDebugController::Continue`コールバックが戻る前にが呼び出されなかった場合、プロセスは停止したままになり、が呼び出されるまで、これ以上イベントコールバックは実行されません `ICorDebugController::Continue` 。</span><span class="sxs-lookup"><span data-stu-id="e40bc-163">If `ICorDebugController::Continue` is not called before the callback returns, the process will remain stopped and no more event callbacks will occur until `ICorDebugController::Continue` is called.</span></span>  
  
 <span data-ttu-id="e40bc-164">デバッガーが .NET Framework バージョン2.0 のアプリケーションをデバッグしている場合は、 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e40bc-164">A debugger must implement [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) if it is debugging .NET Framework version 2.0 applications.</span></span> <span data-ttu-id="e40bc-165">またはのインスタンスは、 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` コールバックオブジェクトとして [ICorDebug:: setmanagedhandler](icordebug-setmanagedhandler-method.md)に渡されます。</span><span class="sxs-lookup"><span data-stu-id="e40bc-165">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e40bc-166">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e40bc-166">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e40bc-167">要件</span><span class="sxs-lookup"><span data-stu-id="e40bc-167">Requirements</span></span>  

 <span data-ttu-id="e40bc-168">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e40bc-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e40bc-169">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e40bc-169">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e40bc-170">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e40bc-170">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e40bc-171">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e40bc-171">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40bc-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="e40bc-172">See also</span></span>

- [<span data-ttu-id="e40bc-173">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e40bc-173">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="e40bc-174">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e40bc-174">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="e40bc-175">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e40bc-175">Debugging Interfaces</span></span>](debugging-interfaces.md)
