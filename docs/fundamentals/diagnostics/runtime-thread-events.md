---
title: ThreadPool ランタイムイベント
description: 「.Net Core のスレッドプールに関する診断情報を収集する .NET ランタイムスレッドプールイベント」を参照してください。 スレッドプールイベントは、ワーカースレッドプールイベントまたは i/o スレッドプールイベントです。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- ThreadPool events (CoreCLR)
- ETW, thread pool events (CoreCLR)
ms.openlocfilehash: cdd6041c5842d4922c60e33daf6db366f7d35327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96594121"
---
# <a name="net-runtime-thread-pool-events"></a><span data-ttu-id="a8d94-104">.NET ランタイムスレッドプールイベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-104">.NET runtime thread pool events</span></span>

<span data-ttu-id="a8d94-105">これらのイベントは、threadpool 内のワーカースレッドと i/o スレッドに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-105">These events collect information about worker and I/O threads in the threadpool.</span></span> <span data-ttu-id="a8d94-106">診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8d94-106">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="iothreadcreate_v1-event"></a><span data-ttu-id="a8d94-107">IOThreadCreate_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-107">IOThreadCreate_V1 event</span></span>

 <span data-ttu-id="a8d94-108">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-108">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-109">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-109">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-110">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-110">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-111">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-111">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-112">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-112">Informational (4)</span></span>|

 <span data-ttu-id="a8d94-113">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-113">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-114">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-114">Event</span></span>|<span data-ttu-id="a8d94-115">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-115">Event ID</span></span>|<span data-ttu-id="a8d94-116">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="a8d94-116">Raised when</span></span>|
|-----------------------------------|-----------|
|`IOThreadCreate_V1`|<span data-ttu-id="a8d94-117">44</span><span class="sxs-lookup"><span data-stu-id="a8d94-117">44</span></span>|<span data-ttu-id="a8d94-118">I/O スレッドがスレッド プールに作成された。</span><span class="sxs-lookup"><span data-stu-id="a8d94-118">An I/O thread is created in the thread pool.</span></span>|

 <span data-ttu-id="a8d94-119">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-119">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-120">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-120">Field name</span></span>|<span data-ttu-id="a8d94-121">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-121">Data type</span></span>|<span data-ttu-id="a8d94-122">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-122">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="a8d94-123">新しく作成されたスレッドを含む、I/O のスレッドの数です。</span><span class="sxs-lookup"><span data-stu-id="a8d94-123">Number of I/O threads, including the newly created thread.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="a8d94-124">提供終了になったワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-124">Number of retired worker threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-125">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-125">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadterminate_v1-event"></a><span data-ttu-id="a8d94-126">IOThreadTerminate_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-126">IOThreadTerminate_V1 event</span></span>

 <span data-ttu-id="a8d94-127">次の表は、キーワードとレベルを示しています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-127">The following table shows the keyword and level</span></span>

