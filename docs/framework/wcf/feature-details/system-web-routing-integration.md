---
title: System.Web.Routing 統合
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: bb820f535a69a24e05b7374bcf97539ae2b87aef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266429"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="60cd4-102">System.Web.Routing 統合</span><span class="sxs-lookup"><span data-stu-id="60cd4-102">System.Web.Routing Integration</span></span>

<span data-ttu-id="60cd4-103">インターネットインフォメーションサービス (IIS) で Windows Communication Foundation (WCF) サービスをホストする場合は、.svc ファイルを仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="60cd4-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="60cd4-104">この .svc ファイルは、使用するサービス ホスト ファクトリと、サービスを実装するクラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="60cd4-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="60cd4-105">サービスに要求を行うときは、URI に .svc ファイルを指定します。たとえば、のように指定します。 `http://contoso.com/EmployeeServce.svc`</span><span class="sxs-lookup"><span data-stu-id="60cd4-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="60cd4-106">REST サービスを記述するプログラマにとっては、この種類の URI は最適とは言えません。</span><span class="sxs-lookup"><span data-stu-id="60cd4-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="60cd4-107">REST サービス用の URI は、特定のリソースを指定しており、拡張子がないのが普通です。</span><span class="sxs-lookup"><span data-stu-id="60cd4-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="60cd4-108"><xref:System.Web.Routing>統合機能を使用すると、拡張されていない uri に応答する WCF REST サービスをホストできます。</span><span class="sxs-lookup"><span data-stu-id="60cd4-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="60cd4-109">ルーティングの詳細については、「 [ASP.NET routing](/previous-versions/aspnet/cc668201(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60cd4-109">For more information about routing see [ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="60cd4-110">System.Web.Routing 統合の使用</span><span class="sxs-lookup"><span data-stu-id="60cd4-110">Using System.Web.Routing Integration</span></span>  

 <span data-ttu-id="60cd4-111"><xref:System.Web.Routing> 統合機能を使用するには、<xref:System.ServiceModel.Activation.ServiceRoute> クラスを使用して 1 つ以上のルートを作成し、Global.asax ファイルでそれらを <xref:System.Web.Routing.RouteTable> に追加します。</span><span class="sxs-lookup"><span data-stu-id="60cd4-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="60cd4-112">これらのルートは、サービスが応答する相対 URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="60cd4-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="60cd4-113">次の例は、その方法を示したものです。</span><span class="sxs-lookup"><span data-stu-id="60cd4-113">The following example shows how to do this.</span></span>  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));
   }  
</script>  
```  
  
 <span data-ttu-id="60cd4-114">これは、Customers で始まる相対 URI が指定されたすべての要求を `Service` サービスにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="60cd4-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="60cd4-115">Web.config ファイルでは、次の例に示すように、`System.Web.Routing.UrlRoutingModule` モジュールを追加し、`runAllManagedModulesForAllRequests` 属性を `true` に設定し、`UrlRoutingHandler` ハンドラーを `<system.webServer>` 要素に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60cd4-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 <span data-ttu-id="60cd4-116">これで、ルーティングに必要なモジュールとハンドラーが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="60cd4-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="60cd4-117">詳細については、[ルーティング](routing.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="60cd4-117">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="60cd4-118">また、次の例に示すように、`aspNetCompatibilityEnabled` 要素で `true` 属性を `<serviceHostingEnvironment>` に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="60cd4-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="60cd4-119">次の例に示すように、このサービスを実装するクラスでは、ASP.NET 互換要件を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="60cd4-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="60cd4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="60cd4-120">See also</span></span>

- [<span data-ttu-id="60cd4-121">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="60cd4-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="60cd4-122">[ASP.NET ルーティング](/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="60cd4-122">[ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
