---
title: 厳密に型指定された XML データへの XPathNavigator を使用したアクセス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 898e0f52-8a7c-4d1f-afcd-6ffb28b050b4
ms.openlocfilehash: 7051aeb8cdc25518f99fe093045e7e769ae7f6f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725418"
---
# <a name="accessing-strongly-typed-xml-data-using-xpathnavigator"></a><span data-ttu-id="f7c9f-102">厳密に型指定された XML データへの XPathNavigator を使用したアクセス</span><span class="sxs-lookup"><span data-stu-id="f7c9f-102">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>

<span data-ttu-id="f7c9f-103">XPath 2.0 データ モデルの一例として、<xref:System.Xml.XPath.XPathNavigator> クラスは、共通言語ランタイム (CLR) 型に対応した厳密に型指定されたデータを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-103">As an instance of the XPath 2.0 data model, the <xref:System.Xml.XPath.XPathNavigator> class can contain strongly typed data that maps to common language runtime (CLR) types.</span></span> <span data-ttu-id="f7c9f-104">XPath 2.0 のデータ モデルに従い、要素と属性のみが厳密に型指定されたデータを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-104">According to the XPath 2.0 data model, only elements and attributes can contain strongly typed data.</span></span> <span data-ttu-id="f7c9f-105"><xref:System.Xml.XPath.XPathNavigator> クラスは、データ型を変換する機構に加えて、厳密に型指定されたデータとして <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のデータにアクセスする機構を提供します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-105">The <xref:System.Xml.XPath.XPathNavigator> class provides mechanisms for accessing data within an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object as strongly typed data as well as mechanisms for converting from one data type to another.</span></span>  
  
## <a name="type-information-exposed-by-xpathnavigator"></a><span data-ttu-id="f7c9f-106">XPathNavigator が公開する型情報</span><span class="sxs-lookup"><span data-stu-id="f7c9f-106">Type Information Exposed by XPathNavigator</span></span>  

 <span data-ttu-id="f7c9f-107">DTD、XML スキーマ定義言語 (XSD) のスキーマ、または他の機構を使用して処理しない限り、XML 1.0 データに型はありません。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-107">XML 1.0 data is technically without type, unless processed with a DTD, XML schema definition language (XSD) schema, or other mechanism.</span></span> <span data-ttu-id="f7c9f-108">XML 要素や属性と関連付けられる型情報のカテゴリは多数あります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-108">There are a number of categories of type information that can be associated with an XML element or attribute.</span></span>  
  
