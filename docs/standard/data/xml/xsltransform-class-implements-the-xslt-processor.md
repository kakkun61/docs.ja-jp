---
title: XslTransform クラスによる XSLT プロセッサの実装
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 88373fe2-4a6b-44f9-8a62-8a3e348e3a46
ms.openlocfilehash: 57632321edf086b644da7ea4fca893edb589834f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818180"
---
# <a name="xsltransform-class-implements-the-xslt-processor"></a><span data-ttu-id="e3c28-102">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="e3c28-102">XslTransform Class Implements the XSLT Processor</span></span>

> [!NOTE]
> <span data-ttu-id="e3c28-103">.NET Framework 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="e3c28-103">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="e3c28-104"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-104">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="e3c28-105">詳しくは、「[XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](migrating-from-the-xsltransform-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e3c28-105">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>

<span data-ttu-id="e3c28-106"><xref:System.Xml.Xsl.XslTransform> クラスは、『XSL Transformations (XSLT) Version 1.0』勧告を実装する XSLT プロセッサです。</span><span class="sxs-lookup"><span data-stu-id="e3c28-106">The <xref:System.Xml.Xsl.XslTransform> class is an XSLT processor implementing the XSL Transformations (XSLT) Version 1.0 recommendation.</span></span> <span data-ttu-id="e3c28-107"><xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドはスタイル シートを検索して読み込み、<xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドは渡されたソース ドキュメントを変換します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-107">The <xref:System.Xml.Xsl.XslTransform.Load%2A> method locates and reads style sheets, and the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method transforms the given source document.</span></span> <span data-ttu-id="e3c28-108"><xref:System.Xml.XPath.IXPathNavigable> インターフェイスを実装している任意のストアを <xref:System.Xml.Xsl.XslTransform> のソース ドキュメントとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-108">Any store that implements the <xref:System.Xml.XPath.IXPathNavigable> interface can be used as the source document for the <xref:System.Xml.Xsl.XslTransform>.</span></span> <span data-ttu-id="e3c28-109">.NET Framework では、現在、<xref:System.Xml.XPath.IXPathNavigable> インターフェイスを <xref:System.Xml.XmlDocument>、<xref:System.Xml.XmlDataDocument>、および <xref:System.Xml.XPath.XPathDocument> に実装しているので、これらすべてを変換用の入力ソース ドキュメントとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-109">The .NET Framework currently implements the <xref:System.Xml.XPath.IXPathNavigable> interface on the <xref:System.Xml.XmlDocument>, the <xref:System.Xml.XmlDataDocument>, and the <xref:System.Xml.XPath.XPathDocument>, so all of these can be used as the input source document to a transformation.</span></span>

<span data-ttu-id="e3c28-110">.NET Framework の <xref:System.Xml.Xsl.XslTransform> オブジェクトは、次の名前空間で定義されている XSLT 1.0 仕様のみをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="e3c28-110">The <xref:System.Xml.Xsl.XslTransform> object in the .NET Framework only supports the XSLT 1.0 specification, defined with the following namespace:</span></span>

```xml
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">
```

<span data-ttu-id="e3c28-111"><xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドを使用して、次のいずれかのクラスからスタイル シートを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-111">The style sheet can be loaded, using the <xref:System.Xml.Xsl.XslTransform.Load%2A> method, from one of the following classes:</span></span>

- <span data-ttu-id="e3c28-112">XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e3c28-112">XPathNavigator</span></span>

- <span data-ttu-id="e3c28-113">XmlReader</span><span class="sxs-lookup"><span data-stu-id="e3c28-113">XmlReader</span></span>

- <span data-ttu-id="e3c28-114">URL を表す文字列</span><span class="sxs-lookup"><span data-stu-id="e3c28-114">A string representing a URL</span></span>

