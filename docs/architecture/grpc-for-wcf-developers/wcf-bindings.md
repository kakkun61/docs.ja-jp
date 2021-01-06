---
title: Wcf のバインディングとトランスポート-WCF 開発者向け gRPC
description: さまざまな WCF バインドとトランスポートが gRPC とどのように比較されるかについて説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 7a50e3e4468d86a6140066502a765818119642d4
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938508"
---
# <a name="wcf-bindings-and-transports"></a><span data-ttu-id="66e07-103">WCF のバインドとトランスポート</span><span class="sxs-lookup"><span data-stu-id="66e07-103">WCF bindings and transports</span></span>

<span data-ttu-id="66e07-104">Windows Communication Foundation (WCF) には、さまざまなネットワークプロトコル、ワイヤ形式、およびその他の実装の詳細を指定する組み込み *バインド* があります。</span><span class="sxs-lookup"><span data-stu-id="66e07-104">Windows Communication Foundation (WCF) has built-in *bindings* that specify different network protocols, wire formats, and other implementation details.</span></span> <span data-ttu-id="66e07-105">gRPC には、ネットワークプロトコルとワイヤ形式が1つだけあります。</span><span class="sxs-lookup"><span data-stu-id="66e07-105">gRPC effectively has just one network protocol and one wire format.</span></span> <span data-ttu-id="66e07-106">(技術的にはワイヤ形式をカスタマイズ *でき* ますが、これはこの書籍の範囲を超えています)。GRPC はほとんどの場合、最適なソリューションを提供していることがわかっているでしょう。</span><span class="sxs-lookup"><span data-stu-id="66e07-106">(Technically you *can* customize the wire format, but that's beyond the scope of this book.) You're likely to discover that gRPC offers the best solution in most cases.</span></span>

<span data-ttu-id="66e07-107">ここでは、最も関連性の高い WCF バインドについて簡単に説明し、gRPC で同等のバインドと比較する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="66e07-107">What follows is a short discussion about the most relevant WCF bindings and how they compare to their equivalents in gRPC.</span></span>

## <a name="nettcp"></a><span data-ttu-id="66e07-108">Wcf-nettcp</span><span class="sxs-lookup"><span data-stu-id="66e07-108">NetTCP</span></span>

<span data-ttu-id="66e07-109">WCF の NetTCP バインディングを使用すると、永続的な接続、小さいメッセージ、および双方向のメッセージングを実現できます。</span><span class="sxs-lookup"><span data-stu-id="66e07-109">WCF's NetTCP binding allows for persistent connections, small messages, and two-way messaging.</span></span> <span data-ttu-id="66e07-110">ただし、.NET クライアントとサーバーの間でのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="66e07-110">But it works only between .NET clients and servers.</span></span> <span data-ttu-id="66e07-111">gRPC では同じ機能を使用できますが、複数のプログラミング言語とプラットフォームでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66e07-111">gRPC allows the same functionality but is supported across multiple programming languages and platforms.</span></span>

<span data-ttu-id="66e07-112">gRPC には WCF の NetTCP バインドの多くの機能がありますが、常に同じ方法で実装されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="66e07-112">gRPC has many features of WCF's NetTCP binding, but they're not always implemented in the same way.</span></span> <span data-ttu-id="66e07-113">たとえば、WCF では、暗号化は構成によって制御され、フレームワークで処理されます。</span><span class="sxs-lookup"><span data-stu-id="66e07-113">For example, in WCF, encryption is controlled through configuration and handled in the framework.</span></span> <span data-ttu-id="66e07-114">GRPC では、TLS 経由で HTTP/2 を介して接続レベルで暗号化が行われます。</span><span class="sxs-lookup"><span data-stu-id="66e07-114">In gRPC, encryption is achieved at the connection level through HTTP/2 over TLS.</span></span>

## <a name="http"></a><span data-ttu-id="66e07-115">HTTP</span><span class="sxs-lookup"><span data-stu-id="66e07-115">HTTP</span></span>

<span data-ttu-id="66e07-116">通常、BasicHttpBinding という WCF バインディングはテキストベースで、ワイヤ形式として SOAP を使用します。</span><span class="sxs-lookup"><span data-stu-id="66e07-116">The WCF binding called BasicHttpBinding is usually text-based and uses SOAP as the wire format.</span></span> <span data-ttu-id="66e07-117">NetTCP バインドと比べて低速です。</span><span class="sxs-lookup"><span data-stu-id="66e07-117">It's slow compared to the NetTCP binding.</span></span> <span data-ttu-id="66e07-118">クロスプラットフォームの相互運用性、またはインターネットインフラストラクチャ経由の接続を提供するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="66e07-118">It's used to provide cross-platform interoperability, or connection over internet infrastructure.</span></span>

<span data-ttu-id="66e07-119">GRPC では、メッセージのバイナリ Protobuf ワイヤ形式を使用して、基になるトランスポート層として HTTP/2 を使用します。</span><span class="sxs-lookup"><span data-stu-id="66e07-119">The equivalent in gRPC uses HTTP/2 as the underlying transport layer with the binary Protobuf wire format for messages.</span></span> <span data-ttu-id="66e07-120">これにより、すべての最新のプログラミング言語とフレームワークを使用して、NetTCP サービスレベルのパフォーマンスと完全なクロスプラットフォームの相互運用性を実現できます。</span><span class="sxs-lookup"><span data-stu-id="66e07-120">So it can offer performance at the NetTCP service level and full cross-platform interoperability with all modern programming languages and frameworks.</span></span>

## <a name="named-pipes"></a><span data-ttu-id="66e07-121">名前付きパイプ</span><span class="sxs-lookup"><span data-stu-id="66e07-121">Named pipes</span></span>

<span data-ttu-id="66e07-122">WCF は、同じ物理マシン上のプロセス間の通信に使用する *名前付きパイプ* のバインドを提供しました。</span><span class="sxs-lookup"><span data-stu-id="66e07-122">WCF provided a *named pipes* binding for communication between processes on the same physical machine.</span></span> <span data-ttu-id="66e07-123">ASP.NET Core gRPC の最初のリリースでは、名前付きパイプはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="66e07-123">The first release of ASP.NET Core gRPC does not support named pipes.</span></span> <span data-ttu-id="66e07-124">名前付きパイプ (および Unix ドメインソケット) のクライアントとサーバーのサポートを追加することは、将来のリリースの目的です。</span><span class="sxs-lookup"><span data-stu-id="66e07-124">Adding client and server support for named pipes (and Unix domain sockets) is a goal for a future release.</span></span>

## <a name="msmq"></a><span data-ttu-id="66e07-125">MSMQ</span><span class="sxs-lookup"><span data-stu-id="66e07-125">MSMQ</span></span>

<span data-ttu-id="66e07-126">MSMQ は専用の Windows メッセージキューです。</span><span class="sxs-lookup"><span data-stu-id="66e07-126">MSMQ is a proprietary Windows message queue.</span></span> <span data-ttu-id="66e07-127">WCF による MSMQ へのバインドを使用すると、将来、いつでも処理される可能性があるクライアントからの "火災および忘れる" 要求を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="66e07-127">WCF's binding to MSMQ enables "fire and forget" requests from clients that might be processed at any time in the future.</span></span> <span data-ttu-id="66e07-128">gRPC では、メッセージキュー機能はネイティブには提供されません。</span><span class="sxs-lookup"><span data-stu-id="66e07-128">gRPC doesn't natively provide any message queue functionality.</span></span>

<span data-ttu-id="66e07-129">代替手段として、Azure Service Bus、RabbitMQ、Kafka などのメッセージングシステムを直接使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66e07-129">The best alternative is to directly use a messaging system like Azure Service Bus, RabbitMQ, or Kafka.</span></span> <span data-ttu-id="66e07-130">この機能は、クライアントがメッセージをキューに直接配置するか、メッセージをキューに入れる gRPC クライアントストリーミングサービスを使用して実装できます。</span><span class="sxs-lookup"><span data-stu-id="66e07-130">You can implement this functionality with the client placing messages directly onto the queue, or a gRPC client streaming service that enqueues the messages.</span></span>

## <a name="webhttpbinding"></a><span data-ttu-id="66e07-131">WebHttpBinding</span><span class="sxs-lookup"><span data-stu-id="66e07-131">WebHttpBinding</span></span>

<span data-ttu-id="66e07-132">WebHttpBinding (WCF REST とも呼ばれます) では、属性と属性を使用することに `WebGet` `WebInvoke` より、この動作があまり一般的ではないときに JSON を読み上げることができる RESTful api を開発できます。</span><span class="sxs-lookup"><span data-stu-id="66e07-132">WebHttpBinding (also known as WCF REST), with the `WebGet` and `WebInvoke` attributes, enabled you to develop RESTful APIs that could speak JSON at a time when this behavior was less common.</span></span> <span data-ttu-id="66e07-133">WCF REST でビルドされた RESTful API を使用している場合は、通常の ASP.NET Core MVC Web API アプリケーションに移行することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="66e07-133">If you have a RESTful API built with WCF REST, consider migrating it to a regular ASP.NET Core MVC Web API application.</span></span> <span data-ttu-id="66e07-134">この移行では、gRPC への変換と同じ機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="66e07-134">This migration would provide the same functionality as a conversion to gRPC.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="66e07-135">[前へ](wcf-endpoints-grpc-methods.md)
>[次へ](rpc-types.md)</span><span class="sxs-lookup"><span data-stu-id="66e07-135">[Previous](wcf-endpoints-grpc-methods.md)
[Next](rpc-types.md)</span></span>