|<span data-ttu-id="a8d94-128">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-128">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-129">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-129">Level</span></span>
|-----------------------------------|-----------
|<span data-ttu-id="a8d94-130">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-130">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-131">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-131">Informational (4)</span></span>

 <span data-ttu-id="a8d94-132">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-132">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-133">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-133">Event</span></span>|<span data-ttu-id="a8d94-134">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-134">Event ID</span></span>|<span data-ttu-id="a8d94-135">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="a8d94-135">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadTerminate`|<span data-ttu-id="a8d94-136">45</span><span class="sxs-lookup"><span data-stu-id="a8d94-136">45</span></span>|<span data-ttu-id="a8d94-137">スレッドプールで i/o スレッドが終了します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-137">An I/O thread is terminated in the thread pool.</span></span>|

 <span data-ttu-id="a8d94-138">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-138">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-139">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-139">Field name</span></span>|<span data-ttu-id="a8d94-140">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-140">Data type</span></span>|<span data-ttu-id="a8d94-141">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-141">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="a8d94-142">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-142">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="a8d94-143">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-143">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-144">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadretire_v1-event"></a><span data-ttu-id="a8d94-145">IOThreadRetire_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-145">IOThreadRetire_V1 event</span></span>

 <span data-ttu-id="a8d94-146">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-146">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-147">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-147">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-148">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-148">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-149">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-149">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-150">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-150">Informational (4)</span></span>|

 <span data-ttu-id="a8d94-151">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-151">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-152">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-152">Event</span></span>|<span data-ttu-id="a8d94-153">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-153">Event ID</span></span>|<span data-ttu-id="a8d94-154">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="a8d94-154">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadRetire_V1`|<span data-ttu-id="a8d94-155">46</span><span class="sxs-lookup"><span data-stu-id="a8d94-155">46</span></span>|<span data-ttu-id="a8d94-156">I/O スレッドが、提供終了の候補になる。</span><span class="sxs-lookup"><span data-stu-id="a8d94-156">An I/O thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="a8d94-157">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-157">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-158">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-158">Field name</span></span>|<span data-ttu-id="a8d94-159">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-159">Data type</span></span>|<span data-ttu-id="a8d94-160">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-160">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="a8d94-161">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-161">Number of I/O threads remaining in the thread pool.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="a8d94-162">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-162">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-163">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="iothreadunretire_v1-event"></a><span data-ttu-id="a8d94-164">IOThreadUnretire_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-164">IOThreadUnretire_V1 event</span></span>

 <span data-ttu-id="a8d94-165">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-165">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-166">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-166">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-167">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-168">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-168">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-169">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-169">Informational (4)</span></span>|

 <span data-ttu-id="a8d94-170">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-170">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-171">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-171">Event</span></span>|<span data-ttu-id="a8d94-172">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-172">Event ID</span></span>|<span data-ttu-id="a8d94-173">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="a8d94-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`IOThreadUnretire_V1`|<span data-ttu-id="a8d94-174">47</span><span class="sxs-lookup"><span data-stu-id="a8d94-174">47</span></span>|<span data-ttu-id="a8d94-175">スレッドが提供終了の候補になってから待機期間内に I/O が到着したため I/O スレッドが提供終了解除された。</span><span class="sxs-lookup"><span data-stu-id="a8d94-175">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|

 <span data-ttu-id="a8d94-176">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-176">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-177">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-177">Field name</span></span>|<span data-ttu-id="a8d94-178">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-178">Data type</span></span>|<span data-ttu-id="a8d94-179">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-179">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt64`|<span data-ttu-id="a8d94-180">これを含む、スレッド プール内の I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-180">Number of I/O threads in the thread pool, including this one.</span></span>|
|`NumRetired`|`win:UInt64`|<span data-ttu-id="a8d94-181">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-181">Number of retired I/O threads.</span></span>|
|`ClrInstanceID`|`Win:UInt16`|<span data-ttu-id="a8d94-182">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-182">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstart-event"></a><span data-ttu-id="a8d94-183">ThreadPoolWorkerThreadStart イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-183">ThreadPoolWorkerThreadStart event</span></span>

|<span data-ttu-id="a8d94-184">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-184">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-185">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-185">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="a8d94-186">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-186">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-187">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-187">Informational (4)</span></span>|

|<span data-ttu-id="a8d94-188">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-188">Event</span></span>|<span data-ttu-id="a8d94-189">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-189">Event ID</span></span>|<span data-ttu-id="a8d94-190">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-190">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="a8d94-191">50</span><span class="sxs-lookup"><span data-stu-id="a8d94-191">50</span></span>|<span data-ttu-id="a8d94-192">ワーカー スレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="a8d94-192">A worker thread is created.</span></span>|

|<span data-ttu-id="a8d94-193">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-193">Field name</span></span>|<span data-ttu-id="a8d94-194">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-194">Data type</span></span>|<span data-ttu-id="a8d94-195">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-195">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-196">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-196">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-197">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-197">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-198">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-198">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadstop-event"></a><span data-ttu-id="a8d94-199">ThreadPoolWorkerThreadStop イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-199">ThreadPoolWorkerThreadStop event</span></span>

