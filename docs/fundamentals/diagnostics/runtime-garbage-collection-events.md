---
title: ガベージコレクションランタイムイベント
description: 「.NET ガベージコレクターに固有の診断情報を収集する .NET ランタイムイベント」を参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594055"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="3e9df-103">.NET ランタイムガベージコレクションイベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="3e9df-104">これらのイベントは、ガベージ コレクションに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="3e9df-105">ガベージコレクションが実行された回数、ガベージコレクション中に解放されたメモリの量など、診断やデバッグに役立ちます。診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e9df-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="3e9df-106">GCStart_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-106">GCStart_V2 Event</span></span>

<span data-ttu-id="3e9df-107">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-108">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-108">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-109">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-110">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-111">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-111">Informational (4)</span></span>|

<span data-ttu-id="3e9df-112">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-112">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-113">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-113">Event</span></span>|<span data-ttu-id="3e9df-114">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-114">Event ID</span></span>|<span data-ttu-id="3e9df-115">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="3e9df-116">1</span><span class="sxs-lookup"><span data-stu-id="3e9df-116">1</span></span>|<span data-ttu-id="3e9df-117">ガベージ コレクションが開始されました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-117">A garbage collection has started.</span></span>|

<span data-ttu-id="3e9df-118">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-118">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-119">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-119">Field name</span></span>|<span data-ttu-id="3e9df-120">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-120">Data type</span></span>|<span data-ttu-id="3e9df-121">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="3e9df-122">*n* 回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="3e9df-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="3e9df-123">収集されるジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="3e9df-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="3e9df-124">ガベージ コレクションが発生した理由:</span><span class="sxs-lookup"><span data-stu-id="3e9df-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="3e9df-125">`0x0` -小さなオブジェクトヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="3e9df-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="3e9df-126">`0x1` 起因.</span><span class="sxs-lookup"><span data-stu-id="3e9df-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="3e9df-127">`0x2` -メモリが不足しています。</span><span class="sxs-lookup"><span data-stu-id="3e9df-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="3e9df-128">`0x3` 指定.</span><span class="sxs-lookup"><span data-stu-id="3e9df-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="3e9df-129">`0x4` -大きなオブジェクトヒープの割り当て。</span><span class="sxs-lookup"><span data-stu-id="3e9df-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="3e9df-130">`0x5` -領域が不足しています (小さなオブジェクトヒープの場合)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="3e9df-131">`0x6` -領域が不足しています (大きなオブジェクトヒープの場合)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="3e9df-132">`0x7` -強制されますが、ブロックとして強制されることはありません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="3e9df-133">`0x0` -バックグラウンドガベージコレクションの外部でブロッキングガベージコレクションが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="3e9df-134">`0x1` -バックグラウンドガベージコレクション。</span><span class="sxs-lookup"><span data-stu-id="3e9df-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="3e9df-135">`0x2` -バックグラウンドガベージコレクションの実行中に、ブロッキングガベージコレクションが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="3e9df-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3e9df-136">win:UInt16</span></span>|<span data-ttu-id="3e9df-137">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="3e9df-138">GCEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="3e9df-139">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-140">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-140">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-141">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-142">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-143">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-143">Informational (4)</span></span>|

<span data-ttu-id="3e9df-144">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-144">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-145">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-145">Event</span></span>|<span data-ttu-id="3e9df-146">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-146">Event ID</span></span>|<span data-ttu-id="3e9df-147">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="3e9df-148">2</span><span class="sxs-lookup"><span data-stu-id="3e9df-148">2</span></span>|<span data-ttu-id="3e9df-149">ガベージ コレクションが終了しました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="3e9df-150">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-150">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-151">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-151">Field name</span></span>|<span data-ttu-id="3e9df-152">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-152">Data type</span></span>|<span data-ttu-id="3e9df-153">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="3e9df-154">*n* 回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="3e9df-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="3e9df-155">収集されたジェネレーション。</span><span class="sxs-lookup"><span data-stu-id="3e9df-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="3e9df-156">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3e9df-156">win:UInt16</span></span>|<span data-ttu-id="3e9df-157">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="3e9df-158">GCHeapStats_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="3e9df-159">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-160">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-160">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-161">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-162">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-163">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-163">Informational (4)</span></span>|

