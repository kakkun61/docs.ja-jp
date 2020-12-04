---
title: ローダーとバインダーのランタイムイベント
description: アセンブリローダーとバインダーに関する情報を収集するローダーおよびバインダー ETW イベントに固有の診断情報を収集する .NET ランタイムイベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- Assembly Loader events (CoreCLR)
- Assembly Binder events (CoreCLR)
- ETW, EventPipe, LTTng assembly loader and binder events (CoreCLR)
ms.openlocfilehash: 2284c580482f6b93a77f44649225ff7e5485666a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96594109"
---
# <a name="net-runtime-loader-and-binder-events"></a><span data-ttu-id="83070-103">.NET ランタイムローダーとバインダーイベント</span><span class="sxs-lookup"><span data-stu-id="83070-103">.NET runtime loader and binder events</span></span>

<span data-ttu-id="83070-104">これらのイベントは、アセンブリとモジュールの読み込みとアンロードに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="83070-104">These events collect information relating to loading and unloading assemblies and modules.</span></span> <span data-ttu-id="83070-105">診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83070-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

|<span data-ttu-id="83070-106">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-106">Keyword for raising the event</span></span>|<span data-ttu-id="83070-107">event</span><span class="sxs-lookup"><span data-stu-id="83070-107">Event</span></span>|<span data-ttu-id="83070-108">Level</span><span class="sxs-lookup"><span data-stu-id="83070-108">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-109">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-109">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-110">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-110">Informational (4)</span></span>|

|<span data-ttu-id="83070-111">event</span><span class="sxs-lookup"><span data-stu-id="83070-111">Event</span></span>|<span data-ttu-id="83070-112">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-112">Event ID</span></span>|<span data-ttu-id="83070-113">説明</span><span class="sxs-lookup"><span data-stu-id="83070-113">Description</span></span>|
|-----------|--------------|-----------------|
|`DomainModuleLoad_V1`|<span data-ttu-id="83070-114">151</span><span class="sxs-lookup"><span data-stu-id="83070-114">151</span></span>|<span data-ttu-id="83070-115">モジュールがアプリケーション ドメインに読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="83070-115">Raised when a module is loaded for an application domain.</span></span>|

## <a name="moduleload_v2-event"></a><span data-ttu-id="83070-116">ModuleLoad_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="83070-116">ModuleLoad_V2 event</span></span>

|<span data-ttu-id="83070-117">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-117">Keyword for raising the event</span></span>|<span data-ttu-id="83070-118">event</span><span class="sxs-lookup"><span data-stu-id="83070-118">Event</span></span>|<span data-ttu-id="83070-119">Level</span><span class="sxs-lookup"><span data-stu-id="83070-119">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-120">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-120">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-121">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-121">Informational (4)</span></span>|

|<span data-ttu-id="83070-122">event</span><span class="sxs-lookup"><span data-stu-id="83070-122">Event</span></span>|<span data-ttu-id="83070-123">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-123">Event ID</span></span>|<span data-ttu-id="83070-124">説明</span><span class="sxs-lookup"><span data-stu-id="83070-124">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleLoad_V2`|<span data-ttu-id="83070-125">152</span><span class="sxs-lookup"><span data-stu-id="83070-125">152</span></span>|<span data-ttu-id="83070-126">プロセスの有効期間中にモジュールが読み込まれるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="83070-126">Raised when a module is loaded during the lifetime of a process.</span></span>|

|<span data-ttu-id="83070-127">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-127">Field name</span></span>|<span data-ttu-id="83070-128">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-128">Data type</span></span>|<span data-ttu-id="83070-129">説明</span><span class="sxs-lookup"><span data-stu-id="83070-129">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="83070-130">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="83070-130">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="83070-131">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="83070-131">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="83070-132">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-132">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="83070-133">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="83070-133">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="83070-134">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-134">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="83070-135">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-135">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="83070-136">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="83070-136">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="83070-137">モジュールの共通中間言語 (CIL) イメージのパス、または動的アセンブリ (null で終わる) の場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="83070-137">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="83070-138">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="83070-138">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-139">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-139">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="83070-140">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="83070-140">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="83070-141">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="83070-141">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-142">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-142">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="83070-143">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-143">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="83070-144">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-144">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="83070-145">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-145">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-146">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-146">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="83070-147">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-147">In some cases, this may just be a file name.</span></span>|

## <a name="moduleunload_v2-event"></a><span data-ttu-id="83070-148">ModuleUnload_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="83070-148">ModuleUnload_V2 event</span></span>

|<span data-ttu-id="83070-149">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-149">Keyword for raising the event</span></span>|<span data-ttu-id="83070-150">event</span><span class="sxs-lookup"><span data-stu-id="83070-150">Event</span></span>|<span data-ttu-id="83070-151">Level</span><span class="sxs-lookup"><span data-stu-id="83070-151">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-152">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-152">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-153">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-153">Informational (4)</span></span>|

|<span data-ttu-id="83070-154">event</span><span class="sxs-lookup"><span data-stu-id="83070-154">Event</span></span>|<span data-ttu-id="83070-155">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-155">Event ID</span></span>|<span data-ttu-id="83070-156">説明</span><span class="sxs-lookup"><span data-stu-id="83070-156">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleUnload_V2`|<span data-ttu-id="83070-157">153</span><span class="sxs-lookup"><span data-stu-id="83070-157">153</span></span>|<span data-ttu-id="83070-158">プロセスの有効期間中にモジュールがアンロードされるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="83070-158">Raised when a module is unloaded during the lifetime of a process.</span></span>|

