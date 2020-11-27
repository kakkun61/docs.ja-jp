---
title: メッセージ フィルター
ms.date: 03/30/2017
helpviewer_keywords:
- routing [WCF], message filters
ms.assetid: cb33ba49-8b1f-4099-8acb-240404a46d9a
ms.openlocfilehash: a0cc4663b9a3044d0ab80f03479a024acba50a3f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279780"
---
# <a name="message-filters"></a><span data-ttu-id="ecae8-102">メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="ecae8-102">Message Filters</span></span>

<span data-ttu-id="ecae8-103">コンテンツ ベースのルーティングを実装する場合、ルーティング サービスは、アドレス、エンドポイント名、特定の XPath ステートメントなど、メッセージの特定のセクションを確認する <xref:System.ServiceModel.Dispatcher.MessageFilter> 実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-103">To implement content-based routing, the Routing Service uses <xref:System.ServiceModel.Dispatcher.MessageFilter> implementations that inspect specific sections of a message, such as the address, endpoint name, or a specific XPath statement.</span></span> <span data-ttu-id="ecae8-104">[!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] に付属のメッセージ フィルターの中にニーズを満たすものがない場合は、<xref:System.ServiceModel.Dispatcher.MessageFilter> 基本クラスの新しい実装を作成することで、カスタム フィルターを作成できます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-104">If none of the message filters provided with [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] meet your needs, you can create a custom filter by creating a new implementation of the base <xref:System.ServiceModel.Dispatcher.MessageFilter> class.</span></span>  
  
 <span data-ttu-id="ecae8-105">ルーティングサービスを構成する場合は、 <xref:System.ServiceModel.Routing.Configuration.FilterElement> **messagefilter** の種類と、メッセージ内で検索する特定の文字列値など、フィルターの作成に必要なサポートデータを記述するフィルター要素 (オブジェクト) を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecae8-105">When configuring the Routing Service, you must define filter elements (<xref:System.ServiceModel.Routing.Configuration.FilterElement> objects) that describe the type of **MessageFilter** and any supporting data required to create the filter, such as specific string values to search for within the message.</span></span> <span data-ttu-id="ecae8-106">フィルター要素を作成しても、個々のメッセージ フィルターが定義されるだけです。フィルターを使用してメッセージを評価およびルーティングするには、フィルター テーブル (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>) を定義する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ecae8-106">Note that creating the filter elements only defines the individual message filters; to use the filters to evaluate and route messages you must also define a filter table (<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryCollection>).</span></span>  
  
 <span data-ttu-id="ecae8-107">フィルター テーブル内の各エントリは、特定のフィルター要素を参照し、メッセージがフィルターに一致した場合にメッセージのルーティング先となるクライアント エンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-107">Each entry in the filter table references a filter element and specifies the client endpoint that a message will be routed to if the message matches the filter.</span></span> <span data-ttu-id="ecae8-108">フィルター テーブルのエントリでは、バックアップ エンドポイントのコレクション (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>) を指定することもできます。このコレクションは、プライマリ エンドポイントへの送信時に転送エラーが発生した場合に、メッセージの転送先となるエンドポイントのリストを定義します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-108">The filter table entries also allow you to specify a collection of backup endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>), which defines a list of endpoints that the message will be transmitted to in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="ecae8-109">それらのエンドポイントのいずれかで転送が成功するまで、指定された順番でバックアップ エンドポイントへの転送が試行されます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-109">These endpoints will be tried in the order specified until one succeeds.</span></span>  
  
