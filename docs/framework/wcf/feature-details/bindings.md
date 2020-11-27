---
title: Windows Communication Foundation バインディング
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], bindings
- Windows Communication Foundation [WCF], bindings
- bindings [WCF]
ms.assetid: 83639133-89f7-43f0-b4ef-8d9e57c08d25
ms.openlocfilehash: 50c430489144589f6deb0930aeb3006bcb7efe8c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262100"
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="22848-102">Windows Communication Foundation バインディング</span><span class="sxs-lookup"><span data-stu-id="22848-102">Windows Communication Foundation Bindings</span></span>

<span data-ttu-id="22848-103">Windows Communication Foundation (WCF) は、アプリケーション用のソフトウェアが他のソフトウェアと通信する方法からどのように記述されるかを分離します。</span><span class="sxs-lookup"><span data-stu-id="22848-103">Windows Communication Foundation (WCF) separates how the software for an application is written from how it communicates with other software.</span></span> <span data-ttu-id="22848-104">バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="22848-104">Bindings are used to specify the transport, encoding, and protocol details required for clients and services to communicate with each other.</span></span> <span data-ttu-id="22848-105">WCF はバインディングを使用してエンドポイントの基になるワイヤ表現を生成するため、バインディングの詳細のほとんどは、通信しているパーティによって合意されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="22848-105">WCF uses bindings to generate the underlying wire representation of the endpoint, so most of the binding details must be agreed upon by the parties that are communicating.</span></span> <span data-ttu-id="22848-106">これを実現する最も簡単な方法は、サービスのクライアントがサービスのエンドポイントと同じバインディングを使用することです。</span><span class="sxs-lookup"><span data-stu-id="22848-106">The easiest way to achieve this is for clients of a service to use the same binding that the endpoint for the service uses.</span></span> <span data-ttu-id="22848-107">これを行う方法の詳細については、「バインドを使用した [サービスとクライアントの構成](../using-bindings-to-configure-services-and-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22848-107">For more information about how to do this, see [Using Bindings to Configure Services and Clients](../using-bindings-to-configure-services-and-clients.md).</span></span>  
  
 <span data-ttu-id="22848-108">バインディングは、バインド要素のコレクションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="22848-108">A binding is made up of a collection of binding elements.</span></span> <span data-ttu-id="22848-109">各要素は、エンドポイントがクライアントと通信する方法の一部分を記述します。</span><span class="sxs-lookup"><span data-stu-id="22848-109">Each element describes some aspect of how the endpoint communicates with clients.</span></span> <span data-ttu-id="22848-110">バインディングには、1 つ以上のトランスポート バインド要素、1 つ以上のメッセージ エンコーディング バインド要素 (既定では、トランスポート バインド要素によって提供されます)、および任意の数の他のプロトコル バインド要素が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="22848-110">A binding must include at least one transport binding element, at least one message-encoding binding element (which the transport binding element can provide by default), and any number of other protocol binding elements.</span></span> <span data-ttu-id="22848-111">このように、ランタイムをビルドするプロセスでは、各バインド要素からランタイムにコードを提供できます。</span><span class="sxs-lookup"><span data-stu-id="22848-111">The process that builds a runtime out of this description allows each binding element to contribute code to that runtime.</span></span>  
  
 <span data-ttu-id="22848-112">WCF には、バインド要素の共通選択を含むバインディングが用意されています。</span><span class="sxs-lookup"><span data-stu-id="22848-112">WCF provides bindings that contain common selections of binding elements.</span></span> <span data-ttu-id="22848-113">これらのバインディングは、既定の設定で使用することも、ユーザーの要件に応じて既定値を変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="22848-113">These can be used with their default settings or you can modify those default values according to user requirements.</span></span> <span data-ttu-id="22848-114">これらのシステム指定のバインディングには、バインド要素およびその設定を直接制御できるプロパティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="22848-114">These system-provided bindings have properties that allow direct control over the binding elements and their settings.</span></span> <span data-ttu-id="22848-115">また、バインディングの各バージョンに独自の名前を付けることで、複数のバージョンを同時に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="22848-115">You can also easily work side-by-side with multiple versions of a binding by giving each version of the binding its own name.</span></span> <span data-ttu-id="22848-116">詳細については、「 [System-Provided バインドの構成](configuring-system-provided-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22848-116">For details, see [Configuring System-Provided Bindings](configuring-system-provided-bindings.md).</span></span>  
  
 <span data-ttu-id="22848-117">システム指定のバインディングに用意されていないバインド要素のコレクションが必要になった場合には、その必要なバインド要素のコレクションで構成されるカスタム バインドを作成できます。</span><span class="sxs-lookup"><span data-stu-id="22848-117">If you need a collection of binding elements not provided by one of these system-provided bindings, you can create a custom binding that consists of the collection of binding elements required.</span></span> <span data-ttu-id="22848-118">このようなカスタム バインドは簡単に作成でき、新しいクラスも必要ありませんが、バインド要素およびその設定を制御するためのプロパティは提供されません。</span><span class="sxs-lookup"><span data-stu-id="22848-118">These custom bindings are easy to create and do not require a new class, but they do not provide properties for controlling the binding elements or their settings.</span></span> <span data-ttu-id="22848-119">バインド要素へのアクセスと設定の変更は、バインド要素を含むコレクションを通じて行います。</span><span class="sxs-lookup"><span data-stu-id="22848-119">You can access the binding elements and modify their settings through the collection that contains them.</span></span> <span data-ttu-id="22848-120">詳細については、「 [カスタムバインド](../extending/custom-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22848-120">For details, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22848-121">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="22848-121">In This Section</span></span>  

 [<span data-ttu-id="22848-122">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="22848-122">Configuring System-Provided Bindings</span></span>](configuring-system-provided-bindings.md)  
 <span data-ttu-id="22848-123">一般的なシナリオをサポートするために WCF が提供するバインディングを使用および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22848-123">Describes how to use and modify the bindings that WCF provides to support common scenarios.</span></span>  
  
 [<span data-ttu-id="22848-124">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="22848-124">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="22848-125">サービスとクライアントの Windows Communication Foundation (WCF) バインドをコード内で強制的に定義し、構成を使用して宣言する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="22848-125">Describes how to define Windows Communication Foundation (WCF) bindings for services and clients imperatively in code and declaratively using configuration.</span></span>  
  
 [<span data-ttu-id="22848-126">カスタム バインディング</span><span class="sxs-lookup"><span data-stu-id="22848-126">Custom Bindings</span></span>](../extending/custom-bindings.md)  
 <span data-ttu-id="22848-127"><xref:System.ServiceModel.Channels.CustomBinding> の概要と使用する状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="22848-127">Describes what a <xref:System.ServiceModel.Channels.CustomBinding> is and when it is used.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="22848-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="22848-128">Reference</span></span>  

 <xref:System.ServiceModel.Channels.Binding>  
  
 <xref:System.ServiceModel.Channels.BindingElement>  
  
 <xref:System.ServiceModel.Channels.CustomBinding>  
  
## <a name="related-sections"></a><span data-ttu-id="22848-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="22848-129">Related Sections</span></span>  

 [<span data-ttu-id="22848-130">バインディングの拡張</span><span class="sxs-lookup"><span data-stu-id="22848-130">Extending Bindings</span></span>](../extending/extending-bindings.md)
