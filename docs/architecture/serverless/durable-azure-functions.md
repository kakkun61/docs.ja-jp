---
title: 永続的な Azure Functions - サーバーレス アプリ
description: Azure Functions ランタイムを永続的な Azure Functions で拡張すると、コード内でステートフル ワークフローを有効にできます。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: c3ee628b5c2239cd13395fda7714b38b06efa058
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557156"
---
# <a name="durable-azure-functions"></a><span data-ttu-id="f16ce-103">永続的な Azure Functions</span><span class="sxs-lookup"><span data-stu-id="f16ce-103">Durable Azure Functions</span></span>

<span data-ttu-id="f16ce-104">Azure Functions でサーバーレス アプリケーションを作成する場合、通常、操作はステートレスな方法で実行するように設計されます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-104">When creating serverless applications with Azure Functions, your operations will typically be designed to run in a stateless manner.</span></span> <span data-ttu-id="f16ce-105">この設計を選択する理由は、プラットフォームの規模が大きくなると、コードが実行されているサーバーを知ることが難しくなるためです。</span><span class="sxs-lookup"><span data-stu-id="f16ce-105">The reason for this design choice is because as the platform scales, it becomes difficult to know what servers the code is running on.</span></span> <span data-ttu-id="f16ce-106">また、ある特定の時点でアクティブになっているインスタンスの数を把握することも困難になります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-106">It also becomes difficult to know how many instances are active at any given point.</span></span> <span data-ttu-id="f16ce-107">その一方で、プロセスの現在の状態を把握することが必要なアプリケーションの種類があります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-107">However, there are classes of applications that require the current state of a process to be known.</span></span> <span data-ttu-id="f16ce-108">オンライン ストアに注文を送信するプロセスを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="f16ce-108">Consider the process of submitting an order to an online store.</span></span> <span data-ttu-id="f16ce-109">そのチェックアウトの操作は、複数の操作で構成された 1 つのワークフローであり、各操作でプロセスの状態がわかっていることが必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-109">The checkout operation might be a workflow that is composed of multiple operations that need to know the state of the process.</span></span> <span data-ttu-id="f16ce-110">このような情報として、製品の在庫、顧客のアカウントに残高があるかどうか、クレジット カード処理の結果などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-110">Such information may include the product inventory, if the customer has any credits on their account, and also the results of processing the credit card.</span></span> <span data-ttu-id="f16ce-111">これらの操作はおそらく、独自の内部ワークフローです。または、サードパーティ システムのサービスであるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="f16ce-111">These operations could easily be their own internal workflows or even services from third-party systems.</span></span>

<span data-ttu-id="f16ce-112">現在、内部システムと外部システムとの間でアプリケーションの状態を調整するのを支援する、さまざまなパターンが存在します。</span><span class="sxs-lookup"><span data-stu-id="f16ce-112">Various patterns exist today that assist with the coordination of application state between internal and external systems.</span></span> <span data-ttu-id="f16ce-113">よくあるのは、一元化されたキュー システム、分散型のキー値ストア、または共有データベースを使用してその状態を管理するソリューションです。</span><span class="sxs-lookup"><span data-stu-id="f16ce-113">It's common to come across solutions that rely on centralized queuing systems, distributed key-value stores, or shared databases to manage that state.</span></span> <span data-ttu-id="f16ce-114">ただし、これらはすべて、プロビジョニングと管理が必要な追加リソースです。</span><span class="sxs-lookup"><span data-stu-id="f16ce-114">However, these are all additional resources that now need to be provisioned and managed.</span></span> <span data-ttu-id="f16ce-115">サーバーレス環境では、これらのリソースを手動で調整しようとすると、コードが煩雑になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-115">In a serverless environment, your code could become cumbersome trying to coordinate with these resources manually.</span></span> <span data-ttu-id="f16ce-116">Azure Functions には、Durable Functions と呼ばれるステートフル関数を作成するための代替手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f16ce-116">Azure Functions offers an alternative for creating stateful functions called Durable Functions.</span></span>

