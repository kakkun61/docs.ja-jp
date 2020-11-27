---
title: WCF の拡張
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: b82dd4fb6a5b41a0160df8680fb1ba65d9a5bd33
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254598"
---
# <a name="extending-wcf"></a><span data-ttu-id="3842c-102">WCF の拡張</span><span class="sxs-lookup"><span data-stu-id="3842c-102">Extending WCF</span></span>

<span data-ttu-id="3842c-103">Windows Communication Foundation (WCF) を使用すると、実行時コンポーネントを変更および拡張して、サービスベースのアプリケーションを正確に制御および拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="3842c-103">Windows Communication Foundation (WCF) allows you to modify and extend run time components to precisely control and extend service-based applications.</span></span> <span data-ttu-id="3842c-104">このセクションのトピックでは、その拡張アーキテクチャについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="3842c-104">The topics in this section go in depth about the extensibility architecture.</span></span> <span data-ttu-id="3842c-105">基本的なプログラミングの詳細については、「 [基本的な WCF プログラミング](../basic-wcf-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3842c-105">For more information about basic programming, see [Basic WCF Programming](../basic-wcf-programming.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3842c-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3842c-106">In This Section</span></span>  

 [<span data-ttu-id="3842c-107">ServiceHost とサービス モデル レイヤーの拡張</span><span class="sxs-lookup"><span data-stu-id="3842c-107">Extending ServiceHost and the Service Model Layer</span></span>](extending-servicehost-and-the-service-model-layer.md)  
 <span data-ttu-id="3842c-108">サービス モデル レイヤーには、基になるチャネルから受信メッセージを取得し、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信するという役割があります。</span><span class="sxs-lookup"><span data-stu-id="3842c-108">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span>  <span data-ttu-id="3842c-109">サービス モデル拡張は、ディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。</span><span class="sxs-lookup"><span data-stu-id="3842c-109">Service model extensions modify or implement execution or communication behavior and features involving dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
 [<span data-ttu-id="3842c-110">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="3842c-110">Extending Bindings</span></span>](extending-bindings.md)  
 <span data-ttu-id="3842c-111">バインディングはエンドポイントに接続するために必要な通信の詳細設定を記述するオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="3842c-111">Bindings are objects that describe the communication details required to connect to an endpoint.</span></span> <span data-ttu-id="3842c-112">バインディングの拡張やカスタム バインドは、アプリケーションの各種機能をサポートするために必要なカスタム通信機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="3842c-112">Binding extensions or custom bindings implement custom communication functionality required to support application features.</span></span>  
  
 [<span data-ttu-id="3842c-113">チャネル レイヤーの拡張</span><span class="sxs-lookup"><span data-stu-id="3842c-113">Extending the Channel Layer</span></span>](extending-the-channel-layer.md)  
 <span data-ttu-id="3842c-114">チャネル レイヤーは、サービス モデル レイヤーより下に位置し、クライアントとサービス間のメッセージの交換を担います。</span><span class="sxs-lookup"><span data-stu-id="3842c-114">The channel layer sits beneath the service model layer and is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="3842c-115">チャネル拡張は、セキュリティなどの新しいプロトコル機能を実装できます。</span><span class="sxs-lookup"><span data-stu-id="3842c-115">Channel extensions can implement new protocol functionality, such as security.</span></span> <span data-ttu-id="3842c-116">また、SOAP メッセージを伝達する新しいネットワーク トランスポートの実装など、トランスポート機能も実装できます。</span><span class="sxs-lookup"><span data-stu-id="3842c-116">Channel extensions also transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
 [<span data-ttu-id="3842c-117">セキュリティの拡張</span><span class="sxs-lookup"><span data-stu-id="3842c-117">Extending Security</span></span>](extending-security.md)  
 <span data-ttu-id="3842c-118">WCF のセキュリティは、転送セキュリティ (整合性、機密性、および認証)、アクセス制御 (承認)、および監査で構成されます。</span><span class="sxs-lookup"><span data-stu-id="3842c-118">Security in WCF consists of transfer security (integrity, confidentiality, and authentication), access control (authorization) and auditing.</span></span> <span data-ttu-id="3842c-119">名前空間で見つかったクラス `IdentityModel` は、アクセス制御のために WCF によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="3842c-119">The classes found in the `IdentityModel` namespace are used by WCF for access control.</span></span> <span data-ttu-id="3842c-120">セキュリティ アーキテクチャを理解することによって、カスタムのアクセス制御システムに対応したカスタムのクレーム タイプを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3842c-120">Understanding the security architecture allows you to create custom claim types to accommodate custom access control systems.</span></span>  
  
 [<span data-ttu-id="3842c-121">メタデータ システムの拡張</span><span class="sxs-lookup"><span data-stu-id="3842c-121">Extending the Metadata System</span></span>](extending-the-metadata-system.md)  
 <span data-ttu-id="3842c-122">WCF メタデータシステムは、サービスベースのアプリケーションを実装するために必要なメタデータを表すクラスとインターフェイスのグループです。</span><span class="sxs-lookup"><span data-stu-id="3842c-122">The WCF metadata system is a group of classes and interfaces that represent metadata required to implement service-based applications.</span></span> <span data-ttu-id="3842c-123">クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。</span><span class="sxs-lookup"><span data-stu-id="3842c-123">Modify or extend the classes or implement and configure the interfaces to export and import custom metadata such as Web Services Description Language (WSDL) extensions or custom WS-PolicyAttachments assertions.</span></span>  
  
 [<span data-ttu-id="3842c-124">エンコーダーとシリアライザーの拡張</span><span class="sxs-lookup"><span data-stu-id="3842c-124">Extending Encoders and Serializers</span></span>](extending-encoders-and-serializers.md)  
 <span data-ttu-id="3842c-125">エンコーダーとシリアライザーは、データをある形式から別の形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="3842c-125">Encoders and serializers translate data from one form to another.</span></span> <span data-ttu-id="3842c-126">このセクションのトピックでは、提供されたクラスを特別な要件に合わせて拡張する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3842c-126">The topics in this section discuss how to extend the supplied classes to meet special requirements.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3842c-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="3842c-127">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a><span data-ttu-id="3842c-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="3842c-128">Related Sections</span></span>  

 [<span data-ttu-id="3842c-129">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="3842c-129">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="3842c-130">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="3842c-130">WCF Feature Details</span></span>](../feature-details/index.md)  
  
 [<span data-ttu-id="3842c-131">ガイドラインと最適な使用方法</span><span class="sxs-lookup"><span data-stu-id="3842c-131">Guidelines and Best Practices</span></span>](../guidelines-and-best-practices.md)
