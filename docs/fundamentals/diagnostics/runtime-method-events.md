---
title: メソッドランタイムイベント
description: 「CLR メソッドイベント」、「clr メソッドマーカー」、「CLR メソッドの詳細イベント」、「MethodJittingStarted」など、メソッドに固有の診断情報を収集する .NET ランタイムイベントを参照してください。
ms.date: 11/13/2020
helpviewer_keywords:
- Method events (CoreCLR)
- ETW, EventPipe, LTTng method events (CoreCLR)
ms.openlocfilehash: f9d08efa420670cf7a8c863f115ff270998f2dca
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594042"
---
# <a name="net-runtime-method-events"></a><span data-ttu-id="a9b7e-103">.NET ランタイムメソッドイベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-103">.NET runtime method events</span></span>

<span data-ttu-id="a9b7e-104">これらのイベントは、メソッド固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-104">These events collect information that is specific to methods.</span></span> <span data-ttu-id="a9b7e-105">これらのイベントのペイロードは、シンボルの解決に必要です。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-105">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="a9b7e-106">また、これらのイベントは、読み込まれたメソッドやアンロードされたメソッドなどの有用な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-106">In addition, these events provide helpful information such as methods that are loaded and unloaded.</span></span> <span data-ttu-id="a9b7e-107">診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-107">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

<span data-ttu-id="a9b7e-108">すべてのメソッド イベントのレベルは「情報提供 (4)」です。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-108">All method events have a level of "Informational (4)".</span></span> <span data-ttu-id="a9b7e-109">すべてのメソッド詳細イベントのレベルは「詳細 (5)」です。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-109">All method verbose events have a level of "Verbose (5)".</span></span>

<span data-ttu-id="a9b7e-110">すべてのメソッド イベントは、ランタイム プロバイダーのもとでは `JITKeyword` (0x10) キーワードまたは `NGenKeyword` (0x20) キーワードが発生させ、ランダウン プロバイダーのもとでは `JitRundownKeyword` (0x10) または `NGENRundownKeyword` (0x20) が発生させます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-110">All method events are raised by the `JITKeyword` (0x10) keyword or the `NGenKeyword` (0x20) keyword under the runtime provider, or `JitRundownKeyword` (0x10) or `NGENRundownKeyword` (0x20) under the rundown provider.</span></span>

<span data-ttu-id="a9b7e-111">これらのイベントの V2 バージョンには ReJITID が含まれていますが、V1 バージョンではありません。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-111">The V2 versions of these events include the ReJITID, the V1 versions do not.</span></span>

## <a name="methodload_v1-event"></a><span data-ttu-id="a9b7e-112">MethodLoad_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-112">MethodLoad_V1 event</span></span>

<span data-ttu-id="a9b7e-113">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-113">The following table shows the event information:</span></span>

|<span data-ttu-id="a9b7e-114">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-114">Event</span></span>|<span data-ttu-id="a9b7e-115">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-115">Event ID</span></span>|<span data-ttu-id="a9b7e-116">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-116">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoad_V1`|<span data-ttu-id="a9b7e-117">141</span><span class="sxs-lookup"><span data-stu-id="a9b7e-117">141</span></span>|<span data-ttu-id="a9b7e-118">メソッドが Just-In-Time 読み込み (JIT 読み込み) される時点、または NGEN イメージが読み込まれる時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-118">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="a9b7e-119">動的メソッドとジェネリック メソッドは、メソッドの読み込みにこのバージョンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-119">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="a9b7e-120">JIT ヘルパーがこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-120">JIT helpers never use this version.</span></span>|

|<span data-ttu-id="a9b7e-121">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-121">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-122">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-122">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-123">`JITKeyword` (0x10) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a9b7e-123">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="a9b7e-124">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-124">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-125">`NGenKeyword` (0x20) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a9b7e-125">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="a9b7e-126">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-126">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-127">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-127">Field name</span></span>|<span data-ttu-id="a9b7e-128">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-128">Data type</span></span>|<span data-ttu-id="a9b7e-129">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-129">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-130">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-130">Unique identifier of a method.</span></span> <span data-ttu-id="a9b7e-131">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-131">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-132">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-132">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-133">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-133">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-134">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-134">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-135">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-135">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-136">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-136">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-137">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-137">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-138">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-138">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="a9b7e-139">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-139">0x8: Helper method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-140">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-140">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodload_v2-event"></a><span data-ttu-id="a9b7e-141">MethodLoad_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-141">MethodLoad_V2 event</span></span>

