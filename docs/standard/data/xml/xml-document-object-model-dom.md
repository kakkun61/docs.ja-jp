---
title: XML ドキュメント オブジェクト モデル (DOM)
ms.date: 03/30/2017
ms.assetid: b5e52844-4820-47c0-a61d-de2da33e9f54
ms.openlocfilehash: 5e7c4e62b7bb19b1ddab61f78b360fed0b6752ef
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821776"
---
# <a name="xml-document-object-model-dom"></a><span data-ttu-id="c2479-102">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="c2479-102">XML Document Object Model (DOM)</span></span>

<span data-ttu-id="c2479-103">XML ドキュメント オブジェクト モデル (DOM) クラスは、XML ドキュメントのメモリ内表現です。</span><span class="sxs-lookup"><span data-stu-id="c2479-103">The XML Document Object Model (DOM) class is an in-memory representation of an XML document.</span></span> <span data-ttu-id="c2479-104">DOM を使用すると、XML ドキュメントの読み込み、操作、および変更をプログラムから実行できます。</span><span class="sxs-lookup"><span data-stu-id="c2479-104">The DOM allows you to programmatically read, manipulate, and modify an XML document.</span></span> <span data-ttu-id="c2479-105">**XmlReader** クラスも XML を読み込めますが、非キャッシュ、前方参照専用、読み取り専用のアクセスしか実行できません。</span><span class="sxs-lookup"><span data-stu-id="c2479-105">The **XmlReader** class also reads XML; however, it provides non-cached, forward-only, read-only access.</span></span> <span data-ttu-id="c2479-106">つまり、**XmlReader** には、属性の値または要素のコンテンツを編集する機能や、ノードを挿入したり削除したりする機能はありません。</span><span class="sxs-lookup"><span data-stu-id="c2479-106">This means that there are no capabilities to edit the values of an attribute or content of an element, or the ability to insert and remove nodes with the **XmlReader**.</span></span> <span data-ttu-id="c2479-107">DOM の主な機能は編集です。</span><span class="sxs-lookup"><span data-stu-id="c2479-107">Editing is the primary function of the DOM.</span></span> <span data-ttu-id="c2479-108">XML データは、通常、メモリ上では構造的に表現されますが、実際の XML データをファイルに保存したり、別のオブジェクトから取り込む場合は、直線的な形式で格納されます。</span><span class="sxs-lookup"><span data-stu-id="c2479-108">It is the common and structured way that XML data is represented in memory, although the actual XML data is stored in a linear fashion when in a file or coming in from another object.</span></span> <span data-ttu-id="c2479-109">XML データの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c2479-109">The following is XML data.</span></span>

## <a name="input"></a><span data-ttu-id="c2479-110">入力</span><span class="sxs-lookup"><span data-stu-id="c2479-110">Input</span></span>

```xml
<?xml version="1.0"?>
  <books>
    <book>
        <author>Carson</author>
        <price format="dollar">31.95</price>
        <pubdate>05/01/2001</pubdate>
    </book>
    <pubinfo>
        <publisher>MSPress</publisher>
        <state>WA</state>
    </pubinfo>
  </books>
```

<span data-ttu-id="c2479-111">この XML データが DOM 構造に読み込まれるとき、メモリがどのように構造化されるかを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="c2479-111">The following illustration shows how memory is structured when this XML data is read into the DOM structure.</span></span>

<span data-ttu-id="c2479-112">![XML ドキュメントの構造](media/xml-to-domtree.gif "XML_To_DOMTree") XML ドキュメントの構造</span><span class="sxs-lookup"><span data-stu-id="c2479-112">![XML document structure](media/xml-to-domtree.gif "XML_To_DOMTree") XML document structure</span></span>

