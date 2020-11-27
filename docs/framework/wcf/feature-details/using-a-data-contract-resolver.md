---
title: データ コントラクト リゾルバーの使用
ms.date: 03/30/2017
ms.assetid: 2e68a16c-36f0-4df4-b763-32021bff2b89
ms.openlocfilehash: a86ad21a5846feec37f8b4b48843eab2d6c161da
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289634"
---
# <a name="using-a-data-contract-resolver"></a><span data-ttu-id="c9000-102">データ コントラクト リゾルバーの使用</span><span class="sxs-lookup"><span data-stu-id="c9000-102">Using a Data Contract Resolver</span></span>

<span data-ttu-id="c9000-103">データ コントラクト リゾルバーでは、既知の型を動的に構成できます。</span><span class="sxs-lookup"><span data-stu-id="c9000-103">A data contract resolver allows you to configure known types dynamically.</span></span> <span data-ttu-id="c9000-104">データ コントラクトが予期しない型をシリアル化または逆シリアル化するときには、既知の型が必要です。</span><span class="sxs-lookup"><span data-stu-id="c9000-104">Known types are required when serializing or deserializing a type not expected by a data contract.</span></span> <span data-ttu-id="c9000-105">既知の型の詳細については、「 [データコントラクトの既知の型](data-contract-known-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9000-105">For more information about known types, see [Data Contract Known Types](data-contract-known-types.md).</span></span> <span data-ttu-id="c9000-106">通常、既知の型は静的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="c9000-106">Known types are normally specified statically.</span></span> <span data-ttu-id="c9000-107">これは、操作を実装する間に操作が受け取る可能性のあるすべての型を把握しておく必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="c9000-107">This means you would have to know all the possible types an operation may receive while implementing the operation.</span></span> <span data-ttu-id="c9000-108">これが当てはまらず、既知の型を動的に指定できることが重要である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c9000-108">There are scenarios in which this is not true and being able to specify known types dynamically is important.</span></span>  
  
## <a name="creating-a-data-contract-resolver"></a><span data-ttu-id="c9000-109">データ コントラクト リゾルバーの作成</span><span class="sxs-lookup"><span data-stu-id="c9000-109">Creating a Data Contract Resolver</span></span>  

 <span data-ttu-id="c9000-110">データ コントラクト リゾルバーを作成する際には、2 つのメソッド、<xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> および <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> を実装します。</span><span class="sxs-lookup"><span data-stu-id="c9000-110">Creating a data contract resolver involves implementing two methods, <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> and <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A>.</span></span> <span data-ttu-id="c9000-111">これらの 2 つのメソッドは、シリアル化および逆シリアル化の際に使用されるコールバックを実装します。</span><span class="sxs-lookup"><span data-stu-id="c9000-111">These two methods implement callbacks that are used during serialization and deserialization, respectively.</span></span> <span data-ttu-id="c9000-112"><xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> メソッドはシリアル化の際に呼び出されて、データ コントラクト型を受け取り、それを `xsi:type` の名前および名前空間にマップします。</span><span class="sxs-lookup"><span data-stu-id="c9000-112">The <xref:System.Runtime.Serialization.DataContractResolver.TryResolveType%2A> method is invoked during serialization and takes a data contract type and maps it to an `xsi:type` name and namespace.</span></span> <span data-ttu-id="c9000-113"><xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> メソッドは逆シリアル化の際に呼び出されて、`xsi:type` の名前および名前空間を受け取り、それをデータ コントラクト型に解決します。</span><span class="sxs-lookup"><span data-stu-id="c9000-113">The <xref:System.Runtime.Serialization.DataContractResolver.ResolveName%2A> method is invoked during deserialization and takes an `xsi:type` name and namespace and resolves it to a data contract type.</span></span> <span data-ttu-id="c9000-114">これらのメソッドの両方には `knownTypeResolver` パラメーターがあり、これを使用して、既定の既知の型のリゾルバーを実装で使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9000-114">Both of these methods have a `knownTypeResolver` parameter that can be used to use the default known type resolver in your implementation.</span></span>  
  
 <span data-ttu-id="c9000-115">次の例は、<xref:System.Runtime.Serialization.DataContractResolver> を実装し、データ コントラクト型 `Customer` から派生した `Person` という名前のデータ コントラクト型との間でマッピングを行う方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c9000-115">The following example shows how to implement a <xref:System.Runtime.Serialization.DataContractResolver> to map to and from a data contract type named `Customer` derived from a data contract type `Person`.</span></span>  
  
```csharp  
public class MyCustomerResolver : DataContractResolver  
{  
    public override bool TryResolveType(Type dataContractType, Type declaredType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        if (dataContractType == typeof(Customer))  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add("SomeCustomer");  
            typeNamespace = dictionary.Add("http://tempuri.com");  
            return true;  
        }  
        else  
        {  
            return knownTypeResolver.TryResolveType(dataContractType, declaredType, null, out typeName, out typeNamespace);  
        }  
    }  
  
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        if (typeName == "SomeCustomer" && typeNamespace == "http://tempuri.com")  
        {  
            return typeof(Customer);  
        }  
        else  
        {  
            return knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="c9000-116"><xref:System.Runtime.Serialization.DataContractResolver> を定義したら、次の例に示すように、それを <xref:System.Runtime.Serialization.DataContractSerializer> コンストラクターに渡して使用できます。</span><span class="sxs-lookup"><span data-stu-id="c9000-116">Once you have defined a <xref:System.Runtime.Serialization.DataContractResolver> you can use it by passing it to the <xref:System.Runtime.Serialization.DataContractSerializer> constructor as shown in the following example.</span></span>  
  
```csharp
XmlObjectSerializer serializer = new DataContractSerializer(typeof(Customer), null, Int32.MaxValue, false, false, null, new MyCustomerResolver());  
```  
  
 <span data-ttu-id="c9000-117">次の例に示すように、<xref:System.Runtime.Serialization.DataContractResolver> を、<xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> メソッドへの呼び出しで指定できます。</span><span class="sxs-lookup"><span data-stu-id="c9000-117">You can specify a <xref:System.Runtime.Serialization.DataContractResolver> in a call to the <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A?displayProperty=nameWithType> or <xref:System.Runtime.Serialization.DataContractSerializer.WriteObject%2A?displayProperty=nameWithType> methods, as shown in the following example.</span></span>  
  
```csharp
MemoryStream ms = new MemoryStream();  
DataContractSerializer serializer = new DataContractSerializer(typeof(Customer));  
XmlDictionaryWriter writer = XmlDictionaryWriter.CreateDictionaryWriter(XmlWriter.Create(ms));  
serializer.WriteObject(writer, new Customer(), new MyCustomerResolver());  
writer.Flush();  
ms.Position = 0;  
Console.WriteLine(((Customer)serializer.ReadObject(XmlDictionaryReader.CreateDictionaryReader(XmlReader.Create(ms)), false, new MyCustomerResolver()));  
```  
  
 <span data-ttu-id="c9000-118">また、次の例に示すように、<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> で設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c9000-118">Or you can set it on the <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> as shown in the following example.</span></span>  
  
```csharp
ServiceHost host = new ServiceHost(typeof(MyService));  
  
ContractDescription cd = host.Description.Endpoints[0].Contract;  
OperationDescription myOperationDescription = cd.Operations.Find("Echo");  
  
DataContractSerializerOperationBehavior serializerBehavior = myOperationDescription.Behaviors.Find<DataContractSerializerOperationBehavior>();  
if (serializerBehavior == null)  
{  
    serializerBehavior = new DataContractSerializerOperationBehavior(myOperationDescription);  
    myOperationDescription.Behaviors.Add(serializerBehavior);  
}  
  
SerializerBehavior.DataContractResolver = new MyCustomerResolver();  
```  
  
 <span data-ttu-id="c9000-119">サービスに適用できる属性を実装して、データ コントラクト リゾルバーを宣言によって指定できます。</span><span class="sxs-lookup"><span data-stu-id="c9000-119">You can declaratively specify a data contract resolver by implementing an attribute that can be applied to a service.</span></span>  <span data-ttu-id="c9000-120">詳細については、「 [Knownassemblyattribute](../samples/knownassemblyattribute.md) サンプル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9000-120">For more information, see the [KnownAssemblyAttribute](../samples/knownassemblyattribute.md) sample.</span></span> <span data-ttu-id="c9000-121">このサンプルでは、カスタムデータコントラクトリゾルバーをサービスの動作に追加する "KnownAssembly" という属性を実装します。</span><span class="sxs-lookup"><span data-stu-id="c9000-121">This sample implements an attribute called "KnownAssembly" that adds a custom data contract resolver to the service’s behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9000-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9000-122">See also</span></span>

- [<span data-ttu-id="c9000-123">既知のデータ コントラクト型</span><span class="sxs-lookup"><span data-stu-id="c9000-123">Data Contract Known Types</span></span>](data-contract-known-types.md)
- [<span data-ttu-id="c9000-124">DataContractSerializer サンプル</span><span class="sxs-lookup"><span data-stu-id="c9000-124">DataContractSerializer Sample</span></span>](../samples/datacontractserializer-sample.md)
- [<span data-ttu-id="c9000-125">KnownAssemblyAttribute</span><span class="sxs-lookup"><span data-stu-id="c9000-125">KnownAssemblyAttribute</span></span>](../samples/knownassemblyattribute.md)
