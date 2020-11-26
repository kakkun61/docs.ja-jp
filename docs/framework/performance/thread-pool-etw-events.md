---
title: スレッド プール ETW イベント
description: スレッドプールの ETW イベントを確認します。これは、.NET のスレッドに関する情報を収集します。 スレッドプールイベントは、ワーカースレッドプールイベントまたは i/o スレッドプールイベントです。
ms.date: 03/30/2017
helpviewer_keywords:
- thread pool events [.NET Framework]
- ETW, thread pool events (CLR)
ms.assetid: f2a21e3a-3b6c-4433-97f3-47ff16855ecc
ms.openlocfilehash: 8b00c20e82ee1b1efa6a8a123e66a4cfc239143b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236170"
---
# <a name="thread-pool-etw-events"></a><span data-ttu-id="13dc3-104">スレッド プール ETW イベント</span><span class="sxs-lookup"><span data-stu-id="13dc3-104">Thread Pool ETW Events</span></span>

<span data-ttu-id="13dc3-105">これらのイベントは、ワーカー スレッドと I/O スレッドに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-105">These events collect information about worker and I/O threads.</span></span>  
  
 <span data-ttu-id="13dc3-106">スレッド プール イベントには 2 つのグループがあります。</span><span class="sxs-lookup"><span data-stu-id="13dc3-106">There are two groups of thread pool events:</span></span>  
  
