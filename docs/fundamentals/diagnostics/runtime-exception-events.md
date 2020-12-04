---
title: 例外ランタイムイベント
description: 「例外と例外処理に固有の診断情報を収集する .NET ランタイムイベント」を参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- exception events (CoreCLR)
- exception handling events (CoreCLR)
- ETW, EventPipe, LTTng exception events (CoreCLR)
ms.openlocfilehash: f4f63c8469f9c734b872ddaec8d1d7f7f0427576
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96594103"
---
# <a name="net-runtime-exception-events"></a><span data-ttu-id="32f32-103">.NET ランタイム例外イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-103">.NET runtime exception events</span></span>

<span data-ttu-id="32f32-104">これらのランタイムイベントは、スローされた例外に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="32f32-104">These runtime events capture information about exceptions that are thrown.</span></span> <span data-ttu-id="32f32-105">診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f32-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="exceptionthrown_v1-event"></a><span data-ttu-id="32f32-106">ExceptionThrown_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-106">ExceptionThrown_V1 event</span></span>

|<span data-ttu-id="32f32-107">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-107">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-108">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-109">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-109">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-110">エラー (1)</span><span class="sxs-lookup"><span data-stu-id="32f32-110">Error (1)</span></span>|

 <span data-ttu-id="32f32-111">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-111">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-112">event</span><span class="sxs-lookup"><span data-stu-id="32f32-112">Event</span></span>|<span data-ttu-id="32f32-113">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-113">Event ID</span></span>|<span data-ttu-id="32f32-114">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrown_V1`|<span data-ttu-id="32f32-115">80</span><span class="sxs-lookup"><span data-stu-id="32f32-115">80</span></span>|<span data-ttu-id="32f32-116">マネージド例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="32f32-116">A managed exception is thrown.</span></span>|

