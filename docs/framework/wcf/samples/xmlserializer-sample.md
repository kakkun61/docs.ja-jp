---
title: XMLSerializer サンプル
ms.date: 03/30/2017
ms.assetid: 7d134453-9a35-4202-ba77-9ca3a65babc3
ms.openlocfilehash: 47fdcfeda796d99740a49997ee85fc63fbb27b21
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237574"
---
# <a name="xmlserializer-sample"></a><span data-ttu-id="e37e8-102">XMLSerializer サンプル</span><span class="sxs-lookup"><span data-stu-id="e37e8-102">XMLSerializer Sample</span></span>

<span data-ttu-id="e37e8-103">このサンプルでは、<xref:System.Xml.Serialization.XmlSerializer> と互換性のある型をシリアル化および逆シリアル化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e37e8-103">This sample demonstrates how to serialize and deserialize types that are compatible with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="e37e8-104">既定の Windows Communication Foundation (WCF) フォーマッタは <xref:System.Runtime.Serialization.DataContractSerializer> クラスです。</span><span class="sxs-lookup"><span data-stu-id="e37e8-104">The default Windows Communication Foundation (WCF) formatter is the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span> <span data-ttu-id="e37e8-105"><xref:System.Xml.Serialization.XmlSerializer> クラスを使用すると、<xref:System.Runtime.Serialization.DataContractSerializer> クラスを使用できない場合に、型をシリアル化および逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="e37e8-105">The <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize and deserialize types when the <xref:System.Runtime.Serialization.DataContractSerializer> class cannot be used.</span></span> <span data-ttu-id="e37e8-106">これは、XML を厳密に制御する必要がある場合、たとえば、データの一部が XML 属性であるが XML 要素ではない、などと制御する必要がある場合に多く該当します。</span><span class="sxs-lookup"><span data-stu-id="e37e8-106">This is often the case when precise control over the XML is required - for example, if a piece of data must be an XML attribute and not an XML element.</span></span> <span data-ttu-id="e37e8-107">また、は、 <xref:System.Xml.Serialization.XmlSerializer> WCF 以外のサービス用のクライアントを作成するときに、自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="e37e8-107">Also, the <xref:System.Xml.Serialization.XmlSerializer> often gets automatically selected when creating clients for non-WCF services.</span></span>  
  
 <span data-ttu-id="e37e8-108">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="e37e8-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e37e8-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e37e8-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e37e8-110"><xref:System.ServiceModel.ServiceContractAttribute> と <xref:System.ServiceModel.XmlSerializerFormatAttribute> をインターフェイスに適用する必要があります。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e37e8-110">The <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.XmlSerializerFormatAttribute> must be applied to the interface as shown in the following sample code.</span></span>  
  
```csharp  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface IXmlSerializerCalculator  
{  
    [OperationContract]  
    ComplexNumber Add(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Subtract(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Multiply(ComplexNumber n1, ComplexNumber n2);  
    [OperationContract]  
    ComplexNumber Divide(ComplexNumber n1, ComplexNumber n2);  
}  
```  
  
 <span data-ttu-id="e37e8-111">`ComplexNumber` クラスのパブリック メンバは、<xref:System.Xml.Serialization.XmlSerializer> によって XML 属性としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="e37e8-111">The public members of `ComplexNumber` class are serialized by <xref:System.Xml.Serialization.XmlSerializer> as XML attributes.</span></span> <span data-ttu-id="e37e8-112"><xref:System.Runtime.Serialization.DataContractSerializer> は、この種の XML インスタンスの作成には使用できません。</span><span class="sxs-lookup"><span data-stu-id="e37e8-112">The <xref:System.Runtime.Serialization.DataContractSerializer> cannot be used to create this kind of XML instance.</span></span>  
  
