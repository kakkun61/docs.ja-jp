---
title: DOM における XML ドキュメントの検証
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: db3748d1d0e1a5687219d5b07d1261639a4ef670
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819293"
---
# <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="c8577-102">DOM における XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="c8577-102">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="c8577-103"><xref:System.Xml.XmlDocument> クラスでは、既定で、ドキュメント オブジェクト モデル (DOM) 内の XML ドキュメントは、XML スキーマ定義言語 (XSD) スキーマまたはドキュメント型定義 (DTD) に対して検証されません。XML が整形式であることだけが検証されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-103">The<xref:System.Xml.XmlDocument> class does not validate the XML in the Document Object Model (DOM) against an XML Schema definition language (XSD) schema or document type definition (DTD) by default; the XML is only verified to be well-formed.</span></span>

<span data-ttu-id="c8577-104">DOM 内の XML を検証するには、スキーマ検証型 <xref:System.Xml.XmlReader> を <xref:System.Xml.XmlDocument.Load%2A> クラスの <xref:System.Xml.XmlDocument> メソッドに渡して、DOM への読み込み時に XML を検証するか、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドを使用して、まだ未検証の DOM 内の XML ドキュメントを検証することができます。</span><span class="sxs-lookup"><span data-stu-id="c8577-104">To validate the XML in the DOM, you can validate the XML as it is loaded into the DOM by passing a schema-validating <xref:System.Xml.XmlReader> to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class, or validate a previously unvalidated XML document in the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a><span data-ttu-id="c8577-105">DOM への読み込み時の XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="c8577-105">Validating an XML Document As It Is Loaded into the DOM</span></span>

<span data-ttu-id="c8577-106">検証型 <xref:System.Xml.XmlDocument> が <xref:System.Xml.XmlReader> クラスの <xref:System.Xml.XmlDocument.Load%2A> メソッドに渡されると、<xref:System.Xml.XmlDocument> クラスは DOM への読み込み時に XML データを検証します。</span><span class="sxs-lookup"><span data-stu-id="c8577-106">The <xref:System.Xml.XmlDocument> class validates the XML data as it is loaded into the DOM when a validating <xref:System.Xml.XmlReader> is passed to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

<span data-ttu-id="c8577-107">検証が正常に終了すると、スキーマの既定値が適用され、必要に応じてテキスト値がアトミック値に変換され、型情報が検証済みの情報項目に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="c8577-107">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="c8577-108">その結果、以前の型指定されていない XML データは、型指定された XML データに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="c8577-108">As a result, typed XML data replaces previously untyped XML data.</span></span>

### <a name="creating-an-xml-schema-validating-xmlreader"></a><span data-ttu-id="c8577-109">XML スキーマ検証型 XmlReader の作成</span><span class="sxs-lookup"><span data-stu-id="c8577-109">Creating an XML Schema-Validating XmlReader</span></span>

<span data-ttu-id="c8577-110">XML スキーマ検証型 <xref:System.Xml.XmlReader> を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c8577-110">To create an XML schema-validating <xref:System.Xml.XmlReader>, follow these steps.</span></span>

1. <span data-ttu-id="c8577-111">新しい <xref:System.Xml.XmlReaderSettings> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8577-111">Construct a new <xref:System.Xml.XmlReaderSettings> instance.</span></span>

2. <span data-ttu-id="c8577-112">XML スキーマを <xref:System.Xml.XmlReaderSettings.Schemas%2A> インスタンスの <xref:System.Xml.XmlReaderSettings> プロパティに追加します。</span><span class="sxs-lookup"><span data-stu-id="c8577-112">Add an XML schema to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> instance.</span></span>

3. <span data-ttu-id="c8577-113">`Schema` を <xref:System.Xml.XmlReaderSettings.ValidationType%2A> として指定します。</span><span class="sxs-lookup"><span data-stu-id="c8577-113">Specify `Schema` as the <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.</span></span>

4. <span data-ttu-id="c8577-114">オプションとして、検証中に検出したスキーマ検証エラーおよび警告を処理する <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> と <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> を指定します。</span><span class="sxs-lookup"><span data-stu-id="c8577-114">Optionally specify <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> and a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> to handle schema validation errors and warnings encountered during validation.</span></span>

5. <span data-ttu-id="c8577-115">最後に、<xref:System.Xml.XmlReaderSettings> オブジェクトを、スキーマ検証型 <xref:System.Xml.XmlReader.Create%2A> を作成する <xref:System.Xml.XmlReader> クラスの <xref:System.Xml.XmlReader> メソッドに、XML ドキュメントと共に渡します。</span><span class="sxs-lookup"><span data-stu-id="c8577-115">Finally, pass the <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class along with the XML document, creating a schema-validating <xref:System.Xml.XmlReader>.</span></span>

