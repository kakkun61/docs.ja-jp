---
title: Windows Communication Foundation のトランザクションの概要
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 1486290241fdb40d415278c4a01738aa711e2182
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261476"
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="cfdcb-102">Windows Communication Foundation のトランザクションの概要</span><span class="sxs-lookup"><span data-stu-id="cfdcb-102">Windows Communication Foundation Transactions Overview</span></span>

<span data-ttu-id="cfdcb-103">トランザクションを使用すると、一連の処理や操作を 1 つの不可分の実行単位にグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="cfdcb-104">トランザクションとは、次の性質を持つ操作のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-104">A transaction is a collection of operations with the following properties:</span></span>  
  
- <span data-ttu-id="cfdcb-105">原子性。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-105">Atomicity.</span></span> <span data-ttu-id="cfdcb-106">特定のトランザクションの下で完了したすべての更新は、コミットされて永続的に格納されるか、すべて中止されて前の状態にロールバックされるかのどちらかになります。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
- <span data-ttu-id="cfdcb-107">一貫性。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-107">Consistency.</span></span> <span data-ttu-id="cfdcb-108">トランザクション下で行う変更は、一貫性のある状態から別の一貫性のある状態への変換を表します。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="cfdcb-109">たとえば、当座預金から普通預金への振り替えトランザクションでは、全体の預金残高は変更されません。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
- <span data-ttu-id="cfdcb-110">分離。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-110">Isolation.</span></span> <span data-ttu-id="cfdcb-111">トランザクションが他の同時実行されているトランザクションに属する確定されていない変更を監視することがなくなります。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="cfdcb-112">分離により、コンカレンシーの抽象概念が提供され、1 つのトランザクションが別のトランザクションの実行に予期しない影響を与える可能性がなくなります。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
- <span data-ttu-id="cfdcb-113">持続性。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-113">Durability.</span></span> <span data-ttu-id="cfdcb-114">マネージド リソース (データベース レコードなど) に対して 1 度コミットされた更新は、障害に直面しても永続的に残ります。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 <span data-ttu-id="cfdcb-115">Windows Communication Foundation (WCF) には、Web サービスアプリケーションで分散トランザクションを作成するための豊富な機能セットが用意されています。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-115">Windows Communication Foundation (WCF) provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 <span data-ttu-id="cfdcb-116">WCF は、WS-AtomicTransaction (WS-AT) プロトコルのサポートを実装します。これにより、WCF アプリケーションは、サードパーティのテクノロジを使用して構築された相互運用可能な Web サービスなど、相互運用可能なアプリケーションにトランザクションをフローさせることができます。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-116">WCF implements support for the WS-AtomicTransaction (WS-AT) protocol that enables WCF applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> <span data-ttu-id="cfdcb-117">また、WCF では、OLE トランザクションプロトコルのサポートも実装しています。これは、トランザクションフローを有効にする相互運用機能が不要なシナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-117">WCF also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="cfdcb-118">アプリケーション構成ファイルを使用してバインディングを構成し、トランザクション フローを有効にしたり無効にしたりできます。また、バインディングに目的のトランザクション プロトコルを設定できます。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="cfdcb-119">さらに、構成ファイルを使用してサービス レベルでのトランザクションのタイムアウトを設定できます。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> <span data-ttu-id="cfdcb-120">詳細については、「 [トランザクションフローの有効化](enabling-transaction-flow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-120">For more information, see [Enabling Transaction Flow](enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="cfdcb-121"><xref:System.ServiceModel> 名前空間のトランザクション属性で次の設定が行えます。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
- <span data-ttu-id="cfdcb-122"><xref:System.ServiceModel.ServiceBehaviorAttribute> 属性を使用して、トランザクションのタイムアウトと分離レベルのフィルター処理を構成する。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="cfdcb-123"><xref:System.ServiceModel.OperationBehaviorAttribute> 属性を使用して、トランザクション機能を有効にし、トランザクションの完了動作を構成する。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
- <span data-ttu-id="cfdcb-124">コントラクト メソッドで <xref:System.ServiceModel.ServiceContractAttribute> 属性と <xref:System.ServiceModel.OperationContractAttribute> 属性を使用して、トランザクション フローの要求、許可、または拒否を行う。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 <span data-ttu-id="cfdcb-125">詳細については、「 [ServiceModel トランザクション属性](servicemodel-transaction-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cfdcb-125">For more information, see [ServiceModel Transaction Attributes](servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdcb-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfdcb-126">See also</span></span>

- [<span data-ttu-id="cfdcb-127">ServiceModel トランザクションの属性</span><span class="sxs-lookup"><span data-stu-id="cfdcb-127">ServiceModel Transaction Attributes</span></span>](servicemodel-transaction-attributes.md)
- [<span data-ttu-id="cfdcb-128">トランザクション フローの有効化</span><span class="sxs-lookup"><span data-stu-id="cfdcb-128">Enabling Transaction Flow</span></span>](enabling-transaction-flow.md)