|<span data-ttu-id="a9b7e-142">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-142">Event</span></span>|<span data-ttu-id="a9b7e-143">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-143">Event ID</span></span>|<span data-ttu-id="a9b7e-144">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-144">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodLoad_V2`|<span data-ttu-id="a9b7e-145">141</span><span class="sxs-lookup"><span data-stu-id="a9b7e-145">141</span></span>|<span data-ttu-id="a9b7e-146">メソッドが Just-In-Time 読み込み (JIT 読み込み) される時点、または NGEN イメージが読み込まれる時点で発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-146">Raised when a method is just-in-time loaded (JIT-loaded) or an NGEN image is loaded.</span></span> <span data-ttu-id="a9b7e-147">動的メソッドとジェネリック メソッドは、メソッドの読み込みにこのバージョンを使用しません。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-147">Dynamic and generic methods do not use this version for method loads.</span></span> <span data-ttu-id="a9b7e-148">JIT ヘルパーがこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-148">JIT helpers never use this version.</span></span>|

|<span data-ttu-id="a9b7e-149">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-149">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-150">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-150">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-151">`JITKeyword` (0x10) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a9b7e-151">`JITKeyword` (0x10) runtime provider</span></span>|<span data-ttu-id="a9b7e-152">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-152">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-153">`NGenKeyword` (0x20) ランタイム プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a9b7e-153">`NGenKeyword` (0x20) runtime provider</span></span>|<span data-ttu-id="a9b7e-154">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-154">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-155">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-155">Field name</span></span>|<span data-ttu-id="a9b7e-156">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-156">Data type</span></span>|<span data-ttu-id="a9b7e-157">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-157">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-158">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-158">Unique identifier of a method.</span></span> <span data-ttu-id="a9b7e-159">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-159">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-160">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-160">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-161">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-161">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-162">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-162">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-163">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-163">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-164">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-164">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-165">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-165">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-166">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-166">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="a9b7e-167">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-167">0x8: Helper method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="a9b7e-168">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-168">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-169">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-169">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunload_v1-event"></a><span data-ttu-id="a9b7e-170">MethodUnLoad_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-170">MethodUnLoad_V1 event</span></span>

|<span data-ttu-id="a9b7e-171">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-171">Event</span></span>|<span data-ttu-id="a9b7e-172">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-172">Event ID</span></span>|<span data-ttu-id="a9b7e-173">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-173">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodUnLoad_V1`|<span data-ttu-id="a9b7e-174">142</span><span class="sxs-lookup"><span data-stu-id="a9b7e-174">142</span></span>|<span data-ttu-id="a9b7e-175">モジュールがアンロードされるとき、またはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-175">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="a9b7e-176">動的メソッドがメソッドのアンロードにこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-176">Dynamic methods never use this version for method unloads.</span></span>|

|<span data-ttu-id="a9b7e-177">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-177">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-178">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-178">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-179">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-179">`JITKeyword` (0x10)</span></span>|<span data-ttu-id="a9b7e-180">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-180">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-181">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-181">`NGenKeyword` (0x20)</span></span>|<span data-ttu-id="a9b7e-182">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-182">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-183">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-183">Field name</span></span>|<span data-ttu-id="a9b7e-184">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-184">Data type</span></span>|<span data-ttu-id="a9b7e-185">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-185">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-186">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-186">Unique identifier of a method.</span></span> <span data-ttu-id="a9b7e-187">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-187">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-188">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-188">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-189">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-189">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-190">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-190">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-191">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-191">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-192">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-192">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-193">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-193">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-194">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-194">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="a9b7e-195">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-195">0x8: Helper method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-196">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-196">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunload_v2-event"></a><span data-ttu-id="a9b7e-197">MethodUnLoad_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-197">MethodUnLoad_V2 event</span></span>

|<span data-ttu-id="a9b7e-198">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-198">Event</span></span>|<span data-ttu-id="a9b7e-199">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-199">Event ID</span></span>|<span data-ttu-id="a9b7e-200">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-200">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodUnLoad_V2`|<span data-ttu-id="a9b7e-201">142</span><span class="sxs-lookup"><span data-stu-id="a9b7e-201">142</span></span>|<span data-ttu-id="a9b7e-202">モジュールがアンロードされるとき、またはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-202">Raised when a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="a9b7e-203">動的メソッドがメソッドのアンロードにこのバージョンを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-203">Dynamic methods never use this version for method unloads.</span></span>|

