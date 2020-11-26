---
title: '方法: 構成でクライアント バインディングを指定する'
description: 構成ファイルで WCF クライアントのバインドを宣言によって指定する方法について説明します。 この例では、クライアントがサービスにアクセスします。
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: e8a552211b28c1323b2afd595c5b060db6b2824a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236508"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a><span data-ttu-id="015c1-104">方法: 構成でクライアント バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="015c1-104">How to: Specify a Client Binding in Configuration</span></span>

<span data-ttu-id="015c1-105">この例では、電卓サービスを使用するためのクライアント コンソール アプリケーションを作成し、そのクライアントのバインディングを構成で宣言によって指定します。</span><span class="sxs-lookup"><span data-stu-id="015c1-105">In this example, a client console application is created to use a calculator service, and the binding for that client is specified declaratively in configuration.</span></span> <span data-ttu-id="015c1-106">クライアントは `CalculatorService` にアクセスします。これにより、`ICalculator` インターフェイスが実装され、サービスとクライアントの両方で <xref:System.ServiceModel.BasicHttpBinding> クラスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="015c1-106">The client accesses the `CalculatorService`, which implements the `ICalculator` interface, and both the service and the client use the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="015c1-107">ここで説明する手順は、電卓サービスが実行されていることを前提とします。</span><span class="sxs-lookup"><span data-stu-id="015c1-107">The procedure outlined assumes that the calculator service is running.</span></span> <span data-ttu-id="015c1-108">サービスを構築する方法の詳細については、「 [方法: 構成でサービスバインディングを指定](how-to-specify-a-service-binding-in-configuration.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="015c1-108">For information about how to build the service, see [How to: Specify a Service Binding in Configuration](how-to-specify-a-service-binding-in-configuration.md).</span></span> <span data-ttu-id="015c1-109">また、Windows Communication Foundation (WCF) によって提供される [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、クライアントコンポーネントを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="015c1-109">It also uses the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) that Windows Communication Foundation (WCF) provides to automatically generate the client components.</span></span> <span data-ttu-id="015c1-110">このツールにより、サービスにアクセスするためのクライアント コードと構成が生成されます。</span><span class="sxs-lookup"><span data-stu-id="015c1-110">The tool generates the client code and configuration for accessing the service.</span></span>  
  
 <span data-ttu-id="015c1-111">クライアントは 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="015c1-111">The client is built in two parts.</span></span> <span data-ttu-id="015c1-112">Svcutil.exe によって、`ClientCalculator` インターフェイスを実装する `ICalculator` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="015c1-112">Svcutil.exe generates the `ClientCalculator` that implements the `ICalculator` interface.</span></span> <span data-ttu-id="015c1-113">次に、`ClientCalculator` のインスタンスを作成することで、クライアント アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="015c1-113">This client application is then constructed by constructing an instance of `ClientCalculator`.</span></span>  
  
 <span data-ttu-id="015c1-114">通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。</span><span class="sxs-lookup"><span data-stu-id="015c1-114">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="015c1-115">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="015c1-115">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="015c1-116">一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="015c1-116">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="015c1-117">[構成エディターツール (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)を使用して、次のすべての構成手順を実行できます。</span><span class="sxs-lookup"><span data-stu-id="015c1-117">You can perform all of the following configuration steps by using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="015c1-118">この例のソースコピーについては、 [Basicbinding](./samples/basicbinding.md) サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="015c1-118">For the source copy of this example, see the [BasicBinding](./samples/basicbinding.md) sample.</span></span>  
  
### <a name="specifying-a-client-binding-in-configuration"></a><span data-ttu-id="015c1-119">構成を使用したクライアント バインディングの指定</span><span class="sxs-lookup"><span data-stu-id="015c1-119">Specifying a client binding in configuration</span></span>  
  
1. <span data-ttu-id="015c1-120">コマンド ラインから Svcutil.exe を実行して、サービス メタデータからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="015c1-120">Use Svcutil.exe from the command line to generate code from service metadata.</span></span>  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="015c1-121">生成されたクライアントには、クライアントの実装時に満たされなければならないサービス コントラクトを定義する `ICalculator` インターフェイスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="015c1-121">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. <span data-ttu-id="015c1-122">生成されたクライアントは `ClientCalculator` も実装します。</span><span class="sxs-lookup"><span data-stu-id="015c1-122">The generated client also contains the implementation of the `ClientCalculator`.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. <span data-ttu-id="015c1-123"><xref:System.ServiceModel.BasicHttpBinding> クラスを使用するクライアントの構成も、Svcutil.exe により生成されます。</span><span class="sxs-lookup"><span data-stu-id="015c1-123">Svcutil.exe also generates the configuration for the client that uses the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span> <span data-ttu-id="015c1-124">Visual Studio を使用する場合は、このファイルに App.config という名前を指定します。サービスの実装内でアドレスおよびバインド情報が指定されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="015c1-124">When using Visual Studio, name this file App.config. Note that the address and binding information are not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="015c1-125">同様に、コードは構成ファイルから情報を取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="015c1-125">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. <span data-ttu-id="015c1-126">アプリケーションで `ClientCalculator` のインスタンスを作成し、サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="015c1-126">Create an instance of the `ClientCalculator` in an application, and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. <span data-ttu-id="015c1-127">クライアントをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="015c1-127">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="015c1-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="015c1-128">See also</span></span>

- [<span data-ttu-id="015c1-129">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="015c1-129">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
