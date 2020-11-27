---
title: DataContract サロゲート
ms.date: 03/30/2017
ms.assetid: b0188f3c-00a9-4cf0-a887-a2284c8fb014
ms.openlocfilehash: 23a83b0a99a17af011bea1193c2ea013a2c3c5a9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253688"
---
# <a name="datacontract-surrogate"></a><span data-ttu-id="1f94e-102">DataContract サロゲート</span><span class="sxs-lookup"><span data-stu-id="1f94e-102">DataContract Surrogate</span></span>

<span data-ttu-id="1f94e-103">このサンプルでは、シリアル化、逆シリアル化、スキーマのエクスポート、スキーマのインポートなどのプロセスを、データ コントラクト サロゲート クラスを使用してカスタマイズする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-103">This sample demonstrates how processes like serialization, deserialization, schema export, and schema import can be customized using a data contract surrogate class.</span></span> <span data-ttu-id="1f94e-104">このサンプルでは、クライアントとサーバーのシナリオでサロゲートを使用する方法を示します。このシナリオでは、データがシリアル化され、Windows Communication Foundation (WCF) クライアントとサービスの間で転送されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-104">This sample shows how to use a surrogate in a client and server scenario where data is serialized and transmitted between a Windows Communication Foundation (WCF) client and service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f94e-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1f94e-106">このサンプルでは、次のサービス コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-106">The sample uses the following service contract:</span></span>  
  
```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
[AllowNonSerializableTypes]  
public interface IPersonnelDataService  
{  
    [OperationContract]  
    void AddEmployee(Employee employee);  
  
    [OperationContract]  
    Employee GetEmployee(string name);  
}  
```  
  
 <span data-ttu-id="1f94e-107">`AddEmployee` 操作は、ユーザーが新しい従業員に関するデータを追加できるようにし、`GetEmployee` 操作は名前に基づく従業員の検索をサポートします。</span><span class="sxs-lookup"><span data-stu-id="1f94e-107">The `AddEmployee` operation allows users to add data about new employees and the `GetEmployee` operation supports search for employees based on name.</span></span>  
  
 <span data-ttu-id="1f94e-108">これらの操作では、次のデータ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-108">These operations use the following data type:</span></span>  
  
```csharp
[DataContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
class Employee  
{  
    [DataMember]  
    public DateTime dateHired;  
  
    [DataMember]  
    public Decimal salary;  
  
    [DataMember]  
    public Person person;  
}  
```  
  
 <span data-ttu-id="1f94e-109">`Employee` 型では、`Person` クラス (次のサンプル コードを参照) は有効なデータ コントラクト クラスではないので、<xref:System.Runtime.Serialization.DataContractSerializer> によってシリアル化できません。</span><span class="sxs-lookup"><span data-stu-id="1f94e-109">In the `Employee` type, the `Person` class (shown in the following sample code) cannot be serialized by the <xref:System.Runtime.Serialization.DataContractSerializer> because it is not a valid data contract class.</span></span>  
  
```csharp
public class Person  
{  
    public string firstName;  
  
    public string lastName;  
  
    public int age;  
  
    public Person() { }  
}  
```  
  
 <span data-ttu-id="1f94e-110"><xref:System.Runtime.Serialization.DataContractAttribute> 属性は `Person` クラスに適用できますが、適用できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="1f94e-110">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the `Person` class, but this is not always possible.</span></span> <span data-ttu-id="1f94e-111">たとえば、`Person` クラスは、ユーザーが制御できない別のアセンブリで定義することができます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-111">For example, the `Person` class can be defined in a separate assembly over which you have no control.</span></span>  
  
 <span data-ttu-id="1f94e-112">このような制限がある場合、`Person` クラスをシリアル化するには、このクラスを <xref:System.Runtime.Serialization.DataContractAttribute> でマークされた別のクラスに置き換え、必要なデータをこの新しいクラスにコピーするという方法があります。</span><span class="sxs-lookup"><span data-stu-id="1f94e-112">Given this restriction, one way to serialize the `Person` class is to substitute it with another class that is marked with <xref:System.Runtime.Serialization.DataContractAttribute> and copy over necessary data to the new class.</span></span> <span data-ttu-id="1f94e-113">この目的は、`Person` クラスを DataContract として <xref:System.Runtime.Serialization.DataContractSerializer> に表示することです。</span><span class="sxs-lookup"><span data-stu-id="1f94e-113">The objective is to make the `Person` class appear as a DataContract to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="1f94e-114">これは、データ コントラクト クラス以外のクラスをシリアル化する 1 つの方法です。</span><span class="sxs-lookup"><span data-stu-id="1f94e-114">Note that this is one way to serialize non-data contract classes.</span></span>  
  
 <span data-ttu-id="1f94e-115">このサンプルでは、 `Person` クラスを `PersonSurrogated` という別のクラスに論理的に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-115">The sample logically replaces the `Person` class with a different class named `PersonSurrogated`.</span></span>  
  
