---
title: XML ドキュメントでの名前空間の管理
description: XML ドキュメントで名前空間を管理する方法について説明します。 XML 名前空間は、XML ドキュメントの要素名と属性名をカスタムの定義済み URI に関連付けます。
ms.date: 03/30/2017
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 120493de430c2372f3f71d1d1498ba880feda3d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720153"
---
# <a name="managing-namespaces-in-an-xml-document"></a><span data-ttu-id="fc151-104">XML ドキュメントでの名前空間の管理</span><span class="sxs-lookup"><span data-stu-id="fc151-104">Managing Namespaces in an XML Document</span></span>

<span data-ttu-id="fc151-105">XML 名前空間は、XML ドキュメントの要素名と属性名をカスタムの定義済み URI に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="fc151-105">XML namespaces associate element and attribute names in an XML document with custom and predefined URIs.</span></span> <span data-ttu-id="fc151-106">この関係を作成するには、名前空間 URI のプレフィックスを定義し、そのプレフィックスを使用して XML データ内の要素名と属性名を修飾します。</span><span class="sxs-lookup"><span data-stu-id="fc151-106">To create these associations, you define prefixes for namespace URIs, and use those prefixes to qualify element and attribute names in XML data.</span></span> <span data-ttu-id="fc151-107">名前空間は要素名や属性名の競合を防ぎ、同じ名前の要素や属性を個別に処理および評価できるようにします。</span><span class="sxs-lookup"><span data-stu-id="fc151-107">Namespaces prevent element and attribute name collisions, and enable elements and attributes of the same name to be handled and validated differently.</span></span>  
  
<a name="declare"></a>

## <a name="declaring-namespaces"></a><span data-ttu-id="fc151-108">名前空間の宣言</span><span class="sxs-lookup"><span data-stu-id="fc151-108">Declaring namespaces</span></span>  

 <span data-ttu-id="fc151-109">要素で名前空間を宣言するには、`xmlns:` 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc151-109">To declare a namespace on an element, you use the `xmlns:` attribute:</span></span>  
  
 `xmlns:<name>=<"uri">`  
  
 <span data-ttu-id="fc151-110">ここで、`<name>` は名前空間プレフィックスで、`<"uri">` は名前空間を識別する URI です。</span><span class="sxs-lookup"><span data-stu-id="fc151-110">where `<name>` is the namespace prefix and `<"uri">` is the URI that identifies the namespace.</span></span> <span data-ttu-id="fc151-111">プレフィックスを宣言したら、そのプレフィックスを使用して XML ドキュメント内の要素と属性を修飾し、名前空間 URI と関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="fc151-111">After you declare the prefix, you can use it to qualify elements and attributes in an XML document and associate them with the namespace URI.</span></span> <span data-ttu-id="fc151-112">名前空間プレフィックスはドキュメント全体を通じて使用されるため、短くする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fc151-112">Because the namespace prefix is used throughout a document, it should be short in length.</span></span>  
  
 <span data-ttu-id="fc151-113">この例では、2 つの `BOOK` 要素を定義しています。</span><span class="sxs-lookup"><span data-stu-id="fc151-113">This example defines two `BOOK` elements.</span></span> <span data-ttu-id="fc151-114">1 つ目の要素はプレフィックス `mybook` で修飾され、2 つ目の要素はプレフィックス `bb` で修飾されています。</span><span class="sxs-lookup"><span data-stu-id="fc151-114">The first element is qualified by the prefix, `mybook`, and the second element is qualified by the prefix, `bb`.</span></span> <span data-ttu-id="fc151-115">プレフィックスはそれぞれ、異なる名前空間 URI に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="fc151-115">Each prefix is associated with a different namespace URI:</span></span>  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines" />
