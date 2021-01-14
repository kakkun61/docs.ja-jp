---
title: リレーショナル データベースの Azure への移行
description: Azure Cloud および Windows コンテナーを使用して既存の .NET アプリケーションを最新化する | リレーショナル データベースを Azure に移行する
ms.date: 12/21/2020
ms.openlocfilehash: c8dc92e1c5c5fb36a68bcad000c10e47c946ca0c
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025382"
---
# <a name="migrate-your-relational-databases-to-azure"></a><span data-ttu-id="644f1-103">リレーショナル データベースの Azure への移行</span><span class="sxs-lookup"><span data-stu-id="644f1-103">Migrate your relational databases to Azure</span></span>

<span data-ttu-id="644f1-104">展望:Azure には、最も包括的なデータベース移行が用意されています。</span><span class="sxs-lookup"><span data-stu-id="644f1-104">Vision: Azure offers the most comprehensive database migration.</span></span>

<span data-ttu-id="644f1-105">Azure では、データベース サーバーを IaaS VM に直接移行 (純粋なリフト アンド シフト) することも、Azure SQL Database に移行して追加のベネフィットを得ることもできます。</span><span class="sxs-lookup"><span data-stu-id="644f1-105">In Azure, you can migrate your database servers directly to IaaS VMs (pure lift and shift), or you can migrate to Azure SQL Database, for additional benefits.</span></span> <span data-ttu-id="644f1-106">Azure SQL Database には、マネージド インスタンスと完全なサービスとしてのデータベース (DBaaS) オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="644f1-106">Azure SQL Database offers the managed instance and full database-as-a-service (DBaaS) options.</span></span> <span data-ttu-id="644f1-107">図 3-1 は、Azure で使用できる複数のリレーショナル データベース移行パスを示しています。</span><span class="sxs-lookup"><span data-stu-id="644f1-107">Figure 3-1 shows the multiple relational database migration paths available in Azure.</span></span>

![Azure のデータベース移行パス](./media/image3-1.png)

<span data-ttu-id="644f1-109">**図 3-1.**</span><span class="sxs-lookup"><span data-stu-id="644f1-109">**Figure 3-1.**</span></span> <span data-ttu-id="644f1-110">Azure のデータベース移行パス</span><span class="sxs-lookup"><span data-stu-id="644f1-110">Database migration paths in Azure</span></span>

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a><span data-ttu-id="644f1-111">Azure SQL Database Managed Instance に移行するタイミング</span><span class="sxs-lookup"><span data-stu-id="644f1-111">When to migrate to Azure SQL Database Managed Instance</span></span>

<span data-ttu-id="644f1-112">データを Azure に移行する際には、ほとんどの場合、Azure SQL Database Managed Instance が最適な選択肢となります。</span><span class="sxs-lookup"><span data-stu-id="644f1-112">In most cases, Azure SQL Database Managed Instance will be your best option to consider when you migrate your data to Azure.</span></span> <span data-ttu-id="644f1-113">SQL Server データベースを移行するときに、アプリケーションを再設計したり、データやデータ アクセス コードを変更したりする必要がないことをほぼ 100% 保証する必要がある場合は、Azure SQL Database の Managed Instance 機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="644f1-113">If you are migrating SQL Server databases and need nearly 100% assurance that you won't need to rearchitect your application or make changes to your data or data access code, choose the Managed Instance feature of Azure SQL Database.</span></span>

<span data-ttu-id="644f1-114">Azure SQL Database Managed Instance は、SQL Server インスタンスレベルの機能に対する追加の要件や、標準の Azure SQL Database (単一データベース モデル) で提供される機能を超える分離要件がある場合に最適なオプションです。</span><span class="sxs-lookup"><span data-stu-id="644f1-114">Azure SQL Database Managed Instance is the best option if you have additional requirements for SQL Server instance-level functionality, or isolation requirements beyond the features provided in a standard Azure SQL Database (single database model).</span></span> <span data-ttu-id="644f1-115">最後の 1 つは、最も PaaS 指向の選択肢ですが、従来の SQL server と同じ機能を提供するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="644f1-115">This last one is the most PaaS-oriented choice, but it doesn't offer the same features as that of a traditional SQL server.</span></span> <span data-ttu-id="644f1-116">移行により摩擦が表面化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-116">Migration might surface frictions.</span></span>

