---
title: ワークフローの永続性
description: .NET Framework 4.6.1 には SqlWorkflowInstanceStore クラスが含まれています。これにより、SQL Server データベースにワークフローデータとメタデータを永続化できます。
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: 2184a159423a611a8936e900591a480ce7ef6ec8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293807"
---
# <a name="workflow-persistence"></a><span data-ttu-id="23b88-103">ワークフローの永続性</span><span class="sxs-lookup"><span data-stu-id="23b88-103">Workflow Persistence</span></span>

<span data-ttu-id="23b88-104">ワークフローの永続化は、ワークフロー インスタンスの状態を、プロセスやコンピューターの情報に依存せず永続的にキャプチャしたものです。</span><span class="sxs-lookup"><span data-stu-id="23b88-104">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="23b88-105">永続化の目的は、システム生涯時にワークフロー インスタンスの既知の回復ポイントを提供するため、アクティブに作業を実行していないワークフロー インスタンスをアンロードしてメモリを節約するため、またはワークフロー インスタンスの状態をサーバー ファーム内のあるノードから別のノードに移行するためです。</span><span class="sxs-lookup"><span data-stu-id="23b88-105">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="23b88-106">永続化によって、プロセスの迅速性、拡張性、エラー時の回復、およびメモリをより効率的に管理できる機能を実現できます。</span><span class="sxs-lookup"><span data-stu-id="23b88-106">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="23b88-107">永続化プロセスには永続化ポイントの指定や保存するデータの収集が含まれ、最終的にはデータの実際のストレージが永続化プロバイダーにデリゲートされます。</span><span class="sxs-lookup"><span data-stu-id="23b88-107">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="23b88-108">ワークフローの永続化を有効にするには、 [「方法: ワークフローとワークフローサービスの永続化を有効](how-to-enable-persistence-for-workflows-and-workflow-services.md)にする」で説明されているように、インスタンスストアを **WorkflowApplication** または **WorkflowServiceHost** に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="23b88-108">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="23b88-109">**WorkflowApplication** と **WorkflowServiceHost** は、関連付けられているインスタンスストアを使用して、永続化ストアへのワークフローインスタンスの永続化と、永続化ストアに格納されているワークフローインスタンスデータに基づいたワークフローインスタンスのメモリへの読み込みを可能にします。</span><span class="sxs-lookup"><span data-stu-id="23b88-109">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="23b88-110">には、 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] **SqlWorkflowInstanceStore** クラスが付属しています。これにより、ワークフローインスタンスに関するデータとメタデータを SQL Server 2005 または SQL Server 2008 データベースに永続化できます。</span><span class="sxs-lookup"><span data-stu-id="23b88-110">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="23b88-111">詳細については、「 [SQL Workflow Instance Store](sql-workflow-instance-store.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23b88-111">See [SQL Workflow Instance Store](sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="23b88-112">アプリケーション固有のデータをワークフロー インスタンス関連の情報と共に格納し、読み込むために、<xref:System.Activities.Persistence.PersistenceParticipant> クラスを拡張する永続参加要素を作成できます。</span><span class="sxs-lookup"><span data-stu-id="23b88-112">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="23b88-113">永続参加要素は永続化プロセスに参加して、カスタムのシリアル化可能なデータを永続化ストアに保存し、インスタンス ストアからメモリにデータを読み込み、永続化トランザクションで任意の追加ロジックを実行します。</span><span class="sxs-lookup"><span data-stu-id="23b88-113">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="23b88-114">詳細については、「 [永続化参加要素](persistence-participants.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23b88-114">For more information, see [Persistence Participants](persistence-participants.md).</span></span>  
  
 <span data-ttu-id="23b88-115">Windows Server App Fabric を使用すると、永続化の構成のプロセスを簡潔化できます。</span><span class="sxs-lookup"><span data-stu-id="23b88-115">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="23b88-116">詳細については、「 [Windows Server App Fabric での永続](/previous-versions/appfabric/ee677272(v=azure.10))化の概念」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23b88-116">For more information, see [Persistence Concepts with Windows Server App Fabric](/previous-versions/appfabric/ee677272(v=azure.10))</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="23b88-117">暗黙的な永続化ポイント</span><span class="sxs-lookup"><span data-stu-id="23b88-117">Implicit Persistence Points</span></span>  

 <span data-ttu-id="23b88-118">次の一覧は、インスタンス ストアがワークフローに関連付けられている場合にワークフローが永続化される条件の例です。</span><span class="sxs-lookup"><span data-stu-id="23b88-118">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
- <span data-ttu-id="23b88-119">**TransactionScope** アクティビティが完了するか、 **TransactedReceiveScope** アクティビティが完了したとき。</span><span class="sxs-lookup"><span data-stu-id="23b88-119">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
- <span data-ttu-id="23b88-120">ワークフローインスタンスがアイドル状態になり、ワークフローホストで **WorkflowIdleBehavior** が設定されたとき。</span><span class="sxs-lookup"><span data-stu-id="23b88-120">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="23b88-121">これは、たとえば、メッセージングアクティビティや **Delay** アクティビティを使用する場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="23b88-121">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
- <span data-ttu-id="23b88-122">WorkflowApplication がアイドル状態になり、アプリケーションの **Persistableidle** プロパティが **PersistableIdleAction** に設定された場合。</span><span class="sxs-lookup"><span data-stu-id="23b88-122">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
- <span data-ttu-id="23b88-123">ホスト アプリケーションに対して、ワークフロー インスタンスの永続化またはアンロードが指示されたとき。</span><span class="sxs-lookup"><span data-stu-id="23b88-123">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
- <span data-ttu-id="23b88-124">ワークフロー インスタンスが終了したとき。</span><span class="sxs-lookup"><span data-stu-id="23b88-124">When a workflow instance is terminated or finishes.</span></span>  
  
- <span data-ttu-id="23b88-125">**Persist** アクティビティが実行されたとき。</span><span class="sxs-lookup"><span data-stu-id="23b88-125">When a **Persist** activity executes.</span></span>  
  
- <span data-ttu-id="23b88-126">以前のバージョンの Windows Workflow Foundation を使用して開発したワークフロー インスタンスが、相互運用可能な実行中に永続化ポイントに到達したとき。</span><span class="sxs-lookup"><span data-stu-id="23b88-126">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23b88-127">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="23b88-127">In This Section</span></span>  
  
- [<span data-ttu-id="23b88-128">SQL Workflow Instance Store</span><span class="sxs-lookup"><span data-stu-id="23b88-128">SQL Workflow Instance Store</span></span>](sql-workflow-instance-store.md)  
  
- [<span data-ttu-id="23b88-129">インスタンス ストア</span><span class="sxs-lookup"><span data-stu-id="23b88-129">Instance Stores</span></span>](instance-stores.md)  
  
- [<span data-ttu-id="23b88-130">永続参加要素</span><span class="sxs-lookup"><span data-stu-id="23b88-130">Persistence Participants</span></span>](persistence-participants.md)  
  
- [<span data-ttu-id="23b88-131">永続化のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="23b88-131">Persistence Best Practices</span></span>](persistence-best-practices.md)  
  
- [<span data-ttu-id="23b88-132">非永続化ワークフロー インスタンス</span><span class="sxs-lookup"><span data-stu-id="23b88-132">Non-Persisted Workflow Instances</span></span>](non-persisted-workflow-instances.md)  
  
- [<span data-ttu-id="23b88-133">ワークフローの一時停止と再開</span><span class="sxs-lookup"><span data-stu-id="23b88-133">Pausing and Resuming a Workflow</span></span>](pausing-and-resuming-a-workflow.md)
