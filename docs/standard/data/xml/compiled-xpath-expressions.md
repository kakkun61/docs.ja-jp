---
title: コンパイルされた XPath 式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e25dd95f-b64c-4d8b-a3a4-379e1aa0ad55
ms.openlocfilehash: 99f06db3c6f1e634e9c4a677c01d1b0849afe43f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701511"
---
# <a name="compiled-xpath-expressions"></a><span data-ttu-id="ff7fe-102">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="ff7fe-102">Compiled XPath Expressions</span></span>

<span data-ttu-id="ff7fe-103"><xref:System.Xml.XPath.XPathExpression> オブジェクトは、<xref:System.Xml.XPath.XPathExpression.Compile%2A> クラスの静的 <xref:System.Xml.XPath.XPathExpression> メソッドまたは <xref:System.Xml.XPath.XPathNavigator.Compile%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドから返されるコンパイル済み XPath クエリを表します。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-103">An <xref:System.Xml.XPath.XPathExpression> object represents a compiled XPath query returned from either the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
## <a name="the-xpathexpression-class"></a><span data-ttu-id="ff7fe-104">XPathExpression クラス</span><span class="sxs-lookup"><span data-stu-id="ff7fe-104">The XPathExpression Class</span></span>  

 <span data-ttu-id="ff7fe-105"><xref:System.Xml.XPath.XPathExpression> オブジェクトにより表されるコンパイル済み XPath クエリは、同じ XPath クエリが複数回使用されるときに有用です。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-105">A compiled XPath query represented by an <xref:System.Xml.XPath.XPathExpression> object is useful if the same XPath query is being used more than once.</span></span>  
  
 <span data-ttu-id="ff7fe-106">たとえば、<xref:System.Xml.XPath.XPathNavigator.Select%2A> メソッドを複数回呼び出すとき、毎回 XPath クエリを表す文字列を使用する代わりに、再使用とパフォーマンスの向上のために、<xref:System.Xml.XPath.XPathExpression.Compile%2A> クラスの <xref:System.Xml.XPath.XPathExpression> メソッド、または <xref:System.Xml.XPath.XPathNavigator.Compile%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドを使用して、XPath クエリを <xref:System.Xml.XPath.XPathExpression> オブジェクトにコンパイルしてキャッシュします。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-106">For example, when calling the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method multiple times, instead of using a string representing the XPath query each time, use the <xref:System.Xml.XPath.XPathExpression.Compile%2A> method of the <xref:System.Xml.XPath.XPathExpression> class or the <xref:System.Xml.XPath.XPathNavigator.Compile%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class to compile and cache the XPath query in an <xref:System.Xml.XPath.XPathExpression> object for reuse and improved performance.</span></span>  
  
 <span data-ttu-id="ff7fe-107">いったんコンパイルされると、<xref:System.Xml.XPath.XPathExpression> オブジェクトは、XPath クエリから返される型に応じて、次の <xref:System.Xml.XPath.XPathNavigator> クラス メソッドの入力として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-107">Once compiled, the <xref:System.Xml.XPath.XPathExpression> object may be used as input to the following <xref:System.Xml.XPath.XPathNavigator> class methods depending on the type returned from the XPath query.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.XPath.XPathNavigator.Matches%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="ff7fe-108">次の表では、W3C XPath の戻り型、それに等価の Microsoft .NET Framework 型、および戻り型に応じて <xref:System.Xml.XPath.XPathExpression> オブジェクトで使用できるメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-108">The following table describes each of the W3C XPath return types, their Microsoft .NET Framework equivalencies, and what methods the <xref:System.Xml.XPath.XPathExpression> object may be used with based on its return type.</span></span>  
  