```csharp
[DataContract(Name="Person", Namespace = "http://Microsoft.ServiceModel.Samples")]  
public class PersonSurrogated  
{  
    [DataMember]  
    public string FirstName;  
  
    [DataMember]  
    public string LastName;  
  
    [DataMember]  
    public int Age;  
}  
```  
  
 <span data-ttu-id="1f94e-116">データ コントラクト サロゲートは、この置き換えを実現するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-116">The data contract surrogate is used to achieve this replacement.</span></span> <span data-ttu-id="1f94e-117">データ コントラクト サロゲートは、<xref:System.Runtime.Serialization.IDataContractSurrogate> を実装するクラスです。</span><span class="sxs-lookup"><span data-stu-id="1f94e-117">A data contract surrogate is a class that implements <xref:System.Runtime.Serialization.IDataContractSurrogate>.</span></span> <span data-ttu-id="1f94e-118">このサンプルでは、`AllowNonSerializableTypesSurrogate` クラスがこのインターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="1f94e-118">In this sample, the `AllowNonSerializableTypesSurrogate` class implements this interface.</span></span>  
  
 <span data-ttu-id="1f94e-119">このインターフェイスの実装での最初のタスクは、`Person` から `PersonSurrogated` への型のマップを確立することです。</span><span class="sxs-lookup"><span data-stu-id="1f94e-119">In the interface implementation, the first task is to establish a type mapping from `Person` to `PersonSurrogated`.</span></span> <span data-ttu-id="1f94e-120">これは、シリアル化の時点およびスキーマをエクスポートする時点の両方で使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-120">This is used both at serialization time as well as at schema export time.</span></span> <span data-ttu-id="1f94e-121">このマッピングは、<xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> メソッドを実装することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-121">This mapping is achieved by implementing the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%28System.Type%29> method.</span></span>  
  
