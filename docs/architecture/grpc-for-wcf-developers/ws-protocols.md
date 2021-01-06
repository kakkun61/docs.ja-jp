---
title: WS-* プロトコル-WCF 開発者向け gRPC
description: WCF でサポートされている WS-* プロトコルと gRPC で使用可能な代替方法の確認
author: markrendle
ms.date: 12/15/2020
ms.openlocfilehash: d6fffdd5153c799c78ad949a3b16fa72e9612e43
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938482"
---
# <a name="ws--protocols"></a><span data-ttu-id="49fdd-103">\*プロトコル</span><span class="sxs-lookup"><span data-stu-id="49fdd-103">WS-\* protocols</span></span>

<span data-ttu-id="49fdd-104">Windows Communication Foundation (WCF) を使用する利点の1つは、既存の _WS \*_ 標準プロトコルの多くをサポートすることでした。</span><span class="sxs-lookup"><span data-stu-id="49fdd-104">One of the real benefits of working with Windows Communication Foundation (WCF) was that it supported many of the existing _WS-\*_ standard protocols.</span></span> <span data-ttu-id="49fdd-105">このセクションでは、gRPC によって同じプロトコルがどのように管理されるか \* について簡単に説明し、代替手段がない場合に使用できるオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="49fdd-105">This section will briefly cover how gRPC manages the same WS-\* protocols and discuss what options are available when there's no alternative.</span></span>

## <a name="metadata-exchange-ws-policy-ws-discovery-and-so-on"></a><span data-ttu-id="49fdd-106">メタデータ交換: WS-POLICY、WS-I Discovery など</span><span class="sxs-lookup"><span data-stu-id="49fdd-106">Metadata exchange: WS-Policy, WS-Discovery, and so on</span></span>

<span data-ttu-id="49fdd-107">SOAP サービスでは、Web サービス記述言語 (WSDL) スキーマドキュメントが、データ形式、操作、通信オプションなどの情報と共に公開されます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-107">SOAP services expose Web Services Description Language (WSDL) schema documents with information such as data formats, operations, or communication options.</span></span> <span data-ttu-id="49fdd-108">このスキーマを使用して、クライアントコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-108">You can use this schema to generate the client code.</span></span>