- <span data-ttu-id="13dc3-107">[ワーカー スレッド プール イベント](#worker-thread-pool-events)は、アプリケーションがどのようにスレッド プールを使用するかに関する情報と、コンカレンシー制御におけるワークロードの効果に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-107">[Worker thread pool events](#worker-thread-pool-events), which provide information about how an application uses the thread pool, and the effect of workloads on concurrency control.</span></span>  
  
- <span data-ttu-id="13dc3-108">[I/O スレッド プール イベント](#io-thread-events)は、スレッド プールで作成、無効化、無効化解除、または終了した I/O スレッドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-108">[I/O thread pool events](#io-thread-events), which provide information about I/O threads that are created, retired, unretired, or terminated in the thread pool.</span></span>  

## <a name="worker-thread-pool-events"></a><span data-ttu-id="13dc3-109">ワーカー スレッド プール イベント</span><span class="sxs-lookup"><span data-stu-id="13dc3-109">Worker Thread Pool Events</span></span>

 <span data-ttu-id="13dc3-110">これらのイベントは、ランタイムのワーカー スレッドのプールに関連付けられており、スレッド イベントに関する通知 (スレッドが作成されたり停止されたりした場合など) を提供します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-110">These events relate to the runtime's worker thread pool and provide notifications for thread events (for example, when a thread is created or stopped).</span></span> <span data-ttu-id="13dc3-111">ワーカー スレッド プールは、スレッドの数が計測されたスループットに基づいて計算されるアダプティブ アルゴリズムを使用して、コンカレンシー制御を実行します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-111">The worker thread pool uses an adaptive algorithm for concurrency control, where the number of threads is calculated based on the measured throughput.</span></span> <span data-ttu-id="13dc3-112">ワーカー スレッド プール イベントを使用すると、アプリケーションで使用されるスレッド プールの様子や特定のワークロードがコンカレンシー制御に与える影響などを理解することができます。</span><span class="sxs-lookup"><span data-stu-id="13dc3-112">Worker thread pool events can be used to understand how an application is using the thread pool, and the effect that certain workloads may have on concurrency control.</span></span>  
  
### <a name="threadpoolworkerthreadstart-and-threadpoolworkerthreadstop"></a><span data-ttu-id="13dc3-113">ThreadPoolWorkerThreadStart および ThreadPoolWorkerThreadStop</span><span class="sxs-lookup"><span data-stu-id="13dc3-113">ThreadPoolWorkerThreadStart and ThreadPoolWorkerThreadStop</span></span>  

 <span data-ttu-id="13dc3-114">次の表に、これらのイベントのキーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-114">The following table shows the keyword and level for these events.</span></span> <span data-ttu-id="13dc3-115">(詳細については、「 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="13dc3-115">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="13dc3-116">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-116">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-117">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-117">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-118">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-118">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-119">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-119">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-120">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-120">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-121">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-121">Event</span></span>|<span data-ttu-id="13dc3-122">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-122">Event ID</span></span>|<span data-ttu-id="13dc3-123">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="13dc3-123">Raised when</span></span>|  
|-|-|-|  
|`ThreadPoolWorkerThreadStart`|<span data-ttu-id="13dc3-124">50</span><span class="sxs-lookup"><span data-stu-id="13dc3-124">50</span></span>|<span data-ttu-id="13dc3-125">ワーカー スレッドが作成された。</span><span class="sxs-lookup"><span data-stu-id="13dc3-125">A worker thread is created.</span></span>|  
|`ThreadPoolWorkerThreadStop`|<span data-ttu-id="13dc3-126">51</span><span class="sxs-lookup"><span data-stu-id="13dc3-126">51</span></span>|<span data-ttu-id="13dc3-127">ワーカー スレッドが停止された。</span><span class="sxs-lookup"><span data-stu-id="13dc3-127">A worker thread is stopped.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStart`|<span data-ttu-id="13dc3-128">52</span><span class="sxs-lookup"><span data-stu-id="13dc3-128">52</span></span>|<span data-ttu-id="13dc3-129">ワーカー スレッドが無効にされた。</span><span class="sxs-lookup"><span data-stu-id="13dc3-129">A worker thread retires.</span></span>|  
|`ThreadPoolWorkerThreadRetirementStop`|<span data-ttu-id="13dc3-130">53</span><span class="sxs-lookup"><span data-stu-id="13dc3-130">53</span></span>|<span data-ttu-id="13dc3-131">提供終了になったワーカー スレッドが再びアクティブになった。</span><span class="sxs-lookup"><span data-stu-id="13dc3-131">A retired worker thread becomes active again.</span></span>|  
  
 <span data-ttu-id="13dc3-132">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-132">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-133">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-133">Field name</span></span>|<span data-ttu-id="13dc3-134">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-134">Data type</span></span>|<span data-ttu-id="13dc3-135">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-135">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-136">ActiveWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="13dc3-136">ActiveWorkerThreadCount</span></span>|<span data-ttu-id="13dc3-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="13dc3-137">win:UInt32</span></span>|<span data-ttu-id="13dc3-138">作業の処理に使用可能なワーカー スレッド (既に作業の処理中のもの含む) の数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-138">Number of worker threads available to process work, including those that are already processing work.</span></span>|  
|<span data-ttu-id="13dc3-139">RetiredWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="13dc3-139">RetiredWorkerThreadCount</span></span>|<span data-ttu-id="13dc3-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="13dc3-140">win:UInt32</span></span>|<span data-ttu-id="13dc3-141">作業の処理に使用できないものの、後にさらに多くのスレッドが必要になった場合に備えて予約されているワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-141">Number of worker threads that are not available to process work, but that are being held in reserve in case more threads are needed later.</span></span>|  
|<span data-ttu-id="13dc3-142">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-142">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-143">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-143">Win:UInt16</span></span>|<span data-ttu-id="13dc3-144">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-144">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="threadpoolworkerthreadadjustment"></a><span data-ttu-id="13dc3-145">ThreadPoolWorkerThreadAdjustment</span><span class="sxs-lookup"><span data-stu-id="13dc3-145">ThreadPoolWorkerThreadAdjustment</span></span>  

 <span data-ttu-id="13dc3-146">これらのスレッド プール イベントは、スレッドの挿入 (コンカレンシー制御) アルゴリズムの動作を理解したりデバッグしたりするための情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-146">These thread pool events provide information for understanding and debugging the behavior of the thread injection (concurrency control) algorithm.</span></span> <span data-ttu-id="13dc3-147">この情報は、ワーカー スレッド プールによって内部で使用されます。</span><span class="sxs-lookup"><span data-stu-id="13dc3-147">The information is used internally by the worker thread pool.</span></span>  
  
#### <a name="threadpoolworkerthreadadjustmentsample"></a><span data-ttu-id="13dc3-148">ThreadPoolWorkerThreadAdjustmentSample</span><span class="sxs-lookup"><span data-stu-id="13dc3-148">ThreadPoolWorkerThreadAdjustmentSample</span></span>  

 <span data-ttu-id="13dc3-149">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-149">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="13dc3-150">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-150">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-151">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-151">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-152">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-152">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-153">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-153">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-154">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-154">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-155">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-155">Event</span></span>|<span data-ttu-id="13dc3-156">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-156">Event ID</span></span>|<span data-ttu-id="13dc3-157">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-157">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentSample`|<span data-ttu-id="13dc3-158">54</span><span class="sxs-lookup"><span data-stu-id="13dc3-158">54</span></span>|<span data-ttu-id="13dc3-159">1 つのサンプルの情報のコレクションを参照します。つまり、特定のコンカレンシー レベルの特定の時刻におけるスループットの測定値です。</span><span class="sxs-lookup"><span data-stu-id="13dc3-159">Refers to the collection of information for one sample; that is, a measurement of throughput with a certain concurrency level, in an instant of time.</span></span>|  
  
 <span data-ttu-id="13dc3-160">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-160">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-161">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-161">Field name</span></span>|<span data-ttu-id="13dc3-162">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-162">Data type</span></span>|<span data-ttu-id="13dc3-163">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-163">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-164">スループット</span><span class="sxs-lookup"><span data-stu-id="13dc3-164">Throughput</span></span>|<span data-ttu-id="13dc3-165">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-165">win:Double</span></span>|<span data-ttu-id="13dc3-166">時間の単位あたりの入力候補の数です。</span><span class="sxs-lookup"><span data-stu-id="13dc3-166">Number of completions per unit of time.</span></span>|  
|<span data-ttu-id="13dc3-167">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-167">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-168">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-168">Win:UInt16</span></span>|<span data-ttu-id="13dc3-169">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-169">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentadjustment"></a><span data-ttu-id="13dc3-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span><span class="sxs-lookup"><span data-stu-id="13dc3-170">ThreadPoolWorkerThreadAdjustmentAdjustment</span></span>  

 <span data-ttu-id="13dc3-171">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-171">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="13dc3-172">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-172">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-173">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-173">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-174">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-174">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-175">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-175">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-176">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-176">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-177">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-177">Event</span></span>|<span data-ttu-id="13dc3-178">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-178">Event ID</span></span>|<span data-ttu-id="13dc3-179">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-179">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentAdjustment`|<span data-ttu-id="13dc3-180">55</span><span class="sxs-lookup"><span data-stu-id="13dc3-180">55</span></span>|<span data-ttu-id="13dc3-181">スレッドの挿入 (山登り法) アルゴリズムが、コンカレンシー レベルに変更があったと判断した場合に、コントロールの変更を記録します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-181">Records a change in control, when the thread injection (hill-climbing) algorithm determines that a change in concurrency level is in place.</span></span>|  
  
 <span data-ttu-id="13dc3-182">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-182">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-183">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-183">Field name</span></span>|<span data-ttu-id="13dc3-184">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-184">Data type</span></span>|<span data-ttu-id="13dc3-185">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-185">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-186">AverageThroughput</span><span class="sxs-lookup"><span data-stu-id="13dc3-186">AverageThroughput</span></span>|<span data-ttu-id="13dc3-187">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-187">win:Double</span></span>|<span data-ttu-id="13dc3-188">計測のサンプルの平均のスループット。</span><span class="sxs-lookup"><span data-stu-id="13dc3-188">Average throughput of a sample of measurements.</span></span>|  
|<span data-ttu-id="13dc3-189">NewWorkerThreadCount</span><span class="sxs-lookup"><span data-stu-id="13dc3-189">NewWorkerThreadCount</span></span>|<span data-ttu-id="13dc3-190">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="13dc3-190">win:UInt32</span></span>|<span data-ttu-id="13dc3-191">新しいアクティブなワーカー スレッド数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-191">New number of active worker threads.</span></span>|  
|<span data-ttu-id="13dc3-192">理由</span><span class="sxs-lookup"><span data-stu-id="13dc3-192">Reason</span></span>|<span data-ttu-id="13dc3-193">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="13dc3-193">win:UInt32</span></span>|<span data-ttu-id="13dc3-194">調整の理由。</span><span class="sxs-lookup"><span data-stu-id="13dc3-194">Reason for the adjustment.</span></span><br /><br /> <span data-ttu-id="13dc3-195">0x00 - ウォーム アップ。</span><span class="sxs-lookup"><span data-stu-id="13dc3-195">0x00 - Warmup.</span></span><br /><br /> <span data-ttu-id="13dc3-196">0x01 - 初期化。</span><span class="sxs-lookup"><span data-stu-id="13dc3-196">0x01 - Initializing.</span></span><br /><br /> <span data-ttu-id="13dc3-197">0x02 - ランダムな移動。</span><span class="sxs-lookup"><span data-stu-id="13dc3-197">0x02 - Random move.</span></span><br /><br /> <span data-ttu-id="13dc3-198">0x03 - 上昇移動。</span><span class="sxs-lookup"><span data-stu-id="13dc3-198">0x03 - Climbing move.</span></span><br /><br /> <span data-ttu-id="13dc3-199">0x04 - 変更点。</span><span class="sxs-lookup"><span data-stu-id="13dc3-199">0x04 - Change point.</span></span><br /><br /> <span data-ttu-id="13dc3-200">0x05 - 安定化。</span><span class="sxs-lookup"><span data-stu-id="13dc3-200">0x05 - Stabilizing.</span></span><br /><br /> <span data-ttu-id="13dc3-201">0x06 - 不足。</span><span class="sxs-lookup"><span data-stu-id="13dc3-201">0x06 - Starvation.</span></span><br /><br /> <span data-ttu-id="13dc3-202">0x07 - スレッドのタイムアウト。</span><span class="sxs-lookup"><span data-stu-id="13dc3-202">0x07 - Thread timed out.</span></span>|  
|<span data-ttu-id="13dc3-203">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-203">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-204">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-204">Win:UInt16</span></span>|<span data-ttu-id="13dc3-205">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-205">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
#### <a name="threadpoolworkerthreadadjustmentstats"></a><span data-ttu-id="13dc3-206">ThreadPoolWorkerThreadAdjustmentStats</span><span class="sxs-lookup"><span data-stu-id="13dc3-206">ThreadPoolWorkerThreadAdjustmentStats</span></span>  

 <span data-ttu-id="13dc3-207">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-207">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="13dc3-208">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-208">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-209">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-209">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-210">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-210">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-211">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-211">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-212">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-212">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-213">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-213">Event</span></span>|<span data-ttu-id="13dc3-214">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-214">Event ID</span></span>|<span data-ttu-id="13dc3-215">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-215">Description</span></span>|  
|-----------|--------------|-----------------|  
|`ThreadPoolWorkerThreadAdjustmentStats`|<span data-ttu-id="13dc3-216">56</span><span class="sxs-lookup"><span data-stu-id="13dc3-216">56</span></span>|<span data-ttu-id="13dc3-217">スレッド プールに関するデータを収集します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-217">Gathers data on the thread pool.</span></span>|  
  
 <span data-ttu-id="13dc3-218">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-218">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-219">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-219">Field name</span></span>|<span data-ttu-id="13dc3-220">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-220">Data type</span></span>|<span data-ttu-id="13dc3-221">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-221">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-222">Duration</span><span class="sxs-lookup"><span data-stu-id="13dc3-222">Duration</span></span>|<span data-ttu-id="13dc3-223">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-223">win:Double</span></span>|<span data-ttu-id="13dc3-224">これらの統計情報が収集される時間数 (秒)。</span><span class="sxs-lookup"><span data-stu-id="13dc3-224">Amount of time, in seconds, during which these statistics were collected.</span></span>|  
|<span data-ttu-id="13dc3-225">スループット</span><span class="sxs-lookup"><span data-stu-id="13dc3-225">Throughput</span></span>|<span data-ttu-id="13dc3-226">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-226">win:Double</span></span>|<span data-ttu-id="13dc3-227">この間隔中の 1 秒あたりの入力候補の平均数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-227">Average number of completions per second during this interval.</span></span>|  
|<span data-ttu-id="13dc3-228">ThreadWave</span><span class="sxs-lookup"><span data-stu-id="13dc3-228">ThreadWave</span></span>|<span data-ttu-id="13dc3-229">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-229">win:Double</span></span>|<span data-ttu-id="13dc3-230">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="13dc3-230">Reserved for internal use.</span></span>|  
|<span data-ttu-id="13dc3-231">ThroughputWave</span><span class="sxs-lookup"><span data-stu-id="13dc3-231">ThroughputWave</span></span>|<span data-ttu-id="13dc3-232">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-232">win:Double</span></span>|<span data-ttu-id="13dc3-233">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="13dc3-233">Reserved for internal use.</span></span>|  
|<span data-ttu-id="13dc3-234">ThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="13dc3-234">ThroughputErrorEstimate</span></span>|<span data-ttu-id="13dc3-235">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-235">win:Double</span></span>|<span data-ttu-id="13dc3-236">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="13dc3-236">Reserved for internal use.</span></span>|  
|<span data-ttu-id="13dc3-237">AverageThroughputErrorEstimate</span><span class="sxs-lookup"><span data-stu-id="13dc3-237">AverageThroughputErrorEstimate</span></span>|<span data-ttu-id="13dc3-238">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-238">win:Double</span></span>|<span data-ttu-id="13dc3-239">内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="13dc3-239">Reserved for internal use.</span></span>|  
|<span data-ttu-id="13dc3-240">ThroughputRatio</span><span class="sxs-lookup"><span data-stu-id="13dc3-240">ThroughputRatio</span></span>|<span data-ttu-id="13dc3-241">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-241">win:Double</span></span>|<span data-ttu-id="13dc3-242">この間隔中にアクティブなワーカー スレッドの数の変動によって引き起こされる、スループットの相対的な向上。</span><span class="sxs-lookup"><span data-stu-id="13dc3-242">The relative improvement in throughput caused by variations in active worker thread count during this interval.</span></span>|  
|<span data-ttu-id="13dc3-243">Confidence</span><span class="sxs-lookup"><span data-stu-id="13dc3-243">Confidence</span></span>|<span data-ttu-id="13dc3-244">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-244">win:Double</span></span>|<span data-ttu-id="13dc3-245">ThroughputRatio フィールドの有効性の測定結果。</span><span class="sxs-lookup"><span data-stu-id="13dc3-245">A measure of the validity of the ThroughputRatio field.</span></span>|  
|<span data-ttu-id="13dc3-246">NewcontrolSetting</span><span class="sxs-lookup"><span data-stu-id="13dc3-246">NewcontrolSetting</span></span>|<span data-ttu-id="13dc3-247">win:Double</span><span class="sxs-lookup"><span data-stu-id="13dc3-247">win:Double</span></span>|<span data-ttu-id="13dc3-248">アクティブなスレッド数の将来のバリエーションのベースラインとして使用するアクティブなワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-248">The number of active worker threads that will serve as the baseline for future variations in active thread count.</span></span>|  
|<span data-ttu-id="13dc3-249">NewThreadWaveMagnitude</span><span class="sxs-lookup"><span data-stu-id="13dc3-249">NewThreadWaveMagnitude</span></span>|<span data-ttu-id="13dc3-250">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-250">Win:UInt16</span></span>|<span data-ttu-id="13dc3-251">アクティブなスレッド数の、将来のバリエーションの大きさを指定します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-251">The magnitude of future variations in active thread count.</span></span>|  
|<span data-ttu-id="13dc3-252">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-252">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-253">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-253">Win:UInt16</span></span>|<span data-ttu-id="13dc3-254">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-254">Unique ID for the instance of CLR or CoreCLR.</span></span>|  

## <a name="io-thread-events"></a><span data-ttu-id="13dc3-255">I/O スレッド イベント</span><span class="sxs-lookup"><span data-stu-id="13dc3-255">I/O Thread Events</span></span>  

 <span data-ttu-id="13dc3-256">これらのスレッド プール イベントは、I/O スレッド プール (完了ポート) にあるスレッドで発生します。これは非同期です。</span><span class="sxs-lookup"><span data-stu-id="13dc3-256">These thread pool events occur for threads in the I/O thread pool (completion ports), which is asynchronous.</span></span>  
  
### <a name="iothreadcreate_v1"></a><span data-ttu-id="13dc3-257">IOThreadCreate_V1</span><span class="sxs-lookup"><span data-stu-id="13dc3-257">IOThreadCreate_V1</span></span>  

 <span data-ttu-id="13dc3-258">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-258">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="13dc3-259">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-259">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-260">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-260">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-261">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-261">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-262">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-262">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-263">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-263">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-264">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-264">Event</span></span>|<span data-ttu-id="13dc3-265">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-265">Event ID</span></span>|<span data-ttu-id="13dc3-266">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="13dc3-266">Raised when</span></span>|  
|-|-|-|  
|`IOThreadCreate_V1`|<span data-ttu-id="13dc3-267">44</span><span class="sxs-lookup"><span data-stu-id="13dc3-267">44</span></span>|<span data-ttu-id="13dc3-268">I/O スレッドがスレッド プールに作成された。</span><span class="sxs-lookup"><span data-stu-id="13dc3-268">An I/O thread is created in the thread pool.</span></span>|  
  
 <span data-ttu-id="13dc3-269">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-269">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-270">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-270">Field name</span></span>|<span data-ttu-id="13dc3-271">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-271">Data type</span></span>|<span data-ttu-id="13dc3-272">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-272">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-273">Count</span><span class="sxs-lookup"><span data-stu-id="13dc3-273">Count</span></span>|<span data-ttu-id="13dc3-274">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-274">win:UInt64</span></span>|<span data-ttu-id="13dc3-275">新しく作成されたスレッドを含む、I/O のスレッドの数です。</span><span class="sxs-lookup"><span data-stu-id="13dc3-275">Number of I/O threads, including the newly created thread.</span></span>|  
|<span data-ttu-id="13dc3-276">NumRetired</span><span class="sxs-lookup"><span data-stu-id="13dc3-276">NumRetired</span></span>|<span data-ttu-id="13dc3-277">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-277">win:UInt64</span></span>|<span data-ttu-id="13dc3-278">提供終了になったワーカー スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-278">Number of retired worker threads.</span></span>|  
|<span data-ttu-id="13dc3-279">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-279">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-280">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-280">Win:UInt16</span></span>|<span data-ttu-id="13dc3-281">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-281">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadretire_v1"></a><span data-ttu-id="13dc3-282">IOThreadRetire_V1</span><span class="sxs-lookup"><span data-stu-id="13dc3-282">IOThreadRetire_V1</span></span>  

 <span data-ttu-id="13dc3-283">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="13dc3-284">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-284">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-285">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-286">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-286">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-287">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-288">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-289">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-289">Event</span></span>|<span data-ttu-id="13dc3-290">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-290">Event ID</span></span>|<span data-ttu-id="13dc3-291">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="13dc3-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadRetire_V1`|<span data-ttu-id="13dc3-292">46</span><span class="sxs-lookup"><span data-stu-id="13dc3-292">46</span></span>|<span data-ttu-id="13dc3-293">I/O スレッドが、提供終了の候補になる。</span><span class="sxs-lookup"><span data-stu-id="13dc3-293">An I/O thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="13dc3-294">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-295">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-295">Field name</span></span>|<span data-ttu-id="13dc3-296">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-296">Data type</span></span>|<span data-ttu-id="13dc3-297">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-298">Count</span><span class="sxs-lookup"><span data-stu-id="13dc3-298">Count</span></span>|<span data-ttu-id="13dc3-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-299">win:UInt64</span></span>|<span data-ttu-id="13dc3-300">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-300">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="13dc3-301">NumRetired</span><span class="sxs-lookup"><span data-stu-id="13dc3-301">NumRetired</span></span>|<span data-ttu-id="13dc3-302">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-302">win:UInt64</span></span>|<span data-ttu-id="13dc3-303">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-303">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="13dc3-304">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-304">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-305">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-305">Win:UInt16</span></span>|<span data-ttu-id="13dc3-306">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-306">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadunretire_v1"></a><span data-ttu-id="13dc3-307">IOThreadUnretire_V1</span><span class="sxs-lookup"><span data-stu-id="13dc3-307">IOThreadUnretire_V1</span></span>  

 <span data-ttu-id="13dc3-308">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-308">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="13dc3-309">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-309">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-310">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-310">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-311">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-311">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-312">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-312">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-313">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-313">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-314">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-314">Event</span></span>|<span data-ttu-id="13dc3-315">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-315">Event ID</span></span>|<span data-ttu-id="13dc3-316">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="13dc3-316">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadUnretire_V1`|<span data-ttu-id="13dc3-317">47</span><span class="sxs-lookup"><span data-stu-id="13dc3-317">47</span></span>|<span data-ttu-id="13dc3-318">スレッドが提供終了の候補になってから待機期間内に I/O が到着したため I/O スレッドが提供終了解除された。</span><span class="sxs-lookup"><span data-stu-id="13dc3-318">An I/O thread is unretired because of I/O that arrives within a waiting period after the thread becomes a retirement candidate.</span></span>|  
  
 <span data-ttu-id="13dc3-319">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-319">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-320">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-320">Field name</span></span>|<span data-ttu-id="13dc3-321">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-321">Data type</span></span>|<span data-ttu-id="13dc3-322">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-322">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-323">Count</span><span class="sxs-lookup"><span data-stu-id="13dc3-323">Count</span></span>|<span data-ttu-id="13dc3-324">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-324">win:UInt64</span></span>|<span data-ttu-id="13dc3-325">これを含む、スレッド プール内の I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-325">Number of I/O threads in the thread pool, including this one.</span></span>|  
|<span data-ttu-id="13dc3-326">NumRetired</span><span class="sxs-lookup"><span data-stu-id="13dc3-326">NumRetired</span></span>|<span data-ttu-id="13dc3-327">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-327">win:UInt64</span></span>|<span data-ttu-id="13dc3-328">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-328">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="13dc3-329">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-329">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-330">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-330">Win:UInt16</span></span>|<span data-ttu-id="13dc3-331">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-331">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
### <a name="iothreadterminate"></a><span data-ttu-id="13dc3-332">IOThreadTerminate</span><span class="sxs-lookup"><span data-stu-id="13dc3-332">IOThreadTerminate</span></span>  

 <span data-ttu-id="13dc3-333">次の表に、キーワードとレベルを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-333">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="13dc3-334">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="13dc3-334">Keyword for raising the event</span></span>|<span data-ttu-id="13dc3-335">Level</span><span class="sxs-lookup"><span data-stu-id="13dc3-335">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="13dc3-336">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="13dc3-336">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="13dc3-337">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="13dc3-337">Informational (4)</span></span>|  
  
 <span data-ttu-id="13dc3-338">次の表に、イベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-338">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="13dc3-339">Event</span><span class="sxs-lookup"><span data-stu-id="13dc3-339">Event</span></span>|<span data-ttu-id="13dc3-340">イベント ID</span><span class="sxs-lookup"><span data-stu-id="13dc3-340">Event ID</span></span>|<span data-ttu-id="13dc3-341">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="13dc3-341">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`IOThreadTerminate`|<span data-ttu-id="13dc3-342">45</span><span class="sxs-lookup"><span data-stu-id="13dc3-342">45</span></span>|<span data-ttu-id="13dc3-343">スレッドプールで i/o スレッドが終了します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-343">An I/O thread is terminated in the thread pool.</span></span>|  
  
 <span data-ttu-id="13dc3-344">次の表に、イベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="13dc3-344">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="13dc3-345">フィールド名</span><span class="sxs-lookup"><span data-stu-id="13dc3-345">Field name</span></span>|<span data-ttu-id="13dc3-346">データ型</span><span class="sxs-lookup"><span data-stu-id="13dc3-346">Data type</span></span>|<span data-ttu-id="13dc3-347">説明</span><span class="sxs-lookup"><span data-stu-id="13dc3-347">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="13dc3-348">Count</span><span class="sxs-lookup"><span data-stu-id="13dc3-348">Count</span></span>|<span data-ttu-id="13dc3-349">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-349">win:UInt64</span></span>|<span data-ttu-id="13dc3-350">スレッド プールに残っている I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-350">Number of I/O threads remaining in the thread pool.</span></span>|  
|<span data-ttu-id="13dc3-351">NumRetired</span><span class="sxs-lookup"><span data-stu-id="13dc3-351">NumRetired</span></span>|<span data-ttu-id="13dc3-352">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="13dc3-352">win:UInt64</span></span>|<span data-ttu-id="13dc3-353">提供終了になった I/O スレッドの数。</span><span class="sxs-lookup"><span data-stu-id="13dc3-353">Number of retired I/O threads.</span></span>|  
|<span data-ttu-id="13dc3-354">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="13dc3-354">ClrInstanceID</span></span>|<span data-ttu-id="13dc3-355">Win:UInt16</span><span class="sxs-lookup"><span data-stu-id="13dc3-355">Win:UInt16</span></span>|<span data-ttu-id="13dc3-356">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="13dc3-356">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13dc3-357">関連項目</span><span class="sxs-lookup"><span data-stu-id="13dc3-357">See also</span></span>

- [<span data-ttu-id="13dc3-358">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="13dc3-358">CLR ETW Events</span></span>](clr-etw-events.md)