|<span data-ttu-id="a8d94-200">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-200">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-201">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-201">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="a8d94-202">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-202">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-203">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-203">Informational (4)</span></span>|

|<span data-ttu-id="a8d94-204">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-204">Event</span></span>|<span data-ttu-id="a8d94-205">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-205">Event ID</span></span>|<span data-ttu-id="a8d94-206">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-206">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="a8d94-207">51</span><span class="sxs-lookup"><span data-stu-id="a8d94-207">51</span></span>|<span data-ttu-id="a8d94-208">ワーカー スレッドが停止された。</span><span class="sxs-lookup"><span data-stu-id="a8d94-208">A worker thread is stopped.</span></span>|

|<span data-ttu-id="a8d94-209">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-209">Field name</span></span>|<span data-ttu-id="a8d94-210">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-210">Data type</span></span>|<span data-ttu-id="a8d94-211">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-211">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-212">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-212">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-213">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-213">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-214">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-214">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadwait-event"></a><span data-ttu-id="a8d94-215">ThreadPoolWorkerThreadWait イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-215">ThreadPoolWorkerThreadWait event</span></span>

|<span data-ttu-id="a8d94-216">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-216">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-217">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-217">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="a8d94-218">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-218">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-219">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-219">Informational (4)</span></span>|

|<span data-ttu-id="a8d94-220">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-220">Event</span></span>|<span data-ttu-id="a8d94-221">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-221">Event ID</span></span>|<span data-ttu-id="a8d94-222">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-222">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadWait`|<span data-ttu-id="a8d94-223">57</span><span class="sxs-lookup"><span data-stu-id="a8d94-223">57</span></span>|<span data-ttu-id="a8d94-224">ワーカースレッドが作業の待機を開始します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-224">A worker thread starts waiting for work.</span></span>|

|<span data-ttu-id="a8d94-225">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-225">Field name</span></span>|<span data-ttu-id="a8d94-226">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-226">Data type</span></span>|<span data-ttu-id="a8d94-227">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-227">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-228">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-228">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-229">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-229">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-230">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-230">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstart-event"></a><span data-ttu-id="a8d94-231">ThreadPoolWorkerThreadRetirementStart イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-231">ThreadPoolWorkerThreadRetirementStart event</span></span>

|<span data-ttu-id="a8d94-232">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-232">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-233">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-233">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="a8d94-234">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-234">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-235">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-235">Informational (4)</span></span>|

|<span data-ttu-id="a8d94-236">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-236">Event</span></span>|<span data-ttu-id="a8d94-237">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-237">Event ID</span></span>|<span data-ttu-id="a8d94-238">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-238">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="a8d94-239">52</span><span class="sxs-lookup"><span data-stu-id="a8d94-239">52</span></span>|<span data-ttu-id="a8d94-240">ワーカー スレッドが無効にされた。</span><span class="sxs-lookup"><span data-stu-id="a8d94-240">A worker thread retires.</span></span>|

|<span data-ttu-id="a8d94-241">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-241">Field name</span></span>|<span data-ttu-id="a8d94-242">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-242">Data type</span></span>|<span data-ttu-id="a8d94-243">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-243">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-244">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-244">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-245">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-245">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-246">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadretirementstop-event"></a><span data-ttu-id="a8d94-247">ThreadPoolWorkerThreadRetirementStop イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-247">ThreadPoolWorkerThreadRetirementStop event</span></span>

|<span data-ttu-id="a8d94-248">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-248">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-249">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-249">Level</span></span>|
|-----------------------------------|-----------|-----------|
|<span data-ttu-id="a8d94-250">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-250">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-251">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-251">Informational (4)</span></span>|

|<span data-ttu-id="a8d94-252">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-252">Event</span></span>|<span data-ttu-id="a8d94-253">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-253">Event ID</span></span>|<span data-ttu-id="a8d94-254">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-254">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="a8d94-255">53</span><span class="sxs-lookup"><span data-stu-id="a8d94-255">53</span></span>|<span data-ttu-id="a8d94-256">提供終了になったワーカー スレッドが再びアクティブになった。</span><span class="sxs-lookup"><span data-stu-id="a8d94-256">A retired worker thread becomes active again.</span></span>|