<span data-ttu-id="c2479-113">図中のそれぞれの円は、XML ドキュメント構造における 1 つのノードを表します。これは **XmlNode** オブジェクトと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c2479-113">Within the XML document structure, each circle in this illustration represents a node, which is called an **XmlNode** object.</span></span> <span data-ttu-id="c2479-114">**XmlNode** オブジェクトは、DOM ツリーの基本オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c2479-114">The **XmlNode** object is the basic object in the DOM tree.</span></span> <span data-ttu-id="c2479-115">**XmlNode** を拡張する **XmlDocument** クラスは、たとえばドキュメントをメモリに読み込んだり、XML をファイルに保存するなど、ドキュメント全体を操作するメソッドをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c2479-115">The **XmlDocument** class, which extends **XmlNode**, supports methods for performing operations on the document as a whole (for example, loading it into memory or saving the XML to a file.</span></span> <span data-ttu-id="c2479-116">さらに **XmlDocument** では、XML ドキュメント全体のノードを参照して操作する手段も提供されます。</span><span class="sxs-lookup"><span data-stu-id="c2479-116">In addition, **XmlDocument** provides a means to view and manipulate the nodes in the entire XML document.</span></span> <span data-ttu-id="c2479-117">**XmlNode** と **XmlDocument** は、いずれもパフォーマンスと使いやすさが向上しており、次の操作を実行するメソッドとプロパティを持っています。</span><span class="sxs-lookup"><span data-stu-id="c2479-117">Both **XmlNode** and **XmlDocument** have performance and usability enhancements and have methods and properties to:</span></span>

- <span data-ttu-id="c2479-118">要素ノード、エンティティ参照ノードなど、DOM に固有のノードへのアクセスと変更。</span><span class="sxs-lookup"><span data-stu-id="c2479-118">Access and modify nodes specific to the DOM, such as element nodes, entity reference nodes, and so on.</span></span>

- <span data-ttu-id="c2479-119">要素ノードのテキストなど、ノードに格納されている情報およびノード全体の取得。</span><span class="sxs-lookup"><span data-stu-id="c2479-119">Retrieve entire nodes, in addition to the information the node contains, such as the text in an element node.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c2479-120">アプリケーションが DOM の提供する構造や編集機能を必要としない場合は、**XmlReader** クラスと **XmlWriter** クラスを使って XML への非キャッシュ、前方参照専用のストリーム アクセスを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c2479-120">If an application does not require the structure or editing capabilities provided by the DOM, the **XmlReader** and **XmlWriter** classes provide non-cached, forward-only stream access to XML.</span></span> <span data-ttu-id="c2479-121">詳細については、次のトピックを参照してください。 <xref:System.Xml.XmlReader> および <xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="c2479-121">For more information, see <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="c2479-122">**Node** オブジェクトには、適切に定義された基本的な特性と、メソッドおよびプロパティのセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c2479-122">**Node** objects have a set of methods and properties, as well as basic and well-defined characteristics.</span></span> <span data-ttu-id="c2479-123">オブジェクトが持つ特性のいくつかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c2479-123">Some of these characteristics are:</span></span>

- <span data-ttu-id="c2479-124">ノードは 1 つの親ノードを持っています。親ノードはノードの 1 つ上のノードです。</span><span class="sxs-lookup"><span data-stu-id="c2479-124">Nodes have a single parent node, a parent node being a node directly above them.</span></span> <span data-ttu-id="c2479-125">ドキュメント ルートは最上位のノードであり、ドキュメント自身とドキュメント フラグメントしか格納されていないため、親ノードを持っていないノードはドキュメント ルートだけです。</span><span class="sxs-lookup"><span data-stu-id="c2479-125">The only nodes that do not have a parent is the Document root, as it is the top-level node and contains the document itself and document fragments.</span></span>