|<span data-ttu-id="83070-159">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-159">Field name</span></span>|<span data-ttu-id="83070-160">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-160">Data type</span></span>|<span data-ttu-id="83070-161">説明</span><span class="sxs-lookup"><span data-stu-id="83070-161">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="83070-162">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="83070-162">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="83070-163">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="83070-163">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="83070-164">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-164">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="83070-165">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="83070-165">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="83070-166">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-166">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="83070-167">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-167">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="83070-168">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="83070-168">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="83070-169">モジュールの共通中間言語 (CIL) イメージのパス、または動的アセンブリ (null で終わる) の場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="83070-169">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="83070-170">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="83070-170">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|``win:UInt16``|<span data-ttu-id="83070-171">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-171">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="83070-172">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="83070-172">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="83070-173">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="83070-173">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-174">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-174">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="83070-175">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-175">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="83070-176">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-176">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="83070-177">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-177">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-178">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-178">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="83070-179">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-179">In some cases, this may just be a file name.</span></span>|

## <a name="moduledcstart_v2-event"></a><span data-ttu-id="83070-180">ModuleDCStart_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="83070-180">ModuleDCStart_V2 event</span></span>

|<span data-ttu-id="83070-181">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-181">Keyword for raising the event</span></span>|<span data-ttu-id="83070-182">event</span><span class="sxs-lookup"><span data-stu-id="83070-182">Event</span></span>|<span data-ttu-id="83070-183">Level</span><span class="sxs-lookup"><span data-stu-id="83070-183">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-184">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-184">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-185">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-185">Informational (4)</span></span>

|<span data-ttu-id="83070-186">event</span><span class="sxs-lookup"><span data-stu-id="83070-186">Event</span></span>|<span data-ttu-id="83070-187">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-187">Event ID</span></span>|<span data-ttu-id="83070-188">説明</span><span class="sxs-lookup"><span data-stu-id="83070-188">Description</span></span>
|-----------|--------------|-----------------|
|`ModuleDCStart_V2`|<span data-ttu-id="83070-189">153</span><span class="sxs-lookup"><span data-stu-id="83070-189">153</span></span>|<span data-ttu-id="83070-190">開始ランダウン中にモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="83070-190">Enumerates modules during a start rundown.</span></span>|

|<span data-ttu-id="83070-191">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-191">Field name</span></span>|<span data-ttu-id="83070-192">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-192">Data type</span></span>|<span data-ttu-id="83070-193">説明</span><span class="sxs-lookup"><span data-stu-id="83070-193">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="83070-194">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="83070-194">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="83070-195">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="83070-195">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="83070-196">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-196">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="83070-197">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="83070-197">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="83070-198">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-198">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="83070-199">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-199">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="83070-200">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="83070-200">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="83070-201">モジュールの共通中間言語 (CIL) イメージのパス、または動的アセンブリ (null で終わる) の場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="83070-201">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="83070-202">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="83070-202">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-203">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-203">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="83070-204">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="83070-204">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="83070-205">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="83070-205">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-206">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-206">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="83070-207">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-207">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="83070-208">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-208">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="83070-209">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-209">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-210">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-210">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="83070-211">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-211">In some cases, this may just be a file name.</span></span>|

## <a name="moduledcend_v2-event"></a><span data-ttu-id="83070-212">ModuleDCEnd_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="83070-212">ModuleDCEnd_V2 event</span></span>

|<span data-ttu-id="83070-213">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-213">Keyword for raising the event</span></span>|<span data-ttu-id="83070-214">event</span><span class="sxs-lookup"><span data-stu-id="83070-214">Event</span></span>|<span data-ttu-id="83070-215">Level</span><span class="sxs-lookup"><span data-stu-id="83070-215">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-216">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-216">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-217">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-217">Informational (4)</span></span>|

|<span data-ttu-id="83070-218">event</span><span class="sxs-lookup"><span data-stu-id="83070-218">Event</span></span>|<span data-ttu-id="83070-219">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-219">Event ID</span></span>|<span data-ttu-id="83070-220">説明</span><span class="sxs-lookup"><span data-stu-id="83070-220">Description</span></span>|
|-----------|--------------|-----------------|
|`ModuleDCEnd_V2`|<span data-ttu-id="83070-221">154</span><span class="sxs-lookup"><span data-stu-id="83070-221">154</span></span>|<span data-ttu-id="83070-222">終了ランダウン中にモジュールを列挙します。</span><span class="sxs-lookup"><span data-stu-id="83070-222">Enumerates modules during an end rundown.</span></span>|