<span data-ttu-id="3e9df-164">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-164">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-165">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-165">Event</span></span>|<span data-ttu-id="3e9df-166">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-166">Event ID</span></span>|<span data-ttu-id="3e9df-167">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="3e9df-168">4</span><span class="sxs-lookup"><span data-stu-id="3e9df-168">4</span></span>|<span data-ttu-id="3e9df-169">各ガベージ コレクション終了時のヒープの統計情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="3e9df-170">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-170">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-171">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-171">Field name</span></span>|<span data-ttu-id="3e9df-172">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-172">Data type</span></span>|<span data-ttu-id="3e9df-173">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="3e9df-174">ジェネレーション 0 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="3e9df-175">ジェネレーション 0 からジェネレーション 1 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="3e9df-176">ジェネレーション 1 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="3e9df-177">ジェネレーション 1 からジェネレーション 2 に移されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="3e9df-178">ジェネレーション 2 メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="3e9df-179">最後のガベージ コレクションの後にジェネレーション 2 に残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="3e9df-180">大きなオブジェクト ヒープのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="3e9df-181">最後のガベージ コレクションの後に大きなオブジェクト ヒープに残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="3e9df-182">終了準備が完了しているオブジェクトの合計サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="3e9df-183">終了準備が完了しているオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="3e9df-184">ピン止めオブジェクト (移動できないオブジェクト) の数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="3e9df-185">使用中の同期ブロックの数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="3e9df-186">使用中のガベージ コレクション ハンドルの数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-187">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="3e9df-188">固定されたオブジェクトヒープのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="3e9df-189">最後のコレクションの後に固定されたオブジェクトヒープに残ったバイト数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="3e9df-190">GCCreateSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="3e9df-191">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-192">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-192">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-193">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-194">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-195">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-195">Informational (4)</span></span>|

<span data-ttu-id="3e9df-196">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-196">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-197">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-197">Event</span></span>|<span data-ttu-id="3e9df-198">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-198">Event ID</span></span>|<span data-ttu-id="3e9df-199">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="3e9df-200">5</span><span class="sxs-lookup"><span data-stu-id="3e9df-200">5</span></span>|<span data-ttu-id="3e9df-201">新しいガベージ コレクション セグメントが作成されました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="3e9df-202">既に実行されているプロセスでトレースを有効にした場合は、このイベントが各既存セグメントについて発生します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="3e9df-203">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-203">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-204">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-204">Field name</span></span>|<span data-ttu-id="3e9df-205">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-205">Data type</span></span>|<span data-ttu-id="3e9df-206">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="3e9df-207">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="3e9df-208">セグメントのサイズ。</span><span class="sxs-lookup"><span data-stu-id="3e9df-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="3e9df-209">0x0 - 小さなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="3e9df-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="3e9df-210">0x1 - 大きなオブジェクト ヒープ。</span><span class="sxs-lookup"><span data-stu-id="3e9df-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="3e9df-211">0x2 - 読み取り専用ヒープ。</span><span class="sxs-lookup"><span data-stu-id="3e9df-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-212">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="3e9df-213">ガベージ コレクターによって割り当てられるセグメントのサイズは実装に固有であり、定期的な更新プログラムによる場合を含め、いつでも変更されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3e9df-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="3e9df-214">アプリでは、セグメント サイズを推測することや、特定のセグメント サイズに依存することを絶対に避けてください。また、セグメントの割り当てに使用可能なメモリの量を構成しようとしてもなりません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="3e9df-215">GCFreeSegment_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="3e9df-216">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-217">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-217">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-218">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-219">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-220">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-220">Informational (4)</span></span>|