|<span data-ttu-id="a9b7e-204">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-204">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-205">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-205">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-206">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-206">`JITKeyword` (0x10)</span></span>|<span data-ttu-id="a9b7e-207">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-207">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-208">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-208">`NGenKeyword` (0x20)</span></span>|<span data-ttu-id="a9b7e-209">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-209">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-210">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-210">Field name</span></span>|<span data-ttu-id="a9b7e-211">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-211">Data type</span></span>|<span data-ttu-id="a9b7e-212">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-212">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-213">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-213">Unique identifier of a method.</span></span> <span data-ttu-id="a9b7e-214">JIT ヘルパー メソッドの場合、これはメソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-214">For JIT helper methods, this is set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-215">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-215">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-216">メソッドの開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-216">Start address of the method.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-217">メソッドのサイズ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-217">Size of the method.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-218">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-218">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-219">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-219">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-220">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-220">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-221">0x4: JIT コンパイル済みコード メソッド (それ以外の場合は NGEN ネイティブ イメージ コード)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-221">0x4: JIT-compiled code method (otherwise NGEN native image code).</span></span><br /><br /> <span data-ttu-id="a9b7e-222">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-222">0x8: Helper method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="a9b7e-223">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-223">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-224">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-224">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="r2rgetentrypoint-event"></a><span data-ttu-id="a9b7e-225">R2RGetEntryPoint イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-225">R2RGetEntryPoint event</span></span>

|<span data-ttu-id="a9b7e-226">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-226">Event</span></span>|<span data-ttu-id="a9b7e-227">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-227">Event ID</span></span>|<span data-ttu-id="a9b7e-228">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-228">Description</span></span>|
|----------------|---------------|-----------------|
|`R2RGetEntryPoint`|<span data-ttu-id="a9b7e-229">159</span><span class="sxs-lookup"><span data-stu-id="a9b7e-229">159</span></span>|<span data-ttu-id="a9b7e-230">R2R エントリポイント参照が終了したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-230">Raised when an R2R entry point lookup ends.</span></span>|

|<span data-ttu-id="a9b7e-231">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-231">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-232">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-232">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-233">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-233">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="a9b7e-234">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-234">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-235">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-235">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="a9b7e-236">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-236">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-237">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-237">Field name</span></span>|<span data-ttu-id="a9b7e-238">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-238">Data type</span></span>|<span data-ttu-id="a9b7e-239">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-239">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-240">R2R メソッドの一意識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-240">Unique identifier of a R2R method.</span></span>|
|`MethodNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-241">検索するメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-241">The namespace of method being looked up.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-242">検索するメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-242">The name of the method being looked up.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-243">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-243">Signature of the method (comma-separated list of type names).</span></span>|
|`EntryPoint`|`win:UInt64`|<span data-ttu-id="a9b7e-244">R2R メソッドのエントリポイントへのポインター</span><span class="sxs-lookup"><span data-stu-id="a9b7e-244">The pointer to the entry point of the R2R method</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-245">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-245">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="r2rgetentrypointstart-event"></a><span data-ttu-id="a9b7e-246">R2RGetEntryPointStart イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-246">R2RGetEntryPointStart event</span></span>

|<span data-ttu-id="a9b7e-247">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-247">Event</span></span>|<span data-ttu-id="a9b7e-248">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-248">Event ID</span></span>|<span data-ttu-id="a9b7e-249">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-249">Description</span></span>|
|----------------|---------------|-----------------|
|`R2RGetEntryPointStart`|<span data-ttu-id="a9b7e-250">160</span><span class="sxs-lookup"><span data-stu-id="a9b7e-250">160</span></span>|<span data-ttu-id="a9b7e-251">R2R エントリポイント参照が開始されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-251">Raised when an R2R entry point lookup starts.</span></span>|

|<span data-ttu-id="a9b7e-252">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-252">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-253">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-253">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-254">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-254">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="a9b7e-255">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-255">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-256">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-256">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="a9b7e-257">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-257">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-258">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-258">Field name</span></span>|<span data-ttu-id="a9b7e-259">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-259">Data type</span></span>|<span data-ttu-id="a9b7e-260">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-260">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-261">R2R メソッドの一意識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-261">Unique identifier of a R2R method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-262">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-262">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodloadverbose_v1-event"></a><span data-ttu-id="a9b7e-263">MethodLoadVerbose_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-263">MethodLoadVerbose_V1 event</span></span>

|<span data-ttu-id="a9b7e-264">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-264">Event</span></span>|<span data-ttu-id="a9b7e-265">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-265">Event ID</span></span>|<span data-ttu-id="a9b7e-266">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-266">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="a9b7e-267">143</span><span class="sxs-lookup"><span data-stu-id="a9b7e-267">143</span></span>|<span data-ttu-id="a9b7e-268">メソッドが JIT 読み込みされるとき、または NGEN イメージが読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-268">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="a9b7e-269">動的メソッドとジェネリック メソッドは、メソッドの読み込みに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-269">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="a9b7e-270">JIT ヘルパーは常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-270">JIT helpers always use this version.</span></span>|

|<span data-ttu-id="a9b7e-271">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-271">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-272">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-272">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-273">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-273">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="a9b7e-274">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-274">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-275">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-275">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="a9b7e-276">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-276">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-277">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-277">Field name</span></span>|<span data-ttu-id="a9b7e-278">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-278">Data type</span></span>|<span data-ttu-id="a9b7e-279">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-279">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-280">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-280">Unique identifier of the method.</span></span> <span data-ttu-id="a9b7e-281">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-281">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-282">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-282">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-283">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-283">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-284">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-284">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-285">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-285">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-286">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-286">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-287">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-287">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-288">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-288">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="a9b7e-289">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-289">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-290">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-290">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-291">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-291">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-292">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-292">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-293">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-293">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodloadverbose_v2-event"></a><span data-ttu-id="a9b7e-294">MethodLoadVerbose_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-294">MethodLoadVerbose_V2 event</span></span>

|<span data-ttu-id="a9b7e-295">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-295">Event</span></span>|<span data-ttu-id="a9b7e-296">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-296">Event ID</span></span>|<span data-ttu-id="a9b7e-297">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-297">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodLoadVerbose_V1`|<span data-ttu-id="a9b7e-298">143</span><span class="sxs-lookup"><span data-stu-id="a9b7e-298">143</span></span>|<span data-ttu-id="a9b7e-299">メソッドが JIT 読み込みされるとき、または NGEN イメージが読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-299">Raised when a method is JIT-loaded or an NGEN image is loaded.</span></span> <span data-ttu-id="a9b7e-300">動的メソッドとジェネリック メソッドは、メソッドの読み込みに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-300">Dynamic and generic methods always use this version for method loads.</span></span> <span data-ttu-id="a9b7e-301">JIT ヘルパーは常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-301">JIT helpers always use this version.</span></span>|

