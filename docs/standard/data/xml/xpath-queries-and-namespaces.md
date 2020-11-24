---
title: XPath クエリおよび名前空間
description: XPath クエリおよび名前空間について説明します。 XPath クエリは XML ドキュメント中の名前空間を認識し、名前空間プレフィックスを使用して要素と属性名を修飾することができます。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: a97ff5afef23c361b1f675d2f07f43b3bc5df299
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818389"
---
# <a name="xpath-queries-and-namespaces"></a><span data-ttu-id="8ab66-104">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="8ab66-104">XPath Queries and Namespaces</span></span>
<span data-ttu-id="8ab66-105">XPath クエリは XML ドキュメント中の名前空間を認識し、名前空間プレフィックスを使用して要素と属性名を修飾することができます。</span><span class="sxs-lookup"><span data-stu-id="8ab66-105">XPath queries are aware of namespaces in an XML document and can use namespace prefixes to qualify element and attribute names.</span></span> <span data-ttu-id="8ab66-106">名前空間プレフィックスで要素や属性の名前を修飾すると、XPath クエリで返されるノードを特定の名前空間に属するノードだけに限定することができます。</span><span class="sxs-lookup"><span data-stu-id="8ab66-106">Qualifying element and attribute names with a namespace prefix limits the nodes returned by an XPath query to only those nodes that belong to a specific namespace.</span></span>  
  
 <span data-ttu-id="8ab66-107">たとえば、プレフィックス `books` が名前空間 `http://www.contoso.com/books` に割り当てられると、XPath クエリ `/books:books/books:book` は名前空間 `book` 内の `http://www.contoso.com/books` 要素だけを選択します。</span><span class="sxs-lookup"><span data-stu-id="8ab66-107">For example if the prefix `books` maps to the namespace `http://www.contoso.com/books`, then the following XPath query `/books:books/books:book` selects only those `book` elements in the namespace `http://www.contoso.com/books`.</span></span>  
  
## <a name="the-xmlnamespacemanager"></a><span data-ttu-id="8ab66-108">XmlNamespaceManager</span><span class="sxs-lookup"><span data-stu-id="8ab66-108">The XmlNamespaceManager</span></span>  
 <span data-ttu-id="8ab66-109">XPath クエリで名前空間を使用するために、<xref:System.Xml.IXmlNamespaceResolver> クラスに似た <xref:System.Xml.XmlNamespaceManager> インターフェイスから派生したオブジェクトが、名前空間 URI と XPath クエリに含まれるプレフィックスを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="8ab66-109">To use namespaces in an XPath query, an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface like the <xref:System.Xml.XmlNamespaceManager> class is constructed with the namespace URI and prefix to include in the XPath query.</span></span>  
  
 <span data-ttu-id="8ab66-110"><xref:System.Xml.XmlNamespaceManager> オブジェクトは次の方法でクエリで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="8ab66-110">The <xref:System.Xml.XmlNamespaceManager> object may be used in the query in each of the following ways.</span></span>  
  
