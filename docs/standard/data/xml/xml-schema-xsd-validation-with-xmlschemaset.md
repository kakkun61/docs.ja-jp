---
title: XmlSchemaSet による XML スキーマ (XSD) 検証
description: .NET で XmlSchemaSet クラスを使用して、XML スキーマ定義言語 (XSD) スキーマに対して XML ドキュメントを検証する方法について学習します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
ms.openlocfilehash: 9e1d4b7e8c805436c32d2ae7b340ee251741f4a1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824572"
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="06c98-103">XmlSchemaSet による XML スキーマ (XSD) 検証</span><span class="sxs-lookup"><span data-stu-id="06c98-103">XML schema (XSD) validation with XmlSchemaSet</span></span>

<span data-ttu-id="06c98-104">XML ドキュメントは、<xref:System.Xml.Schema.XmlSchemaSet> の XML スキーマ定義言語 (XSD) スキーマを基準として検証できます。</span><span class="sxs-lookup"><span data-stu-id="06c98-104">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validate-xml-documents"></a><span data-ttu-id="06c98-105">XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="06c98-105">Validate XML documents</span></span>  
 <span data-ttu-id="06c98-106">XML ドキュメントは、<xref:System.Xml.XmlReader.Create%2A> クラスの <xref:System.Xml.XmlReader> メソッドを使用して検証します。</span><span class="sxs-lookup"><span data-stu-id="06c98-106">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="06c98-107">XML ドキュメントを検証するには、XML ドキュメントの検証に使用する XML スキーマ定義言語 (XSD) スキーマを持つ <xref:System.Xml.XmlReaderSettings> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="06c98-107">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06c98-108"><xref:System.Xml.Schema> 名前空間には、[LINQ to XML (C#)](../../linq/linq-xml-overview.md) や [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md) を使用しているときに XSD ファイルに対する XML ツリーの検証を容易にする拡張メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="06c98-108">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span> <span data-ttu-id="06c98-109">LINQ to XML を使用した XML ドキュメントの検証に関する詳細については、「[XSD を使用して検証する方法 (LINQ to XML) (C#)](../../linq/validate-xsd.md)」および「[方法: XSD を使用して検証する (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06c98-109">For more information on validating XML documents with LINQ to XML, see [How to validate using XSD (LINQ to XML) (C#)](../../linq/validate-xsd.md) and [How to: Validate Using XSD (LINQ to XML) (Visual Basic)](../../linq/validate-xsd.md).</span></span>
  
 <span data-ttu-id="06c98-110">独立したスキーマまたはスキーマのセット (<xref:System.Xml.Schema.XmlSchemaSet> を使用) を <xref:System.Xml.Schema.XmlSchemaSet> に追加するには、そのどちらかを <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> の <xref:System.Xml.Schema.XmlSchemaSet> メソッドにパラメーターとして渡します。</span><span class="sxs-lookup"><span data-stu-id="06c98-110">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="06c98-111">ドキュメントを検証する際には、ドキュメントの対象名前空間がスキーマ セット内のスキーマの対象名前空間と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="06c98-111">When validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="06c98-112">XML ドキュメントのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="06c98-112">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="06c98-113">XML ドキュメントのサンプルを検証するスキーマを次に示します。</span><span class="sxs-lookup"><span data-stu-id="06c98-113">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples #6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="06c98-114">以下のコード サンプルでは、<xref:System.Xml.XmlReaderSettings> オブジェクトの <xref:System.Xml.XmlReaderSettings.Schemas%2A> プロパティに上記のスキーマが追加されます。</span><span class="sxs-lookup"><span data-stu-id="06c98-114">In the code example that follows, the schema above is added to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="06c98-115"><xref:System.Xml.XmlReaderSettings> オブジェクトは、上記の XML ドキュメントを検証する <xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドにパラメーターとして渡されます。</span><span class="sxs-lookup"><span data-stu-id="06c98-115">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="06c98-116"><xref:System.Xml.XmlReaderSettings.ValidationType%2A> オブジェクトの <xref:System.Xml.XmlReaderSettings> プロパティが `Schema` に設定されて、<xref:System.Xml.XmlReader.Create%2A> オブジェクトの <xref:System.Xml.XmlReader> メソッドによる XML ドキュメントの検証が行われます。</span><span class="sxs-lookup"><span data-stu-id="06c98-116">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="06c98-117">XML のドキュメントおよびスキーマの検証中に発見されたエラーによって発生する <xref:System.Xml.Schema.ValidationEventHandler> イベントまたは <xref:System.Xml.XmlReaderSettings> イベントを処理するために、<xref:System.Xml.Schema.XmlSeverityType.Warning> オブジェクトに <xref:System.Xml.Schema.XmlSeverityType.Error> を追加します。</span><span class="sxs-lookup"><span data-stu-id="06c98-117">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example #1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example #1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="06c98-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="06c98-118">See also</span></span>

- [<span data-ttu-id="06c98-119">スキーマをコンパイルするための XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="06c98-119">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="06c98-120">XML スキーマの使用</span><span class="sxs-lookup"><span data-stu-id="06c98-120">Working with XML Schemas</span></span>](working-with-xml-schemas.md)