```csharp
public Type GetDataContractType(Type type)  
{  
    if (typeof(Person).IsAssignableFrom(type))  
    {  
        return typeof(PersonSurrogated);  
    }  
    return type;  
}  
```  
  
 <span data-ttu-id="1f94e-122"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> メソッドは、シリアル化中に `Person` インスタンスを `PersonSurrogated` インスタンスにマップします。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-122">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%28System.Object%2CSystem.Type%29> method maps a `Person` instance to a `PersonSurrogated` instance during serialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetObjectToSerialize(object obj, Type targetType)  
{  
    if (obj is Person)  
    {  
        Person person = (Person)obj;  
        PersonSurrogated personSurrogated = new PersonSurrogated();  
        personSurrogated.FirstName = person.firstName;  
        personSurrogated.LastName = person.lastName;  
        personSurrogated.Age = person.age;  
        return personSurrogated;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="1f94e-123"><xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> メソッドは、逆シリアル化のための逆マップを実現します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-123">The <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%28System.Object%2CSystem.Type%29> method provides the reverse mapping for deserialization, as shown in the following sample code.</span></span>  
  
```csharp
public object GetDeserializedObject(object obj,
Type targetType)  
{  
    if (obj is PersonSurrogated)  
    {  
        PersonSurrogated personSurrogated = (PersonSurrogated)obj;  
        Person person = new Person();  
        person.firstName = personSurrogated.FirstName;  
        person.lastName = personSurrogated.LastName;  
        person.age = personSurrogated.Age;  
        return person;  
    }  
    return obj;  
}  
```  
  
 <span data-ttu-id="1f94e-124">スキーマのインポート中に `PersonSurrogated` データ コントラクトを既存の `Person` クラスにマップするため、このサンプルでは <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> メソッドを実装しています。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-124">To map the `PersonSurrogated` data contract to the existing `Person` class during schema import, the sample implements the <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%28System.String%2CSystem.String%2CSystem.Object%29> method, as shown in the following sample code.</span></span>  
  
```csharp
public Type GetReferencedTypeOnImport(string typeName,
               string typeNamespace, object customData)  
{  
if (  
typeNamespace.Equals("http://schemas.datacontract.org/2004/07/DCSurrogateSample")  
)  
    {  
         if (typeName.Equals("PersonSurrogated"))  
        {  
             return typeof(Person);  
        }  
     }  
     return null;  
}  
```  
  
 <span data-ttu-id="1f94e-125"><xref:System.Runtime.Serialization.IDataContractSurrogate> インターフェイスの実装を完了するサンプル コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-125">The following sample code completes the implementation of the <xref:System.Runtime.Serialization.IDataContractSurrogate> interface.</span></span>  
  
```csharp
public System.CodeDom.CodeTypeDeclaration ProcessImportedType(  
          System.CodeDom.CodeTypeDeclaration typeDeclaration,
          System.CodeDom.CodeCompileUnit compileUnit)  
{  
    return typeDeclaration;  
}  
public object GetCustomDataToExport(Type clrType,
                               Type dataContractType)  
{  
    return null;  
}  
  
public object GetCustomDataToExport(  
System.Reflection.MemberInfo memberInfo, Type dataContractType)  
{  
    return null;  
}  
public void GetKnownCustomDataTypes(  
        KnownTypeCollection customDataTypes)  
{  
    // It does not matter what we do here.  
    throw new NotImplementedException();  
}  
```  
  
 <span data-ttu-id="1f94e-126">このサンプルでは、`AllowNonSerializableTypesAttribute` という属性により、ServiceModel でサロゲートが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1f94e-126">In this sample, the surrogate is enabled in ServiceModel by an attribute called `AllowNonSerializableTypesAttribute`.</span></span> <span data-ttu-id="1f94e-127">開発の際には、この属性をサービス コントラクトに適用する必要があります。上の `IPersonnelDataService` サービス コントラクトを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-127">Developers would need to apply this attribute on their service contract as shown on the `IPersonnelDataService` service contract above.</span></span> <span data-ttu-id="1f94e-128">この属性は `IContractBehavior` を実装し、`ApplyClientBehavior` メソッドと `ApplyDispatchBehavior` メソッドでの操作にサロゲートを設定します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-128">This attribute implements `IContractBehavior` and sets up the surrogate on operations in its `ApplyClientBehavior` and `ApplyDispatchBehavior` methods.</span></span>  
  
 <span data-ttu-id="1f94e-129">この場合、この属性は必要ありません。このサンプルでのデモンストレーション用にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-129">The attribute is not necessary in this case - it is used for demonstration purposes in this sample.</span></span> <span data-ttu-id="1f94e-130">これ以外の方法として、コードまたは構成を使用して同様の `IContractBehavior`、`IEndpointBehavior`、または `IOperationBehavior` を手動で追加することにより、サロゲートを有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-130">Users can alternatively enable a surrogate by manually adding a similar `IContractBehavior`, `IEndpointBehavior` or `IOperationBehavior` using code or using configuration.</span></span>  
  
 <span data-ttu-id="1f94e-131">`IContractBehavior` の実装は、操作に `DataContractSerializerOperationBehavior` が登録されているかどうかをチェックすることにより、DataContract を使用する操作を検索します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-131">The `IContractBehavior` implementation looks for operations that use DataContract by checking if they have a `DataContractSerializerOperationBehavior` registered.</span></span> <span data-ttu-id="1f94e-132">登録されている場合は、その動作に `DataContractSurrogate` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-132">If they do, it sets the `DataContractSurrogate` property on that behavior.</span></span> <span data-ttu-id="1f94e-133">この処理を行うサンプル コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-133">The following sample code shows how this is done.</span></span> <span data-ttu-id="1f94e-134">この操作にサロゲートが設定されると、シリアル化および逆シリアル化のために動作でサロゲートが有効化されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-134">Setting the surrogate on this operation behavior enables it for serialization and deserialization.</span></span>  
  
```csharp
public void ApplyClientBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime proxy)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
public void ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatch)  
{  
    foreach (OperationDescription opDesc in description.Operations)  
    {  
        ApplyDataContractSurrogate(opDesc);  
    }  
}  
  
private static void ApplyDataContractSurrogate(OperationDescription description)  
{  
    DataContractSerializerOperationBehavior dcsOperationBehavior = description.Behaviors.Find<DataContractSerializerOperationBehavior>();  
    if (dcsOperationBehavior != null)  
    {  
        if (dcsOperationBehavior.DataContractSurrogate == null)  
            dcsOperationBehavior.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
    }  
}  
```  
  
 <span data-ttu-id="1f94e-135">メタデータの生成中にサロゲートをプラグインとして使用するには、追加手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="1f94e-135">Additional steps need to be taken to plug in the surrogate for use during metadata generation.</span></span> <span data-ttu-id="1f94e-136">これを行うための機構として、このサンプルで示す `IWsdlExportExtension` が用意されています。</span><span class="sxs-lookup"><span data-stu-id="1f94e-136">One mechanism to do this is to provide an `IWsdlExportExtension` which is what this sample demonstrates.</span></span> <span data-ttu-id="1f94e-137">さらに、`WsdlExporter` を直接変更するという方法もあります。</span><span class="sxs-lookup"><span data-stu-id="1f94e-137">Another way is to modify the `WsdlExporter` directly.</span></span>  
  
 <span data-ttu-id="1f94e-138">`AllowNonSerializableTypesAttribute`属性は `IWsdlExportExtension` 、およびを実装し `IContractBehavior` ます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-138">The `AllowNonSerializableTypesAttribute` attribute implements `IWsdlExportExtension` and `IContractBehavior`.</span></span> <span data-ttu-id="1f94e-139">拡張機能には、またはのいずれかを指定でき `IContractBehavior` `IEndpointBehavior` ます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-139">The extension can be either an `IContractBehavior` or `IEndpointBehavior` in this case.</span></span> <span data-ttu-id="1f94e-140">`IWsdlExportExtension.ExportContract` メソッドの実装は、DataContract のスキーマ生成中に使用される`XsdDataContractExporter` にサロゲートを追加することによって、サロゲートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1f94e-140">Its `IWsdlExportExtension.ExportContract` method implementation enables the surrogate by adding it to the `XsdDataContractExporter` used during schema generation for DataContract.</span></span> <span data-ttu-id="1f94e-141">これを行う方法を次のコード スニペットに示します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-141">The following code snippet shows how to do this.</span></span>  
  
```csharp
public void ExportContract(WsdlExporter exporter, WsdlContractConversionContext context)  
{  
    if (exporter == null)  
        throw new ArgumentNullException("exporter");  
  
    object dataContractExporter;  
    XsdDataContractExporter xsdDCExporter;  
    if (!exporter.State.TryGetValue(typeof(XsdDataContractExporter), out dataContractExporter))  
    {  
        xsdDCExporter = new XsdDataContractExporter(exporter.GeneratedXmlSchemas);  
        exporter.State.Add(typeof(XsdDataContractExporter), xsdDCExporter);  
    }  
    else  
    {  
        xsdDCExporter = (XsdDataContractExporter)dataContractExporter;  
    }  
    if (xsdDCExporter.Options == null)  
        xsdDCExporter.Options = new ExportOptions();  
  
    if (xsdDCExporter.Options.DataContractSurrogate == null)  
        xsdDCExporter.Options.DataContractSurrogate = new AllowNonSerializableTypesSurrogate();  
}  
```  
  
 <span data-ttu-id="1f94e-142">サンプルを実行すると、クライアントは AddEmployee の呼び出しに続いて、最初の呼び出しが正常に行われたかどうかをチェックする GetEmployee を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-142">When you run the sample, the client calls AddEmployee followed by a GetEmployee call to check if the first call was successful.</span></span> <span data-ttu-id="1f94e-143">GetEmployee の操作要求の結果は、クライアント コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-143">The result of the GetEmployee operation request is displayed in the client console window.</span></span> <span data-ttu-id="1f94e-144">GetEmployee 操作では、従業員の検索と "found" の印刷を成功させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f94e-144">The GetEmployee operation must succeed in finding the employee and print "found".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f94e-145">このサンプルでは、シリアル化、逆シリアル化、およびメタデータの生成で、サロゲートをプラグインとして使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-145">This sample shows how to plug in a surrogate for serialize, deserialize and metadata generation.</span></span> <span data-ttu-id="1f94e-146">メタデータからコードを生成するためにサロゲートをプラグインとして使用する方法を示すものではありません。</span><span class="sxs-lookup"><span data-stu-id="1f94e-146">It does not show how to plug in a surrogate for code generation from metadata.</span></span> <span data-ttu-id="1f94e-147">サロゲートを使用してクライアントコード生成にプラグインする方法のサンプルについては、「 [カスタム WSDL 発行](custom-wsdl-publication.md) のサンプル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-147">To see a sample of how a surrogate can be used to plug into client code generation, see the [Custom WSDL Publication](custom-wsdl-publication.md) sample.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1f94e-148">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="1f94e-148">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1f94e-149">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f94e-149">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1f94e-150">ソリューションの C# エディションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1f94e-150">To build the C# edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1f94e-151">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1f94e-151">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1f94e-152">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1f94e-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1f94e-153">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="1f94e-154">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="1f94e-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f94e-155">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1f94e-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DataContract`  