<span data-ttu-id="49fdd-109">gRPC は、サーバーとクライアントが同じファイルから生成された場合に最適に機能し `.proto` ますが、サーバーリフレクションオプションの拡張機能を使用すると、実行中のサーバーから動的な情報を公開することができます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-109">gRPC works best when servers and clients are generated from the same `.proto` files, but a Server Reflection optional extension does provide a way to expose dynamic information from a running server.</span></span> <span data-ttu-id="49fdd-110">詳細については、「 [grpc. リフレクション](https://nuget.org/packages/Grpc.Reflection) NuGet パッケージ」および「 [Grpc C# サーバーリフレクション](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49fdd-110">For more information, see the [Grpc.Reflection](https://nuget.org/packages/Grpc.Reflection) NuGet package and the [gRPC C# Server Reflection](https://github.com/grpc/grpc/blob/master/doc/csharp/server_reflection.md) article.</span></span>

<span data-ttu-id="49fdd-111">WS-Discovery プロトコルは、ローカルネットワーク上のサービスを検索するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-111">The WS-Discovery protocol is used to locate services on a local network.</span></span> <span data-ttu-id="49fdd-112">gRPC サービスは、DNS または Consul や飼育係などのサービスレジストリを使用して配置されます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-112">gRPC services are located through DNS or a service registry such as Consul or ZooKeeper.</span></span>

## <a name="security-ws-security-ws-federation-xml-encryption-and-so-on"></a><span data-ttu-id="49fdd-113">セキュリティ: WS-SECURITY、WS-FEDERATION、XML 暗号化、その他</span><span class="sxs-lookup"><span data-stu-id="49fdd-113">Security: WS-Security, WS-Federation, XML Encryption, and so on</span></span>

<span data-ttu-id="49fdd-114">セキュリティ、認証、および承認の詳細については、 [第6章](security.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49fdd-114">Security, authentication, and authorization are covered in much more detail in [chapter 6](security.md).</span></span> <span data-ttu-id="49fdd-115">ただし、WCF とは異なり、gRPC は WS-SECURITY、WS-FEDERATION、または XML 暗号化をサポートしていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="49fdd-115">But it's worth noting here that, unlike WCF, gRPC doesn't support WS-Security, WS-Federation, or XML Encryption.</span></span> <span data-ttu-id="49fdd-116">それでも、gRPC は優れたセキュリティを提供しています。</span><span class="sxs-lookup"><span data-stu-id="49fdd-116">Even so, gRPC provides excellent security.</span></span> <span data-ttu-id="49fdd-117">すべての gRPC ネットワークトラフィックは、HTTP/2 over TLS を使用しているときに自動的に暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-117">All gRPC network traffic is automatically encrypted when it's using HTTP/2 over TLS.</span></span> <span data-ttu-id="49fdd-118">相互クライアント/サーバー認証には X509 証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-118">You can use X509 certificates for mutual client/server authentication.</span></span>

## <a name="ws-reliablemessaging"></a><span data-ttu-id="49fdd-119">WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="49fdd-119">WS-ReliableMessaging</span></span>

<span data-ttu-id="49fdd-120">gRPC では、ws-reliablemessaging に相当するものは提供されません。</span><span class="sxs-lookup"><span data-stu-id="49fdd-120">gRPC does not provide an equivalent to WS-ReliableMessaging.</span></span> <span data-ttu-id="49fdd-121">再試行のセマンティクスは、コードで処理する必要があります [。たとえば](https://github.com/App-vNext/Polly)、通常のようなライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="49fdd-121">Retry semantics should be handled in code, possibly with a library like [Polly](https://github.com/App-vNext/Polly).</span></span> <span data-ttu-id="49fdd-122">Kubernetes または同様のオーケストレーション環境で実行されている場合、 [サービスメッシュ](service-mesh.md) はサービス間の信頼性の高いメッセージングを提供するのにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="49fdd-122">When you're running in Kubernetes or similar orchestration environments, [service meshes](service-mesh.md) can also help to provide reliable messaging between services.</span></span>

## <a name="ws-transaction-ws-coordination"></a><span data-ttu-id="49fdd-123">WS-ATOMICTRANSACTION、WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="49fdd-123">WS-Transaction, WS-Coordination</span></span>

<span data-ttu-id="49fdd-124">WCF による分散トランザクションの実装では、Microsoft 分散トランザクションコーディネーター (MSDTC) を使用します。</span><span class="sxs-lookup"><span data-stu-id="49fdd-124">WCF's implementation of distributed transactions uses Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="49fdd-125">これは、SQL Server、MSMQ、Windows ファイルシステムなど、特にサポートされているリソースマネージャーと連携します。</span><span class="sxs-lookup"><span data-stu-id="49fdd-125">It works with resource managers that specifically support it, like SQL Server, MSMQ, or Windows file systems.</span></span> <span data-ttu-id="49fdd-126">現在のマイクロサービスの世界では、使用されているテクノロジの範囲が広いため、まだ同等のものはありません。</span><span class="sxs-lookup"><span data-stu-id="49fdd-126">There's no equivalent yet in the modern microservices world, in part due to the wider range of technologies in use.</span></span> <span data-ttu-id="49fdd-127">トランザクションの詳細については、「 [付録 a](appendix.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49fdd-127">For a discussion of transactions, see [Appendix A](appendix.md).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="49fdd-128">[前へ](error-handling.md)
>[次へ](migrate-wcf-to-grpc.md)</span><span class="sxs-lookup"><span data-stu-id="49fdd-128">[Previous](error-handling.md)
[Next](migrate-wcf-to-grpc.md)</span></span>
