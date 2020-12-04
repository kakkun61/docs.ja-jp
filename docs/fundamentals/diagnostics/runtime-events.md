---
title: ランタイムイベント
description: ETW、LTTng、または EventPipe で使用できる .NET ランタイム (CoreCLR) によって生成される診断イベントを確認します。
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- runtime events (CoreCLR)
- ETW, EventPipe runtime events (CoreCLR)
ms.openlocfilehash: 33fa7275ce40934ce043b4d0dba5749c37515755
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "96594049"
---
# <a name="net-runtime-events"></a><span data-ttu-id="f06a8-103">.NET ランタイムイベント</span><span class="sxs-lookup"><span data-stu-id="f06a8-103">.NET runtime events</span></span>

<span data-ttu-id="f06a8-104">.NET ランタイム (CoreCLR) は、、、などのさまざまなメカニズムを使用して使用できる .NET アプリケーションの問題を診断するために使用できるさまざまなイベントを生成し `ETW` `LTTng` `EventPipe` ます。</span><span class="sxs-lookup"><span data-stu-id="f06a8-104">The .NET runtime (CoreCLR) emits various events that can be used to diagnose issues with your .NET application that can be consumed via various mechanisms such as `ETW`, `LTTng`, and `EventPipe`.</span></span>

<span data-ttu-id="f06a8-105">このドキュメントは、.NET Core ランタイムによって発生するイベントの参照として機能します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-105">This document serves as a reference on the events that are fired by .NET Core runtime.</span></span>

<span data-ttu-id="f06a8-106">.NET Framework のランタイムイベントについては、「 [CLR ETW events](../../framework/performance/clr-etw-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f06a8-106">For runtime events in .NET Framework, see [CLR ETW Events](../../framework/performance/clr-etw-events.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f06a8-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f06a8-107">In this section</span></span>

<span data-ttu-id="f06a8-108">[競合イベント](runtime-contention-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-108">[Contention Events](runtime-contention-events.md)</span></span>\
<span data-ttu-id="f06a8-109">これらのイベントは、モニターのロック競合に関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-109">These events collect information about monitor lock contentions.</span></span>

<span data-ttu-id="f06a8-110">[ガベージコレクションイベント](runtime-garbage-collection-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-110">[Garbage Collection Events](runtime-garbage-collection-events.md)</span></span>\
<span data-ttu-id="f06a8-111">これらのイベントは、ガベージ コレクションに関連する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-111">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="f06a8-112">ガベージコレクションが実行された回数、ガベージコレクション中に解放されたメモリの量など、診断やデバッグに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f06a8-112">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc.</span></span>

<span data-ttu-id="f06a8-113">[例外イベント](runtime-exception-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-113">[Exception Events](runtime-exception-events.md)</span></span>\
<span data-ttu-id="f06a8-114">これらのランタイムイベントは、スローされた例外に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="f06a8-114">These runtime events capture information about exceptions that are thrown.</span></span>

<span data-ttu-id="f06a8-115">[相互運用イベント](runtime-interop-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-115">[Interop Events](runtime-interop-events.md)</span></span>\
<span data-ttu-id="f06a8-116">これらのランタイムイベントは、共通中間言語 (CIL) のスタブ生成に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="f06a8-116">These runtime events capture information about Common Intermediate Language (CIL) stub generation.</span></span>

<span data-ttu-id="f06a8-117">[ローダーイベントとバインダーイベント](runtime-loader-binder-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-117">[Loader and Binder Events](runtime-loader-binder-events.md)</span></span>\
<span data-ttu-id="f06a8-118">これらのイベントは、アセンブリとモジュールの読み込みとアンロードに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-118">These events collect information relating to loading and unloading assemblies and modules.</span></span>

<span data-ttu-id="f06a8-119">[メソッドイベント](runtime-method-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-119">[Method Events](runtime-method-events.md)</span></span>\
<span data-ttu-id="f06a8-120">これらのイベントは、メソッド固有の情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-120">These events collect information that is specific to methods.</span></span> <span data-ttu-id="f06a8-121">これらのイベントのペイロードは、シンボルの解決に必要です。</span><span class="sxs-lookup"><span data-stu-id="f06a8-121">The payload of these events is required for symbol resolution.</span></span> <span data-ttu-id="f06a8-122">さらに、これらのイベントは、メソッドが呼び出された回数などの有用な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-122">In addition, these events provide helpful information such as the number of times a method was called.</span></span>

<span data-ttu-id="f06a8-123">[スレッドイベント](runtime-thread-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-123">[Thread Events](runtime-thread-events.md)</span></span>\
<span data-ttu-id="f06a8-124">これらのイベントは、ワーカー スレッドと I/O スレッドに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-124">These events collect information about worker and I/O threads.</span></span>

<span data-ttu-id="f06a8-125">[型イベント](runtime-type-events.md)</span><span class="sxs-lookup"><span data-stu-id="f06a8-125">[Type Events](runtime-type-events.md)</span></span>\
<span data-ttu-id="f06a8-126">これらのイベントは、型システムに関する情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="f06a8-126">These events collect information about the type system.</span></span>