|<span data-ttu-id="83070-223">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-223">Field name</span></span>|<span data-ttu-id="83070-224">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-224">Data type</span></span>|<span data-ttu-id="83070-225">説明</span><span class="sxs-lookup"><span data-stu-id="83070-225">Description</span></span>|
|----------------|---------------|-----------------|
|`ModuleID`|`win:UInt64`|<span data-ttu-id="83070-226">モジュールの一意な ID。</span><span class="sxs-lookup"><span data-stu-id="83070-226">Unique ID for the module.</span></span>|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="83070-227">このモジュールが存在するアセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="83070-227">ID of the assembly in which this module resides.</span></span>|
|`ModuleFlags`|`win:UInt32`|<span data-ttu-id="83070-228">0x1: ドメインに中立的なモジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-228">0x1: Domain neutral module.</span></span><br /><br /> <span data-ttu-id="83070-229">0x2: モジュールにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="83070-229">0x2: Module has a native image.</span></span><br /><br /> <span data-ttu-id="83070-230">0x4: 動的モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-230">0x4: Dynamic module.</span></span><br /><br /> <span data-ttu-id="83070-231">0x8: マニフェスト モジュール。</span><span class="sxs-lookup"><span data-stu-id="83070-231">0x8: Manifest module.</span></span>|
|`Reserved1`|`win:UInt32`|<span data-ttu-id="83070-232">予約済みのフィールド。</span><span class="sxs-lookup"><span data-stu-id="83070-232">Reserved field.</span></span>|
|`ModuleILPath`|`win:UnicodeString`|<span data-ttu-id="83070-233">モジュールの共通中間言語 (CIL) イメージのパス、または動的アセンブリ (null で終わる) の場合は動的モジュール名。</span><span class="sxs-lookup"><span data-stu-id="83070-233">Path of the Common Intermediate Language (CIL) image for the module, or dynamic module name if it is a dynamic assembly (null-terminated).</span></span>|
|`ModuleNativePath`|`win:UnicodeString`|<span data-ttu-id="83070-234">モジュール ネイティブ イメージがある場合、そのパス (null で終わる)。</span><span class="sxs-lookup"><span data-stu-id="83070-234">Path of the module native image, if present (null-terminated).</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-235">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-235">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|`ManagedPdbSignature`|`win:GUID`|<span data-ttu-id="83070-236">このモジュールに一致するマネージド プログラム データベース (PDB) の GUID の署名。</span><span class="sxs-lookup"><span data-stu-id="83070-236">GUID signature of the managed program database (PDB) that matches this module.</span></span>|
|`ManagedPdbAge`|`win:UInt32`|<span data-ttu-id="83070-237">このモジュールに一致する管理対象 PDB に書き込まれた期間を表す数値。</span><span class="sxs-lookup"><span data-stu-id="83070-237">Age number written to the managed PDB that matches this module.</span></span>|
|`ManagedPdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-238">このモジュールに一致する管理対象の PDB が構成されている場所へのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-238">Path to the location where the managed PDB that matches this module was built.</span></span> <span data-ttu-id="83070-239">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-239">In some cases, this may just be a file name.</span></span>|
|`NativePdbSignature`|`win:GUID`|<span data-ttu-id="83070-240">このモジュールに一致するネイティブ イメージ ジェネレーター (NGen) PDB の GUID の署名 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-240">GUID signature of the Native Image Generator (NGen) PDB that matches this module, if applicable.</span></span>|
|`NativePdbAge`|`win:UInt32`|<span data-ttu-id="83070-241">このモジュールに一致する NGen PDB に書き込まれた期間を表す数値 (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-241">Age number written to the NGen PDB that matches this module, if applicable.</span></span>|
|`NativePdbBuildPath`|`win:UnicodeString`|<span data-ttu-id="83070-242">このモジュールに一致する管理対象の NGen PDB が構成されている場所へのパス (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="83070-242">Path to the location where the NGen PDB that matches this module was built, if applicable.</span></span> <span data-ttu-id="83070-243">これは、ファイル名だけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="83070-243">In some cases, this may just be a file name.</span></span>|

## <a name="assemblyload_v1-event"></a><span data-ttu-id="83070-244">AssemblyLoad_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="83070-244">AssemblyLoad_V1 event</span></span>

|<span data-ttu-id="83070-245">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-245">Keyword for raising the event</span></span>|<span data-ttu-id="83070-246">event</span><span class="sxs-lookup"><span data-stu-id="83070-246">Event</span></span>|<span data-ttu-id="83070-247">Level</span><span class="sxs-lookup"><span data-stu-id="83070-247">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-248">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-248">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-249">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-249">Informational (4)</span></span>|

|<span data-ttu-id="83070-250">event</span><span class="sxs-lookup"><span data-stu-id="83070-250">Event</span></span>|<span data-ttu-id="83070-251">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-251">Event ID</span></span>|<span data-ttu-id="83070-252">説明</span><span class="sxs-lookup"><span data-stu-id="83070-252">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoad_V1`|<span data-ttu-id="83070-253">154</span><span class="sxs-lookup"><span data-stu-id="83070-253">154</span></span>|<span data-ttu-id="83070-254">アセンブリが読み込まれたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="83070-254">Raised when an assembly is loaded.</span></span>|