<span data-ttu-id="644f1-117">たとえば、インスタンスレベルの SQL Server 機能に対して多額の投資を行ってきた組織は、SQL Managed Instance に移行することでベネフィットが得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-117">For example, an organization that has made deep investments in instance-level SQL Server capabilities would benefit from migrating to SQL Managed Instance.</span></span> <span data-ttu-id="644f1-118">インスタンスレベルの SQL Server 機能の例としては、SQL 共通言語ランタイム (CLR) の統合、SQL Server エージェント、データベース間クエリなどがあります。</span><span class="sxs-lookup"><span data-stu-id="644f1-118">Examples of instance-level SQL Server capabilities include SQL common language runtime (CLR) integration, SQL Server Agent, and cross-database querying.</span></span> <span data-ttu-id="644f1-119">これらの機能のサポートは、標準の Azure SQL Database (単一データベース モデル) では使用できません。</span><span class="sxs-lookup"><span data-stu-id="644f1-119">Support for these features is not available in standard Azure SQL Database (a single-database model).</span></span>

<span data-ttu-id="644f1-120">高度に規制された業界で事業を行っていて、セキュリティのために分離を維持する必要がある組織も、SQL Managed Instance モデルを選択することによってベネフィットが得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-120">An organization that operates in a highly regulated industry, and which needs to maintain isolation for security purposes, also might benefit from choosing the SQL Managed Instance model.</span></span>

<span data-ttu-id="644f1-121">Azure SQL Database の Managed Instance には、次の特性があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-121">Managed Instance in Azure SQL Database has the following characteristics:</span></span>

- <span data-ttu-id="644f1-122">Azure Virtual Network を使用したセキュリティの分離</span><span class="sxs-lookup"><span data-stu-id="644f1-122">Security isolation through Azure Virtual Network</span></span>

- <span data-ttu-id="644f1-123">次の機能を使用した、アプリケーション サーフェスの互換性:</span><span class="sxs-lookup"><span data-stu-id="644f1-123">Application surface compatibility, with these features:</span></span>

  - <span data-ttu-id="644f1-124">SQL Server エージェントと SQL Server プロファイラー</span><span class="sxs-lookup"><span data-stu-id="644f1-124">SQL Server Agent and SQL Server Profiler</span></span>

  - <span data-ttu-id="644f1-125">データベース間参照とクエリ、SQL CLR、レプリケーション、変更データ キャプチャ (CDC)、および Service Broker</span><span class="sxs-lookup"><span data-stu-id="644f1-125">Cross-database references and queries, SQL CLR, replication, change data capture (CDC), and Service Broker</span></span>

- <span data-ttu-id="644f1-126">最大 35 TB のデータベース サイズ</span><span class="sxs-lookup"><span data-stu-id="644f1-126">Database sizes up to 35 TB</span></span>

- <span data-ttu-id="644f1-127">次の機能を使用した、最小限のダウンタイムでの移行:</span><span class="sxs-lookup"><span data-stu-id="644f1-127">Minimum-downtime migration, with these features:</span></span>

  - <span data-ttu-id="644f1-128">Azure Database Migration Service</span><span class="sxs-lookup"><span data-stu-id="644f1-128">Azure Database Migration Service</span></span>

  - <span data-ttu-id="644f1-129">ネイティブのバックアップと復元、およびログ配布</span><span class="sxs-lookup"><span data-stu-id="644f1-129">Native backup and restore, and log shipping</span></span>

<span data-ttu-id="644f1-130">これらの機能を使用すると、既存のアプリケーション データベースを Azure SQL Database に移行するときに、Managed Instance モデルによって PaaS のベネフィットのほぼ 100% が SQL Server に提供されます。</span><span class="sxs-lookup"><span data-stu-id="644f1-130">With these capabilities, when you migrate existing application databases to Azure SQL Database, the Managed Instance model offers nearly 100% of the benefits of PaaS for SQL Server.</span></span> <span data-ttu-id="644f1-131">Managed Instance は SQL Server 環境なので、アプリケーションの設計を変更することなく、インスタンスレベルの機能を引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="644f1-131">Managed Instance is a SQL Server environment where you continue using instance-level capabilities without changing your application design.</span></span>

