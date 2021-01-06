---
title: 暗号化とネットワークセキュリティ-WCF 開発者向けの gRPC
description: GRPC でのネットワークセキュリティと暗号化に関する注意事項
ms.date: 12/15/2020
ms.openlocfilehash: 0735158ed69ce425c4f00eed6c42689b888a1885
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938625"
---
# <a name="encryption-and-network-security"></a><span data-ttu-id="89b6f-103">暗号化とネットワークセキュリティ</span><span class="sxs-lookup"><span data-stu-id="89b6f-103">Encryption and network security</span></span>

<span data-ttu-id="89b6f-104">Windows Communication Foundation (WCF) のネットワークセキュリティモデルは広範で複雑です。</span><span class="sxs-lookup"><span data-stu-id="89b6f-104">The network security model for Windows Communication Foundation (WCF) is extensive and complex.</span></span> <span data-ttu-id="89b6f-105">これには、HTTPS または TLS over TCP を使用したトランスポートレベルのセキュリティと、個々のメッセージを暗号化するための WS-Security 仕様を使用したメッセージレベルのセキュリティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="89b6f-105">It includes transport-level security by using HTTPS or TLS-over-TCP, and message-level security by using the WS-Security specification to encrypt individual messages.</span></span>

<span data-ttu-id="89b6f-106">gRPC は、基盤となる HTTP/2 プロトコルにセキュリティで保護されたネットワークを残し、TLS 証明書を使用してセキュリティで保護することができます。</span><span class="sxs-lookup"><span data-stu-id="89b6f-106">gRPC leaves secure networking to the underlying HTTP/2 protocol, which you can secure by using TLS certificates.</span></span>

<span data-ttu-id="89b6f-107">Web ブラウザーは、HTTP/2 の TLS 接続を使用することを主張していますが、を含むほとんどのプログラム用クライアントです。NET は `HttpClient` 、暗号化されていない接続を介して HTTP/2 を使用できます。</span><span class="sxs-lookup"><span data-stu-id="89b6f-107">Web browsers insist on using TLS connections for HTTP/2, but most programmatic clients, including .NET's `HttpClient`, can use HTTP/2 over unencrypted connections.</span></span> <span data-ttu-id="89b6f-108">`HttpClient` 既定では暗号化が必要ですが、スイッチを使用してこの動作をオーバーライドでき <xref:System.AppContext> ます。</span><span class="sxs-lookup"><span data-stu-id="89b6f-108">`HttpClient` does require encryption by default, but you can override this behavior by using an <xref:System.AppContext> switch.</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

<span data-ttu-id="89b6f-109">パブリック Api の場合、TLS 接続を常に使用し、適切な SSL 機関からサービスに有効な証明書を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b6f-109">For public APIs, you should always use TLS connections, and provide valid certificates for your services from a proper SSL authority.</span></span> <span data-ttu-id="89b6f-110">この[暗号化](https://letsencrypt.org)は、無料の自動 SSL 証明書を提供します。ほとんどのホスティングインフラストラクチャでは、一般的なプラグインまたは拡張機能を使用して、標準のプラグインまたは拡張機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="89b6f-110">[LetsEncrypt](https://letsencrypt.org) provides free, automated SSL certificates, and most hosting infrastructure today supports the LetsEncrypt standard with common plug-ins or extensions.</span></span>

<span data-ttu-id="89b6f-111">企業ネットワーク全体の内部サービスについても、TLS を使用して、gRPC サービスとの間のネットワークトラフィックをセキュリティで保護することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89b6f-111">For internal services across a corporate network, you should still consider using TLS to secure network traffic to and from your gRPC services.</span></span>

<span data-ttu-id="89b6f-112">Kubernetes で実行されているサービス間で明示的な TLS を使用する必要がある場合は、クラスター内証明機関と、 [cert](https://docs.cert-manager.io/en/latest/)manager のような証明書マネージャーコントローラーの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="89b6f-112">If you need to use explicit TLS between services running in Kubernetes, consider using an in-cluster certificate authority and a certificate manager controller like [cert-manager](https://docs.cert-manager.io/en/latest/).</span></span> <span data-ttu-id="89b6f-113">展開時に、サービスに証明書を自動的に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="89b6f-113">You can then automatically assign certificates to services at deployment time.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="89b6f-114">[前へ](channel-credentials.md)
>[次へ](grpc-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="89b6f-114">[Previous](channel-credentials.md)
[Next](grpc-in-production.md)</span></span>
