---
title: トランザクション モデル
ms.date: 03/30/2017
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
ms.openlocfilehash: ce7eb74a3e06df8db2e6d8261faca16650e4e4f1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242267"
---
# <a name="transaction-models"></a><span data-ttu-id="ff5fe-102">トランザクション モデル</span><span class="sxs-lookup"><span data-stu-id="ff5fe-102">Transaction Models</span></span>

<span data-ttu-id="ff5fe-103">ここでは、トランザクション プログラミング モデルと、マイクロソフトが提供するインフラストラクチャ コンポーネントとの関係を説明します。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-103">This topic describes the relationship between the transaction programming models and the infrastructure components Microsoft provides.</span></span>  
  
 <span data-ttu-id="ff5fe-104">Windows Communication Foundation (WCF) でトランザクションを使用する場合は、異なるトランザクションモデルを選択するのではなく、統合された一貫性のあるモデルの異なる層で操作することを理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-104">When using transactions in Windows Communication Foundation (WCF), it is important to understand that you are not selecting between different transactional models, but rather operating at different layers of an integrated and consistent model.</span></span>  
  
 <span data-ttu-id="ff5fe-105">以下に、3 つの主要なトランザクション コンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-105">The following sections describe the three primary transaction components.</span></span>  
  
## <a name="windows-communication-foundation-transactions"></a><span data-ttu-id="ff5fe-106">Windows Communication Foundation トランザクション</span><span class="sxs-lookup"><span data-stu-id="ff5fe-106">Windows Communication Foundation Transactions</span></span>  

 <span data-ttu-id="ff5fe-107">WCF でのトランザクションのサポートにより、トランザクションサービスを記述することができます。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-107">The transaction support in WCF allows you write transactional services.</span></span> <span data-ttu-id="ff5fe-108">さらに、WS-AtomicTransaction (WS-AT) プロトコルがサポートされているため、アプリケーションは WCF またはサードパーティのテクノロジを使用して構築された Web サービスにトランザクションをフローできます。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-108">In addition, with its support for the WS-AtomicTransaction (WS-AT) protocol, applications can flow transactions to Web services built using either WCF or third-party technology.</span></span>  
  
 <span data-ttu-id="ff5fe-109">WCF サービスまたはアプリケーションでは、WCF トランザクション機能によって属性と構成が提供され、インフラストラクチャがトランザクションを作成、フロー、および同期する方法とタイミングを宣言によって指定できます。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-109">In a WCF service or application, WCF transaction features provide attributes and configuration for declaratively specifying how and when the infrastructure should create, flow, and synchronize transactions.</span></span>  
  
## <a name="systemtransactions-transactions"></a><span data-ttu-id="ff5fe-110">System.Transactions トランザクション</span><span class="sxs-lookup"><span data-stu-id="ff5fe-110">System.Transactions Transactions</span></span>  

 <span data-ttu-id="ff5fe-111"><xref:System.Transactions> 名前空間は、<xref:System.Transactions.Transaction> クラスに基づく明示的なプログラミング モデルだけでなく、インフラストラクチャがトランザクションを自動的に管理する、<xref:System.Transactions.TransactionScope> クラスを使用した暗黙的なプログラミング モデルも提供します。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-111">The <xref:System.Transactions> namespace provides both an explicit programming model based on the <xref:System.Transactions.Transaction> class, as well as an implicit programming model using the <xref:System.Transactions.TransactionScope> class, in which the infrastructure automatically manages transactions.</span></span>  
  
 <span data-ttu-id="ff5fe-112">これら2つのモデルを使用してトランザクションアプリケーションを作成する方法の詳細については、「 [トランザクションアプリケーションの](https://go.microsoft.com/fwlink/?LinkId=94947)作成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-112">For more information about how to create a transactional application using these two models, see [Writing a Transactional Application](https://go.microsoft.com/fwlink/?LinkId=94947).</span></span>  
  
 <span data-ttu-id="ff5fe-113">WCF サービスまたはアプリケーションでは、は、 <xref:System.Transactions> クライアントアプリケーション内でトランザクションを作成するためのプログラミングモデルを提供し、必要に応じてサービス内でトランザクションを明示的に操作します。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-113">In a WCF service or application, <xref:System.Transactions> provides the programming model for creating transactions within a client application and for explicitly interacting with a transaction, when required, within a service.</span></span>  
  
## <a name="msdtc-transactions"></a><span data-ttu-id="ff5fe-114">MSDTC トランザクション</span><span class="sxs-lookup"><span data-stu-id="ff5fe-114">MSDTC Transactions</span></span>  

 <span data-ttu-id="ff5fe-115">Microsoft 分散トランザクション コーディネーター (MSDTC) は、分散トランザクションをサポートするトランザクション マネージャーです。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-115">The Microsoft Distributed Transaction Coordinator (MSDTC) is a transaction manager that provides support for distributed transactions.</span></span>  
  
 <span data-ttu-id="ff5fe-116">詳細については、「 [DTC プログラマーズリファレンス](/previous-versions/windows/desktop/ms686108(v=vs.85))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-116">For more information, see the [DTC Programmer's Reference](/previous-versions/windows/desktop/ms686108(v=vs.85)).</span></span>  
  
 <span data-ttu-id="ff5fe-117">WCF サービスまたはアプリケーションでは、MSDTC によって、クライアントまたはサービス内で作成されたトランザクションを調整するためのインフラストラクチャが提供されます。</span><span class="sxs-lookup"><span data-stu-id="ff5fe-117">In a WCF service or application, MSDTC provides the infrastructure for the coordination of transactions created within a client or service.</span></span>