|<span data-ttu-id="a9b7e-302">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-302">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-303">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-304">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-304">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="a9b7e-305">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-305">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-306">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-306">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="a9b7e-307">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-307">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-308">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-308">Field name</span></span>|<span data-ttu-id="a9b7e-309">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-309">Data type</span></span>|<span data-ttu-id="a9b7e-310">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-310">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-311">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-311">Unique identifier of the method.</span></span> <span data-ttu-id="a9b7e-312">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-312">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-313">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-313">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-314">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-314">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-315">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-315">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-316">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-316">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-317">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-317">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-318">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-318">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-319">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-319">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="a9b7e-320">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-320">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-321">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-321">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-322">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-322">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-323">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-323">Signature of the method (comma-separated list of type names).</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="a9b7e-324">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-324">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-325">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-325">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunloadverbose_v1-event"></a><span data-ttu-id="a9b7e-326">MethodUnLoadVerbose_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-326">MethodUnLoadVerbose_V1 event</span></span>

|<span data-ttu-id="a9b7e-327">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-327">Event</span></span>|<span data-ttu-id="a9b7e-328">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-328">Event ID</span></span>|<span data-ttu-id="a9b7e-329">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-329">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V1`|<span data-ttu-id="a9b7e-330">144</span><span class="sxs-lookup"><span data-stu-id="a9b7e-330">144</span></span>|<span data-ttu-id="a9b7e-331">動的メソッドが破棄されるとき、またはモジュールがアンロードされるとき、あるいはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-331">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="a9b7e-332">動的メソッドは、メソッドのアンロードに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-332">Dynamic methods always use this version for method unloads.</span></span>|

|<span data-ttu-id="a9b7e-333">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-333">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-334">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-334">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-335">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-335">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="a9b7e-336">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-336">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-337">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-337">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="a9b7e-338">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-338">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-339">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-339">Field name</span></span>|<span data-ttu-id="a9b7e-340">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-340">Data type</span></span>|<span data-ttu-id="a9b7e-341">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-341">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-342">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-342">Unique identifier of the method.</span></span> <span data-ttu-id="a9b7e-343">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-343">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-344">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-344">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-345">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-345">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-346">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-346">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-347">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-347">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-348">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-348">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-349">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-349">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-350">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-350">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="a9b7e-351">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-351">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-352">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-352">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-353">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-353">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-354">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-354">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-355">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-355">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodunloadverbose_v2-event"></a><span data-ttu-id="a9b7e-356">MethodUnLoadVerbose_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-356">MethodUnLoadVerbose_V2 event</span></span>

|<span data-ttu-id="a9b7e-357">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-357">Event</span></span>|<span data-ttu-id="a9b7e-358">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-358">Event ID</span></span>|<span data-ttu-id="a9b7e-359">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-359">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodUnLoadVerbose_V2`|<span data-ttu-id="a9b7e-360">144</span><span class="sxs-lookup"><span data-stu-id="a9b7e-360">144</span></span>|<span data-ttu-id="a9b7e-361">動的メソッドが破棄されるとき、またはモジュールがアンロードされるとき、あるいはアプリケーション ドメインが破棄されるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-361">Raised when a dynamic method is destroyed, a module is unloaded, or an application domain is destroyed.</span></span> <span data-ttu-id="a9b7e-362">動的メソッドは、メソッドのアンロードに常にこのバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-362">Dynamic methods always use this version for method unloads.</span></span>|