## <a name="message-filters"></a><span data-ttu-id="ecae8-110">メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="ecae8-110">Message Filters</span></span>  

 <span data-ttu-id="ecae8-111">ルーティング サービスが使用するメッセージ フィルターは、メッセージの送信先の名前、SOAP アクション、メッセージの送信先のアドレスまたはアドレス プレフィックスの評価など、一般的なメッセージ選択機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-111">The message filters used by the Routing Service provide common message selection functionality, such as evaluating the name of the endpoint that a message was sent to, the SOAP action, or the address or address prefix that the message was sent to.</span></span> <span data-ttu-id="ecae8-112">フィルターに `AND` 条件を付けて、メッセージが両方のフィルターに一致した場合は、特定のエンドポイントにのみルーティングされるように指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-112">Filters can also be joined with an `AND` condition, so that messages will only be routed to an endpoint if the message matches both filters.</span></span> <span data-ttu-id="ecae8-113">また、<xref:System.ServiceModel.Dispatcher.MessageFilter> の独自の実装を作成することで、カスタム フィルターを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-113">You can also create custom filters by creating your own implementation of <xref:System.ServiceModel.Dispatcher.MessageFilter>.</span></span>  
  
 <span data-ttu-id="ecae8-114">次の表に、ルーティング サービスが使用する <xref:System.ServiceModel.Routing.Configuration.FilterType>、そのメッセージ フィルターを実装するクラス、および必須の <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> パラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-114">The following table lists the <xref:System.ServiceModel.Routing.Configuration.FilterType> used by the Routing Service, the class that implements the specific message filter, and the required <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A> parameters.</span></span>  
  
