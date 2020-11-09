---
title: 属性を使用した XML シリアル化の制御
description: 属性を使用すると、オブジェクトの XML シリアル化を制御したり、同じ一連のクラスから代替 XML ストリームを作成したりできます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, serializing
- XML serialization, examples
- derived classes, serializing
- arrays, serializing
- XML serialization, attributes
- preventing serialization
- attributes [.NET], XML serialization
- serialization, examples
- serialization, attributes
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
ms.openlocfilehash: 36456d373b7482c4a4267b69e031c1e45baa9abb
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93281776"
---
# <a name="control-xml-serialization-using-attributes"></a><span data-ttu-id="8318f-103">属性を使用した XML シリアル化の制御</span><span class="sxs-lookup"><span data-stu-id="8318f-103">Control XML serialization using attributes</span></span>

<span data-ttu-id="8318f-104">属性を使用すると、オブジェクトの XML シリアル化を制御したり、同じ一連のクラスから代替 XML ストリームを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="8318f-104">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="8318f-105">代替 XML ストリームの作成の詳細については、「[方法: XML ストリームの代替要素名を指定する](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8318f-105">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8318f-106">生成される XML が、World Wide Web コンソーシアム (W3C) のドキュメント『[Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)』のセクション 5 に準拠している必要がある場合は、「[エンコード済み SOAP シリアル化を制御する属性](attributes-that-control-encoded-soap-serialization.md)」に記載されている属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="8318f-106">If the XML generated must conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use the attributes listed in [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>

<span data-ttu-id="8318f-107">既定では、クラス名またはメンバー名によって XML 要素名が決まります。</span><span class="sxs-lookup"><span data-stu-id="8318f-107">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="8318f-108">次の例に示すように、`Book` という名前の単純なクラスでは、`ISBN` という名前のフィールドから \<ISBN> という XML 要素タグが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-108">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>

```vb
Public Class Book
    Public ISBN As String
End Class
' When an instance of the Book class is serialized, it might
' produce this XML:
' <ISBN>1234567890</ISBN>.
```

```csharp
public class Book
{
    public string ISBN;
}
// When an instance of the Book class is serialized, it might
// produce this XML:
// <ISBN>1234567890</ISBN>.
```

<span data-ttu-id="8318f-109">この既定の動作を変更して、要素に新しい名前を付けることもできます。</span><span class="sxs-lookup"><span data-stu-id="8318f-109">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="8318f-110">次のコードでは、<xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> の <xref:System.Xml.Serialization.XmlElementAttribute> プロパティを設定することにより、属性でこの変更を実現する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8318f-110">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>

```vb
Public Class TaxRates
   < XmlElement(ElementName = "TaxRate")> _
    Public ReturnTaxRate As Decimal
End Class
```

```csharp
public class TaxRates {
    [XmlElement(ElementName = "TaxRate")]
    public decimal ReturnTaxRate;
}
```

<span data-ttu-id="8318f-111">属性の詳細については、「[属性](../attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8318f-111">For more information about attributes, see [Attributes](../attributes/index.md).</span></span> <span data-ttu-id="8318f-112">XML シリアル化を制御する属性の一覧については、「[Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md)」(XML シリアル化を制御する属性) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8318f-112">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md).</span></span>

## <a name="controlling-array-serialization"></a><span data-ttu-id="8318f-113">配列のシリアル化の制御</span><span class="sxs-lookup"><span data-stu-id="8318f-113">Controlling Array Serialization</span></span>

<span data-ttu-id="8318f-114"><xref:System.Xml.Serialization.XmlArrayAttribute> 属性および <xref:System.Xml.Serialization.XmlArrayItemAttribute> 属性は、配列のシリアル化を制御できるようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="8318f-114">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="8318f-115">この 2 つの属性を使用して、要素名、名前空間、および XML スキーマ (XSD) データ型 (World Wide Web コンソーシアム [www.w3.org] のドキュメント『XML Schema Part 2: Datatypes』で定義) を制御できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-115">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="8318f-116">また、配列に挿入できる型も指定できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-116">You can also specify the types that can be included in an array.</span></span>

<span data-ttu-id="8318f-117"><xref:System.Xml.Serialization.XmlArrayAttribute> は、配列をシリアル化すると生成される外側の XML 要素のプロパティを決定します。</span><span class="sxs-lookup"><span data-stu-id="8318f-117">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="8318f-118">たとえば、次に示す配列をシリアル化すると、既定で `Employees` という名前の XML 要素が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-118">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="8318f-119">この `Employees` 要素は、`Employee` 配列型に基づいた名前の一連の要素で構成されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-119">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>

```vb
Public Class Group
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
```

```csharp
public class Group {
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
```

<span data-ttu-id="8318f-120">シリアル化されたインスタンスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8318f-120">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

<span data-ttu-id="8318f-121"><xref:System.Xml.Serialization.XmlArrayAttribute> を適用すると、この XML 要素の名前を次のように変更できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-121">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>

```vb
Public Class Group
    <XmlArray("TeamMembers")> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlArray("TeamMembers")]
    public Employee[] Employees;
}
```

<span data-ttu-id="8318f-122">その結果、次のような XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-122">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<span data-ttu-id="8318f-123">一方、<xref:System.Xml.Serialization.XmlArrayItemAttribute> は、配列内の項目をシリアル化する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="8318f-123">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="8318f-124">この属性は、配列を返すフィールドに適用されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-124">Note that the attribute is applied to the field returning the array.</span></span>

```vb
Public Class Group
    <XmlArrayItem("MemberName")> _
    Public Employee() As Employees
End Class
```

```csharp
public class Group {
    [XmlArrayItem("MemberName")]
    public Employee[] Employees;
}
```

<span data-ttu-id="8318f-125">その結果、次のような XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-125">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a><span data-ttu-id="8318f-126">派生クラスのシリアル化</span><span class="sxs-lookup"><span data-stu-id="8318f-126">Serializing Derived Classes</span></span>

<span data-ttu-id="8318f-127"><xref:System.Xml.Serialization.XmlArrayItemAttribute> のもう 1 つの用途は、派生クラスをシリアル化することです。</span><span class="sxs-lookup"><span data-stu-id="8318f-127">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="8318f-128">たとえば、`Manager` から派生した `Employee` という名前の別のクラスを、前の例に追加できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-128">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="8318f-129"><xref:System.Xml.Serialization.XmlArrayItemAttribute> を適用しないと、この派生クラス型が認識されないため、実行時にコードが失敗します。</span><span class="sxs-lookup"><span data-stu-id="8318f-129">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="8318f-130">これを回避するには、この属性を 2 回適用し、受け入れ可能な各型 (基本型と派生型) の <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> プロパティをそれぞれ設定します。</span><span class="sxs-lookup"><span data-stu-id="8318f-130">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>

```vb
Public Class Group
    <XmlArrayItem(Type:=GetType(Employee)), _
    XmlArrayItem(Type:=GetType(Manager))> _
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
Public Class Manager
Inherits Employee
    Public Level As Integer
End Class
```

```csharp
public class Group {
    [XmlArrayItem(Type = typeof(Employee)),
    XmlArrayItem(Type = typeof(Manager))]
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
public class Manager:Employee {
    public int Level;
}
```

<span data-ttu-id="8318f-131">シリアル化されたインスタンスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8318f-131">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    </Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="8318f-132">要素のシーケンスとしての配列のシリアル化</span><span class="sxs-lookup"><span data-stu-id="8318f-132">Serializing an Array as a Sequence of Elements</span></span>

<span data-ttu-id="8318f-133">次の例に示すように、配列を返すフィールドに <xref:System.Xml.Serialization.XmlElementAttribute> を適用して、配列を XML 要素のフラットなシーケンスとしてシリアル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="8318f-133">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>

```vb
Public Class Group
    <XmlElement> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlElement]
    public Employee[] Employees;
}
```

<span data-ttu-id="8318f-134">シリアル化されたインスタンスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="8318f-134">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Name>Haley</Name>
</Employees>
<Employees>
    <Name>Noriko</Name>
</Employees>
<Employees>
    <Name>Marco</Name>
</Employees>
</Group>
```

<span data-ttu-id="8318f-135">2 つの XML ストリームを区別するもう 1 つの方法は、XML スキーマ定義ツールを使用して、コンパイル済みのコードから XML スキーマ (XSD) ドキュメント ファイルを生成することです</span><span class="sxs-lookup"><span data-stu-id="8318f-135">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="8318f-136">(ツールの使用の詳細については、「[The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md)」(XML スキーマ定義ツールと XML シリアル化) を参照してください)。フィールドに属性を適用しないと、スキーマには次のように要素が記述されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-136">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

<span data-ttu-id="8318f-137">フィールドに <xref:System.Xml.Serialization.XmlElementAttribute> を適用すると、生成されたスキーマには次のように要素が記述されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-137">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />
```

## <a name="serializing-an-arraylist"></a><span data-ttu-id="8318f-138">ArrayList のシリアル化</span><span class="sxs-lookup"><span data-stu-id="8318f-138">Serializing an ArrayList</span></span>

<span data-ttu-id="8318f-139"><xref:System.Collections.ArrayList> クラスには、さまざまなオブジェクトのコレクションを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="8318f-139">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="8318f-140">このため、<xref:System.Collections.ArrayList> は配列とほとんど同じように使用できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-140">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="8318f-141">型指定されたオブジェクトの配列を返すフィールドを作成する代わりに、単一の <xref:System.Collections.ArrayList> を返すフィールドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="8318f-141">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="8318f-142">ただし、配列の場合と同様に、<xref:System.Xml.Serialization.XmlSerializer> に含まれるオブジェクトの型を <xref:System.Collections.ArrayList> に通知する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8318f-142">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="8318f-143">そのためには、次の例に示すように、<xref:System.Xml.Serialization.XmlElementAttribute> の複数のインスタンスをフィールドに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="8318f-143">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>

```vb
Public Class Group
    <XmlElement(Type:=GetType(Employee)), _
    XmlElement(Type:=GetType(Manager))> _
    Public Info As ArrayList
End Class
```

```csharp
public class Group {
    [XmlElement(Type = typeof(Employee)),
    XmlElement(Type = typeof(Manager))]
    public ArrayList Info;
}
```

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="8318f-144">XmlRootAttribute と XmlTypeAttribute を使用したクラスのシリアル化の制御</span><span class="sxs-lookup"><span data-stu-id="8318f-144">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>

<span data-ttu-id="8318f-145">クラスのみに適用できる、<xref:System.Xml.Serialization.XmlRootAttribute> と <xref:System.Xml.Serialization.XmlTypeAttribute> という属性があります。</span><span class="sxs-lookup"><span data-stu-id="8318f-145">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="8318f-146">この 2 つの属性は非常に似ています。</span><span class="sxs-lookup"><span data-stu-id="8318f-146">These attributes are very similar.</span></span> <span data-ttu-id="8318f-147"><xref:System.Xml.Serialization.XmlRootAttribute> は、シリアル化されたときに XML ドキュメントの開始要素と終了要素、つまりルート要素を表す 1 つのクラスにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-147">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="8318f-148">一方 <xref:System.Xml.Serialization.XmlTypeAttribute> は、ルート クラスを含む任意のクラスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-148">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>

<span data-ttu-id="8318f-149">たとえば、前の例では、`Group` クラスがルート クラスであり、そのすべてのパブリック フィールドとパブリック プロパティは、XML ドキュメント内の XML 要素になります。</span><span class="sxs-lookup"><span data-stu-id="8318f-149">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="8318f-150">したがって、存在するルート クラスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="8318f-150">Therefore, there can be only one root class.</span></span> <span data-ttu-id="8318f-151"><xref:System.Xml.Serialization.XmlRootAttribute> を適用することで、<xref:System.Xml.Serialization.XmlSerializer> によって生成される XML ストリームを制御できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-151">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="8318f-152">たとえば、要素名や名前空間を変更できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-152">For example, you can change the element name and namespace.</span></span>

<span data-ttu-id="8318f-153"><xref:System.Xml.Serialization.XmlTypeAttribute> を使用すると、生成される XML のスキーマを制御できます。</span><span class="sxs-lookup"><span data-stu-id="8318f-153">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="8318f-154">この機能は、XML Web サービスを通じてスキーマを公開する必要がある場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8318f-154">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="8318f-155">次の例では、<xref:System.Xml.Serialization.XmlTypeAttribute> と <xref:System.Xml.Serialization.XmlRootAttribute> の両方を同じクラスに適用しています。</span><span class="sxs-lookup"><span data-stu-id="8318f-155">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>

```vb
<XmlRoot("NewGroupName"), _
XmlType("NewTypeName")> _
Public Class Group
    Public Employees() As Employee
End Class
```

```csharp
[XmlRoot("NewGroupName")]
[XmlType("NewTypeName")]
public class Group {
    public Employee[] Employees;
}
```

<span data-ttu-id="8318f-156">このクラスをコンパイルし、XML スキーマ定義ツールを使用してそのスキーマを生成すると、`Group` を記述する次の XML が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-156">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>

```xml
<xs:element name="NewGroupName" type="NewTypeName" />
```

<span data-ttu-id="8318f-157">これに対し、クラスのインスタンスをシリアル化した場合は、XML ドキュメントに `NewGroupName` のみが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8318f-157">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="8318f-158">XmlIgnoreAttribute によるシリアル化の回避</span><span class="sxs-lookup"><span data-stu-id="8318f-158">Preventing Serialization with the XmlIgnoreAttribute</span></span>

<span data-ttu-id="8318f-159">パブリック プロパティやパブリック フィールドをシリアル化する必要がない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8318f-159">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="8318f-160">たとえば、メタデータの格納に使用しているフィールドまたはプロパティの場合、</span><span class="sxs-lookup"><span data-stu-id="8318f-160">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="8318f-161"><xref:System.Xml.Serialization.XmlIgnoreAttribute> を適用すると、<xref:System.Xml.Serialization.XmlSerializer> がそのフィールドまたはプロパティをスキップします。</span><span class="sxs-lookup"><span data-stu-id="8318f-161">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>

## <a name="see-also"></a><span data-ttu-id="8318f-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="8318f-162">See also</span></span>

- [<span data-ttu-id="8318f-163">XML シリアル化を制御する属性</span><span class="sxs-lookup"><span data-stu-id="8318f-163">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="8318f-164">エンコード済み SOAP シリアル化を制御する属性</span><span class="sxs-lookup"><span data-stu-id="8318f-164">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="8318f-165">XML シリアル化の概要</span><span class="sxs-lookup"><span data-stu-id="8318f-165">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="8318f-166">XML シリアル化の例</span><span class="sxs-lookup"><span data-stu-id="8318f-166">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)
- [<span data-ttu-id="8318f-167">方法: XML ストリームの代替要素名を指定する</span><span class="sxs-lookup"><span data-stu-id="8318f-167">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="8318f-168">方法: オブジェクトをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="8318f-168">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="8318f-169">方法: オブジェクトを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="8318f-169">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