|<span data-ttu-id="a9b7e-363">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-363">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-364">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-364">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-365">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-365">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="a9b7e-366">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-366">Informational (4)</span></span>|
|<span data-ttu-id="a9b7e-367">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-367">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="a9b7e-368">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-368">Informational (4)</span></span>|

|<span data-ttu-id="a9b7e-369">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-369">Field name</span></span>|<span data-ttu-id="a9b7e-370">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-370">Data type</span></span>|<span data-ttu-id="a9b7e-371">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-371">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-372">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-372">Unique identifier of the method.</span></span> <span data-ttu-id="a9b7e-373">JIT ヘルパー メソッドの場合は、メソッドの開始アドレスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-373">For JIT helper methods, set to the start address of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-374">このメソッドが属するモジュールの識別子 (JIT ヘルパーの場合は 0)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-374">Identifier of the module to which this method belongs (0 for JIT helpers).</span></span>|
|`MethodStartAddress`|`win:UInt64`|<span data-ttu-id="a9b7e-375">開始アドレス。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-375">Start address.</span></span>|
|`MethodSize`|`win:UInt32`|<span data-ttu-id="a9b7e-376">メソッドの長さ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-376">Method length.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-377">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-377">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodFlags`|`win:UInt32`|<span data-ttu-id="a9b7e-378">0x1: 動的メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-378">0x1: Dynamic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-379">0x2: ジェネリック メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-379">0x2: Generic method.</span></span><br /><br /> <span data-ttu-id="a9b7e-380">0x4: JIT コンパイル済みメソッド (それ以外の場合は NGen.exe により生成)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-380">0x4: JIT-compiled method (otherwise, generated by NGen.exe)</span></span><br /><br /> <span data-ttu-id="a9b7e-381">0x8: ヘルパー メソッド。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-381">0x8: Helper method.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-382">メソッドに関連付けられた完全な名前空間名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-382">Full namespace name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-383">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-383">Full class name associated with the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-384">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-384">Signature of the method (comma-separated list of type names).</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="a9b7e-385">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-385">ReJIT ID of the method.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-386">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-386">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittingstarted_v1-event"></a><span data-ttu-id="a9b7e-387">MethodJittingStarted_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-387">MethodJittingStarted_V1 event</span></span>

<span data-ttu-id="a9b7e-388">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-388">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="a9b7e-389">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-389">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-390">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-390">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-391">`JITKeyword` (0x10)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-391">`JITKeyword` (0x10)</span></span> |<span data-ttu-id="a9b7e-392">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-392">Verbose (5)</span></span>|
|<span data-ttu-id="a9b7e-393">`NGenKeyword` 0x20</span><span class="sxs-lookup"><span data-stu-id="a9b7e-393">`NGenKeyword` (0x20)</span></span> |<span data-ttu-id="a9b7e-394">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-394">Verbose (5)</span></span>|

|<span data-ttu-id="a9b7e-395">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-395">Event</span></span>|<span data-ttu-id="a9b7e-396">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-396">Event ID</span></span>|<span data-ttu-id="a9b7e-397">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-397">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJittingStarted_V1`|<span data-ttu-id="a9b7e-398">145</span><span class="sxs-lookup"><span data-stu-id="a9b7e-398">145</span></span>|<span data-ttu-id="a9b7e-399">メソッドが JIT コンパイルされているときに発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-399">Raised when a method is being JIT-compiled.</span></span>|

