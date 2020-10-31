---
title: .NET ガベージ コレクション
description: .NET のガベージ コレクションについて説明します。 .NET のガベージ コレクターは、アプリケーションのメモリの割り当てと解放を管理します。
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: 39b5bf62935054bd4b9be2d228cc42202aa89144
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063190"
---
# <a name="garbage-collection"></a><span data-ttu-id="a8e2b-104">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="a8e2b-104">Garbage collection</span></span>

<span data-ttu-id="a8e2b-105">.NET のガベージ コレクターは、アプリケーションのメモリの割り当てと解放を管理します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-105">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="a8e2b-106">新しいオブジェクトを生成するたびに、共通言語ランタイムは、マネージド ヒープからオブジェクトにメモリを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-106">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="a8e2b-107">マネージド ヒープに使用可能なアドレス空間がある限り、ランタイムは新しいオブジェクト用に領域の割り当てを続けます。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-107">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="a8e2b-108">しかし、メモリの大きさは無限ではありません。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-108">However, memory is not infinite.</span></span> <span data-ttu-id="a8e2b-109">最終的には、ガベージ コレクターが、一部のメモリを解放するためにガベージ コレクションを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-109">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="a8e2b-110">コレクションの実行に最適な時期は、ガベージ コレクターの最適化エンジンが、割り当てられるオブジェクトの状況に応じて決定します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-110">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="a8e2b-111">コレクションを実行する場合、ガベージ コレクターは、アプリケーションによって使用されなくなったオブジェクトがマネージド ヒープにあるかどうかをチェックし、使われていないオブジェクトのメモリを再利用するために必要な操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-111">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8e2b-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a8e2b-112">In this section</span></span>
  
|<span data-ttu-id="a8e2b-113">Title</span><span class="sxs-lookup"><span data-stu-id="a8e2b-113">Title</span></span>|<span data-ttu-id="a8e2b-114">説明</span><span class="sxs-lookup"><span data-stu-id="a8e2b-114">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a8e2b-115">ガベージ コレクションの基礎</span><span class="sxs-lookup"><span data-stu-id="a8e2b-115">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="a8e2b-116">ガベージ コレクションの動作、マネージド ヒープに対するオブジェクトの割り当て方法、およびその他の主要な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-116">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="a8e2b-117">ワークステーションとサーバーのガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="a8e2b-117">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="a8e2b-118">ワークステーションのクライアント アプリ用ガベージ コレクションと、サーバーのサーバー アプリ用ガベージ コレクションの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-118">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="a8e2b-119">バックグラウンド ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="a8e2b-119">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="a8e2b-120">バックグラウンド ガベージ コレクションについて説明します。これは、第 2 世代のコレクションを処理中の、第 0 世代と第 1 世代のオブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-120">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="a8e2b-121">大きなオブジェクト ヒープ</span><span class="sxs-lookup"><span data-stu-id="a8e2b-121">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="a8e2b-122">大きなオブジェクト ヒープ (LOH) について、および大きなオブジェクトをガベージ コレクションする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-122">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="a8e2b-123">ガベージ コレクションとパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="a8e2b-123">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="a8e2b-124">ガベージ コレクションとパフォーマンスの問題を診断するために使用できるパフォーマンス チェックについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-124">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="a8e2b-125">発生したコレクション</span><span class="sxs-lookup"><span data-stu-id="a8e2b-125">Induced collections</span></span>](induced.md)|<span data-ttu-id="a8e2b-126">ガベージ コレクションがどのように行われるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-126">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="a8e2b-127">待機モード</span><span class="sxs-lookup"><span data-stu-id="a8e2b-127">Latency modes</span></span>](latency.md)|<span data-ttu-id="a8e2b-128">ガベージ コレクションの割り込みの動作を決定するモードについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-128">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="a8e2b-129">共有 Web ホストの最適化</span><span class="sxs-lookup"><span data-stu-id="a8e2b-129">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="a8e2b-130">複数の小規模な Web サイトで共有されているサーバーで、ガベージ コレクションを最適化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-130">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="a8e2b-131">ガベージ コレクションの通知</span><span class="sxs-lookup"><span data-stu-id="a8e2b-131">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="a8e2b-132">フル ガベージ コレクションが近づいたときと完了したときを検出する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-132">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="a8e2b-133">アプリケーション ドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="a8e2b-133">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="a8e2b-134">アプリケーション ドメインによる CPU とメモリの使用状況を監視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-134">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="a8e2b-135">弱い参照</span><span class="sxs-lookup"><span data-stu-id="a8e2b-135">Weak references</span></span>](weak-references.md)|<span data-ttu-id="a8e2b-136">アプリケーションからオブジェクトへのアクセスを許容したまま、そのオブジェクトをガベージ コレクターが収集できるようにする機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8e2b-136">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="a8e2b-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8e2b-137">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="a8e2b-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8e2b-138">See also</span></span>

- [<span data-ttu-id="a8e2b-139">アンマネージド リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="a8e2b-139">Clean up unmanaged resources</span></span>](unmanaged.md)