- <span data-ttu-id="f7c9f-109">単純な CLR 型: XML スキーマ言語で共通言語ランタイム (CLR) 型を直接サポートするものはありません。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-109">Simple CLR Types: None of the XML Schema languages support Common Language Runtime (CLR) types directly.</span></span> <span data-ttu-id="f7c9f-110">要素や属性の単純コンテンツを最適な CLR 型として見ることができると便利なので、コンテンツをさらに適切な型に細分化する追加のスキーマ情報がない場合、すべての単純コンテンツは <xref:System.String> として型指定できます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-110">Because it is useful to be able to view simple element and attribute content as the most appropriate CLR type, all simple content can be typed as <xref:System.String> in the absence of schema information with any added schema information potentially refining this content to a more appropriate type.</span></span> <span data-ttu-id="f7c9f-111"><xref:System.Xml.XPath.XPathNavigator.ValueType%2A> プロパティを使用することにより、要素と属性の単純コンテンツに最も一致する CLR 型を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-111">You can find the best matching CLR type of simple element and attribute content by using the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property.</span></span> <span data-ttu-id="f7c9f-112">スキーマの組み込み型から CLR 型への対応の詳細については、「[System.Xml クラスでの型のサポート](type-support-in-the-system-xml-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-112">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="f7c9f-113">単純 (CLR) 型のリスト: 単純コンテンツを持つ要素と属性には、空白で区切られた値のリストを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-113">Lists of Simple (CLR) Types: An element or attribute with simple content can contain a list of values separated by white space.</span></span> <span data-ttu-id="f7c9f-114">値は XML スキーマで "リスト型" として指定します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-114">The values are specified by an XML Schema to be a "list type."</span></span> <span data-ttu-id="f7c9f-115">XML スキーマがない場合、こうした単純型は 1 つのテキスト ノードとして取り扱われます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-115">In the absence of an XML Schema, such simple content would be treated as a single text node.</span></span> <span data-ttu-id="f7c9f-116">XML スキーマが使用可能な場合、この単純コンテンツは、各項が CLR オブジェクトの 1 つのコレクションに対応した単純型を持つ、これ以上分割不可能な一連の値として取り扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-116">When an XML Schema is available, this simple content can be exposed as a series of atomic values each having a simple type that maps to a collection of CLR objects.</span></span> <span data-ttu-id="f7c9f-117">スキーマの組み込み型から CLR 型への対応の詳細については、「[System.Xml クラスでの型のサポート](type-support-in-the-system-xml-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-117">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="f7c9f-118">型指定された値: スキーマにより検証された単純型の属性と要素は、型指定された値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-118">Typed Value: A schema-validated attribute or element with a simple type has a typed value.</span></span> <span data-ttu-id="f7c9f-119">この値は、数値型、文字列型、または日付型などのプリミティブ型です。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-119">This value is a primitive type such as a numeric, string, or date type.</span></span> <span data-ttu-id="f7c9f-120">XSD のすべての組み込みの単純型は、単に <xref:System.String> としてでなく、さらに適当な型としてノードの値にアクセスできる CLR 型と対応をとることができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-120">All the built-in simple types in XSD can be mapped to CLR types that provide access to the value of a node as a more appropriate type instead of just as a <xref:System.String>.</span></span> <span data-ttu-id="f7c9f-121">属性や子要素を持つ要素は複合型と考えられます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-121">An element with attributes or element children is considered to be a complex type.</span></span> <span data-ttu-id="f7c9f-122">単純コンテンツ (子としてテキスト ノードのみ) を持つ複合型の型指定された値は、そのコンテンツの単純型のそれと同じです。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-122">The typed value of a complex type with simple content (only text nodes as children) is the same as that of the simple type of its content.</span></span> <span data-ttu-id="f7c9f-123">複合コンテンツ (1 つ以上の子要素) を持つ複合型の型指定された値は、<xref:System.String> として返されたすべての子テキスト ノードの連結された文字列値です。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-123">The typed value of a complex type with complex content (one or more child elements) is the string value of the concatenation of all its child text nodes returned as a <xref:System.String>.</span></span> <span data-ttu-id="f7c9f-124">スキーマの組み込み型から CLR 型への対応の詳細については、「[System.Xml クラスでの型のサポート](type-support-in-the-system-xml-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-124">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
- <span data-ttu-id="f7c9f-125">スキーマ言語固有の型名: 多くの場合、ノードの値へのアクセスに使用されるのは (外部スキーマを適用したため設定された) CLR 型です。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-125">Schema-Language Specific Type Name: In most cases, the CLR types, which are set as a side-effect of applying an external schema, are used to provide access to the value of a node.</span></span> <span data-ttu-id="f7c9f-126">しかし、XML ドキュメントに適用された特定のスキーマに関連付けられた型を調べる必要がある場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-126">However, there may be situations where you may want to examine the type associated with a particular schema applied to an XML document.</span></span> <span data-ttu-id="f7c9f-127">たとえば、XML ドキュメントを検索して、添付されたスキーマに従って "PurchaseOrder" 型の内容を持つすべての要素を抽出したいが場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-127">For example, you may wish to search through an XML document, extracting all elements that are determined to have content of type "PurchaseOrder" according to an attached schema.</span></span> <span data-ttu-id="f7c9f-128">このような型情報はスキーマ検証の結果としてのみ設定され、この情報には <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> プロパティと <xref:System.Xml.XPath.XPathNavigator> プロパティを通じてアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-128">Such type information can be set only as a result of schema validation and this information is accessed through the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> and <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="f7c9f-129">詳細については、下の「スキーマ検証後の情報セット (PSVI)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-129">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
- <span data-ttu-id="f7c9f-130">スキーマ言語固有の型のリフレクション: また、XML ドキュメントに適用されたスキーマ固有の型の詳細をさらに取得する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-130">Schema-Language Specific Type Reflection: In other cases, you may want to obtain further details of the schema-specific type applied to an XML document.</span></span> <span data-ttu-id="f7c9f-131">たとえば、何か特別な計算をするために、XML ファイルの読み込み中に XML ドキュメント中の有効な各ノードについて `maxOccurs` 属性を抽出する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-131">For example, when reading an XML file, you may want to extract the `maxOccurs` attribute for each valid node in the XML document in order to perform some custom calculation.</span></span> <span data-ttu-id="f7c9f-132">この情報はスキーマ検証を通じてのみ設定されるので、<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> プロパティを通じてアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-132">Because this information is set only through schema validation, it is accessed through the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span> <span data-ttu-id="f7c9f-133">詳細については、下の「スキーマ検証後の情報セット (PSVI)」のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-133">For more information, see The Post Schema Validation Infoset (PSVI) section below.</span></span>  
  
## <a name="xpathnavigator-typed-accessors"></a><span data-ttu-id="f7c9f-134">XPathNavigator の型指定されたアクセサー</span><span class="sxs-lookup"><span data-stu-id="f7c9f-134">XPathNavigator Typed Accessors</span></span>  

 <span data-ttu-id="f7c9f-135">次の表に、ノードの型情報へのアクセスに使用できる <xref:System.Xml.XPath.XPathNavigator> クラスの各種プロパティとメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-135">The following table shows the various properties and methods of the <xref:System.Xml.XPath.XPathNavigator> class that can be used to access the type information about a node.</span></span>  
  
|<span data-ttu-id="f7c9f-136">プロパティ</span><span class="sxs-lookup"><span data-stu-id="f7c9f-136">Property</span></span>|<span data-ttu-id="f7c9f-137">説明</span><span class="sxs-lookup"><span data-stu-id="f7c9f-137">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Xml.XPath.XPathNavigator.XmlType%2A>|<span data-ttu-id="f7c9f-138">有効な場合、ノードの XML スキーマ型の情報を含みます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-138">This contains the XML schema type information for the node if it is valid.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A>|<span data-ttu-id="f7c9f-139">検証後に追加されたノードのスキーマ検証後の情報セットを含みます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-139">This contains the Post Schema Validation Infoset of the node that is added after validation.</span></span> <span data-ttu-id="f7c9f-140">これには、検証情報に加えて、XML スキーマ型情報も含まれます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-140">This includes the XML schema type information, as well as validity information.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueType%2A>|<span data-ttu-id="f7c9f-141">ノードの型指定された値の CLR 型。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-141">The CLR type of the typed value of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A>|<span data-ttu-id="f7c9f-142">型がノードの XML スキーマ型に最も一致する 1 つ以上の CLR 値としてのノードの内容。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-142">The content of the node as one or more CLR values whose type is the closest match to the XML schema type of the node.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsBoolean%2A>|<span data-ttu-id="f7c9f-143">XPath 2.0 の <xref:System.String> のキャスト規則に従って、<xref:System.Boolean> 値にキャストされた現在のノードの `xs:boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-143">The <xref:System.String> value of the current node cast to a <xref:System.Boolean> value, according to the XPath 2.0 casting rules for `xs:boolean`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDateTime%2A>|<span data-ttu-id="f7c9f-144">XPath 2.0 の <xref:System.String> のキャスト規則に従って、<xref:System.DateTime> 値にキャストされた現在のノードの `xs:datetime` 値。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-144">The <xref:System.String> value of the current node cast to a <xref:System.DateTime> value, according to the XPath 2.0 casting rules for `xs:datetime`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>|<span data-ttu-id="f7c9f-145">XPath 2.0 の <xref:System.String> のキャスト規則に従って、<xref:System.Double> 値にキャストされた現在のノードの `xsd:double` 値。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-145">The <xref:System.String> value of the current node cast to a <xref:System.Double> value, according to the XPath 2.0 casting rules for `xsd:double`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>|<span data-ttu-id="f7c9f-146">XPath 2.0 の <xref:System.String> のキャスト規則に従って、<xref:System.Int32> 値にキャストされた現在のノードの `xs:integer` 値。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-146">The <xref:System.String> value of the current node cast to a <xref:System.Int32> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A>|<span data-ttu-id="f7c9f-147">XPath 2.0 の <xref:System.String> のキャスト規則に従って、<xref:System.Int64> 値にキャストされた現在のノードの `xs:integer` 値。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-147">The <xref:System.String> value of the current node cast to a <xref:System.Int64> value, according to the XPath 2.0 casting rules for `xs:integer`.</span></span>|  
|<xref:System.Xml.XPath.XPathNavigator.ValueAs%2A>|<span data-ttu-id="f7c9f-148">XPath 2.0 のキャスト規則に従って、変換先の型にキャストされたノードのコンテンツ。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-148">The contents of the node cast to the target type according to the XPath 2.0 casting rules.</span></span>|  
  
 <span data-ttu-id="f7c9f-149">スキーマの組み込み型から CLR 型への対応の詳細については、「[System.Xml クラスでの型のサポート](type-support-in-the-system-xml-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-149">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="the-post-schema-validation-infoset-psvi"></a><span data-ttu-id="f7c9f-150">スキーマ検証後の情報セット (PSVI)</span><span class="sxs-lookup"><span data-stu-id="f7c9f-150">The Post Schema Validation Infoset (PSVI)</span></span>  

 <span data-ttu-id="f7c9f-151">XML スキーマ プロセッサは、XML 情報セットを入力として受け入れ、それをスキーマ検証後の情報セット (PSVI) に変換します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-151">An XML Schema processor accepts an XML Infoset as input and converts it into a Post Schema Validation Infoset (PSVI).</span></span> <span data-ttu-id="f7c9f-152">PSVI は、元の入力 XML 情報セットに新しい情報項目を追加し、新しいプロパティを追加したものです。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-152">A PSVI is the original input XML infoset with new information items added and new properties added to existing information items.</span></span> <span data-ttu-id="f7c9f-153"><xref:System.Xml.XPath.XPathNavigator> によって公開される PSVI 中の XML 情報セットに追加される情報には 3 つの広範なクラスがあります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-153">There are three broad classes of information added to the XML Infoset in the PSVI that are exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
1. <span data-ttu-id="f7c9f-154">検証結果: 要素または属性が問題なく検証されたかどうかの情報。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-154">Validation Outcomes: Information as to whether an element or attribute was successfully validated or not.</span></span> <span data-ttu-id="f7c9f-155">これは、<xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> プロパティの <xref:System.Xml.XPath.XPathNavigator> プロパティによって公開されます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-155">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
2. <span data-ttu-id="f7c9f-156">既定の情報: 要素または属性の値が、スキーマに定義された既定値により得られたものかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-156">Default Information: Indications as to whether the value of the element or attribute was obtained via default values specified in the schema or not.</span></span> <span data-ttu-id="f7c9f-157">これは、<xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> プロパティの <xref:System.Xml.XPath.XPathNavigator> プロパティによって公開されます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-157">This is exposed by the <xref:System.Xml.Schema.IXmlSchemaInfo.IsDefault%2A> property of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
3. <span data-ttu-id="f7c9f-158">型のコメント: スキーマ コンポーネントへの参照。これは型の定義や、要素と属性の宣言である場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-158">Type Annotations: References to schema components that may be type definitions or element and attribute declarations.</span></span> <span data-ttu-id="f7c9f-159">ノードが有効な場合、<xref:System.Xml.XPath.XPathNavigator.XmlType%2A> の <xref:System.Xml.XPath.XPathNavigator> プロパティは、ノード固有の型情報を含みます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-159">The <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property of the <xref:System.Xml.XPath.XPathNavigator> contains the specific type information of the node if it is valid.</span></span> <span data-ttu-id="f7c9f-160">検証された後に編集されているときなど、ノードの有効性が不明な場合は、</span><span class="sxs-lookup"><span data-stu-id="f7c9f-160">If the validity of a node is unknown, such as when it was validated then subsequently edited.</span></span> <span data-ttu-id="f7c9f-161"><xref:System.Xml.XPath.XPathNavigator.XmlType%2A> プロパティが `null` に設定されますが、この場合でも、<xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> プロパティの各種プロパティから型情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-161">then the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property is set to `null` but type information is still available from the various properties of the <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> property of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 <span data-ttu-id="f7c9f-162">次の例は、<xref:System.Xml.XPath.XPathNavigator> によって公開されるスキーマ検証後の情報セット内の情報の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-162">The following example illustrates using information in the Post Schema Validation Infoset exposed by the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("books.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("published", "http://www.contoso.com/books")  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name)  
Console.WriteLine(navigator.SchemaInfo.Validity)  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "books.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("books.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("published", "http://www.contoso.com/books");  
  
Console.WriteLine(navigator.SchemaInfo.SchemaType.Name);  
Console.WriteLine(navigator.SchemaInfo.Validity);  
Console.WriteLine(navigator.SchemaInfo.SchemaElement.MinOccurs);  
```  
  
 <span data-ttu-id="f7c9f-163">この例は、`books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-163">The example takes the `books.xml` file as input.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="f7c9f-164">また、`books.xsd` スキーマも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-164">The example also takes the `books.xsd` schema as input.</span></span>  
  
```xml  
<xs:schema xmlns="http://www.contoso.com/books"
attributeFormDefault="unqualified" elementFormDefault="qualified"
targetNamespace="http://www.contoso.com/books"
xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:simpleType name="publishedType">  
        <xs:restriction base="xs:date">  
            <xs:minInclusive value="2003-01-01" />  
            <xs:maxInclusive value="2003-12-31" />  
        </xs:restriction>  
    </xs:simpleType>  
    <xs:complexType name="bookType">  
        <xs:sequence>  
            <xs:element name="title" type="xs:string"/>  
            <xs:element name="price" type="xs:decimal"/>  
            <xs:element name="published" type="publishedType"/>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="booksType">  
        <xs:sequence>  
            <xs:element name="book" type="bookType" />  
        </xs:sequence>  
    </xs:complexType>  
    <xs:element name="books" type="booksType" />  
</xs:schema>  
```  
  
## <a name="obtain-typed-values-using-valueas-properties"></a><span data-ttu-id="f7c9f-165">ValueAs プロパティによる型指定された値の取得</span><span class="sxs-lookup"><span data-stu-id="f7c9f-165">Obtain Typed Values Using ValueAs Properties</span></span>  

 <span data-ttu-id="f7c9f-166">ノードの型指定された値は、<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> の <xref:System.Xml.XPath.XPathNavigator> プロパティにアクセスして取得することができます。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-166">The typed value of a node can be retrieved by accessing the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property of the <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="f7c9f-167">場合により、ノードの型指定された値を別の型に変換する必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-167">In certain cases you may want to convert the typed value of a node to a different type.</span></span> <span data-ttu-id="f7c9f-168">一般的な例として、XML ノードから数値を取得する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-168">A common example is to get a numeric value from an XML node.</span></span> <span data-ttu-id="f7c9f-169">たとえば、次のような未検証で型指定されていない XML ドキュメントがあるとします。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-169">For example, consider the following unvalidated and untyped XML document.</span></span>  
  
```xml  
<books>  
    <book>  
        <title>Title</title>  
        <price>10.00</price>  
        <published>2003-12-31</published>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="f7c9f-170"><xref:System.Xml.XPath.XPathNavigator> が `price` 要素上に位置している場合、<xref:System.Xml.XPath.XPathNavigator.XmlType%2A> プロパティは `null` となり、<xref:System.Xml.XPath.XPathNavigator.ValueType%2A> プロパティは <xref:System.String> であり、<xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> プロパティは文字列 `10.00` です。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-170">If the <xref:System.Xml.XPath.XPathNavigator> is positioned on the `price` element the <xref:System.Xml.XPath.XPathNavigator.XmlType%2A> property would be `null`, the <xref:System.Xml.XPath.XPathNavigator.ValueType%2A> property would be <xref:System.String>, and the <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> property would be the string `10.00`.</span></span>  
  
 <span data-ttu-id="f7c9f-171">しかし、<xref:System.Xml.XPath.XPathItem.ValueAs%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>、<xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>、または <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> のメソッドとプロパティを使用して、値を数値として抽出することは可能です。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-171">However, it is still possible to extract the value as a numeric value using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsDouble%2A>, <xref:System.Xml.XPath.XPathNavigator.ValueAsInt%2A>, or <xref:System.Xml.XPath.XPathNavigator.ValueAsLong%2A> method and properties.</span></span> <span data-ttu-id="f7c9f-172">次の例では、<xref:System.Xml.XPath.XPathItem.ValueAs%2A> メソッドを使用してキャストを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-172">The following example illustrates performing such a cast using the <xref:System.Xml.XPath.XPathItem.ValueAs%2A> method.</span></span>  
  
```vb  
Dim document As New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
navigator.MoveToChild("books", "")  
navigator.MoveToChild("book", "")  
navigator.MoveToChild("price", "")  
  
Dim price = navigator.ValueAs(GetType(Decimal))  
Dim discount As Decimal = 0.2  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * discount))  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
navigator.MoveToChild("books", "");  
navigator.MoveToChild("book", "");  
navigator.MoveToChild("price", "");  
  
Decimal price = (decimal)navigator.ValueAs(typeof(decimal));  
  
Console.WriteLine("The price of the book has been dropped 20% from {0:C} to {1:C}", navigator.Value, (price - price * (decimal)0.20));  
```  
  
 <span data-ttu-id="f7c9f-173">スキーマの組み込み型から CLR 型への対応の詳細については、「[System.Xml クラスでの型のサポート](type-support-in-the-system-xml-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f7c9f-173">For more information about the mapping from schema built-in types to CLR types, see [Type Support in the System.Xml Classes](type-support-in-the-system-xml-classes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c9f-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7c9f-174">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="f7c9f-175">System.Xml クラスでの型のサポート</span><span class="sxs-lookup"><span data-stu-id="f7c9f-175">Type Support in the System.Xml Classes</span></span>](type-support-in-the-system-xml-classes.md)
- [<span data-ttu-id="f7c9f-176">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="f7c9f-176">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="f7c9f-177">XPathNavigator を使用するノード セットのナビゲーション</span><span class="sxs-lookup"><span data-stu-id="f7c9f-177">Node Set Navigation Using XPathNavigator</span></span>](node-set-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="f7c9f-178">XPathNavigator を使用する属性と名前空間のナビゲーション</span><span class="sxs-lookup"><span data-stu-id="f7c9f-178">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [<span data-ttu-id="f7c9f-179">XpathNavigator を使用した XML データの抽出</span><span class="sxs-lookup"><span data-stu-id="f7c9f-179">Extract XML Data Using XPathNavigator</span></span>](extract-xml-data-using-xpathnavigator.md)