|<span data-ttu-id="ecae8-115">フィルターの型</span><span class="sxs-lookup"><span data-stu-id="ecae8-115">Filter  Type</span></span>|<span data-ttu-id="ecae8-116">[説明]</span><span class="sxs-lookup"><span data-stu-id="ecae8-116">Description</span></span>|<span data-ttu-id="ecae8-117">フィルター データの意味</span><span class="sxs-lookup"><span data-stu-id="ecae8-117">Filter Data Meaning</span></span>|<span data-ttu-id="ecae8-118">フィルターの例</span><span class="sxs-lookup"><span data-stu-id="ecae8-118">Example Filter</span></span>|  
|------------------|-----------------|-------------------------|--------------------|  
|<span data-ttu-id="ecae8-119">操作</span><span class="sxs-lookup"><span data-stu-id="ecae8-119">Action</span></span>|<span data-ttu-id="ecae8-120"><xref:System.ServiceModel.Dispatcher.ActionMessageFilter> クラスを使用して、特定のアクションを含むメッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-120">Uses the <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> class to match messages containing a specific action.</span></span>|<span data-ttu-id="ecae8-121">フィルター処理するアクション。</span><span class="sxs-lookup"><span data-stu-id="ecae8-121">The action to filter upon.</span></span>|\<filter name="action1" filterType="Action" filterData="http://namespace/contract/operation" />|  
|<span data-ttu-id="ecae8-122">EndpointAddress</span><span class="sxs-lookup"><span data-stu-id="ecae8-122">EndpointAddress</span></span>|<span data-ttu-id="ecae8-123">クラスを使用し <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> て、 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` 特定のアドレスを含むメッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-123">Uses the <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address.</span></span>|<span data-ttu-id="ecae8-124">フィルター処理するアドレス (To ヘッダー)。</span><span class="sxs-lookup"><span data-stu-id="ecae8-124">The address to filter upon (in the To header).</span></span>|\<filter name="address1" filterType="EndpointAddress" filterData="http://host/vdir/s.svc/b"  />|  
|<span data-ttu-id="ecae8-125">EndpointAddressPrefix</span><span class="sxs-lookup"><span data-stu-id="ecae8-125">EndpointAddressPrefix</span></span>|<span data-ttu-id="ecae8-126">クラスを使用し <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> て、 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A>  ==  `true` 特定のアドレスプレフィックスを含むメッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-126">Uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> class, with <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter.IncludeHostNameInComparison%2A> == `true` to match messages containing a specific address prefix.</span></span>|<span data-ttu-id="ecae8-127">最長プレフィックス一致を使用してフィルター処理するアドレス。</span><span class="sxs-lookup"><span data-stu-id="ecae8-127">The address to filter upon using longest prefix matching.</span></span>|\<filter name="prefix1" filterType="EndpointAddressPrefix" filterData="http://host/" />|  
|<span data-ttu-id="ecae8-128">And</span><span class="sxs-lookup"><span data-stu-id="ecae8-128">And</span></span>|<span data-ttu-id="ecae8-129">常に両方の条件を評価してから結果を返す <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-129">Uses the <xref:System.ServiceModel.Dispatcher.StrictAndMessageFilter> class that always evaluates both conditions before returning.</span></span>|<span data-ttu-id="ecae8-130">filterData は使用されません。代わりに、filter1 および filter2 には、対応するメッセージフィルターの名前 (テーブルにも含まれます) が含まれています。これは、 **と** で同時に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ecae8-130">filterData is not used; instead filter1 and filter2 have the names of the corresponding message filters (also in the table), which should be **AND** ed together.</span></span>|\<filter name="and1" filterType="And" filter1="address1" filter2="action1" />|  
|<span data-ttu-id="ecae8-131">カスタム</span><span class="sxs-lookup"><span data-stu-id="ecae8-131">Custom</span></span>|<span data-ttu-id="ecae8-132"><xref:System.ServiceModel.Dispatcher.MessageFilter> クラスを拡張し、文字列を受け取るコンストラクターを持つユーザー定義の型。</span><span class="sxs-lookup"><span data-stu-id="ecae8-132">A user-defined type that extends the <xref:System.ServiceModel.Dispatcher.MessageFilter> class and has a constructor taking a string.</span></span>|<span data-ttu-id="ecae8-133">customType 属性は、作成するクラスの完全修飾型名で、filterData は、フィルターの作成時にコンストラクターに渡す文字列です。</span><span class="sxs-lookup"><span data-stu-id="ecae8-133">The customType attribute is the fully qualified type name of the class to create; filterData is the string to pass to the constructor when creating the filter.</span></span>|\<filter name="custom1" filterType="Custom" customType="CustomAssembly.CustomMsgFilter, CustomAssembly" filterData="Custom Data" />|  
|<span data-ttu-id="ecae8-134">EndpointName</span><span class="sxs-lookup"><span data-stu-id="ecae8-134">EndpointName</span></span>|<span data-ttu-id="ecae8-135"><xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> クラスを使用して、メッセージを受信したサービス エンドポイントの名前を基にメッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-135">Uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> class to match messages based on the name of the service endpoint they arrived on.</span></span>|<span data-ttu-id="ecae8-136">サービスエンドポイントの名前 (例: "serviceEndpoint1")。</span><span class="sxs-lookup"><span data-stu-id="ecae8-136">The name of the service endpoint, for example: "serviceEndpoint1".</span></span>  <span data-ttu-id="ecae8-137">このサービス エンドポイントは、ルーティング サービスで公開されるいずれかのエンドポイントでなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ecae8-137">This should be one of the endpoints exposed on the Routing Service.</span></span>|\<filter name="stock1" filterType="Endpoint" filterData="SvcEndpoint" />|  
|<span data-ttu-id="ecae8-138">MatchAll</span><span class="sxs-lookup"><span data-stu-id="ecae8-138">MatchAll</span></span>|<span data-ttu-id="ecae8-139"><xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-139">Uses the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> class.</span></span> <span data-ttu-id="ecae8-140">このフィルターは、すべての着信メッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-140">This filter matches all arriving messages.</span></span>|<span data-ttu-id="ecae8-141">filterData は使用されません。</span><span class="sxs-lookup"><span data-stu-id="ecae8-141">filterData is not used.</span></span> <span data-ttu-id="ecae8-142">このフィルターは、常にすべてのメッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-142">This filter will always match all messages.</span></span>|\<filter name="matchAll1" filterType="MatchAll" />|  
|<span data-ttu-id="ecae8-143">XPath</span><span class="sxs-lookup"><span data-stu-id="ecae8-143">XPath</span></span>|<span data-ttu-id="ecae8-144"><xref:System.ServiceModel.Dispatcher.XPathMessageFilter> クラスを使用して、メッセージ内の特定の XPath クエリを照合します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-144">Uses the <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> class to match specific XPath queries within the message.</span></span>|<span data-ttu-id="ecae8-145">メッセージの照合時に使用する XPath クエリ。</span><span class="sxs-lookup"><span data-stu-id="ecae8-145">The XPath query to use when matching messages.</span></span>|\<filter name="XPath1" filterType="XPath" filterData="//ns:element" />|  
  
 <span data-ttu-id="ecae8-146">次の例では、XPath、EndpointName、および PrefixEndpointAddress メッセージ フィルターを使用するフィルター エントリを定義しています。</span><span class="sxs-lookup"><span data-stu-id="ecae8-146">The following example defines filter entries that use the XPath, EndpointName, and PrefixEndpointAddress message filters.</span></span> <span data-ttu-id="ecae8-147">また、この例では、RoundRobinFilter1 エントリと RoundRobinFilter2 エントリに対するカスタム フィルターの使用方法も示しています。</span><span class="sxs-lookup"><span data-stu-id="ecae8-147">This example also demonstrates using a custom filter for the RoundRobinFilter1 and RoundRobinFilter2 entries.</span></span>  
  
```xml  
<filters>  
     <filter name="XPathFilter" filterType="XPath"
             filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
     <filter name="EndpointNameFilter" filterType="EndpointName"
             filterData="calculatorEndpoint"/>  
     <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"
             filterData="http://localhost/routingservice/router/rounding/"/>  
     <filter name="RoundRobinFilter1" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
     <filter name="RoundRobinFilter2" filterType="Custom"
             customType="RoutingServiceFilters.RoundRobinMessageFilter,
             RoutingService" filterData="group1"/>  
