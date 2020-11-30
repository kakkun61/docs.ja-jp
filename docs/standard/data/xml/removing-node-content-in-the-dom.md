---
title: DOM のノード コンテンツの削除
ms.date: 03/30/2017
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
ms.openlocfilehash: d624e3eff3d61c2b8d312f370a4a11e3aede37e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721492"
---
# <a name="removing-node-content-in-the-dom"></a><span data-ttu-id="c9e36-102">DOM のノード コンテンツの削除</span><span class="sxs-lookup"><span data-stu-id="c9e36-102">Removing Node Content in the DOM</span></span>

<span data-ttu-id="c9e36-103"><xref:System.Xml.XmlCharacterData> を継承するノード型、つまり <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace>、および <xref:System.Xml.XmlSignificantWhitespace> ノード型では、ノードから文字範囲を削除する <xref:System.Xml.XmlCharacterData.DeleteData%2A> メソッドを使用して文字を削除できます。</span><span class="sxs-lookup"><span data-stu-id="c9e36-103">For node types that inherit from <xref:System.Xml.XmlCharacterData>, which are the <xref:System.Xml.XmlComment>, <xref:System.Xml.XmlText>, <xref:System.Xml.XmlCDataSection>, <xref:System.Xml.XmlWhitespace>, and <xref:System.Xml.XmlSignificantWhitespace> node types, you can remove characters using the <xref:System.Xml.XmlCharacterData.DeleteData%2A> method, which removes a range of characters from the node.</span></span> <span data-ttu-id="c9e36-104">コンテンツを完全に削除するには、そのコンテンツが含まれているノードを削除します。</span><span class="sxs-lookup"><span data-stu-id="c9e36-104">If you want to remove content completely, you remove the node that contains the content.</span></span> <span data-ttu-id="c9e36-105">ノードを保持する必要があり、コンテンツが正しくない場合は、そのコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="c9e36-105">If you want to keep the node, but the content is incorrect, then modify the content.</span></span> <span data-ttu-id="c9e36-106">ノードのコンテンツを変更する方法については、「[XML ドキュメントのノード、コンテンツ、値の変更](modifying-nodes-content-and-values-in-an-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c9e36-106">For information on modifying the content of a node, see [Modifying Nodes, Content, and Values in an XML Document](modifying-nodes-content-and-values-in-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e36-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9e36-107">See also</span></span>

- [<span data-ttu-id="c9e36-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="c9e36-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