<span data-ttu-id="644f1-132">Managed Instance は、現在 SQL Server を使用していて、クラウドでのネットワーク セキュリティに柔軟性を必要とする企業にとっておそらく最適な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="644f1-132">Managed Instance is probably the best fit for enterprises that currently are using SQL Server, and which require flexibility in their network security in the cloud.</span></span> <span data-ttu-id="644f1-133">これは、SQL データベース用のプライベート仮想ネットワークを持つのと似ています。</span><span class="sxs-lookup"><span data-stu-id="644f1-133">It's like having a private virtual network for your SQL databases.</span></span>

## <a name="when-to-migrate-to-azure-sql-database"></a><span data-ttu-id="644f1-134">Azure SQL Database に移行するタイミング</span><span class="sxs-lookup"><span data-stu-id="644f1-134">When to migrate to Azure SQL Database</span></span>

<span data-ttu-id="644f1-135">前述のように、標準の Azure SQL Database はフル マネージドのリレーショナル DBaaS です。</span><span class="sxs-lookup"><span data-stu-id="644f1-135">As mentioned, the standard Azure SQL Database is a fully managed, relational DBaaS.</span></span> <span data-ttu-id="644f1-136">SQL Database では現在、世界中の 38 のデータセンターで、数百万の実稼働データベースが管理されています。</span><span class="sxs-lookup"><span data-stu-id="644f1-136">SQL Database currently manages millions of production databases, across 38 datacenters, around the world.</span></span> <span data-ttu-id="644f1-137">単純なトランザクション データ処理アプリケーションの管理から、世界規模の高度なデータ処理を必要とするデータ集約型のミッション クリティカルなアプリケーションの駆動まで、幅広いアプリケーションとワークロードをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="644f1-137">It supports a broad range of applications and workloads, from managing straightforward transactional data, to driving the most data-intensive, mission-critical applications that require advanced data processing at a global scale.</span></span>

<span data-ttu-id="644f1-138">その PaaS の完全な機能により、基本的な標準の SQL データベースを使用し、追加のインスタンス機能を使用しないアプリケーションがある場合は、"既定の選択肢" として標準の Azure SQL Database に移行することで、より良い価格設定となり、最終的にはコストが削減されます。</span><span class="sxs-lookup"><span data-stu-id="644f1-138">Because of its full PaaS features, better pricing-and ultimately lower cost-you should move to the standard Azure SQL Database as your "by-default choice" if you have an application that uses basic, standard SQL databases, and no additional instance features.</span></span> <span data-ttu-id="644f1-139">SQL CLR 統合、SQL Server エージェント、データベース間クエリなどの SQL Server 機能は、標準の Azure SQL Database ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="644f1-139">SQL Server features like SQL CLR integration, SQL Server Agent, and cross-database querying are not supported in the standard Azure SQL Database.</span></span> <span data-ttu-id="644f1-140">これらの機能は、Azure SQL Database Managed Instance モデルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="644f1-140">Those features are available only in the Azure SQL Database Managed Instance model.</span></span>

<span data-ttu-id="644f1-141">Azure SQL Database は、アプリ開発者向けに構築された唯一のインテリジェントなクラウド データベース サービスです。</span><span class="sxs-lookup"><span data-stu-id="644f1-141">Azure SQL Database is the only intelligent cloud database service that's built for app developers.</span></span> <span data-ttu-id="644f1-142">また、ダウンタイムを発生させることなく、すぐにスケーリングできる唯一のクラウド データベース サービスでもあるため、マルチテナント アプリを効率的に配信するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="644f1-142">It's also the only cloud database service that scales on-the-fly, without downtime, to help you efficiently deliver multitenant apps.</span></span> <span data-ttu-id="644f1-143">最終的に、Azure SQL Database によって、イノベーションにより多くの時間がかけられるようになり、市場投入までの時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="644f1-143">Ultimately, Azure SQL Database leaves you more time to innovate, and it accelerates your time to market.</span></span> <span data-ttu-id="644f1-144">お好みの言語とプラットフォームを使用して、セキュリティで保護されたアプリをビルドして SQL データベースに接続できます。</span><span class="sxs-lookup"><span data-stu-id="644f1-144">You can build secure apps and connect to your SQL database by using the languages and platforms that you prefer.</span></span>