### <a name="example"></a><span data-ttu-id="c8577-116">例</span><span class="sxs-lookup"><span data-stu-id="c8577-116">Example</span></span>

<span data-ttu-id="c8577-117">次のコード サンプルでは、スキーマ検証型 <xref:System.Xml.XmlReader> が DOM に読み込まれた XML データを検証します。</span><span class="sxs-lookup"><span data-stu-id="c8577-117">In the code example that follows, a schema-validating <xref:System.Xml.XmlReader> validates the XML data loaded into the DOM.</span></span> <span data-ttu-id="c8577-118">無効な変更を加えられた後、XML ドキュメントが再検証され、スキーマ検証エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c8577-118">Invalid modifications are made to the XML document and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="c8577-119">最後に、エラーの 1 つが修正された後、XML ドキュメントの一部が部分的に検証されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-119">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="c8577-120">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="c8577-120">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="c8577-121">また、`contosoBooks.xsd` ファイルも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="c8577-121">The example also takes the `contosoBooks.xsd` file as input.</span></span>

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

<span data-ttu-id="c8577-122">DOM への読み込み時に XML データを検証する場合は、以下を検討します。</span><span class="sxs-lookup"><span data-stu-id="c8577-122">Consider the following when validating XML data as it is loaded into the DOM.</span></span>

- <span data-ttu-id="c8577-123">上の例では、無効な型が見つかるたびに <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-123">In the above example, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is called whenever an invalid type is encountered.</span></span> <span data-ttu-id="c8577-124">検証を行う <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> で <xref:System.Xml.XmlReader> を設定しなかった場合は、<xref:System.Xml.Schema.XmlSchemaValidationException> を呼び出したときに属性や要素の型が検証スキーマで指定されている型と一致しないと、<xref:System.Xml.XmlDocument.Load%2A> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c8577-124">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is not set on the validating <xref:System.Xml.XmlReader>,an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span>

- <span data-ttu-id="c8577-125">XML ドキュメントが既定値を定義した関連付けられたスキーマと共に <xref:System.Xml.XmlDocument> オブジェクトに読み込まれる場合、<xref:System.Xml.XmlDocument> は、これらの既定値があたかも XML ドキュメント内にあるかのように扱います。</span><span class="sxs-lookup"><span data-stu-id="c8577-125">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="c8577-126">これは、スキーマから既定値を得た要素に対して <xref:System.Xml.XmlReader.IsEmptyElement%2A> プロパティは常に `false` を返すことを意味します。</span><span class="sxs-lookup"><span data-stu-id="c8577-126">This means that the <xref:System.Xml.XmlReader.IsEmptyElement%2A> property always returns `false` for an element that was defaulted from the schema.</span></span> <span data-ttu-id="c8577-127">XML ドキュメント内で空要素として書かれている場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="c8577-127">Even if in the XML document, it was written as an empty element.</span></span>

## <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="c8577-128">DOM における XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="c8577-128">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="c8577-129"><xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドは、DOM に読み込まれた XML データを <xref:System.Xml.XmlDocument> オブジェクトの <xref:System.Xml.XmlDocument.Schemas%2A> プロパティに対して検証します。</span><span class="sxs-lookup"><span data-stu-id="c8577-129">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML data loaded in the DOM against the schemas in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span> <span data-ttu-id="c8577-130">検証が正常に終了すると、スキーマの既定値が適用され、必要に応じてテキスト値がアトミック値に変換され、型情報が検証済みの情報項目に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="c8577-130">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="c8577-131">その結果、以前の型指定されていない XML データは、型指定された XML データに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="c8577-131">As a result, typed XML data replaces previously untyped XML data.</span></span>

