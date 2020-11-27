---
title: ワークフロー ホスティングのオプション
ms.date: 03/30/2017
ms.assetid: 37bcd668-9c5c-4e7c-81da-a1f1b3a16514
ms.openlocfilehash: 8ddb83f068eab8480bacc8b80bc5d44b7755fa59
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293781"
---
# <a name="workflow-hosting-options"></a><span data-ttu-id="f4e75-102">ワークフロー ホスティングのオプション</span><span class="sxs-lookup"><span data-stu-id="f4e75-102">Workflow Hosting Options</span></span>

<span data-ttu-id="f4e75-103">ほとんどの Windows Workflow Foundation (WF) のサンプルでは、コンソールアプリケーションでホストされているワークフローを使用しますが、これは実際のワークフローにとって現実的なシナリオではありません。</span><span class="sxs-lookup"><span data-stu-id="f4e75-103">Most of the Windows Workflow Foundation (WF) samples use workflows that are hosted in a console application, but this isn't a realistic scenario for real-world workflows.</span></span> <span data-ttu-id="f4e75-104">実際のビジネスアプリケーションのワークフローは、開発者が作成した Windows サービスまたは IIS 7.0 や AppFabric などのサーバーアプリケーションのいずれかの永続的なプロセスでホストされます。</span><span class="sxs-lookup"><span data-stu-id="f4e75-104">Workflows in actual business applications will be hosted in persistent processes- either a Windows service authored by the developer, or a server application such as IIS 7.0 or AppFabric.</span></span> <span data-ttu-id="f4e75-105">これらの方法の違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f4e75-105">The differences between these approaches are as follows.</span></span>

## <a name="hosting-workflows-in-iis-with-windows-appfabric"></a><span data-ttu-id="f4e75-106">Windows AppFabric を使用した IIS でのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="f4e75-106">Hosting workflows in IIS with Windows AppFabric</span></span>

<span data-ttu-id="f4e75-107">IIS と AppFabric は、ワークフローに推奨されるホストです。</span><span class="sxs-lookup"><span data-stu-id="f4e75-107">Using IIS with AppFabric is the preferred host for workflows.</span></span> <span data-ttu-id="f4e75-108">AppFabric を使用したワークフローのホスト アプリケーションは Windows プロセス アクティブ化サービスで、これは IIS を介した HTTP への依存関係のみを解消します。</span><span class="sxs-lookup"><span data-stu-id="f4e75-108">The host application for workflows using AppFabric is Windows Activation Service, which removes the dependency on HTTP over IIS alone.</span></span>

## <a name="hosting-workflows-in-iis-alone"></a><span data-ttu-id="f4e75-109">IIS のみでのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="f4e75-109">Hosting workflows in IIS alone</span></span>

<span data-ttu-id="f4e75-110">実行中のアプリケーションのメンテナンスを容易にする AppFabric で使用できる管理ツールと監視ツールがあるため、IIS 7.0 だけを使用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="f4e75-110">Using IIS 7.0 alone is not recommended, as there are management and monitoring tools available with AppFabric that facilitate maintenance of running applications.</span></span> <span data-ttu-id="f4e75-111">AppFabric への移行に関するインフラストラクチャの問題がある場合、ワークフローは IIS 7.0 のみでホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4e75-111">Workflows should only be hosted in IIS 7.0 alone if there are infrastructure concerns with moving to AppFabric.</span></span>

> [!WARNING]
> <span data-ttu-id="f4e75-112">IIS 7.0 は、さまざまな理由でアプリケーションプールを定期的にリサイクルします。</span><span class="sxs-lookup"><span data-stu-id="f4e75-112">IIS 7.0 recycles application pools periodically for various reasons.</span></span> <span data-ttu-id="f4e75-113">アプリケーション プールがリサイクルされると、IIS は古いプールへのメッセージの受け取りを中止し、新しいアプリケーション プールをインスタンス化して新しい要求を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f4e75-113">When an application pool is recycled, IIS stops accepting messages to the old pool, and instantiates a new application pool to accept new requests.</span></span> <span data-ttu-id="f4e75-114">応答を送信した後もワークフローが動作を続ける場合、IIS 7.0 は、実行されている作業を認識しないため、ホストしているアプリケーションプールをリサイクルする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f4e75-114">If a workflow continues working after sending a response, IIS 7.0 will not be aware of the work being done, and may recycle the hosting application pool.</span></span> <span data-ttu-id="f4e75-115">これが発生すると、ワークフローが中止され、追跡サービスによって、"理由" フィールドが空の [1004-WorkflowInstanceAborted](1004-workflowinstanceaborted.md) メッセージが記録されます。</span><span class="sxs-lookup"><span data-stu-id="f4e75-115">If this happens, the workflow will abort, and tracking services will record a [1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md) message with an empty Reason field.</span></span>
>
> <span data-ttu-id="f4e75-116">永続化を使用する場合、ホストは、最後の永続性ポイントから、中止されたインスタンスを明示的に再開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4e75-116">If persistence is used, the host must explicitly restart aborted instances from the last persistence point.</span></span>
>
> <span data-ttu-id="f4e75-117">AppFabric を使用する場合、永続化を使用すると、ワークフロー管理サービスは、最終的に、最後に成功した永続性ポイントからワークフローを再開します。</span><span class="sxs-lookup"><span data-stu-id="f4e75-117">If AppFabric is used, the workflow management service will eventually resume the workflow from the last successful persistence point if persistence is used.</span></span> <span data-ttu-id="f4e75-118">永続化を使用せず、ワークフローが要求/応答パターン以外の操作を実行している場合、ワークフローが中止されるとデータは失われます。</span><span class="sxs-lookup"><span data-stu-id="f4e75-118">If no persistence is used, and the workflow performs operations outside a Request/Response pattern, data will be lost when the workflow aborts.</span></span>

## <a name="hosting-a-workflow-in-a-custom-windows-service"></a><span data-ttu-id="f4e75-119">カスタム Windows サービスでのワークフローのホスト</span><span class="sxs-lookup"><span data-stu-id="f4e75-119">Hosting a workflow in a custom Windows Service</span></span>

<span data-ttu-id="f4e75-120">カスタム ワークフロー サービスを作成してワークフローをホストする場合、開発者は AppFabric に標準搭載されている多くの機能を複製する必要がありますが、カスタム機能をより柔軟に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f4e75-120">Creating a custom workflow service to host the workflow will require the developer to duplicate a lot of the functionality provided out-of-box by AppFabric, but will allow for more flexibility with custom functionality.</span></span> <span data-ttu-id="f4e75-121">このオプションは、AppFabric を選択できない場合にのみ検討してください。</span><span class="sxs-lookup"><span data-stu-id="f4e75-121">This option should only be considered if AppFabric proves to not be an option.</span></span>
