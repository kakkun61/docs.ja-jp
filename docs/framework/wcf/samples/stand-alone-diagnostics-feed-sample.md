---
title: スタンドアロン診断フィードのサンプル
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: b4c3613656e0aec42c0d3f5cd7cde0af6540a69a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268249"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="286cb-102">スタンドアロン診断フィードのサンプル</span><span class="sxs-lookup"><span data-stu-id="286cb-102">Stand-Alone Diagnostics Feed Sample</span></span>

<span data-ttu-id="286cb-103">このサンプルでは、Windows Communication Foundation (WCF) を使用して配信するために RSS/Atom フィードを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="286cb-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="286cb-104">これは基本的な "Hello World" プログラムであり、オブジェクトモデルの基本と、Windows Communication Foundation (WCF) サービスでの設定方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="286cb-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="286cb-105">WCF は、特別なデータ型を返すサービス操作として配信フィードをモデル化し <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> ます。</span><span class="sxs-lookup"><span data-stu-id="286cb-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="286cb-106"><xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> のインスタンスは、フィードを RSS 2.0 形式および Atom 1.0 形式の両方にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="286cb-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="286cb-107">使用するコントラクトを次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="286cb-107">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="286cb-108">この `GetProcesses` 操作には、 <xref:System.ServiceModel.Web.WebGetAttribute> WCF が HTTP GET 要求をサービス操作にディスパッチする方法を制御し、送信されるメッセージの形式を指定できるようにする属性で注釈が付けられています。</span><span class="sxs-lookup"><span data-stu-id="286cb-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="286cb-109">任意の WCF サービスと同様に、配信フィードは任意のマネージアプリケーションで自己ホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="286cb-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="286cb-110">配信サービスが適切に機能するには、特定のバインディング (<xref:System.ServiceModel.WebHttpBinding>) と、特定のエンドポイント動作 (<xref:System.ServiceModel.Description.WebHttpBehavior>) が必要です。</span><span class="sxs-lookup"><span data-stu-id="286cb-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="286cb-111">新しい <xref:System.ServiceModel.Web.WebServiceHost> クラスには、特定の構成を使用せずにこのようなエンドポイントを作成する際に便利な API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="286cb-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="286cb-112">または、IIS でホストされる .svc ファイルから <xref:System.ServiceModel.Activation.WebServiceHostFactory> を使用して、同等の機能を用意することもできます (この手法は、このサンプル コードでは示されません)。</span><span class="sxs-lookup"><span data-stu-id="286cb-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<% @ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="286cb-113">このサービスは標準の HTTP GET を使用して要求を受け取るので、サービスへのアクセスには、RSS または ATOM に対応している任意のクライアントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="286cb-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="286cb-114">たとえば、 `http://localhost:8000/diagnostics/feed/?format=atom` RSS 対応のブラウザーでまたはに移動して、このサービスの出力を表示でき `http://localhost:8000/diagnostics/feed/?format=rss` ます。</span><span class="sxs-lookup"><span data-stu-id="286cb-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="286cb-115">また、 [WCF 配信オブジェクトモデルが Atom および RSS にマップ](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) され、命令型コードを使用してシンジケートデータを読み取り、処理する方法を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="286cb-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="286cb-116">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="286cb-116">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="286cb-117">Windows Communication Foundation のサンプルについては、「 [1 回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)」で説明されているように、コンピューター上で HTTP および HTTPS に対する適切なアドレス登録アクセス許可を持っていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="286cb-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="286cb-118">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="286cb-118">Build the solution.</span></span>

3. <span data-ttu-id="286cb-119">コンソール アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="286cb-119">Run the console application.</span></span>

4. <span data-ttu-id="286cb-120">コンソールアプリケーションの実行中に、RSS 対応のブラウザーに移動するか、を `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` 使用します。</span><span class="sxs-lookup"><span data-stu-id="286cb-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="286cb-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="286cb-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="286cb-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="286cb-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="286cb-123">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="286cb-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="286cb-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="286cb-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="286cb-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="286cb-125">See also</span></span>

- [<span data-ttu-id="286cb-126">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="286cb-126">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="286cb-127">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="286cb-127">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