|<span data-ttu-id="32f32-117">フィールド名</span><span class="sxs-lookup"><span data-stu-id="32f32-117">Field name</span></span>|<span data-ttu-id="32f32-118">データ型</span><span class="sxs-lookup"><span data-stu-id="32f32-118">Data type</span></span>|<span data-ttu-id="32f32-119">説明</span><span class="sxs-lookup"><span data-stu-id="32f32-119">Description</span></span>|
|----------------|---------------|-----------------|
|`ExceptionType`|`win:UnicodeString`|<span data-ttu-id="32f32-120">例外の種類 (`System.NullReferenceException` など)。</span><span class="sxs-lookup"><span data-stu-id="32f32-120">Type of the exception; for example, `System.NullReferenceException`.</span></span>|
|`ExceptionMessage`|`win:UnicodeString`|<span data-ttu-id="32f32-121">実際の例外メッセージ。</span><span class="sxs-lookup"><span data-stu-id="32f32-121">Actual exception message.</span></span>|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="32f32-122">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="32f32-122">Instruction pointer where exception occurred.</span></span>|
|`ExceptionHR`|`win:UInt32`|<span data-ttu-id="32f32-123">例外 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。</span><span class="sxs-lookup"><span data-stu-id="32f32-123">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|
|`ExceptionFlags`|`win:UInt16`|<span data-ttu-id="32f32-124">`0x01`: HasInnerException。</span><span class="sxs-lookup"><span data-stu-id="32f32-124">`0x01`: HasInnerException.</span></span><br /><br /> <span data-ttu-id="32f32-125">`0x02`: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="32f32-125">`0x02`: IsNestedException.</span></span><br /><br /> <span data-ttu-id="32f32-126">`0x04`: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="32f32-126">`0x04`: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="32f32-127">`0x08`: IsCorruptedStateException (プロセスの状態が破損していることを示します。「 [破損状態の例外の処理](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="32f32-127">`0x08`: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="32f32-128">`0x10`: IsCLSCompliant (から派生した例外 <xref:System.Exception> は cls に準拠していますが、それ以外の場合は cls に準拠していません)。</span><span class="sxs-lookup"><span data-stu-id="32f32-128">`0x10`: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="32f32-129">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="32f32-129">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstart-event"></a><span data-ttu-id="32f32-130">ExceptionCatchStart イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-130">ExceptionCatchStart event</span></span>

<span data-ttu-id="32f32-131">このイベントは、マネージ例外の catch ハンドラーが開始されると生成されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-131">This event is emitted when a managed exception catch handler begins.</span></span>

|<span data-ttu-id="32f32-132">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-132">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-133">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-133">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-134">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-134">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-135">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="32f32-135">Informational (4)</span></span>|

 <span data-ttu-id="32f32-136">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-136">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-137">event</span><span class="sxs-lookup"><span data-stu-id="32f32-137">Event</span></span>|<span data-ttu-id="32f32-138">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-138">Event ID</span></span>|<span data-ttu-id="32f32-139">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-139">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStart`|<span data-ttu-id="32f32-140">250</span><span class="sxs-lookup"><span data-stu-id="32f32-140">250</span></span>|<span data-ttu-id="32f32-141">マネージ例外は、ランタイムによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-141">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="32f32-142">フィールド名</span><span class="sxs-lookup"><span data-stu-id="32f32-142">Field name</span></span>|<span data-ttu-id="32f32-143">データ型</span><span class="sxs-lookup"><span data-stu-id="32f32-143">Data type</span></span>|<span data-ttu-id="32f32-144">説明</span><span class="sxs-lookup"><span data-stu-id="32f32-144">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="32f32-145">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="32f32-145">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="32f32-146">例外が発生したメソッドのメソッド記述子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="32f32-146">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="32f32-147">例外が発生したメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="32f32-147">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="32f32-148">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="32f32-148">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptioncatchstop-event"></a><span data-ttu-id="32f32-149">ExceptionCatchStop イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-149">ExceptionCatchStop event</span></span>

<span data-ttu-id="32f32-150">このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-150">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="32f32-151">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-151">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-152">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-152">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-153">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-153">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-154">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="32f32-154">Informational (4)</span></span>|

 <span data-ttu-id="32f32-155">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-155">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-156">event</span><span class="sxs-lookup"><span data-stu-id="32f32-156">Event</span></span>|<span data-ttu-id="32f32-157">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-157">Event ID</span></span>|<span data-ttu-id="32f32-158">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-158">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionCatchStop`|<span data-ttu-id="32f32-159">251</span><span class="sxs-lookup"><span data-stu-id="32f32-159">251</span></span>|<span data-ttu-id="32f32-160">マネージ例外の catch ハンドラーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-160">A managed exception catch handler is done.</span></span>|

## <a name="exceptionfinallystart-event"></a><span data-ttu-id="32f32-161">Exceptionfinを開始するイベント</span><span class="sxs-lookup"><span data-stu-id="32f32-161">ExceptionFinallyStart event</span></span>

<span data-ttu-id="32f32-162">このイベントは、マネージ例外の finally ハンドラーが開始したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-162">This event is emitted when a managed exception finally handler begins.</span></span>

|<span data-ttu-id="32f32-163">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-163">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-164">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-164">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-165">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-165">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-166">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="32f32-166">Informational (4)</span></span>|

 <span data-ttu-id="32f32-167">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-167">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-168">event</span><span class="sxs-lookup"><span data-stu-id="32f32-168">Event</span></span>|<span data-ttu-id="32f32-169">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-169">Event ID</span></span>|<span data-ttu-id="32f32-170">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-170">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStart`|<span data-ttu-id="32f32-171">252</span><span class="sxs-lookup"><span data-stu-id="32f32-171">252</span></span>|<span data-ttu-id="32f32-172">マネージ例外は、ランタイムによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-172">A managed exception is handled by the runtime.</span></span>|

|<span data-ttu-id="32f32-173">フィールド名</span><span class="sxs-lookup"><span data-stu-id="32f32-173">Field name</span></span>|<span data-ttu-id="32f32-174">データ型</span><span class="sxs-lookup"><span data-stu-id="32f32-174">Data type</span></span>|<span data-ttu-id="32f32-175">説明</span><span class="sxs-lookup"><span data-stu-id="32f32-175">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="32f32-176">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="32f32-176">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="32f32-177">例外が発生したメソッドのメソッド記述子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="32f32-177">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="32f32-178">例外が発生したメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="32f32-178">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="32f32-179">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="32f32-179">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="exceptionfinallystop-event"></a><span data-ttu-id="32f32-180">Exceptionfinが停止イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-180">ExceptionFinallyStop event</span></span>

<span data-ttu-id="32f32-181">このイベントは、マネージ例外の catch ハンドラーが終了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-181">This event is emitted when a managed exception catch handler ends.</span></span>

|<span data-ttu-id="32f32-182">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-182">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-183">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-183">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-184">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-184">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-185">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="32f32-185">Informational (4)</span></span>|

 <span data-ttu-id="32f32-186">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-186">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-187">event</span><span class="sxs-lookup"><span data-stu-id="32f32-187">Event</span></span>|<span data-ttu-id="32f32-188">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-188">Event ID</span></span>|<span data-ttu-id="32f32-189">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-189">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFinallyStop`|<span data-ttu-id="32f32-190">253</span><span class="sxs-lookup"><span data-stu-id="32f32-190">253</span></span>|<span data-ttu-id="32f32-191">マネージ例外 finally ハンドラーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-191">A managed exception finally handler is done.</span></span>|

## <a name="exceptionfilterstart-event"></a><span data-ttu-id="32f32-192">ExceptionFilterStart イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-192">ExceptionFilterStart event</span></span>

<span data-ttu-id="32f32-193">このイベントは、マネージ例外のフィルター処理が開始されるときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-193">This event is emitted when a managed exception filtering begins.</span></span>

|<span data-ttu-id="32f32-194">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-194">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-195">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-195">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-196">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-196">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-197">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="32f32-197">Informational (4)</span></span>|

 <span data-ttu-id="32f32-198">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-198">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-199">event</span><span class="sxs-lookup"><span data-stu-id="32f32-199">Event</span></span>|<span data-ttu-id="32f32-200">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-200">Event ID</span></span>|<span data-ttu-id="32f32-201">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-201">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilterStart`|<span data-ttu-id="32f32-202">254</span><span class="sxs-lookup"><span data-stu-id="32f32-202">254</span></span>|<span data-ttu-id="32f32-203">マネージ例外のフィルター処理が開始されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-203">A managed exception filtering begins.</span></span>|

|<span data-ttu-id="32f32-204">フィールド名</span><span class="sxs-lookup"><span data-stu-id="32f32-204">Field name</span></span>|<span data-ttu-id="32f32-205">データ型</span><span class="sxs-lookup"><span data-stu-id="32f32-205">Data type</span></span>|<span data-ttu-id="32f32-206">説明</span><span class="sxs-lookup"><span data-stu-id="32f32-206">Description</span></span>|
|----------------|---------------|-----------------|
|`EIPCodeThrow`|`win:Pointer`|<span data-ttu-id="32f32-207">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="32f32-207">Instruction pointer where exception occurred.</span></span>|
|`MethodID`|`win:Pointer`|<span data-ttu-id="32f32-208">例外が発生したメソッドのメソッド記述子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="32f32-208">Pointer to the method descriptor on the method where exception occurred.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="32f32-209">例外が発生したメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="32f32-209">Name of the method where exception occurred.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="32f32-210">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="32f32-210">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="exceptionfilterstop-event"></a><span data-ttu-id="32f32-211">ExceptionFilterStop イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-211">ExceptionFilterStop event</span></span>

<span data-ttu-id="32f32-212">このイベントは、マネージ例外のフィルター処理が終了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-212">This event is emitted when a managed exception filtering ends.</span></span>

|<span data-ttu-id="32f32-213">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-213">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-214">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-214">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-215">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-215">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-216">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="32f32-216">Informational (4)</span></span>|

 <span data-ttu-id="32f32-217">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-217">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-218">event</span><span class="sxs-lookup"><span data-stu-id="32f32-218">Event</span></span>|<span data-ttu-id="32f32-219">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-219">Event ID</span></span>|<span data-ttu-id="32f32-220">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-220">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionFilteringStart`|<span data-ttu-id="32f32-221">255</span><span class="sxs-lookup"><span data-stu-id="32f32-221">255</span></span>|<span data-ttu-id="32f32-222">マネージ例外のフィルター処理が終了します。</span><span class="sxs-lookup"><span data-stu-id="32f32-222">A managed exception filtering ends.</span></span>|

## <a name="exceptionthrownstop-event"></a><span data-ttu-id="32f32-223">ExceptionThrownStop イベント</span><span class="sxs-lookup"><span data-stu-id="32f32-223">ExceptionThrownStop event</span></span>

<span data-ttu-id="32f32-224">このイベントは、スローされたマネージ例外の処理がランタイムによって完了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="32f32-224">This event is emitted when the runtime is done handling a managed exception that was thrown.</span></span>

|<span data-ttu-id="32f32-225">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="32f32-225">Keyword for raising the event</span></span>|<span data-ttu-id="32f32-226">Level</span><span class="sxs-lookup"><span data-stu-id="32f32-226">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="32f32-227">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="32f32-227">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="32f32-228">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="32f32-228">Informational (4)</span></span>|
  
 <span data-ttu-id="32f32-229">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="32f32-229">The following table shows event information.</span></span>

|<span data-ttu-id="32f32-230">event</span><span class="sxs-lookup"><span data-stu-id="32f32-230">Event</span></span>|<span data-ttu-id="32f32-231">イベント ID</span><span class="sxs-lookup"><span data-stu-id="32f32-231">Event ID</span></span>|<span data-ttu-id="32f32-232">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="32f32-232">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ExceptionThrownStop`|<span data-ttu-id="32f32-233">256</span><span class="sxs-lookup"><span data-stu-id="32f32-233">256</span></span>|<span data-ttu-id="32f32-234">マネージ例外のフィルター処理が終了します。</span><span class="sxs-lookup"><span data-stu-id="32f32-234">A managed exception filtering ends.</span></span>|
