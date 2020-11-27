---
title: '方法: 構成を使用せずに ASP.NET AJAX エンドポイントを追加する'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: e33f1fed7dd7bf45966815949ac544250f4d1de8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257627"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="b7416-102">方法: 構成を使用せずに ASP.NET AJAX エンドポイントを追加する</span><span class="sxs-lookup"><span data-stu-id="b7416-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>

<span data-ttu-id="b7416-103">Windows Communication Foundation (WCF) を使用すると、クライアント Web サイトの JavaScript から呼び出すことができる ASP.NET AJAX 対応エンドポイントを公開するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b7416-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="b7416-104">このようなエンドポイントを作成するには、他のすべての WCF エンドポイントと同様に、構成ファイルを使用するか、または構成要素を必要としないメソッドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b7416-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="b7416-105">ここでは、2 番目の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7416-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="b7416-106">構成を使用せずに ASP.NET AJAX エンドポイントを持つサービスを作成するには、サービスがインターネット インフォメーション サービス (IIS) でホストされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7416-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b7416-107">この方法を使用して ASP.NET AJAX エンドポイントをアクティブ化するには、 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> .svc ファイルで[ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブのファクトリパラメーターとしてを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7416-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="b7416-108">このカスタム ファクトリは自動的に ASP.NET AJAX エンドポイントを構成するコンポーネントであるため、クライアント Web サイトの JavaScript から呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b7416-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="b7416-109">実際の例については、「 [構成なしの AJAX サービス](../samples/ajax-service-without-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7416-109">For a working example, see the [AJAX Service Without Configuration](../samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="b7416-110">構成要素を使用して ASP.NET AJAX エンドポイントを構成する方法の概要については、「 [方法: 構成を使用して ASP.NET Ajax エンドポイントを追加](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7416-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="b7416-111">基本的な WCF サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="b7416-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="b7416-112">属性でマークされたインターフェイスを使用して、基本的な WCF サービスコントラクトを定義 <xref:System.ServiceModel.ServiceContractAttribute> します。</span><span class="sxs-lookup"><span data-stu-id="b7416-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="b7416-113">各操作を <xref:System.ServiceModel.OperationContractAttribute> でマークします。</span><span class="sxs-lookup"><span data-stu-id="b7416-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="b7416-114"><xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> プロパティが設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b7416-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="b7416-115">`ICalculator` を使用して、`CalculatorService` サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="b7416-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="b7416-116">名前空間ブロック内にラップすることにより、`ICalculator` と `CalculatorService` の実装の名前空間を定義します。</span><span class="sxs-lookup"><span data-stu-id="b7416-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="b7416-117">構成を使用せずにインターネット インフォメーション サービスでサービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="b7416-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="b7416-118">アプリケーションで、.svc という拡張子を付けて新しい service ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b7416-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="b7416-119">このファイルを編集するには、サービスに適切な[ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブ情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="b7416-119">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="b7416-120"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>ASP.NET AJAX エンドポイントを自動的に構成するために、 [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)ディレクティブでを使用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b7416-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="b7416-121">サービスをビルドしてクライアントから呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b7416-121">Build the service and call it from the client.</span></span> <span data-ttu-id="b7416-122">呼び出されたサービスがインターネット インフォメーション サービス (IIS) によってアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="b7416-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="b7416-123">IIS でのホストの詳細については、「 [How to: Host a WCF Service IN iis](how-to-host-a-wcf-service-in-iis.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7416-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="b7416-124">サービスを呼び出すには</span><span class="sxs-lookup"><span data-stu-id="b7416-124">To call the service</span></span>  
  
1. <span data-ttu-id="b7416-125">エンドポイントは、.svc ファイルを基準とした空のアドレスで構成されます。これにより、サービスが使用できるようになり、サービスに要求を送信することによって呼び出すことができます。 \<operation> たとえば、service .svc/Add を操作に送信します。 `Add`</span><span class="sxs-lookup"><span data-stu-id="b7416-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="b7416-126">これは、ASP.NET AJAX Script Manager コントロールのスクリプト コレクションにサービス URL を入力することで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b7416-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="b7416-127">例については、「 [構成なしの AJAX サービス](../samples/ajax-service-without-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7416-127">For an example, see the [AJAX Service Without Configuration](../samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7416-128">例</span><span class="sxs-lookup"><span data-stu-id="b7416-128">Example</span></span>  
  
 <span data-ttu-id="b7416-129">自動的に構成されたエンドポイントは、ベース URL に対して相対的に空のアドレスの位置に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7416-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="b7416-130">この方法では、構成ファイルを追加して使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b7416-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="b7416-131">構成ファイルにエンドポイントの定義がある場合、これらのエンドポイントは自動的に構成されたエンドポイントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b7416-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="b7416-132">たとえば、service.svc が <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用していて、そのサービス ディレクトリには、<xref:System.ServiceModel.BasicHttpBinding> を使用して "soap" という相対アドレスで同じサービスのエンドポイントを定義する Web.config ファイルが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="b7416-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="b7416-133">この場合、サービスには、service.svc に含まれるエンドポイント (ASP.NET AJAX 要求に応答) と、service.svc/soap にあるもう 1 つのエンドポイント (SOAP 要求に応答) の 2 つのエンドポイントが含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="b7416-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="b7416-134">構成ファイルで空の相対アドレスにエンドポイントを定義した場合は、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> が使用されると例外がスローされ、サービスの開始に失敗します。</span><span class="sxs-lookup"><span data-stu-id="b7416-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="b7416-135">自動的に構成されるエンドポイントの設定を変更するために構成を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="b7416-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="b7416-136">リーダーのクォータなど、設定の変更が必要な場合は、.svc ファイルから <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を削除し、エンドポイントの構成エントリを作成することで、構成を使用しない方法の採用を中止します。</span><span class="sxs-lookup"><span data-stu-id="b7416-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="b7416-137"><xref:System.Web.HttpContext> クラスや ASP.NET 承認機構を使用するなど、サービスで ASP.NET 互換モードが必要な場合は、このモードを有効にするために引き続き構成ファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="b7416-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="b7416-138">必要な構成要素は要素で、次のように [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) 追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7416-138">The configuration element required is the [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="b7416-139">詳細については、「 [WCF サービスと ASP.NET](wcf-services-and-aspnet.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7416-139">For more information, see the [WCF Services and ASP.NET](wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="b7416-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> クラスは、<xref:System.ServiceModel.Activation.ServiceHostFactory> の派生クラスです。</span><span class="sxs-lookup"><span data-stu-id="b7416-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="b7416-141">サービスホストファクトリメカニズムの詳細については、「 [ServiceHostFactory を使用したホストの拡張](../extending/extending-hosting-using-servicehostfactory.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7416-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7416-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7416-142">See also</span></span>

- [<span data-ttu-id="b7416-143">ASP.NET AJAX 用の WCF サービスの作成</span><span class="sxs-lookup"><span data-stu-id="b7416-143">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="b7416-144">方法: AJAX 対応 ASP.NET Web サービスを WCF に移行する</span><span class="sxs-lookup"><span data-stu-id="b7416-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
