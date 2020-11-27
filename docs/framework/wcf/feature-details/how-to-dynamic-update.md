---
title: '方法: 動的な更新'
ms.date: 03/30/2017
ms.assetid: 9b8f6e0d-edab-4a7e-86e3-8c66bebc64bb
ms.openlocfilehash: a12d480163bb579f34d006ae1837ed4392bf47ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265545"
---
# <a name="how-to-dynamic-update"></a><span data-ttu-id="db7a4-102">方法: 動的な更新</span><span class="sxs-lookup"><span data-stu-id="db7a4-102">How To: Dynamic Update</span></span>

<span data-ttu-id="db7a4-103">ここでは、ルーティング構成の作成および動的な更新に必要な基本的手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-103">This topic outlines the basic steps required to create and dynamically update the routing configuration.</span></span> <span data-ttu-id="db7a4-104">この例では、ルーティングの初期構成を構成ファイルから取得し、すべてのメッセージを regularCalc 電卓サービスにルーティングします。ただし、これは、roundingCalc のサービスの提供先となるエンドポイントを変更するために、後でプログラムによって更新されます。</span><span class="sxs-lookup"><span data-stu-id="db7a4-104">In this example, the initial routing configuration is obtained from the configuration file and routes all messages to the regularCalc calculator service; however, it is subsequently updated programmatically in order to change the destination endpoint the roundingCalc service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db7a4-105">多くの実装では、構成が完全に動的で、既定の構成に依存しません。ただし、このトピックのシナリオのように、サービスの開始時は既定の構成の状態を使用することが望ましい場合もあります。</span><span class="sxs-lookup"><span data-stu-id="db7a4-105">In many implementations, configuration will be fully dynamic and will not rely on a default configuration; however, there are some scenarios, such as the one in this topic, where it is desirable to have a default configuration state when the service starts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db7a4-106">動的な更新はメモリ内のみで実行され、構成ファイルが変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="db7a4-106">Dynamic updates occur only in memory, and do not result in the modification of configuration files.</span></span>  
  
 <span data-ttu-id="db7a4-107">regularCalc でも roundingCalc でも、同じ加算、減算、乗算、および除算の操作がサポートされますが、roundingCalc では、すべての計算結果が、四捨五入によって最も近い整数値に変換されてから返されます。</span><span class="sxs-lookup"><span data-stu-id="db7a4-107">Both regularCalc and roundingCalc support the same operations of add, subtract, multiply and divide; however, roundingCalc rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="db7a4-108">regularCalc サービスにすべてのメッセージをルーティングするようにサービスを構成するには、構成ファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="db7a4-108">A configuration file is used to configure the service to route all messages to the regularCalc service.</span></span> <span data-ttu-id="db7a4-109">ルーティング サービスが開始されると、<xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> を使用して、メッセージを roundingCalc サービスにルーティングするようにルーティング サービスが構成されます。</span><span class="sxs-lookup"><span data-stu-id="db7a4-109">After the Routing Service has been started, <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> is used to reconfigure the service to route messages to the roundingCalc service.</span></span>  
  
### <a name="implement-initial-configuration"></a><span data-ttu-id="db7a4-110">初期構成の実装</span><span class="sxs-lookup"><span data-stu-id="db7a4-110">Implement Initial Configuration</span></span>  
  
1. <span data-ttu-id="db7a4-111">サービスによって公開されるサービス エンドポイントを指定することによって、ルーティング サービスの基本的な構成を作成します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-111">Create the basic Routing Service Configuration by specifying the service endpoints exposed by the service.</span></span> <span data-ttu-id="db7a4-112">次の例では、メッセージの受信に使用される、単一のサービス エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-112">The following example defines a single service endpoint, which will be used to receive messages.</span></span> <span data-ttu-id="db7a4-113">また、regularCalc へのメッセージ送信に使用するクライアント エンドポイントも定義します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-113">It also defines a client endpoint that will be used to send messages to the regularCalc.</span></span>  
  
    ```xml  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <client>  
    <!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    ```  
  
2. <span data-ttu-id="db7a4-114">送信先エンドポイントへのメッセージのルーティングに使用するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-114">Define the filter used to route messages to the destination endpoints.</span></span> <span data-ttu-id="db7a4-115">この例では、MatchAll フィルターを使用して、前に定義した regularCalcEndpoint にすべてのメッセージをルーティングしています。</span><span class="sxs-lookup"><span data-stu-id="db7a4-115">For this example, the MatchAll filter is used to route all messages to the regularCalcEndpoint defined previously.</span></span> <span data-ttu-id="db7a4-116">次の例では、フィルターおよびフィルター テーブルを定義します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-116">The following example defines the filter and filter table.</span></span>  
  
    ```xml  
    <filters>  
      <!--define the message filter-->  
      <filter name="MatchAllFilter" filterType="MatchAll"/>  
    </filters>  
    <filterTables>  
      <filterTable name="filterTable1">  
          <!--add the filter to the message filter table-->  
          <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
      </filterTable>  
    </filterTables>  
    ```  
  