<span data-ttu-id="f16ce-117">Durable Functions は、コードでステートフル ワークフローを定義できるようにする、Azure Functions ランタイムの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="f16ce-117">Durable Functions is an extension to the Azure Functions runtime that enables the definition of stateful workflows in code.</span></span> <span data-ttu-id="f16ce-118">Durable Functions 拡張機能を使用すると、ワークフローをアクティビティに分割することにより、状態の管理、進行状況のチェックポイントの作成、サーバー間での関数呼び出しの分散の処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-118">By breaking down workflows into activities, the Durable Functions extension can manage state, create progress checkpoints, and handle the distribution of function calls across servers.</span></span> <span data-ttu-id="f16ce-119">バックグラウンドでは、Azure ストレージ アカウントを使用して、実行履歴の保持、アクティビティ関数のスケジュール設定、応答の取得が行われます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-119">In the background, it makes use of an Azure Storage account to persist execution history, schedule activity functions and retrieve responses.</span></span> <span data-ttu-id="f16ce-120">サーバーレス コードでは、そのストレージ アカウントの永続化された情報を操作することはできません。通常、開発者が操作する必要のあるものではありません。</span><span class="sxs-lookup"><span data-stu-id="f16ce-120">Your serverless code should never interact with persisted information in that storage account, and is typically not something with which developers need to interact.</span></span>

## <a name="triggering-a-stateful-workflow"></a><span data-ttu-id="f16ce-121">ステートフル ワークフローのトリガー</span><span class="sxs-lookup"><span data-stu-id="f16ce-121">Triggering a stateful workflow</span></span>

<span data-ttu-id="f16ce-122">Durable Functions のステートフル ワークフローは、オーケストレーション トリガーとアクティビティ トリガーという 2 つの組み込みコンポーネントに分けることができます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-122">Stateful workflows in Durable Functions can be broken down into two intrinsic components; orchestration and activity triggers.</span></span> <span data-ttu-id="f16ce-123">トリガーとバインドは、Azure Functions によって使用されるコア コンポーネントです。トリガーとバインドによって、サーバーレス関数に開始、入力の受け取り、結果の返送を行うきっかけを通知できます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-123">Triggers and bindings are core components used by Azure Functions to enable your serverless functions to be notified when to start, receive input, and return results.</span></span>

### <a name="working-with-the-orchestration-client"></a><span data-ttu-id="f16ce-124">オーケストレーション クライアントの操作</span><span class="sxs-lookup"><span data-stu-id="f16ce-124">Working with the Orchestration client</span></span>

<span data-ttu-id="f16ce-125">オーケストレーションは、Azure Functions でトリガーされる他のスタイルの操作と比較した場合、独特なものです。</span><span class="sxs-lookup"><span data-stu-id="f16ce-125">Orchestrations are unique when compared to other styles of triggered operations in Azure Functions.</span></span> <span data-ttu-id="f16ce-126">Durable Functions では、完了までに数時間または数日かかる可能性のある関数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-126">Durable Functions enables the execution of functions that may take hours or even days to complete.</span></span> <span data-ttu-id="f16ce-127">この種類の動作では、実行中のオーケストレーションの状態の確認、プリエンプティブな終了、外部イベントの通知の送信ができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-127">That type of behavior comes with the need to able to check the status of a running orchestration, preemptively terminate, or send notifications of external events.</span></span>

<span data-ttu-id="f16ce-128">このような場合のために、Durable Functions 拡張機能には、調整された関数を操作できる `DurableOrchestrationClient` クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f16ce-128">For such cases, the Durable Functions extension provides the `DurableOrchestrationClient` class that allows you to interact with orchestrated functions.</span></span> <span data-ttu-id="f16ce-129">オーケストレーション クライアントにアクセスするには、`OrchestrationClientAttribute` バインドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f16ce-129">You get access to the orchestration client by using the `OrchestrationClientAttribute` binding.</span></span> <span data-ttu-id="f16ce-130">通常、この属性は、`HttpTrigger` や `ServiceBusTrigger` など、別の種類のトリガーに含めます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-130">Generally, you would include this attribute with another trigger type, such as an `HttpTrigger` or `ServiceBusTrigger`.</span></span> <span data-ttu-id="f16ce-131">ソース関数がトリガーされたら、オーケストレーション クライアントを使用してオーケストレーター関数を開始できます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-131">Once the source function has been triggered, the orchestration client can be used to start an orchestrator function.</span></span>

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a><span data-ttu-id="f16ce-132">オーケストレーター関数</span><span class="sxs-lookup"><span data-stu-id="f16ce-132">The orchestrator function</span></span>