<span data-ttu-id="3e9df-221">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-221">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-222">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-222">Event</span></span>|<span data-ttu-id="3e9df-223">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-223">Event ID</span></span>|<span data-ttu-id="3e9df-224">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="3e9df-225">6</span><span class="sxs-lookup"><span data-stu-id="3e9df-225">6</span></span>|<span data-ttu-id="3e9df-226">ガベージ コレクション セグメントが解放されました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="3e9df-227">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-227">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-228">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-228">Field name</span></span>|<span data-ttu-id="3e9df-229">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-229">Data type</span></span>|<span data-ttu-id="3e9df-230">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="3e9df-231">セグメントのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-232">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="3e9df-233">GCRestartEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="3e9df-234">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-235">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-235">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-236">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-237">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-238">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-238">Informational (4)</span></span>|

<span data-ttu-id="3e9df-239">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-239">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-240">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-240">Event</span></span>|<span data-ttu-id="3e9df-241">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-241">Event ID</span></span>|<span data-ttu-id="3e9df-242">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="3e9df-243">7</span><span class="sxs-lookup"><span data-stu-id="3e9df-243">7</span></span>|<span data-ttu-id="3e9df-244">共通言語ランタイムの中断からの再開が開始されました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="3e9df-245">このイベントには、イベントデータがありません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="3e9df-246">GCRestartEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="3e9df-247">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-248">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-248">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-249">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-250">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-251">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-251">Informational (4)</span></span>|

<span data-ttu-id="3e9df-252">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-252">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-253">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-253">Event</span></span>|<span data-ttu-id="3e9df-254">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-254">Event Id</span></span>|<span data-ttu-id="3e9df-255">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="3e9df-256">3</span><span class="sxs-lookup"><span data-stu-id="3e9df-256">3</span></span>|<span data-ttu-id="3e9df-257">共通言語ランタイムの中断からの再開が終了しました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="3e9df-258">このイベントには、イベントデータがありません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="3e9df-259">GCSuspendEEEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="3e9df-260">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-261">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-261">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-262">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-263">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-264">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-264">Informational (4)</span></span>|

<span data-ttu-id="3e9df-265">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-265">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-266">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-266">Event</span></span>|<span data-ttu-id="3e9df-267">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-267">Event ID</span></span>|<span data-ttu-id="3e9df-268">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="3e9df-269">8</span><span class="sxs-lookup"><span data-stu-id="3e9df-269">8</span></span>|<span data-ttu-id="3e9df-270">ガベージ コレクションのための実行エンジンの中断の終了。</span><span class="sxs-lookup"><span data-stu-id="3e9df-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="3e9df-271">このイベントには、イベントデータがありません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="3e9df-272">GCSuspendEEBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="3e9df-273">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-274">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-274">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-275">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-276">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-277">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-277">Informational (4)</span></span>|

<span data-ttu-id="3e9df-278">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-278">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-279">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-279">Event</span></span>|<span data-ttu-id="3e9df-280">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-280">Event ID</span></span>|<span data-ttu-id="3e9df-281">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="3e9df-282">8</span><span class="sxs-lookup"><span data-stu-id="3e9df-282">8</span></span>|<span data-ttu-id="3e9df-283">ガベージ コレクションのための実行エンジンの中断の開始。</span><span class="sxs-lookup"><span data-stu-id="3e9df-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="3e9df-284">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-284">Field name</span></span>|<span data-ttu-id="3e9df-285">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-285">Data type</span></span>|<span data-ttu-id="3e9df-286">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="3e9df-287">*n* 回めのガベージ コレクション。</span><span class="sxs-lookup"><span data-stu-id="3e9df-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="3e9df-288">EE の中断の理由。</span><span class="sxs-lookup"><span data-stu-id="3e9df-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="3e9df-289">`0x0`: その他を中断</span><span class="sxs-lookup"><span data-stu-id="3e9df-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="3e9df-290">`0x1`: GC を中断します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="3e9df-291">`0x2`: AppDomain のシャットダウンを中断します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="3e9df-292">`0x3`: コードピッチを中断します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="3e9df-293">`0x4`: シャットダウンを中断します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="3e9df-294">`0x5`: デバッガーを中断します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="3e9df-295">`0x6`: GC 準備のために中断します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="3e9df-296">`0x7`: デバッガースイープの中断</span><span class="sxs-lookup"><span data-stu-id="3e9df-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="3e9df-297">GCAllocationTick_V3 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="3e9df-298">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-299">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-299">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-300">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-301">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-302">詳細 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-302">Verbose (4)</span></span>|