3. <span data-ttu-id="db7a4-117">フィルター テーブルに含まれているフィルターと照合して受信メッセージを評価するには、ルーティング動作を使用して、フィルター テーブルをサービス エンドポイントと関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="db7a4-117">To evaluate incoming messages against the filters contained in the filter table, you must associate the filter table with the service endpoints by using the routing behavior.</span></span> <span data-ttu-id="db7a4-118">次の例は、"filterTable1" をサービスエンドポイントに関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="db7a4-118">The following example demonstrates associating "filterTable1" with the service endpoint.</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="implement-dynamic-configuration"></a><span data-ttu-id="db7a4-119">動的構成の実装</span><span class="sxs-lookup"><span data-stu-id="db7a4-119">Implement Dynamic Configuration</span></span>  

 <span data-ttu-id="db7a4-120">ルーティング サービスの動的構成は、コードでのみ実行できます。これを実行するには、新しい <xref:System.ServiceModel.Routing.RoutingConfiguration> を作成し、<xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> を使用して現在の構成を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="db7a4-120">Dynamic configuration of the Routing Service can only be performed in code by creating a new <xref:System.ServiceModel.Routing.RoutingConfiguration> and using <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> to replace the current configuration.</span></span>  <span data-ttu-id="db7a4-121">この例では、ルーティング サービスがコンソール アプリケーション内に自己ホストされます。</span><span class="sxs-lookup"><span data-stu-id="db7a4-121">For this example, the Routing Service is self-hosted within a console application.</span></span> <span data-ttu-id="db7a4-122">アプリケーションが起動したら、ルーティングの構成を変更できます。メッセージのルーティング先のエンドポイントを構成するには、コンソール ウィンドウで「regular」または「rounding」と入力します。「regular」と入力した場合は regularCalc が、「rounding」と入力した場合は roundingCalc になります。</span><span class="sxs-lookup"><span data-stu-id="db7a4-122">After the application has started, you can modify the routing configuration by entering ‘regular’ or ‘rounding’ at the console window to configure the destination endpoint that messages are routed to; regularCalc when ‘regular’ is entered, otherwise roundingCalc when ‘rounding’ is entered.</span></span>  
  