</filters>  
```  
  
> [!NOTE]
> <span data-ttu-id="ecae8-148">単にフィルターを定義しただけでは、そのフィルターに対してメッセージが評価されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ecae8-148">Simply defining a filter does not cause messages to be evaluated against the filter.</span></span> <span data-ttu-id="ecae8-149">フィルターをフィルター テーブルに追加する必要があります。テーブルに追加することで、ルーティング サービスが公開するサービス エンドポイントに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-149">The filter must be added to a filter table, which is then associated with the service endpoint exposed by the Routing Service.</span></span>  
  
### <a name="namespace-table"></a><span data-ttu-id="ecae8-150">名前空間テーブル</span><span class="sxs-lookup"><span data-stu-id="ecae8-150">Namespace Table</span></span>  

 <span data-ttu-id="ecae8-151">XPath フィルターを使用すると、XPath クエリを含むフィルター データは、名前空間を使用するため、非常に大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="ecae8-151">When using an XPath filter, the filter data that contains the XPath query can become extremely large due to the use of namespaces.</span></span> <span data-ttu-id="ecae8-152">この問題を軽減するために、ルーティング サービスでは、名前空間テーブルを使用して、独自の名前空間プレフィックスを定義できるようにしています。</span><span class="sxs-lookup"><span data-stu-id="ecae8-152">To alleviate this problem the Routing Service provides the ability to define your own namespace prefixes by using the namespace table.</span></span>  
  
 <span data-ttu-id="ecae8-153">名前空間テーブルは、XPath で使用できる一般的な名前空間の名前空間プレフィックスを定義する <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> オブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="ecae8-153">The namespace table is a collection of <xref:System.ServiceModel.Routing.Configuration.NamespaceElement> objects that defines the namespace prefixes for common namespaces that can be used in an XPath.</span></span> <span data-ttu-id="ecae8-154">以下は、名前空間テーブルに格納されている既定の名前空間およびプレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="ecae8-154">The following are the default namespaces and namespace prefixes that are contained in the namespace table.</span></span>  
  
|<span data-ttu-id="ecae8-155">Prefix</span><span class="sxs-lookup"><span data-stu-id="ecae8-155">Prefix</span></span>|<span data-ttu-id="ecae8-156">名前空間</span><span class="sxs-lookup"><span data-stu-id="ecae8-156">Namespace</span></span>|  
|------------|---------------|  
|<span data-ttu-id="ecae8-157">s11</span><span class="sxs-lookup"><span data-stu-id="ecae8-157">s11</span></span>|`http://schemas.xmlsoap.org/soap/envelope`|  
|<span data-ttu-id="ecae8-158">s12</span><span class="sxs-lookup"><span data-stu-id="ecae8-158">s12</span></span>|`http://www.w3.org/2003/05/soap-envelope`|  
|<span data-ttu-id="ecae8-159">wsaAugust2004</span><span class="sxs-lookup"><span data-stu-id="ecae8-159">wsaAugust2004</span></span>|`http://schemas.xmlsoap.org/ws/2004/08/addressing`|  
|<span data-ttu-id="ecae8-160">wsa10</span><span class="sxs-lookup"><span data-stu-id="ecae8-160">wsa10</span></span>|`http://www.w3.org/2005/08/addressing`|  
|<span data-ttu-id="ecae8-161">sm</span><span class="sxs-lookup"><span data-stu-id="ecae8-161">sm</span></span>|`http://schemas.microsoft.com/serviceModel/2004/05/xpathfunctions`|  
|<span data-ttu-id="ecae8-162">tempuri</span><span class="sxs-lookup"><span data-stu-id="ecae8-162">tempuri</span></span>|`http://tempuri.org`|  
|<span data-ttu-id="ecae8-163">ser</span><span class="sxs-lookup"><span data-stu-id="ecae8-163">ser</span></span>|`http://schemas.microsoft.com/2003/10/Serialization`|  
  
 <span data-ttu-id="ecae8-164">XPath クエリに特定の名前空間を使用することがわかっている場合は、その名前空間を一意の名前空間プレフィックスと併せて名前空間テーブルに追加し、完全名前空間ではなく、プレフィックスを XPath クエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-164">When you know that you will be using a specific namespace in your XPath queries, you can add it to the namespace table along with a unique namespace prefix and use the prefix in any XPath query instead of the full namespace.</span></span> <span data-ttu-id="ecae8-165">次の例では、名前空間のプレフィックスとして "custom" を定義してい `"http://my.custom.namespace"` ます。これは、filterData に含まれる XPath クエリで使用されます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-165">The following example defines a prefix of "custom" for the namespace `"http://my.custom.namespace"`, which is then used in the XPath query contained in filterData.</span></span>  
  
