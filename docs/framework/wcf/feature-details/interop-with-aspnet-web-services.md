---
title: ASP.NET Web サービスとの相互運用
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: cca4e1b3da26d8026d41d0a7107432cdd2960545
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276634"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="fc89c-102">ASP.NET Web サービスとの相互運用</span><span class="sxs-lookup"><span data-stu-id="fc89c-102">Interoperability with ASP.NET Web Services</span></span>

<span data-ttu-id="fc89c-103">ASP.NET ウェブサービスと Windows Communication Foundation (WCF) Web サービスの間の相互運用性を実現するには、両方のテクノロジを使用して実装されたサービスが WS-I Basic Profile 1.1 仕様に準拠していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fc89c-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="fc89c-104">WS-I Basic Profile 1.1 に準拠している ASP.NET Web サービスは、WCF システム指定のバインディングを使用して、WCF クライアントと相互運用 <xref:System.ServiceModel.BasicHttpBinding> できます。</span><span class="sxs-lookup"><span data-stu-id="fc89c-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="fc89c-105"><xref:System.Web.Services.WebService> <xref:System.Web.Services.WebMethodAttribute> 次のサンプルコードに示すように、属性と属性をクラスではなくインターフェイスに追加し、インターフェイスを実装するクラスを記述するには、ASP.NET 2.0 オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc89c-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="fc89c-106"><xref:System.Web.Services.WebService> 属性を持つインターフェイスは、同じコントラクトを異なる方法で実装する可能性のあるさまざまなクラスで再利用可能なサービスによって実行される操作のコントラクトを構成するため、このオプションを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fc89c-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="fc89c-107"><xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> 属性を使用する場合、`SOAPAction` HTTP ヘッダーではなく、SOAP メッセージの本文要素の完全修飾名に基づいてメッセージをメソッドへルーティングすることは避けます。</span><span class="sxs-lookup"><span data-stu-id="fc89c-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="fc89c-108">WCF は、 `SOAPAction` メッセージのルーティングに HTTP ヘッダーを使用します。</span><span class="sxs-lookup"><span data-stu-id="fc89c-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="fc89c-109"><xref:System.Xml.Serialization.XmlSerializer> によって既定で型のシリアル化が行われる XML は、XML の名前空間が明示的に定義されている場合、<xref:System.Runtime.Serialization.DataContractSerializer> によって型のシリアル化が行われる XML と意味的に同一です。</span><span class="sxs-lookup"><span data-stu-id="fc89c-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="fc89c-110">WCF を導入するために、ASP.NET Web サービスで使用するデータ型を定義する場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="fc89c-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="fc89c-111">XML スキーマではなく、.NET Framework クラスを使用して型を定義します。</span><span class="sxs-lookup"><span data-stu-id="fc89c-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="fc89c-112"><xref:System.SerializableAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> だけをそのクラスに追加します。後者を使用して型の名前空間を明示的に定義してください。</span><span class="sxs-lookup"><span data-stu-id="fc89c-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="fc89c-113">.NET Framework クラスを XML に変換する方法を制御する目的で、<xref:System.Xml.Serialization> 名前空間の属性を追加しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc89c-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="fc89c-114">この手法を採用すると、後から <xref:System.Runtime.Serialization.DataContractAttribute> および <xref:System.Runtime.Serialization.DataMemberAttribute> を追加することで、転送のためにクラスをシリアル化する XML に大きな変更を加えることなく .NET クラスをデータ コントラクトにすることができます。</span><span class="sxs-lookup"><span data-stu-id="fc89c-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="fc89c-115">ASP.NET Web サービスによってメッセージで使用される型は、WCF アプリケーションによるデータコントラクトとして処理することができ、その他の利点として、WCF アプリケーションでパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="fc89c-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="fc89c-116">インターネット インフォメーション サービス (IIS) に用意されている認証オプションは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fc89c-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="fc89c-117">WCF クライアントはこれらをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="fc89c-117">WCF clients do not support them.</span></span> <span data-ttu-id="fc89c-118">サービスをセキュリティで保護する必要がある場合は、WCF に用意されているオプションを使用します。これらのオプションは堅牢で、標準プロトコルに基づいているためです。</span><span class="sxs-lookup"><span data-stu-id="fc89c-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="fc89c-119">ServiceModel HttpModule の読み込みがパフォーマンスに及ぼす影響</span><span class="sxs-lookup"><span data-stu-id="fc89c-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  

 <span data-ttu-id="fc89c-120">.NET Framework Version 3.0 では、WCF `HttpModule` が、すべての ASP.NET アプリケーションが WCF 対応になるように、ルートの Web.config ファイルにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fc89c-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="fc89c-121">これによりパフォーマンスに影響が出る場合があるため、次の例に示すように、Web.config ファイルの `ServiceModel` を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="fc89c-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="fc89c-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc89c-122">See also</span></span>

- [<span data-ttu-id="fc89c-123">方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する</span><span class="sxs-lookup"><span data-stu-id="fc89c-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](config-wcf-service-with-aspnet-web-service.md)
