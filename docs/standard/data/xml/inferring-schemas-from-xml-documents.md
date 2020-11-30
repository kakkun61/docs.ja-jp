---
title: XML ドキュメントからのスキーマの推論
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: f3d97d53-614d-4a04-a174-87965b7405f6
ms.openlocfilehash: 4540e1706cbd3dad9490f100d7e8fa58e80a9206
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733439"
---
# <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="a766f-102">XML ドキュメントからのスキーマの推論</span><span class="sxs-lookup"><span data-stu-id="a766f-102">Inferring Schemas from XML Documents</span></span>

<span data-ttu-id="a766f-103">このトピックでは、<xref:System.Xml.Schema.XmlSchemaInference> クラスを使用して、XML ドキュメントの構造から XML スキーマ定義言語 (XSD) スキーマを推論する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="a766f-103">This topic describes how to use the <xref:System.Xml.Schema.XmlSchemaInference> class to infer an XML Schema definition language (XSD) schema from the structure of an XML document.</span></span>  
  
## <a name="the-schema-inference-process"></a><span data-ttu-id="a766f-104">スキーマの推論プロセス</span><span class="sxs-lookup"><span data-stu-id="a766f-104">The Schema Inference Process</span></span>  

 <span data-ttu-id="a766f-105"><xref:System.Xml.Schema.XmlSchemaInference> 名前空間の <xref:System.Xml.Schema?displayProperty=nameWithType> クラスを使用して、XML ドキュメントの構造から 1 つ以上の XML スキーマ定義言語 (XSD) スキーマを生成できます。</span><span class="sxs-lookup"><span data-stu-id="a766f-105">The <xref:System.Xml.Schema.XmlSchemaInference> class of the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace is used to generate one or more XML Schema definition language (XSD) schemas from the structure of an XML document.</span></span> <span data-ttu-id="a766f-106">生成されるスキーマは、元の XML ドキュメントの検証に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a766f-106">The generated schemas may be used to validate the original XML document.</span></span>  
  
 <span data-ttu-id="a766f-107">XML ドキュメントは <xref:System.Xml.Schema.XmlSchemaInference> クラスによって処理されます。<xref:System.Xml.Schema.XmlSchemaInference> クラスは、XML ドキュメント上の要素と属性を定義するスキーマ コンポーネントに関する推測を行います。</span><span class="sxs-lookup"><span data-stu-id="a766f-107">As an XML document is processed by the <xref:System.Xml.Schema.XmlSchemaInference> class, the <xref:System.Xml.Schema.XmlSchemaInference> class makes assumptions about the schema components that describe the elements and attributes in the XML document.</span></span> <span data-ttu-id="a766f-108"><xref:System.Xml.Schema.XmlSchemaInference> クラスは、特定の要素または属性について最も限定的な型を推論することにより、制限された方法でスキーマ コンポーネントを推論します。</span><span class="sxs-lookup"><span data-stu-id="a766f-108">The <xref:System.Xml.Schema.XmlSchemaInference> class also infers schema components in a constrained way by inferring the most restrictive type for a particular element or attribute.</span></span> <span data-ttu-id="a766f-109">XML ドキュメントに関する情報の蓄積が進むほど、より限定度の低い型が推論されることで、制約が緩和されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-109">As more information about the XML document is gathered, these constraints are loosened by inferring less restrictive types.</span></span> <span data-ttu-id="a766f-110">最も限定度が低い推論可能な型は `xs:string` です。</span><span class="sxs-lookup"><span data-stu-id="a766f-110">The least restrictive type that can be inferred is `xs:string`.</span></span>  
  
 <span data-ttu-id="a766f-111">たとえば、次の XML ドキュメントを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="a766f-111">Take, for example, the following piece of an XML document.</span></span>  
  