<span data-ttu-id="3e9df-303">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-303">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-304">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-304">Event</span></span>|<span data-ttu-id="3e9df-305">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-305">Event ID</span></span>|<span data-ttu-id="3e9df-306">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="3e9df-307">10</span><span class="sxs-lookup"><span data-stu-id="3e9df-307">10</span></span>|<span data-ttu-id="3e9df-308">約 100 KB が割り当てられるたび。</span><span class="sxs-lookup"><span data-stu-id="3e9df-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="3e9df-309">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-309">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-310">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-310">Field name</span></span>|<span data-ttu-id="3e9df-311">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-311">Data type</span></span>|<span data-ttu-id="3e9df-312">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="3e9df-313">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-313">The allocation size, in bytes.</span></span> <span data-ttu-id="3e9df-314">この値は、ULONG (4,294,967,295 バイト) の長さより短い割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="3e9df-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="3e9df-315">割り当てがこれを超える場合、このフィールドには切り捨てられた値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3e9df-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="3e9df-316">非常に大きな割り当てには `AllocationAmount64` を使用します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="3e9df-317">`0x0` -小さなオブジェクトの割り当て (小さなオブジェクトヒープ内の割り当て)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="3e9df-318">`0x1` -大きなオブジェクトの割り当て (大きなオブジェクトヒープ内の割り当て)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="3e9df-319">割り当てサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="3e9df-319">The allocation size, in bytes.</span></span> <span data-ttu-id="3e9df-320">この値は非常に大きな割り当ての場合に正確です。</span><span class="sxs-lookup"><span data-stu-id="3e9df-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="3e9df-321">MethodTable のアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-321">The address of the MethodTable.</span></span> <span data-ttu-id="3e9df-322">このイベント中に複数の型のオブジェクトが割り当てられた場合、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) に対応する MethodTable のアドレスです。</span><span class="sxs-lookup"><span data-stu-id="3e9df-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="3e9df-323">割り当てられた型の名前。</span><span class="sxs-lookup"><span data-stu-id="3e9df-323">The name of the type that was allocated.</span></span> <span data-ttu-id="3e9df-324">このイベント中に複数の型のオブジェクトが割り当てられた場合は、これは最後に割り当てられたオブジェクト (100 KB のしきい値を超えたオブジェクト) の型です。</span><span class="sxs-lookup"><span data-stu-id="3e9df-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="3e9df-325">オブジェクトが割り当てられたヒープ。</span><span class="sxs-lookup"><span data-stu-id="3e9df-325">The heap where the object was allocated.</span></span> <span data-ttu-id="3e9df-326">ワークステーションのガベージ コレクションと共に実行する場合、この値は 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="3e9df-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="3e9df-327">最後に割り当てられたオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-328">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="3e9df-329">GCCreateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="3e9df-330">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-331">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-331">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-332">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-333">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-334">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-334">Informational (4)</span></span>|
|<span data-ttu-id="3e9df-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="3e9df-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="3e9df-336">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-336">Informational (4)</span></span>|

<span data-ttu-id="3e9df-337">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-337">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-338">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-338">Event</span></span>|<span data-ttu-id="3e9df-339">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-339">Event ID</span></span>|<span data-ttu-id="3e9df-340">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="3e9df-341">11</span><span class="sxs-lookup"><span data-stu-id="3e9df-341">11</span></span>|<span data-ttu-id="3e9df-342">同時実行ガベージ コレクション スレッドが作成されました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="3e9df-343">このイベントには、イベントデータがありません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="3e9df-344">GCTerminateConcurrentThread_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="3e9df-345">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-346">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-346">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-347">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-348">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-349">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-349">Informational (4)</span></span>|
|<span data-ttu-id="3e9df-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="3e9df-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="3e9df-351">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-351">Informational (4)</span></span>|

