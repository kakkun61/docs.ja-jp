---
title: XslTransform への XmlDocument の入力
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97115892-410a-4657-ab47-1e14dfba73f8
ms.openlocfilehash: 0afee2d706b95117971c02b57a5570427e0fbd3d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827556"
---
# <a name="xmldocument-input-to-xsltransform"></a><span data-ttu-id="cd8ab-102">XslTransform への XmlDocument の入力</span><span class="sxs-lookup"><span data-stu-id="cd8ab-102">XmlDocument Input to XslTransform</span></span>
<span data-ttu-id="cd8ab-103"><xref:System.Xml.XmlDocument> クラスは、XML ドキュメントの編集機能を持っています。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-103">The <xref:System.Xml.XmlDocument> class provides editing capabilities for an XML document.</span></span> <span data-ttu-id="cd8ab-104">XML を <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに送信する前に編集または変更する必要がある場合は、XML を <xref:System.Xml.XmlDocument> に読み込み、編集し、<xref:System.Xml.Xsl.XslTransform> に送信します。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-104">If the XML needs to be edited or modified before being sent to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method, load the XML into an <xref:System.Xml.XmlDocument>, edit it, and send it in to the <xref:System.Xml.Xsl.XslTransform>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd8ab-105">.NET Framework 2.0 では <xref:System.Xml.Xsl.XslTransform> クラスが廃止されています。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="cd8ab-106"><xref:System.Xml.Xsl.XslCompiledTransform> クラスを使用して XSLT (Extensible Stylesheet Language for Transformations) 変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="cd8ab-107">詳しくは、「[XslCompiledTransform クラスの使用](using-the-xslcompiledtransform-class.md)」および「[XslTransform クラスからの移行](migrating-from-the-xsltransform-class.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="cd8ab-108"><xref:System.Xml.XmlDocument> は <xref:System.Xml.XPath.IXPathNavigable> インターフェイスを実装しているため、ドキュメントを編集した後で <xref:System.Xml.Xsl.XslTransform.Transform%2A> メソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-108">The <xref:System.Xml.XmlDocument> implements the <xref:System.Xml.XPath.IXPathNavigable> interface, so the document can be passed to the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method after editing.</span></span>  
  
 <span data-ttu-id="cd8ab-109"><xref:System.Xml.XmlDocument> は編集機能を持っているのに対して、<xref:System.Xml.XmlDocument> は内部ストレージを利用して XPath (XML Path Language) クエリに最適化されているため、<xref:System.Xml.XPath.XPathDocument> クラスを変換への入力として使用する方法は、<xref:System.Xml.XPath.XPathDocument> を XSLT (Extensible Stylesheet Language for Transformations) 変換に使用する方法より動作が遅くなります。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-109">Due to the editing capability of the <xref:System.Xml.XmlDocument>, using the <xref:System.Xml.XmlDocument> class as input to a transformation is slower than using an <xref:System.Xml.XPath.XPathDocument> for the Extensible Stylesheet Language for Transformations (XSLT) transformations, as the <xref:System.Xml.XPath.XPathDocument> is optimized for XML Path Language (XPath) queries due to the internal storage.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd8ab-110">例</span><span class="sxs-lookup"><span data-stu-id="cd8ab-110">Example</span></span>  
 <span data-ttu-id="cd8ab-111"><xref:System.Xml.XmlDocument> を <xref:System.Xml.Xsl.XslTransform> に渡し、出力を <xref:System.Xml.XmlReader> に送信するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cd8ab-111">The following code example shows how an <xref:System.Xml.XmlDocument> can be supplied to the <xref:System.Xml.Xsl.XslTransform>, with the output sent to an <xref:System.Xml.XmlReader>.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.Load("books.xml")  
Dim trans As XslTransform = new XslTransform()  
trans.Load("book.xsl")  
Dim rdr As XmlReader = trans.Transform(doc, Nothing, Nothing)  
while (rdr.Read())  
end while  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
XslTransform trans = new XslTransform();  
trans.Load("book.xsl");  
XmlReader rdr = trans.Transform(doc, null, null);  
while (rdr.Read()) {}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd8ab-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd8ab-112">See also</span></span>

- <xref:System.Xml.XmlDocument>
- [<span data-ttu-id="cd8ab-113">XslTransform クラスを使用した XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="cd8ab-113">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)
- [<span data-ttu-id="cd8ab-114">XslTransform クラスによる XSLT プロセッサの実装</span><span class="sxs-lookup"><span data-stu-id="cd8ab-114">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
- [<span data-ttu-id="cd8ab-115">変換における XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="cd8ab-115">XPathNavigator in Transformations</span></span>](xpathnavigator-in-transformations.md)
- [<span data-ttu-id="cd8ab-116">変換における XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="cd8ab-116">XPathNodeIterator in Transformations</span></span>](xpathnodeiterator-in-transformations.md)
- [<span data-ttu-id="cd8ab-117">XslTransform への XPathDocument の入力</span><span class="sxs-lookup"><span data-stu-id="cd8ab-117">XPathDocument Input to XslTransform</span></span>](xpathdocument-input-to-xsltransform.md)
- [<span data-ttu-id="cd8ab-118">XslTransform への XmlDataDocument の入力</span><span class="sxs-lookup"><span data-stu-id="cd8ab-118">XmlDataDocument Input to XslTransform</span></span>](xmldatadocument-input-to-xsltransform.md)