|<span data-ttu-id="a8d94-257">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-257">Field name</span></span>|<span data-ttu-id="a8d94-258">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-258">Data type</span></span>|<span data-ttu-id="a8d94-259">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-259">Description</span></span>|
|----------------|---------------|-----------------|
|`ActiveWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-260">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-260">Number of worker threads available to process work, including those that are already processing work.</span></span>|
|`RetiredWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-261">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-261">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-262">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-262">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentsample-event"></a><span data-ttu-id="a8d94-263">ThreadPoolWorkerThreadAdjustmentSample イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-263">ThreadPoolWorkerThreadAdjustmentSample event</span></span>

 <span data-ttu-id="a8d94-264">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-264">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-265">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-265">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-266">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-266">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-267">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-267">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-268">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-268">Informational (4)</span></span>|

 <span data-ttu-id="a8d94-269">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-269">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-270">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-270">Event</span></span>|<span data-ttu-id="a8d94-271">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-271">Event ID</span></span>|<span data-ttu-id="a8d94-272">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-272">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="a8d94-273">54</span><span class="sxs-lookup"><span data-stu-id="a8d94-273">54</span></span>|<span data-ttu-id="a8d94-274">1 つのサンプルの情報のコレクションを参照します。つまり、特定のコンカレンシー レベルの特定の時刻におけるスループットの測定値です。</span><span class="sxs-lookup"><span data-stu-id="a8d94-274">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|

 <span data-ttu-id="a8d94-275">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-275">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-276">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-276">Field name</span></span>|<span data-ttu-id="a8d94-277">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-277">Data type</span></span>|<span data-ttu-id="a8d94-278">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-278">Description</span></span>|
|----------------|---------------|-----------------|
|`Throughput`|`win:Double`|<span data-ttu-id="a8d94-279">時間の単位あたりの入力候補の数です。</span><span class="sxs-lookup"><span data-stu-id="a8d94-279">Number of completions per unit of time.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-280">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-280">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentadjustment-event"></a><span data-ttu-id="a8d94-281">ThreadPoolWorkerThreadAdjustmentAdjustment イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-281">ThreadPoolWorkerThreadAdjustmentAdjustment event</span></span>

 <span data-ttu-id="a8d94-282">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-282">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-283">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-283">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-284">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-284">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-285">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-285">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-286">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-286">Informational (4)</span></span>|

 <span data-ttu-id="a8d94-287">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-287">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-288">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-288">Event</span></span>|<span data-ttu-id="a8d94-289">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-289">Event ID</span></span>|<span data-ttu-id="a8d94-290">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-290">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="a8d94-291">55</span><span class="sxs-lookup"><span data-stu-id="a8d94-291">55</span></span>|<span data-ttu-id="a8d94-292">スレッドの挿入 (山登り法) アルゴリズムが、コンカレンシー レベルに変更があったと判断した場合に、コントロールの変更を記録します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-292">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|

 <span data-ttu-id="a8d94-293">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-293">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-294">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-294">Field name</span></span>|<span data-ttu-id="a8d94-295">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-295">Data type</span></span>|<span data-ttu-id="a8d94-296">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-296">Description</span></span>|