1. <span data-ttu-id="db7a4-123">ルーティング サービスをサポートするには、次の using ステートメントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db7a4-123">The following using statements must be added in order to support the Routing Service.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.ServiceModel;  
    using System.ServiceModel.Channels;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Routing;  
    ```  
  
2. <span data-ttu-id="db7a4-124">ルーティング サービスをコンソール アプリケーションとして自己ホストするには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-124">The following code is used to self-host the Routing Service as a console application.</span></span> <span data-ttu-id="db7a4-125">これは、前の手順で説明した構成を使用してルーティング サービスを初期化します。この構成は、アプリケーション構成ファイルに保持されています。</span><span class="sxs-lookup"><span data-stu-id="db7a4-125">This initializes the Routing Service using the configuration described in the previous step, which is contained within the application configuration file.</span></span> <span data-ttu-id="db7a4-126">while ループには、ルーティング構成の変更に使用されるコードが設定されています。</span><span class="sxs-lookup"><span data-stu-id="db7a4-126">The while loop contains the code used to change the routing configuration.</span></span>  
  
    ```csharp  
    // Host the service within this EXE console application.  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost =  
            new ServiceHost(typeof(RoutingService)))  
        {  
            // Open the ServiceHost to create listeners
            // and start listening for messages.  
            Console.WriteLine("The Routing Service configured, opening....");  
            serviceHost.Open();  
            Console.WriteLine("The Routing Service is now running.");  
             Console.WriteLine("Type 'quit' to terminate router.");  
             Console.WriteLine("<ENTER> to change routing configuration.");  
             while (Console.ReadLine() != "quit")  
             {  
            ....  
            }  
        }  
    }  
    ```  
  
3. <span data-ttu-id="db7a4-127">ルーティング構成を動的に更新するには、新しいルーティング構成を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="db7a4-127">To dynamically update the routing configuration, a new routing configuration must be created.</span></span> <span data-ttu-id="db7a4-128">作成する構成には、新しいルーティング構成に必要なすべてのエンドポイント、フィルター、およびフィルター テーブルの情報が含まれている必要があります。これは、既存のルーティング構成全体が、この構成に置き換えられるためです。</span><span class="sxs-lookup"><span data-stu-id="db7a4-128">This must contain all endpoints, filters and filter tables that are required for the new routing configuration, as it will completely replace the existing routing configuration.</span></span> <span data-ttu-id="db7a4-129">新しいルーティング構成を使用するには、<xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> を呼び出して新しい構成を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="db7a4-129">In order to use the new routing configuration, you must invoke <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> and pass the new configuration.</span></span>  
  
     <span data-ttu-id="db7a4-130">前の手順で定義した while ループに次のコードを追加して、ユーザー入力を基にサービスを再構成できるようにします。</span><span class="sxs-lookup"><span data-stu-id="db7a4-130">Add the following code to the while loop defined previously to allow the service to be reconfigured based on user input.</span></span>  
  
    ```csharp  
    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
    string destEndpoint = Console.ReadLine();  
    // Create a new RoutingConfiguration  
    RoutingConfiguration rc = new RoutingConfiguration();  
    // Determine the endpoint to configure for  
    switch (destEndpoint)  
    {  
        case "regular":  
            // Define the destination endpoint  
            ServiceEndpoint regularCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        case "rounding":  
            // Define the destination endpoint  
            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
               ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
               new NetTcpBinding(),  
               new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
            // Create a MatchAll filter and add to the filter table  
            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
            // Use ApplyConfiguration to update the Routing Service  
            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
            Console.WriteLine("Applied new routing configuration.");  
            break;  
        default:  
            Console.WriteLine("Incorrect value entered, no change.");  
            break;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="db7a4-131">新しい RoutingConfiguration を提供するメソッドは RoutingExtension service サービス拡張に含まれているため、新しい RoutingConfiguration オブジェクトは、ServiceHost または ServiceExtension (別の ServiceExtension など) への参照を含む WCF 拡張モデル、またはこの参照を取得できる WCF 拡張モデル内の任意の場所で提供できます。</span><span class="sxs-lookup"><span data-stu-id="db7a4-131">Since the method for providing a new RoutingConfiguration is contained in the RoutingExtension service extension, new RoutingConfiguration objects can be provided anywhere in the WCF extensibility model that has or can obtain a reference to the ServiceHost or ServiceExtensions (such as in another ServiceExtension).</span></span>
  
## <a name="example"></a><span data-ttu-id="db7a4-132">例</span><span class="sxs-lookup"><span data-stu-id="db7a4-132">Example</span></span>  

<span data-ttu-id="db7a4-133">この例で使用されているコンソールアプリケーションの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-133">The following is a complete listing of the console application used in this example:</span></span>
  
```csharp
//-----------------------------------------------------------------  
//  Copyright (c) Microsoft Corporation.  All Rights Reserved.  
//-----------------------------------------------------------------  
  
using System;  
using System.Collections.Generic;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.ServiceModel.Description;  
using System.ServiceModel.Dispatcher;  
using System.ServiceModel.Routing;  
  
namespace Microsoft.Samples.AdvancedFilters  
{  
    public class Router  
    {  
        // Host the service within this EXE console application.  
        public static void Main()  
        {
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
            {  
                // Open the ServiceHost to create listeners
                // and start listening for messages.  
                Console.WriteLine("The Routing Service configured, opening....");  
                serviceHost.Open();  
                Console.WriteLine("The Routing Service is now running.");  
                Console.WriteLine("Type 'quit' to terminate router.");  
                Console.WriteLine("<ENTER> to change routing configuration.");  
                while (Console.ReadLine() != "quit")  
                {  
                    Console.WriteLine("Enter 'regular' or 'rounding' to set the destination endpoint:");  
                    string destEndpoint = Console.ReadLine();  
                    // Create a new RoutingConfiguration  
                    RoutingConfiguration rc = new RoutingConfiguration();  
                    // Determine the endpoint to configure for  
                    switch (destEndpoint)  
                    {  
                        case "regular":  
                            // Define the destination endpoint  
                            ServiceEndpoint regularCalc = new ServiceEndpoint(  
                            ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                            new NetTcpBinding(),  
                            new EndpointAddress("net.tcp://localhost:9090/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { regularCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        case "rounding":  
                            // Define the destination endpoint  
                            ServiceEndpoint roundingCalc = new ServiceEndpoint(  
                                ContractDescription.GetContract(typeof(IRequestReplyRouter)),  
                                new NetTcpBinding(),  
                                new EndpointAddress("net.tcp://localhost:8080/servicemodelsamples/service/"));  
                            // Create a MatchAll filter and add to the filter table  
                            rc.FilterTable.Add(new MatchAllMessageFilter(), new List<ServiceEndpoint> { roundingCalc });  
                            // Use ApplyConfiguration to update the Routing Service  
                            serviceHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc);  
                            Console.WriteLine("Applied new routing configuration.");  
                            break;  
                        default:  
                            Console.WriteLine("Incorrect value entered, no change.");  
                            break;  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="db7a4-134">例</span><span class="sxs-lookup"><span data-stu-id="db7a4-134">Example</span></span>  

<span data-ttu-id="db7a4-135">この例で使用される構成ファイルの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="db7a4-135">The following is a complete listing of the configuration file used in this example:</span></span>
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoint for the Routing Service-->  
        <endpoint address="calculator"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoint-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
  
      <filters>  
        <!--define the message filter-->  
        <filter name="MatchAllFilter" filterType="MatchAll"/>  
      </filters>  
      <filterTables>  
        <filterTable name="filterTable1">  
            <!--add the filter to the message filter table-->  
            <add filterName="MatchAllFilter" endpointName="regularCalcEndpoint"/>  
        </filterTable>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="db7a4-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="db7a4-136">See also</span></span>

- [<span data-ttu-id="db7a4-137">ルーティング サービス</span><span class="sxs-lookup"><span data-stu-id="db7a4-137">Routing Services</span></span>](../samples/routing-services.md)
