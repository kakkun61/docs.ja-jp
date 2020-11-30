---
title: XML スキーマのインクルードまたはインポート
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fe1b4a11-37f4-4e1a-93c9-239f4fe736c0
ms.openlocfilehash: b2feb14e304c8ba7ecc19b2e79b943204044da05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722675"
---
# <a name="including-or-importing-xml-schemas"></a><span data-ttu-id="a22bb-102">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="a22bb-102">Including or Importing XML Schemas</span></span>

<span data-ttu-id="a22bb-103">XML スキーマには、`<xs:import />` 要素、`<xs:include />` 要素、および `<xs:redefine />` 要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a22bb-103">An XML schema may contain `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements.</span></span> <span data-ttu-id="a22bb-104">これらのスキーマ要素は、インクルードまたはインポートするスキーマの構造を補足するために使用できる他の XML スキーマを参照します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-104">These schema elements refer to other XML schemas that can be used to supplement the structure of the schema that includes or imports them.</span></span> <span data-ttu-id="a22bb-105"><xref:System.Xml.Schema.XmlSchemaImport> クラス、<xref:System.Xml.Schema.XmlSchemaInclude> クラス、および <xref:System.Xml.Schema.XmlSchemaRedefine> クラスは、スキーマ オブジェクト モデル (SOM) API でこれらの要素にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a22bb-105">The <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, map to these elements in the Schema Object Model (SOM) API.</span></span>  
  
## <a name="including-or-importing-an-xml-schema"></a><span data-ttu-id="a22bb-106">XML スキーマのインクルードまたはインポート</span><span class="sxs-lookup"><span data-stu-id="a22bb-106">Including or Importing an XML Schema</span></span>  

 <span data-ttu-id="a22bb-107">次のコード サンプルは、アドレス スキーマを使用して「[XML スキーマの作成](building-xml-schemas.md)」で作成したカスタム スキーマを補足します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-107">The following code example supplements the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic with the address schema.</span></span> <span data-ttu-id="a22bb-108">アドレス スキーマを使用してカスタム スキーマを補足すると、カスタム スキーマでアドレス型が使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a22bb-108">Supplementing the customer schema with the address schema makes address types available in the customer schema.</span></span>  
  
 <span data-ttu-id="a22bb-109">アドレス スキーマを統合するには、`<xs:include />` 要素または `<xs:import />` 要素を使用して、アドレス スキーマのコンポーネントをそのまま使用するか、または `<xs:redefine />` 要素を使用して、カスタム スキーマのニーズに合わせてコンポーネントを変更します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-109">The address schema can be incorporated using either `<xs:include />` or `<xs:import />` elements to use the components of the address schema as-is, or using an `<xs:redefine />` element to modify any of its components to suit the need of the customer schema.</span></span> <span data-ttu-id="a22bb-110">アドレス スキーマの `targetNamespace` はカスタム スキーマのものとは異なっているため、`<xs:import />` 要素 (インポートのセマンティクス) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="a22bb-110">Because the address schema has a `targetNamespace` that is different from that of the customer schema, the `<xs:import />` element and therefore import semantics is used.</span></span>  
  
 <span data-ttu-id="a22bb-111">このコード サンプルでは、アドレス スキーマのインクルードを次の手順で行います。</span><span class="sxs-lookup"><span data-stu-id="a22bb-111">The code example includes the address schema in the following steps.</span></span>  
  
1. <span data-ttu-id="a22bb-112">カスタム スキーマとアドレス スキーマを新しい <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトに追加し、コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="a22bb-112">Adds the customer schema and the address schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles them.</span></span> <span data-ttu-id="a22bb-113">スキーマの読み込みまたはコンパイル時に発生するスキーマ検証に関する警告とエラーは、<xref:System.Xml.Schema.ValidationEventHandler> デリゲートによって処理されます。</span><span class="sxs-lookup"><span data-stu-id="a22bb-113">Any schema validation warnings and errors encountered reading or compiling the schemas are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2. <span data-ttu-id="a22bb-114"><xref:System.Xml.Schema.XmlSchema> プロパティを反復処理して、<xref:System.Xml.Schema.XmlSchemaSet> からカスタム スキーマとアドレス スキーマの両方に対するコンパイルされた <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-114">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> objects for both the customer and address schemas from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="a22bb-115">これらのスキーマはコンパイルされているため、スキーマのコンパイル後の情報セット (PSCI) プロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a22bb-115">Because the schemas are compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3. <span data-ttu-id="a22bb-116"><xref:System.Xml.Schema.XmlSchemaImport> オブジェクトを作成し、インポートの <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> プロパティをアドレス スキーマの名前空間に設定し、インポートの <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> プロパティをアドレス スキーマの <xref:System.Xml.Schema.XmlSchema> オブジェクトに設定して、カスタム スキーマの <xref:System.Xml.Schema.XmlSchema.Includes%2A> プロパティにインポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-116">Creates an <xref:System.Xml.Schema.XmlSchemaImport> object, sets the <xref:System.Xml.Schema.XmlSchemaImport.Namespace%2A> property of the import to the namespace of the address schema, sets the <xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A> property of the import to the <xref:System.Xml.Schema.XmlSchema> object of the address schema, and adds the import to the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span>  
  
