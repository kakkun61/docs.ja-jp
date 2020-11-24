---
title: XPath ナビゲーションによるノードの選択
description: .NET で XML ノードを選択する方法について説明します。 XML Path Language (XPath) ナビゲーションを使用して DOM 情報を照会できる、ドキュメント オブジェクト モデル (DOM) メソッドを使用します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e4450dc-56b3-472b-b467-32f5694f83ad
ms.openlocfilehash: b8a67d1fd508d0674d9230d4b934071a15669599
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829246"
---
# <a name="select-nodes-using-xpath-navigation"></a><span data-ttu-id="a0aee-104">XPath ナビゲーションによるノードの選択</span><span class="sxs-lookup"><span data-stu-id="a0aee-104">Select Nodes Using XPath Navigation</span></span>
<span data-ttu-id="a0aee-105">XML ドキュメント オブジェクト モデル (DOM) には、DOM 内の情報を照会するための XPath (XML Path Language) ナビゲーションに使用できるメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0aee-105">The XML Document Object Model (DOM) contains methods that allow you to use XML Path Language (XPath) navigation to query information in the DOM.</span></span> <span data-ttu-id="a0aee-106">XPath を使用すると、特定の単一ノードを見つけたり、条件に一致するすべてのノードを検索したりできます。</span><span class="sxs-lookup"><span data-stu-id="a0aee-106">You can use XPath to find a single, specific node or to find all nodes that match some criteria.</span></span>  
  
## <a name="xpath-select-methods"></a><span data-ttu-id="a0aee-107">XPath の選択メソッド</span><span class="sxs-lookup"><span data-stu-id="a0aee-107">XPath Select Methods</span></span>  
 <span data-ttu-id="a0aee-108">DOM クラスは、XPath による選択に、<xref:System.Xml.XmlNode.SelectSingleNode%2A> および <xref:System.Xml.XmlNode.SelectNodes%2A> という 2 つのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="a0aee-108">The DOM classes provide two methods for XPath selection: the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method and the <xref:System.Xml.XmlNode.SelectNodes%2A> method.</span></span> <span data-ttu-id="a0aee-109"><xref:System.Xml.XmlNode.SelectSingleNode%2A> メソッドは、選択基準に一致した最初のノードを返します。</span><span class="sxs-lookup"><span data-stu-id="a0aee-109">The <xref:System.Xml.XmlNode.SelectSingleNode%2A> method returns the first node that matches the selection criteria.</span></span> <span data-ttu-id="a0aee-110"><xref:System.Xml.XmlNode.SelectNodes%2A> メソッドは、一致したノードを含む <xref:System.Xml.XmlNodeList> を返します。</span><span class="sxs-lookup"><span data-stu-id="a0aee-110">The <xref:System.Xml.XmlNode.SelectNodes%2A> method returns an <xref:System.Xml.XmlNodeList> that contains the matching nodes.</span></span>  
  
 <span data-ttu-id="a0aee-111">次の例では、<xref:System.Xml.XmlNode.SelectSingleNode%2A> メソッドを使用して、著者の姓が指定した条件と一致する最初の `book` ノードを選択しています。</span><span class="sxs-lookup"><span data-stu-id="a0aee-111">The following example uses the <xref:System.Xml.XmlNode.SelectSingleNode%2A> method to select the first `book` node in which the author's last name meets the specified criteria.</span></span> <span data-ttu-id="a0aee-112">bookstore.xml ファイル (このトピックの最後にあります) を入力ファイルとして使用します。</span><span class="sxs-lookup"><span data-stu-id="a0aee-112">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select and display the first node in which the author's
