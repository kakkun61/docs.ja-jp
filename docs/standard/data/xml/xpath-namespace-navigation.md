---
title: XPath 名前空間のナビゲーション
ms.date: 03/30/2017
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: d5350f0c8f73c5efb0f7d9e4c492a841b4978c36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720894"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="2dedf-102">XPath 名前空間のナビゲーション</span><span class="sxs-lookup"><span data-stu-id="2dedf-102">XPath Namespace Navigation</span></span>

<span data-ttu-id="2dedf-103">XML ドキュメントで XPath クエリを使用するには、XML 名前空間およびそれらの名前空間に含まれる要素を、正しくアドレス指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2dedf-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="2dedf-104">名前空間は、名前が複数のコンテキストで使用される場合に生じる可能性がある、あいまいさを防ぎます。たとえば、`ID` という名前は、XML ドキュメントの複数の異なる要素に関連付けられた複数の ID を参照する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2dedf-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="2dedf-105">名前空間の構文では、XML ドキュメントの各要素を識別する、URI、名前、およびプレフィックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="2dedf-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="2dedf-106">このトピックの例では、<xref:System.Xml.XPath.XPathNavigator> で XML ドキュメントをナビゲーションする際のプレフィックスの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2dedf-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="2dedf-107">名前空間と構文の詳細については、「[XML ファイル: XML 名前空間入門](/previous-versions/dotnet/articles/bb986013(v=msdn.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2dedf-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="2dedf-108">名前空間の宣言</span><span class="sxs-lookup"><span data-stu-id="2dedf-108">Namespace Declarations</span></span>  

 <span data-ttu-id="2dedf-109">名前空間の宣言によって、<xref:System.Xml.XPath.XPathNavigator> のインスタンスを使用する際に、XML ドキュメントの各要素の識別とアドレス指定が可能になります。</span><span class="sxs-lookup"><span data-stu-id="2dedf-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="2dedf-110">名前空間のプレフィックスでは、アドレス名前空間用の短い構文が指定されます。</span><span class="sxs-lookup"><span data-stu-id="2dedf-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="2dedf-111">プレフィックスは、`<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` という形式で定義されます。この構文では、プレフィックス "`e`" が、名前空間の正式な URI の省略形になります。</span><span class="sxs-lookup"><span data-stu-id="2dedf-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="2dedf-112">`Body` という構文を使用して、`Envelope` 要素を `e:Body` 名前空間のメンバーとして識別できます。</span><span class="sxs-lookup"><span data-stu-id="2dedf-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="2dedf-113">次の XML ドキュメントは、次のセクションで示すナビゲーション例で `response.xml` として参照されます。</span><span class="sxs-lookup"><span data-stu-id="2dedf-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="2dedf-114">名前空間プレフィックスによるナビゲーション</span><span class="sxs-lookup"><span data-stu-id="2dedf-114">Navigation by Namespace Prefix</span></span>  

 <span data-ttu-id="2dedf-115">このセクションで示すコードでは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトと <xref:System.Xml.XmlNamespaceManager> オブジェクトを使用して、前のセクションで示した XML ドキュメントの `Search` 要素を選択します。</span><span class="sxs-lookup"><span data-stu-id="2dedf-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="2dedf-116">`xpath` クエリには、パス内の各要素の名前空間プレフィックスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2dedf-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="2dedf-117">各要素が含まれている名前空間の正確な ID を指定することによって、`Search` メソッドで <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 要素に正しく移動できます。</span><span class="sxs-lookup"><span data-stu-id="2dedf-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 <span data-ttu-id="2dedf-118">名前空間で完全修飾された名前を使用するのは、利便性のためだけではありません。</span><span class="sxs-lookup"><span data-stu-id="2dedf-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="2dedf-119">前に示したドキュメント定義とコードでは、要素名を完全修飾せずにナビゲーションすると例外がスローされることがわかります。</span><span class="sxs-lookup"><span data-stu-id="2dedf-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="2dedf-120">たとえば、要素の定義が `<Search xmlns="http://schemas.microsoft.com/v1/Search">` で、クエリ文字列が `xpath = "/s:Envelope/s:Body/Search";` の場合、`Search` 要素に名前空間プレフィックスがないので、`null` 要素ではなく `Search` が返されます。</span><span class="sxs-lookup"><span data-stu-id="2dedf-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dedf-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="2dedf-121">See also</span></span>

- [<span data-ttu-id="2dedf-122">XPathNavigator による XML データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="2dedf-122">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="2dedf-123">XPathNavigator を使用した XML データの選択、評価、および照合</span><span class="sxs-lookup"><span data-stu-id="2dedf-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