|----------------|---------------|-----------------|
|`AverageThroughput`|`win:Double`|<span data-ttu-id="a8d94-297">計測のサンプルの平均のスループット。</span><span class="sxs-lookup"><span data-stu-id="a8d94-297">Average throughput of a sample of measurements.</span></span>|
|`NewWorkerThreadCount`|`win:UInt32`|<span data-ttu-id="a8d94-298">新しいアクティブなワーカー スレッド数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-298">New number of active worker threads.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="a8d94-299">調整の理由。</span><span class="sxs-lookup"><span data-stu-id="a8d94-299">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="a8d94-300">`0x0` ウォームアップ.</span><span class="sxs-lookup"><span data-stu-id="a8d94-300">`0x0` - Warmup.</span></span><br /><br /> <span data-ttu-id="a8d94-301">`0x1` 初期化.</span><span class="sxs-lookup"><span data-stu-id="a8d94-301">`0x1` - Initializing.</span></span><br /><br /> <span data-ttu-id="a8d94-302">`0x2` -ランダムな移動。</span><span class="sxs-lookup"><span data-stu-id="a8d94-302">`0x2` - Random move.</span></span><br /><br /> <span data-ttu-id="a8d94-303">`0x3` -上昇移動。</span><span class="sxs-lookup"><span data-stu-id="a8d94-303">`0x3` - Climbing move.</span></span><br /><br /> <span data-ttu-id="a8d94-304">`0x4` -ポイントを変更します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-304">`0x4` - Change point.</span></span><br /><br /> <span data-ttu-id="a8d94-305">`0x5` 固定.</span><span class="sxs-lookup"><span data-stu-id="a8d94-305">`0x5` - Stabilizing.</span></span><br /><br /> <span data-ttu-id="a8d94-306">`0x6` 不足.</span><span class="sxs-lookup"><span data-stu-id="a8d94-306">`0x6` - Starvation.</span></span><br /><br /> <span data-ttu-id="a8d94-307">`0x7` -スレッドがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="a8d94-307">`0x7` - Thread timed out.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-308">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-308">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolworkerthreadadjustmentstats-event"></a><span data-ttu-id="a8d94-309">ThreadPoolWorkerThreadAdjustmentStats イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-309">ThreadPoolWorkerThreadAdjustmentStats event</span></span>

 <span data-ttu-id="a8d94-310">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-310">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-311">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-311">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-312">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-312">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-313">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-313">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-314">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a8d94-314">Verbose (5)</span></span>

 <span data-ttu-id="a8d94-315">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-315">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-316">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-316">Event</span></span>|<span data-ttu-id="a8d94-317">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-317">Event ID</span></span>|<span data-ttu-id="a8d94-318">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-318">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="a8d94-319">56</span><span class="sxs-lookup"><span data-stu-id="a8d94-319">56</span></span>|<span data-ttu-id="a8d94-320">スレッド プールに関するデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-320">Gathers data on the thread pool.</span></span>|

 <span data-ttu-id="a8d94-321">次の表に、イベントデータを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-321">The following table shows the event data</span></span>

