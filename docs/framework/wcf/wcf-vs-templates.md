---
title: WCF Visual Studio テンプレート
ms.date: 03/30/2017
ms.assetid: 6a608575-3535-4190-89da-911e24c8374f
ms.openlocfilehash: a3aa7e3ee57759ef54ddaa898fe036c4e3caa33e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2020
ms.locfileid: "96279702"
---
# <a name="wcf-visual-studio-templates"></a><span data-ttu-id="1234a-102">WCF Visual Studio テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-102">WCF Visual Studio Templates</span></span>

<span data-ttu-id="1234a-103">Windows Communication Foundation (WCF) Visual Studio テンプレートは、Visual Studio で使用できる事前定義されたプロジェクトおよび項目テンプレートで、WCF サービスと周囲のアプリケーションをすばやく構築できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-103">Windows Communication Foundation (WCF) Visual Studio templates are predefined project and item templates you can use in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
## <a name="using-the-wcf-templates"></a><span data-ttu-id="1234a-104">WCF テンプレートの使用</span><span class="sxs-lookup"><span data-stu-id="1234a-104">Using the WCF Templates</span></span>  

 <span data-ttu-id="1234a-105">WCF Visual Studio テンプレートによって、サービス開発のための基本的なクラス構造が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1234a-105">WCF Visual Studio templates provide a basic class structure for service development.</span></span> <span data-ttu-id="1234a-106">これには、サービス コントラクト、データ コントラクト、サービス実装、および構成の基本的な定義が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1234a-106">Specifically, these templates provide the basic definitions for service contract, data contract, service implementation, and configuration.</span></span> <span data-ttu-id="1234a-107">これらのテンプレートを使用すると、最小限のコードを使用した単純なサービスや、より高度なサービスのビルド ブロックを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-107">You can use these templates to create a simple service with minimal code interaction, as well as a building block for more advanced services.</span></span>  
  