<span data-ttu-id="c8577-132">以下の例は、上記の「DOM への読み込み時の XML ドキュメントの検証」の例に似ています。</span><span class="sxs-lookup"><span data-stu-id="c8577-132">The example below is similar to the example in "Validating an XML Document As It Is Loaded into the DOM" above.</span></span> <span data-ttu-id="c8577-133">この例では、XML ドキュメントは DOM への読み込み時には検証されませんが、DOM への読み込み後に、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドを使用して検証されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-133">In this example, the XML document is not validated as it is loaded into the DOM, but rather is validated after it has been loaded into the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="c8577-134"><xref:System.Xml.XmlDocument.Validate%2A> メソッドは XML ドキュメントを <xref:System.Xml.XmlDocument.Schemas%2A> の <xref:System.Xml.XmlDocument> プロパティに含まれている XML スキーマに対して検証します。</span><span class="sxs-lookup"><span data-stu-id="c8577-134">The <xref:System.Xml.XmlDocument.Validate%2A> method validates the XML document against the XML schemas contained in the <xref:System.Xml.XmlDocument.Schemas%2A> property of the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="c8577-135">その後、無効な変更を加えられた後、XML ドキュメントが再検証され、スキーマ検証エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="c8577-135">Invalid modifications are then made to the XML document, and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="c8577-136">最後に、エラーの 1 つが修正された後、XML ドキュメントの一部が部分的に検証されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-136">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="c8577-137">この例は入力として、上記の「DOM への読み込み時の XML ドキュメントの検証」で参照されている `contosoBooks.xml` ファイルと `contosoBooks.xsd` ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="c8577-137">The example takes as input the `contosoBooks.xml` and `contosoBooks.xsd` files referred to in "Validating an XML Document as it is Loaded into the DOM" above.</span></span>

## <a name="handling-validation-errors-and-warnings"></a><span data-ttu-id="c8577-138">検証エラーおよび警告の処理</span><span class="sxs-lookup"><span data-stu-id="c8577-138">Handling Validation Errors and Warnings</span></span>

<span data-ttu-id="c8577-139">XML スキーマ検証エラーは、DOM に読み込まれる XML データの検証時に報告されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-139">XML schema validation errors are reported when validating XML data loaded in the DOM.</span></span> <span data-ttu-id="c8577-140">XML データ読み込み時の検証中またはまだ未検証の XML ドキュメントの検証時に検出されたスキーマ検証エラーのすべてについて通知されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-140">You are notified about all schema validation errors found while validating the XML data as it is being loaded, or when validating a previously unvalidated XML document.</span></span>

<span data-ttu-id="c8577-141">検証エラーは <xref:System.Xml.Schema.ValidationEventHandler> によって処理されます。</span><span class="sxs-lookup"><span data-stu-id="c8577-141">Validation errors are handled by the <xref:System.Xml.Schema.ValidationEventHandler>.</span></span> <span data-ttu-id="c8577-142"><xref:System.Xml.Schema.ValidationEventHandler> が <xref:System.Xml.XmlReaderSettings> インスタンスに割り当てられているか、<xref:System.Xml.XmlDocument.Validate%2A> クラスの <xref:System.Xml.XmlDocument> メソッドに渡されている場合、<xref:System.Xml.Schema.ValidationEventHandler> がスキーマ検証エラーを処理します。それ以外の場合は、スキーマ検証エラーの検出時に <xref:System.Xml.Schema.XmlSchemaValidationException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="c8577-142">If a <xref:System.Xml.Schema.ValidationEventHandler> was assigned to the <xref:System.Xml.XmlReaderSettings> instance, or passed to the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.Schema.ValidationEventHandler> will handle schema validation errors; otherwise an <xref:System.Xml.Schema.XmlSchemaValidationException> is raised when a schema validation error is encountered.</span></span>

> [!NOTE]
> <span data-ttu-id="c8577-143"><xref:System.Xml.Schema.ValidationEventHandler> がプロセスを停止する例外を生成しない限り、スキーマ検証エラーが発生しても XML データは DOM に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="c8577-143">The XML data is loaded into the DOM despite schema validation errors unless your <xref:System.Xml.Schema.ValidationEventHandler> raises an exception to stop the process.</span></span>
>
> <span data-ttu-id="c8577-144"><xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> フラグが <xref:System.Xml.XmlReaderSettings> オブジェクトに指定されていない場合、スキーマ検証警告は報告されません。</span><span class="sxs-lookup"><span data-stu-id="c8577-144">Schema validation warnings are not reported unless the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> flag is specified to the <xref:System.Xml.XmlReaderSettings> object.</span></span>

 <span data-ttu-id="c8577-145"><xref:System.Xml.Schema.ValidationEventHandler> を説明する例については、上記の「DOM への読み込み時の XML ドキュメントの検証」と「DOM における XML ドキュメントの検証」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8577-145">For examples illustrating the <xref:System.Xml.Schema.ValidationEventHandler>, see "Validating an XML Document As It Is Loaded into the DOM" and "Validating an XML Document in the DOM" above.</span></span>

## <a name="see-also"></a><span data-ttu-id="c8577-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="c8577-146">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [<span data-ttu-id="c8577-147">DOM モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="c8577-147">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)
- [<span data-ttu-id="c8577-148">XML スキーマの使用</span><span class="sxs-lookup"><span data-stu-id="c8577-148">Working with XML Schemas</span></span>](working-with-xml-schemas.md)
