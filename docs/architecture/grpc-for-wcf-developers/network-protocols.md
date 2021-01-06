---
title: ネットワークプロトコル-WCF 開発者向け gRPC
description: GRPC ネットワークプロトコルの概要について説明します。
ms.date: 09/02/2019
ms.openlocfilehash: 801d57c95aec748e5dcf667ca480775ff945b55c
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938560"
---
# <a name="network-protocols"></a><span data-ttu-id="ec163-103">ネットワーク プロトコル</span><span class="sxs-lookup"><span data-stu-id="ec163-103">Network protocols</span></span>

<span data-ttu-id="ec163-104">Windows Communication Foundation (WCF) とは異なり、gRPC はネットワークのベースとして HTTP/2 を使用します。</span><span class="sxs-lookup"><span data-stu-id="ec163-104">Unlike Windows Communication Foundation (WCF), gRPC uses HTTP/2 as a base for its networking.</span></span> <span data-ttu-id="ec163-105">このプロトコルは、HTTP/1.1 でのみ動作する WCF と SOAP よりも大きな利点を提供します。</span><span class="sxs-lookup"><span data-stu-id="ec163-105">This protocol offers significant advantages over WCF and SOAP, which operate only on HTTP/1.1.</span></span> <span data-ttu-id="ec163-106">GRPC の使用を検討している開発者にとって、HTTP/2 の代替手段がない場合は、HTTP/2 の詳細を確認し、gRPC を使用する利点をさらに特定することが理想的です。</span><span class="sxs-lookup"><span data-stu-id="ec163-106">For developers wanting to use gRPC, given that there's no alternative to HTTP/2, it would seem to be the ideal moment to explore HTTP/2 in more detail and identify additional benefits of using gRPC.</span></span>

<span data-ttu-id="ec163-107">2015の Internet Engineering Task Force によってリリースされた HTTP/2 は、既に Google によって使用されていた実験的な SPDY プロトコルから派生しました。</span><span class="sxs-lookup"><span data-stu-id="ec163-107">HTTP/2, released by Internet Engineering Task Force in 2015, was derived from the experimental SPDY protocol, which was already being used by Google.</span></span> <span data-ttu-id="ec163-108">これは、HTTP/1.1 よりも効率的で高速かつ安全になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="ec163-108">It was specifically designed to be more efficient, faster, and more secure than HTTP/1.1.</span></span>

## <a name="key-features-of-http2"></a><span data-ttu-id="ec163-109">HTTP/2 の主な機能</span><span class="sxs-lookup"><span data-stu-id="ec163-109">Key features of HTTP/2</span></span>

<span data-ttu-id="ec163-110">この一覧には、HTTP/2 の主な機能と利点がいくつか示されています。</span><span class="sxs-lookup"><span data-stu-id="ec163-110">This list shows some of the key features and advantages of HTTP/2:</span></span>

### <a name="binary-protocol"></a><span data-ttu-id="ec163-111">バイナリプロトコル</span><span class="sxs-lookup"><span data-stu-id="ec163-111">Binary protocol</span></span>

<span data-ttu-id="ec163-112">要求/応答サイクルでは、テキストコマンドが不要になりました。</span><span class="sxs-lookup"><span data-stu-id="ec163-112">Request/response cycles no longer need text commands.</span></span> <span data-ttu-id="ec163-113">このアクティビティは、コマンドの実装を簡素化し、高速化します。</span><span class="sxs-lookup"><span data-stu-id="ec163-113">This activity simplifies and speeds up the implementation of commands.</span></span> <span data-ttu-id="ec163-114">具体的には、データの解析が高速で、使用するメモリが少なくなるため、ネットワーク待機時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="ec163-114">Specifically, parsing data is faster and uses less memory, network latency is reduced with obvious related improvements to speed, and there's an overall better use of network resources.</span></span>

### <a name="streams"></a><span data-ttu-id="ec163-115">ストリーム</span><span class="sxs-lookup"><span data-stu-id="ec163-115">Streams</span></span>

<span data-ttu-id="ec163-116">ストリームを使用すると、送信側と受信側の間に有効期間の長い接続を作成し、複数のメッセージやフレームを非同期に送信することができます。</span><span class="sxs-lookup"><span data-stu-id="ec163-116">Streams allow you to create long-lived connections between sender and receiver, over which multiple messages or frames can be sent asynchronously.</span></span> <span data-ttu-id="ec163-117">複数のストリームは、1つの HTTP/2 接続で個別に操作できます。</span><span class="sxs-lookup"><span data-stu-id="ec163-117">Multiple streams can operate independently over a single HTTP/2 connection.</span></span>

### <a name="request-multiplexing-over-a-single-tcp-connection"></a><span data-ttu-id="ec163-118">1つの TCP 接続で多重化を要求する</span><span class="sxs-lookup"><span data-stu-id="ec163-118">Request multiplexing over a single TCP connection</span></span>

<span data-ttu-id="ec163-119">この機能は、HTTP/2 の最も重要なイノベーションの1つです。</span><span class="sxs-lookup"><span data-stu-id="ec163-119">This feature is one of the most important innovations of HTTP/2.</span></span> <span data-ttu-id="ec163-120">データに対して複数の並列要求が許可されるため、1台のサーバーから web ファイルを同時にダウンロードできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ec163-120">Because it allows multiple parallel requests for data, it's now possible to download web files concurrently from a single server.</span></span> <span data-ttu-id="ec163-121">Web サイトの読み込みが速くなり、最適化の必要性が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="ec163-121">Websites load faster, and the need for optimization is reduced.</span></span> <span data-ttu-id="ec163-122">先行 (ホル) ブロック。これは、前の要求が完了するまで送信されるのを待機する必要がある場合にも軽減されます (ただし、ホルブロックは TCP トランスポートレベルでも発生します)。</span><span class="sxs-lookup"><span data-stu-id="ec163-122">Head-of-line (HOL) blocking, where responses that are ready must wait to be sent until an earlier request is completed, is also mitigated (although HOL blocking can still occur at the TCP-transport level).</span></span>

### <a name="nettcp-like-performance-cross-platform"></a><span data-ttu-id="ec163-123">Net.tcp と同様のパフォーマンス、クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="ec163-123">Net.TCP-like performance, cross-platform</span></span>

<span data-ttu-id="ec163-124">基本的に、gRPC と HTTP/2 の組み合わせにより、開発者は、少なくとも WCF の Net.tcp バインドと同等の速度と効率が得られます。また、場合によっては、速度と効率が向上します。</span><span class="sxs-lookup"><span data-stu-id="ec163-124">Fundamentally, the combination of gRPC and HTTP/2 offers developers at least the equivalent speed and efficiency of Net.TCP bindings for WCF, and in some cases even greater speed and efficiency.</span></span> <span data-ttu-id="ec163-125">ただし、Net.tcp とは異なり、gRPC over HTTP/2 は .NET アプリケーションに制約されません。</span><span class="sxs-lookup"><span data-stu-id="ec163-125">But, unlike Net.TCP, gRPC over HTTP/2 isn't constrained to .NET applications.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ec163-126">[前へ](interface-definition-language.md)
>[次へ](why-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="ec163-126">[Previous](interface-definition-language.md)
[Next](why-grpc.md)</span></span>