|<span data-ttu-id="ff7fe-109">W3C XPath の戻り値の型</span><span class="sxs-lookup"><span data-stu-id="ff7fe-109">W3C XPath Return Type</span></span>|<span data-ttu-id="ff7fe-110">.NET Framework の等価の型</span><span class="sxs-lookup"><span data-stu-id="ff7fe-110">.NET Framework Equivalent Type</span></span>|<span data-ttu-id="ff7fe-111">説明</span><span class="sxs-lookup"><span data-stu-id="ff7fe-111">Description</span></span>|<span data-ttu-id="ff7fe-112">メソッド</span><span class="sxs-lookup"><span data-stu-id="ff7fe-112">Methods</span></span>|  
|---------------------------|------------------------------------|-----------------|-------------|  
|`Node set`|<xref:System.Xml.XPath.XPathNodeIterator>|<span data-ttu-id="ff7fe-113">重複がなく順序付けされていない、ドキュメント順に作成されたノードのコレクション。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-113">An unordered collection of nodes without duplicates created in document order.</span></span>|<span data-ttu-id="ff7fe-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> または <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span><span class="sxs-lookup"><span data-stu-id="ff7fe-114"><xref:System.Xml.XPath.XPathNavigator.Select%2A> or <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A></span></span>|  
|`Boolean`|<xref:System.Boolean>|<span data-ttu-id="ff7fe-115">`true` または `false` の値。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-115">A `true` or `false` value.</span></span>|<span data-ttu-id="ff7fe-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> または</span><span class="sxs-lookup"><span data-stu-id="ff7fe-116"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> or</span></span><br /><br /> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>|  
|`Number`|<xref:System.Double>|<span data-ttu-id="ff7fe-117">浮動小数点数。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-117">A floating-point number.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
|`String`|<xref:System.String>|<span data-ttu-id="ff7fe-118">UCS 文字のシーケンス。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-118">A sequence of UCS characters.</span></span>|<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>|  
  
> [!NOTE]
> <span data-ttu-id="ff7fe-119"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> メソッドは、XPath 式をパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-119">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method accepts an XPath expression as its parameter.</span></span> <span data-ttu-id="ff7fe-120"><xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> メソッドは W3C XPath の戻り型の 1 つではなく、1 つの <xref:System.Xml.XPath.XPathNavigator> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-120">The <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method returns an <xref:System.Xml.XPath.XPathNavigator> object, not one of the W3C XPath return types.</span></span>  
  
### <a name="the-returntype-property"></a><span data-ttu-id="ff7fe-121">戻り型のプロパティ</span><span class="sxs-lookup"><span data-stu-id="ff7fe-121">The ReturnType Property</span></span>  

 <span data-ttu-id="ff7fe-122">XPath クエリが <xref:System.Xml.XPath.XPathExpression> オブジェクトにコンパイルされた後、<xref:System.Xml.XPath.XPathExpression.ReturnType%2A> オブジェクトの <xref:System.Xml.XPath.XPathExpression> プロパティを使用して、XPath クエリで何が返されるかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-122">After an XPath query has been compiled into an <xref:System.Xml.XPath.XPathExpression> object, you can use the <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of the <xref:System.Xml.XPath.XPathExpression> object to determine what the XPath query returns.</span></span>  
  
 <span data-ttu-id="ff7fe-123"><xref:System.Xml.XPath.XPathExpression.ReturnType%2A> プロパティは、W3C XPath 戻り値を表す、次の <xref:System.Xml.XPath.XPathResultType> 列挙値の 1 つを返します。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-123">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property returns one of the following <xref:System.Xml.XPath.XPathResultType> enumeration values representing the W3C XPath return types.</span></span>  
  
- <xref:System.Xml.XPath.XPathResultType.Any>  
  
- <xref:System.Xml.XPath.XPathResultType.Boolean>  
  
- <xref:System.Xml.XPath.XPathResultType.Error>  
  
- <xref:System.Xml.XPath.XPathResultType.Navigator>  
  
- <xref:System.Xml.XPath.XPathResultType.NodeSet>  
  
- <xref:System.Xml.XPath.XPathResultType.Number>  
  
- <xref:System.Xml.XPath.XPathResultType.String>  
  
 <span data-ttu-id="ff7fe-124">次の例は、<xref:System.Xml.XPath.XPathExpression> オブジェクトを使用して、`books.xml` ファイルから 1 つの数値とノード セットを返します。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-124">The following example uses the <xref:System.Xml.XPath.XPathExpression> object to return a number and a node set from the `books.xml` file.</span></span> <span data-ttu-id="ff7fe-125">各 <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> オブジェクトの <xref:System.Xml.XPath.XPathExpression> プロパティと共に、<xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> および <xref:System.Xml.XPath.XPathNavigator.Select%2A> メソッドからの結果がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-125">The <xref:System.Xml.XPath.XPathExpression.ReturnType%2A> property of each <xref:System.Xml.XPath.XPathExpression> object as well as the results from the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> and <xref:System.Xml.XPath.XPathNavigator.Select%2A> methods are written to the console.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Returns a number.  