</mybook>
```  
  
 <span data-ttu-id="fc151-116">ある要素が特定の名前空間の一部であることを指定するには、名前空間プレフィックスをその要素に追加します。</span><span class="sxs-lookup"><span data-stu-id="fc151-116">To signify that an element is a part of a particular namespace, add the namespace prefix to it.</span></span> <span data-ttu-id="fc151-117">たとえば、`Author` 要素が `mybook` 名前空間に属する場合は、`<mybook:Author>` として宣言されます。</span><span class="sxs-lookup"><span data-stu-id="fc151-117">For example, if a `Author` element belongs to the `mybook` namespace, it is declared as `<mybook:Author>`.</span></span>  
  
<a name="scope"></a>

## <a name="declaration-scope"></a><span data-ttu-id="fc151-118">宣言のスコープ</span><span class="sxs-lookup"><span data-stu-id="fc151-118">Declaration scope</span></span>  

 <span data-ttu-id="fc151-119">名前空間の有効な範囲は、宣言された位置から、宣言された要素の最後までです。</span><span class="sxs-lookup"><span data-stu-id="fc151-119">A namespace is effective from its point of declaration until the end of the element it was declared in.</span></span> <span data-ttu-id="fc151-120">この例では、`BOOK` 要素で定義されている名前空間は、`BOOK` 要素など、`Publisher` 要素の外側にある要素には適用されません。</span><span class="sxs-lookup"><span data-stu-id="fc151-120">In this example, the namespace defined in the `BOOK` element doesn't apply to elements outside the `BOOK` element, such as the `Publisher` element:</span></span>  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 <span data-ttu-id="fc151-121">名前空間は使用する前に宣言されている必要がありますが、必ずしも XML ドキュメントの先頭に示されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fc151-121">A namespace must be declared before it can be used, but it doesn't have to appear at the top of the XML document.</span></span>  
  
 <span data-ttu-id="fc151-122">1 つの XML ドキュメントで複数の名前空間を使用する場合は、そのうちの 1 つを既定の名前空間として定義することで、ドキュメントの外観を見やすくできます。</span><span class="sxs-lookup"><span data-stu-id="fc151-122">When you use multiple namespaces in an XML document, you can define one namespace as the default namespace to create a cleaner looking document.</span></span> <span data-ttu-id="fc151-123">既定の名前空間はルート要素で宣言され、ドキュメント内の修飾されていないすべての要素に適用されます。</span><span class="sxs-lookup"><span data-stu-id="fc151-123">The default namespace is declared in the root element and applies to all unqualified elements in the document.</span></span> <span data-ttu-id="fc151-124">既定の名前空間は要素にのみ適用されます。属性には適用されません。</span><span class="sxs-lookup"><span data-stu-id="fc151-124">Default namespaces apply to elements only, not to attributes.</span></span>  
  
 <span data-ttu-id="fc151-125">既定の名前空間を使用するには、要素の宣言でプレフィックスとコロンを省略します。</span><span class="sxs-lookup"><span data-stu-id="fc151-125">To use the default namespace, omit the prefix and the colon from the declaration on the element:</span></span>  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
...
</BOOK>
```  
  
