---
title: XML ドキュメント オブジェクト モデル (DOM) の階層構造
ms.date: 03/30/2017
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 24ef51a18392fe3034e64bd585d879941fca4b95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718359"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="e9169-102">XML ドキュメント オブジェクト モデル (DOM) の階層構造</span><span class="sxs-lookup"><span data-stu-id="e9169-102">XML Document Object Model (DOM) Hierarchy</span></span>

<span data-ttu-id="e9169-103">XML ドキュメント オブジェクト モデル (DOM) のクラスの階層構造を次の図に示します。クラス名に続くかっこ内の名前は、W3C (World Wide Web Consortium) 名です。</span><span class="sxs-lookup"><span data-stu-id="e9169-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="e9169-104">![XML ドキュメント オブジェクト モデル &#40;DOM&#41; の階層構造](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="e9169-104">![XML Document Object Model &#40;DOM&#41; hierarchy](media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="e9169-105">XML ドキュメント オブジェクト モデル (DOM) の階層構造</span><span class="sxs-lookup"><span data-stu-id="e9169-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="e9169-106">次のクラスは **XmlNode** から継承したものではありません。</span><span class="sxs-lookup"><span data-stu-id="e9169-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="e9169-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="e9169-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="e9169-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="e9169-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="e9169-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="e9169-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="e9169-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="e9169-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="e9169-111">**XmlImplementation** クラスは、XML ドキュメントを作成するために使われます。</span><span class="sxs-lookup"><span data-stu-id="e9169-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="e9169-112">詳細については、「[XML ドキュメントの作成](xml-document-creation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9169-112">For more information, see [XML Document Creation](xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="e9169-113">**XmlNamedNodeMap** クラスは、順序付けられていないノード セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9169-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="e9169-114">詳細については、「[名前またはインデックスによる順序付けられていないノードの取得](unordered-node-retrieval-by-name-or-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9169-114">For more information, see [Unordered Node Retrieval by Name or Index](unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="e9169-115">**XmlNodeList** クラスは、順序付けられたノード リストを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9169-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="e9169-116">詳細については、「[インデックスによる順序付けられたノードの取得](ordered-node-retrieval-by-index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9169-116">For more information, see [Ordered Node Retrieval by Index](ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="e9169-117">**XmlNodeChangedEventArgs** クラスは、**XmlDocument** に登録されたイベント ハンドラーを処理します。</span><span class="sxs-lookup"><span data-stu-id="e9169-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="e9169-118">詳細については、「[XmlNodeChangedEventArgs による XML ドキュメントのイベント処理](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9169-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="e9169-119">**XmlLinkedNode** クラスは **XmlNode** から継承しています。</span><span class="sxs-lookup"><span data-stu-id="e9169-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="e9169-120">その目的は、**XmlNode** の **PreviousSibling** と **NextSibling** という 2 つのメソッドをオーバーライドすることです。</span><span class="sxs-lookup"><span data-stu-id="e9169-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="e9169-121">これらのオーバーライドされたメソッドは、前後に兄弟を持つ **XmlCharacterData**、**XmlDeclaration**、**XmlDocumentType**、**XmlElement**、**XmlEntityReference**、**XmlProcessingInstruction** クラスによって継承され、使用されます。</span><span class="sxs-lookup"><span data-stu-id="e9169-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9169-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9169-122">See also</span></span>

- [<span data-ttu-id="e9169-123">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="e9169-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