```xml  
<namespaceTable>  
     <add prefix="custom" namespace="http://my.custom.namespace/"/>  
</namespaceTable>  
<filters>  
     <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 1"/>  
</filters>  
```  
  
## <a name="filter-tables"></a><span data-ttu-id="ecae8-166">フィルター テーブル</span><span class="sxs-lookup"><span data-stu-id="ecae8-166">Filter Tables</span></span>  

 <span data-ttu-id="ecae8-167">各フィルター要素では、メッセージに適用できる論理比較が定義されますが、フィルター テーブルでは、フィルター要素と送信先クライアント エンドポイントが関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-167">While each filter element defines a logical comparison that can be applied to a message, the filter table provides the association between the filter element and the destination client endpoint.</span></span> <span data-ttu-id="ecae8-168">フィルター テーブルは、フィルター、プライマリの送信先エンドポイント、および代替のバックアップ エンドポイントのリスト間の関連付けを定義する <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> オブジェクトの名前付きコレクションです。</span><span class="sxs-lookup"><span data-stu-id="ecae8-168">A filter table is a named collection of <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement> objects that define the association between a filter, a primary destination endpoint, and a list of alternative backup endpoints.</span></span> <span data-ttu-id="ecae8-169">フィルター テーブル エントリでは、必要に応じて、各フィルター条件に優先度を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-169">The filter table entries also allow you to specify an optional priority for each filter condition.</span></span> <span data-ttu-id="ecae8-170">次の例では、まず、2 つのフィルターを定義し、各フィルターを送信先エンドポイントに関連付けるフィルター テーブルを定義しています。</span><span class="sxs-lookup"><span data-stu-id="ecae8-170">The following example defines two filters and then defines a filter table that associates each filter with a destination endpoint.</span></span>  
  
```xml  
<routing>  
     <filters>  
       <filter name="AddAction" filterType="Action" filterData="Add" />  
       <filter name="SubtractAction" filterType="Action" filterData="Subtract" />  
     </filters>  
     <filterTables>  
       <table name="routingTable1">  
         <filters>  
           <add filterName="AddAction" endpointName="Addition" />  
           <add filterName="SubtractAction" endpointName="Subtraction" />  
         </filters>  
       </table>  
     </filterTables>
</routing>  
```  
  
