---
title: '方法: フィルターの使用'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 149c0809820d6a4a9c8dabfb545258b9a3ffb40b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280846"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="79fe4-102">方法: フィルターの使用</span><span class="sxs-lookup"><span data-stu-id="79fe4-102">How To: Use Filters</span></span>

<span data-ttu-id="79fe4-103">ここでは、複数のフィルターを使用したルーティング構成を作成するために必要な基本手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="79fe4-104">この例では、メッセージが、電卓サービスの 2 つの実装である regularCalc および roundingCalc にルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="79fe4-105">これらの実装は両方とも同じ操作をサポートしますが、片方のサービスでは、値を返す前にすべての計算を最も近い整数値に丸めます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="79fe4-106">クライアント アプリケーションが、丸め処理を行うバージョンのサービスを使用するかどうかを表示可能である必要がありますが、優先するサービスが示されていない場合は、メッセージが 2 つのサービス間で負荷分散されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="79fe4-107">次の操作が両方のサービスによって公開されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="79fe4-108">追加</span><span class="sxs-lookup"><span data-stu-id="79fe4-108">Add</span></span>  
  
- <span data-ttu-id="79fe4-109">減算</span><span class="sxs-lookup"><span data-stu-id="79fe4-109">Subtract</span></span>  
  
- <span data-ttu-id="79fe4-110">乗算</span><span class="sxs-lookup"><span data-stu-id="79fe4-110">Multiply</span></span>  
  
- <span data-ttu-id="79fe4-111">除算</span><span class="sxs-lookup"><span data-stu-id="79fe4-111">Divide</span></span>  
  
 <span data-ttu-id="79fe4-112">どちらのサービスも同じ操作を実装するため、アクション フィルターを使用することはできません。メッセージで指定されるアクションが一意にならないためです。</span><span class="sxs-lookup"><span data-stu-id="79fe4-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="79fe4-113">代わりに、メッセージが適切なエンドポイントに必ずルーティングされるための追加作業が必要になります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="79fe4-114">一意なデータを特定する</span><span class="sxs-lookup"><span data-stu-id="79fe4-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="79fe4-115">両方のサービス実装が同じ操作を処理し、返すデータを除いて基本的に同一であるため、クライアント アプリケーションから送信されるメッセージに含まれる基本データでは、要求をルーティングする方法を特定できません。</span><span class="sxs-lookup"><span data-stu-id="79fe4-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="79fe4-116">ただし、クライアント アプリケーションでメッセージに一意のヘッダー値を追加すると、この値を使用して、メッセージのルーティング方法を決定できます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="79fe4-117">この例では、クライアント アプリケーションで丸め処理を行う電卓を使ってメッセージを処理する必要がある場合に、次のコードを使用してカスタム ヘッダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="79fe4-118">これで、XPath フィルターを使用して、メッセージにこのヘッダーが含まれるかどうかを確認し、このヘッダーを持つメッセージを roundCalc サービスにルーティングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="79fe4-119">さらに、ルーティング サービスが、EndpointName、EndpointAddress、または PrefixEndpointAddress の各フィルターと共に使用できる仮想サービス エンドポイントを 2 つ公開し、クライアント アプリケーションの要求の送信先エンドポイントに基づいて、受信メッセージを特定の電卓の実装に一意にルーティングします。</span><span class="sxs-lookup"><span data-stu-id="79fe4-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="79fe4-120">エンドポイントを定義する</span><span class="sxs-lookup"><span data-stu-id="79fe4-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="79fe4-121">ルーティング サービスで使用するエンドポイントを定義する場合は、最初にクライアントおよびサービスが使用するチャンネルの形状を決める必要があります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="79fe4-122">このシナリオでは、両方の送信先サービスで要求/応答パターンが使用されるため、<xref:System.ServiceModel.Routing.IRequestReplyRouter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="79fe4-123">次の例では、ルーティング サービスが公開するサービス エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="79fe4-124">この構成では、ルーティング サービスは 3 つの別個のエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="79fe4-125">実行時の選択に応じて、クライアント アプリケーションは、これらのアドレスの 1 つにメッセージを送ります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="79fe4-126">"仮想" サービスエンドポイント ("丸め処理/計算" または "regular/calculator") のいずれかに到着したメッセージは、対応する電卓の実装に転送されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="79fe4-127">クライアント アプリケーションが特定のエンドポイントに要求を送信しない場合、メッセージの送信先は標準のエンドポイントになります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="79fe4-128">選択されたエンドポイントにかかわらず、クライアント アプリケーションでは、メッセージにカスタム ヘッダーを含めるように選択することで、丸め処理を行う電卓の実装にメッセージを転送するように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="79fe4-129">次の例では、ルーティング サービスによるメッセージのルーティング先であるクライアント (送信先) エンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="79fe4-130">これらのエンドポイントは、特定のフィルターと一致したメッセージの送信先エンドポイントを示すために、フィルター テーブルで使用されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="79fe4-131">[フィルターの定義]</span><span class="sxs-lookup"><span data-stu-id="79fe4-131">Define Filters</span></span>  
  