|<span data-ttu-id="a8d94-322">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-322">Field name</span></span>|<span data-ttu-id="a8d94-323">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-323">Data type</span></span>|<span data-ttu-id="a8d94-324">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-324">Description</span></span>|
|----------------|---------------|-----------------|
|`Duration`|`win:Double`|<span data-ttu-id="a8d94-325">これらの統計情報が収集される時間数 (秒)。</span><span class="sxs-lookup"><span data-stu-id="a8d94-325">Amount of time, in seconds, during which these statistics were collected.</span></span>|
|`Throughput`|`win:Double`|<span data-ttu-id="a8d94-326">この間隔中の 1 秒あたりの入力候補の平均数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-326">Average number of completions per second during this interval.</span></span>|
|`ThreadWave`|`win:Double`|<span data-ttu-id="a8d94-327">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-327">Reserved for internal use.</span></span>|
|`ThroughputWave`|`win:Double`|<span data-ttu-id="a8d94-328">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-328">Reserved for internal use.</span></span>|
|`ThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="a8d94-329">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-329">Reserved for internal use.</span></span>|
|`AverageThroughputErrorEstimate`|`win:Double`|<span data-ttu-id="a8d94-330">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-330">Reserved for internal use.</span></span>|
|`ThroughputRatio`|`win:Double`|<span data-ttu-id="a8d94-331">この間隔中にアクティブなワーカー スレッドの数の変動によって引き起こされる、スループットの相対的な向上。</span><span class="sxs-lookup"><span data-stu-id="a8d94-331">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|
|`Confidence`|`win:Double`|<span data-ttu-id="a8d94-332">ThroughputRatio フィールドの有効性の測定結果。</span><span class="sxs-lookup"><span data-stu-id="a8d94-332">A measure of the validity of the ThroughputRatio field.</span></span>|
|`NewcontrolSetting`|`win:Double`|<span data-ttu-id="a8d94-333">アクティブなスレッド数の将来のバリエーションのベースラインとして使用するアクティブなワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="a8d94-333">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|
|`NewThreadWaveMagnitude`|`win:UInt16`|<span data-ttu-id="a8d94-334">アクティブなスレッド数の、将来のバリエーションの大きさを指定します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-334">The magnitude of future variations in active thread count.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-335">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-335">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="threadpoolenqueue-event"></a><span data-ttu-id="a8d94-336">ThreadPoolEnqueue キューイベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-336">ThreadPoolEnqueue event</span></span>

 <span data-ttu-id="a8d94-337">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-337">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-338">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-338">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-339">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-339">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-340">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-340">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-341">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a8d94-341">Verbose (5)</span></span>

 <span data-ttu-id="a8d94-342">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-342">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-343">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-343">Event</span></span>|<span data-ttu-id="a8d94-344">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-344">Event ID</span></span>|<span data-ttu-id="a8d94-345">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-345">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolEnqueue`|<span data-ttu-id="a8d94-346">61</span><span class="sxs-lookup"><span data-stu-id="a8d94-346">61</span></span>|<span data-ttu-id="a8d94-347">作業項目がスレッドプールキューにエンキューされました。</span><span class="sxs-lookup"><span data-stu-id="a8d94-347">A work item was enqueued in the thread pool queue.</span></span>|

 <span data-ttu-id="a8d94-348">次の表に、イベントデータを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-348">The following table shows the event data</span></span>

|<span data-ttu-id="a8d94-349">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-349">Field name</span></span>|<span data-ttu-id="a8d94-350">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-350">Data type</span></span>|<span data-ttu-id="a8d94-351">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-351">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="a8d94-352">作業要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a8d94-352">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-353">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-353">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooldequeue-event"></a><span data-ttu-id="a8d94-354">ThreadPoolDequeue イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-354">ThreadPoolDequeue event</span></span>

 <span data-ttu-id="a8d94-355">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-355">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-356">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-356">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-357">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-357">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-358">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-358">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-359">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a8d94-359">Verbose (5)</span></span>

 <span data-ttu-id="a8d94-360">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-360">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-361">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-361">Event</span></span>|<span data-ttu-id="a8d94-362">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-362">Event ID</span></span>|<span data-ttu-id="a8d94-363">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-363">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolDequeue`|<span data-ttu-id="a8d94-364">62</span><span class="sxs-lookup"><span data-stu-id="a8d94-364">62</span></span>|<span data-ttu-id="a8d94-365">作業項目がスレッドプールキューからデキューされました。</span><span class="sxs-lookup"><span data-stu-id="a8d94-365">A work item was dequeued from the thread pool queue.</span></span>|

 <span data-ttu-id="a8d94-366">次の表に、イベントデータを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-366">The following table shows the event data</span></span>

|<span data-ttu-id="a8d94-367">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-367">Field name</span></span>|<span data-ttu-id="a8d94-368">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-368">Data type</span></span>|<span data-ttu-id="a8d94-369">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-369">Description</span></span>|
|----------------|---------------|-----------------|
|`WorkID`|`win:Pointer`|<span data-ttu-id="a8d94-370">作業要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a8d94-370">Pointer to the work request.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-371">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-371">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpoolioenqueue-event"></a><span data-ttu-id="a8d94-372">ThreadPoolIOEnqueue キューイベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-372">ThreadPoolIOEnqueue event</span></span>

 <span data-ttu-id="a8d94-373">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-373">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-374">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-374">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-375">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-376">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-376">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-377">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a8d94-377">Verbose (5)</span></span>

 <span data-ttu-id="a8d94-378">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-378">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-379">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-379">Event</span></span>|<span data-ttu-id="a8d94-380">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-380">Event ID</span></span>|<span data-ttu-id="a8d94-381">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-381">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOEnqueue`|<span data-ttu-id="a8d94-382">63</span><span class="sxs-lookup"><span data-stu-id="a8d94-382">63</span></span>|<span data-ttu-id="a8d94-383">スレッドは、非同期 IO 完了後に IO 完了通知をエンキューします。</span><span class="sxs-lookup"><span data-stu-id="a8d94-383">A thread enqueues an IO completion notification after an async IO completion occurs.</span></span>|

 <span data-ttu-id="a8d94-384">次の表に、イベントデータを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-384">The following table shows the event data</span></span>