|<span data-ttu-id="a9b7e-400">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-400">Field name</span></span>|<span data-ttu-id="a9b7e-401">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-401">Data type</span></span>|<span data-ttu-id="a9b7e-402">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-402">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-403">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-403">Unique identifier of the method.</span></span>|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="a9b7e-404">このメソッドが属するモジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-404">Identifier of the module to which this method belongs.</span></span>|
|`MethodToken`|`win:UInt32`|<span data-ttu-id="a9b7e-405">動的メソッドおよび JIT ヘルパーの場合は 0。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-405">0 for dynamic methods and JIT helpers.</span></span>|
|`MethodILSize`|`win:UInt32`|<span data-ttu-id="a9b7e-406">JIT コンパイルされるメソッドの共通中間言語 (CIL) のサイズ。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-406">The size of the Common Intermediate Language (CIL) for the method that is being JIT-compiled.</span></span>|
|`MethodNameSpace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-407">メソッドに関連付けられた完全クラス名。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-407">Full class name associated with the method.</span></span>|
|`MethodName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-408">メソッドの名前です。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-408">Name of the method.</span></span>|
|`MethodSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-409">メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-409">Signature of the method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-410">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-410">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjitinliningsucceeded-event"></a><span data-ttu-id="a9b7e-411">MethodJitInliningSucceeded イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-411">MethodJitInliningSucceeded event</span></span>

|<span data-ttu-id="a9b7e-412">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-412">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-413">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-413">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-414">`JITTracingKeyword` 0x1000</span><span class="sxs-lookup"><span data-stu-id="a9b7e-414">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="a9b7e-415">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-415">Verbose (5)</span></span>|

|<span data-ttu-id="a9b7e-416">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-416">Event</span></span>|<span data-ttu-id="a9b7e-417">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-417">Event ID</span></span>|<span data-ttu-id="a9b7e-418">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-418">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitInliningSucceeded`|<span data-ttu-id="a9b7e-419">185</span><span class="sxs-lookup"><span data-stu-id="a9b7e-419">185</span></span>|<span data-ttu-id="a9b7e-420">JIT コンパイラによってメソッドが正常にインライン化された場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-420">Raised when a method is successfully inlined by the JIT compiler.</span></span>|

|<span data-ttu-id="a9b7e-421">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-421">Field name</span></span>|<span data-ttu-id="a9b7e-422">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-422">Data type</span></span>|<span data-ttu-id="a9b7e-423">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-423">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-424">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-424">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-425">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-425">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-426">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-426">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`InlinerNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-427">このインライナ ("parent") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-427">The namespace of inliner ("parent") method.</span></span>|
|`InlinerName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-428">このインライナ ("parent") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-428">Name of the inliner ("parent") method.</span></span>|
|`InlinerNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-429">このインライナ ("parent") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-429">Signature of the inliner ("parent") method (comma-separated list of type names).</span></span>|
|`InlineeNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-430">インライン ("child") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-430">The namespace of inlinee ("child") method.</span></span>|
|`InlineeName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-431">インライン ("child") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-431">Name of the inlinee ("child") method.</span></span>|
|`InlineeNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-432">インライン ("child") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-432">Signature of the inlinee ("child") method (comma-separated list of type names).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-433">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-433">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjitinliningfailed-event"></a><span data-ttu-id="a9b7e-434">MethodJitInliningFailed イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-434">MethodJitInliningFailed event</span></span>

|<span data-ttu-id="a9b7e-435">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-435">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-436">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-436">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-437">`JITTracingKeyword` 0x1000</span><span class="sxs-lookup"><span data-stu-id="a9b7e-437">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="a9b7e-438">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-438">Verbose (5)</span></span>|

|<span data-ttu-id="a9b7e-439">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-439">Event</span></span>|<span data-ttu-id="a9b7e-440">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-440">Event ID</span></span>|<span data-ttu-id="a9b7e-441">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-441">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitInliningFailed`|<span data-ttu-id="a9b7e-442">192</span><span class="sxs-lookup"><span data-stu-id="a9b7e-442">192</span></span>|<span data-ttu-id="a9b7e-443">メソッドが JIT コンパイラによってインライン化されなかった場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-443">Raised when a method was failed to be inlined by the JIT compiler.</span></span>|

|<span data-ttu-id="a9b7e-444">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-444">Field name</span></span>|<span data-ttu-id="a9b7e-445">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-445">Data type</span></span>|<span data-ttu-id="a9b7e-446">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-446">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-447">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-447">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-448">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-448">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-449">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-449">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`InlinerNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-450">このインライナ ("parent") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-450">The namespace of inliner ("parent") method.</span></span>|
|`InlinerName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-451">このインライナ ("parent") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-451">Name of the inliner ("parent") method.</span></span>|
|`InlinerNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-452">このインライナ ("parent") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-452">Signature of the inliner ("parent") method (comma-separated list of type names).</span></span>|
|`InlineeNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-453">インライン ("child") メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-453">The namespace of inlinee ("child") method.</span></span>|
|`InlineeName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-454">インライン ("child") メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-454">Name of the inlinee ("child") method.</span></span>|
|`InlineeNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-455">インライン ("child") メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-455">Signature of the inlinee ("child") method (comma-separated list of type names).</span></span>|
|`FailAlways`|`win:Boolean`|<span data-ttu-id="a9b7e-456">メソッドが not linable としてマークされているかどうか。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-456">Whether the method is marked as not inlinable.</span></span>|
|`FailReason`|`win:UnicodeString`|<span data-ttu-id="a9b7e-457">理由のインライン展開に失敗しました。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-457">Reason inlining failed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-458">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-458">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittailcallsucceeded-event"></a><span data-ttu-id="a9b7e-459">MethodJitTailCallSucceeded イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-459">MethodJitTailCallSucceeded event</span></span>

|<span data-ttu-id="a9b7e-460">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-460">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-461">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-461">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-462">`JITTracingKeyword` 0x1000</span><span class="sxs-lookup"><span data-stu-id="a9b7e-462">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="a9b7e-463">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-463">Verbose (5)</span></span>|

|<span data-ttu-id="a9b7e-464">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-464">Event</span></span>|<span data-ttu-id="a9b7e-465">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-465">Event ID</span></span>|<span data-ttu-id="a9b7e-466">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-466">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitTailCallSucceeded`|<span data-ttu-id="a9b7e-467">192</span><span class="sxs-lookup"><span data-stu-id="a9b7e-467">192</span></span>|<span data-ttu-id="a9b7e-468">JIT コンパイラによって発生します。メソッドを正常に終了させることができます。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-468">Raised by the JIT compiler when a method can be successfully tail called.</span></span>|