```xml  
<parent attribute1="6">  
    <child>One</child>  
    <child>Two</child>  
</parent>  
<parent attribute1="A" />
```  
  
 <span data-ttu-id="a766f-112">上の例で `attribute1` 属性の値 `6` が <xref:System.Xml.Schema.XmlSchemaInference> プロセスによって検出されると、この属性は `xs:unsignedByte` 型であると想定されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-112">In the example above, when the `attribute1` attribute is encountered with a value of `6` by the <xref:System.Xml.Schema.XmlSchemaInference> process, it is assumed to be of type `xs:unsignedByte`.</span></span> <span data-ttu-id="a766f-113">2 番目の `parent` 要素が <xref:System.Xml.Schema.XmlSchemaInference> プロセスによって検出されると、`xs:string` 属性の値が `attribute1` であるため、型が `A` に変更され、制限が緩和されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-113">When the second `parent` element is encountered by the <xref:System.Xml.Schema.XmlSchemaInference> process, the constraint is loosened by modifying the type to `xs:string` because the value of the `attribute1` attribute is now `A`.</span></span> <span data-ttu-id="a766f-114">同様に、2 番目の親要素が子要素を持っていないため、スキーマで推論されるすべての `minOccurs` 要素の `child` 属性が `minOccurs="0"` に緩和されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-114">Similarly, the `minOccurs` attribute for all the `child` elements inferred in the schema are loosened to `minOccurs="0"` because the second parent element has no child elements.</span></span>  
  
