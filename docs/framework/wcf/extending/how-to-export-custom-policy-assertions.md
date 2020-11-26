---
title: '方法: カスタム ポリシー アサーションをエクスポートする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 8bdc9948d6846631fde1d428c113682f40d15ec3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249216"
---
# <a name="how-to-export-custom-policy-assertions"></a><span data-ttu-id="ae5d5-102">方法: カスタム ポリシー アサーションをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="ae5d5-102">How to: Export Custom Policy Assertions</span></span>

<span data-ttu-id="ae5d5-103">ポリシー アサーションはサービス エンドポイントの機能と要件を説明します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-103">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span> <span data-ttu-id="ae5d5-104">サービス アプリケーションは、サービス メタデータに含まれるカスタム ポリシー アサーションを使用して、エンドポイントのバインディングまたはコントラクトのカスタマイズ情報をクライアント アプリケーションに伝達します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-104">Service applications can use custom policy assertions in service metadata to communicate endpoint, binding or contract customization information to the client application.</span></span> <span data-ttu-id="ae5d5-105">Windows Communication Foundation (WCF) を使用すると、通信する機能や要件に応じて、エンドポイント、操作、またはメッセージのサブジェクトで WSDL バインディングに結び付けられているポリシー式のアサーションをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-105">You can use Windows Communication Foundation (WCF) to export assertions in policy expressions attached in WSDL bindings at the endpoint, operation, or message subjects, depending upon the capabilities or requirements you are communicating.</span></span>  
  
 <span data-ttu-id="ae5d5-106">カスタム ポリシー アサーションは、<xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> インターフェイスを <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> に実装して、サービス エンドポイントのバインディングにバインド要素を直接挿入するか、またはアプリケーション構成ファイルにバインド要素を登録することによってエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-106">Custom policy assertions are exported by implementing the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and either inserting the binding element directly into the binding of the service endpoint or by registering the binding element in your application configuration file.</span></span> <span data-ttu-id="ae5d5-107">ポリシーのエクスポートの実装では、<xref:System.Xml.XmlElement?displayProperty=nameWithType> メソッドに渡された <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> の適切な <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> に、<xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> インスタンスとしてカスタム ポリシー アサーションを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-107">Your policy export implementation should add your custom policy assertion as a <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance to the appropriate <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passed into the <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> method.</span></span>  
  
 <span data-ttu-id="ae5d5-108">また、<xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> クラスの <xref:System.ServiceModel.Description.WsdlExporter> プロパティをチェックし、入れ子になったポリシー表現およびポリシー フレームワーク属性を、指定されたポリシー バージョンに基づいた正しい名前空間にエクスポートする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-108">In addition you must check the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property of the <xref:System.ServiceModel.Description.WsdlExporter> class and export nested policy expressions and policy framework attributes in the correct namespace based on the policy version specified.</span></span>  
  
 <span data-ttu-id="ae5d5-109">カスタムポリシーアサーションをインポートするには、「」 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> および「 [方法: カスタムポリシーアサーションをインポート](how-to-import-custom-policy-assertions.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-109">To import custom policy assertions, see <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> and [How to: Import Custom Policy Assertions](how-to-import-custom-policy-assertions.md).</span></span>  
  
### <a name="to-export-custom-policy-assertions"></a><span data-ttu-id="ae5d5-110">カスタム ポリシー アサーションをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="ae5d5-110">To export custom policy assertions</span></span>  
  
1. <span data-ttu-id="ae5d5-111"><xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> に <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-111">Implement the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ae5d5-112">バインディング レベルでのカスタム ポリシー アサーションの実装を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-112">The following code example shows the implementation of a custom policy assertion at the binding level.</span></span>  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. <span data-ttu-id="ae5d5-113">プログラムまたはアプリケーション構成ファイルを使用して、エンドポイントのバインディングにバインド要素を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-113">Insert the binding element into the endpoint binding either programmatically or using an application configuration file.</span></span> <span data-ttu-id="ae5d5-114">次の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-114">See the following procedures.</span></span>  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a><span data-ttu-id="ae5d5-115">アプリケーション構成ファイルを使用してバインディングを挿入するには</span><span class="sxs-lookup"><span data-stu-id="ae5d5-115">To insert a binding element using an application configuration file</span></span>  
  
1. <span data-ttu-id="ae5d5-116">カスタム ポリシー アサーション バインド要素の <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> を実装します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-116">Implement <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> for your custom policy assertion binding element.</span></span>  
  
2. <span data-ttu-id="ae5d5-117">要素を使用して、構成ファイルにバインド要素拡張を追加し [\<bindingElementExtensions>](../../configure-apps/file-schema/wcf/bindingelementextensions.md) ます。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-117">Add the binding element extension to the configuration file using the [\<bindingElementExtensions>](../../configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span></span>  
  
3. <span data-ttu-id="ae5d5-118"><xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> を使用してカスタム バインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-118">Build a custom binding using the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-insert-a-binding-element-programmatically"></a><span data-ttu-id="ae5d5-119">プログラムでバインド要素を挿入するには</span><span class="sxs-lookup"><span data-stu-id="ae5d5-119">To insert a binding element programmatically</span></span>  
  
1. <span data-ttu-id="ae5d5-120">新しい <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> を作成して <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-120">Create a new <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and add it to a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="ae5d5-121">手順 1. のカスタム バインドを</span><span class="sxs-lookup"><span data-stu-id="ae5d5-121">Add the custom binding from step 1.</span></span> <span data-ttu-id="ae5d5-122">新しいエンドポイントに追加し、<xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドを呼び出してその新しいサービス エンドポイントを <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> に追加します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-122">to a new endpoint and add that new service endpoint to the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> by calling the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
3. <span data-ttu-id="ae5d5-123"><xref:System.ServiceModel.ServiceHost> を開きます。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-123">Open the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="ae5d5-124">カスタム バインディングの作成と、プログラムによるバインド要素の挿入を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="ae5d5-124">The following code example shows the creation of a custom binding and the programmatic insertion of binding elements.</span></span>  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ae5d5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae5d5-125">See also</span></span>

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [<span data-ttu-id="ae5d5-126">方法: カスタム ポリシー アサーションをインポートする</span><span class="sxs-lookup"><span data-stu-id="ae5d5-126">How to: Import Custom Policy Assertions</span></span>](how-to-import-custom-policy-assertions.md)