' last name is Kingsolver.  
Dim node As XmlNode = root.SelectSingleNode( _  
     "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr)  
Console.WriteLine(node.InnerXml)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select and display the first node in which the author's
// last name is Kingsolver.  
XmlNode node = root.SelectSingleNode(  
    "descendant::bk:book[bk:author/bk:last-name='Kingsolver']", nsmgr);  
Console.WriteLine(node.InnerXml);  
```  
  
 <span data-ttu-id="a0aee-113">次の例では、<xref:System.Xml.XmlNode.SelectNodes%2A> メソッドを使用して、指定した値より高い価格の book ノードをすべて選択しています。</span><span class="sxs-lookup"><span data-stu-id="a0aee-113">The next example uses the <xref:System.Xml.XmlNode.SelectNodes%2A> method to select all the book nodes in which the price is greater than a specified amount.</span></span> <span data-ttu-id="a0aee-114">その後、選択されたリストに含まれる各書籍の価格を、プログラムで 10% 安くしています。</span><span class="sxs-lookup"><span data-stu-id="a0aee-114">The price for each book in the selected list is then programmatically reduced by ten percent.</span></span> <span data-ttu-id="a0aee-115">最後に、更新したファイルをコンソールに書き出します。</span><span class="sxs-lookup"><span data-stu-id="a0aee-115">Finally, the updated file is written to the console.</span></span> <span data-ttu-id="a0aee-116">bookstore.xml ファイル (このトピックの最後にあります) を入力ファイルとして使用します。</span><span class="sxs-lookup"><span data-stu-id="a0aee-116">The bookstore.xml file (which is provided at the end of this topic) is used as the input file.</span></span>  
  
```vb  
' Load the document and set the root element.  
Dim doc As New XmlDocument()  
doc.Load("bookstore.xml")  
Dim root As XmlNode = doc.DocumentElement  
  
' Add the namespace.  
Dim nsmgr As New XmlNamespaceManager(doc.NameTable)  
nsmgr.AddNamespace("bk", "urn:newbooks-schema")  
  
' Select all nodes where the book price is greater than 10.00.  
Dim nodeList As XmlNodeList = root.SelectNodes( _  
     "descendant::bk:book[bk:price>10.00]", nsmgr)  
For Each book As XmlNode In nodeList  
     Dim price As Double  
     price = Math.Round(Convert.ToSingle( _  
          book.LastChild.InnerText) * 0.9, 2)  
     book.LastChild.InnerText = price.ToString()  
Next  
  
' Display the updated document.  
doc.Save(Console.Out)  
```  
  
```csharp  
// Load the document and set the root element.  
XmlDocument doc = new XmlDocument();  
doc.Load("bookstore.xml");  
XmlNode root = doc.DocumentElement;  
  
// Add the namespace.  
XmlNamespaceManager nsmgr = new XmlNamespaceManager(doc.NameTable);  
nsmgr.AddNamespace("bk", "urn:newbooks-schema");  
  
// Select all nodes where the book price is greater than 10.00.  
XmlNodeList nodeList = root.SelectNodes(  
     "descendant::bk:book[bk:price>10.00]", nsmgr);  
foreach (XmlNode book in nodeList)  
{  
     // Discount prices by 10%.  
     double price;  
     price = Math.Round(Convert.ToSingle(  
          book.LastChild.InnerText) * 0.9, 2);  
     book.LastChild.InnerText = price.ToString();  
}  
  
// Display the updated document.  
doc.Save(Console.Out);  
```  
  
 <span data-ttu-id="a0aee-117">上の例で、XPath クエリはドキュメント要素から開始されます。</span><span class="sxs-lookup"><span data-stu-id="a0aee-117">The examples above start the XPath query at the document element.</span></span> <span data-ttu-id="a0aee-118">XPath クエリの始点を設定すると、コンテキスト ノードが設定され、XPath クエリの開始点になります。</span><span class="sxs-lookup"><span data-stu-id="a0aee-118">Setting the starting point for the XPath query sets the context node, which is the starting point for the XPath query.</span></span> <span data-ttu-id="a0aee-119">ドキュメント要素からではなく、ドキュメント要素の最初の子から開始するには、次のように選択ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="a0aee-119">If you do not want to start at the document element, but want to start from the first child of the document element, you can code the select statement as follows:</span></span>  
  
```vb  
doc.DocumentElement.FirstChild.SelectNodes(. . . )  
```  
  
```csharp  
this doc.DocumentElement.FirstChild.SelectNodes(. . .);  
```  
  
 <span data-ttu-id="a0aee-120">すべての <xref:System.Xml.XmlNodeList> オブジェクトは、元のドキュメントに同期されます。</span><span class="sxs-lookup"><span data-stu-id="a0aee-120">All <xref:System.Xml.XmlNodeList> objects are synchronized with the underlying document.</span></span> <span data-ttu-id="a0aee-121">そのため、ノード リストを反復処理してノードの値を変更すると、そのノードは元のドキュメントにおいても更新されます。</span><span class="sxs-lookup"><span data-stu-id="a0aee-121">Therefore, if you iterate through the node list and modify the value of a node, that node is also updated in the document it came from.</span></span> <span data-ttu-id="a0aee-122">前の例で、選択した <xref:System.Xml.XmlNodeList> でノードが変更されると、基になっているドキュメントも変更されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a0aee-122">Notice in the previous example that when a node is modified in the selected <xref:System.Xml.XmlNodeList> the underlying document is also modified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0aee-123">元のドキュメントが変更された場合は、選択を再実行するのが適切です。</span><span class="sxs-lookup"><span data-stu-id="a0aee-123">When the underlying document is modified, it is advisable to rerun the select.</span></span> <span data-ttu-id="a0aee-124">変更されたノードが、以前はノード リストに含まれておらず、ノード リストに追加されるものであったり、ノード リストから削除されるものであったりした場合は、ノード リストの正確さは保証されなくなります。</span><span class="sxs-lookup"><span data-stu-id="a0aee-124">If the node modified is one that could cause the node to be added to the node list when it was not previously, or would now cause it to be removed from the node list, there is no guarantee that the node list is now accurate.</span></span>  
  
## <a name="namespaces-in-xpath-expressions"></a><span data-ttu-id="a0aee-125">XPath 式の名前空間</span><span class="sxs-lookup"><span data-stu-id="a0aee-125">Namespaces in XPath Expressions</span></span>  
 <span data-ttu-id="a0aee-126">XPath 式は名前空間を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="a0aee-126">XPath expressions can include namespaces.</span></span> <span data-ttu-id="a0aee-127">名前空間の解決は <xref:System.Xml.XmlNamespaceManager> を使用してサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a0aee-127">Namespace resolution is supported using the <xref:System.Xml.XmlNamespaceManager>.</span></span> <span data-ttu-id="a0aee-128">XPath 式にプレフィックスが含まれる場合は、プレフィックスと名前空間 URI のペアを <xref:System.Xml.XmlNamespaceManager> に追加して、<xref:System.Xml.XmlNamespaceManager> を <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> メソッド、または <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> メソッドに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0aee-128">If the XPath expression includes a prefix, the prefix and namespace URI pair must be added to the <xref:System.Xml.XmlNamespaceManager>, and the <xref:System.Xml.XmlNamespaceManager> is passed to the <xref:System.Xml.XmlNode.SelectNodes%28System.String%2CSystem.Xml.XmlNamespaceManager%29> or <xref:System.Xml.XmlNode.SelectSingleNode%28System.String%2CSystem.Xml.XmlNamespaceManager%29> method.</span></span> <span data-ttu-id="a0aee-129">前のコード例では、<xref:System.Xml.XmlNamespaceManager> を使用して bookstore.xml ドキュメントの名前空間を解決しています。</span><span class="sxs-lookup"><span data-stu-id="a0aee-129">Notice that the code examples above use the <xref:System.Xml.XmlNamespaceManager> to resolve the namespace of the bookstore.xml document.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0aee-130">XPath 式にプレフィックスが含まれない場合は、名前空間 URI は空の名前空間であると仮定されます。</span><span class="sxs-lookup"><span data-stu-id="a0aee-130">If the XPath expression does not include a prefix, it is assumed that the namespace Uniform Resource Identifier (URI) is the empty namespace.</span></span> <span data-ttu-id="a0aee-131">XML に既定の名前空間が含まれる場合でも、プレフィックスと名前空間 URI を <xref:System.Xml.XmlNamespaceManager> に追加する必要があります。そうしないと、ノードは選択されません。</span><span class="sxs-lookup"><span data-stu-id="a0aee-131">If your XML includes a default namespace, you must still add a prefix and namespace URI to the <xref:System.Xml.XmlNamespaceManager>; otherwise, no nodes will be selected.</span></span>  
  
#### <a name="input-file"></a><span data-ttu-id="a0aee-132">入力ファイル</span><span class="sxs-lookup"><span data-stu-id="a0aee-132">Input File</span></span>  
 <span data-ttu-id="a0aee-133">次に示すのは、このトピックの例で入力ファイルとして使用している bookstore.xml ファイルです。</span><span class="sxs-lookup"><span data-stu-id="a0aee-133">The following is the bookstore.xml file that is used as the input file in the examples in this topic:</span></span>  
  
```xml  
<?xml version='1.0'?>  
<bookstore xmlns="urn:newbooks-schema">  
  <book genre="novel" style="hardcover">  
    <title>The Handmaid's Tale</title>  
    <author>  
      <first-name>Margaret</first-name>  
      <last-name>Atwood</last-name>  
    </author>  
    <price>19.95</price>  
  </book>  
  <book genre="novel" style="other">  
    <title>The Poisonwood Bible</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="novel" style="paperback">  
    <title>The Bean Trees</title>  
    <author>  
      <first-name>Barbara</first-name>  
      <last-name>Kingsolver</last-name>  
    </author>  
    <price>5.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0aee-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0aee-134">See also</span></span>

- [<span data-ttu-id="a0aee-135">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="a0aee-135">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
