---
title: 非同期の概要
description: ブロッキング I/O と複数コアでの同時操作の処理を容易にする鍵となる手法である非同期プログラミングについて説明します。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 495f225a3732812666dfa2f5c8c07f6f5b849c95
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824806"
---
# <a name="async-overview"></a><span data-ttu-id="6897b-103">非同期の概要</span><span class="sxs-lookup"><span data-stu-id="6897b-103">Async Overview</span></span>

<span data-ttu-id="6897b-104">少し前まで、アプリの高速化は、より新しい PC やサーバーを購入することによって単純に実現されていましたが、その傾向は終わりました。</span><span class="sxs-lookup"><span data-stu-id="6897b-104">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="6897b-105">実際には、逆転しました。</span><span class="sxs-lookup"><span data-stu-id="6897b-105">In fact, it reversed.</span></span> <span data-ttu-id="6897b-106">1 GHz のシングル コア ARM チップを搭載した携帯電話が登場し、サーバーのワークロードは VM に移行されました。</span><span class="sxs-lookup"><span data-stu-id="6897b-106">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="6897b-107">ユーザーは引き続き応答速度の速い UI を望み、ビジネス オーナーは業務の拡大に合わせて拡張できるサーバーを必要としています。</span><span class="sxs-lookup"><span data-stu-id="6897b-107">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="6897b-108">モバイルおよびクラウドへの移行が進み、インターネット接続ユーザーが 30 億人を超えた結果、新しいソフトウェア パターンが生まれました。</span><span class="sxs-lookup"><span data-stu-id="6897b-108">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span>

- <span data-ttu-id="6897b-109">クライアント アプリケーションには、アプリ ストアの高い評価と共に、常時オンで常時接続であること、そのうえでユーザーの操作 (タッチなど) に対する応答性を常に維持することが期待されます。</span><span class="sxs-lookup"><span data-stu-id="6897b-109">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
- <span data-ttu-id="6897b-110">サービスは、適切にスケールアップおよびスケールダウンしてトラフィックの急増に対処することが期待されます。</span><span class="sxs-lookup"><span data-stu-id="6897b-110">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span>

<span data-ttu-id="6897b-111">非同期プログラミングは、ブロッキング I/O と複数コアでの同時操作の処理を容易にする鍵となる手法です。</span><span class="sxs-lookup"><span data-stu-id="6897b-111">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="6897b-112">.NET では、C#、Visual Basic、F# で簡単に使用できる言語レベルの非同期プログラミング モデルにより、アプリやサービスの応答性と弾力性を実現する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="6897b-112">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, Visual Basic, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="6897b-113">非同期コードを記述する理由</span><span class="sxs-lookup"><span data-stu-id="6897b-113">Why Write Async Code?</span></span>

<span data-ttu-id="6897b-114">最新アプリでは、ファイルおよびネットワーク I/O を広範囲に使用します。</span><span class="sxs-lookup"><span data-stu-id="6897b-114">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="6897b-115">従来の I/O API は既定によりブロックし、困難なパターンを学習して使用しない限り、結果的にユーザー エクスペリエンスとハードウェア使用率が不適切になっていました。</span><span class="sxs-lookup"><span data-stu-id="6897b-115">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="6897b-116">このモデルを逆転させたのがタスクベースの非同期 API と言語レベルの非同期プログラミング モデルであり、非同期実行が既定になりました。これに関して新たに学習する必要がある概念はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="6897b-116">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="6897b-117">非同期コードの特性は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6897b-117">Async code has the following characteristics:</span></span>

- <span data-ttu-id="6897b-118">スレッドを生成することによって、I/O 要求が戻るのを待つ間により多くのサーバー要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="6897b-118">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
- <span data-ttu-id="6897b-119">I/O 要求の待機中に UI 操作に対してスレッドを生成し、実行時間の長い作業を他の CPU コアに移行することによって、UI の応答性を高めます。</span><span class="sxs-lookup"><span data-stu-id="6897b-119">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
- <span data-ttu-id="6897b-120">新しい .NET API の多くは非同期です。</span><span class="sxs-lookup"><span data-stu-id="6897b-120">Many of the newer .NET APIs are asynchronous.</span></span>
- <span data-ttu-id="6897b-121">.NET で非同期コードを記述するのはとても簡単です。</span><span class="sxs-lookup"><span data-stu-id="6897b-121">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="6897b-122">次の操作</span><span class="sxs-lookup"><span data-stu-id="6897b-122">What's next?</span></span>

<span data-ttu-id="6897b-123">詳しくは、「[非同期の詳細](async-in-depth.md)」トピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6897b-123">For more information, see the [Async in depth](async-in-depth.md) topic.</span></span>

<span data-ttu-id="6897b-124">「[非同期プログラミングのパターン](asynchronous-programming-patterns/index.md)」トピックでは、.NET でサポートされている 3 種類の非同期プログラミング パターンの概要が説明されています。</span><span class="sxs-lookup"><span data-stu-id="6897b-124">The [Asynchronous Programming Patterns](asynchronous-programming-patterns/index.md) topic provides an overview of the three asynchronous programming patterns supported in .NET:</span></span>  
  
- <span data-ttu-id="6897b-125">[非同期プログラミング モデル (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (レガシ)</span><span class="sxs-lookup"><span data-stu-id="6897b-125">[Asynchronous Programming Model (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
- <span data-ttu-id="6897b-126">[イベント ベースの非同期パターン (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (レガシ)</span><span class="sxs-lookup"><span data-stu-id="6897b-126">[Event-based Asynchronous Pattern (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
- <span data-ttu-id="6897b-127">[タスク ベースの非同期パターン (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (新規の開発に推奨)</span><span class="sxs-lookup"><span data-stu-id="6897b-127">[Task-based Asynchronous Pattern (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  

<span data-ttu-id="6897b-128">推奨されるタスク ベースのプログラミング モデルについて詳しくは、「[タスク ベースの非同期プログラミング](parallel-programming/task-based-asynchronous-programming.md)」トピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6897b-128">For more information about recommended task-based programming model, see the [Task-based asynchronous programming](parallel-programming/task-based-asynchronous-programming.md) topic.</span></span>