|<span data-ttu-id="83070-255">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-255">Field name</span></span>|<span data-ttu-id="83070-256">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-256">Data type</span></span>|<span data-ttu-id="83070-257">説明</span><span class="sxs-lookup"><span data-stu-id="83070-257">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="83070-258">アセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-258">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="83070-259">このアセンブリのドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="83070-259">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="83070-260">アセンブリ バインディングを一意に識別する ID。</span><span class="sxs-lookup"><span data-stu-id="83070-260">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="83070-261">0x1: ドメインに中立的なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-261">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="83070-262">0x2: 動的アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-262">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="83070-263">0x4: アセンブリにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="83070-263">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="83070-264">0x8: 収集可能なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-264">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-265">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="83070-265">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-266">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-266">Unique ID for the instance of CoreCLR.</span></span>

## <a name="assemblyunload_v1-event"></a><span data-ttu-id="83070-267">AssemblyUnload_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="83070-267">AssemblyUnload_V1 event</span></span>

|<span data-ttu-id="83070-268">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-268">Keyword for raising the event</span></span>|<span data-ttu-id="83070-269">event</span><span class="sxs-lookup"><span data-stu-id="83070-269">Event</span></span>|<span data-ttu-id="83070-270">Level</span><span class="sxs-lookup"><span data-stu-id="83070-270">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-271">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-271">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-272">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-272">Informational (4)</span></span>|

|<span data-ttu-id="83070-273">event</span><span class="sxs-lookup"><span data-stu-id="83070-273">Event</span></span>|<span data-ttu-id="83070-274">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-274">Event ID</span></span>|<span data-ttu-id="83070-275">説明</span><span class="sxs-lookup"><span data-stu-id="83070-275">Description</span></span>|
|-----------|--------------|-----------------|
|`FireAssemblyUnload_V1`|<span data-ttu-id="83070-276">155</span><span class="sxs-lookup"><span data-stu-id="83070-276">155</span></span>|<span data-ttu-id="83070-277">アセンブリが読み込まれたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="83070-277">Raised when an assembly is loaded.</span></span>|

|<span data-ttu-id="83070-278">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-278">Field name</span></span>|<span data-ttu-id="83070-279">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-279">Data type</span></span>|<span data-ttu-id="83070-280">説明</span><span class="sxs-lookup"><span data-stu-id="83070-280">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="83070-281">アセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-281">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="83070-282">このアセンブリのドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="83070-282">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="83070-283">アセンブリ バインディングを一意に識別する ID。</span><span class="sxs-lookup"><span data-stu-id="83070-283">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="83070-284">0x1: ドメインに中立的なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-284">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="83070-285">0x2: 動的アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-285">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="83070-286">0x4: アセンブリにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="83070-286">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="83070-287">0x8: 収集可能なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-287">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-288">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="83070-288">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-289">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-289">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblydcstart_v1-event"></a><span data-ttu-id="83070-290">AssemblyDCStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="83070-290">AssemblyDCStart_V1 event</span></span>

|<span data-ttu-id="83070-291">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-291">Keyword for raising the event</span></span>|<span data-ttu-id="83070-292">event</span><span class="sxs-lookup"><span data-stu-id="83070-292">Event</span></span>|<span data-ttu-id="83070-293">Level</span><span class="sxs-lookup"><span data-stu-id="83070-293">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-294">`LoaderKeyword` (0x8)</span><span class="sxs-lookup"><span data-stu-id="83070-294">`LoaderKeyword` (0x8)</span></span>|`DomainModuleLoad_V1`|<span data-ttu-id="83070-295">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-295">Informational (4)</span></span>|

|<span data-ttu-id="83070-296">event</span><span class="sxs-lookup"><span data-stu-id="83070-296">Event</span></span>|<span data-ttu-id="83070-297">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-297">Event ID</span></span>|<span data-ttu-id="83070-298">説明</span><span class="sxs-lookup"><span data-stu-id="83070-298">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyDCStart_V1`|<span data-ttu-id="83070-299">155</span><span class="sxs-lookup"><span data-stu-id="83070-299">155</span></span>|<span data-ttu-id="83070-300">開始ランダウン中にアセンブリを列挙します。</span><span class="sxs-lookup"><span data-stu-id="83070-300">Enumerates assemblies during a start rundown.</span></span>|