|<span data-ttu-id="a9b7e-469">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-469">Field name</span></span>|<span data-ttu-id="a9b7e-470">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-470">Data type</span></span>|<span data-ttu-id="a9b7e-471">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-471">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-472">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-472">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-473">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-473">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-474">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-474">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`CallerNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-475">呼び出し元のメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-475">Namespace of the caller method.</span></span>|
|`CallerName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-476">呼び出し元のメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-476">Name of the caller method.</span></span>|
|`CallerNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-477">呼び出し元のメソッドのシグネチャ (型名のコンマ区切りのリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-477">Signature of the caller method (Comma-separated list of type names).</span></span>|
|`CalleeNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-478">呼び出し先メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-478">Namespace of the callee method.</span></span>|
|`CalleeName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-479">呼び出し先メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-479">Name of the callee method.</span></span>|
|`CalleeNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-480">呼び出し先メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-480">Signature of the callee method (Comma-separated list of type names).</span></span>|
|`TailPrefix`|`win:Boolean`|<span data-ttu-id="a9b7e-481">Tail プレフィックス命令であるかどうか。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-481">Whether it is a tail prefix instruction.</span></span>|
|`TailCallType`|`win:UInt32`|<span data-ttu-id="a9b7e-482">末尾呼び出しの種類。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-482">The type of tail call.</span></span><br/><br/><span data-ttu-id="a9b7e-483">0: tail 呼び出しを最適化します (エピローグ + jmp)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-483">0: Optimized tail call (epilog + jmp)</span></span><br/><br/><span data-ttu-id="a9b7e-484">1: 再帰的な末尾呼び出し (メソッドの末尾の呼び出し自体)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-484">1: Recursive tail call (method tail calls itself)</span></span><br/><br/><span data-ttu-id="a9b7e-485">2: ヘルパーによるテール呼び出し</span><span class="sxs-lookup"><span data-stu-id="a9b7e-485">2: Helper assisted tail call</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-486">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-486">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodjittailcallfailed-event"></a><span data-ttu-id="a9b7e-487">MethodJitTailCallFailed イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-487">MethodJitTailCallFailed event</span></span>

|<span data-ttu-id="a9b7e-488">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-488">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-489">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-489">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-490">`JITTracingKeyword` 0x1000</span><span class="sxs-lookup"><span data-stu-id="a9b7e-490">`JITTracingKeyword` (0x1000)</span></span> |<span data-ttu-id="a9b7e-491">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-491">Verbose (5)</span></span>|

|<span data-ttu-id="a9b7e-492">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-492">Event</span></span>|<span data-ttu-id="a9b7e-493">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-493">Event ID</span></span>|<span data-ttu-id="a9b7e-494">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-494">Description</span></span>|
|-----------|--------------|-----------------|
|`MethodJitTailCallFailed`|<span data-ttu-id="a9b7e-495">191</span><span class="sxs-lookup"><span data-stu-id="a9b7e-495">191</span></span>|<span data-ttu-id="a9b7e-496">メソッドが末尾の呼び出しに失敗したときに JIT コンパイラによって発生します。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-496">Raised by the JIT compiler when a method was failed to be tail called.</span></span>|

|<span data-ttu-id="a9b7e-497">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-497">Field name</span></span>|<span data-ttu-id="a9b7e-498">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-498">Data type</span></span>|<span data-ttu-id="a9b7e-499">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-499">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodBeingCompiledNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-500">コンパイルされるメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-500">Namespace of the method being compiled.</span></span>|
|`MethodBeingCompiledName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-501">コンパイルされるメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-501">Name of the method being compiled.</span></span>|
|`MethodBeingCompiledNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-502">コンパイルされるメソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-502">Signature of the method (comma-separated list of type names) being compiled.</span></span>|
|`CallerNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-503">呼び出し元のメソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-503">Namespace of the caller method.</span></span>|
|<span data-ttu-id="a9b7e-504">`CallerNam`e</span><span class="sxs-lookup"><span data-stu-id="a9b7e-504">`CallerNam`e</span></span>|`win:UnicodeString`|<span data-ttu-id="a9b7e-505">呼び出し元のメソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-505">Name of the caller method.</span></span>|
|`CallerNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-506">呼び出し元のメソッドのシグネチャ (型名のコンマ区切りのリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-506">Signature of the caller method (Comma-separated list of type names).</span></span>|
|`CalleeNamespace`|`win:UnicodeString`|<span data-ttu-id="a9b7e-507">呼び出し先メソッドの名前空間。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-507">Namespace of the callee method.</span></span>|
|`CalleeName`|`win:UnicodeString`|<span data-ttu-id="a9b7e-508">呼び出し先メソッドの名前。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-508">Name of the callee method.</span></span>|
|`CalleeNameSignature`|`win:UnicodeString`|<span data-ttu-id="a9b7e-509">呼び出し先メソッドのシグネチャ (型名のコンマ区切りリスト)。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-509">Signature of the callee method (Comma-separated list of type names).</span></span>|
|`TailPrefix`|`win:Boolean`|<span data-ttu-id="a9b7e-510">Tail プレフィックス命令であるかどうか。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-510">Whether it is a tail prefix instruction.</span></span>|
|`FailReason`|`win:UnicodeString`|<span data-ttu-id="a9b7e-511">理由の末尾の呼び出しが失敗しました。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-511">Reason tail call failed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-512">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-512">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="methodiltonativemap-event"></a><span data-ttu-id="a9b7e-513">MethodILToNativeMap イベント</span><span class="sxs-lookup"><span data-stu-id="a9b7e-513">MethodILToNativeMap event</span></span>

|<span data-ttu-id="a9b7e-514">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a9b7e-514">Keyword for raising the event</span></span>|<span data-ttu-id="a9b7e-515">Level</span><span class="sxs-lookup"><span data-stu-id="a9b7e-515">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a9b7e-516">`JittedMethodILToNativeMapKeyword` 0x20000</span><span class="sxs-lookup"><span data-stu-id="a9b7e-516">`JittedMethodILToNativeMapKeyword` (0x20000)</span></span> |<span data-ttu-id="a9b7e-517">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a9b7e-517">Verbose (5)</span></span>|

|<span data-ttu-id="a9b7e-518">event</span><span class="sxs-lookup"><span data-stu-id="a9b7e-518">Event</span></span>|<span data-ttu-id="a9b7e-519">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a9b7e-519">Event ID</span></span>|<span data-ttu-id="a9b7e-520">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-520">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodILToNativeMap`|<span data-ttu-id="a9b7e-521">190</span><span class="sxs-lookup"><span data-stu-id="a9b7e-521">190</span></span>|<span data-ttu-id="a9b7e-522">JIT コンパイル済みメソッドの IL からネイティブへのマップイベントをマップします。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-522">Maps the IL-to-native map event for JIT-compiled methods.</span></span>|