<span data-ttu-id="e3c28-115">これらの入力クラスには、それぞれに対応する別々の <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-115">There is a different <xref:System.Xml.Xsl.XslTransform.Load%2A> method for each of the above input classes.</span></span> <span data-ttu-id="e3c28-116">これらのクラスの 1 つと <xref:System.Xml.XmlResolver> クラスの組み合わせを引数として受け取るメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-116">Some methods take in a combination of one of these classes and the <xref:System.Xml.XmlResolver> class as arguments.</span></span> <span data-ttu-id="e3c28-117"><xref:System.Xml.XmlResolver> は、スタイル シート内の `<xsl:import>` または `<xsl:include>` によって参照されているリソースを検索します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-117">The <xref:System.Xml.XmlResolver> locates resources referenced by `<xsl:import>` or `<xsl:include>` found in the style sheet.</span></span> <span data-ttu-id="e3c28-118">次に示すメソッドは、文字列、<xref:System.Xml.XmlReader>、または <xref:System.Xml.XPath.XPathNavigator> を入力として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-118">The following methods take a string, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> as input.</span></span>

```vb
Overloads Public Sub Load(String)
```

```csharp
public void Load(string);
```

```vb
Overloads Public Sub Load(String, XmlResolver)
```

```csharp
public void Load(string, XmlResolver);
```

```vb
Overloads Public Sub Load(XmlReader, XmlResolver, Evidence)
```

```csharp
public void Load(XmlReader, XmlResolver, Evidence);
```

```vb
Overloads Public Sub Load(XPathNavigator, XmlResolver, Evidence)
```

```csharp
public void Load(XPathNavigator, XmlResolver, Evidence);
```

<span data-ttu-id="e3c28-119">上に示した <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドの大半は、<xref:System.Xml.XmlResolver> をパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-119">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods shown above take an <xref:System.Xml.XmlResolver> as a parameter.</span></span> <span data-ttu-id="e3c28-120"><xref:System.Xml.XmlResolver> は、スタイル シートおよび xsl:import 要素と xsl:include 要素で参照されているスタイル シートの読み込みに使用します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-120">The <xref:System.Xml.XmlResolver> is used to load the style sheet and any style sheet(s) referenced in xsl:import and xsl:include elements.</span></span>

<span data-ttu-id="e3c28-121">大半の <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドは証拠もパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-121">Most of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods also take evidence as a parameter.</span></span> <span data-ttu-id="e3c28-122">証拠パラメーターは、スタイル シートに関連付けられている <xref:System.Security.Policy.Evidence> です。</span><span class="sxs-lookup"><span data-stu-id="e3c28-122">The evidence parameter is the <xref:System.Security.Policy.Evidence> that is associated with the style sheet.</span></span> <span data-ttu-id="e3c28-123">スタイル シートのセキュリティ レベルに応じて、スタイル シートに含まれているスクリプト、スタイル シートで使用されている `document()` 関数、<xref:System.Xml.Xsl.XsltArgumentList> で使用されている拡張オブジェクトなど、そのスタイル シートが参照しているリソースのセキュリティ レベルも変わります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-123">The security level of the style sheet affects the security level of any subsequent resources it references, such as the script it contains, any `document()` functions it uses, and any extension objects used by the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="e3c28-124">URL パラメーターが含まれた <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドを使用してスタイル シートを読み込んだ場合、証拠が指定されていなければ、指定された URL およびそのサイトとゾーンを組み合わせてスタイル シートの証拠が計算されます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-124">If the style sheet is loaded using a <xref:System.Xml.Xsl.XslTransform.Load%2A> method that contains a URL parameter and no evidence is provided, the evidence of the style sheet is calculated by combining the given URL with its site and zone.</span></span>

<span data-ttu-id="e3c28-125">URI も証拠も指定されていない場合は、スタイル シートに対して設定されている証拠が完全に信頼されます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-125">If no URI or evidence is provided, then the evidence set for the style sheet is fully trusted.</span></span> <span data-ttu-id="e3c28-126">信頼されていないソースからスタイル シートを読み込んだり、信頼されていない拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> に追加したりしないでください。</span><span class="sxs-lookup"><span data-stu-id="e3c28-126">Do not load style sheets from untrusted sources, or add untrusted extension objects into the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

