---
title: '方法: IIS で WCF サービスをホストする'
description: インターネットインフォメーションサービス (IIS) でホストされている WCF サービスを作成する方法について説明します。 IIS ホストは、HTTP トランスポートでのみ使用できます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: e0eb61e56b20eda6627030700b823042e07d10c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244445"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="22590-104">方法: IIS で WCF サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="22590-104">How to: Host a WCF Service in IIS</span></span>

<span data-ttu-id="22590-105">このトピックでは、インターネットインフォメーションサービス (IIS) でホストされている Windows Communication Foundation (WCF) サービスを作成するために必要な基本的な手順の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="22590-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="22590-106">このトピックは、IIS に関する知識があり、IIS 管理ツールを使用して IIS アプリケーションを作成および管理する方法を理解していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="22590-106">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="22590-107">IIS の詳細については、「 [インターネットインフォメーションサービス](https://www.iis.net/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22590-107">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="22590-108">IIS 環境で実行される WCF サービスでは、プロセスのリサイクル、アイドルシャットダウン、プロセスの正常性の監視、メッセージベースのアクティブ化など、IIS の機能を最大限に活用できます。</span><span class="sxs-lookup"><span data-stu-id="22590-108">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="22590-109">このホスト オプションでは、IIS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。</span><span class="sxs-lookup"><span data-stu-id="22590-109">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="22590-110">IIS ホストは、HTTP トランスポートでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="22590-110">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="22590-111">WCF と ASP.NET の相互作用の詳細については、「 [Wcf Services と ASP.NET](wcf-services-and-aspnet.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22590-111">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="22590-112">セキュリティ構成の詳細については、「 [セキュリティ](security.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22590-112">For more information about configuring security, see [Security](security.md).</span></span>  
  
 <span data-ttu-id="22590-113">この例のソースコピーについては、「 [インラインコードを使用した IIS のホスト](../samples/iis-hosting-using-inline-code.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22590-113">For the source copy of this example, see [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="22590-114">IIS でホストされるサービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="22590-114">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="22590-115">コンピューターに IIS がインストールされ、実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="22590-115">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="22590-116">IIS のインストールと構成の詳細については、「 [iis 7.0 のインストールと構成](/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22590-116">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="22590-117">"IISHostedCalcService" という名前のアプリケーションファイル用の新しいフォルダーを作成し、ASP.NET がフォルダーの内容にアクセスできることを確認し、IIS 管理ツールを使用して、このアプリケーションディレクトリに物理的に配置された新しい IIS アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="22590-117">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="22590-118">アプリケーション ディレクトリのエイリアスを作成する場合は、"IISHostedCalc" を使用します。</span><span class="sxs-lookup"><span data-stu-id="22590-118">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="22590-119">"service.svc" という新しいファイルをアプリケーション ディレクトリに作成します。</span><span class="sxs-lookup"><span data-stu-id="22590-119">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="22590-120">次の要素を追加して、このファイルを編集し @ServiceHost ます。</span><span class="sxs-lookup"><span data-stu-id="22590-120">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="22590-121">アプリケーション ディレクトリ内に App_Code サブディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="22590-121">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="22590-122">App_Code サブディレクトリに Service.cs というコード ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="22590-122">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="22590-123">Service.cs ファイルの先頭に次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="22590-123">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="22590-124">using ステートメントの後に、次の名前空間宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="22590-124">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="22590-125">次のコードに示すように、名前空間宣言内にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="22590-125">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="22590-126">次のコードに示すように、サービス コントラクト定義の後に、サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="22590-126">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="22590-127">アプリケーション ディレクトリ内に "Web.config" というファイルを作成し、次の構成コードをファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="22590-127">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="22590-128">実行時に、WCF インフラストラクチャは、クライアントアプリケーションが通信できるエンドポイントを構築するために情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="22590-128">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="22590-129">この例では、構成ファイルにエンドポイントを明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="22590-129">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="22590-130">エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。</span><span class="sxs-lookup"><span data-stu-id="22590-130">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="22590-131">既定のエンドポイント、バインディング、および動作の詳細については、「簡略化された [構成](../simplified-configuration.md) と [WCF サービスの簡略化](../samples/simplified-configuration-for-wcf-services.md)された構成」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="22590-131">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="22590-132">サービスが正確にホストされるようにするには、Internet Explorer のインスタンスを開き、サービスの URL: `http://localhost/IISHostedCalc/Service.svc` を参照します。</span><span class="sxs-lookup"><span data-stu-id="22590-132">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="22590-133">例</span><span class="sxs-lookup"><span data-stu-id="22590-133">Example</span></span>  

 <span data-ttu-id="22590-134">IIS がホストする電卓サービスのコードの完全な一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="22590-134">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="22590-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="22590-135">See also</span></span>

- [<span data-ttu-id="22590-136">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="22590-136">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="22590-137">ホスティング サービス</span><span class="sxs-lookup"><span data-stu-id="22590-137">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="22590-138">WCF サービスと ASP.NET</span><span class="sxs-lookup"><span data-stu-id="22590-138">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="22590-139">Security</span><span class="sxs-lookup"><span data-stu-id="22590-139">Security</span></span>](security.md)
- <span data-ttu-id="22590-140">[AppFabric のホスティング機能](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="22590-140">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