|<span data-ttu-id="a9b7e-523">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a9b7e-523">Field name</span></span>|<span data-ttu-id="a9b7e-524">データ型</span><span class="sxs-lookup"><span data-stu-id="a9b7e-524">Data type</span></span>|<span data-ttu-id="a9b7e-525">説明</span><span class="sxs-lookup"><span data-stu-id="a9b7e-525">Description</span></span>|
|----------------|---------------|-----------------|
|`MethodID`|`win:UInt64`|<span data-ttu-id="a9b7e-526">メソッドの一意の識別子。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-526">Unique identifier of a method.</span></span>|
|`ReJITID`|`win:UInt64`|<span data-ttu-id="a9b7e-527">メソッドの ReJIT ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-527">The ReJIT ID of the method.</span></span>|
|`MethodExtent`|`win:UInt8`|<span data-ttu-id="a9b7e-528">Just-in-time メソッドの範囲。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-528">The extent for the jitted method.</span></span>|
|`CountOfMapEntries`|`win:UInt8`|<span data-ttu-id="a9b7e-529">マップエントリの数</span><span class="sxs-lookup"><span data-stu-id="a9b7e-529">Number of map entries</span></span>|
|`ILOffsets`|`win:UInt32`|<span data-ttu-id="a9b7e-530">オフセット IL。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-530">The IL offset.</span></span>|
|`NativeOffsets`|`win:UInt32`|<span data-ttu-id="a9b7e-531">ネイティブコードオフセット。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-531">The native code offset.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a9b7e-532">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a9b7e-532">Unique ID for the instance of CoreCLR.</span></span>|