<span data-ttu-id="644f1-145">Azure SQL Database を使用することで、次のベネフィットが得られます。</span><span class="sxs-lookup"><span data-stu-id="644f1-145">Azure SQL Database offers the following benefits:</span></span>

- <span data-ttu-id="644f1-146">学習してアプリに適応する組み込みのインテリジェンス (機械学習)</span><span class="sxs-lookup"><span data-stu-id="644f1-146">Built-in intelligence (machine learning) that learns and adapts to your app</span></span>

- <span data-ttu-id="644f1-147">オンデマンドのデータベース プロビジョニング</span><span class="sxs-lookup"><span data-stu-id="644f1-147">On-demand database provisioning</span></span>

- <span data-ttu-id="644f1-148">あらゆるワークロードに対応する幅広いオファー</span><span class="sxs-lookup"><span data-stu-id="644f1-148">A range of offers, for all workloads</span></span>

- <span data-ttu-id="644f1-149">99.99% の可用性 SLA、メンテナンス不要</span><span class="sxs-lookup"><span data-stu-id="644f1-149">99.99% availability SLA, zero maintenance</span></span>

- <span data-ttu-id="644f1-150">データ保護のための geo レプリケーションと復元サービス</span><span class="sxs-lookup"><span data-stu-id="644f1-150">Geo-replication and restore services for data protection</span></span>

- <span data-ttu-id="644f1-151">Azure SQL Database のポイント イン タイム リストア機能</span><span class="sxs-lookup"><span data-stu-id="644f1-151">Azure SQL Database Point in Time Restore feature</span></span>

- <span data-ttu-id="644f1-152">ハイブリッドおよび移行を含む SQL Server 2016 との互換性</span><span class="sxs-lookup"><span data-stu-id="644f1-152">Compatibility with SQL Server 2016, including hybrid and migration</span></span>

<span data-ttu-id="644f1-153">標準の Azure SQL Database は、Azure SQL Database Managed Instance よりも PaaS に近いです。</span><span class="sxs-lookup"><span data-stu-id="644f1-153">The standard Azure SQL Database is closer to PaaS than Azure SQL Database Managed Instance.</span></span> <span data-ttu-id="644f1-154">マネージド クラウドからより多くのベネフィットを得られるため、標準の Azure SQL Database をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="644f1-154">Prefer the standard Azure SQL Database because you'll get more benefits from a managed cloud.</span></span> <span data-ttu-id="644f1-155">ただし、Azure SQL Database には、通常およびオンプレミスの SQL Server インスタンスとの主な違いがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="644f1-155">However, Azure SQL Database has some key differences from regular and on-premises SQL Server instances.</span></span> <span data-ttu-id="644f1-156">既存のアプリケーションのデータベース要件、および自社の要件とポリシーによっては、クラウドへの移行を計画するときに、これが最適な選択肢ではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-156">Depending on your existing application's database requirements, and your enterprise requirements and policies, it might not be the best choice when you are planning your migration to the cloud.</span></span>

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a><span data-ttu-id="644f1-157">元の RDBMS を VM (IaaS) に移行するタイミング</span><span class="sxs-lookup"><span data-stu-id="644f1-157">When to move your original RDBMS to a VM (IaaS)</span></span>

<span data-ttu-id="644f1-158">移行オプションの 1 つは、Oracle、IBM DB2、MySQL、PostgreSQL、SQL Server などの元のリレーショナル データベース管理システム (RDBMS) を、Azure VM 上で実行されている同様のサーバーに移動することです。</span><span class="sxs-lookup"><span data-stu-id="644f1-158">One of your migration options is to move your original relational database management system (RDBMS), including Oracle, IBM DB2, MySQL, PostgreSQL, or SQL Server, to a similar server that's running on an Azure VM.</span></span> <span data-ttu-id="644f1-159">最小限の変更、またはまったく変更を加えずに、クラウドへの移行を最速で行う必要がある既存のアプリケーションがある場合、クラウドの IaaS に直接移行することが正しい選択肢となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-159">If you have existing applications that require the fastest migration to the cloud with minimal changes, or no changes at all, a direct migration to IaaS in the cloud might be a fair option.</span></span> <span data-ttu-id="644f1-160">クラウドのベネフィットをすべて活用するのが最善の方法ではない場合もありますが、最初はそれが最短の近道となるでしょう。</span><span class="sxs-lookup"><span data-stu-id="644f1-160">It might not be the best way to take advantage of all the cloud's benefits, but it's probably the fastest initial path.</span></span>