1. <span data-ttu-id="79fe4-132">クライアントアプリケーションによってメッセージに追加される "RoundingCalculator" カスタムヘッダーに基づいてメッセージをルーティングするには、XPath クエリを使用してこのヘッダーの存在を確認するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="79fe4-133">このヘッダーはカスタム名前空間を使用して定義されるため、XPath クエリで使用されるカスタム名前空間プレフィックス "custom" を定義する名前空間エントリも追加します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="79fe4-134">次の例では、必要なルーティング セクション、名前空間のテーブル、および XPath フィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="79fe4-135">この **Messagefilter** は、メッセージ内で "丸め処理" の値を含む RoundingCalculator ヘッダーを検索します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="79fe4-136">このヘッダーは、メッセージを roundingCalc サービスにルーティングする必要があることを示すために、クライアント側で設定されたものです。</span><span class="sxs-lookup"><span data-stu-id="79fe4-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="79fe4-137">S12 名前空間プレフィックスは、既定で名前空間テーブルに定義され、名前空間を表し `http://www.w3.org/2003/05/soap-envelope` ます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="79fe4-138">また、2 つの仮想エンドポイントで受信したメッセージがあるかどうかを検索するフィルターも定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="79fe4-139">最初の仮想エンドポイントは、"regular/calculator" エンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="79fe4-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="79fe4-140">クライアントは、メッセージを regularCalc サービスにルーティングする必要があることを示すために、このエンドポイントに要求を送信できます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="79fe4-141">次の構成では、<xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> を使用するフィルターを定義して、filterData で指定された名前のエンドポイントでメッセージが受信されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="79fe4-142">"電卓 Atorendpoint" という名前のサービスエンドポイントによってメッセージが受信された場合、このフィルターはに評価さ `true` れます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="79fe4-143">次に、roundingEndpoint のアドレスに送信されたメッセージがあるかどうかを検索するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="79fe4-144">クライアントは、メッセージを roundingCalc サービスにルーティングする必要があることを示すために、このエンドポイントに要求を送信できます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="79fe4-145">次の構成では、を使用して、 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> "丸め処理/計算" エンドポイントでメッセージが到着したかどうかを判断するフィルターを定義します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="79fe4-146">で始まるアドレスでメッセージが受信された場合、 `http://localhost/routingservice/router/rounding/` このフィルターは **true** と評価されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="79fe4-147">この構成で使用されるベースアドレスがで、 `http://localhost/routingservice/router` roundingEndpoint に指定されたアドレスが "丸め/計算" であるため、このエンドポイントとの通信に使用される完全なアドレスは `http://localhost/routingservice/router/rounding/calculator` 、このフィルターに一致します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="79fe4-148">PrefixEndpointAddress フィルターは、一致するメッセージの確認を行う際にホスト名を評価しません。これは、1 つのホストへの参照を表す際に使用できるホスト名にはさまざまな種類があり、そのすべてが、クライアント アプリケーションからホストを参照するための正しい方法であるためです。</span><span class="sxs-lookup"><span data-stu-id="79fe4-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="79fe4-149">たとえば、次の例はすべて、同じホストを参照します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-149">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="79fe4-150">localhost</span><span class="sxs-lookup"><span data-stu-id="79fe4-150">localhost</span></span>  
    > - <span data-ttu-id="79fe4-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="79fe4-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="79fe4-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="79fe4-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="79fe4-153">最後のフィルターでは、標準のエンドポイントで受信する、カスタム ヘッダーのないメッセージのルーティングがサポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="79fe4-154">このシナリオでは、regularCalc サービスと roundingCalc サービスで交互にメッセージが処理されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="79fe4-155">これらのメッセージの "ラウンドロビン" ルーティングをサポートするには、処理されたメッセージごとに1つのフィルターインスタンスが一致するようにするカスタムフィルターを使用します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="79fe4-156">次のコードでは、RoundRobinMessageFilter のインスタンスを 2 つ定義します。これらは、交互に使用されることを示すために、グループ化されています。</span><span class="sxs-lookup"><span data-stu-id="79fe4-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="79fe4-157">実行中に、このフィルターの種類は、同じグループで 1 つのコレクションとして構成されている、この種類の定義済みフィルター インスタンスすべてを相次いで使用します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="79fe4-158">これにより、このカスタムフィルターによって処理されたメッセージは、とのどちらを返すかによって異なり `true` `RoundRobinFilter1` `RoundRobinFilter2` ます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="79fe4-159">フィルター テーブルを定義する</span><span class="sxs-lookup"><span data-stu-id="79fe4-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="79fe4-160">フィルターを特定のクライアント エンドポイントと関連付けるには、それぞれをフィルター テーブル内で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="79fe4-161">このサンプルのシナリオでは、フィルターの優先順位設定も使用しています。この設定は省略可能で、フィルターを処理する順序を指定できます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="79fe4-162">優先順位を指定しない場合は、すべてのフィルターが同時に評価されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="79fe4-163">フィルターの優先順位を指定すると、フィルターが処理される順序を制御できますが、ルーティング サービスのパフォーマンスに影響を与える場合があります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="79fe4-164">可能な場合は、フィルターの優先順位設定が不要になるようにフィルター ロジックを構築します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="79fe4-165">次の例では、フィルターテーブルを定義し、前に定義した "Xpath フィルター" を優先度が2のテーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="79fe4-166">このエントリは、がメッセージと一致する場合に、メッセージがにルーティングされることも指定し `XPathFilter` `roundingCalcEndpoint` ます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="79fe4-167">フィルターの優先順位を指定すると、優先順位の高いフィルターから評価されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="79fe4-168">指定された優先順位と一致するフィルターが 1 つまたは複数ある場合は、指定した優先順位より低いレベルのフィルターは評価されません。</span><span class="sxs-lookup"><span data-stu-id="79fe4-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="79fe4-169">ここでは、2 が、指定されている優先順位で最高であり、このレベルの唯一のフィルター エントリです。</span><span class="sxs-lookup"><span data-stu-id="79fe4-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="79fe4-170">フィルター エントリは、メッセージが特定のエンドポイントで受信されているかどうかを、エンドポイント名またはアドレスのプレフィックスを調べることによって確認するために定義されています。</span><span class="sxs-lookup"><span data-stu-id="79fe4-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="79fe4-171">次のように入力することで、これらのフィルター エントリの両方をフィルター テーブルに追加し、メッセージがルーティングされる送信先エンドポイントに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="79fe4-172">前の XPath フィルターがメッセージと一致しない場合にのみ、これらのフィルターが実行されるようにするため、これらのフィルターの優先順位は 1 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="79fe4-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="79fe4-173">優先順位が 1 に設定されているため、これらのフィルターは、優先順位が 2 に設定されているフィルターがメッセージと一致しない場合にのみ評価されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="79fe4-174">また、両方のフィルターに同じ優先順位が指定されているため、これらは同時に評価されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="79fe4-175">これらのフィルターは同時に指定できないため、いずれか一方だけがメッセージと一致する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="79fe4-176">それまでのどのフィルターとも一致しないメッセージは、一般的なサービス エンドポイントを介して受信されており、ルーティング先を示すヘッダー情報が含まれていないメッセージです。</span><span class="sxs-lookup"><span data-stu-id="79fe4-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="79fe4-177">このようなメッセージはカスタム フィルターによって処理され、2 つの電卓サービス間で負荷分散されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="79fe4-178">次の例では、フィルター テーブルにフィルター エントリを追加する方法を示しています。各フィルターは、2 つの送信先エンドポイントのうちの 1 つに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="79fe4-179">これらのエントリの優先順位は 0 に設定されているため、これらのフィルターは、優先順位が高いフィルターがメッセージと一致しない場合にのみ評価されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="79fe4-180">また、両方のフィルターに同じ優先順位が指定されているため、これらは同時に評価されます。</span><span class="sxs-lookup"><span data-stu-id="79fe4-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="79fe4-181">既に説明したように、これらのフィルター定義で使用されるカスタム フィルターは、受信するメッセージごとにどちらかのフィルターだけを `true` と評価します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="79fe4-182">このフィルターを使用して定義されたフィルターは、同じグループ設定を持つ 2 つのフィルターのみであるため、ルーティング サービスが、regularCalcEndpoint と roundingCalcEndpoint に交互に送信するという効果をもたらします。</span><span class="sxs-lookup"><span data-stu-id="79fe4-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="79fe4-183">メッセージをフィルターと照合して評価するには、最初に、フィルター テーブルをメッセージの受信に使用するサービス エンドポイントに関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="79fe4-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="79fe4-184">次の例は、ルーティング動作を使用して、ルーティング テーブルをサービス エンドポイントに関連付ける方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="79fe4-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="79fe4-185">例</span><span class="sxs-lookup"><span data-stu-id="79fe4-185">Example</span></span>  

 <span data-ttu-id="79fe4-186">構成ファイル全体の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="79fe4-186">The following is a complete listing of the configuration file.</span></span>  
  
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
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
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
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79fe4-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="79fe4-187">See also</span></span>

- [<span data-ttu-id="79fe4-188">ルーティング サービス</span><span class="sxs-lookup"><span data-stu-id="79fe4-188">Routing Services</span></span>](../samples/routing-services.md)