<span data-ttu-id="f16ce-133">Azure Functions の OrchestrationTriggerAttribute を使用して関数に注釈を付けると、その関数がオーケストレーター関数としてマークされます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-133">Annotating a function with the OrchestrationTriggerAttribute in Azure Functions marks that function as an orchestrator function.</span></span> <span data-ttu-id="f16ce-134">ステートフル ワークフローを構成するさまざまなアクティビティを管理する責任を負います。</span><span class="sxs-lookup"><span data-stu-id="f16ce-134">It's responsible for managing the various activities that make up your stateful workflow.</span></span>

<span data-ttu-id="f16ce-135">オーケストレーター関数で OrchestrationTriggerAttribute 以外のバインドを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f16ce-135">Orchestrator functions are unable to make use of bindings other than the OrchestrationTriggerAttribute.</span></span> <span data-ttu-id="f16ce-136">この属性は、パラメーターの種類が DurableOrchestrationContext の場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-136">This attribute can only be used with a parameter type of DurableOrchestrationContext.</span></span> <span data-ttu-id="f16ce-137">関数シグネチャの入力の逆シリアル化がサポートされていないため、その他の入力を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f16ce-137">No other inputs can be used since deserialization of inputs in the function signature isn't supported.</span></span> <span data-ttu-id="f16ce-138">オーケストレーター クライアントによって提供される入力を取得するには、GetInput\<T\> メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-138">To get inputs provided by the orchestration client, the GetInput\<T\> method must be used.</span></span>

<span data-ttu-id="f16ce-139">また、オーケストレーション関数の戻り値の型は、void、タスク、または JSON のシリアル化可能な値のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-139">Also, the return types of orchestration functions must be either void, Task, or a JSON serializable value.</span></span>

> <span data-ttu-id="f16ce-140">*簡潔にするため、エラー処理コードは省略されています*</span><span class="sxs-lookup"><span data-stu-id="f16ce-140">*Error handling code has been left out for brevity*</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="f16ce-141">オーケストレーションの複数のインスタンスを同時に開始して実行できます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-141">Multiple instances of an orchestration can be started and running at the same time.</span></span> <span data-ttu-id="f16ce-142">`DurableOrchestrationClient` で `StartNewAsync` メソッドを呼び出すと、オーケストレーションの新しいインスタンスが起動されます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-142">Calling the `StartNewAsync` method on the `DurableOrchestrationClient` launches a new instance of the orchestration.</span></span> <span data-ttu-id="f16ce-143">そのメソッドからは、オーケストレーションが開始されたときに完了する `Task<string>` が返されます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-143">The method returns a `Task<string>` that completes when the orchestration has started.</span></span> <span data-ttu-id="f16ce-144">オーケストレーションが 30 秒以内に開始されなかった場合は、`TimeoutException` 型の例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-144">An exception of type `TimeoutException` gets thrown if the orchestration hasn't started within 30 seconds.</span></span>

<span data-ttu-id="f16ce-145">`StartNewAsync` から完了した `Task<string>` には、オーケストレーション インスタンスの一意の ID が含まれているはずです。</span><span class="sxs-lookup"><span data-stu-id="f16ce-145">The completed `Task<string>` from `StartNewAsync` should contain the unique ID of the orchestration instance.</span></span> <span data-ttu-id="f16ce-146">このインスタンス ID を使用して、その特定のオーケストレーションに対する操作を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-146">This instance ID can be used to invoke operations on that specific orchestration.</span></span> <span data-ttu-id="f16ce-147">オーケストレーションに状態を照会したり、イベント通知を送信したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-147">The orchestration can be queried for the status or sent event notifications.</span></span>