### <a name="wcf-service-library-project-template"></a><span data-ttu-id="1234a-108">WCF サービス ライブラリ プロジェクト テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-108">WCF Service Library Project Template</span></span>  

 <span data-ttu-id="1234a-109">WCF サービスライブラリプロジェクトテンプレートは、[新しいプロジェクト] ダイアログボックスの [ **visual C#** ]、[wcf]、[ **visual basic**]、[wcf] で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-109">The WCF Service Library project template is available in the new project dialog box under **Visual C#\WCF** and **Visual Basic\WCF**.</span></span>  
  
 <span data-ttu-id="1234a-110">**WCF サービス** テンプレートを使用して新しいプロジェクトを作成すると、新しいプロジェクトには次の3つのファイルが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="1234a-110">When you create a new project using the **WCF Service** template, the new project automatically includes the following three files:</span></span>  
  
- <span data-ttu-id="1234a-111">サービス コントラクト ファイル (IService1.cs または IService1.vb)。</span><span class="sxs-lookup"><span data-stu-id="1234a-111">Service contract file (IService1.cs or IService1.vb).</span></span> <span data-ttu-id="1234a-112">サービスコントラクトファイルは、WCF サービス属性が適用されたインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="1234a-112">The service contract file is an interface that has WCF service attributes applied.</span></span> <span data-ttu-id="1234a-113">このファイルには、サービスの定義方法を示す単純なサービスの定義が含まれています。その他に、パラメーター ベースの操作や、単純なデータ コントラクトのサンプルも含まれています。</span><span class="sxs-lookup"><span data-stu-id="1234a-113">This file provides a definition of a simple service to show you how to define your services, and includes parameter-based operations and a simple data contract sample.</span></span> <span data-ttu-id="1234a-114">これは、WCF サービスプロジェクトの作成後にコードエディターに表示される既定のファイルです。</span><span class="sxs-lookup"><span data-stu-id="1234a-114">This is the default file displayed in the code editor after creating a WCF service project.</span></span>  
  
- <span data-ttu-id="1234a-115">サービス実装ファイル (Service1.cs または Service1.vb)。</span><span class="sxs-lookup"><span data-stu-id="1234a-115">Service implementation file (Service1.cs or Service1.vb).</span></span> <span data-ttu-id="1234a-116">サービス実装ファイルは、サービス コントラクト ファイルに定義されているコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="1234a-116">The service implementation file implements the contract defined in the service contract file.</span></span>  
  
- <span data-ttu-id="1234a-117">アプリケーション構成ファイル (App.config)。</span><span class="sxs-lookup"><span data-stu-id="1234a-117">Application configuration file (App.config).</span></span> <span data-ttu-id="1234a-118">構成ファイルは、セキュリティで保護された HTTP バインディングを使用して、WCF サービスモデルの基本的な要素を提供します。</span><span class="sxs-lookup"><span data-stu-id="1234a-118">The configuration file provides the basic elements of a WCF service model with a secure HTTP binding.</span></span> <span data-ttu-id="1234a-119">サービスのエンドポイントも含まれており、メタデータの交換も可能です。</span><span class="sxs-lookup"><span data-stu-id="1234a-119">It also includes an endpoint for the service and enables metadata exchange.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1234a-120">Visual Studio は、既定の構成である [WCF サービスホスト (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)を使用して実行されるときに、プロジェクトの構成ファイルとして App.config ファイルを認識するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="1234a-120">Visual Studio is configured to recognize the App.config file as the configuration file for the project when it is run using the [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md), which is the default configuration.</span></span> <span data-ttu-id="1234a-121">サービス ライブラリを実行可能ファイルでホストする場合は、DLL の構成ファイルは無効になるため、その実行可能ファイルの構成ファイルに構成コードを移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1234a-121">If you host the service library in an executable, you have to move the configuration code to the configuration file of the executable, as configuration files for DLLs are not valid.</span></span>  
  
### <a name="wcf-service-application-template"></a><span data-ttu-id="1234a-122">WCF サービス アプリケーション テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-122">WCF Service Application Template</span></span>  

 <span data-ttu-id="1234a-123">WCF サービスアプリケーションテンプレートは、[新しいプロジェクト] ダイアログボックスの [ **visual C#** ]、[wcf]、[ **visual basic**]、[wcf] で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-123">The WCF Service Application template is available in the New Project dialog box under **Visual C#\WCF** and **Visual Basic\WCF**.</span></span>  
  
 <span data-ttu-id="1234a-124">**WCF Web アプリケーションサービス** テンプレートを使用して新しいプロジェクトを作成する場合、プロジェクトには次の4つのファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1234a-124">When you create a new project using the **WCF Web Application Service** template, the project includes the following four files:</span></span>  
  
- <span data-ttu-id="1234a-125">サービス ホスト ファイル (service1.svc)。</span><span class="sxs-lookup"><span data-stu-id="1234a-125">Service host file (service1.svc).</span></span>  
  
- <span data-ttu-id="1234a-126">サービス コントラクト ファイル (IService1.cs または IService1.vb)。</span><span class="sxs-lookup"><span data-stu-id="1234a-126">Service contract file (IService1.cs or IService1.vb).</span></span>  
  
- <span data-ttu-id="1234a-127">サービス実装ファイル (Service1.svc.cs または Service1.svc.vb)。</span><span class="sxs-lookup"><span data-stu-id="1234a-127">Service implementation file (Service1.svc.cs or Service1.svc.vb).</span></span>  
  
- <span data-ttu-id="1234a-128">Web 構成ファイル (Web.config)。</span><span class="sxs-lookup"><span data-stu-id="1234a-128">Web configuration file (Web.config).</span></span>  
  
 <span data-ttu-id="1234a-129">このテンプレートでは、自動的に Web サイトが作成されて (仮想ディレクトリに配置されます)、サービスがホストされます。</span><span class="sxs-lookup"><span data-stu-id="1234a-129">The template automatically creates a Web site (to be deployed to a virtual directory) and hosts a service in it.</span></span>  
  
### <a name="wcf-web-site-template"></a><span data-ttu-id="1234a-130">WCF Web サイト テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-130">WCF Web Site Template</span></span>  

 <span data-ttu-id="1234a-131">WCF Web サイトテンプレートは、[新しいプロジェクト] ダイアログボックスの [ **visual C# \Web Site\WCF service** ] と [ **Visual Basic\Web Site\WCF service**] で使用できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-131">The WCF Web Site template is available in the New Project dialog box under **Visual C#\Web Site\WCF Service** and **Visual Basic\Web Site\WCF Service**.</span></span> <span data-ttu-id="1234a-132">これによって、WCF サービス アプリケーションのテンプレートと同じファイルが作成されますが、ASP.NET Web サイトであるかのように編成されます。</span><span class="sxs-lookup"><span data-stu-id="1234a-132">This creates the same files as the WCF Service Application template but organizes it as if it were a ASP.NET web site.</span></span> <span data-ttu-id="1234a-133">App_Code フォルダーと App_Data フォルダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="1234a-133">App_Code and App_Data folders are created.</span></span>  
  
### <a name="wcf-service-item-template"></a><span data-ttu-id="1234a-134">WCF サービス項目テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-134">WCF Service Item Template</span></span>  

 <span data-ttu-id="1234a-135">WCF サービス項目テンプレートは、既存の Visual Studio プロジェクトに WCF サービスを簡単に追加できるようにするカスタムテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="1234a-135">The WCF Service Item template is a custom template that provides a quick way to add WCF services to your existing Visual Studio projects.</span></span>  
  
 <span data-ttu-id="1234a-136">このテンプレートを使用するには、 **ソリューションエクスプローラー** ウィンドウにアクセスし、プロジェクト名を右クリックして [ **追加**] をポイントし、[ **新しい項目** ] をクリックして [新しい項目の **追加** ] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="1234a-136">To use this template, go to the **Solution Explorer** pane, right-click your project name, point to **Add**, and then click **New Item** to launch the **Add New Item** dialog box.</span></span>  
  
 <span data-ttu-id="1234a-137">サービス インターフェイス ファイルとサービス実装ファイルがルート プロジェクト フォルダーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="1234a-137">The service interface and implementation files are placed in the root project folder.</span></span>  
  
 <span data-ttu-id="1234a-138">このテンプレートでは、新しいサービスの構成セクションが既存の構成ファイルと互換性がある場合にそれらがマージされます。</span><span class="sxs-lookup"><span data-stu-id="1234a-138">The template attempts to merge the configuration section of the new service to the existing configuration file, if they are compatible types.</span></span>  
  
 <span data-ttu-id="1234a-139">既存のプロジェクトが Web プロジェクトの場合は、サービス ホスト ファイル (service1.svc) も作成されます。</span><span class="sxs-lookup"><span data-stu-id="1234a-139">A service host file (service1.svc) is also created if the existing project is a Web project.</span></span>  
  
### <a name="wcf-wf-service-project-and-item-template"></a><span data-ttu-id="1234a-140">WCF WF サービス プロジェクト/項目テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-140">WCF WF Service Project and Item Template.</span></span>  

 <span data-ttu-id="1234a-141">これらのテンプレートは、ワークフローサービスをホストする WCF サービスを作成します。これは、web サービスのようにアクセスできるワークフローです。</span><span class="sxs-lookup"><span data-stu-id="1234a-141">These templates create WCF services that host a Workflow Service, which is a workflow that can be accessed like a web service.</span></span> <span data-ttu-id="1234a-142">この他に、XAML プログラミング モデルや命令型プログラミング モデルのテンプレートも用意されています。</span><span class="sxs-lookup"><span data-stu-id="1234a-142">Separate templates exist for XAML or imperative programming models.</span></span> <span data-ttu-id="1234a-143">これらのテンプレートを使用すると、シーケンシャル ワークフローやステート マシン ワークフローを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-143">Using the templates, you can create sequential or state machine workflow.</span></span> <span data-ttu-id="1234a-144">これらの種類のワークフローの詳細については、「 [方法: ワークフローを作成](../windows-workflow-foundation/how-to-create-a-workflow.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1234a-144">For more information on these types of workflow, see [How to: Create a Workflow](../windows-workflow-foundation/how-to-create-a-workflow.md).</span></span> <span data-ttu-id="1234a-145">ワークフロープロジェクトの作成の詳細については、「 [従来のワークフロープロジェクトの作成](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1234a-145">For more information about creating workflow projects, see [Creating Legacy Workflow Projects](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer).</span></span>  
  
 <span data-ttu-id="1234a-146">コードベースのワークフローではなく、XOML 型のワークフローを使用すると、Visual Studio デザイナーの応答性が向上します。</span><span class="sxs-lookup"><span data-stu-id="1234a-146">Visual Studio designer is more responsive when XOML type workflows are used instead of code based ones.</span></span> <span data-ttu-id="1234a-147">XOML ワークフローは、既定で作成されるワークフロー型です。</span><span class="sxs-lookup"><span data-stu-id="1234a-147">XOML workflow is the default workflow type to be created.</span></span>  
  
### <a name="wcf-syndication-service-library-template"></a><span data-ttu-id="1234a-148">WCF 配信サービス ライブラリ テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-148">WCF Syndication Service Library Template</span></span>  

 <span data-ttu-id="1234a-149">このテンプレートを使用すると、RSS または ATOM 形式のフィードを WCF サービスとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-149">This template enables you to expose your feed in the RSS or ATOM format as a WCF service.</span></span> <span data-ttu-id="1234a-150">詳細については、「 [WCF 配信](./feature-details/wcf-syndication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1234a-150">For more information, see [WCF Syndication](./feature-details/wcf-syndication.md).</span></span>  
  
#### <a name="changing-the-address-of-the-feed"></a><span data-ttu-id="1234a-151">フィードのアドレスの変更</span><span class="sxs-lookup"><span data-stu-id="1234a-151">Changing the Address of the Feed</span></span>  

 <span data-ttu-id="1234a-152">配信テンプレートは、実行中に Internet Explorer を使用します。</span><span class="sxs-lookup"><span data-stu-id="1234a-152">The syndication template uses Internet Explorer during execution.</span></span> <span data-ttu-id="1234a-153">Visual Studio の **ソリューションエクスプローラー** でプロジェクトを右クリックし、[ **プロパティ**] を選択し、[ **デバッグ** ] タブを選択すると、テンプレートの既定のアドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1234a-153">When you right-click your project in **Solutions Explorer** in Visual Studio, select **Properties**, then select the **Debug** tab and you can see the default address of the template.</span></span> <span data-ttu-id="1234a-154">Internet Explorer は、このアドレスにあるフィードを開きます。</span><span class="sxs-lookup"><span data-stu-id="1234a-154">Internet Explorer attempts to open the feed at this address.</span></span>  
  
 <span data-ttu-id="1234a-155">フィードのアドレスを変更する場合は、[ **デバッグ** ] タブのアドレスも変更する必要があります。この操作を行わないと、Internet Explorer は既定のアドレスでフィードを開こうとして失敗します。</span><span class="sxs-lookup"><span data-stu-id="1234a-155">If you change the address of your feed, you must also change the address in the **Debug** tab. If you do not do this, Internet Explorer attempts to open the feed at the default address and fail.</span></span>  
  
### <a name="ajax-enabled-wcf-service-item-template"></a><span data-ttu-id="1234a-156">AJAX 対応 WCF サービス項目テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-156">AJAX enabled WCF Service Item Template</span></span>  

 <span data-ttu-id="1234a-157">このテンプレートは、AJAX コントロールを WCF サービスとして公開します。</span><span class="sxs-lookup"><span data-stu-id="1234a-157">This template exposes an AJAX control as a WCF service.</span></span> <span data-ttu-id="1234a-158">AJAX コントロールの詳細については、 [ajax コントロールのドキュメント](/aspnet/ajax/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1234a-158">For more information on AJAX controls, see the [AJAX control documentation](/aspnet/ajax/).</span></span>  
  
### <a name="silverlight-enabled-wcf-service-item-template"></a><span data-ttu-id="1234a-159">Silverlight 対応 WCF サービス項目テンプレート</span><span class="sxs-lookup"><span data-stu-id="1234a-159">Silverlight-enabled WCF Service Item Template</span></span>  

 <span data-ttu-id="1234a-160">このテンプレートは、Silverlight クライアントまたはフロントエンドにデータを提供する Web サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="1234a-160">This template creates a Web service that provides data to a Silverlight client or front-end.</span></span> <span data-ttu-id="1234a-161">このテンプレートを Web サイトまたは Web アプリケーションプロジェクトに追加すると、WCF サービスを作成できます。これには、Silverlight クライアントとの通信をサポートするサービスコードと構成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1234a-161">The template can be added to a Web site or Web application project to create a WCF service, which includes service code and configuration that support communicating with a Silverlight client.</span></span> <span data-ttu-id="1234a-162">次に、 **サービス参照の追加** を使用して、クライアントにサービスのクライアントプロキシを追加し、silverlight クライアントと SILVERLIGHT 対応 WCF サービスの間でデータを交換できます。</span><span class="sxs-lookup"><span data-stu-id="1234a-162">You can then use **Add Service Reference** to add a client proxy of the service to the client, and exchange data between the Silverlight client and the Silverlight-enabled WCF service.</span></span>  
  
 <span data-ttu-id="1234a-163">このテンプレートにアクセスするには、 **ソリューションエクスプローラー** で web サイトまたは web アプリケーションプロジェクトを右クリックし、[ **新しいアイテムの追加**] をクリックして、[ **Silverlight 対応 WCF サービス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1234a-163">To access this template, right-click a Web site or Web application project in **Solution Explorer**, click **Add a new item**, and click **Silverlight-enabled WCF Service**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1234a-164">Silverlight 対応 WCF サービスは、セキュリティ設定を一切有効にせずに `basicHttpBinding` エンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="1234a-164">The Silverlight-enabled WCF Service exposes a `basicHttpBinding` endpoint without enabling any security settings.</span></span> <span data-ttu-id="1234a-165">したがって、サービスに接続しているすべてのクライアントが、このサービスに関する情報を取得できることになります。</span><span class="sxs-lookup"><span data-stu-id="1234a-165">Therefore, information about the service can be obtained by all clients that connect to this service.</span></span> <span data-ttu-id="1234a-166">また、サービスとクライアント間で交換されるメッセージの署名と暗号化も行われません。</span><span class="sxs-lookup"><span data-stu-id="1234a-166">Messages exchanged between the service and the client are also not signed or encrypted.</span></span> <span data-ttu-id="1234a-167">エンドポイントを正しくセキュリティで保護するには、ASP.NET 認証や HTTPS などのメカニズムを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1234a-167">To secure the endpoint properly, you should use ASP.NET authentication, HTTPS or other mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1234a-168">関連項目</span><span class="sxs-lookup"><span data-stu-id="1234a-168">See also</span></span>

- [<span data-ttu-id="1234a-169">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="1234a-169">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="1234a-170">WCF のテスト用クライアント (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="1234a-170">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