<span data-ttu-id="3e9df-352">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-352">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-353">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-353">Event</span></span>|<span data-ttu-id="3e9df-354">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-354">Event ID</span></span>|<span data-ttu-id="3e9df-355">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="3e9df-356">12</span><span class="sxs-lookup"><span data-stu-id="3e9df-356">12</span></span>|<span data-ttu-id="3e9df-357">同時実行ガベージ コレクションスレッドが終了しました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="3e9df-358">このイベントには、イベントデータがありません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="3e9df-359">GCFinalizersBegin_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="3e9df-360">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-361">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-361">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-362">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-363">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-364">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-364">Informational (4)</span></span>|

<span data-ttu-id="3e9df-365">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-365">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-366">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-366">Event</span></span>|<span data-ttu-id="3e9df-367">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-367">Event ID</span></span>|<span data-ttu-id="3e9df-368">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="3e9df-369">14</span><span class="sxs-lookup"><span data-stu-id="3e9df-369">14</span></span>|<span data-ttu-id="3e9df-370">ファイナライザーの実行の開始。</span><span class="sxs-lookup"><span data-stu-id="3e9df-370">The start of running finalizers.</span></span>|

<span data-ttu-id="3e9df-371">このイベントには、イベントデータがありません。</span><span class="sxs-lookup"><span data-stu-id="3e9df-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="3e9df-372">GCFinalizersEnd_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="3e9df-373">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-374">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-374">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-375">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-376">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-377">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-377">Informational (4)</span></span>|

<span data-ttu-id="3e9df-378">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-378">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-379">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-379">Event</span></span>|<span data-ttu-id="3e9df-380">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-380">Event ID</span></span>|<span data-ttu-id="3e9df-381">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="3e9df-382">13</span><span class="sxs-lookup"><span data-stu-id="3e9df-382">13</span></span>|<span data-ttu-id="3e9df-383">ファイナライザーの実行の終了。</span><span class="sxs-lookup"><span data-stu-id="3e9df-383">The end of running finalizers.</span></span>|

<span data-ttu-id="3e9df-384">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-384">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-385">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-385">Field name</span></span>|<span data-ttu-id="3e9df-386">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-386">Data type</span></span>|<span data-ttu-id="3e9df-387">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="3e9df-388">実行されたファイナライザーの数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="3e9df-389">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3e9df-389">win:UInt16</span></span>|<span data-ttu-id="3e9df-390">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="3e9df-391">SetGCHandle イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-391">SetGCHandle event</span></span>

<span data-ttu-id="3e9df-392">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-393">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-393">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-394">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-395">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="3e9df-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="3e9df-396">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-396">Informational (4)</span></span>|

<span data-ttu-id="3e9df-397">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-397">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-398">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-398">Event</span></span>|<span data-ttu-id="3e9df-399">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-399">Event ID</span></span>|<span data-ttu-id="3e9df-400">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="3e9df-401">30</span><span class="sxs-lookup"><span data-stu-id="3e9df-401">30</span></span>|<span data-ttu-id="3e9df-402">GC ハンドルが設定されました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="3e9df-403">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-403">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-404">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-404">Field name</span></span>|<span data-ttu-id="3e9df-405">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-405">Data type</span></span>|<span data-ttu-id="3e9df-406">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="3e9df-407">割り当てられたハンドルのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="3e9df-408">ハンドルが作成されたオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="3e9df-409">設定された GC ハンドルの型。</span><span class="sxs-lookup"><span data-stu-id="3e9df-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="3e9df-410">`0x0`:%/Short</span><span class="sxs-lookup"><span data-stu-id="3e9df-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="3e9df-411">`0x1`:% (中)</span><span class="sxs-lookup"><span data-stu-id="3e9df-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="3e9df-412">`0x2`: Strong</span><span class="sxs-lookup"><span data-stu-id="3e9df-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="3e9df-413">`0x3`: ピン留め</span><span class="sxs-lookup"><span data-stu-id="3e9df-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="3e9df-414">`0x4`: 変数</span><span class="sxs-lookup"><span data-stu-id="3e9df-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="3e9df-415">`0x5`: RefCounted</span><span class="sxs-lookup"><span data-stu-id="3e9df-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="3e9df-416">`0x6`: 依存</span><span class="sxs-lookup"><span data-stu-id="3e9df-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="3e9df-417">`0x7`: AsyncPinned</span><span class="sxs-lookup"><span data-stu-id="3e9df-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="3e9df-418">`0x8`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="3e9df-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="3e9df-419">ハンドルが作成されたオブジェクトの生成。</span><span class="sxs-lookup"><span data-stu-id="3e9df-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="3e9df-420">AppDomain ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-421">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="3e9df-422">DestroyGCHandle イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-422">DestroyGCHandle event</span></span>