|<span data-ttu-id="83070-301">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-301">Field name</span></span>|<span data-ttu-id="83070-302">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-302">Data type</span></span>|<span data-ttu-id="83070-303">説明</span><span class="sxs-lookup"><span data-stu-id="83070-303">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyID`|`win:UInt64`|<span data-ttu-id="83070-304">アセンブリの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-304">Unique ID for the assembly.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="83070-305">このアセンブリのドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="83070-305">ID of the domain of this assembly.</span></span>|
|`BindingID`|`win:UInt64`|<span data-ttu-id="83070-306">アセンブリ バインディングを一意に識別する ID。</span><span class="sxs-lookup"><span data-stu-id="83070-306">ID that uniquely identifies the assembly binding.</span></span>|
|`AssemblyFlags`|`win:UInt32`|<span data-ttu-id="83070-307">0x1: ドメインに中立的なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-307">0x1: Domain neutral assembly.</span></span><br /><br /> <span data-ttu-id="83070-308">0x2: 動的アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-308">0x2: Dynamic assembly.</span></span><br /><br /> <span data-ttu-id="83070-309">0x4: アセンブリにネイティブ イメージがある。</span><span class="sxs-lookup"><span data-stu-id="83070-309">0x4: Assembly has a native image.</span></span><br /><br /> <span data-ttu-id="83070-310">0x8: 収集可能なアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-310">0x8: Collectible assembly.</span></span>|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-311">完全修飾アセンブリ名。</span><span class="sxs-lookup"><span data-stu-id="83070-311">Fully qualified assembly name.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-312">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-312">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadstart-event"></a><span data-ttu-id="83070-313">AssemblyLoadStart イベント</span><span class="sxs-lookup"><span data-stu-id="83070-313">AssemblyLoadStart event</span></span>

|<span data-ttu-id="83070-314">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-314">Keyword for raising the event</span></span>|<span data-ttu-id="83070-315">event</span><span class="sxs-lookup"><span data-stu-id="83070-315">Event</span></span>|<span data-ttu-id="83070-316">Level</span><span class="sxs-lookup"><span data-stu-id="83070-316">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-317">`Binder` 0x4</span><span class="sxs-lookup"><span data-stu-id="83070-317">`Binder` (0x4)</span></span>|`AssemblyLoadStart`|<span data-ttu-id="83070-318">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-318">Informational (4)</span></span>|

|<span data-ttu-id="83070-319">event</span><span class="sxs-lookup"><span data-stu-id="83070-319">Event</span></span>|<span data-ttu-id="83070-320">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-320">Event ID</span></span>|<span data-ttu-id="83070-321">説明</span><span class="sxs-lookup"><span data-stu-id="83070-321">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|<span data-ttu-id="83070-322">290</span><span class="sxs-lookup"><span data-stu-id="83070-322">290</span></span>|<span data-ttu-id="83070-323">アセンブリの読み込みが要求されました。</span><span class="sxs-lookup"><span data-stu-id="83070-323">An assembly load has been requested.</span></span>

|<span data-ttu-id="83070-324">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-324">Field name</span></span>|<span data-ttu-id="83070-325">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-325">Data type</span></span>|<span data-ttu-id="83070-326">説明</span><span class="sxs-lookup"><span data-stu-id="83070-326">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-327">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="83070-327">Name of assembly name.</span></span>|
|`AssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-328">アセンブリ名のパス。</span><span class="sxs-lookup"><span data-stu-id="83070-328">Path of assembly name.</span></span>|
|`RequestingAssembly`|`win:UnicodeString`|<span data-ttu-id="83070-329">要求している ("親") アセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-329">Name of the requesting ("parent") assembly.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="83070-330">アセンブリのコンテキストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="83070-330">Load context of the assembly.</span></span>|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="83070-331">要求している ("親") アセンブリのコンテキストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="83070-331">Load context of the requesting ("parent") assembly.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-332">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-332">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadstop-event"></a><span data-ttu-id="83070-333">AssemblyLoadStop イベント</span><span class="sxs-lookup"><span data-stu-id="83070-333">AssemblyLoadStop event</span></span>

|<span data-ttu-id="83070-334">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-334">Keyword for raising the event</span></span>|<span data-ttu-id="83070-335">event</span><span class="sxs-lookup"><span data-stu-id="83070-335">Event</span></span>|<span data-ttu-id="83070-336">Level</span><span class="sxs-lookup"><span data-stu-id="83070-336">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-337">`Binder` 0x4</span><span class="sxs-lookup"><span data-stu-id="83070-337">`Binder` (0x4)</span></span>|`AssemblyLoadStart`|<span data-ttu-id="83070-338">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-338">Informational (4)</span></span>|

|<span data-ttu-id="83070-339">event</span><span class="sxs-lookup"><span data-stu-id="83070-339">Event</span></span>|<span data-ttu-id="83070-340">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-340">Event ID</span></span>|<span data-ttu-id="83070-341">説明</span><span class="sxs-lookup"><span data-stu-id="83070-341">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadStart`|<span data-ttu-id="83070-342">291</span><span class="sxs-lookup"><span data-stu-id="83070-342">291</span></span>|<span data-ttu-id="83070-343">アセンブリの読み込みが要求されました。</span><span class="sxs-lookup"><span data-stu-id="83070-343">An assembly load has been requested.</span></span>

|<span data-ttu-id="83070-344">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-344">Field name</span></span>|<span data-ttu-id="83070-345">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-345">Data type</span></span>|<span data-ttu-id="83070-346">説明</span><span class="sxs-lookup"><span data-stu-id="83070-346">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-347">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="83070-347">Name of assembly name.</span></span>|
|`AssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-348">アセンブリ名のパス。</span><span class="sxs-lookup"><span data-stu-id="83070-348">Path of assembly name.</span></span>|
|`RequestingAssembly`|`win:UnicodeString`|<span data-ttu-id="83070-349">要求している ("親") アセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-349">Name of the requesting ("parent") assembly.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="83070-350">アセンブリのコンテキストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="83070-350">Load context of the assembly.</span></span>|
|`RequestingAssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="83070-351">要求している ("親") アセンブリのコンテキストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="83070-351">Load context of the requesting ("parent") assembly.</span></span>|
|`Success`|`win:Boolean`|<span data-ttu-id="83070-352">アセンブリの読み込みが成功したかどうか。</span><span class="sxs-lookup"><span data-stu-id="83070-352">Whether the assembly load succeeded.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-353">読み込まれたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-353">The name of assembly that was loaded.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-354">から読み込まれたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-354">The path of the assembly that was loaded from.</span></span>|
|`Cached`|`win:UnicodeString`|<span data-ttu-id="83070-355">読み込みがキャッシュされたかどうか。</span><span class="sxs-lookup"><span data-stu-id="83070-355">Whether the load was cached.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-356">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-356">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="resolutionattempted-event"></a><span data-ttu-id="83070-357">試行された解決イベント</span><span class="sxs-lookup"><span data-stu-id="83070-357">ResolutionAttempted event</span></span>