|<span data-ttu-id="a8d94-385">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-385">Field name</span></span>|<span data-ttu-id="a8d94-386">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-386">Data type</span></span>|<span data-ttu-id="a8d94-387">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-387">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="a8d94-388">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-388">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="a8d94-389">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-389">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="a8d94-390">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-390">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-391">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-391">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliodequeue-event"></a><span data-ttu-id="a8d94-392">ThreadPoolIODequeue イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-392">ThreadPoolIODequeue event</span></span>

 <span data-ttu-id="a8d94-393">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-393">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-394">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-394">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-395">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-395">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-396">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-396">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-397">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a8d94-397">Verbose (5)</span></span>

 <span data-ttu-id="a8d94-398">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-398">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-399">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-399">Event</span></span>|<span data-ttu-id="a8d94-400">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-400">Event ID</span></span>|<span data-ttu-id="a8d94-401">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-401">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIODequeue`|<span data-ttu-id="a8d94-402">64</span><span class="sxs-lookup"><span data-stu-id="a8d94-402">64</span></span>|<span data-ttu-id="a8d94-403">IO 完了通知をデキューするスレッド。</span><span class="sxs-lookup"><span data-stu-id="a8d94-403">A thread dequeues the IO completion notification.</span></span>|

 <span data-ttu-id="a8d94-404">次の表に、イベントデータを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-404">The following table shows the event data</span></span>

|<span data-ttu-id="a8d94-405">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-405">Field name</span></span>|<span data-ttu-id="a8d94-406">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-406">Data type</span></span>|<span data-ttu-id="a8d94-407">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-407">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="a8d94-408">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-408">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="a8d94-409">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-409">Reserved for internal use.</span></span>|
|`MultiDequeues`|`win:Boolean`|<span data-ttu-id="a8d94-410">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-410">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-411">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-411">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadpooliopack-event"></a><span data-ttu-id="a8d94-412">ThreadPoolIOPack イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-412">ThreadPoolIOPack event</span></span>

 <span data-ttu-id="a8d94-413">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-413">The following table shows the keyword and level.</span></span>

|<span data-ttu-id="a8d94-414">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-414">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-415">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-415">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-416">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-416">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-417">詳細 (5)</span><span class="sxs-lookup"><span data-stu-id="a8d94-417">Verbose (5)</span></span>|

 <span data-ttu-id="a8d94-418">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-418">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-419">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-419">Event</span></span>|<span data-ttu-id="a8d94-420">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-420">Event ID</span></span>|<span data-ttu-id="a8d94-421">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-421">Description</span></span>|
|-----------|--------------|-----------------|
|`ThreadPoolIOPack`|<span data-ttu-id="a8d94-422">65</span><span class="sxs-lookup"><span data-stu-id="a8d94-422">65</span></span>|<span data-ttu-id="a8d94-423">ThreadPool のオーバーラップ IO パックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a8d94-423">ThreadPool overlapped IO pack is called.</span></span>|

 <span data-ttu-id="a8d94-424">次の表に、イベントデータを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-424">The following table shows the event data</span></span>