```csharp  
public class ComplexNumber  
{  
    private double real;  
    private double imaginary;  
  
    [XmlAttribute]  
    public double Real  
    {  
        get { return real; }  
        set { real = value; }  
    }  
  
    [XmlAttribute]  
    public double Imaginary  
    {  
        get { return imaginary; }  
        set { imaginary = value; }  
    }  
  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
    public ComplexNumber()  
    {  
        this.Real = 0;  
        this.Imaginary = 0;  
    }  
  
}  
```  
  
 <span data-ttu-id="e37e8-113">サービス実装は計算を行い、結果を返します。つまり、`ComplexNumber` 型の値を受け入れて返します。</span><span class="sxs-lookup"><span data-stu-id="e37e8-113">The service implementation calculates and returns the appropriate result—accepting and returning values of the `ComplexNumber` type.</span></span>  
  
```csharp  
public class XmlSerializerCalculatorService : IXmlSerializerCalculator  
{  
    public ComplexNumber Add(ComplexNumber n1, ComplexNumber n2)  
    {  
        return new ComplexNumber(n1.Real + n2.Real, n1.Imaginary +  
                                                      n2.Imaginary);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="e37e8-114">クライアント実装でも複素数を使用します。</span><span class="sxs-lookup"><span data-stu-id="e37e8-114">The client implementation also uses complex numbers.</span></span> <span data-ttu-id="e37e8-115">サービスコントラクトとデータ型はどちらも、サービスメタデータから [ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) によって生成された generatedClient.cs ソースファイルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="e37e8-115">Both the service contract and the data types are defined in the generatedClient.cs source file, which was generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from service metadata.</span></span> <span data-ttu-id="e37e8-116">コントラクトが <xref:System.Runtime.Serialization.DataContractSerializer> でシリアル化されずにこの場合の送出元の `XmlSerializable` 型に戻る場合、Svcutil.exe で検出することができます。</span><span class="sxs-lookup"><span data-stu-id="e37e8-116">Svcutil.exe can detect when a contract is not serializable by the <xref:System.Runtime.Serialization.DataContractSerializer> and reverts to emitting `XmlSerializable` types in this case.</span></span> <span data-ttu-id="e37e8-117"><xref:System.Xml.Serialization.XmlSerializer> を強制的に使用する場合は、/serializer:XmlSerializer (XmlSerializer を使用) コマンド オプションを Svcutil.exe ツールに渡します。</span><span class="sxs-lookup"><span data-stu-id="e37e8-117">If you want to force the use of the <xref:System.Xml.Serialization.XmlSerializer>, you can pass the /serializer:XmlSerializer (use XmlSerializer) command option to the Svcutil.exe tool.</span></span>  
  
```csharp  
// Create a client.  
XmlSerializerCalculatorClient client = new  
                         XmlSerializerCalculatorClient();  
  
// Call the Add service operation.  
ComplexNumber value1 = new ComplexNumber();  
value1.Real = 1;  
value1.Imaginary = 2;  
ComplexNumber value2 = new ComplexNumber();  
value2.Real = 3;  
value2.Imaginary = 4;  
ComplexNumber result = client.Add(value1, value2);  
Console.WriteLine("Add({0} + {1}i, {2} + {3}i) = {4} + {5}i",  
    value1.Real, value1.Imaginary, value2.Real, value2.Imaginary,
    result.Real, result.Imaginary);  
    …  
}  
```  
  
 <span data-ttu-id="e37e8-118">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e37e8-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e37e8-119">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e37e8-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(1 + 2i, 3 + 4i) = 4 + 6i  
Subtract(1 + 2i, 3 + 4i) = -2 + -2i  
Multiply(2 + 3i, 4 + 7i) = -13 + 26i  
Divide(3 + 7i, 5 + -2i) = 0.0344827586206897 + 1.41379310344828i  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e37e8-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="e37e8-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e37e8-121">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e37e8-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e37e8-122">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e37e8-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e37e8-123">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e37e8-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e37e8-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e37e8-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e37e8-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e37e8-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e37e8-126">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="e37e8-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e37e8-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e37e8-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\XmlSerializer`  