|<span data-ttu-id="83070-358">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-358">Keyword for raising the event</span></span>|<span data-ttu-id="83070-359">Level</span><span class="sxs-lookup"><span data-stu-id="83070-359">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-360">`Binder` 0x4</span><span class="sxs-lookup"><span data-stu-id="83070-360">`Binder` (0x4)</span></span>|<span data-ttu-id="83070-361">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-361">Informational (4)</span></span>|

|<span data-ttu-id="83070-362">event</span><span class="sxs-lookup"><span data-stu-id="83070-362">Event</span></span>|<span data-ttu-id="83070-363">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-363">Event ID</span></span>|<span data-ttu-id="83070-364">説明</span><span class="sxs-lookup"><span data-stu-id="83070-364">Description</span></span>|
|-----------|--------------|-----------------|
|`ResolutionAttempted`|<span data-ttu-id="83070-365">292</span><span class="sxs-lookup"><span data-stu-id="83070-365">292</span></span>|<span data-ttu-id="83070-366">アセンブリの読み込みが要求されました。</span><span class="sxs-lookup"><span data-stu-id="83070-366">An assembly load has been requested.</span></span>

|<span data-ttu-id="83070-367">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-367">Field name</span></span>|<span data-ttu-id="83070-368">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-368">Data type</span></span>|<span data-ttu-id="83070-369">説明</span><span class="sxs-lookup"><span data-stu-id="83070-369">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-370">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="83070-370">Name of assembly name.</span></span>|
|`Stage`|`win:UInt16`|<span data-ttu-id="83070-371">解決段階。</span><span class="sxs-lookup"><span data-stu-id="83070-371">The resolution stage.</span></span><br/><br/><span data-ttu-id="83070-372">0: 読み込み中に検索します。</span><span class="sxs-lookup"><span data-stu-id="83070-372">0: Find in load.</span></span><br/><br/><span data-ttu-id="83070-373">1: アセンブリの読み込みコンテキスト</span><span class="sxs-lookup"><span data-stu-id="83070-373">1: Assembly Load Context</span></span></br><br/><span data-ttu-id="83070-374">2: アプリケーションアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-374">2: Application assemblies.</span></span><br/><br/><span data-ttu-id="83070-375">3: 既定のアセンブリ読み込みコンテキストフォールバック。</span><span class="sxs-lookup"><span data-stu-id="83070-375">3: Default assembly load context fallback.</span></span> <br/><br/><span data-ttu-id="83070-376">4: サテライトアセンブリを解決します。</span><span class="sxs-lookup"><span data-stu-id="83070-376">4: Resolve satellite assembly.</span></span> <br/><br/><span data-ttu-id="83070-377">5: アセンブリの読み込みコンテキストを解決しています。</span><span class="sxs-lookup"><span data-stu-id="83070-377">5: Assembly load context resolving.</span></span><br/><br/><span data-ttu-id="83070-378">6: AppDomain アセンブリを解決しています。</span><span class="sxs-lookup"><span data-stu-id="83070-378">6: AppDomain assembly resolving.</span></span>
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="83070-379">アセンブリのコンテキストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="83070-379">Load context of the assembly.</span></span>|
|`Result`|`win:UInt16`|<span data-ttu-id="83070-380">解決試行の結果。</span><span class="sxs-lookup"><span data-stu-id="83070-380">The result of resolution attempt.</span></span><br/><br/><span data-ttu-id="83070-381">0: 成功</span><span class="sxs-lookup"><span data-stu-id="83070-381">0: Success</span></span><br/><br/><span data-ttu-id="83070-382">1: アセンブリ NotFound</span><span class="sxs-lookup"><span data-stu-id="83070-382">1: Assembly NotFound</span></span><br/><br/><span data-ttu-id="83070-383">2: 互換性のないバージョン</span><span class="sxs-lookup"><span data-stu-id="83070-383">2: Incompatible Version</span></span><br/><br/><span data-ttu-id="83070-384">3: アセンブリ名が一致しません</span><span class="sxs-lookup"><span data-stu-id="83070-384">3: Mismatched Assembly Name</span></span><br/><br/><span data-ttu-id="83070-385">4: 失敗</span><span class="sxs-lookup"><span data-stu-id="83070-385">4: Failure</span></span><br/><br/><span data-ttu-id="83070-386">5: 例外</span><span class="sxs-lookup"><span data-stu-id="83070-386">5: Exception</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-387">解決されたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-387">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-388">から解決されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-388">The path of the assembly that was resolved from.</span></span>|
|`ErrorMessage`|`win:UnicodeString`|<span data-ttu-id="83070-389">例外が発生した場合のエラーメッセージ。</span><span class="sxs-lookup"><span data-stu-id="83070-389">Error message if there is an exception.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-390">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-390">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadcontextresolvinghandlerinvoked-event"></a><span data-ttu-id="83070-391">AssemblyLoadContextResolvingHandlerInvoked イベント</span><span class="sxs-lookup"><span data-stu-id="83070-391">AssemblyLoadContextResolvingHandlerInvoked event</span></span>