- <span data-ttu-id="c2479-126">ほとんどのノードは、複数の子ノードを持つことができます。子ノードは、ノードの 1 つ下のノードです。</span><span class="sxs-lookup"><span data-stu-id="c2479-126">Most nodes can have multiple child nodes, which are nodes directly below them.</span></span> <span data-ttu-id="c2479-127">子ノードを持つことができるノード型の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c2479-127">The following is a list of node types that can have child nodes.</span></span>

  - <span data-ttu-id="c2479-128">**Document**</span><span class="sxs-lookup"><span data-stu-id="c2479-128">**Document**</span></span>

  - <span data-ttu-id="c2479-129">**DocumentFragment**</span><span class="sxs-lookup"><span data-stu-id="c2479-129">**DocumentFragment**</span></span>

  - <span data-ttu-id="c2479-130">**EntityReference**</span><span class="sxs-lookup"><span data-stu-id="c2479-130">**EntityReference**</span></span>

  - <span data-ttu-id="c2479-131">**要素**</span><span class="sxs-lookup"><span data-stu-id="c2479-131">**Element**</span></span>

  - <span data-ttu-id="c2479-132">**属性**</span><span class="sxs-lookup"><span data-stu-id="c2479-132">**Attribute**</span></span>

  <span data-ttu-id="c2479-133">**XmlDeclaration** ノード、**Notation** ノード、**Entity** ノード、**CDATASection** ノード、**Text** ノード、**Comment** ノード、**ProcessingInstruction** ノード、**DocumentType** ノードは子ノードを持ちません。</span><span class="sxs-lookup"><span data-stu-id="c2479-133">The **XmlDeclaration**, **Notation**, **Entity**, **CDATASection**, **Text**, **Comment**, **ProcessingInstruction**, and **DocumentType** nodes do not have child nodes.</span></span>

- <span data-ttu-id="c2479-134">図中に **book** および **pubinfo** として同レベルに表現されているノードは兄弟です。</span><span class="sxs-lookup"><span data-stu-id="c2479-134">Nodes that are at the same level, represented in the diagram by the **book** and **pubinfo** nodes, are siblings.</span></span>