<span data-ttu-id="3e9df-423">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-424">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-424">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-425">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-426">`GCHandleKeyword` 0x2</span><span class="sxs-lookup"><span data-stu-id="3e9df-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="3e9df-427">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-427">Informational (4)</span></span>|

<span data-ttu-id="3e9df-428">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-428">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-429">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-429">Event</span></span>|<span data-ttu-id="3e9df-430">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-430">Event ID</span></span>|<span data-ttu-id="3e9df-431">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="3e9df-432">31</span><span class="sxs-lookup"><span data-stu-id="3e9df-432">31</span></span>|<span data-ttu-id="3e9df-433">GC ハンドルが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="3e9df-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="3e9df-434">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-434">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-435">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-435">Field name</span></span>|<span data-ttu-id="3e9df-436">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-436">Data type</span></span>|<span data-ttu-id="3e9df-437">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="3e9df-438">破棄されたハンドルのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="3e9df-439">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3e9df-439">win:UInt16</span></span>|<span data-ttu-id="3e9df-440">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="3e9df-441">PinObjectAtGCTime イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="3e9df-442">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-443">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-443">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-444">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-445">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-446">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="3e9df-446">Verbose (5)</span></span>|

<span data-ttu-id="3e9df-447">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-447">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-448">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-448">Event</span></span>|<span data-ttu-id="3e9df-449">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-449">Event ID</span></span>|<span data-ttu-id="3e9df-450">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="3e9df-451">33</span><span class="sxs-lookup"><span data-stu-id="3e9df-451">33</span></span>|<span data-ttu-id="3e9df-452">オブジェクトは GC 中にピン留めされました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="3e9df-453">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-453">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-454">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-454">Field name</span></span>|<span data-ttu-id="3e9df-455">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-455">Data type</span></span>|<span data-ttu-id="3e9df-456">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="3e9df-457">ハンドルのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="3e9df-458">固定されたオブジェクトのアドレス。</span><span class="sxs-lookup"><span data-stu-id="3e9df-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="3e9df-459">ピン留めされたオブジェクトのサイズ。</span><span class="sxs-lookup"><span data-stu-id="3e9df-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="3e9df-460">固定されたオブジェクトの型の名前。</span><span class="sxs-lookup"><span data-stu-id="3e9df-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-461">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="3e9df-462">GCTriggered イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-462">GCTriggered event</span></span>

<span data-ttu-id="3e9df-463">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-464">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-464">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-465">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-466">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-467">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="3e9df-467">Verbose (5)</span></span>|

<span data-ttu-id="3e9df-468">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-468">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-469">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-469">Event</span></span>|<span data-ttu-id="3e9df-470">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-470">Event ID</span></span>|<span data-ttu-id="3e9df-471">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="3e9df-472">33</span><span class="sxs-lookup"><span data-stu-id="3e9df-472">33</span></span>|<span data-ttu-id="3e9df-473">GC がトリガーされました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-473">A GC has been triggered.</span></span>|