|<span data-ttu-id="83070-392">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-392">Keyword for raising the event</span></span>|<span data-ttu-id="83070-393">Level</span><span class="sxs-lookup"><span data-stu-id="83070-393">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-394">`Binder` 0x4</span><span class="sxs-lookup"><span data-stu-id="83070-394">`Binder` (0x4)</span></span>|<span data-ttu-id="83070-395">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-395">Informational (4)</span></span>|

|<span data-ttu-id="83070-396">event</span><span class="sxs-lookup"><span data-stu-id="83070-396">Event</span></span>|<span data-ttu-id="83070-397">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-397">Event ID</span></span>|<span data-ttu-id="83070-398">説明</span><span class="sxs-lookup"><span data-stu-id="83070-398">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadContextResolvingHandlerInvoked`|<span data-ttu-id="83070-399">293</span><span class="sxs-lookup"><span data-stu-id="83070-399">293</span></span>|<span data-ttu-id="83070-400">[Assemblyloadcontext](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving)が呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="83070-400">An [AssemblyLoadContext.Resolving](xref:System.Runtime.Loader.AssemblyLoadContext.Resolving) handler has been invoked.</span></span>|

|<span data-ttu-id="83070-401">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-401">Field name</span></span>|<span data-ttu-id="83070-402">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-402">Data type</span></span>|<span data-ttu-id="83070-403">説明</span><span class="sxs-lookup"><span data-stu-id="83070-403">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-404">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="83070-404">Name of assembly name.</span></span>|
|`HandlerName`|`win:UnicodeString`|<span data-ttu-id="83070-405">呼び出されたハンドラーの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-405">Name of the handler invoked.</span></span>|
|`AssemblyLoadContext`|`win:UnicodeString`|<span data-ttu-id="83070-406">アセンブリのコンテキストを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="83070-406">Load context of the assembly.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-407">解決されたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-407">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-408">から解決されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-408">The path of the assembly that was resolved from.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-409">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-409">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="appdomainassemblyresolvehandlerinvoked-event"></a><span data-ttu-id="83070-410">AppDomainAssemblyResolveHandlerInvoked イベント</span><span class="sxs-lookup"><span data-stu-id="83070-410">AppDomainAssemblyResolveHandlerInvoked event</span></span>

|<span data-ttu-id="83070-411">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-411">Keyword for raising the event</span></span>|<span data-ttu-id="83070-412">Level</span><span class="sxs-lookup"><span data-stu-id="83070-412">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-413">`Binder` 0x4</span><span class="sxs-lookup"><span data-stu-id="83070-413">`Binder` (0x4)</span></span>|<span data-ttu-id="83070-414">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-414">Informational (4)</span></span>|

|<span data-ttu-id="83070-415">event</span><span class="sxs-lookup"><span data-stu-id="83070-415">Event</span></span>|<span data-ttu-id="83070-416">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-416">Event ID</span></span>|<span data-ttu-id="83070-417">説明</span><span class="sxs-lookup"><span data-stu-id="83070-417">Description</span></span>|
|-----------|--------------|-----------------|
|`AppDomainAssemblyResolveHandlerInvoked`|<span data-ttu-id="83070-418">294</span><span class="sxs-lookup"><span data-stu-id="83070-418">294</span></span>|<span data-ttu-id="83070-419"><xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType>ハンドラーが呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="83070-419">An <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> handler has been invoked.</span></span>|

|<span data-ttu-id="83070-420">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-420">Field name</span></span>|<span data-ttu-id="83070-421">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-421">Data type</span></span>|<span data-ttu-id="83070-422">説明</span><span class="sxs-lookup"><span data-stu-id="83070-422">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-423">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="83070-423">Name of assembly name.</span></span>|
|`HandlerName`|`win:UnicodeString`|<span data-ttu-id="83070-424">呼び出されたハンドラーの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-424">Name of the handler invoked.</span></span>|
|`ResultAssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-425">解決されたアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="83070-425">The name of assembly that was resolved.</span></span>|
|`ResultAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-426">から解決されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-426">The path of the assembly that was resolved from.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-427">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-427">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="assemblyloadfromresolvehandlerinvoked-event"></a><span data-ttu-id="83070-428">AssemblyLoadFromResolveHandlerInvoked イベント</span><span class="sxs-lookup"><span data-stu-id="83070-428">AssemblyLoadFromResolveHandlerInvoked event</span></span>

|<span data-ttu-id="83070-429">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-429">Keyword for raising the event</span></span>|<span data-ttu-id="83070-430">Level</span><span class="sxs-lookup"><span data-stu-id="83070-430">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-431">`Binder` 0x4</span><span class="sxs-lookup"><span data-stu-id="83070-431">`Binder` (0x4)</span></span>|<span data-ttu-id="83070-432">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-432">Informational (4)</span></span>|