### <a name="the-activity-functions"></a><span data-ttu-id="f16ce-148">アクティビティ関数</span><span class="sxs-lookup"><span data-stu-id="f16ce-148">The activity functions</span></span>

<span data-ttu-id="f16ce-149">アクティビティ関数は、ワークフローを作成するためにオーケストレーション関数内にまとめて構成される個別の操作です。</span><span class="sxs-lookup"><span data-stu-id="f16ce-149">Activity functions are the discrete operations that get composed together within an orchestration function to create the workflow.</span></span> <span data-ttu-id="f16ce-150">実際の作業のほとんどがここで行われます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-150">Here is where most of actual work would take place.</span></span> <span data-ttu-id="f16ce-151">ビジネス ロジック、長時間実行されるプロセス、大規模なソリューションに対するパズルのピースを表します。</span><span class="sxs-lookup"><span data-stu-id="f16ce-151">They represent the business logic, long running processes, and the puzzle pieces to a larger solution.</span></span>

<span data-ttu-id="f16ce-152">`ActivityTriggerAttribute` は、`DurableActivityContext` 型の関数パラメーターに注釈を付けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-152">The `ActivityTriggerAttribute` is used to annotate a function parameter of type `DurableActivityContext`.</span></span> <span data-ttu-id="f16ce-153">注釈を使用すると、アクティビティ関数としての使用を意図した関数であることを、ランタイムに通知できます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-153">Using the annotation informs the runtime that the function is intended to be used as an activity function.</span></span> <span data-ttu-id="f16ce-154">アクティビティ関数への入力値は、`DurableActivityContext` パラメーターの `GetInput<T>` メソッドを使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-154">Input values to activity functions are retrieved using the `GetInput<T>` method of the `DurableActivityContext` parameter.</span></span>

<span data-ttu-id="f16ce-155">オーケストレーション関数と同様に、アクティビティ関数の戻り値の型は、void、タスク、または JSON のシリアル化可能な値のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f16ce-155">Similar to orchestration functions, the return types of activity functions must be either void, Task, or a JSON serializable value.</span></span>

<span data-ttu-id="f16ce-156">アクティビティ関数内でスローされたハンドルされない例外は、呼び出し元のオーケストレーター関数に送信され、`TaskFailedException` として示されます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-156">Any unhandled exceptions that get thrown within activity functions will get sent up to the calling orchestrator function and presented as a `TaskFailedException`.</span></span> <span data-ttu-id="f16ce-157">この時点でエラーを捕捉し、オーケストレーターのログに記録して、アクティビティを再試行できます。</span><span class="sxs-lookup"><span data-stu-id="f16ce-157">At this point, the error can be caught and logged in the orchestrator, and the activity can be retried.</span></span>

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a><span data-ttu-id="f16ce-158">推奨リソース</span><span class="sxs-lookup"><span data-stu-id="f16ce-158">Recommended resources</span></span>

- [<span data-ttu-id="f16ce-159">Durable Functions</span><span class="sxs-lookup"><span data-stu-id="f16ce-159">Durable Functions</span></span>](/azure/azure-functions/durable-functions-overview)
- [<span data-ttu-id="f16ce-160">Durable Functions のバインド</span><span class="sxs-lookup"><span data-stu-id="f16ce-160">Bindings for Durable Functions</span></span>](/azure/azure-functions/durable-functions-bindings)
- [<span data-ttu-id="f16ce-161">Durable Functions でのインスタンスの管理</span><span class="sxs-lookup"><span data-stu-id="f16ce-161">Manage instances in Durable Functions</span></span>](/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
><span data-ttu-id="f16ce-162">[前へ](event-grid.md)
>[次へ](orchestration-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="f16ce-162">[Previous](event-grid.md)
[Next](orchestration-patterns.md)</span></span>
