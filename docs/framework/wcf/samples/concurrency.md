---
title: コンカレンシー
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 69692f48cc1f45057e865a3908ddf41afc599bb1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243257"
---
# <a name="concurrency"></a><span data-ttu-id="4580b-102">コンカレンシー</span><span class="sxs-lookup"><span data-stu-id="4580b-102">Concurrency</span></span>

<span data-ttu-id="4580b-103">コンカレンシーのサンプルでは、<xref:System.ServiceModel.ServiceBehaviorAttribute> を <xref:System.ServiceModel.ConcurrencyMode> 列挙体と共に使用する方法を示します。この列挙体は、サービスのインスタンスがメッセージを順番に処理するか、または同時に処理するかを制御します。</span><span class="sxs-lookup"><span data-stu-id="4580b-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="4580b-104">このサンプルは、サービスコントラクトを実装する [はじめに](getting-started-sample.md)に基づいてい `ICalculator` ます。</span><span class="sxs-lookup"><span data-stu-id="4580b-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="4580b-105">このサンプルでは、`ICalculatorConcurrency` から継承される新しいコントラクト `ICalculator` を定義します。これによって、サービスのコンカレンシーの状態を検査するための 2 つの操作が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4580b-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="4580b-106">コンカレンシー設定を変更してから、クライアントを実行して動作の変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="4580b-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="4580b-107">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="4580b-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4580b-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4580b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4580b-109">選択可能なコンカレンシー モードは次の 3 つです。</span><span class="sxs-lookup"><span data-stu-id="4580b-109">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="4580b-110">`Single`: 各サービス インスタンスは、一度に 1 つのメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="4580b-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="4580b-111">これが既定のコンカレンシー モードです。</span><span class="sxs-lookup"><span data-stu-id="4580b-111">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="4580b-112">`Multiple`: 各サービス インスタンスは、同時に複数のメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="4580b-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="4580b-113">このコンカレンシー モードを使用するには、サービスの実装がスレッドセーフである必要があります。</span><span class="sxs-lookup"><span data-stu-id="4580b-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="4580b-114">`Reentrant`: 各サービス インスタンスは、一度に 1 つのメッセージを処理しますが、再入可能呼び出しを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="4580b-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="4580b-115">サービスは、呼び出し元である場合にのみ、これらの呼び出しを受け入れます。再入は、 [ConcurrencyMode](concurrencymode-reentrant.md) サンプルで説明されています。</span><span class="sxs-lookup"><span data-stu-id="4580b-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="4580b-116">コンカレンシーの使用は、インスタンス化モードに関連します。</span><span class="sxs-lookup"><span data-stu-id="4580b-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="4580b-117">ph x="1" /&gt; インスタンス化では、各メッセージが新しいサービス インスタンスによって処理されるため、コンカレンシーは関係しません。</span><span class="sxs-lookup"><span data-stu-id="4580b-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="4580b-118">ph x="1" /&gt; インスタンス化では、<xref:System.ServiceModel.ConcurrencyMode.Single> と <xref:System.ServiceModel.ConcurrencyMode.Multiple> のいずれかのコンカレンシーが関係します。これは 1 つのインスタンスがメッセージを順番に処理するか、同時に処理するかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="4580b-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="4580b-119">ph x="1" /&gt; インスタンス化では、どのコンカレンシー モードも関係する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4580b-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="4580b-120">サービス クラスは、`[ServiceBehavior(ConcurrencyMode=<setting>)]` 属性を使用してコンカレンシー動作を指定します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4580b-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="4580b-121">行のコメント化を変更して、`Single` および `Multiple` のコンカレンシー モードをそれぞれ試してみてください。</span><span class="sxs-lookup"><span data-stu-id="4580b-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="4580b-122">コンカレンシー モードを変更したら、サービスを再ビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4580b-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="4580b-123">サンプルの既定の設定では、<xref:System.ServiceModel.ConcurrencyMode.Multiple> インスタンス化と <xref:System.ServiceModel.InstanceContextMode.Single> コンカレンシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4580b-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="4580b-124">クライアント コードは、非同期プロキシを使用するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="4580b-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="4580b-125">これにより、クライアントはサービスを呼び出した後に、応答を待たずに次の呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4580b-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="4580b-126">サービスのコンカレンシー モードの動作の違いを観察してください。</span><span class="sxs-lookup"><span data-stu-id="4580b-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="4580b-127">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4580b-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4580b-128">実行中のサービスのコンカレンシー モードが表示され、各操作が呼び出され、その後で操作数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4580b-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="4580b-129">コンカレンシー モードが `Multiple` の場合、結果が返される順序は呼び出された順序とは異なります。サービスは複数のメッセージを同時に実行するからです。</span><span class="sxs-lookup"><span data-stu-id="4580b-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="4580b-130">コンカレンシー モードを `Single` に変更すると、結果は呼び出された順序どおりに返されます。サービスは各メッセージを順次処理するからです。</span><span class="sxs-lookup"><span data-stu-id="4580b-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="4580b-131">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4580b-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4580b-132">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="4580b-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4580b-133">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4580b-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4580b-134">Svcutil.exe を使用してプロキシクライアントを生成する場合は、オプションが含まれていることを確認してください `/async` 。</span><span class="sxs-lookup"><span data-stu-id="4580b-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="4580b-135">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4580b-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="4580b-136">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4580b-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4580b-137">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4580b-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4580b-138">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4580b-138">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4580b-139">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="4580b-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4580b-140">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4580b-140">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