### <a name="filter-evaluation-priority"></a><span data-ttu-id="ecae8-171">フィルター評価の優先度</span><span class="sxs-lookup"><span data-stu-id="ecae8-171">Filter Evaluation Priority</span></span>  

 <span data-ttu-id="ecae8-172">既定では、フィルター テーブルのすべてのエントリが同時に評価され、評価対象のメッセージは、一致するフィルター エントリに関連付けられているエンドポイントにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-172">By default, all entries in the filter table are evaluated simultaneously, and the message being evaluated is routed to the endpoint(s) associated with each matching filter entry.</span></span> <span data-ttu-id="ecae8-173">複数のフィルターが `true` に評価され、メッセージが一方向または双方向である場合は、メッセージが、一致するすべてのフィルターのエンドポイントにマルチキャストされます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-173">If multiple filters evaluate to `true`, and the message is one-way or duplex, the message is multicast to the endpoints for all matching filters.</span></span> <span data-ttu-id="ecae8-174">要求/応答メッセージは、クライアントに返すことができる応答が 1 つのみであるため、マルチキャストできません。</span><span class="sxs-lookup"><span data-stu-id="ecae8-174">Request-reply messages cannot be multicast because only one reply can be returned to the client.</span></span>  
  
 <span data-ttu-id="ecae8-175">各フィルターに優先度レベルを指定することで、より複雑なルーティング ロジックを実装できます。ルーティング サービスは、優先度レベルが最も高いフィルターをすべて最初に評価します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-175">More complex routing logic can be implemented by specifying priority levels for each filter; the Routing Service evaluates all filters at the highest priority level first.</span></span> <span data-ttu-id="ecae8-176">メッセージがこのレベルのフィルターに一致した場合、優先度がこれよりも低いフィルターは処理されません。</span><span class="sxs-lookup"><span data-stu-id="ecae8-176">If a message matches a filter of this level, no filters of a lower priority are processed.</span></span> <span data-ttu-id="ecae8-177">たとえば、一方向の受信メッセージは、最初に、優先度が 2 であるすべてのフィルターに対して評価されるとします。</span><span class="sxs-lookup"><span data-stu-id="ecae8-177">For example, an incoming one-way message is first evaluated against all filters with a priority of 2.</span></span> <span data-ttu-id="ecae8-178">この優先度レベルのどのフィルターにもメッセージが一致しなかった場合は、次に、優先度が 1 のフィルターと比較されます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-178">The message does not match any filter at this priority level, so next the message is compared against filters with a priority of 1.</span></span> <span data-ttu-id="ecae8-179">優先度 1 のフィルターのうち、2 つがメッセージに一致した場合、メッセージは、一方向のメッセージであるため、両方の送信先エンドポイントにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-179">Two priority 1 filters match the message, and because it is a one-way message it is routed to both destination endpoints.</span></span>  <span data-ttu-id="ecae8-180">優先度 1 のフィルターの中に一致するものが見つかったため、優先度が 0 のフィルターは評価されません。</span><span class="sxs-lookup"><span data-stu-id="ecae8-180">Because a match was found among the priority 1 filters, no filters of priority 0 are evaluated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecae8-181">優先度が指定されていない場合は、既定の優先度の 0 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-181">If no priority is specified, the default priority of 0 is used.</span></span>  
  
 <span data-ttu-id="ecae8-182">次の例では、フィルター テーブルを定義しています。このテーブルでは、テーブルで参照しているフィルターに優先度 2、1、および 0 を指定しています。</span><span class="sxs-lookup"><span data-stu-id="ecae8-182">The following example defines a filter table that specifies priorities of 2, 1, and 0 for the filters referenced in the table.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="XPathFilter" endpointName="roundingCalcEndpoint"
               priority="2"/>  
          <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint"
               priority="1"/>  
          <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint"
               priority="1"/>  
          <add filterName="MatchAllMessageFilter" endpointName="defaultCalcEndpoint"
               priority="0"/>  
     </filterTable>  