<span data-ttu-id="e3c28-127">セキュリティ レベルと証拠、それがスクリプトに及ぼす影響の詳細については、「[\<msxsl:script> を使用した XSLT スタイルシートのスクリプト](xslt-stylesheet-scripting-using-msxsl-script.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3c28-127">For more information about security levels and evidence and how it affects scripting, see [XSLT Stylesheet Scripting Using \<msxsl:script>](xslt-stylesheet-scripting-using-msxsl-script.md).</span></span> <span data-ttu-id="e3c28-128">セキュリティ レベルと証拠、それが拡張オブジェクトに与える影響の詳細については、「[スタイル シート パラメーターと拡張オブジェクト用の XsltArgumentList](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3c28-128">For information about security levels and evidence and how it affects extension objects, see [XsltArgumentList for Style Sheet Parameters and Extension Objects](xsltargumentlist-for-style-sheet-parameters-and-extension-objects.md).</span></span>

<span data-ttu-id="e3c28-129">セキュリティ レベルと証拠、それが `document()` 関数に及ぼす影響については、「[外部の XSLT スタイル シートとドキュメントの解決](resolving-external-xslt-style-sheets-and-documents.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3c28-129">For information about security levels and evidence and how it affects the `document()` function, see [Resolving External XSLT Style Sheets and Documents](resolving-external-xslt-style-sheets-and-documents.md).</span></span>

<span data-ttu-id="e3c28-130">スタイル シートに対しては、多くの入力パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-130">A style sheet can be supplied with a number of input parameters.</span></span> <span data-ttu-id="e3c28-131">スタイル シートでは、拡張オブジェクトの関数を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-131">The style sheet can also call functions on extension objects.</span></span> <span data-ttu-id="e3c28-132">パラメーターおよび拡張オブジェクトのいずれも <xref:System.Xml.Xsl.XsltArgumentList> クラスを使用してスタイル シートに渡されます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-132">Both parameters and extension objects are supplied to the style sheet using the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span> <span data-ttu-id="e3c28-133"><xref:System.Xml.Xsl.XsltArgumentList> の詳細については、「<xref:System.Xml.Xsl.XsltArgumentList>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3c28-133">For more information about the <xref:System.Xml.Xsl.XsltArgumentList>, see <xref:System.Xml.Xsl.XsltArgumentList>.</span></span>

## <a name="recommended-secure-use-of-xsltransform-class"></a><span data-ttu-id="e3c28-134">XslTransform クラスの安全な使用方法</span><span class="sxs-lookup"><span data-stu-id="e3c28-134">Recommended Secure Use of XslTransform Class</span></span>

<span data-ttu-id="e3c28-135">スタイル シートのセキュリティ特権は、指定されている証拠によって異なります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-135">The security privileges of the style sheet depend on the evidence provided.</span></span> <span data-ttu-id="e3c28-136">次の表では、スタイル シートの場所と、指定する証拠の種類を説明します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-136">The following table summarizes the location of the style sheet and gives an explanation of what type of evidence to give.</span></span>

- <span data-ttu-id="e3c28-137">XSLT スタイル シートに外部参照がない場合。またはスタイル シートが信頼できるコード ベースにある場合。</span><span class="sxs-lookup"><span data-stu-id="e3c28-137">The XSLT style sheet has no external references, or the style sheet comes from a code base that you trust.</span></span>

  - <span data-ttu-id="e3c28-138">アセンブリの証拠を指定します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-138">Provide the evidence from your assembly:</span></span>

    ```vb
    Dim xslt = New XslTransform() xslt.Load(stylesheet, resolver, Me.GetType().Assembly.Evidence)

    XsltTransform xslt = new XslTransform();  xslt.Load(stylesheet, resolver, this.GetType().Assembly.Evidence);
    ```

- <span data-ttu-id="e3c28-139">XSLT スタイル シートが外部ソースにある場合。</span><span class="sxs-lookup"><span data-stu-id="e3c28-139">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="e3c28-140">ソースの出所が知られており、検証可能な URI がある。</span><span class="sxs-lookup"><span data-stu-id="e3c28-140">The origin of the source is known and there is a verifiable URI.</span></span>

  - <span data-ttu-id="e3c28-141">URI を使用して証拠を作成します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-141">Create evidence using the URI.</span></span>

    ```vb
    Dim xslt As New XslTransform() Dim ev As Evidence = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri) xslt.Load(stylesheet, resolver, evidence)

    XslTransform xslt = new XslTransform(); Evidence ev = XmlSecureResolver.CreateEvidenceForUrl(stylesheetUri); xslt.Load(stylesheet, resolver, evidence);
    ```

- <span data-ttu-id="e3c28-142">XSLT スタイル シートが外部ソースにある場合。</span><span class="sxs-lookup"><span data-stu-id="e3c28-142">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="e3c28-143">ソースの出所は不明。</span><span class="sxs-lookup"><span data-stu-id="e3c28-143">The origin of the source is not known.</span></span>

  - <span data-ttu-id="e3c28-144">証拠を `null` に設定します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-144">Set evidence to `null`.</span></span> <span data-ttu-id="e3c28-145">スクリプト ブロックは処理されません。XSLT `document()` 関数はサポートされません。特権を持つ拡張オブジェクトは許可されません。</span><span class="sxs-lookup"><span data-stu-id="e3c28-145">Script blocks are not processed, the XSLT `document()` function is not supported, and privileged extension objects are disallowed.</span></span>

    <span data-ttu-id="e3c28-146">`resolver` パラメーターを `null` に設定することもできます。そうすれば、`xsl:import` 要素と `xsl:include` 要素は処理されません。</span><span class="sxs-lookup"><span data-stu-id="e3c28-146">Additionally, you can also set the `resolver` parameter to `null` This ensures that `xsl:import` and `xsl:include` elements are not processed.</span></span>

- <span data-ttu-id="e3c28-147">XSLT スタイル シートが外部ソースにある場合。</span><span class="sxs-lookup"><span data-stu-id="e3c28-147">The XSLT style sheet comes from an outside source.</span></span> <span data-ttu-id="e3c28-148">ソースの出所が不明であるが、スクリプトのサポートが必要。</span><span class="sxs-lookup"><span data-stu-id="e3c28-148">The origin of the source is not known, but you require script support.</span></span>

  - <span data-ttu-id="e3c28-149">呼び出し元の証拠を要求します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-149">Request evidence from the caller.</span></span>

## <a name="transformation-of-xml-data"></a><span data-ttu-id="e3c28-150">XML データの変換</span><span class="sxs-lookup"><span data-stu-id="e3c28-150">Transformation of XML Data</span></span>

<span data-ttu-id="e3c28-151">スタイル シートが読み込まれた後で、いずれかの <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを呼び出し、入力ソース ドキュメントを渡すと、変換が開始されます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-151">Once a style sheet is loaded, the transformation starts by calling one of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> methods and supplying an input source document.</span></span> <span data-ttu-id="e3c28-152"><xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドは、さまざまな変換出力を提供できるように、オーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-152">The <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is overloaded to provide different transformation outputs.</span></span> <span data-ttu-id="e3c28-153">変換の結果として得られる出力形式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-153">The transformation can result in the following output formats:</span></span>

- <xref:System.Xml.XmlReader>

- <xref:System.Xml.XmlWriter>

- <xref:System.IO.TextWriter>

- <xref:System.IO.Stream>

- <span data-ttu-id="e3c28-154">ファイルの文字列 URL</span><span class="sxs-lookup"><span data-stu-id="e3c28-154">String URL of file</span></span>

<span data-ttu-id="e3c28-155">最後の文字列 URL 形式は、URL 上にある入力ドキュメントを変換し、そのドキュメントを出力 URL に書き込む場合によく使用されます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-155">This last format, the string URL, provides for a commonly used scenario in transforming an input document located in a URL and writing the document to the output URL.</span></span> <span data-ttu-id="e3c28-156">この <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドは、ファイルから XML ドキュメントを読み込み、XSLT 変換を実行し、出力をファイルに書き込む場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="e3c28-156">This <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is a convenience method to load an XML document from a file, perform the XSLT transformation, and write the output to a file.</span></span> <span data-ttu-id="e3c28-157">これにより、入力ソース ドキュメントを作成および読み込んでからファイル ストリームに書き込む必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-157">This prevents you from having to create and load the input source document, and then write to a file stream.</span></span> <span data-ttu-id="e3c28-158">文字列 URL を入出力として使う <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドを使用するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-158">The following code sample shows this use of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method using the string URL as input and output:</span></span>

```vb
Dim xsltransform As XslTransform = New XslTransform()
xsltransform.Load("favorite.xsl")
xsltransform.Transform("MyDocument.Xml", "TransformResult.xml", Nothing)
```

```csharp
XslTransform xsltransform = new XslTransform();
xsltransform.Load("favorite.xsl");
xsltransform.Transform("MyDocument.xml", "TransformResult.xml", null);
```

## <a name="transforming-a-section-of-an-xml-document"></a><span data-ttu-id="e3c28-159">XML ドキュメントのセクションの変換</span><span class="sxs-lookup"><span data-stu-id="e3c28-159">Transforming a Section of an XML Document</span></span>

<span data-ttu-id="e3c28-160">変換はドキュメント全体に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-160">Transformations apply to the document as a whole.</span></span> <span data-ttu-id="e3c28-161">つまり、ドキュメント ルート ノード以外のノードを指定しても、変換処理では、読み込んだドキュメントのすべてのノードがアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-161">In other words, if you pass in a node other than the document root node, this does not prevent the transformation process from accessing all nodes in the loaded document.</span></span> <span data-ttu-id="e3c28-162">結果ツリー フラグメントを変換するには、結果ツリー フラグメントだけが含まれた <xref:System.Xml.XmlDocument> を作成し、その <xref:System.Xml.XmlDocument> を <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-162">To transform a result tree fragment, you must create an <xref:System.Xml.XmlDocument> containing just the result tree fragment and pass that <xref:System.Xml.XmlDocument> to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="e3c28-163">結果ツリー フラグメントの変換を実行する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-163">The following example performs a transformation on a result tree fragment.</span></span>

```vb
Dim xslt As New XslTransform()
xslt.Load("print_root.xsl")
Dim doc As New XmlDocument()
doc.Load("library.xml")
' Create a new document containing just the result tree fragment.
Dim testNode As XmlNode = doc.DocumentElement.FirstChild
Dim tmpDoc As New XmlDocument()
tmpDoc.LoadXml(testNode.OuterXml)
' Pass the document containing the result tree fragment
' to the Transform method.
Console.WriteLine(("Passing " + tmpDoc.OuterXml + " to print_root.xsl"))
xslt.Transform(tmpDoc, Nothing, Console.Out, Nothing)
```

```csharp
XslTransform xslt = new XslTransform();
xslt.Load("print_root.xsl");
XmlDocument doc = new XmlDocument();
doc.Load("library.xml");
// Create a new document containing just the result tree fragment.
XmlNode testNode = doc.DocumentElement.FirstChild;
XmlDocument tmpDoc = new XmlDocument();
tmpDoc.LoadXml(testNode.OuterXml);
// Pass the document containing the result tree fragment
// to the Transform method.
Console.WriteLine("Passing " + tmpDoc.OuterXml + " to print_root.xsl");
xslt.Transform(tmpDoc, null, Console.Out, null);
```

<span data-ttu-id="e3c28-164">この例では、library.xml ファイルと print_root.xsl ファイルを入力として使用し、次の出力をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-164">The example uses the library.xml and print_root.xsl files as input and outputs the following to the console:</span></span>

```console
Passing <book genre="novel" ISBN="1-861001-57-5"><title>Pride And Prejudice</title></book> to print_root.xsl
Root node is book.
```

<span data-ttu-id="e3c28-165">library.xml</span><span class="sxs-lookup"><span data-stu-id="e3c28-165">library.xml</span></span>

```xml
<library>
  <book genre='novel' ISBN='1-861001-57-5'>
     <title>Pride And Prejudice</title>
  </book>
  <book genre='novel' ISBN='1-81920-21-2'>
     <title>Hook</title>
  </book>
</library>
```

<span data-ttu-id="e3c28-166">print_root.xsl</span><span class="sxs-lookup"><span data-stu-id="e3c28-166">print_root.xsl</span></span>

```xml
<stylesheet version="1.0" xmlns="http://www.w3.org/1999/XSL/Transform" >
  <output method="text" />
  <template match="/">
     Root node is  <value-of select="local-name(//*[position() = 1])" />
  </template>
</stylesheet>
```

## <a name="migration-of-xslt-from-net-framework-version-10-to-net-framework-version-11"></a><span data-ttu-id="e3c28-167">.NET Framework Version 1.0 から .NET Framework Version 1.1 への XSLT の移行</span><span class="sxs-lookup"><span data-stu-id="e3c28-167">Migration of XSLT from .NET Framework version 1.0 to .NET Framework version 1.1</span></span>

<span data-ttu-id="e3c28-168">廃止された .NET Framework バージョン 1.0 と新しい .NET Framework バージョン 1.1 の <xref:System.Xml.Xsl.XslTransform.Load%2A> メソッドを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-168">The following table shows the obsolete .NET Framework version 1.0 methods and new .NET Framework version 1.1 methods for the <xref:System.Xml.Xsl.XslTransform.Load%2A> method.</span></span> <span data-ttu-id="e3c28-169">新しいメソッドでは、証拠を指定することで、スタイル シートのアクセス許可を制限できます。</span><span class="sxs-lookup"><span data-stu-id="e3c28-169">The new methods enable you to limit the permissions of the style sheet by specifying evidence.</span></span>

|<span data-ttu-id="e3c28-170">廃止された .NET Framework バージョン 1.0 の Load メソッド</span><span class="sxs-lookup"><span data-stu-id="e3c28-170">Obsolete .NET Framework version 1.0 Load Methods</span></span>|<span data-ttu-id="e3c28-171">新しい .NET Framework バージョン 1.1 の Load メソッド</span><span class="sxs-lookup"><span data-stu-id="e3c28-171">Replacement .NET Framework version 1.1 Load Methods</span></span>|
|------------------------------------------------------|---------------------------------------------------------|
|<span data-ttu-id="e3c28-172">Load(XPathNavigator input);</span><span class="sxs-lookup"><span data-stu-id="e3c28-172">Load(XPathNavigator input);</span></span><br /><br /> <span data-ttu-id="e3c28-173">Load(XPathNavigator input, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="e3c28-173">Load(XPathNavigator input, XmlResolver resolver);</span></span>|<span data-ttu-id="e3c28-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="e3c28-174">Load(XPathNavigator stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="e3c28-175">Load(IXPathNavigable stylesheet);</span><span class="sxs-lookup"><span data-stu-id="e3c28-175">Load(IXPathNavigable stylesheet);</span></span><br /><br /> <span data-ttu-id="e3c28-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="e3c28-176">Load(IXPathNavigable stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="e3c28-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="e3c28-177">Load(IXPathNavigable stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|
|<span data-ttu-id="e3c28-178">Load(XmlReader stylesheet);</span><span class="sxs-lookup"><span data-stu-id="e3c28-178">Load(XmlReader stylesheet);</span></span><br /><br /> <span data-ttu-id="e3c28-179">Load(XmlReader stylesheet, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="e3c28-179">Load(XmlReader stylesheet, XmlResolver resolver);</span></span>|<span data-ttu-id="e3c28-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span><span class="sxs-lookup"><span data-stu-id="e3c28-180">Load(XmlReader stylesheet, XmlResolver resolver, Evidence evidence);</span></span>|

<span data-ttu-id="e3c28-181">廃止された <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドと新しい  メソッドを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-181">The following table shows the obsolete and new methods for the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method.</span></span> <span data-ttu-id="e3c28-182">新しいメソッドは <xref:System.Xml.XmlResolver> オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e3c28-182">The new methods take an <xref:System.Xml.XmlResolver> object.</span></span>

|<span data-ttu-id="e3c28-183">廃止された .NET Framework バージョン 1.0 の Transform メソッド</span><span class="sxs-lookup"><span data-stu-id="e3c28-183">Obsolete .NET Framework version 1.0 Transform Methods</span></span>|<span data-ttu-id="e3c28-184">新しい .NET Framework バージョン 1.1 の Transform メソッド</span><span class="sxs-lookup"><span data-stu-id="e3c28-184">Replacement .NET Framework version Transform 1.1 Methods</span></span>|
|-----------------------------------------------------------|--------------------------------------------------------------|
|<span data-ttu-id="e3c28-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="e3c28-185">XmlReader Transform(XPathNavigator input, XsltArgumentList args)</span></span>|<span data-ttu-id="e3c28-186">XmlReader Transform(XPathNavigator input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-186">XmlReader Transform(XPathNavigator  input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span><span class="sxs-lookup"><span data-stu-id="e3c28-187">XmlReader Transform(IXPathNavigable input, XsltArgumentList args)</span></span>|<span data-ttu-id="e3c28-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-188">XmlReader Transform(IXPathNavigable input, XsltArgumentList args, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="e3c28-189">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="e3c28-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-190">Void Transform(XPathNavigator input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span><span class="sxs-lookup"><span data-stu-id="e3c28-191">Void Transform(IXPathNavigable input, XsltArgumentList args, XmlWriter output)</span></span>|<span data-ttu-id="e3c28-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-192">Void Transform(IXpathNavigable input, XsltArgumentList args, XmlWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="e3c28-193">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="e3c28-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-194">Void Transform(XPathNavigator input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span><span class="sxs-lookup"><span data-stu-id="e3c28-195">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output)</span></span>|<span data-ttu-id="e3c28-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-196">Void Transform(IXPathNavigable input, XsltArgumentList args, TextWriter output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="e3c28-197">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="e3c28-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-198">Void Transform(XPathNavigator input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span><span class="sxs-lookup"><span data-stu-id="e3c28-199">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output)</span></span>|<span data-ttu-id="e3c28-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span><span class="sxs-lookup"><span data-stu-id="e3c28-200">Void Transform(IXPathNavigable input, XsltArgumentList args, Stream output, XmlResolver resolver)</span></span>|
|<span data-ttu-id="e3c28-201">Void Transform(String input, String output);</span><span class="sxs-lookup"><span data-stu-id="e3c28-201">Void Transform(String input, String output);</span></span>|<span data-ttu-id="e3c28-202">Void Transform(String input, String output, XmlResolver resolver);</span><span class="sxs-lookup"><span data-stu-id="e3c28-202">Void Transform(String input, String output, XmlResolver resolver);</span></span>|

<span data-ttu-id="e3c28-203">.NET Framework バージョン 1.1 では、<xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> プロパティが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="e3c28-203">The <xref:System.Xml.Xsl.XslTransform.XmlResolver%2A?displayProperty=nameWithType> property is obsolete in .NET Framework version 1.1.</span></span> <span data-ttu-id="e3c28-204">代わりに、<xref:System.Xml.XmlResolver> オブジェクトを受け取る新しい <xref:System.Xml.Xsl.XslTransform.Transform%2A> オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="e3c28-204">Instead, use the new <xref:System.Xml.Xsl.XslTransform.Transform%2A> overloads which take an <xref:System.Xml.XmlResolver> object.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3c28-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3c28-205">See also</span></span>

- <xref:System.Xml.Xsl.XslTransform>
- [<span data-ttu-id="e3c28-206">XslTransform クラスを使用した XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="e3c28-206">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="e3c28-207">変換における XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="e3c28-207">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="e3c28-208">変換における XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="e3c28-208">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="e3c28-209">XslTransform への XPathDocument の入力</span><span class="sxs-lookup"><span data-stu-id="e3c28-209">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="e3c28-210">XslTransform への XmlDataDocument の入力</span><span class="sxs-lookup"><span data-stu-id="e3c28-210">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
- [<span data-ttu-id="e3c28-211">XslTransform への XmlDocument の入力</span><span class="sxs-lookup"><span data-stu-id="e3c28-211">XmlDocument Input to XslTransform</span></span>](xmldocument-input-to-xsltransform.md)