|<span data-ttu-id="a8d94-425">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-425">Field name</span></span>|<span data-ttu-id="a8d94-426">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-426">Data type</span></span>|<span data-ttu-id="a8d94-427">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-427">Description</span></span>|
|----------------|---------------|-----------------|
|`NativeOverlapped`|`win:Pointer`|<span data-ttu-id="a8d94-428">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-428">Reserved for internal use.</span></span>|
|`Overlapped`|`win:Pointer`|<span data-ttu-id="a8d94-429">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-429">Reserved for internal use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-430">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-430">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadcreating-event"></a><span data-ttu-id="a8d94-431">ThreadCreating イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-431">ThreadCreating event</span></span>

 <span data-ttu-id="a8d94-432">次の表は、キーワードとレベルを示しています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-432">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="a8d94-433">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-433">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-434">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-435">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-435">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-436">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-436">Informational (4)</span></span>|

 <span data-ttu-id="a8d94-437">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-437">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-438">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-438">Event</span></span>|<span data-ttu-id="a8d94-439">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-439">Event ID</span></span>|<span data-ttu-id="a8d94-440">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-440">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadCreating`|<span data-ttu-id="a8d94-441">70</span><span class="sxs-lookup"><span data-stu-id="a8d94-441">70</span></span>|<span data-ttu-id="a8d94-442">スレッドが作成されました。</span><span class="sxs-lookup"><span data-stu-id="a8d94-442">Thread has been created.</span></span>|

 <span data-ttu-id="a8d94-443">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-443">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-444">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-444">Field name</span></span>|<span data-ttu-id="a8d94-445">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-445">Data type</span></span>|<span data-ttu-id="a8d94-446">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-446">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="a8d94-447">スレッド ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-447">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-448">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-448">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="threadrunning-event"></a><span data-ttu-id="a8d94-449">ThreadRunning イベント</span><span class="sxs-lookup"><span data-stu-id="a8d94-449">ThreadRunning event</span></span>

 <span data-ttu-id="a8d94-450">次の表は、キーワードとレベルを示しています。</span><span class="sxs-lookup"><span data-stu-id="a8d94-450">The following table shows the keywords and level.</span></span>

|<span data-ttu-id="a8d94-451">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="a8d94-451">Keyword for raising the event</span></span>|<span data-ttu-id="a8d94-452">Level</span><span class="sxs-lookup"><span data-stu-id="a8d94-452">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a8d94-453">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="a8d94-453">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="a8d94-454">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="a8d94-454">Informational (4)</span></span>|

 <span data-ttu-id="a8d94-455">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-455">The following table shows the event information.</span></span>

|<span data-ttu-id="a8d94-456">event</span><span class="sxs-lookup"><span data-stu-id="a8d94-456">Event</span></span>|<span data-ttu-id="a8d94-457">イベント ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-457">Event ID</span></span>|<span data-ttu-id="a8d94-458">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-458">Description</span></span>|
|----------------|---------------|-----------------|
|`ThreadRunning`|<span data-ttu-id="a8d94-459">71</span><span class="sxs-lookup"><span data-stu-id="a8d94-459">71</span></span>|<span data-ttu-id="a8d94-460">スレッドが実行を開始しました。</span><span class="sxs-lookup"><span data-stu-id="a8d94-460">Thread has started running.</span></span>|

 <span data-ttu-id="a8d94-461">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="a8d94-461">The following table shows the event data.</span></span>

|<span data-ttu-id="a8d94-462">フィールド名</span><span class="sxs-lookup"><span data-stu-id="a8d94-462">Field name</span></span>|<span data-ttu-id="a8d94-463">データ型</span><span class="sxs-lookup"><span data-stu-id="a8d94-463">Data type</span></span>|<span data-ttu-id="a8d94-464">説明</span><span class="sxs-lookup"><span data-stu-id="a8d94-464">Description</span></span>|
|----------------|---------------|-----------------|
|`ID`|`win:Pointer`|<span data-ttu-id="a8d94-465">スレッド ID</span><span class="sxs-lookup"><span data-stu-id="a8d94-465">Thread ID</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="a8d94-466">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="a8d94-466">Unique ID for the instance of CoreCLR.</span></span>|