|<span data-ttu-id="83070-433">event</span><span class="sxs-lookup"><span data-stu-id="83070-433">Event</span></span>|<span data-ttu-id="83070-434">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-434">Event ID</span></span>|<span data-ttu-id="83070-435">説明</span><span class="sxs-lookup"><span data-stu-id="83070-435">Description</span></span>|
|-----------|--------------|-----------------|
|`AssemblyLoadFromResolveHandlerInvoked`|<span data-ttu-id="83070-436">295</span><span class="sxs-lookup"><span data-stu-id="83070-436">295</span></span>|<span data-ttu-id="83070-437"><xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>ハンドラーが呼び出されました。</span><span class="sxs-lookup"><span data-stu-id="83070-437">An <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> handler has been invoked.</span></span>|

|<span data-ttu-id="83070-438">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-438">Field name</span></span>|<span data-ttu-id="83070-439">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-439">Data type</span></span>|<span data-ttu-id="83070-440">説明</span><span class="sxs-lookup"><span data-stu-id="83070-440">Description</span></span>|
|----------------|---------------|-----------------|
|`AssemblyName`|`win:UnicodeString`|<span data-ttu-id="83070-441">アセンブリ名の名前。</span><span class="sxs-lookup"><span data-stu-id="83070-441">Name of assembly name.</span></span>|
|`IsTrackedLoad`|`win:Boolean`|<span data-ttu-id="83070-442">アセンブリの読み込みを追跡するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="83070-442">Whether the assembly load is tracked.</span></span>|
|`RequestingAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-443">要求元のアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-443">The path of the requesting assembly.</span></span>|
|`ComputedRequestedAssemblyPath`|`win:UnicodeString`|<span data-ttu-id="83070-444">要求されたアセンブリのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-444">The path of the assembly that was requested.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-445">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-445">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="knownpathprobed-event"></a><span data-ttu-id="83070-446">KnownPathProbed イベント</span><span class="sxs-lookup"><span data-stu-id="83070-446">KnownPathProbed event</span></span>

|<span data-ttu-id="83070-447">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="83070-447">Keyword for raising the event</span></span>|<span data-ttu-id="83070-448">Level</span><span class="sxs-lookup"><span data-stu-id="83070-448">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="83070-449">`Binder` 0x4</span><span class="sxs-lookup"><span data-stu-id="83070-449">`Binder` (0x4)</span></span>|<span data-ttu-id="83070-450">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="83070-450">Informational (4)</span></span>|

|<span data-ttu-id="83070-451">event</span><span class="sxs-lookup"><span data-stu-id="83070-451">Event</span></span>|<span data-ttu-id="83070-452">イベント ID</span><span class="sxs-lookup"><span data-stu-id="83070-452">Event ID</span></span>|<span data-ttu-id="83070-453">説明</span><span class="sxs-lookup"><span data-stu-id="83070-453">Description</span></span>|
|-----------|--------------|-----------------|
|`KnownPathProbed`|<span data-ttu-id="83070-454">296</span><span class="sxs-lookup"><span data-stu-id="83070-454">296</span></span>|<span data-ttu-id="83070-455">アセンブリの既知のパスがプローブされました。</span><span class="sxs-lookup"><span data-stu-id="83070-455">A known path was probed for an assembly.</span></span>|

|<span data-ttu-id="83070-456">フィールド名</span><span class="sxs-lookup"><span data-stu-id="83070-456">Field Name</span></span>|<span data-ttu-id="83070-457">データ型</span><span class="sxs-lookup"><span data-stu-id="83070-457">Data Type</span></span>|<span data-ttu-id="83070-458">説明</span><span class="sxs-lookup"><span data-stu-id="83070-458">Description</span></span>|
|----------------|---------------|-----------------|
|`FilePath`|`win:UnicodeString`|<span data-ttu-id="83070-459">プローブしたパス。</span><span class="sxs-lookup"><span data-stu-id="83070-459">Path probed.</span></span>|
|`Source`|`win:UInt16`|<span data-ttu-id="83070-460">パスのソースが調査されています。</span><span class="sxs-lookup"><span data-stu-id="83070-460">Source of the path probed.</span></span><br/><br/><span data-ttu-id="83070-461">0x0: アプリケーションアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="83070-461">0x0:Application Assemblies.</span></span><br/><br/><span data-ttu-id="83070-462">0x1: アプリネイティブイメージパス。</span><span class="sxs-lookup"><span data-stu-id="83070-462">0x1:App native image path.</span></span><br/><br/><span data-ttu-id="83070-463">0x2: アプリのパス。</span><span class="sxs-lookup"><span data-stu-id="83070-463">0x2:App path.</span></span></br><br/><span data-ttu-id="83070-464">0x3: プラットフォームリソースルート。</span><span class="sxs-lookup"><span data-stu-id="83070-464">0x3:Platform resource roots.</span></span><br/><br/><span data-ttu-id="83070-465">0x4: サテライトサブディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="83070-465">0x4:Satellite Subdirectory.</span></span></br>|
|`Result`|`win:UInt32`|<span data-ttu-id="83070-466">プローブの HRESULT。</span><span class="sxs-lookup"><span data-stu-id="83070-466">HRESULT for the probe.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="83070-467">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="83070-467">Unique ID for the instance of CoreCLR.</span></span>|