## <a name="inferring-schemas-from-xml-documents"></a><span data-ttu-id="a766f-115">XML ドキュメントからのスキーマの推論</span><span class="sxs-lookup"><span data-stu-id="a766f-115">Inferring Schemas from XML Documents</span></span>  

 <span data-ttu-id="a766f-116"><xref:System.Xml.Schema.XmlSchemaInference> クラスでは、2 つのオーバーロードされた <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> メソッドを使用して XML ドキュメントからスキーマを推論します。</span><span class="sxs-lookup"><span data-stu-id="a766f-116">The <xref:System.Xml.Schema.XmlSchemaInference> class uses two overloaded <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A> methods to infer a schema from an XML document.</span></span>  
  
 <span data-ttu-id="a766f-117">最初の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> メソッドは、XML ドキュメントに基づくスキーマの作成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-117">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to create a schema based on an XML document.</span></span> <span data-ttu-id="a766f-118">2 番目の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> メソッドは、複数の XML ドキュメントを記述するスキーマの推論に使用されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-118">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method is used to infer a schema that describes multiple XML documents.</span></span> <span data-ttu-id="a766f-119">たとえば、複数の XML ドキュメントを 1 つずつ <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> メソッドに渡すことで、XML ドキュメントのセット全体を記述する 1 つのスキーマを生成できます。</span><span class="sxs-lookup"><span data-stu-id="a766f-119">For example, you can feed multiple XML documents to the <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method one at a time to produce a schema that describes the entire set of XML documents.</span></span>  
  
 <span data-ttu-id="a766f-120">最初の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> メソッドは、<xref:System.Xml.XmlReader> オブジェクトに含まれている XML ドキュメントからスキーマを推論し、推論されたスキーマが含まれる <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="a766f-120">The first <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method infers a schema from an XML document contained in an <xref:System.Xml.XmlReader> object, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span> <span data-ttu-id="a766f-121">2 番目の <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> メソッドは、<xref:System.Xml.Schema.XmlSchemaSet> オブジェクトを対象として、<xref:System.Xml.XmlReader> オブジェクトに含まれている XML ドキュメントと同じ対象の名前空間を持つスキーマを検索し、既存のスキーマを限定し、推論されたスキーマが含まれる <xref:System.Xml.Schema.XmlSchemaSet> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="a766f-121">The second <xref:System.Xml.Schema.XmlSchemaInference.InferSchema%2A?displayProperty=nameWithType> method searches an <xref:System.Xml.Schema.XmlSchemaSet> object for a schema with the same target namespace as the XML document contained in the <xref:System.Xml.XmlReader> object, refines the existing schema, and returns an <xref:System.Xml.Schema.XmlSchemaSet> object containing the inferred schema.</span></span>  
  
 <span data-ttu-id="a766f-122">限定されたスキーマに加えられた変更は、XML ドキュメントで検出された新しい構造に基づいています。</span><span class="sxs-lookup"><span data-stu-id="a766f-122">The changes made to the refined schema are based on new structure found in the XML document.</span></span> <span data-ttu-id="a766f-123">たとえば、XML ドキュメントが詳細に検討されるときは、検出されるデータ型が想定され、その想定に基づいてスキーマが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-123">For example, as an XML document is traversed, assumptions are made about the data types found, and the schema is created based on those assumptions.</span></span> <span data-ttu-id="a766f-124">しかし、2 回目の推論で検出されたデータが最初の想定と異なっている場合は、スキーマが限定されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-124">However, if data is encountered on a second inference pass that differs from the original assumption, the schema is refined.</span></span> <span data-ttu-id="a766f-125">次の例は限定のプロセスを示しています。</span><span class="sxs-lookup"><span data-stu-id="a766f-125">The following example illustrates the refinement process.</span></span>  
  
 [!code-cpp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaInferenceExamples/CPP/XmlSchemaInferenceExamples.cpp#4)]
 [!code-csharp[XmlSchemaInferenceExamples#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaInferenceExamples/CS/XmlSchemaInferenceExamples.cs#4)]
 [!code-vb[XmlSchemaInferenceExamples#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaInferenceExamples/VB/XmlSchemaInferenceExamples.vb#4)]  
  
 <span data-ttu-id="a766f-126">この例では、次に示す `item1.xml` というファイルを最初の入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a766f-126">The example takes the following file, `item1.xml`, as its first input.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#13](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item1.xml#13)]  
  
 <span data-ttu-id="a766f-127">この例では、さらに `item2.xml` というファイルを 2 番目の入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a766f-127">The example then takes the `item2.xml` file as its second input:</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#14](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/item2.xml#14)]  
  
 <span data-ttu-id="a766f-128">最初の XML ドキュメントで `productID` 属性が検出されると、値 `123456789` は `xs:unsignedInt` 型であると想定されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-128">When the `productID` attribute is encountered in the first XML document, the value of `123456789` is assumed to be an `xs:unsignedInt` type.</span></span> <span data-ttu-id="a766f-129">しかし、2 番目の XML ドキュメントが読み取られ、値 `A53-246` が検出されると、`xs:unsignedInt` 型だとは想定できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a766f-129">However, when the second XML document is read and the value of `A53-246` is found, the `xs:unsignedInt` type can no longer be assumed.</span></span> <span data-ttu-id="a766f-130">そこで、スキーマは限定され、`productID` の型が `xs:string` に変更されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-130">The schema is refined and the type of `productID` is changed to `xs:string`.</span></span> <span data-ttu-id="a766f-131">さらに、2 番目の XML ドキュメントに `minOccurs` 要素が含まれていないため、`supplierID` 要素の `0` 属性が `supplierID` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a766f-131">In addition, the `minOccurs` attribute for the `supplierID` element is set to `0`, because the second XML document contains no `supplierID` element.</span></span>  
  
 <span data-ttu-id="a766f-132">次に示すのは、最初の XML ドキュメントから推論されたスキーマです。</span><span class="sxs-lookup"><span data-stu-id="a766f-132">The following is the schema inferred from the first XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#15](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema1.xml#15)]  
  
 <span data-ttu-id="a766f-133">次に示すのは、最初の XML ドキュメントから推論され、2 番目の XML ドキュメントによって限定されたスキーマです。</span><span class="sxs-lookup"><span data-stu-id="a766f-133">The following is the schema inferred from the first XML document, refined by the second XML document.</span></span>  
  
 [!code-xml[XmlSchemaInferenceExamples#16](../../../../samples/snippets/xml/VS_Snippets_Data/XmlSchemaInferenceExamples/XML/InferSchema2.xml#16)]  
  
## <a name="inline-schemas"></a><span data-ttu-id="a766f-134">インライン スキーマ</span><span class="sxs-lookup"><span data-stu-id="a766f-134">Inline Schemas</span></span>  

 <span data-ttu-id="a766f-135"><xref:System.Xml.Schema.XmlSchemaInference> プロセスの実行中にインライン XML スキーマ定義言語 (XSD) スキーマが検出されると、<xref:System.Xml.Schema.XmlSchemaInferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a766f-135">If an inline XML Schema definition language (XSD) schema is encountered during the <xref:System.Xml.Schema.XmlSchemaInference> process, an <xref:System.Xml.Schema.XmlSchemaInferenceException> is thrown.</span></span> <span data-ttu-id="a766f-136">たとえば、次のインライン スキーマが検出されると、<xref:System.Xml.Schema.XmlSchemaInferenceException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="a766f-136">For example, the following inline schema throws an <xref:System.Xml.Schema.XmlSchemaInferenceException>.</span></span>  
  
```xml  
<root xmlns:ex="http://www.contoso.com" xmlns="http://www.tempuri.org">  
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.contoso.com">  
        <xs:element name="Contoso" type="xs:normalizedString" />  
    </xs:schema>  
    <ex:Contoso>Test</ex:Contoso>  
</root>  
```  
  
## <a name="schemas-that-cannot-be-refined"></a><span data-ttu-id="a766f-137">限定できないスキーマ</span><span class="sxs-lookup"><span data-stu-id="a766f-137">Schemas that Cannot be Refined</span></span>  

 <span data-ttu-id="a766f-138">限定を目的として型を渡されたときに、XML スキーマ定義言語 (XSD) スキーマの <xref:System.Xml.Schema.XmlSchemaInference> プロセスが処理できず、例外をスローする W3C XML スキーマ構造があります。</span><span class="sxs-lookup"><span data-stu-id="a766f-138">There are W3C XML Schema constructs that the XML Schema definition language (XSD) schema <xref:System.Xml.Schema.XmlSchemaInference> process cannot handle if given a type to refine and cause an exception to be thrown.</span></span> <span data-ttu-id="a766f-139">最上位のコンポジターがシーケンス以外のものである複合型がその例です。</span><span class="sxs-lookup"><span data-stu-id="a766f-139">Such as a complex type whose top-level compositor is anything other than a sequence.</span></span> <span data-ttu-id="a766f-140">スキーマ オブジェクト モデル (SOM) では、<xref:System.Xml.Schema.XmlSchemaComplexType> プロパティが <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> のインスタンスでない <xref:System.Xml.Schema.XmlSchemaSequence> がそれに相当します。</span><span class="sxs-lookup"><span data-stu-id="a766f-140">In the Schema Object Model (SOM), this corresponds to an <xref:System.Xml.Schema.XmlSchemaComplexType> whose <xref:System.Xml.Schema.XmlSchemaComplexType.Particle%2A> property is not an instance of <xref:System.Xml.Schema.XmlSchemaSequence>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a766f-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="a766f-141">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaInference>
- [<span data-ttu-id="a766f-142">XML スキーマ オブジェクト モデル (SOM)</span><span class="sxs-lookup"><span data-stu-id="a766f-142">XML Schema Object Model (SOM)</span></span>](xml-schema-object-model-som.md)
- [<span data-ttu-id="a766f-143">XML スキーマの推論</span><span class="sxs-lookup"><span data-stu-id="a766f-143">Inferring an XML Schema</span></span>](inferring-an-xml-schema.md)
- [<span data-ttu-id="a766f-144">スキーマのノード型および構造を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="a766f-144">Rules for Inferring Schema Node Types and Structure</span></span>](rules-for-inferring-schema-node-types-and-structure.md)
- [<span data-ttu-id="a766f-145">単純型を推論するときの規則</span><span class="sxs-lookup"><span data-stu-id="a766f-145">Rules for Inferring Simple Types</span></span>](rules-for-inferring-simple-types.md)
