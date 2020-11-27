---
title: '方法: 構成でサービス バインディングを指定する'
description: 構成ファイルで WCF サービスのエンドポイントを構成する方法について説明します。 コントラクトは、サービスに対して定義され、クラスに実装されます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 06b1cd009d28f854ec73286efa29d42f0f557314
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293690"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a><span data-ttu-id="29094-104">方法: 構成でサービス バインディングを指定する</span><span class="sxs-lookup"><span data-stu-id="29094-104">How to: Specify a Service Binding in Configuration</span></span>

<span data-ttu-id="29094-105">この例では、簡単な電卓サービス用に `ICalculator` コントラクトを定義し、そのサービスを `CalculatorService` クラスで実装し、そのエンドポイントを Web.config ファイルで構成します。このファイルでは、サービスが <xref:System.ServiceModel.BasicHttpBinding> を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="29094-105">In this example, an `ICalculator` contract is defined for a basic calculator service, the service is implemented in the `CalculatorService` class, and then its endpoint is configured in the Web.config file, where it is specified that the service uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="29094-106">構成ではなくコードを使用してこのサービスを構成する方法の詳細については、「 [方法: コード内でサービスバインディングを指定](how-to-specify-a-service-binding-in-code.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29094-106">For a description of how to configure this service using code instead of a configuration, see [How to: Specify a Service Binding in Code](how-to-specify-a-service-binding-in-code.md).</span></span>  
  
 <span data-ttu-id="29094-107">通常、ベスト プラクティスは、コードで命令として記述するよりも、構成でバインディングを指定して情報を明示的にアドレス指定することです。</span><span class="sxs-lookup"><span data-stu-id="29094-107">It is usually the best practice to specify the binding and address information declaratively in configuration rather than imperatively in code.</span></span> <span data-ttu-id="29094-108">設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="29094-108">Defining endpoints in code is usually not practical because the bindings and addresses for a deployed service are typically different from those used while the service is being developed.</span></span> <span data-ttu-id="29094-109">一般的に、バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="29094-109">More generally, keeping the binding and addressing information out of the code allows them to change without having to recompile or redeploy the application.</span></span>  
  
 <span data-ttu-id="29094-110">次のすべての構成手順は、 [構成エディターツール (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="29094-110">All of the following configuration steps can be undertaken using the [Configuration Editor Tool (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="29094-111">この例のソースコピーについては、「 [Basicbinding](./samples/basicbinding.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29094-111">For the source copy of this example, see [BasicBinding](./samples/basicbinding.md).</span></span>  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a><span data-ttu-id="29094-112">サービスの構成で BasicHttpBinding が使用されるように指定するには</span><span class="sxs-lookup"><span data-stu-id="29094-112">To specify the BasicHttpBinding to use to configure the service</span></span>  
  
1. <span data-ttu-id="29094-113">サービスの種類にサービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="29094-113">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. <span data-ttu-id="29094-114">サービス クラスにサービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="29094-114">Implement the service contract in a service class.</span></span>  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > <span data-ttu-id="29094-115">アドレス情報とバインディング情報は、サービスの実装内では指定されません。</span><span class="sxs-lookup"><span data-stu-id="29094-115">Address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="29094-116">また、構成ファイルからこの情報をフェッチするためのコードを記述する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="29094-116">Also, code does not have to be written to fetch that information from the configuration file.</span></span>  
  
3. <span data-ttu-id="29094-117">`CalculatorService` を使用する <xref:System.ServiceModel.WSHttpBinding> のエンドポイントを構成する Web.config ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="29094-117">Create a Web.config file to configure an endpoint for the `CalculatorService` that uses the <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="29094-118">次の行を含む Service.svc ファイルを作成し、インターネット インフォメーション サービス (IIS: Internet Information Services) 仮想ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="29094-118">Create a Service.svc file that contains the following line and place it in your Internet Information Services (IIS) virtual directory.</span></span>  
  
    ```aspx-csharp
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a><span data-ttu-id="29094-119">バインディング プロパティの既定値を変更するには</span><span class="sxs-lookup"><span data-stu-id="29094-119">To modify the default values of the binding properties</span></span>  
  
1. <span data-ttu-id="29094-120">の既定のプロパティ値の1つを変更するには、 <xref:System.ServiceModel.WSHttpBinding> 要素内に新しいバインド構成名を作成 `<binding name="Binding1">` [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) し、このバインド要素でバインディングの属性の新しい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="29094-120">To modify one of the default property values of the <xref:System.ServiceModel.WSHttpBinding>, create a new binding configuration name - `<binding name="Binding1">` - within the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element and set the new values for the attributes of the binding in this binding element.</span></span> <span data-ttu-id="29094-121">たとえば、開く操作と閉じる操作の既定のタイムアウト値を 1 分から 2 分に変更するには、構成ファイルに以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="29094-121">For example, to change the default open and close timeout values of 1 minute to 2 minutes, add the following to the configuration file.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="29094-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="29094-122">See also</span></span>

- [<span data-ttu-id="29094-123">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="29094-123">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="29094-124">エンドポイント アドレスの指定</span><span class="sxs-lookup"><span data-stu-id="29094-124">Specifying an Endpoint Address</span></span>](specifying-an-endpoint-address.md)