Dim query1 As XPathExpression = navigator.Compile("bookstore/book/price/text()*10")  
Console.WriteLine(query1.ReturnType)  
  
Dim number As Double = CType(navigator.Evaluate(query1), Double)  
Console.WriteLine(number)  
  
' Returns a node set.  
Dim query2 As XPathExpression = navigator.Compile("bookstore/book/price")  
Console.WriteLine(query2.ReturnType)  
  
Dim nodes As XPathNodeIterator = navigator.Select(query2)  
nodes.MoveNext()  
Console.WriteLine(nodes.Current.Value)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Returns a number.  
XPathExpression query1 = navigator.Compile("bookstore/book/price/text()*10");  
Console.WriteLine(query1.ReturnType);  
  
Double number = (Double)navigator.Evaluate(query1);  
Console.WriteLine(number);  
  
// Returns a node set.  
XPathExpression query2 = navigator.Compile("bookstore/book/price");  
Console.WriteLine(query2.ReturnType);  
  
XPathNodeIterator nodes = navigator.Select(query2);  
nodes.MoveNext();  
Console.WriteLine(nodes.Current.Value);  
```  
  
 <span data-ttu-id="ff7fe-126">この例は、`books.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-126">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="higher-performance-xpath-expressions"></a><span data-ttu-id="ff7fe-127">XPath 式のパフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="ff7fe-127">Higher Performance XPath Expressions</span></span>  

 <span data-ttu-id="ff7fe-128">パフォーマンスを向上させるには、クエリで可能な限り特定した XPath 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-128">For better performance, use the most specific XPath expression possible in your queries.</span></span> <span data-ttu-id="ff7fe-129">たとえば、`book` が `bookstore` ノードの子ノードであり `bookstore` ノードが XML ドキュメントで最上位のノードの場合は、XPath 式 `/bookstore/book` を使用すると `//book` を使用した場合より高速です。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-129">For example, if the `book` node is a child node of the `bookstore` node and the `bookstore` node is the top-most element in an XML document, using the XPath expression `/bookstore/book` is faster than using `//book`.</span></span> <span data-ttu-id="ff7fe-130">`//book` XPath 式は、XML ツリーのすべてのノードをスキャンしてノードとの一致を調べます。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-130">The `//book` XPath expression will scan every node in the XML tree to identify matching nodes.</span></span>  
  
 <span data-ttu-id="ff7fe-131">さらに、選択基準が単純な場合は <xref:System.Xml.XPath.XPathNavigator> クラスが提供するノード セット ナビゲーション メソッドは、<xref:System.Xml.XPath.XPathNavigator> クラスが提供する選択メソッドに比べてパフォーマンスが高いことがあります。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-131">Additionally, using the node set navigation methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class may result in improved performance over the selection methods supplied by the <xref:System.Xml.XPath.XPathNavigator> class in cases where your selection criteria are simple.</span></span> <span data-ttu-id="ff7fe-132">たとえば、現在のノードの最初の子を選択する場合、<xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> メソッドを使用した方が `child::*[1]` XPath 式と <xref:System.Xml.XPath.XPathNavigator.Select%2A> メソッドを使用するよりも高速です。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-132">For example, if you need to select the first child of the current node, it is faster to use the <xref:System.Xml.XPath.XPathNavigator.MoveToFirst%2A> method than to use the `child::*[1]` XPath expression and the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method.</span></span>  
  
 <span data-ttu-id="ff7fe-133"><xref:System.Xml.XPath.XPathNavigator> クラスのノード セット ナビゲーション メソッドの詳細については「[XPathNavigator を使用するノード セットのナビゲーション](node-set-navigation-using-xpathnavigator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ff7fe-133">For more information about the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class, see [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff7fe-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff7fe-134">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="ff7fe-135">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="ff7fe-135">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="ff7fe-136">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="ff7fe-136">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="ff7fe-137">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="ff7fe-137">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="ff7fe-138">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="ff7fe-138">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="ff7fe-139">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="ff7fe-139">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="ff7fe-140">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="ff7fe-140">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