<span data-ttu-id="3e9df-474">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-474">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-475">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-475">Field name</span></span>|<span data-ttu-id="3e9df-476">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-476">Data type</span></span>|<span data-ttu-id="3e9df-477">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="3e9df-478">GC がトリガーされた理由。</span><span class="sxs-lookup"><span data-stu-id="3e9df-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="3e9df-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="3e9df-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="3e9df-480">`0x1`: 誘発</span><span class="sxs-lookup"><span data-stu-id="3e9df-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="3e9df-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="3e9df-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="3e9df-482">`0x3`: 空</span><span class="sxs-lookup"><span data-stu-id="3e9df-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="3e9df-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="3e9df-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="3e9df-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="3e9df-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="3e9df-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="3e9df-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="3e9df-486">`0x7`:InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="3e9df-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="3e9df-487">`0x8`: ストレス</span><span class="sxs-lookup"><span data-stu-id="3e9df-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="3e9df-488">`0x9`: InducedLowMemory</span><span class="sxs-lookup"><span data-stu-id="3e9df-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-489">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="3e9df-490">IncreaseMemoryPressure イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="3e9df-491">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-492">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-492">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-493">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-494">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-495">情報 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-495">Information (4)</span></span>|

<span data-ttu-id="3e9df-496">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-496">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-497">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-497">Event</span></span>|<span data-ttu-id="3e9df-498">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-498">Event ID</span></span>|<span data-ttu-id="3e9df-499">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="3e9df-500">200</span><span class="sxs-lookup"><span data-stu-id="3e9df-500">200</span></span>|<span data-ttu-id="3e9df-501">メモリ不足が増加しました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="3e9df-502">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-502">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-503">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-503">Field Name</span></span>|<span data-ttu-id="3e9df-504">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-504">Data type</span></span>|<span data-ttu-id="3e9df-505">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="3e9df-506">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3e9df-506">win:UInt16</span></span>|<span data-ttu-id="3e9df-507">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="3e9df-508">DecreaseMemoryPressure イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="3e9df-509">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-510">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-510">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-511">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-512">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-513">情報 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-513">Information (4)</span></span>|

<span data-ttu-id="3e9df-514">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-514">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-515">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-515">Event</span></span>|<span data-ttu-id="3e9df-516">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-516">Event ID</span></span>|<span data-ttu-id="3e9df-517">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="3e9df-518">201</span><span class="sxs-lookup"><span data-stu-id="3e9df-518">201</span></span>|<span data-ttu-id="3e9df-519">メモリの負荷が減少しました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="3e9df-520">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-520">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-521">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-521">Field Name</span></span>|<span data-ttu-id="3e9df-522">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-522">Data type</span></span>|<span data-ttu-id="3e9df-523">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="3e9df-524">解放されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-525">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="3e9df-526">GCMarkWithType イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-526">GCMarkWithType event</span></span>

<span data-ttu-id="3e9df-527">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-528">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-528">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-529">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-530">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-531">情報 (4)</span><span class="sxs-lookup"><span data-stu-id="3e9df-531">Information (4)</span></span>|

