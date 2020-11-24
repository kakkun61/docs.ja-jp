---
title: XmlNameTable によるオブジェクトの比較
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 1e47bee50f7fa51df82bb37ed3049765f8f360d2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830078"
---
# <a name="object-comparison-using-xmlnametable"></a><span data-ttu-id="40b06-102">XmlNameTable によるオブジェクトの比較</span><span class="sxs-lookup"><span data-stu-id="40b06-102">Object Comparison Using XmlNameTable</span></span>
<span data-ttu-id="40b06-103">**XmlDocuments** の作成時には、そのドキュメント用の名前テーブルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="40b06-103">**XmlDocuments**, when created, have a name table created specifically for that document.</span></span> <span data-ttu-id="40b06-104">XML がドキュメントに読み込まれるか、新しい要素または属性が作成されると、その属性名と要素名が **XmlNameTable** に格納されます。</span><span class="sxs-lookup"><span data-stu-id="40b06-104">When XML is loaded into the document, or new elements or attributes are created, the attribute and element names are put into the **XmlNameTable**.</span></span> <span data-ttu-id="40b06-105">別のドキュメントからの既存の **NameTable** を使用して **XmlDocument** を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="40b06-105">You can also create an **XmlDocument** using an existing **NameTable** from another document.</span></span> <span data-ttu-id="40b06-106">**XmlNameTable** パラメーターをとるコンストラクターを使用して **XmlDocuments** を作成すると、ドキュメントは、その **XmlNameTable** に既に保存されているノード名、名前空間、プレフィックスにアクセスするようになります。</span><span class="sxs-lookup"><span data-stu-id="40b06-106">When **XmlDocuments** are created with the constructor that takes an **XmlNameTable** parameter, the document has access to the node names, namespaces, and prefixes already stored in the **XmlNameTable**.</span></span> <span data-ttu-id="40b06-107">どのような方法で名前テーブルと名前が読み込まれたとしても、いったんテーブルに名前が格納されると、文字列比較によってではなく、オブジェクト比較を利用して高速に名前を比較できます。</span><span class="sxs-lookup"><span data-stu-id="40b06-107">Regardless of how the name table is loaded with names, once the names are stored in the table, names can be compared quickly using object comparison instead of string comparison.</span></span> <span data-ttu-id="40b06-108"><xref:System.Xml.NameTable.Add%2A> を使用して、名前テーブルに文字列を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="40b06-108">Strings can also be added to the name table using the <xref:System.Xml.NameTable.Add%2A>.</span></span> <span data-ttu-id="40b06-109">名前テーブルを作成し、そのテーブルに **MyString** という文字列を追加するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="40b06-109">The following code sample shows a name table being created and the string **MyString** being added to the table.</span></span> <span data-ttu-id="40b06-110">その後、そのテーブルを使用して **XmlDocument** を作成し、**Myfile.xml** の要素名と属性名を既存の名前テーブルに追加します。</span><span class="sxs-lookup"><span data-stu-id="40b06-110">After that, an **XmlDocument** is created using that table, and the element and attribute names in **Myfile.xml** are added to the existing name table.</span></span>  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 <span data-ttu-id="40b06-111">ドキュメントを作成し、ドキュメントに 2 つの新しい要素を追加し、それらの要素をドキュメントの名前テーブルにも追加して、名前のオブジェクト比較を実行するコード サンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="40b06-111">The following code example shows the creation of a document, two new elements being added to the document, which also adds them to the document name table, and the object comparison on the names.</span></span>  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 <span data-ttu-id="40b06-112">上記のように 2 つのドキュメント間で名前テーブルが渡される状況は、同じタイプのドキュメントを繰り返し処理する場合によく発生します。たとえば、XML スキーマ定義言語 (XSD) スキーマまたはドキュメント型定義 (DTD) に準拠し、同じ文字列が繰り返し使われる発注ドキュメントを e コマース サイトで処理する場合などです。</span><span class="sxs-lookup"><span data-stu-id="40b06-112">The above scenario of a name table passed between two documents is typical when the same type of document is being processed repeatedly, such as order documents at an ecommerce site, which conform to an XML Schema definition language (XSD) schema or document type definition (DTD) and the same strings are repeated.</span></span> <span data-ttu-id="40b06-113">このような場合は、同じ要素名が複数のドキュメントに現れるため、同じ名前テーブルを使用することによってパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="40b06-113">Using the same name table gives a performance improvement, as the same element name occurs in multiple documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40b06-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="40b06-114">See also</span></span>

- [<span data-ttu-id="40b06-115">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="40b06-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
