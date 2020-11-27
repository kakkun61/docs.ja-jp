---
title: '方法: 探索プロキシで登録される探索可能なサービスの実装する'
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: 1e6b57193d25da7e5c9a865525dd5e9ea21110b0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254260"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="7eb94-102">方法: 探索プロキシで登録される探索可能なサービスの実装する</span><span class="sxs-lookup"><span data-stu-id="7eb94-102">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>

<span data-ttu-id="7eb94-103">これは、探索プロキシの実装方法に関する 4 つのトピックのうちの 2 番目のトピックです。</span><span class="sxs-lookup"><span data-stu-id="7eb94-103">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="7eb94-104">前のトピック「 [方法: 探索プロキシを実装](how-to-implement-a-discovery-proxy.md)する」では、探索プロキシを実装しています。</span><span class="sxs-lookup"><span data-stu-id="7eb94-104">In the previous topic, [How to: Implement a Discovery Proxy](how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="7eb94-105">このトピックでは、アナウンスメッセージ (および) を探索プロキシに送信する WCF サービスを作成し `Hello` `Bye` ます。これにより、探索プロキシに登録および登録解除が行われます。</span><span class="sxs-lookup"><span data-stu-id="7eb94-105">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>

### <a name="to-define-the-service-contract"></a><span data-ttu-id="7eb94-106">サービス コントラクトを定義するには</span><span class="sxs-lookup"><span data-stu-id="7eb94-106">To define the service contract</span></span>

1. <span data-ttu-id="7eb94-107">新しいコンソール アプリケーション プロジェクトを、`DiscoveryProxyExample` という `Service` ソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>

2. <span data-ttu-id="7eb94-108">次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-108">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="7eb94-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7eb94-109">System.ServiceModel</span></span>

    2. <span data-ttu-id="7eb94-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="7eb94-110">System.ServiceModel.Discovery</span></span>

3. <span data-ttu-id="7eb94-111">新しいクラスを `CalculatorService` プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-111">Add a new class to the project called `CalculatorService`.</span></span>

4. <span data-ttu-id="7eb94-112">次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-112">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    ```

5. <span data-ttu-id="7eb94-113">CalculatorService.cs でサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-113">Within CalculatorService.cs, define the service contract.</span></span>

    ```csharp
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
    ```

6. <span data-ttu-id="7eb94-114">また、CalculatorService.cs でサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-114">Also within CalculatorService.cs, implement the service contract.</span></span>

    ```csharp
    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
    ```

### <a name="to-host-the-service"></a><span data-ttu-id="7eb94-115">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="7eb94-115">To host the service</span></span>

1. <span data-ttu-id="7eb94-116">プロジェクトの作成時に生成された Program.cs ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="7eb94-116">Open the Program.cs file that was generated when you created the project.</span></span>

2. <span data-ttu-id="7eb94-117">次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-117">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="7eb94-118">`Main()` メソッド内に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-118">Within the `Main()` method, add the following code:</span></span>

    ```csharp
    // Define the base address of the service
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
    // Define the endpoint address where announcement messages will be sent
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Create the service host
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
    try
    {
        // Add a service endpoint
        ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
            new NetTcpBinding(), string.Empty);

        // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
            new EndpointAddress(announcementEndpointAddress));

        // Create a ServiceDiscoveryBehavior and add the announcement endpoint
        ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
        serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

        // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable
        serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

        // Start listening for messages
        serviceHost.Open();

        Console.WriteLine("Calculator Service started at {0}", baseAddress);
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        serviceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (serviceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        serviceHost.Abort();
    }
    ```

<span data-ttu-id="7eb94-119">これで、探索サービスの実装が完了しました。</span><span class="sxs-lookup"><span data-stu-id="7eb94-119">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="7eb94-120">[「方法: 探索プロキシを使用してサービスを検索するクライアントアプリケーションを実装](client-app-discovery-proxy-to-find-a-service.md)する」に進みます。</span><span class="sxs-lookup"><span data-stu-id="7eb94-120">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](client-app-discovery-proxy-to-find-a-service.md).</span></span>

## <a name="example"></a><span data-ttu-id="7eb94-121">例</span><span class="sxs-lookup"><span data-stu-id="7eb94-121">Example</span></span>

 <span data-ttu-id="7eb94-122">このトピックで使用するコード全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7eb94-122">This is the full listing of the code used in this topic.</span></span>

```csharp
// CalculatorService.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;

namespace Microsoft.Samples.Discovery
{
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }

    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
  
        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
// Program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
            try
            {
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
                    new NetTcpBinding(), string.Empty);

                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
                    new EndpointAddress(announcementEndpointAddress));

                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

                // Make the service discoverable
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

                serviceHost.Open();

                Console.WriteLine("Calculator Service started at {0}", baseAddress);
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                serviceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (serviceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                serviceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="7eb94-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="7eb94-123">See also</span></span>

- [<span data-ttu-id="7eb94-124">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="7eb94-124">WCF Discovery</span></span>](wcf-discovery.md)
- [<span data-ttu-id="7eb94-125">方法: 探索プロキシを実装する</span><span class="sxs-lookup"><span data-stu-id="7eb94-125">How to: Implement a Discovery Proxy</span></span>](how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="7eb94-126">方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションを実装する</span><span class="sxs-lookup"><span data-stu-id="7eb94-126">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
