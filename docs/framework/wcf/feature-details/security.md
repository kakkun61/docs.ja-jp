---
title: Windows Communication Foundation セキュリティ
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, programming
- security [WCF]
- Windows Communication Foundation, security
ms.assetid: 7ea87fcb-dcfb-4a4a-8b03-6b954575d45b
ms.openlocfilehash: b92f1ad8bb00e9df8daf55da4d7a808420d909cf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254000"
---
# <a name="windows-communication-foundation-security"></a><span data-ttu-id="3e588-102">Windows Communication Foundation セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3e588-102">Windows Communication Foundation Security</span></span>

<span data-ttu-id="3e588-103">このセクションのトピックでは、Windows Communication Foundation (WCF) のセキュリティ機能と、それらを使用してメッセージをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-103">The topics in this section describe Windows Communication Foundation (WCF) security features and how to use them to help secure messages.</span></span>  
  
 <span data-ttu-id="3e588-104">Windows Server AppFabric とセキュリティの詳細については、「 [Windows Server appfabric のセキュリティモデル](/previous-versions/appfabric/ee677202(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3e588-104">For more information about Windows Server AppFabric and security, see [Security Model for Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3e588-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3e588-105">In This Section</span></span>  

 [<span data-ttu-id="3e588-106">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="3e588-106">Security Overview</span></span>](security-overview.md)  
 <span data-ttu-id="3e588-107">WCF のセキュリティ機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-107">Describes the security features in WCF.</span></span>  
  
 [<span data-ttu-id="3e588-108">セキュリティの概念</span><span class="sxs-lookup"><span data-stu-id="3e588-108">Security Concepts</span></span>](security-concepts.md)  
 <span data-ttu-id="3e588-109">WCF セキュリティで使用される基本的な用語と概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-109">Describes the basic terminology and concepts used in WCF security.</span></span>  
  
 [<span data-ttu-id="3e588-110">一般的なセキュリティ シナリオ</span><span class="sxs-lookup"><span data-stu-id="3e588-110">Common Security Scenarios</span></span>](common-security-scenarios.md)  
 <span data-ttu-id="3e588-111">WCF で構成できるシナリオとトポロジについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-111">Describes scenarios and topologies you can configure with WCF.</span></span>  
  
 [<span data-ttu-id="3e588-112">セキュリティ動作</span><span class="sxs-lookup"><span data-stu-id="3e588-112">Security Behaviors</span></span>](security-behaviors-in-wcf.md)  
 <span data-ttu-id="3e588-113">資格情報の設定など、セキュリティに影響する WCF の動作に関する概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-113">Provides an overview of WCF behaviors that affect security, such as setting credentials.</span></span>  
  
 [<span data-ttu-id="3e588-114">バインディングとセキュリティ</span><span class="sxs-lookup"><span data-stu-id="3e588-114">Bindings and Security</span></span>](bindings-and-security.md)  
 <span data-ttu-id="3e588-115">カスタム セキュリティ バインディングの作成方法を示すトピックなど、バインディングをセキュリティの観点から説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-115">A security-oriented view of the bindings, including topics that demonstrate how to create custom security bindings.</span></span>  
  
 [<span data-ttu-id="3e588-116">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="3e588-116">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
 <span data-ttu-id="3e588-117">WCF のセキュリティ機能を使用してメッセージをセキュリティで保護する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-117">Describes how to secure messages using WCF security features.</span></span>  
  
 [<span data-ttu-id="3e588-118">認証</span><span class="sxs-lookup"><span data-stu-id="3e588-118">Authentication</span></span>](authentication-in-wcf.md)  
 <span data-ttu-id="3e588-119">一般的な認証タスクを示します。</span><span class="sxs-lookup"><span data-stu-id="3e588-119">Demonstrates common authentication tasks.</span></span>  
  
 [<span data-ttu-id="3e588-120">承認</span><span class="sxs-lookup"><span data-stu-id="3e588-120">Authorization</span></span>](authorization-in-wcf.md)  
 <span data-ttu-id="3e588-121">セキュリティ実装を使用した一般的な承認シナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-121">Describes common authorization scenarios with security implementations.</span></span>  
  
 [<span data-ttu-id="3e588-122">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="3e588-122">Federation and Issued Tokens</span></span>](federation-and-issued-tokens.md)  
 <span data-ttu-id="3e588-123">フェデレーションの基本事項と、フェデレーション サーバーと通信するクライアントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-123">Describes the basics of federation and how to create clients that communicate with federated servers.</span></span>  
  
 [<span data-ttu-id="3e588-124">部分信頼</span><span class="sxs-lookup"><span data-stu-id="3e588-124">Partial Trust</span></span>](partial-trust.md)  
 <span data-ttu-id="3e588-125">部分的に信頼されている場合に、部分信頼シナリオと WCF 制限を実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-125">Describes how to run partially-trusted scenarios and WCF limitations when running partially trusted.</span></span>  
  
 [<span data-ttu-id="3e588-126">監査</span><span class="sxs-lookup"><span data-stu-id="3e588-126">Auditing</span></span>](auditing-security-events.md)  
 <span data-ttu-id="3e588-127">セキュリティ イベントを監査する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3e588-127">Describes how to audit security events.</span></span>  
  
 [<span data-ttu-id="3e588-128">セキュリティ ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="3e588-128">Security Guidance and Best Practices</span></span>](security-guidance-and-best-practices.md)  
 <span data-ttu-id="3e588-129">セキュリティで保護された WCF アプリケーションを作成するためのガイドライン。</span><span class="sxs-lookup"><span data-stu-id="3e588-129">Guidelines for creating secure WCF applications.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3e588-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e588-130">Reference</span></span>  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="3e588-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e588-131">Related Sections</span></span>  

 [<span data-ttu-id="3e588-132">WCF 機能の詳細</span><span class="sxs-lookup"><span data-stu-id="3e588-132">WCF Feature Details</span></span>](index.md)  
  
 [<span data-ttu-id="3e588-133">基本的な WCF プログラミング</span><span class="sxs-lookup"><span data-stu-id="3e588-133">Basic WCF Programming</span></span>](../basic-wcf-programming.md)  
  
 [<span data-ttu-id="3e588-134">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="3e588-134">Getting Started Tutorial</span></span>](../getting-started-tutorial.md)  
  
 [<span data-ttu-id="3e588-135">概念の概要</span><span class="sxs-lookup"><span data-stu-id="3e588-135">Conceptual Overview</span></span>](../conceptual-overview.md)  
  
## <a name="see-also"></a><span data-ttu-id="3e588-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="3e588-136">See also</span></span>

- [<span data-ttu-id="3e588-137">アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="3e588-137">Configuring Your Application</span></span>](../diagnostics/configuring-your-application.md)