- <span data-ttu-id="8ab66-111"><xref:System.Xml.XmlNamespaceManager> オブジェクトの <xref:System.Xml.XPath.XPathExpression> メソッドを使用して、<xref:System.Xml.XPath.XPathExpression.SetContext%2A> オブジェクトを既存の <xref:System.Xml.XPath.XPathExpression> オブジェクトに関連付ける。</span><span class="sxs-lookup"><span data-stu-id="8ab66-111">The <xref:System.Xml.XmlNamespaceManager> object is associated with an existing <xref:System.Xml.XPath.XPathExpression> object by using the <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method of the <xref:System.Xml.XPath.XPathExpression> object.</span></span> <span data-ttu-id="8ab66-112">静的 <xref:System.Xml.XPath.XPathExpression> メソッドを使用して、新しい <xref:System.Xml.XPath.XPathExpression.Compile%2A> オブジェクトをコンパイルすることもできます。このメソッドは XPath 式を表す文字列と <xref:System.Xml.XmlNamespaceManager> オブジェクトをパラメーターとして取り、新しい <xref:System.Xml.XPath.XPathExpression> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="8ab66-112">You may also compile a new <xref:System.Xml.XPath.XPathExpression> object using the static <xref:System.Xml.XPath.XPathExpression.Compile%2A> method which takes a string representing the XPath expression and an <xref:System.Xml.XmlNamespaceManager> object as parameters and returns a new <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
- <span data-ttu-id="8ab66-113">XPath 式を表す文字列と共に <xref:System.Xml.XmlNamespaceManager> オブジェクト自体をパラメーターとして受け入れ側の <xref:System.Xml.XPath.XPathNavigator> クラス メソッドに渡す。</span><span class="sxs-lookup"><span data-stu-id="8ab66-113">The <xref:System.Xml.XmlNamespaceManager> object itself is passed as a parameter to an accepting <xref:System.Xml.XPath.XPathNavigator> class method along with a string representing the XPath expression.</span></span>  
  
 <span data-ttu-id="8ab66-114">次は、<xref:System.Xml.XPath.XPathNavigator> インターフェイスから派生したオブジェクトをパラメーターとして受け付ける <xref:System.Xml.IXmlNamespaceResolver> クラスのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="8ab66-114">The following are the methods of the <xref:System.Xml.XPath.XPathNavigator> class that accept an object derived from the <xref:System.Xml.IXmlNamespaceResolver> interface as a parameter.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a><span data-ttu-id="8ab66-115">既定の名前空間</span><span class="sxs-lookup"><span data-stu-id="8ab66-115">The Default Namespace</span></span>  
 <span data-ttu-id="8ab66-116">次の XML ドキュメントでは、`http://www.contoso.com/books` 名前空間を宣言するために、空のプレフィックスの既定の名前空間が使用されています。</span><span class="sxs-lookup"><span data-stu-id="8ab66-116">In the XML document that follows, the default namespace with an empty prefix is used to declare the `http://www.contoso.com/books` namespace.</span></span>  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 <span data-ttu-id="8ab66-117">XPath は空のプレフィックスを `null` 名前空間として取り扱います。</span><span class="sxs-lookup"><span data-stu-id="8ab66-117">XPath treats the empty prefix as the `null` namespace.</span></span> <span data-ttu-id="8ab66-118">つまり、XPath クエリでは、名前空間に割り当てられたプレフィックスだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ab66-118">In other words, only prefixes mapped to namespaces can be used in XPath queries.</span></span> <span data-ttu-id="8ab66-119">このことは、XML ドキュメント内の名前空間に対してクエリする場合、たとえそれが既定の名前空間であっても、そのプレフィックスを定義する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8ab66-119">This means that if you want to query against a namespace in an XML document, even if it is the default namespace, you need to define a prefix for it.</span></span>  
  
 <span data-ttu-id="8ab66-120">たとえば、上記の XML ドキュメントでプレフィックスを定義しなければ、XPath クエリ `/books/book` は何も結果を返しません。</span><span class="sxs-lookup"><span data-stu-id="8ab66-120">For example, without defining a prefix for the XML document above, the XPath query `/books/book` would not return any results.</span></span>  
  
 <span data-ttu-id="8ab66-121">ドキュメントで、名前空間内にないノードと既定の名前空間内のノードに対してクエリを行う場合には、あいまいさを避けるために、プレフィックスを付加しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="8ab66-121">A prefix must be bound to prevent ambiguity when querying documents with some nodes not in a namespace, and some in a default namespace.</span></span>  
  
 <span data-ttu-id="8ab66-122">次のコードは、既定の名前空間のプレフィックスを定義し、`book` 名前空間からすべての `http://www.contoso.com/books` 要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="8ab66-122">The following code defines a prefix for the default namespace and selects all the `book` elements from the `http://www.contoso.com/books` namespace.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ab66-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ab66-123">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="8ab66-124">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8ab66-124">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="8ab66-125">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="8ab66-125">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="8ab66-126">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="8ab66-126">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="8ab66-127">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="8ab66-127">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="8ab66-128">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="8ab66-128">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="8ab66-129">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="8ab66-129">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
