---
title: 列挙体のデバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
ms.openlocfilehash: bdd4b60d068677ae2a0874b589294ba220f0d854
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723000"
---
# <a name="debugging-enumerations"></a><span data-ttu-id="fc709-102">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="fc709-102">Debugging Enumerations</span></span>

<span data-ttu-id="fc709-103">このセクションでは、デバッグ API が使用するアンマネージ列挙体について説明します。</span><span class="sxs-lookup"><span data-stu-id="fc709-103">This section describes the unmanaged enumerations that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc709-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="fc709-104">In This Section</span></span>  

 [<span data-ttu-id="fc709-105">CLR_DEBUGGING_PROCESS_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-105">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>](clr-debugging-process-flags-enumeration.md)  
 <span data-ttu-id="fc709-106">[ICLRDebugging:: OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md)メソッドによって使用される値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-106">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="fc709-107">CLRDataEnumMemoryFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-107">CLRDataEnumMemoryFlags Enumeration</span></span>](clrdataenummemoryflags-enumeration.md)  
 <span data-ttu-id="fc709-108">[ICLRDataEnumMemoryRegions:: EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md)メソッドへの呼び出しに含まれるメモリ領域を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-108">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
 [<span data-ttu-id="fc709-109">COR_PUB_ENUMPROCESS 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-109">COR_PUB_ENUMPROCESS Enumeration</span></span>](cor-pub-enumprocess-enumeration.md)  
 <span data-ttu-id="fc709-110">列挙するプロセスの型を識別します。</span><span class="sxs-lookup"><span data-stu-id="fc709-110">Identifies the type of process to be enumerated.</span></span>  
  
 [<span data-ttu-id="fc709-111">CorDebugBlockingReason 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-111">CorDebugBlockingReason Enumeration</span></span>](cordebugblockingreason-enumeration.md)  
 <span data-ttu-id="fc709-112">指定されたオブジェクト上でスレッドがブロックされる理由を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc709-112">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
 <span data-ttu-id="fc709-113">CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="fc709-113">CorDebugChainReason</span></span>  
 <span data-ttu-id="fc709-114">呼び出しチェーンが開始する理由を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-114">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
 [<span data-ttu-id="fc709-115">CorDebugCodeInvokeKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-115">CorDebugCodeInvokeKind Enumeration</span></span>](cordebugcodeinvokekind-enumeration.md)  
 <span data-ttu-id="fc709-116">エクスポートされた関数がマネージド コードを呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-116">Describes how an exported function invokes managed code.</span></span>  
  
 [<span data-ttu-id="fc709-117">CorDebugCodeInvokePurpose 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-117">CorDebugCodeInvokePurpose Enumeration</span></span>](cordebugcodeinvokepurpose-enumeration.md)  
 <span data-ttu-id="fc709-118">エクスポートされた関数がマネージド コードを呼び出す理由を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-118">Describes why an exported function calls managed code.</span></span>  
  
 <span data-ttu-id="fc709-119">CorDebugCreateProcessFlags</span><span class="sxs-lookup"><span data-stu-id="fc709-119">CorDebugCreateProcessFlags</span></span>  
 <span data-ttu-id="fc709-120">[ICorDebug:: CreateProcess](icordebug-createprocess-method.md)メソッドの呼び出しで使用できる追加のデバッグオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-120">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](icordebug-createprocess-method.md) method.</span></span>  
  
 [<span data-ttu-id="fc709-121">CorDebugDebugEventKind 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-121">CorDebugDebugEventKind Enumeration</span></span>](cordebugdebugeventkind-enumeration.md)  
 <span data-ttu-id="fc709-122">[DecodeEvent](icordebugprocess6-decodeevent-method.md)メソッドによって情報がデコードされるイベントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-122">Indicates the type of event whose information is decoded by the [DecodeEvent](icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
 [<span data-ttu-id="fc709-123">CorDebugDecodeEventFlagsWindows 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-123">CorDebugDecodeEventFlagsWindows Enumeration</span></span>](cordebugdecodeeventflagswindows-enumeration.md)  
 <span data-ttu-id="fc709-124">Windows プラットフォームのデバッグ イベントに関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-124">Provides additional information about debug events on the Windows platform.</span></span>  
  
 <span data-ttu-id="fc709-125">CorDebugExceptionCallbackType</span><span class="sxs-lookup"><span data-stu-id="fc709-125">CorDebugExceptionCallbackType</span></span>  
 <span data-ttu-id="fc709-126">[ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)イベントから作成されたコールバックの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-126">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
 [<span data-ttu-id="fc709-127">CorDebugExceptionFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-127">CorDebugExceptionFlags Enumeration</span></span>](cordebugexceptionflags-enumeration.md)  
 <span data-ttu-id="fc709-128">例外に関する追加情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-128">Provides additional information about an exception.</span></span>  
  
 <span data-ttu-id="fc709-129">CorDebugExceptionUnwindCallbackType</span><span class="sxs-lookup"><span data-stu-id="fc709-129">CorDebugExceptionUnwindCallbackType</span></span>  
 <span data-ttu-id="fc709-130">アンワインド フェーズ中にコールバックによって通知されるイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-130">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 [<span data-ttu-id="fc709-131">CorDebugGCType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-131">CorDebugGCType Enumeration</span></span>](cordebuggctype-enumeration.md)  
 <span data-ttu-id="fc709-132">ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-132">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
 [<span data-ttu-id="fc709-133">CorDebugGenerationTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-133">CorDebugGenerationTypes Enumeration</span></span>](cordebuggenerationtypes-enumeration.md)  
 <span data-ttu-id="fc709-134">マネージド ヒープ上のメモリ領域の生成を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc709-134">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
 <span data-ttu-id="fc709-135">CorDebugHandleType</span><span class="sxs-lookup"><span data-stu-id="fc709-135">CorDebugHandleType</span></span>  
 <span data-ttu-id="fc709-136">ハンドル型を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-136">Indicates the handle type.</span></span>  
  
 [<span data-ttu-id="fc709-137">CorDebugIlToNativeMappingTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-137">CorDebugIlToNativeMappingTypes Enumeration</span></span>](cordebugiltonativemappingtypes-enumeration.md)  
 <span data-ttu-id="fc709-138">ネイティブ命令の特定の範囲が特別なコード領域に対応するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-138">Indicates whether a particular range of native instructions corresponds to a special code region.</span></span>  
  
 <span data-ttu-id="fc709-139">CorDebugIntercept</span><span class="sxs-lookup"><span data-stu-id="fc709-139">CorDebugIntercept</span></span>  
 <span data-ttu-id="fc709-140">ステップ インできるコードの型を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-140">Indicates the types of code that can be stepped into.</span></span>  
  
 [<span data-ttu-id="fc709-141">CorDebugInterfaceVersion 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-141">CorDebugInterfaceVersion Enumeration</span></span>](cordebuginterfaceversion-enumeration.md)  
 <span data-ttu-id="fc709-142">.NET Framework のバージョン、またはインターフェイスが導入された .NET Framework のバージョンのいずれかを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc709-142">Specifies either a version of the .NET Framework, or the version of the .NET Framework in which an interface was introduced.</span></span>  
  
 <span data-ttu-id="fc709-143">CorDebugInternalFrameType</span><span class="sxs-lookup"><span data-stu-id="fc709-143">CorDebugInternalFrameType</span></span>  
 <span data-ttu-id="fc709-144">スタック フレームの型を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-144">Identifies the type of stack frame.</span></span>  
  
 [<span data-ttu-id="fc709-145">CorDebugJITCompilerFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-145">CorDebugJITCompilerFlags Enumeration</span></span>](cordebugjitcompilerflags-enumeration.md)  
 <span data-ttu-id="fc709-146">マネージド Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fc709-146">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
 [<span data-ttu-id="fc709-147">CorDebugJITCompilerFlagsDeprecated 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-147">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>](cordebugjitcompilerflagsdeprecated-enumeration.md)  
 <span data-ttu-id="fc709-148">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="fc709-148">Obsolete.</span></span> <span data-ttu-id="fc709-149">代わりに、 `CORDEBUG_JIT_DEFAULT` [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) 列挙体のメンバーを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fc709-149">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
 <span data-ttu-id="fc709-150">CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="fc709-150">CorDebugMappingResult</span></span>  
 <span data-ttu-id="fc709-151">命令ポインター (IP) の値が得られた方法の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-151">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
 [<span data-ttu-id="fc709-152">CorDebugMDAFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-152">CorDebugMDAFlags Enumeration</span></span>](cordebugmdaflags-enumeration.md)  
 <span data-ttu-id="fc709-153">マネージド デバッグ アシスタント (MDA) が生成されるスレッドのステータスを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc709-153">Specifies the status of the thread on which the managed debugging assistant (MDA) is fired.</span></span>  
  
 [<span data-ttu-id="fc709-154">CorDebugNGenPolicy 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-154">CorDebugNGenPolicy Enumeration</span></span>](cordebugngenpolicy-enumeration.md)  
 <span data-ttu-id="fc709-155">デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-155">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
 [<span data-ttu-id="fc709-156">CorDebugPlatform 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-156">CorDebugPlatform Enumeration</span></span>](cordebugplatform-enumeration.md)  
 <span data-ttu-id="fc709-157">は [、のターゲットプラットフォームの値](icordebugdatatarget-getplatform-method.md) を提供しています。</span><span class="sxs-lookup"><span data-stu-id="fc709-157">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
 [<span data-ttu-id="fc709-158">CorDebugRecordFormat 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-158">CorDebugRecordFormat Enumeration</span></span>](cordebugrecordformat-enumeration.md)  
 <span data-ttu-id="fc709-159">ネイティブ例外デバッグ イベントに関する情報を格納するバイト配列内のデータの形式を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-159">Describes the format of the data in a byte array that contains information about a native exception debug event.</span></span>  
  
 <span data-ttu-id="fc709-160">CorDebugRegister</span><span class="sxs-lookup"><span data-stu-id="fc709-160">CorDebugRegister</span></span>  
 <span data-ttu-id="fc709-161">指定されたプロセッサ アーキテクチャに関連付けられたレジスタを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc709-161">Specifies the registers associated with a given processor architecture.</span></span>  
  
 [<span data-ttu-id="fc709-162">CorDebugSetContextFlag 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-162">CorDebugSetContextFlag Enumeration</span></span>](cordebugsetcontextflag-enumeration.md)  
 <span data-ttu-id="fc709-163">スタック上のアクティブ (またはリーフ) フレーム上からのコンテキストなのか、別のフレームからのアンワインドにより計算されたコンテキストなのかを示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-163">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
 [<span data-ttu-id="fc709-164">CorDebugStateChange 列挙体</span><span class="sxs-lookup"><span data-stu-id="fc709-164">CorDebugStateChange Enumeration</span></span>](cordebugstatechange-enumeration.md)  
 <span data-ttu-id="fc709-165">プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-165">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
 <span data-ttu-id="fc709-166">CorDebugStepReason</span><span class="sxs-lookup"><span data-stu-id="fc709-166">CorDebugStepReason</span></span>  
 <span data-ttu-id="fc709-167">個々のステップの結果を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-167">Indicates the outcome of an individual step.</span></span>  
  
 <span data-ttu-id="fc709-168">CorDebugThreadState</span><span class="sxs-lookup"><span data-stu-id="fc709-168">CorDebugThreadState</span></span>  
 <span data-ttu-id="fc709-169">デバッグのスレッドの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc709-169">Specifies the state of a thread for debugging.</span></span>  
  
 <span data-ttu-id="fc709-170">\>CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="fc709-170">\>CorDebugUnmappedStop</span></span>  
 <span data-ttu-id="fc709-171">ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fc709-171">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
 <span data-ttu-id="fc709-172">CorDebugUserState</span><span class="sxs-lookup"><span data-stu-id="fc709-172">CorDebugUserState</span></span>  
 <span data-ttu-id="fc709-173">スレッドのユーザーの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-173">Indicates the user state of a thread.</span></span>  
  
 [<span data-ttu-id="fc709-174">CorGCReferenceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-174">CorGCReferenceType Enumeration</span></span>](corgcreferencetype-enumeration.md)  
 <span data-ttu-id="fc709-175">ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。</span><span class="sxs-lookup"><span data-stu-id="fc709-175">Identifies the source of an object to be garbage-collected.</span></span>  
  
 [<span data-ttu-id="fc709-176">ILCodeKind 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-176">ILCodeKind Enumeration</span></span>](ilcodekind-enumeration.md)  
 <span data-ttu-id="fc709-177">デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-177">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="fc709-178">LoggingLevelEnum 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-178">LoggingLevelEnum Enumeration</span></span>](logginglevelenum-enumeration.md)  
 <span data-ttu-id="fc709-179">マネージド スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-179">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
 [<span data-ttu-id="fc709-180">LogSwitchCallReason 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-180">LogSwitchCallReason Enumeration</span></span>](logswitchcallreason-enumeration.md)  
 <span data-ttu-id="fc709-181">デバッグとトレースの切り替えで実行された操作を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-181">Indicates the operation that was performed on a debugging/tracing switch.</span></span>  
  
 [<span data-ttu-id="fc709-182">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-182">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)  
 <span data-ttu-id="fc709-183">変数のネイティブな場所の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="fc709-183">Indicates the native location type of a variable.</span></span>  
  
 [<span data-ttu-id="fc709-184">WriteableMetadataUpdateMode 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc709-184">WriteableMetadataUpdateMode Enumeration</span></span>](writeablemetadataupdatemode-enumeration.md)  
 <span data-ttu-id="fc709-185">メモリ内のメタデータ更新をデバッガーに対して可視にするかどうかを指定する値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-185">Provides values that specify whether in-memory updates to metadata are visible to a debugger.</span></span>

 <span data-ttu-id="fc709-186">[ClrDataSourceType 列挙型](clrdatasourcetype-enumeration.md) CLRDATA_IL_ADDRESS_MAP 構造体によって使用される値を提供します。</span><span class="sxs-lookup"><span data-stu-id="fc709-186">[ClrDataSourceType Enumeration](clrdatasourcetype-enumeration.md) Provides values that are used by the CLRDATA_IL_ADDRESS_MAP structure.</span></span>

## <a name="related-sections"></a><span data-ttu-id="fc709-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc709-187">Related Sections</span></span>  

 [<span data-ttu-id="fc709-188">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="fc709-188">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="fc709-189">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc709-189">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="fc709-190">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="fc709-190">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)  
  
 [<span data-ttu-id="fc709-191">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="fc709-191">Debugging Structures</span></span>](debugging-structures.md)
