---
title: 既存のノードのコピー
ms.date: 03/30/2017
ms.assetid: 2aa8f65c-cc62-4638-9c46-129dc15be786
ms.openlocfilehash: 651e9fc9dc0d1a50a2d15d382b3ca65f7fd4b7fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701433"
---
# <a name="copy-existing-nodes"></a><span data-ttu-id="2c55d-102">既存のノードのコピー</span><span class="sxs-lookup"><span data-stu-id="2c55d-102">Copy Existing Nodes</span></span>

<span data-ttu-id="2c55d-103">XML ドキュメント オブジェクト モデル (DOM) には、**SelectSingleNode**、**ChildNodes[int i]** 、**Attributes[int i]** など、ノードの選択に使用できるメソッドとプロパティが多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="2c55d-103">There are many methods and properties in the XML Document Object Model (DOM)you can use to select a node, such as **SelectSingleNode**, **ChildNodes[int i]**, **Attributes[int i]**.</span></span> <span data-ttu-id="2c55d-104">ノードを選択すると、その特定のノード型で利用できる挿入メソッドを使用してツリーに挿入できます。</span><span class="sxs-lookup"><span data-stu-id="2c55d-104">Once the node is selected, you can insert it into the tree using one of the insert methods that work for that particular node type.</span></span> <span data-ttu-id="2c55d-105">ノードをツリーに挿入するときの唯一の制約は、ノードを挿入した後もドキュメントが整形式になっていなければならないことです。</span><span class="sxs-lookup"><span data-stu-id="2c55d-105">The only restriction to inserting a node into the tree is that the document must still be well-formed after the node is inserted.</span></span> <span data-ttu-id="2c55d-106">既存のノードを DOM ツリーに挿入すると、そのノードは元の位置から削除され、挿入先の位置に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2c55d-106">When an existing node is inserted into the DOM tree, it is removed from its original position and added to its target position.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c55d-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c55d-107">See also</span></span>

- [<span data-ttu-id="2c55d-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="2c55d-108">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
