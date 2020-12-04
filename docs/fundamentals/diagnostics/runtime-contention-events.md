---
title: ロック競合ランタイムイベントの監視
description: モニターのロック競合に固有の情報を収集する ETW イベントを参照してください。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- monitor lock contention events (CoreCLR)
- ETW, EventPipe, LTTng contention events (CoreCLR)
ms.openlocfilehash: 38e5f493d4b223b4839dbd6f814cf656722189b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594054"
---
# <a name="net-runtime-contention-events"></a><span data-ttu-id="2b47f-103">.NET ランタイム競合イベント</span><span class="sxs-lookup"><span data-stu-id="2b47f-103">.NET runtime contention events</span></span>

<span data-ttu-id="2b47f-104">これらのランタイムイベント `Monitor.Enter` は、または C# の lock キーワードを使用したなど、モニターのロックの競合に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="2b47f-104">These runtime events capture information about monitor lock contentions such as with `Monitor.Enter` or the C# lock keyword.</span></span> <span data-ttu-id="2b47f-105">診断のためにこれらのイベントを使用する方法の詳細については、「 [.net アプリケーションのログ記録とトレース](../../core/diagnostics/logging-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b47f-105">For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="contentionstart_v1-event"></a><span data-ttu-id="2b47f-106">ContentionStart_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2b47f-106">ContentionStart_V1 event</span></span>

<span data-ttu-id="2b47f-107">このイベントは、モニターのロック競合の開始時に生成されます。</span><span class="sxs-lookup"><span data-stu-id="2b47f-107">This event is emitted at the start of a monitor lock contention.</span></span>

|<span data-ttu-id="2b47f-108">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2b47f-108">Keyword for raising the event</span></span>|<span data-ttu-id="2b47f-109">Level</span><span class="sxs-lookup"><span data-stu-id="2b47f-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2b47f-110">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="2b47f-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="2b47f-111">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2b47f-111">Informational (4)</span></span>|

 <span data-ttu-id="2b47f-112">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2b47f-112">The following table shows event information.</span></span>

|<span data-ttu-id="2b47f-113">event</span><span class="sxs-lookup"><span data-stu-id="2b47f-113">Event</span></span>|<span data-ttu-id="2b47f-114">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2b47f-114">Event ID</span></span>|<span data-ttu-id="2b47f-115">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2b47f-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="2b47f-116">81</span><span class="sxs-lookup"><span data-stu-id="2b47f-116">81</span></span>|<span data-ttu-id="2b47f-117">モニターのロックの競合が開始されます。</span><span class="sxs-lookup"><span data-stu-id="2b47f-117">A monitor lock contention starts.</span></span>|

|<span data-ttu-id="2b47f-118">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2b47f-118">Field name</span></span>|<span data-ttu-id="2b47f-119">データ型</span><span class="sxs-lookup"><span data-stu-id="2b47f-119">Data type</span></span>|<span data-ttu-id="2b47f-120">説明</span><span class="sxs-lookup"><span data-stu-id="2b47f-120">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="2b47f-121">`0` マネージドの場合 `1` ネイティブの場合。</span><span class="sxs-lookup"><span data-stu-id="2b47f-121">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2b47f-122">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2b47f-122">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="contentionstop_v1-event"></a><span data-ttu-id="2b47f-123">ContentionStop_V1 イベント</span><span class="sxs-lookup"><span data-stu-id="2b47f-123">ContentionStop_V1 event</span></span>

<span data-ttu-id="2b47f-124">このイベントは、モニターロックの競合が終了したときに生成されます。</span><span class="sxs-lookup"><span data-stu-id="2b47f-124">This event is emitted at the end of a monitor lock contention.</span></span>

|<span data-ttu-id="2b47f-125">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="2b47f-125">Keyword for raising the event</span></span>|<span data-ttu-id="2b47f-126">Level</span><span class="sxs-lookup"><span data-stu-id="2b47f-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="2b47f-127">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="2b47f-127">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="2b47f-128">情報提供 (4)</span><span class="sxs-lookup"><span data-stu-id="2b47f-128">Informational (4)</span></span>|

 <span data-ttu-id="2b47f-129">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="2b47f-129">The following table shows event information.</span></span>

|<span data-ttu-id="2b47f-130">event</span><span class="sxs-lookup"><span data-stu-id="2b47f-130">Event</span></span>|<span data-ttu-id="2b47f-131">イベント ID</span><span class="sxs-lookup"><span data-stu-id="2b47f-131">Event ID</span></span>|<span data-ttu-id="2b47f-132">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="2b47f-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStop_V1`|<span data-ttu-id="2b47f-133">91</span><span class="sxs-lookup"><span data-stu-id="2b47f-133">91</span></span>|<span data-ttu-id="2b47f-134">モニターのロックの競合が終了します。</span><span class="sxs-lookup"><span data-stu-id="2b47f-134">A monitor lock contention ends.</span></span>|

|<span data-ttu-id="2b47f-135">フィールド名</span><span class="sxs-lookup"><span data-stu-id="2b47f-135">Field name</span></span>|<span data-ttu-id="2b47f-136">データ型</span><span class="sxs-lookup"><span data-stu-id="2b47f-136">Data type</span></span>|<span data-ttu-id="2b47f-137">説明</span><span class="sxs-lookup"><span data-stu-id="2b47f-137">Description</span></span>|
|----------------|---------------|-----------------|
|`Flags`|`win:UInt8`|<span data-ttu-id="2b47f-138">`0` マネージドの場合 `1` ネイティブの場合。</span><span class="sxs-lookup"><span data-stu-id="2b47f-138">`0` for managed; `1` for native.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="2b47f-139">CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2b47f-139">Unique ID for the instance of CoreCLR.</span></span>|
|`DurationNs`|`win:Double`|<span data-ttu-id="2b47f-140">競合の継続時間 (ナノ秒単位)。</span><span class="sxs-lookup"><span data-stu-id="2b47f-140">Duration of the contention in nanoseconds.</span></span>|