<span data-ttu-id="3e9df-532">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-532">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-533">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-533">Event</span></span>|<span data-ttu-id="3e9df-534">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-534">Event ID</span></span>|<span data-ttu-id="3e9df-535">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="3e9df-536">202</span><span class="sxs-lookup"><span data-stu-id="3e9df-536">202</span></span>|<span data-ttu-id="3e9df-537">Gc マークフェーズ中に GC ルートがマークされました。</span><span class="sxs-lookup"><span data-stu-id="3e9df-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="3e9df-538">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-538">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-539">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-539">Field Name</span></span>|<span data-ttu-id="3e9df-540">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-540">Data type</span></span>|<span data-ttu-id="3e9df-541">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="3e9df-542">ヒープ番号。</span><span class="sxs-lookup"><span data-stu-id="3e9df-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="3e9df-543">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3e9df-543">win:UInt16</span></span>|<span data-ttu-id="3e9df-544">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="3e9df-545">GC ルート型。</span><span class="sxs-lookup"><span data-stu-id="3e9df-545">The GC root type.</span></span><br/><br/><span data-ttu-id="3e9df-546">`0x0`: スタック</span><span class="sxs-lookup"><span data-stu-id="3e9df-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="3e9df-547">`0x1`: ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="3e9df-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="3e9df-548">`0x2`: ハンドル</span><span class="sxs-lookup"><span data-stu-id="3e9df-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="3e9df-549">`0x3`: 古い</span><span class="sxs-lookup"><span data-stu-id="3e9df-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="3e9df-550">`0x4`: SizedRef</span><span class="sxs-lookup"><span data-stu-id="3e9df-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="3e9df-551">`0x5`: オーバーフロー</span><span class="sxs-lookup"><span data-stu-id="3e9df-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="3e9df-552">マークされたバイト数。</span><span class="sxs-lookup"><span data-stu-id="3e9df-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="3e9df-553">GCJoin_V2 イベント</span><span class="sxs-lookup"><span data-stu-id="3e9df-553">GCJoin_V2 event</span></span>

<span data-ttu-id="3e9df-554">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="3e9df-555">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="3e9df-555">Keyword for raising the event</span></span>|<span data-ttu-id="3e9df-556">Level</span><span class="sxs-lookup"><span data-stu-id="3e9df-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="3e9df-557">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="3e9df-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="3e9df-558">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="3e9df-558">Verbose (5)</span></span>|

<span data-ttu-id="3e9df-559">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-559">The following table shows the event information:</span></span>

|<span data-ttu-id="3e9df-560">event</span><span class="sxs-lookup"><span data-stu-id="3e9df-560">Event</span></span>|<span data-ttu-id="3e9df-561">イベント ID</span><span class="sxs-lookup"><span data-stu-id="3e9df-561">Event ID</span></span>|<span data-ttu-id="3e9df-562">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="3e9df-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="3e9df-563">203</span><span class="sxs-lookup"><span data-stu-id="3e9df-563">203</span></span>|<span data-ttu-id="3e9df-564">参加している GC スレッド。</span><span class="sxs-lookup"><span data-stu-id="3e9df-564">A GC thread joined.</span></span>|

<span data-ttu-id="3e9df-565">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="3e9df-565">The following table shows the event data:</span></span>

|<span data-ttu-id="3e9df-566">フィールド名</span><span class="sxs-lookup"><span data-stu-id="3e9df-566">Field name</span></span>|<span data-ttu-id="3e9df-567">データ型</span><span class="sxs-lookup"><span data-stu-id="3e9df-567">Data type</span></span>|<span data-ttu-id="3e9df-568">説明</span><span class="sxs-lookup"><span data-stu-id="3e9df-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="3e9df-569">ヒープ番号</span><span class="sxs-lookup"><span data-stu-id="3e9df-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="3e9df-570">このイベントが結合の開始時に発生したか、または結合の終了時に発生したかを示します (結合の `0x0` 開始、 `0x1` 結合の終了)</span><span class="sxs-lookup"><span data-stu-id="3e9df-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="3e9df-571">結合の種類。</span><span class="sxs-lookup"><span data-stu-id="3e9df-571">The join type.</span></span> <br/><br/><span data-ttu-id="3e9df-572">`0x0`: 最後の結合</span><span class="sxs-lookup"><span data-stu-id="3e9df-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="3e9df-573">`0x1`: Join</span><span class="sxs-lookup"><span data-stu-id="3e9df-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="3e9df-574">`0x2`: 再起動</span><span class="sxs-lookup"><span data-stu-id="3e9df-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="3e9df-575">`0x3`: 最初の逆結合</span><span class="sxs-lookup"><span data-stu-id="3e9df-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="3e9df-576">`0x4`: 逆結合</span><span class="sxs-lookup"><span data-stu-id="3e9df-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="3e9df-577">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="3e9df-577">Unique ID for the instance of CoreCLR.</span></span>|
