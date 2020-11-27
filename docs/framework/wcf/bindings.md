---
title: Windows Communication Foundation バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
ms.openlocfilehash: 3ce861404e59d24c2b1e0b548026bc795157fffe
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272372"
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="86a8c-102">Windows Communication Foundation バインディング</span><span class="sxs-lookup"><span data-stu-id="86a8c-102">Windows Communication Foundation Bindings</span></span>

<span data-ttu-id="86a8c-103">バインディングは、Windows Communication Foundation (WCF) サービスエンドポイントが他のエンドポイントと通信する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="86a8c-103">Bindings specify how a Windows Communication Foundation (WCF) service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="86a8c-104">バインディングでは、まず、使用するトランスポート (HTTP や TCP など) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86a8c-104">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="86a8c-105">セキュリティやトランザクションのサポートなど、その他の特性もバインディングによって設定できます。</span><span class="sxs-lookup"><span data-stu-id="86a8c-105">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86a8c-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="86a8c-106">In This Section</span></span>  

 [<span data-ttu-id="86a8c-107">WCF のバインディングの概要</span><span class="sxs-lookup"><span data-stu-id="86a8c-107">WCF Bindings Overview</span></span>](bindings-overview.md)  
 <span data-ttu-id="86a8c-108">WCF バインディングの概要、システムが提供するバインディング、およびそれらを定義または変更する方法の概要。</span><span class="sxs-lookup"><span data-stu-id="86a8c-108">Overview of what WCF bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="86a8c-109">システム標準のバインディング</span><span class="sxs-lookup"><span data-stu-id="86a8c-109">System-Provided Bindings</span></span>](system-provided-bindings.md)  
 <span data-ttu-id="86a8c-110">WCF に含まれるバインディングの一覧。</span><span class="sxs-lookup"><span data-stu-id="86a8c-110">A list of bindings included with WCF.</span></span> <span data-ttu-id="86a8c-111">これらのバインディングは、ほとんどのセキュリティ要件およびメッセージ パターン要件を満たします。</span><span class="sxs-lookup"><span data-stu-id="86a8c-111">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="86a8c-112">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="86a8c-112">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="86a8c-113">WCF バインディングには、クライアントがサービスエンドポイントに接続するために使用する必要がある重要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="86a8c-113">A WCF binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="86a8c-114">サービスのバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="86a8c-114">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="86a8c-115">管理者やインストール担当者は、構成を使用してサービス エンドポイントのバインディングをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="86a8c-115">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="86a8c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="86a8c-116">Reference</span></span>  

 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="86a8c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="86a8c-117">Related Sections</span></span>  

 [<span data-ttu-id="86a8c-118">エンドポイント:アドレス、バインディング、およびコントラクト</span><span class="sxs-lookup"><span data-stu-id="86a8c-118">Endpoints: Addresses, Bindings, and Contracts</span></span>](./feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="86a8c-119">バインド</span><span class="sxs-lookup"><span data-stu-id="86a8c-119">Bindings</span></span>](./feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="86a8c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="86a8c-120">See also</span></span>

- [<span data-ttu-id="86a8c-121">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="86a8c-121">Custom Bindings</span></span>](./extending/custom-bindings.md)