<span data-ttu-id="c2479-135">DOM の特性の 1 つは、属性の取り扱い方法にあります。</span><span class="sxs-lookup"><span data-stu-id="c2479-135">One characteristic of the DOM is how it handles attributes.</span></span> <span data-ttu-id="c2479-136">属性は、互いに親子関係や兄弟関係を持つノードではありません。</span><span class="sxs-lookup"><span data-stu-id="c2479-136">Attributes are not nodes that are part of the parent, child, and sibling relationships.</span></span> <span data-ttu-id="c2479-137">属性は要素ノードのプロパティと見なされ、名前と値ペアから構成されます。</span><span class="sxs-lookup"><span data-stu-id="c2479-137">Attributes are considered a property of the element node and are made up of a name and a value pair.</span></span> <span data-ttu-id="c2479-138">たとえば、要素 `format="dollar` に関連付けられている `price`" という形式の XML データがある場合は、単語 `format` が名前になり、`format` 属性の値は `dollar` になります。</span><span class="sxs-lookup"><span data-stu-id="c2479-138">For example, if you have XML data consisting of `format="dollar`" associated with the element `price`, the word `format` is the name, and the value of the `format` attribute is `dollar`.</span></span> <span data-ttu-id="c2479-139">**price** ノードの `format="dollar"` 属性を取得するには、カーソルが `price` 要素ノード上にあるときに **GetAttribute** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c2479-139">To retrieve the `format="dollar"` attribute of the **price** node, you call the **GetAttribute** method when the cursor is located at the `price` element node.</span></span> <span data-ttu-id="c2479-140">詳細については、「[DOM の属性へのアクセス](accessing-attributes-in-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2479-140">For more information, see [Accessing Attributes in the DOM](accessing-attributes-in-the-dom.md).</span></span>

<span data-ttu-id="c2479-141">XML をメモリに読み込むと、ノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c2479-141">As XML is read into memory, nodes are created.</span></span> <span data-ttu-id="c2479-142">ただし、すべてのノードが同じタイプというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="c2479-142">However, not all nodes are the same type.</span></span> <span data-ttu-id="c2479-143">XML の要素の規則と構文は、処理命令の規則と構文とは異なります。</span><span class="sxs-lookup"><span data-stu-id="c2479-143">An element in XML has different rules and syntax than a processing instruction.</span></span> <span data-ttu-id="c2479-144">したがって、さまざまなデータが読み込まれるときに、個々のノードにノード型が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c2479-144">Therefore, as various data is read, a node type is assigned to each node.</span></span> <span data-ttu-id="c2479-145">このノード型によって、ノードの特性と機能が決定されます。</span><span class="sxs-lookup"><span data-stu-id="c2479-145">This node type determines the characteristics and functionality of the node.</span></span>

<span data-ttu-id="c2479-146">メモリに生成されるノード型の詳細については、「[XML ノードの種類](types-of-xml-nodes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2479-146">For more information on the types of nodes generated in memory, see [Types of XML Nodes](types-of-xml-nodes.md).</span></span> <span data-ttu-id="c2479-147">ノード ツリーに作成されるオブジェクトの詳細については、「[オブジェクト階層の XML データへのマップ](mapping-the-object-hierarchy-to-xml-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2479-147">For more information on the objects created in the node tree, see [Mapping the Object Hierarchy to XML Data](mapping-the-object-hierarchy-to-xml-data.md).</span></span>

<span data-ttu-id="c2479-148">Microsoft では、XML ドキュメントの操作を容易にするために、W3C (World Wide Web Consortium) DOM Level 1 および Level 2 で規定されている API を拡張しています。</span><span class="sxs-lookup"><span data-stu-id="c2479-148">Microsoft has extended the APIs that are available in the World Wide Web Consortium (W3C) DOM Level 1 and Level 2 to make it easier to work with an XML document.</span></span> <span data-ttu-id="c2479-149">W3C の標準を完全にサポートする一方で、追加のクラス、メソッド、プロパティにより、W3C の XML DOM で実現できる以上の機能が付加されています。</span><span class="sxs-lookup"><span data-stu-id="c2479-149">While fully supporting the W3C standards, the additional classes, methods, and properties add functionality beyond what can be done using the W3C XML DOM.</span></span> <span data-ttu-id="c2479-150">新しいクラスを使用すると、リレーショナル データにアクセスし、ADO.NET との同期をとりながら、データを XML として公開できます。</span><span class="sxs-lookup"><span data-stu-id="c2479-150">New classes enable you to access relational data, giving you methods for synchronizing with ADO.NET data, simultaneously exposing data as XML.</span></span> <span data-ttu-id="c2479-151">詳細については、「[Dataset と XmlDataDocument の同期](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2479-151">For more information, see [Synchronizing a DataSet with an XmlDataDocument](../../../framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md).</span></span>

<span data-ttu-id="c2479-152">DOM が最も役に立つのは、XML データをメモリに読み込み、その構造を変更したり、ノードを追加または削除したり、要素内のテキストとしてノードが保持しているデータを変更したりする場合です。</span><span class="sxs-lookup"><span data-stu-id="c2479-152">The DOM is most useful for reading XML data into memory to change its structure, to add or remove nodes, or to modify the data held by a node as in the text contained by an element.</span></span> <span data-ttu-id="c2479-153">ただし、他のクラスも用意されており、シナリオによっては DOM より高速になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="c2479-153">However, other classes are available that are faster than the DOM in other scenarios.</span></span> <span data-ttu-id="c2479-154">XML に対して高速、非キャッシュ、前方参照専用のストリーム アクセスを行うには、**XmlReader** と **XmlWriter** を使用します。</span><span class="sxs-lookup"><span data-stu-id="c2479-154">For fast, non-cached, forward-only stream access to XML, use the **XmlReader** and **XmlWriter**.</span></span> <span data-ttu-id="c2479-155">カーソル モデルと **XPath** を使用したランダム アクセスが必要な場合は、**XPathNavigator** クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="c2479-155">If you need random access with a cursor model and **XPath**, use the **XPathNavigator** class.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2479-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2479-156">See also</span></span>

- [<span data-ttu-id="c2479-157">XML ノードの種類</span><span class="sxs-lookup"><span data-stu-id="c2479-157">Types of XML Nodes</span></span>](types-of-xml-nodes.md)
- [<span data-ttu-id="c2479-158">オブジェクト階層の XML データへのマップ</span><span class="sxs-lookup"><span data-stu-id="c2479-158">Mapping the Object Hierarchy to XML Data</span></span>](mapping-the-object-hierarchy-to-xml-data.md)