</filterTables>  
```  
  
 <span data-ttu-id="ecae8-183">上記の例では、メッセージが XPathFilter に一致すると、roundingCalcEndpoint にルーティングされます。また、その他のフィルターはすべて、これよりも優先度が低いため、テーブル内の他のフィルターは評価されません。</span><span class="sxs-lookup"><span data-stu-id="ecae8-183">In the preceding example, if a message matches the XPathFilter, it will be routed to the roundingCalcEndpoint and no further filters in the table will be evaluated because all other filters are of a lower priority.</span></span> <span data-ttu-id="ecae8-184">ただし、メッセージが XPathFilter に一致しなかった場合は、次に優先度が低いすべてのフィルター、つまり、EndpointNameFilter と PrefixAddressFilter に対してメッセージが評価されます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-184">However, if the message does not match the XPathFilter it will then be evaluated against all filters of the next lower priority, EndpointNameFilter and PrefixAddressFilter.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecae8-185">可能な場合は、優先度の評価によってパフォーマンスが低下する可能性があるため、優先度を指定する代わりに、排他的なフィルターを使用してください。</span><span class="sxs-lookup"><span data-stu-id="ecae8-185">When possible, use exclusive filters instead of specifying a priority because priority evaluation can result in performance degradation.</span></span>  
  
### <a name="backup-lists"></a><span data-ttu-id="ecae8-186">バックアップ リスト</span><span class="sxs-lookup"><span data-stu-id="ecae8-186">Backup Lists</span></span>  

 <span data-ttu-id="ecae8-187">フィルター テーブルの各フィルターには、必要に応じて、バックアップ リストを指定できます。バックアップ リストは、エンドポイントの名前付きコレクション (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>) です。</span><span class="sxs-lookup"><span data-stu-id="ecae8-187">Each filter in the filter table can optionally specify a backup list, which is a named collection of endpoints (<xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection>).</span></span> <span data-ttu-id="ecae8-188">このコレクションには、<xref:System.ServiceModel.CommunicationException> に指定されているプライマリ エンドポイントへの送信時に <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A> が発生した場合に、メッセージの転送先となるエンドポイントの順序指定されたリストが保持されます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-188">This collection contains an ordered list of endpoints that the message will be transmitted to in the event of a <xref:System.ServiceModel.CommunicationException> when sending to the primary endpoint specified in <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.EndpointName%2A>.</span></span> <span data-ttu-id="ecae8-189">次の例では、2つのエンドポイントを含む "backupServiceEndpoints" という名前のバックアップリストを定義します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-189">The following example defines a backup list named "backupServiceEndpoints" that contains two endpoints.</span></span>  
  
```xml  
<filterTables>  
     <filterTable name="filterTable1">  
          <add filterName="MatchAllFilter1" endpointName="Destination" backupList="backupEndpointList"/>  
     </filterTable>  
</filterTables>  
<backupLists>  
     <backupList name="backupEndpointList">  
          <add endpointName="backupServiceQueue" />  
          <add endpointName="alternateServiceQueue" />  
     </backupList>  
</backupLists>  
```  
  
 <span data-ttu-id="ecae8-190">前の例では、プライマリエンドポイント "宛先" への送信が失敗した場合、ルーティングサービスは、リストされているシーケンス内の各エンドポイントに送信しようとします。最初に、backupServiceQueue に送信し、その後、backupServiceQueue への送信が失敗した場合は alternateServiceQueue に送信します。</span><span class="sxs-lookup"><span data-stu-id="ecae8-190">In the preceding example, if a send to the primary endpoint "Destination" fails, the Routing Service will try sending to each endpoint in the sequence they are listed, first sending to backupServiceQueue and subsequently sending to alternateServiceQueue if the send to backupServiceQueue fails.</span></span> <span data-ttu-id="ecae8-191">すべてのバックアップ エンドポイントへの送信が失敗した場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="ecae8-191">If all backup endpoints fail, a fault is returned.</span></span>
