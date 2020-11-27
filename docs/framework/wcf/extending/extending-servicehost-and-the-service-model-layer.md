---
title: ServiceHost とサービス モデル レイヤーの拡張
ms.date: 03/30/2017
helpviewer_keywords:
- extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
ms.openlocfilehash: 184719f5c3e2e3830d7e1c9c69b73649b66fff34
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273036"
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="a30ee-102">ServiceHost とサービス モデル レイヤーの拡張</span><span class="sxs-lookup"><span data-stu-id="a30ee-102">Extending ServiceHost and the Service Model Layer</span></span>

<span data-ttu-id="a30ee-103">サービス モデル レイヤーには、基になるチャネルから受信メッセージを取得し、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信するという役割があります。</span><span class="sxs-lookup"><span data-stu-id="a30ee-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="a30ee-104">サービス モデル拡張は、クライアントやディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a30ee-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a30ee-105">In This Section</span></span>  

 [<span data-ttu-id="a30ee-106">クライアントの拡張</span><span class="sxs-lookup"><span data-stu-id="a30ee-106">Extending Clients</span></span>](extending-clients.md)  
 <span data-ttu-id="a30ee-107">クライアント ランタイムを途中受信して変更できるインターフェイス、およびクライアント アプリケーションのカスタム拡張を挿入できるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="a30ee-108">たとえば、カスタム クライアント メッセージ ログやカスタム メッセージ シリアル化などを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a30ee-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="a30ee-109">ディスパッチャーの拡張</span><span class="sxs-lookup"><span data-stu-id="a30ee-109">Extending Dispatchers</span></span>](extending-dispatchers.md)  
 <span data-ttu-id="a30ee-110">サービス ランタイムを途中受信して変更できるインターフェイス、およびサービス アプリケーションのカスタム拡張を挿入できるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="a30ee-111">たとえば、カスタム サービス ログ、サービス側でのメッセージ検証、カスタム ディスパッチなどを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a30ee-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="a30ee-112">拡張可能オブジェクト</span><span class="sxs-lookup"><span data-stu-id="a30ee-112">Extensible Objects</span></span>](extensible-objects.md)  
 <span data-ttu-id="a30ee-113">5 つの拡張可能オブジェクトと、<xref:System.ServiceModel.IExtensibleObject%601> パターンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="a30ee-114">拡張可能オブジェクト パターンは、既存のランタイム クラスに新しい機能を付加して拡張したり、オブジェクトに新しい状態を追加するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="a30ee-115">このようなオブジェクトを実際に拡張することにより、処理の段階に応じて、共通の拡張可能オブジェクトに定義された共有の状態や機能にアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="a30ee-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="a30ee-116">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="a30ee-116">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="a30ee-117">WCF ランタイムで設定を変更したり拡張機能を挿入したりするには、ビヘイビアーを使用します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-117">To change settings on or insert extensions in the WCF runtime, you use Behaviors.</span></span> <span data-ttu-id="a30ee-118">WCF には、調整機能、インスタンス化、およびサービスと操作に関するその他のさまざまな側面を制御するための、システムに実装済みの動作が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a30ee-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="a30ee-119">ここでは、独自のカスタム動作を作成し、プログラムおよび構成ファイルにより、作成したカスタム動作を使用できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="a30ee-120">ServiceHostFactory を使用したホストの拡張</span><span class="sxs-lookup"><span data-stu-id="a30ee-120">Extending Hosting Using ServiceHostFactory</span></span>](extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="a30ee-121"><xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> および <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> を拡張し、<xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> クラスを使用してホスト環境をカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a30ee-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a30ee-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a30ee-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a30ee-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a30ee-123">Related Sections</span></span>