4. <span data-ttu-id="a22bb-117"><xref:System.Xml.Schema.XmlSchema> クラスの <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> メソッドおよび <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> メソッドを使用して、カスタム スキーマの変更された <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトの再処理とコンパイルを行って、コンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-117">Reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object of the customer schema using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
5. <span data-ttu-id="a22bb-118">最後に、カスタム スキーマの <xref:System.Xml.Schema.XmlSchema.Includes%2A> プロパティを使用して、カスタム スキーマにインポートされたすべてのスキーマを再帰的にコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-118">Finally, recursively writes all of the schemas imported into the customer schema to the console using the <xref:System.Xml.Schema.XmlSchema.Includes%2A> property of the customer schema.</span></span> <span data-ttu-id="a22bb-119"><xref:System.Xml.Schema.XmlSchema.Includes%2A> プロパティを使用すると、スキーマに追加されたすべてのインクルード、インポート、および再定義にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a22bb-119">The <xref:System.Xml.Schema.XmlSchema.Includes%2A> property provides access to all the includes, imports, or redefines added to a schema.</span></span>  
  
 <span data-ttu-id="a22bb-120">以下に、完全なコード サンプルおよびコンソールに出力されるカスタム スキーマとアドレス スキーマを示します。</span><span class="sxs-lookup"><span data-stu-id="a22bb-120">The following is the complete code example and the customer and address schemas written to the console.</span></span>  
  
 [!code-cpp[XmlSchemaImportExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaImportExample/CPP/XmlSchemaImportExample.cpp#1)]
 [!code-csharp[XmlSchemaImportExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaImportExample/CS/XmlSchemaImportExample.cs#1)]
 [!code-vb[XmlSchemaImportExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaImportExample/VB/XmlSchemaImportExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:import namespace="http://www.example.com/IPO" />  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
<schema targetNamespace="http://www.example.com/IPO" xmlns="http://www.w3.org/2001/XMLSchema" xmlns:ipo="http://www.example.com/IPO">  
  <annotation>  
    <documentation xml:lang="en">  
      Addresses for International Purchase order schema  
      Copyright 2000 Example.com. All rights reserved.  
    </documentation>  
  </annotation>  
  <complexType name="Address">  
    <sequence>  
      <element name="name"   type="string"/>  
      <element name="street" type="string"/>  
      <element name="city"   type="string"/>  
    </sequence>  
  </complexType>  
  <complexType name="USAddress">  
    <complexContent>  
      <extension base="ipo:Address">  
        <sequence>  
          <element name="state" type="ipo:USState"/>  
          <element name="zip"   type="positiveInteger"/>  
        </sequence>  
      </extension>  
    </complexContent>  
  </complexType>  
  <!-- other Address derivations for more countries or regions -->  
  <simpleType name="USState">  
    <restriction base="string">  
      <enumeration value="AK"/>  
      <enumeration value="AL"/>  
      <enumeration value="AR"/>  
      <!-- and so on ... -->  
    </restriction>  
  </simpleType>  
</schema>  
```  
  
 <span data-ttu-id="a22bb-121">`<xs:import />` 要素、`<xs:include />` 要素、`<xs:redefine />` 要素、<xref:System.Xml.Schema.XmlSchemaImport> クラス、<xref:System.Xml.Schema.XmlSchemaInclude> クラス、<xref:System.Xml.Schema.XmlSchemaRedefine> クラスの詳細については、[W3C XML スキーマ](https://www.w3.org/XML/Schema)および <xref:System.Xml.Schema?displayProperty=nameWithType> 名前空間クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a22bb-121">For more information about the `<xs:import />`, `<xs:include />`, and `<xs:redefine />` elements and the <xref:System.Xml.Schema.XmlSchemaImport>, <xref:System.Xml.Schema.XmlSchemaInclude> and <xref:System.Xml.Schema.XmlSchemaRedefine> classes, see the [W3C XML Schema](https://www.w3.org/XML/Schema) and the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace class reference documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a22bb-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="a22bb-122">See also</span></span>

- [<span data-ttu-id="a22bb-123">XML スキーマ オブジェクト モデルの概要</span><span class="sxs-lookup"><span data-stu-id="a22bb-123">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="a22bb-124">XML スキーマの読み取りと書き込み</span><span class="sxs-lookup"><span data-stu-id="a22bb-124">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="a22bb-125">XML スキーマの作成</span><span class="sxs-lookup"><span data-stu-id="a22bb-125">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="a22bb-126">XML スキーマの走査</span><span class="sxs-lookup"><span data-stu-id="a22bb-126">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="a22bb-127">XML スキーマの編集</span><span class="sxs-lookup"><span data-stu-id="a22bb-127">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="a22bb-128">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="a22bb-128">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
