---
title: DOM モデルを使用した XML データの処理
ms.date: 03/30/2017
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
ms.openlocfilehash: 2608008f33eb8bc0dd0a9b5fe96e619df6138b51
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830910"
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="7e890-102">DOM モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="7e890-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="7e890-103">XML ドキュメント オブジェクト モデル (DOM) は、XML データをメモリ内で処理するために使用され、XML データを標準の一連のオブジェクトとして取り扱います。</span><span class="sxs-lookup"><span data-stu-id="7e890-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="7e890-104">`System.Xml` 名前空間は、XML ドキュメント、フラグメント、ノード、またはノードセットのプログラム表現を提供します。</span><span class="sxs-lookup"><span data-stu-id="7e890-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="7e890-105">これは、W3C (World Wide Web Consortium) の DOM Level 1 Core および DOM Level 2 Core 勧告に基づいています。</span><span class="sxs-lookup"><span data-stu-id="7e890-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="7e890-106"><xref:System.Xml.XmlDocument> クラスは、XML ドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="7e890-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="7e890-107">これには、他のすべての XML オブジェクトの取り出しと作成のためのメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7e890-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="7e890-108"><xref:System.Xml.XmlDocument> およびその関連クラスを使用して、XML ドキュメントの作成、データの読み込みとアクセス、データの変更、および変更の保存が可能です。</span><span class="sxs-lookup"><span data-stu-id="7e890-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7e890-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7e890-109">In This Section</span></span>  
  
- [<span data-ttu-id="7e890-110">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="7e890-110">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)  
  
- [<span data-ttu-id="7e890-111">XML ノードの種類</span><span class="sxs-lookup"><span data-stu-id="7e890-111">Types of XML Nodes</span></span>](types-of-xml-nodes.md)  
  
- [<span data-ttu-id="7e890-112">XML ドキュメント オブジェクト モデル (DOM) の階層構造</span><span class="sxs-lookup"><span data-stu-id="7e890-112">XML Document Object Model (DOM) Hierarchy</span></span>](xml-document-object-model-dom-hierarchy.md)  
  
- [<span data-ttu-id="7e890-113">オブジェクト階層の XML データへのマップ</span><span class="sxs-lookup"><span data-stu-id="7e890-113">Mapping the Object Hierarchy to XML Data</span></span>](mapping-the-object-hierarchy-to-xml-data.md)  
  
- [<span data-ttu-id="7e890-114">XML ドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="7e890-114">XML Document Creation</span></span>](xml-document-creation.md)  
  
- [<span data-ttu-id="7e890-115">XML ドキュメントの DOM への読み取り</span><span class="sxs-lookup"><span data-stu-id="7e890-115">Reading an XML Document into the DOM</span></span>](reading-an-xml-document-into-the-dom.md)  
  
- [<span data-ttu-id="7e890-116">XML ドキュメントへのノードの挿入</span><span class="sxs-lookup"><span data-stu-id="7e890-116">Inserting Nodes into an XML Document</span></span>](inserting-nodes-into-an-xml-document.md)  
  
- [<span data-ttu-id="7e890-117">XML ドキュメントからのノード、コンテンツ、値の削除</span><span class="sxs-lookup"><span data-stu-id="7e890-117">Removing Nodes, Content, and Values from an XML Document</span></span>](removing-nodes-content-and-values-from-an-xml-document.md)  
  
- [<span data-ttu-id="7e890-118">XML ドキュメントのノード、コンテンツ、値の変更</span><span class="sxs-lookup"><span data-stu-id="7e890-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](modifying-nodes-content-and-values-in-an-xml-document.md)  
  
- [<span data-ttu-id="7e890-119">DOM における XML ドキュメントの検証</span><span class="sxs-lookup"><span data-stu-id="7e890-119">Validating an XML Document in the DOM</span></span>](validating-an-xml-document-in-the-dom.md)  
  
- [<span data-ttu-id="7e890-120">ドキュメントの保存と書き込み</span><span class="sxs-lookup"><span data-stu-id="7e890-120">Saving and Writing a Document</span></span>](saving-and-writing-a-document.md)  
  
- [<span data-ttu-id="7e890-121">XPath ナビゲーションによるノードの選択</span><span class="sxs-lookup"><span data-stu-id="7e890-121">Select Nodes Using XPath Navigation</span></span>](select-nodes-using-xpath-navigation.md)  
  
- [<span data-ttu-id="7e890-122">外部リソースの解決</span><span class="sxs-lookup"><span data-stu-id="7e890-122">Resolving External Resources</span></span>](resolving-external-resources.md)  
  
- [<span data-ttu-id="7e890-123">XmlNameTable によるオブジェクトの比較</span><span class="sxs-lookup"><span data-stu-id="7e890-123">Object Comparison Using XmlNameTable</span></span>](object-comparison-using-xmlnametable.md)  
  
- [<span data-ttu-id="7e890-124">NamedNodeMaps と NodeLists のノード コレクション</span><span class="sxs-lookup"><span data-stu-id="7e890-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](node-collections-in-namednodemaps-and-nodelists.md)  
  
- [<span data-ttu-id="7e890-125">NodeLists および NamedNodeMaps の動的更新</span><span class="sxs-lookup"><span data-stu-id="7e890-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
- [<span data-ttu-id="7e890-126">DOM における名前空間のサポート</span><span class="sxs-lookup"><span data-stu-id="7e890-126">Namespace Support in the DOM</span></span>](namespace-support-in-the-dom.md)  
  
- [<span data-ttu-id="7e890-127">XmlNodeChangedEventArgs による XML ドキュメントのイベント処理</span><span class="sxs-lookup"><span data-stu-id="7e890-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
- [<span data-ttu-id="7e890-128">DOM の拡張</span><span class="sxs-lookup"><span data-stu-id="7e890-128">Extending the DOM</span></span>](extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="7e890-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="7e890-129">Related Sections</span></span>  
 [<span data-ttu-id="7e890-130">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="7e890-130">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="7e890-131"><xref:System.Xml.XPath.XPathNavigator> クラスによる XML の処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="7e890-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
