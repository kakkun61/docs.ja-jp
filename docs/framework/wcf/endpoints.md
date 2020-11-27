---
title: Windows Communication Foundation エンドポイント
ms.date: 03/30/2017
helpviewer_keywords:
- endpoints [WCF]
ms.assetid: bd0c310f-dd9f-4081-9be2-3db5909850b6
ms.openlocfilehash: d3281ac648ecb43ce5248fe86b6da1d268e382f8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262152"
---
# <a name="windows-communication-foundation-endpoints"></a><span data-ttu-id="21b65-102">Windows Communication Foundation エンドポイント</span><span class="sxs-lookup"><span data-stu-id="21b65-102">Windows Communication Foundation Endpoints</span></span>

<span data-ttu-id="21b65-103">Windows Communication Foundation (WCF) サービスとの通信はすべて、サービスの *エンドポイント* を介して行われます。</span><span class="sxs-lookup"><span data-stu-id="21b65-103">All communication with a Windows Communication Foundation (WCF) service occurs through the *endpoints* of the service.</span></span> <span data-ttu-id="21b65-104">エンドポイントは、クライアントが WCF サービスによって提供される機能にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="21b65-104">Endpoints provide clients access to the functionality that a WCF service offers.</span></span>  
  
 <span data-ttu-id="21b65-105">エンドポイントを作成する方法の概要については、「 [エンドポイントの作成の概要](endpoint-creation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21b65-105">For an overview about how to create an endpoint, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="21b65-106">エンドポイントは次の要素から成ります。</span><span class="sxs-lookup"><span data-stu-id="21b65-106">Each endpoint contains:</span></span>  
  
- <span data-ttu-id="21b65-107">そのエンドポイントの場所を示すアドレス。</span><span class="sxs-lookup"><span data-stu-id="21b65-107">An address that indicates where to find the endpoint.</span></span>  
  
- <span data-ttu-id="21b65-108">クライアントがエンドポイントと通信する方法を指定するバインディング。</span><span class="sxs-lookup"><span data-stu-id="21b65-108">A binding that specifies how a client can communicate with the endpoint.</span></span>  
  
- <span data-ttu-id="21b65-109">利用可能なメソッドを指定するためのコントラクト。</span><span class="sxs-lookup"><span data-stu-id="21b65-109">A contract that identifies the methods available.</span></span>  
  
 <span data-ttu-id="21b65-110">エンドポイントを構成する個々の要素を指定する方法については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21b65-110">For descriptions about how to specify these individual parts of an endpoint, see:</span></span>  
  
- [<span data-ttu-id="21b65-111">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="21b65-111">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
  
- [<span data-ttu-id="21b65-112">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="21b65-112">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)  
  
- [<span data-ttu-id="21b65-113">サービスの設計と実装</span><span class="sxs-lookup"><span data-stu-id="21b65-113">Designing and Implementing Services</span></span>](designing-and-implementing-services.md)  
  
## <a name="in-this-section"></a><span data-ttu-id="21b65-114">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="21b65-114">In This Section</span></span>  

 [<span data-ttu-id="21b65-115">エンドポイントの作成の概要</span><span class="sxs-lookup"><span data-stu-id="21b65-115">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)  
 <span data-ttu-id="21b65-116">エンドポイントの構造を説明し、構成やコード内にエンドポイントを定義する方法と、ランタイムによって提供される既定のエンドポイント、バインディング、および動作の使用方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="21b65-116">Describes the structure of an endpoint and outlines how to define an endpoint in configuration and in code, as well as how to use the default endpoints, bindings, and behaviors provided by the runtime.</span></span>  
  
 [<span data-ttu-id="21b65-117">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="21b65-117">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)  
 <span data-ttu-id="21b65-118">WCF サービスとの通信がエンドポイントを介してどのように行われるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="21b65-118">Describes how communication with a WCF service occurs through endpoints.</span></span>  
  
 [<span data-ttu-id="21b65-119">方法: 構成にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="21b65-119">How to: Create a Service Endpoint in Configuration</span></span>](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 <span data-ttu-id="21b65-120">構成でサービス エンドポイントを作成する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="21b65-120">Demonstrates how to create a service endpoint in configuration.</span></span>  
  
 [<span data-ttu-id="21b65-121">方法: コード内にサービス エンドポイントを作成する</span><span class="sxs-lookup"><span data-stu-id="21b65-121">How to: Create a Service Endpoint in Code</span></span>](./feature-details/how-to-create-a-service-endpoint-in-code.md)  
 <span data-ttu-id="21b65-122">コードでサービス エンドポイントを作成する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="21b65-122">Demonstrates how to create a service endpoint in code.</span></span>  
  
 [<span data-ttu-id="21b65-123">メタデータ エンドポイントを公開する</span><span class="sxs-lookup"><span data-stu-id="21b65-123">Publishing Metadata Endpoints</span></span>](publishing-metadata-endpoints.md)  
 <span data-ttu-id="21b65-124">構成およびコードでメタデータ エンドポイントを公開することによりってメタデータを公開する方法を解説します。</span><span class="sxs-lookup"><span data-stu-id="21b65-124">Demonstrates how to publish metadata by publishing metadata endpoints in configuration and in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="21b65-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="21b65-125">Reference</span></span>  

 <xref:System.ServiceModel.EndpointAddress>  
  
## <a name="related-sections"></a><span data-ttu-id="21b65-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="21b65-126">Related Sections</span></span>  

 [<span data-ttu-id="21b65-127">基本的なプログラミング ライフサイクル</span><span class="sxs-lookup"><span data-stu-id="21b65-127">Basic Programming Lifecycle</span></span>](basic-programming-lifecycle.md)