## <a name="managing-namespaces"></a><span data-ttu-id="fc151-126">名前空間の管理</span><span class="sxs-lookup"><span data-stu-id="fc151-126">Managing namespaces</span></span>  

 <span data-ttu-id="fc151-127"><xref:System.Xml.XmlNamespaceManager> クラスには、名前空間 URI とそのプレフィックスのコレクションが格納されます。このクラスを使用すると、コレクションで名前空間を検索、追加、および削除できます。</span><span class="sxs-lookup"><span data-stu-id="fc151-127">The <xref:System.Xml.XmlNamespaceManager> class stores a collection of namespace URIs and their prefixes, and lets you look up, add, and remove namespaces from this collection.</span></span> <span data-ttu-id="fc151-128">このクラスは、特定のコンテキストで、XML の処理のパフォーマンスを向上させるために必要です。</span><span class="sxs-lookup"><span data-stu-id="fc151-128">In certain contexts, this class is required for better XML processing performance.</span></span> <span data-ttu-id="fc151-129">たとえば、XPath をサポートするには、<xref:System.Xml.Xsl.XsltContext> クラスで <xref:System.Xml.XmlNamespaceManager> を使用します。</span><span class="sxs-lookup"><span data-stu-id="fc151-129">For example, the <xref:System.Xml.Xsl.XsltContext> class uses <xref:System.Xml.XmlNamespaceManager> for XPath support.</span></span>  
  
 <span data-ttu-id="fc151-130">名前空間マネージャーでは名前空間の検証は一切実行されません。このマネージャーでは、プレフィックスと名前空間が既に確認され、[W3C 名前空間](https://www.w3.org/TR/REC-xml-names/)仕様に準拠していることが前提となっています。</span><span class="sxs-lookup"><span data-stu-id="fc151-130">The namespace manager doesn't perform any validation on the namespaces, but assumes that prefixes and namespaces have already been verified and conform to the [W3C Namespaces](https://www.w3.org/TR/REC-xml-names/) specification.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc151-131">[C#](../../linq/linq-xml-overview.md) および [Visual Basic](../../linq/linq-xml-overview.md) の LINQ to XML では、名前空間を管理するために <xref:System.Xml.XmlNamespaceManager> を使用しません。</span><span class="sxs-lookup"><span data-stu-id="fc151-131">LINQ TO XML in [C#](../../linq/linq-xml-overview.md) and [Visual Basic](../../linq/linq-xml-overview.md) don't use <xref:System.Xml.XmlNamespaceManager> to manage namespaces.</span></span> <span data-ttu-id="fc151-132">LINQ to XML を使用している場合の名前空間の管理については、LINQ のドキュメントにある「[XML 名前空間の使用 (C#)](../../linq/namespaces-overview.md)」および [XML 名前空間の使用 (Visual Basic)](../../linq/namespaces-overview.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc151-132">See [Working with XML Namespaces (C#)](../../linq/namespaces-overview.md) and [Working with XML Namespaces (Visual Basic)](../../linq/namespaces-overview.md) in the LINQ documentation for information about managing namespaces when using LINQ to XML.</span></span>  
  
 <span data-ttu-id="fc151-133"><xref:System.Xml.XmlNamespaceManager> クラスを使用して実行できる管理タスクと検索タスクをいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="fc151-133">Here are some of the management and lookup tasks you can perform with the <xref:System.Xml.XmlNamespaceManager> class.</span></span> <span data-ttu-id="fc151-134">使用例を含む詳細については、各メソッドまたはプロパティのリファレンス ページへのリンクをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="fc151-134">For more information and examples, follow the links to the reference page for each method or property.</span></span>  
  
|<span data-ttu-id="fc151-135">終了</span><span class="sxs-lookup"><span data-stu-id="fc151-135">To</span></span>|<span data-ttu-id="fc151-136">使用</span><span class="sxs-lookup"><span data-stu-id="fc151-136">Use</span></span>|  
|--------|---------|  
|<span data-ttu-id="fc151-137">名前空間を追加する</span><span class="sxs-lookup"><span data-stu-id="fc151-137">Add a namespace</span></span>|<span data-ttu-id="fc151-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="fc151-138"><xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> method</span></span>|  
|<span data-ttu-id="fc151-139">名前空間を削除する</span><span class="sxs-lookup"><span data-stu-id="fc151-139">Remove a namespace</span></span>|<span data-ttu-id="fc151-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="fc151-140"><xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> method</span></span>|  
|<span data-ttu-id="fc151-141">既定の名前空間の URI を検索する</span><span class="sxs-lookup"><span data-stu-id="fc151-141">Find the URI for the default namespace</span></span>|<span data-ttu-id="fc151-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> プロパティ</span><span class="sxs-lookup"><span data-stu-id="fc151-142"><xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> property</span></span>|  
|<span data-ttu-id="fc151-143">名前空間プレフィックスの URI を検索する</span><span class="sxs-lookup"><span data-stu-id="fc151-143">Find the URI for a namespace prefix</span></span>|<span data-ttu-id="fc151-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="fc151-144"><xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> method</span></span>|  
|<span data-ttu-id="fc151-145">名前空間 URI のプレフィックスを検索する</span><span class="sxs-lookup"><span data-stu-id="fc151-145">Find the prefix for a namespace URI</span></span>|<span data-ttu-id="fc151-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="fc151-146"><xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> method</span></span>|  
|<span data-ttu-id="fc151-147">現在のノードの名前空間の一覧を取得する</span><span class="sxs-lookup"><span data-stu-id="fc151-147">Get a list of namespaces in the current node</span></span>|<span data-ttu-id="fc151-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="fc151-148"><xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> method</span></span>|  
|<span data-ttu-id="fc151-149">名前空間のスコープを指定する</span><span class="sxs-lookup"><span data-stu-id="fc151-149">Scope a namespace</span></span>|<span data-ttu-id="fc151-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> メソッドおよび <xref:System.Xml.XmlNamespaceManager.PopScope%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="fc151-150"><xref:System.Xml.XmlNamespaceManager.PushScope%2A> and <xref:System.Xml.XmlNamespaceManager.PopScope%2A> methods</span></span>|  
|<span data-ttu-id="fc151-151">現在のスコープ内にプレフィックスが定義されているかどうかを確認する</span><span class="sxs-lookup"><span data-stu-id="fc151-151">Check whether a prefix is defined in the current scope</span></span>|<span data-ttu-id="fc151-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> メソッド</span><span class="sxs-lookup"><span data-stu-id="fc151-152"><xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> method</span></span>|  
|<span data-ttu-id="fc151-153">プレフィックスおよび URI を検索するときに使用する名前テーブルを取得する</span><span class="sxs-lookup"><span data-stu-id="fc151-153">Get the name table used to look up prefixes and URIs</span></span>|<span data-ttu-id="fc151-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> プロパティ</span><span class="sxs-lookup"><span data-stu-id="fc151-154"><xref:System.Xml.XmlNamespaceManager.NameTable%2A> property</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc151-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc151-155">See also</span></span>

- <xref:System.Xml.XmlNamespaceManager>
- [<span data-ttu-id="fc151-156">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="fc151-156">XML Documents and Data</span></span>](index.md)