<span data-ttu-id="644f1-161">現在、Microsoft Azure では、IaaS VM としてデプロイされる、最大 [331 台の異なるデータベース サーバー](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="644f1-161">Currently, Microsoft Azure supports up to [331 different database servers](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all) deployed as IaaS VMs.</span></span> <span data-ttu-id="644f1-162">これには、SQL Server、Oracle、MySQL、PostgreSQL、IBM DB2 などの一般的な RDBMS や、MongoDB、Cassandra、DataNoSQL x、MariaDB、Cloudera などの SQL 以外の他の多くのデータベースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="644f1-162">These include popular RDBMS like SQL Server, Oracle, MySQL, PostgreSQL, and IBM DB2, and many other NoSQL databases like MongoDB, Cassandra, DataStax, MariaDB, and Cloudera.</span></span>

> [!NOTE]
> <span data-ttu-id="644f1-163">データをクラウドに移行する最速の方法は、RDBMS を Azure VM に移動することかもしれませんが (IaaS であるため)、この方法では、IT チーム (データベース管理者および IT プロフェッショナル) に多大な投資を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-163">Although moving your RDBMS to an Azure VM might be the fastest way to migrate your data to the cloud (because it is IaaS), this approach requires a significant investment in your IT teams (database administrators and IT pros).</span></span> <span data-ttu-id="644f1-164">エンタープライズ チームは、SQL Server の高可用性、ディザスター リカバリー、修正プログラムの適用を設定して管理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-164">Enterprise teams need to be able to set up and manage high availability, disaster recovery, and patching for SQL Server.</span></span> <span data-ttu-id="644f1-165">この場合は、完全な管理者アクセス権がある、カスタマイズされた環境も必要です。</span><span class="sxs-lookup"><span data-stu-id="644f1-165">This context also needs a customized environment, with full administrative rights.</span></span>

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a><span data-ttu-id="644f1-166">VM として SQL Server に移行するタイミング (IaaS)</span><span class="sxs-lookup"><span data-stu-id="644f1-166">When to migrate to SQL Server as a VM (IaaS)</span></span>

<span data-ttu-id="644f1-167">少数ですが、通常の VM として SQL Server に移行する必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="644f1-167">There might be a few cases where you still need to migrate to SQL Server as a regular VM.</span></span> <span data-ttu-id="644f1-168">サンプル シナリオとして、SQL Server Reporting Services を使用する必要がある場合が挙げられます。</span><span class="sxs-lookup"><span data-stu-id="644f1-168">An example scenario is if you need to use SQL Server Reporting Services.</span></span> <span data-ttu-id="644f1-169">ただし、ほとんどの場合、Azure SQL Database Managed Instance で、オンプレミスの SQL サーバーから移行するために必要なすべてのものを提供できるため、SQL Server VM への移行は、最後の手段として行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-169">In most cases, though, Azure SQL Database Managed Instance can provide everything you need to migrate from on-premises SQL servers, so migration to a SQL Server VM should be your last resort to try.</span></span>

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a><span data-ttu-id="644f1-170">Azure Database Migration Service を使用してリレーショナル データベースを Azure に移行する</span><span class="sxs-lookup"><span data-stu-id="644f1-170">Use Azure Database Migration Service to migrate your relational databases to Azure</span></span>

<span data-ttu-id="644f1-171">Azure Database Migration Service を使用して、SQL Server、Oracle、MySQL などのリレーショナル データベースを Azure に移行することができます。これは、ターゲット データベースが Azure SQL Database、Azure SQL Database Managed Instance、または Azure VM 上の SQL Server のいずれでも関係ありません。</span><span class="sxs-lookup"><span data-stu-id="644f1-171">You can use Azure Database Migration Service to migrate relational databases like SQL Server, Oracle, and MySQL to Azure, whether your target database is Azure SQL Database, Azure SQL Database Managed Instance, or SQL Server on an Azure VM.</span></span>

<span data-ttu-id="644f1-172">自動化されたワークフローと評価レポートを使用すると、データベースを移行する前に必要な変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="644f1-172">The automated workflow, with assessment reporting, guides you through the changes you need to make before you migrate the database.</span></span> <span data-ttu-id="644f1-173">準備が整うと、サービスによってソース データベースが Azure に移行されます。</span><span class="sxs-lookup"><span data-stu-id="644f1-173">When you are ready, the service migrates the source database to Azure.</span></span>

<span data-ttu-id="644f1-174">元の RDBMS を変更するたびに、再テストが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-174">Whenever you change an original RDBMS, you might need to retest.</span></span> <span data-ttu-id="644f1-175">また、テスト結果によっては、アプリケーションの SQL 文またはオブジェクト リレーショナル マッピング (ORM) コードの変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="644f1-175">You also might need to change the SQL sentences or Object-Relational Mapping (ORM) code in your application, depending on testing results.</span></span>

<span data-ttu-id="644f1-176">その他のデータベース (IBM DB2 など) があり、リフト アンド シフト アプローチを選択した場合は、より複雑なデータ移行を実行する場合を除き、これらのデータベースを Azure で IaaS VM として引き続き使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="644f1-176">If you have any other database (for example, IBM DB2) and you opt for a lift and shift approach, you might want to continue using those databases as IaaS VMs in Azure, unless you are willing to perform a more complex data migration.</span></span> <span data-ttu-id="644f1-177">より複雑なデータ移行では、新しいスキーマと異なるプログラミング ライブラリを持つ別の種類のデータベースに移行するため、追加の作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="644f1-177">A more complex data migration will require additional effort because you'd be migrating to a different database type with the new schema and different programming libraries.</span></span>

<span data-ttu-id="644f1-178">Azure Database Migration Service を使用してデータベースを移行する方法については、「[Get to the cloud faster with Azure SQL Database Managed Instance and Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008)」 (Azure SQL Database Managed Instance と Azure Database Migration Service を使用してクラウドにすばやく移行する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="644f1-178">To learn how to migrate databases by using Azure Database Migration Service, see [Get to the cloud faster with Azure SQL Database Managed Instance and Azure Database Migration Service](https://channel9.msdn.com/Events/Build/2017/P4008).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="644f1-179">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="644f1-179">Additional resources</span></span>

- <span data-ttu-id="644f1-180">**クラウド SQL Server オプションを選択する:Azure SQL Database (PaaS) または Azure VM 上の SQL Server (IaaS)**</span><span class="sxs-lookup"><span data-stu-id="644f1-180">**Choose a cloud SQL Server option: Azure SQL Database (PaaS) or SQL Server on Azure VM (IaaS)**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- <span data-ttu-id="644f1-181">**Azure SQL DB Managed Instance と Database Migration Service を使用してクラウドにすばやく移行する**</span><span class="sxs-lookup"><span data-stu-id="644f1-181">**Get to the cloud faster with Azure SQL DB Managed Instance and Database Migration Service**</span></span>

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- <span data-ttu-id="644f1-182">**SQL Server データベースのクラウド内の SQL Database への移行**</span><span class="sxs-lookup"><span data-stu-id="644f1-182">**SQL Server database migration to SQL Database in the cloud**</span></span>

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- <span data-ttu-id="644f1-183">**Azure SQL Database**</span><span class="sxs-lookup"><span data-stu-id="644f1-183">**Azure SQL Database**</span></span>

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- <span data-ttu-id="644f1-184">**仮想マシン上の SQL Server**</span><span class="sxs-lookup"><span data-stu-id="644f1-184">**SQL Server on virtual machines**</span></span>

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> <span data-ttu-id="644f1-185">[前へ](lift-and-shift-existing-apps-azure-iaas.md)
> [次へ](modernize-existing-apps-to-cloud-optimized/index.md)</span><span class="sxs-lookup"><span data-stu-id="644f1-185">[Previous](lift-and-shift-existing-apps-azure-iaas.md)
[Next](modernize-existing-apps-to-cloud-optimized/index.md)</span></span> <!-- Next Chapter -->
